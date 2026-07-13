# 4/July/2026
## We developed this basic code for the open challenge in WRO Future Engineers

---
### basic code:

!/usr/bin/env python3

from ev3dev2.motor import MediumMotor, OUTPUT_A, OUTPUT_B
from ev3dev2.sensor.lego import UltrasonicSensor
from ev3dev2.sensor import INPUT_2, INPUT_3
import time 

direccion = MediumMotor(OUTPUT_A)
traccion = MediumMotor(OUTPUT_B)

us_izq = UltrasonicSensor(INPUT_2)
us_der = UltrasonicSensor(INPUT_3)

DT = 0.05

KP = 0.35
KD = 0.30

error_anterior = 0

try:
    while True:

        izq = us_izq.distance_centimeters
        der = us_der.distance_centimeters

        error = der - izq

        derivada = (error - error_anterior) / DT

        output = KP * error + KD * derivada

        # Limitamos la velocidad de giro del motor de dirección
        if output > 55:
            output = 55
        if output < -55:
            output = -55

        # Dirección por velocidad continua (sin encoder/calibración)
        direccion.on(speed=output)

        traccion.run_forever(speed_sp=450)

        error_anterior = error

        time.sleep(DT)

except KeyboardInterrupt:
    pass

finally:
    direccion.stop()
    
    traccion.stop()
    
    ---
# 8/July/2026 
## We ordered the custom PCB from China today.
---
# 10/July/2026

## The custom PCB we ordered arrived today.
---
# 13/July/2026

## We developed a new code that is much more effective in theory:
---
#!/usr/bin/env micropython
from ev3dev2.motor import LargeMotor, OUTPUT_A, OUTPUT_B
from ev3dev2.sensor import Sensor, INPUT_1, INPUT_2, INPUT_3, INPUT_4
from ev3dev2.sensor.lego import ColorSensor
import time

 --- CONFIGURACIÓN DE HARDWARE (Mapeo limpio de 4 puertos) ---
motor_izq = LargeMotor(OUTPUT_A)
motor_der = LargeMotor(OUTPUT_B)

/// Un puerto físico real asignado a cada sensor
sensor_90_izq = Sensor(INPUT_1)
sensor_90_der = Sensor(INPUT_2)
sensor_35_izq = Sensor(INPUT_3)  
sensor_35_der = Sensor(INPUT_4) 

/// El sensor HSDV de color lo cambiamos a INPUT_4 junto con el ultrasónico 
/// usando un splitter, o reasigna aquí los 4 puertos finales si usas expansor:
sensor_color = ColorSensor(INPUT_4) 

 --- VARIABLES DE CONTROL (MEF Y PID) ---
ESTADO_PASILLO = 0
ESTADO_CURVA = 1
estado_actual = ESTADO_PASILLO

DIRECCION_IZQ = -1
DIRECCION_DER = 1
direccion_curva = 0

/// Conteo de líneas de meta
lineas_contadas = 0
linea_detectada = False

/// Variables de control temporal e historial
error_anterior = 0
tiempo_vacio_detectado = None

 --- FUNCIÓN PID DE CENTRADO (PASILLO RECTO) ---
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

--- BUCLE PRINCIPAL DE CARRERA ---
while True:
    # 1. LECTURAS CONSTANTES ÚNICAS
    dist_35_izq = sensor_35_izq.value() / 10
    dist_35_der = sensor_35_der.value() / 10
    tiempo_actual = time.ticks_ms()

    # [SEGURO EVASIVO ELIMINADO PARA EVITAR CONFLICTO DE PUERTOS Y BUCLE INFINITO]

    # 2. CONTEO DE LÍNEAS CON SENSOR HSDV (Solo activo en pasillo recto)
    if estado_actual == ESTADO_PASILLO:
        if sensor_color.ambient_light_intensity < 30: 
            if not linea_detectada:
                lineas_contadas += 1
                linea_detectada = True
        else:
            linea_detectada = False

    /// 3. VERIFICACIÓN DE META (Frenado lineal uniforme de 20 décimas de segundo)
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

    /// 4. MÁQUINA DE ESTADOS FINITOS (MEF)
    if estado_actual == ESTADO_PASILLO:
        calcular_pid(kp=1.2, kd=4.5, velocidad_base=70)
        
        vacio_izq = dist_35_izq > 100
        vacio_der = dist_35_der > 100

        if vacio_izq or vacio_der:
            if tiempo_vacio_detectado is None:
                tiempo_vacio_detectado = tiempo_actual
            elif time.ticks_diff(tiempo_actual, tiempo_vacio_detectado) >= 35:
                # Transición de confianza sin congelar el procesador
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
        /// Trazado de curvas asimétrico controlado según la propuesta
        if direccion_curva == DIRECCION_IZQ:
            motor_izq.on(20)  
            motor_der.on(60)  
            
            /// Condición de salida: El diagonal izquierdo vuelve a ver la pared
            if dist_35_izq < 85:
                error_anterior = 0
                estado_actual = ESTADO_PASILLO
        
        elif direccion_curva == DIRECCION_DER:
            motor_izq.on(60)  
            motor_der.on(20)  
            
            /// Condición de salida: El diagonal derecho vuelve a ver la pared
            if dist_35_der < 85:
                error_anterior = 0
                estado_actual = ESTADO_PASILLO
                ---

 ---

