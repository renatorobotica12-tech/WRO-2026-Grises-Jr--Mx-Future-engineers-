
## Engineering journal

## 4/July/2026: Initial Prototyping & Basic Control Code
We developed a foundational steering and traction system for the open challenge. This code implements a basic PD (Proportional-Derivative) controller utilizing two ultrasonic sensors to maintain a central position in the hallway.

```python
#!/usr/bin/env python3

from ev3dev2.motor import MediumMotor, OUTPUT_A, OUTPUT_B
from ev3dev2.sensor.lego import UltrasonicSensor
from ev3dev2.sensor import INPUT_2, INPUT_3
import time

# ==========================
# HARDWARE
# ==========================
direccion = MediumMotor(OUTPUT_B)
traccion = MediumMotor(OUTPUT_A)

# OBLIGATORIO: Pon las llantas derechas con la mano antes de correr el programa
direccion.position = 0 

us_izq = UltrasonicSensor(INPUT_2)
us_der = UltrasonicSensor(INPUT_3)

# ==========================
# PID CONFIG
# ==========================
DT = 0.02 
KP = 3 
KD = 2.0 
error_anterior = 0

# ==========================
# LOOP PRINCIPAL
# ==========================
try:
    print("Corriendo... dale pista!")
    while True:
        izq = us_izq.distance_centimeters
        der = us_der.distance_centimeters

        # Filtro por si un sensor se va al infinito
        if izq > 140: izq = 140
        if der > 140: der = 140

        error = der - izq

        # Zona muerta para que vaya recto
        if abs(error) < 1.0:
            output = 0
        else:
            derivada = (error - error_anterior) / DT
            output = (KP * error) + (KD * derivada)

        # Límites de seguridad para el output (-35 a 35)
        if output > 35:
            output = 35
        elif output < -35:
            output = -35
        
        # ACCIÓN DE LOS MOTORES (Fuera de los ifs de control)
        # Forzamos que sea un entero para que ev3dev2 no tire error
        direccion.on(speed=int(output))

        # Motor de tracción constante
        traccion.on(speed=35)

        error_anterior = error
        time.sleep(DT)

except KeyboardInterrupt:
    pass
finally:
    direccion.off()
    traccion.off()
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
We used a beta version of the previous code because we were waiting for some cables that had been ordered and were scheduled to arrive on July 22, 2026:

```python

#!/usr/bin/env python3

from ev3dev2.motor import MediumMotor, OUTPUT_A, OUTPUT_B
from ev3dev2.sensor.lego import UltrasonicSensor
from ev3dev2.sensor import INPUT_2, INPUT_3
import time

# ==========================
# HARDWARE
# ==========================
direccion = MediumMotor(OUTPUT_B)
traccion = MediumMotor(OUTPUT_A)

# OBLIGATORIO: Pon las llantas derechas con la mano antes de correr el programa
direccion.position = 0 

us_izq = UltrasonicSensor(INPUT_2)
us_der = UltrasonicSensor(INPUT_3)

# ==========================
# PID CONFIG
# ==========================
DT = 0.02 
KP = 3 
KD = 2.0 
error_anterior = 0

# ==========================
# LOOP PRINCIPAL
# ==========================
try:
    print("Corriendo sin zona muerta... dale pista!")
    while True:
        izq = us_izq.distance_centimeters
        der = us_der.distance_centimeters

        # Filtro de distancia (ajusta este límite según tu pista, ej. 69.5)
        if izq > 69.5: izq = 69.5
        if der > 69.5: der = 69.5

        error = der - izq

        # ZONA MUERTA ELIMINADA: El PD calcula siempre
        derivada = (error - error_anterior) / DT
        output = (KP * error) + (KD * derivada)

        # Límites de seguridad para el output (-35 a 35)
        if output > 35:
            output = 35
        elif output < -35:
            output = -35
         
        # ACCIÓN DE LOS MOTORES
        direccion.on(speed=int(output))

        # Motor de tracción constante
        traccion.on(speed=35)

        error_anterior = error
        time.sleep(DT)

except KeyboardInterrupt:
    pass
finally:
    direccion.off()
    traccion.off()
```
## We also programmed the system using the I²C communication protocol:

```python

/*!
 * WRO TIJUANA 26 - Nano
 * Solo lectura de 5 sensores ultrasónicos por I2C
 */
#include <Wire.h>

// ── Variables de los 5 sensores ─────────────────────────────
// Sensores: Izquierda, Izquierda-Diagonal, Frente, Derecha-Diagonal, Derecha
float distIzq, distIzqDiag, distFrente, distDerDiag, distDer;

// Direcciones I2C de ejemplo para los 5 sensores (modifícalas según las direcciones configuradas en tus módulos)
const byte direccionesI2C[5] = {0x11, 0x12, 0x13, 0x14, 0x15};

// ─────────────────────────────────────────────────────────────
// Función genérica para leer un sensor ultrasónico por I2C
float leerSensorI2C(byte direccion) {
  Wire.beginTransmission(direccion);
  Wire.write(0x01); // Registro de inicio de medición (varía según el modelo del sensor)
  Wire.endTransmission();
  
  delay(10); // Tiempo para que el sensor procese la lectura
  
  Wire.requestFrom((int)direccion, 2); // Pedir 2 bytes (distancia en cm)
  if (Wire.available() >= 2) {
    int distanciaRaw = Wire.read() << 8 | Wire.read();
    return (float)distanciaRaw; // Retornar en centímetros
  }
  return 150.0; // Valor por defecto si falla la lectura
}

// ─────────────────────────────────────────────────────────────
void setup() {
  Serial.begin(9600);

  // Iniciar bus I2C
  Wire.begin();               // A4=SDA, A5=SCL en Nano
  Wire.setClock(400000);
  delay(100);
}

void loop() {
  // Lectura de los 5 sensores por I2C usando sus respectivas direcciones
  distIzq     = leerSensorI2C(direccionesI2C[0]);
  distIzqDiag = leerSensorI2C(direccionesI2C[1]);
  distFrente  = leerSensorI2C(direccionesI2C[2]);
  distDerDiag = leerSensorI2C(direccionesI2C[3]);
  distDer     = leerSensorI2C(direccionesI2C[4]);

  Serial.print("izq ");     Serial.print(distIzq);
  Serial.print(" izqD ");   Serial.print(distIzqDiag);
  Serial.print(" frente "); Serial.print(distFrente);
  Serial.print(" derD ");   Serial.print(distDerDiag);
  Serial.print(" der ");    Serial.println(distDer);

  delay(10);
}


```

## 27/07/26 – Today, we integrated the sensor multiplexer into the robot, allowing us to remove almost all the cables from the numbered ports, leaving only one of the original four letter ports in use.

## We also integrated 3D-printed mounts for the ultrasonic sensors into the robot. Additionally, due to time constraints and ease of development, we decided to return to using EV3-G (EV3 Blocks). However, we will provide the code in pseudocode, along with the original source code file in the src (source code) section.
