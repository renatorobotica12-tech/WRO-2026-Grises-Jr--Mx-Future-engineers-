# Los Grises Jr — WRO Future Engineers 2026

This repository contains the official documentation of Team **"Los Grises Jr"** for the Future Engineers category at the World Robot Olympiad 2026.

<p align="center">
  <img src="https://github.com/user-attachments/assets/6422e0d6-8cc2-4bbc-beaf-4bbada98c140" width="700" />
</p>

---

## Team Photo

<p align="center">
<img width="650" height="700" alt="Image" src="https://github.com/user-attachments/assets/bfdd1ee5-125a-459d-8794-e7c5e245de1f" />
</p>

---

## Team Members

### Mateo Briones

<p align="center">
<img width="350" height="350" alt="Image" src="https://github.com/user-attachments/assets/7d893a62-c48c-434c-9ddc-abf3b26181aa" />
</p>

**Role:** Electronics Specialist

Two years ago in high school, I became interested in robotics and computer science, which led me to compete in RoboCup 2025. Since then I've focused on this hobby and want to keep growing in it. In this competition, my goal is to place in the top three.

**Age:** 14

---

### Ruth García

<p align="center">
<img width="350" height="350" alt="Image" src="https://github.com/user-attachments/assets/0eeb4fe7-00a4-4f3b-9274-29eee74b13ef" />
</p>

**Role:** Builder

This is my first time being part of a robotics club, and I'm really excited to be here. I enjoy learning new things and working with technology. I'm motivated to keep improving my skills and to help the team succeed.

**Age:** 15

---

### Renato Medina

<p align="center">
<img width="350" height="350" alt="Image" src="https://github.com/user-attachments/assets/dd9e997b-65a7-4909-8207-ea3630b5aff4" />
</p>

**Role:** Programmer and Captain

I started two years ago in elementary school at OnStage TMR, which sparked my interest in robotics. In this competition, my goal is to become a more well-rounded programmer.

**Age:** 14

---

## Project Overview

This project presents the development of an autonomous vehicle for the Future Engineers category of the World Robot Olympiad 2026.

The robot currently focuses on the **Open Challenge**: navigating the track using ultrasonic distance sensors and a closed-loop PD controller for steering.

The system integrates:

- Ultrasonic-based lane centering
- A dedicated steering motor with automatic calibration
- PD-based control for smooth, accurate trajectory tracking

The Obstacle Challenge subsystem (computer vision with a HuskyLens camera and Arduino Nano) is in earlier development and documented separately below as **planned/in progress**.

---

## Vehicle Photo

<div align="center">

| Top |
|:--:|
| <img width="300" alt="Image" src="https://github.com/user-attachments/assets/db4220f0-02e5-4a55-ab61-ab2f27a2ebf8" /> |
| Right |
| <img width="300" alt="Image" src="https://github.com/user-attachments/assets/592dc860-29e7-4466-9803-3c76527497e0" /> |
| Left |
| <img width="300" alt="Image" src="https://github.com/user-attachments/assets/8f9ba958-2dd1-4182-8742-dd3fb614702a" /> |
| Bottom |
| <img width="300" alt="Image" src="https://github.com/user-attachments/assets/f74e4b12-1b4c-46d5-8b1d-bdd542ea7e7e" /> |
| Rear |
| <img width="300" alt="Image" src="https://github.com/user-attachments/assets/c91b58f6-3492-42d3-a011-75c5045cd772" /> |

</div>

---

## Components and Hardware

| Component | Description | Status |
|-----------|-------------|--------|
| **45544 LEGO MINDSTORMS Education EV3 Core Set** | Forms the chassis, drive motor, and steering motor. Controlled via `ev3dev2`. | **In use** |
| **5x Ultrasonic Sensors** | Mounted on the sides of the chassis for lane centering (left/right wall distance). | **In use** |
| **Arduino Nano** | ATmega328-based microcontroller, planned for vision processing. | Planned (Obstacle Challenge) |
| **DFRobot HuskyLens AI Camera** | AI vision sensor for detecting colored obstacles. | Planned (Obstacle Challenge) |

---

## Open Challenge: Control System

