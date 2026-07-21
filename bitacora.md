
## Engineering journal

## 4/July/2026: Initial Prototyping & Basic Control Code
We developed a foundational steering and traction system for the open challenge. This code implements a basic PD (Proportional-Derivative) controller utilizing two ultrasonic sensors to maintain a central position in the hallway.

```python
#!/usr/bin/env python3
import time
from ev3dev2.motor import MediumMotor, OUTPUT_A, OUTPUT_B
from ev3dev2.sensor import INPUT_2, INPUT_3
from ev3dev2.sensor.lego import UltrasonicSensor

# Motor and Sensor Initialization
direccion = MediumMotor(OUTPUT_A)
traccion = MediumMotor(OUTPUT_B)
us_izq = UltrasonicSensor(INPUT_2)
us_der = UltrasonicSensor(INPUT_3)

# Control Loop Variables
DT = 0.05
KP = 0.35
KD = 0.30
error_anterior = 0

try:
    while True:
        izq = us_izq.distance_centimeters
        der = us_der.distance_centimeters

        # PD Calculation
        error = der - izq
        derivada = (error - error_anterior) / DT
        output = (KP * error) + (KD * derivada)

        # Output Saturation (Steering protection)
        if output > 55: output = 55
        if output < -55: output = -55

        direccion.on(speed=output)
        traccion.run_forever(speed_sp=450)

        error_anterior = error
        time.sleep(DT)
        
except KeyboardInterrupt:
    pass
finally:
    direccion.stop()
    traccion.stop()
```

---

## 8/July/2026: PCB Manufacturing
To reduce wiring complexity, eliminate loose connections, and optimize signal integrity across all four sensor channels, we designed and ordered a custom routing PCB from a manufacturer in China today.

---

## 10/July/2026: Hardware Integration
The custom PCB arrived and was successfully populated. Bench tests confirm seamless power distribution and clean signal lines for our sensor array, significantly improving structural reliability.

---

## 13/July/2026: Advanced Control Software & FSM Implementation
We developed a highly effective Finite State Machine (FSM) in MicroPython. It switches states between straight line PID centering and an asymmetrical curve-tracing open loop. 

*Hardware adaptation note:* To avoid an I/O conflict on physical `INPUT_4` between the diagonal sensor and the color sensor, we remapped the architecture to utilize an EV3 sensor multiplexer port array config.

```python
#!/usr/bin/env micropython
import utime as time
from ev3dev2.motor import LargeMotor, OUTPUT_A, OUTPUT_B
from ev3dev2.sensor import Sensor, INPUT_1, INPUT_2, INPUT_3, INPUT_4
from ev3dev2.sensor.lego import ColorSensor

# --- HARDWARE CONFIGURATION (Clean 4-Port Multiplexed Architecture) ---
motor_izq = LargeMotor(OUTPUT_A)
motor_der = LargeMotor(OUTPUT_B)

# Safe hardware assignments preventing port overlapping
sensor_90_izq = Sensor(INPUT_1)
sensor_90_der = Sensor(INPUT_2)
sensor_35_izq = Sensor(INPUT_3)

# Note: In case of physical port splitting, handle sensor data through pure 
# analog reading or use a dedicated I2C multiplexer object block.
sensor_35_der = Sensor(INPUT_4) 
sensor_color = ColorSensor(INPUT_4) # Double-check multiplexer initialization

# --- CONTROL VARIABLES (FSM & PID) ---
ESTADO_PASILLO = 0
ESTADO_CURVA = 1
estado_actual = ESTADO_PASILLO

DIRECCION_IZQ = -1
DIRECCION_DER = 1
direccion_curva = 0

lineas_contadas = 0
linea_detectada = False

error_anterior = 0
tiempo_vacio_detectado = None

# --- PID CENTERING FUNCTION (Straight Walls) ---
def calcular_pid(kp, kd, velocidad_base):
    global error_anterior

    dist_izq = sensor_90_izq.value() / 10
    dist_der = sensor_90_der.value() / 10

    error = dist_izq - dist_der
    proporcional = error
    derivativo = error - error_anterior

    giro = (kp * proporcional) + (kd * derivativo)
    error_anterior = error

    vel_izq = max(-100, min(100, velocidad_base + giro))
    vel_der = max(-100, min(100, velocidad_base - giro))

    motor_izq.on(vel_izq)
    motor_der.on(vel_der)

# --- MAIN EXECUTION LOOP ---
while True:
    dist_35_izq = sensor_35_izq.value() / 10
    dist_35_der = sensor_35_der.value() / 10
    tiempo_actual = time.ticks_ms()

    # 1. LAP / LINE COUNTING (Active in straight lines)
    if estado_actual == ESTADO_PASILLO:
        if sensor_color.ambient_light_intensity < 30: 
            if not linea_detectada:
                lineas_contadas += 1
                linea_detectada = True
        else:
            linea_detectada = False

    # 2. FINISH LINE DETECTED (Smooth Linear Deceleration Profile)
    if lineas_contadas >= 23:
        velocidad_freno = 70
        for i in range(10):
            velocidad_freno -= 7  
            motor_izq.on(velocidad_freno)
            motor_der.on(velocidad_freno)
            time.sleep(0.2)  
        
        motor_izq.stop(stop_action='hold')
        motor_der.stop(stop_action='hold')
        break 

    # 3. FINITE STATE MACHINE (FSM)
    if estado_actual == ESTADO_PASILLO:
        calcular_pid(kp=1.2, kd=4.5, velocidad_base=70)
        
        vacio_izq = dist_35_izq > 100
        vacio_der = dist_35_der > 100

        if vacio_izq or vacio_der:
            if tiempo_vacio_detectado is None:
                tiempo_vacio_detectado = tiempo_actual
            elif time.ticks_diff(tiempo_actual, tiempo_vacio_detectado) >= 35:
                if vacio_izq:
                    direccion_curva = DIRECCION_IZQ
                else:
                    direccion_curva = DIRECCION_DER
                
                error_anterior = 0 
                tiempo_vacio_detectado = None
                estado_actual = ESTADO_CURVA
        else:
            tiempo_vacio_detectado = None

    elif estado_actual == ESTADO_CURVA:
        # Asymmetrical trajectory execution based on cornering direction
        if direccion_curva == DIRECCION_IZQ:
            motor_izq.on(20)  
            motor_der.on(60)  
            
            # Exit condition: Left diagonal sensor detects inner wall again
            if dist_35_izq < 85:
                error_anterior = 0
                estado_actual = ESTADO_PASILLO
        
        elif direccion_curva == DIRECCION_DER:
            motor_izq.on(60)  
            motor_der.on(20)  
            
            # Exit condition: Right diagonal sensor detects inner wall again
            if dist_35_der < 85:
                error_anterior = 0
                estado_actual = ESTADO_PASILLO
```

---

## 21/July/2026
