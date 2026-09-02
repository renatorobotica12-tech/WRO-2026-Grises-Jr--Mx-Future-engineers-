## - PSEUDOCODE OPEN CHALLENGE

START

    // Initialization
    Start motor D
    // Motor D is used as the PCB adapter


    WHILE the program is running:

        // ------------------------------------------------
        // 1. FRONT ULTRASONIC CHECK
        // ------------------------------------------------

        Read front ultrasonic sensor
        ARD ← measured distance

        IF ARD < 25 cm THEN

            // An obstacle has been detected
            Stop motors

            Wait a few milliseconds

            // Emergency reverse
            Move LEGO motor in reverse
            for 0.5 rotations


        ELSE

            // ------------------------------------------------
            // 2. ERROR CALCULATION FOR THE PID
            // ------------------------------------------------

            Read ultrasonic sensor 1
            Read ultrasonic sensor 2
            Read ultrasonic sensor 3
            Read ultrasonic sensor 4

            // Sensors are grouped by side
            SIDE_A ← Ultrasonic_1 + Ultrasonic_2

            SIDE_B ← Ultrasonic_3 + Ultrasonic_4

            // Difference between both sides
            ERROR ← SIDE_A - SIDE_B


            // ------------------------------------------------
            // 3. SPEED CALCULATION / UPDATE
            // ------------------------------------------------

            Calculate VEL using the
            speed control logic


            // ------------------------------------------------
            // 4. PID CONTROL
            // ------------------------------------------------

            PID(
                ERROR,
                VEL,
                Kp,
                Ki,
                Kd
            )

            // Kp, Ki, and Kd correspond to the
            // values tuned and tested on the track.


        END IF

    END WHILE

END


## - FLOW SCHEME
                 ┌──────────────┐
                 │    START     │
                 └──────┬───────┘
                        ↓
                  Start motor D
                        ↓
                ┌──────────────┐
                │ MAIN LOOP    │◄─────────────────┐
                └──────┬───────┘                  │
                       ↓                          │
            Read front ultrasonic                 │
                       ↓                          │
                 Is ARD < 25 cm?                  │
                  /          \                    │
                YES           NO                  │
                ↓              ↓                  │
          Stop motors     Read 4 ultrasonic       │
                ↓              ↓                  │
       Wait a few ms      Calculate ERROR         │
                ↓              ↓                  │
       Reverse 0.5        Calculate VEL           │
       rotations               ↓                  │
                         Execute PID              │
                │              │                  │
                └──────────────┴───────────────────┘


                
## - EXPLANATION:

As you know, our working methodology is based on iteration, optimization, and continuous testing. Following this methodology, we developed this code through dozens of beta versions and extensive testing.

After numerous iterations and adjustments, we achieved a highly efficient PID controller. The values presented here are the result of real-world tuning and testing on the track, allowing us to optimize the system for actual competition conditions.