### Steering Mechanism

Steering is controlled by a dedicated `MediumMotor`, operated via absolute encoder positions rather than continuous rotation. This allows precise, repeatable steering angles relative to a calibrated center.

### Automatic Steering Calibration

Because the steering motor's "center" position can vary between runs (depending on how the wheels were last left), the robot performs an automatic calibration routine at startup:

1. The steering motor drives left until it reaches its mechanical limit.
2. The steering motor drives right until it reaches its opposite mechanical limit.
3. The total range of motion is measured, and the mathematical center is calculated.
4. The motor moves to this calculated center and resets its encoder count to zero, establishing it as the new reference point.

This ensures consistent, centered steering at the start of every run without manual adjustment.

### Sensor Offset Calibration

At startup, both ultrasonic sensors take an initial reading while the robot is assumed to be centered on the track. The difference between the left and right readings is stored as an **offset** and subtracted from the error in every control loop. This compensates for small asymmetries in sensor placement or mounting.

### PD Control for Lane Centering

The robot maintains its position in the lane using a PD (Proportional-Derivative) controller based on the difference between the left and right ultrasonic sensor readings.

```
error = (right_distance - left_distance) - sensor_offset
derivative = (error - previous_error) / dt
output = Kp * error + Kd * derivative
```

The output is mapped directly to a target steering position (in encoder degrees), clamped to a safe range to avoid over-steering past the calibrated mechanical limits.

| Parameter | Value |
|:---------:|:-----:|
| KP | 0.35 |
| KI | 0.0 |
| KD | 0.30 |

The integral term is disabled (KI = 0) to avoid windup and instability from sensor noise.

### Why PD Instead of Full PID?

- **Proportional (KP):** provides immediate correction based on the current error.
- **Derivative (KD):** reduces oscillation by responding to how quickly the error is changing, smoothing out steering corrections.
- **Integral (KI):** disabled, since accumulated error from ultrasonic sensor noise could cause windup and erratic steering.

### Results

Early testing shows the robot tracking near the center of the lane with smooth, small steering corrections rather than abrupt swings, completing multiple laps consistently. Further tuning and lap-counting logic are in progress.

---

## Obstacle Challenge (Planned)

The Obstacle Challenge will extend the system with a vision-based subsystem for detecting and avoiding colored pillars.

### Planned Architecture

| Subsystem | Responsibility |
|-----------|----------------|
| HuskyLens (on Arduino Nano) | Detects colored pillars, extracts horizontal position |
| Arduino Nano | Processes vision data, sends position over UART |
| EV3 | Receives position data, controls steering and drive motors |

**Data flow:** HuskyLens → Arduino Nano → EV3 → Motors

### Planned Control Approach

```
loop:
    if object_detected and width > threshold:
        # Vision mode
        error = setpoint - x_position
    else:
        # Ultrasonic mode (same as Open Challenge)
        error = right_distance - left_distance

    derivative = error - previous_error
    output = Kp * error + Kd * derivative
    output = clamp(output, -limit, limit)
```

This approach has not yet been successfully implemented and is being redesigned. It will be documented in detail once a working version is achieved.

---

## Engineering Decisions

### Steering by Absolute Encoder Position

Earlier versions controlled steering using continuous motor rotation (as in EV3-G block programming). The current implementation, written for `ev3dev2`, uses **absolute encoder positions** instead. This required adding the automatic calibration routine described above, but provides far more precise and repeatable steering angles, which improved trajectory accuracy significantly.

### PD Controller Tuning

Initial values (KP = 0.35, KD = 0.30) were carried over conceptually from earlier block-based experiments but had to be re-tuned for the new encoder-based output scale. The current values produce smooth, centered lane-following without the oscillation seen in earlier versions.

### Sensor Offset Compensation

Adding a one-time sensor offset measurement at startup helps account for minor asymmetries in sensor mounting without requiring physical realignment.

---

## Challenges

- Migrating steering control from block-based programming (EV3-G) to `ev3dev2`, including building a reliable automatic calibration routine for the steering motor.
- Tuning PD parameters for the new encoder-based steering scale.
- Designing the vision-based obstacle avoidance subsystem (in progress).

