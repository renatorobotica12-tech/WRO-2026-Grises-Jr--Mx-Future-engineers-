
- FINAL PLATFORM diagram


| System | Implementation |
|:---|:---|
| Steering | Ackermann steering geometry |
| Drive System | Rear-wheel drive |
| Main Controller | LEGO Mindstorms EV3 Brick |
| Coprocessors | 2 Arduino Nano, 1 for the camera and one for the PCB |
| Vision System | HuskyLens AI Camera |
| Distance Measurement | Five ultrasonic sensors |
| Communication | I²C protocol and UART protocol |
| Electronics | Custom-designed PCB |
| Control Algorithm | Adaptive Dual PD Controller |
| Decision System | Finite State Machine |


---

- QUICK SYSTEM OVERVIEW diagram

                 ┌──────────────────┐               ┌────────────────┐
                 │ HuskyLens Camera │               │   Ultrasonic   │
                 └────────┬─────────┘               │  Sensors (x5)  │
                          │                         └───────┬────────┘
                          │ UART                            │
                          ▼                                 ▼
                 ┌──────────────────┐               ┌────────────────┐
                 │   Arduino Nano   │               │   Custom PCB   │
                 │      (UART)      │               └───────┬────────┘
                 └────────┬─────────┘                       │
                          │                                 ▼
                          │                         ┌────────────────┐
                          │                         │  Arduino Nano  │
                          │                         │     (I²C)      │
                          │                         └───────┬────────┘
                          │                                 │
                          └────────────────┬────────────────┘
                                           │
                                           ▼
                                   ┌────────────────┐
                                   │    LEGO EV3    │
                                   │   Controller   │
                                   └────────┬───────┘
                                            │
                            ┌───────────────┴───────────────┐
                            ▼                               ▼
                    ┌──────────────┐                ┌──────────────┐
                    │Steering Motor│                │  Drive Motor │
                    └──────────────┘                └──────────────┘
