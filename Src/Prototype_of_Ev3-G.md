## Pseudocódigo
INICIO

    Inicializar el robot.
    Inicializar la comunicación I2C.
    Inicializar los cinco sensores ultrasónicos.
    Inicializar el motor de dirección y el motor de avance.

    MIENTRAS el programa esté en ejecución HACER

        Leer mediante I2C las mediciones de los cinco sensores ultrasónicos.

        SI la distancia ≤ 80 cm ENTONCES

            // Modo de vuelta
            kP ← 1.6
            kI ← 0
            kD ← 0.2
            Velocidad de avance ← 65
            Limitador de dirección ← ±20

            MIENTRAS la distancia ≤ 80 cm HACER

                Leer los sensores de seguimiento.
                Calcular el error.
                Calcular la salida del controlador PD.
                Limitar la salida a ±20.

                Motor de avance ← 65
                Motor de dirección ← Salida del PD

                Leer nuevamente la distancia mediante I2C.

            FIN MIENTRAS

        SINO

            // Modo de pasillo
            kP ← 3.0
            kI ← 0
            kD ← 0.2
            Velocidad de avance ← 35
            Limitador de dirección ← ±40

            MIENTRAS la distancia > 80 cm HACER

                Leer los sensores de seguimiento.
                Calcular el error.
                Calcular la salida del controlador PD.
                Limitar la salida a ±40.

                Motor de avance ← 35
                Motor de dirección ← Salida del PD

                Leer nuevamente la distancia mediante I2C.

            FIN MIENTRAS

        FIN SI

    FIN MIENTRAS

FIN

## Código en Ev3-G 
<img width="1286" height="481" alt="3388029a-0e82-4c70-ba89-43083cc78581" src="https://github.com/user-attachments/assets/0cdb5868-6990-4e59-840f-fe66571ec242" />