---

## Limitations

- The Obstacle Challenge vision subsystem is not yet functional and is under redesign.
- Ultrasonic sensor readings can be affected by surface angle and material, which may introduce small inconsistencies in distance measurements.

---

## Conclusion

The Los Grises Jr robot currently implements a reliable Open Challenge navigation system based on ultrasonic sensing, automatic steering calibration, and PD control. The Obstacle Challenge vision subsystem remains a work in progress and will be documented as it develops.

---

## System Diagram (Current)

```mermaid
flowchart LR
    A[Ultrasonic Sensors] -->|Distance Data| B[EV3 Controller]
    B -->|PD Control Output| C[Steering Motor]
    B -->|Constant Speed| D[Drive Motor]
```




# Los Grises Jr — WRO Future Engineers 2026

This repository contains the official documentation, design files, and engineering decisions of Team **"Los Grises Jr"** competing in the Future Engineers category at the World Robot Olympiad 2026.

<p align="center">
  <img src="logo.jpg" width="700" alt="Los Grises Jr Logo" />
</p>

---

## Team Photo

<p align="center">
  <img src="team_photo.jpg" width="650" alt="Los Grises Jr Team Photo" />
</p>

---

## Team Members

### Mateo Briones
<p align="center">
  <img src="mateo.jpg" width="250" height="250" alt="Mateo Briones" />
</p>

* **Role:** Electronics Specialist  
* **Age:** 14  
* **Bio:** Two years ago in high school, I became interested in robotics and computer science, which led me to compete in RoboCup 2025. Since then, I've focused on this hobby and want to keep growing in it. In this competition, my goal is to place in the top three.

---

### Ruth García
<p align="center">
  <img src="ruth.jpg" width="250" height="250" alt="Ruth García" />
</p>

* **Role:** Builder  
* **Age:** 15  
* **Bio:** This is my first time being part of a robotics club, and I'm really excited to be here. I enjoy learning new things and working with technology. I'm motivated to keep improving my skills and to help the team succeed.

---

### Renato Medina
<p align="center">
  <img src="renato.jpg" width="250" height="250" alt="Renato Medina" />
</p>

* **Role:** Programmer and Captain  
* **Age:** 14  
* **Bio:** I started two years ago in elementary school at OnStage TMR, which sparked my interest in robotics. In this competition, my goal is to become a more well-rounded programmer.

---

## Project Overview

This project presents the development of an autonomous vehicle designed for the Future Engineers category of the World Robot Olympiad 2026. 

The robot currently focuses on completing the **Open Challenge**: navigating the track reliably using ultrasonic distance sensors and a closed-loop PD controller for steering. 

### Key System Features
* **Ultrasonic-Based Lane Centering:** Real-time distance tracking to maintain a straight trajectory.
* **Dedicated Steering System:** Closed-loop steering utilizing motor encoder values.
* **Automatic Calibration:** Software routines that eliminate manual alignment variations before a run.

> **Note:** The Obstacle Challenge subsystem (computer vision with a HuskyLens camera and Arduino Nano) is under early development and is documented separately below as *Planned / In Progress*.

---

## Vehicle Photos

<div align="center">

| Top View | Right Side |
| :---: | :---: |
| <img src="robot_top.jpg" width="300" alt="Robot Top View" /> | <img src="robot_right.jpg" width="300" alt="Robot Right Side" /> |

| Left Side | Bottom View |
| :---: | :---: |
| <img src="robot_left.jpg" width="300" alt="Robot Left Side" /> | <img src="robot_bottom.jpg" width="300" alt="Robot Bottom View" /> |

| Rear View |
| :---: |
| <img src="robot_rear.jpg" width="300" alt="Robot Rear View" /> |

</div>

---

## Components and Hardware

| Component | Description | Status |
| :--- | :--- | :--- |
| **LEGO MINDSTORMS EV3 Core Set (45544)** | Forms the structural chassis, drive motor, and steering assembly. Controlled via `ev3dev2`. | **In Use** |
| **2x Ultrasonic Sensors** | Mounted symmetrically on both sides of the chassis to track left and right wall distances. | **In Use** |
| **Arduino Nano** | ATmega328-based microcontroller utilized for offloading vision processing tasks. | **Planned** (Obstacle Subsystem) |
| **DFRobot HuskyLens AI Camera** | Vision sensor configured for colored pillar recognition and distance bounding. | **Planned** (Obstacle Subsystem) |

