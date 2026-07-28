## This repository contains the official documentation of Team **"Los Grises Jr"** for the Future Engineers category at the World Robot Olympiad 2026.

<p align="center">
  <img src="https://github.com/user-attachments/assets/6422e0d6-8cc2-4bbc-beaf-4bbada98c140" width="700" />
</p>

---

## Team Photo


---
## Team Members

### Renato Medina

<p align="center">
<img width="350" height="350" alt="Image" src="https://github.com/user-attachments/assets/dd9e997b-65a7-4909-8207-ea3630b5aff4" />
</p>

**Role:** Programmer, Mechanical Designer & Team Captain

I began my robotics journey through the OnStage TMR program, where I discovered my passion for autonomous systems and engineering. Since then, I have focused on software development, electronics integration, and robot design.

For WRO 2026, my objective is to develop a reliable autonomous vehicle while expanding my knowledge in embedded systems, control theory, and robotic engineering. 

**Age:** 14

---

Project Description

Our robot is designed to autonomously complete the Future Engineers challenges by combining precise steering, ultrasonic sensing, and embedded control systems.

The current version focuses primarily on the Open Challenge, using multiple ultrasonic sensors and a closed-loop PD controller to maintain the vehicle centered inside the track.

Future development includes the integration of a computer vision subsystem for obstacle detection and avoidance.

Main Features
Closed-loop PD steering controller
Automatic steering calibration
Five ultrasonic sensors connected through a custom PCB
I²C communication between the Arduino Nano and EV3
Custom-designed PCB manufactured specifically for the project
3D-printed sensor supports
Finite State Machine (FSM) architecture (development stage)
Modular software architecture

---

## Vehicle Photo

<div align="center">



| Top | Right | Left |
| :---: | :---: | :---: |
| <img width="200" alt="Top" src="https://github.com/user-attachments/assets/db4220f0-02e5-4a55-ab61-ab2f27a2ebf8" /> | <img width="200" alt="Right" src="https://github.com/user-attachments/assets/592dc860-29e7-4466-9803-3c76527497e0" /> | <img width="200" alt="Left" src="https://github.com/user-attachments/assets/8f9ba958-2dd1-4182-8742-dd3fb614702a" /> |
| **Bottom** | **Rear** | |
| <img width="200" alt="Bottom" src="https://github.com/user-attachments/assets/f74e4b12-1b4c-46d5-8b1d-bdd542ea7e7e" /> | <img width="200" alt="Rear" src="https://github.com/user-attachments/assets/c91b58f6-3492-42d3-a011-75c5045cd772" /> | |


---

## Components and Hardware

| Component | Description | Status |
|-----------|-------------|--------|
| **45544 LEGO MINDSTORMS Education EV3 Core Set** | Forms the chassis, drive motor, and steering motor. Controlled via `ev3-g`. | **In use** |
| **5x Ultrasonic Sensors** | Mounted on the sides of the chassis for lane centering (left/right wall distance). | **In use** |
| **Arduino Nano** | ATmega328-based microcontroller, planned for vision processing. | Planned (Obstacle Challenge) |
| **DFRobot HuskyLens AI Camera** | AI vision sensor for detecting colored obstacles. | Planned (Obstacle Challenge) |

---
Mechanical Design

The vehicle uses an Ackermann-inspired steering mechanism driven by a dedicated EV3 Medium Motor.

Instead of continuously rotating the steering motor, the robot commands absolute steering positions obtained from the motor encoder. This approach provides greater repeatability and significantly improves steering accuracy.

Custom 3D-printed brackets maintain all ultrasonic sensors in fixed positions, reducing vibration and improving measurement consistency.

Electronics

One of the main engineering improvements was replacing individual sensor wiring with a custom-designed PCB.

The PCB:

simplifies cable management;
distributes power to every sensor;
routes all communication signals;
improves electrical reliability;
allows quick maintenance.

Communication between the Arduino Nano and the EV3 is performed through the I²C protocol, reducing the number of required EV3 input ports.

Software Architecture

The robot software is divided into several modules:

Sensor acquisition
Steering calibration
PD controller
Motion control
Finite State Machine
Safety functions

This modular structure makes future modifications easier while improving readability and maintenance.

Automatic Steering Calibration

Every run begins with an automatic calibration routine.

The steering motor:

Rotates to the left mechanical limit.
Rotates to the right mechanical limit.
Measures the total steering range.
Calculates the midpoint.
Moves to the calculated center.
Resets the encoder to zero.

This guarantees a repeatable steering reference without manual adjustment.

Sensor Calibration

At startup, the robot records both ultrasonic sensor readings while positioned approximately at the center of the track.

The measured difference is stored as a calibration offset and later removed from every control cycle, compensating for small mechanical assembly tolerances.

PD Steering Controller

The steering controller uses the difference between the left and right ultrasonic sensors.

error = (right_distance - left_distance) - sensor_offset

derivative = (error - previous_error) / dt

output = KP × error + KD × derivative

Current parameters:

Constant	Value
KP	0.35
KI	0.00
KD	0.30

The controller output is converted directly into a steering angle while remaining inside safe mechanical limits.

The integral term is intentionally disabled because ultrasonic measurements contain small fluctuations that could accumulate over time, reducing steering stability.

Engineering Journal

Development milestones are documented separately in the Engineering Journal, where each hardware and software iteration is described chronologically.

Engineering Decisions
Custom PCB

A custom PCB was designed to reduce wiring complexity and improve electrical reliability.

I²C Communication

Instead of connecting every ultrasonic sensor directly to the EV3, sensor data is collected by the Arduino Nano and transmitted through a single communication channel.

Encoder-Based Steering

Absolute encoder positioning provides greater steering precision than continuous motor rotation.

3D Printed Mounts

Custom supports improve sensor alignment while increasing structural rigidity.

Current Performance

Current testing demonstrates:

Stable lane centering
Smooth steering corrections
Reliable automatic calibration
Consistent multi-lap performance
Improved sensor reliability after PCB integration
Future Improvements

Planned developments include:

Obstacle Challenge implementation
HuskyLens computer vision
Dynamic speed control
Complete FSM implementation
Additional sensor fusion
Repository Structure
.
├── docs/
│   ├── engineering_journal.md
│   ├── mechanical_design.md
│   ├── electronics.md
│   └── software.md
│
├── models/
│   ├── chassis.stl
│   ├── sensor_mount.stl
│   └── pcb/
│
├── src/
│   ├── EV3-G/
│   ├── pseudocode/
│   └── arduino/
│
├── images/
│
└── README.md

The current version of the Los Grises Jr robot represents the result of an iterative engineering process involving mechanical design, electronics development, embedded programming, and control systems.

Key improvements—including a custom PCB, encoder-based steering, automatic calibration, and a modular software architecture—have significantly increased the robot's reliability and repeatability during testing. Future work will focus on integrating vision-based obstacle avoidance while preserving the robustness achieved in the Open Challenge.