---

## Open Challenge: Control System

### Steering Mechanism
Steering is driven by a dedicated `MediumMotor` operated via **absolute encoder positions** instead of continuous time-based rotation. This approach yields precise, repeatable steering angles relative to a calculated center reference point.

### Automatic Steering Calibration
To account for varying initial wheel alignments between runs, the vehicle runs an automated calibration script at boot:
1. The steering motor drives fully left until it hits the physical mechanical boundary.
2. The motor drives fully right to the opposite mechanical limit.
3. The total step range is measured, and the exact mathematical center is calculated.
4. The motor returns to this center position and zeros its encoder count, creating a precise reference point.

### Sensor Offset Calibration
At startup, the vehicle takes initial resting readings from both side ultrasonic sensors. The difference between the left and right measurements is captured as an **offset** value. This value is mathematically subtracted from the error in the active control loop to compensate for minor physical mounting asymmetries.

### PD Control Loop
Lane centering is sustained through a Proportional-Derivative (PD) controller processing the distance error between the track walls:

```python
error = (right_distance - left_distance) - sensor_offset
derivative = (error - previous_error) / dt
output = (Kp * error) + (Kd * derivative)
```

The computed output maps directly to the target encoder position of the steering motor, clamped strictly to safe operational parameters to avoid mechanical strain.

| Parameter | Value | Purpose |
| :---: | :---: | :--- |
| **$K_p$** | 0.35 | Immediate correction proportional to path error |
| **$K_i$** | 0.00 | Disabled to avoid sensor noise windup and oscillation |
| **$K_d$** | 0.30 | Smooths steering reactions based on rate of error change |

---

## Obstacle Challenge (Planned)

The vehicle will be extended with an intelligent vision coprocessor subsystem to tackle the obstacle avoidance phase.

[HuskyLens Camera] ---> [Arduino Nano (via UART)] ---> [EV3 Brick] ---> [Actuators]
### Planned Control Logic
```python
# Conceptual loop under development
while True:
    if object_detected and width > threshold:
        # Vision Mode: Track pillar center displacement
        error = setpoint - x_position
    else:
        # Ultrasonic Mode: Center within track walls
        error = right_distance - left_distance
        
    # Process through common PD controller
    ...
```

---

## Engineering Decisions

* **Absolute Position Steering:** Shifting from continuous time-based motor control (`EV3-G`) to absolute encoder positions (`ev3dev2`) vastly enhanced steering accuracy and lap trajectory repetition.
* **Omission of Integral Term ($K_i$):** Early tests revealed that integrating ultrasonic distance data over time caused severe steering windup due to momentary sensor noise reflections. Keeping $K_i = 0$ kept the steering agile and stable.
* **Software-Based Offset Injection:** Rather than spending critical time physically rebuilding sensor brackets to achieve symmetry, applying a software calculation at boot cleanly resolved natural hardware build tolerances.

---

## Challenges & Limitations

### Overcome / In Progress
* Porting low-level block structures over to clean, object-oriented Python utilizing the `ev3dev2` libraries.
* Calibrating precise scaling factors between structural sensor errors and physical motor hub encoder turns.

### Current Limitations
* **Subsystem Integration:** The Arduino-to-EV3 serial connection for the HuskyLens tracking routine is undergoing structural redesign and is not yet field-operational.
* **Sensor Material Vulnerability:** Ultrasonic data can spike or drop based on the angle of incidence against specific wall materials, which requires software filtering logic to smooth out anomalous spikes.

---

## System Diagram

```mermaid
flowchart LR
    A[Ultrasonic Sensors] -->|Distance Data| B[EV3 Controller]
    B -->|PD Control Output| C[Steering Motor]
    B -->|Constant Speed| D[Drive Motor]
    
    style B fill:#f9f,stroke:#333,stroke-width:2px
```
