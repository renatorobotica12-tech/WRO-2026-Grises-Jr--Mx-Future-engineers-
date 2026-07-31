(**BETA DEL VERDADERO, TODAVIA MANTENEMOS EL ANTERIOR DEBIDO PORQUE TENEMOS Q TENER DE DONDE SACAR LAS IMAGENES, SIN EMBARGO DESPUES DE ESO LO BORRAREMOS**)

# Los Grises Jr

<p align="center">
  <!-- TODO: Replace with a YouTube video thumbnail or the main photo of the robot -->
  <img src="https://github.com/user-attachments/assets/6422e0d6-8cc2-4bbc-beaf-4bbada98c140" width="600">
</p>

<h2 align="center">
World Robot Olympiad 2026
<br>
Future Engineers Category
</h2>

<p align="center">

![WRO](https://img.shields.io/badge/WRO-2026-blue)
![Category](https://img.shields.io/badge/Category-Future%20Engineers-success)
![Controller](https://img.shields.io/badge/Main%20Controller-LEGO%20EV3-red)
![Coprocessor](https://img.shields.io/badge/Coprocessor-Arduino%20Nano-green)
![Vision](https://img.shields.io/badge/Vision-HuskyLens-orange)
![PCB](https://img.shields.io/badge/Electronics-Custom%20PCB-purple)
![Software](https://img.shields.io/badge/Software-EV3--G%20%2B%20Arduino-lightgrey)

</p>

---

# Official Repository

This repository contains the official engineering documentation of **Team Los Grises Jr** for the **World Robot Olympiad 2026 – Future Engineers Category**.

The objective of this repository is to document every stage of the engineering process, including mechanical design, electronics development, software architecture, autonomous control algorithms, and hardware evolution throughout the season.

---

# Table of Contents

- [Team](#team)
- [Project Overview](#project-overview)
- [Engineering Highlights](#engineering-highlights)
- [Robot Specifications](#robot-specifications)
- [Vehicle Gallery](#vehicle-gallery)
- [Components and Hardware](#components-and-hardware)
- [Mechanical Design](#mechanical-design)
- [Electronics](#electronics)
- [Custom PCB](#custom-pcb)
- [Software Architecture](#software-architecture)
- [Automatic Steering Calibration](#automatic-steering-calibration)
- [Sensor Calibration](#sensor-calibration)
- [PD Steering Controller](#pd-steering-controller)
- [Finite State Machine](#finite-state-machine)
- [Engineering Decisions](#engineering-decisions)
- [Current Performance](#current-performance)
- [Future Improvements](#future-improvements)
- [Engineering Journal](#engineering-journal)
- [Repository Structure](#repository-structure)

---

# Team

## Team Photo

<p align="center">

<!-- TODO: Insert team photo -->

<img src="YOUR_TEAM_PHOTO" width="700">

</p>

---

## Team Members

<table>
<tr>

<td align="center" width="50%">

<!-- TODO: Replace with Renato's picture -->

<img src="https://github.com/user-attachments/assets/dd9e997b-65a7-4909-8207-ea3630b5aff4" width="220">

### Renato Medina

**Team Captain**

**Primary Roles**

Software Development

Mechanical Design

Robot Integration

Project Documentation

System Architecture

**Age:** 14

</td>

<td align="center" width="50%">

<!-- TODO: Replace with Paulina's picture -->

<img src="PAULINA_PHOTO" width="220">

### Paulina

**Mechanical & Electronics Designer**

**Primary Roles**

Mechanical Assembly

Electronics Integration

PCB Installation

Robot Testing

Structural Optimization

</td>

</tr>
</table>

---

### Renato Medina

Renato serves as the **Team Captain** and is responsible for the overall software architecture, autonomous navigation algorithms, project documentation, and system integration.

His robotics journey began through the **OnStage TMR** program, where he discovered a strong interest in autonomous systems, embedded programming, and engineering design. Since then, he has focused on developing reliable robotic systems by combining software, electronics, and mechanical engineering.

For WRO 2026, his objective is to design a highly reliable autonomous vehicle while expanding his knowledge of embedded systems, control theory, and robotic engineering.

---

### Paulina

Paulina is responsible for the robot's mechanical construction and electronic integration.

Her work focuses on the structural assembly of the robot, PCB installation, sensor integration, and ensuring the mechanical reliability of every subsystem throughout testing and development.

Her contributions have been fundamental in transforming the initial prototype into the team's final competition robot.

---

# Team Responsibilities

| Area | Renato | Paulina |
|:------------------------------|:------:|:-------:|
| Mechanical Design | ✅ | ✅ |
| Robot Assembly | ✅ | ✅ |
| Electronics Integration |  | ✅ |
| PCB Installation | ✅ | ✅ |
| Software Development | ✅ | |
| EV3 Programming | ✅ | |
| Arduino Programming | ✅ | |
| Documentation | ✅ | ✅ |
| Testing & Validation | ✅ | ✅ |

---

# Project Overview

Our robot is a fully autonomous four-wheeled vehicle designed for the **World Robot Olympiad 2026 Future Engineers** competition.

The current platform combines an Ackermann steering system, rear-wheel drive, five ultrasonic sensors, a HuskyLens AI camera, an Arduino Nano coprocessor, and a custom-designed PCB to achieve reliable autonomous navigation.

The software architecture is based on modular design principles and currently includes automatic steering calibration, sensor calibration, a closed-loop PD steering controller, and a Finite State Machine (FSM) that manages the robot's driving behavior.

Throughout the development process, special attention has been given to repeatability, electrical reliability, mechanical stability, and ease of maintenance.

---

# Engineering Highlights

The current version of the robot incorporates several engineering improvements developed specifically for the Future Engineers challenge.

- ✅ Ackermann steering geometry
- ✅ Rear-wheel drive
- ✅ Five ultrasonic sensors
- ✅ HuskyLens AI vision sensor
- ✅ Arduino Nano coprocessor
- ✅ Custom-designed PCB
- ✅ I²C communication architecture
- ✅ Automatic steering calibration
- ✅ Closed-loop PD steering controller
- ✅ Modular software architecture
- ✅ Finite State Machine (FSM)
- ✅ 3D-printed sensor mounts
- ✅ Optimized center of gravity
- ✅ Improved cable management

---

# Robot Specifications

| Specification | Value |
|------------------------------|-------------------------------|
| Competition | WRO Future Engineers 2026 |
| Robot Type | Autonomous Vehicle |
| Dimensions | **24 × 23 × 18 cm** |
| Maximum Allowed Size | **30 × 30 × 30 cm** |
| Steering System | Ackermann Steering |
| Drive System | Rear-Wheel Drive |
| Chassis | LEGO Mindstorms EV3 |
| Main Controller | LEGO EV3 Brick |
| Coprocessor | Arduino Nano |
| Vision System | HuskyLens AI Camera |
| Distance Sensors | 5 Ultrasonic Sensors |
| Communication | I²C |
| Custom Electronics | Custom PCB |
| Sensor Supports | 3D Printed |
| Programming Languages | EV3-G & Arduino C++ |

---

# Vehicle Gallery

> **Note:** A demonstration video will be added once final testing has been completed.


| Top View | Right Side | Left Side |
|:---------:|:----------:|:---------:|
| <img src="https://github.com/user-attachments/assets/4440147d-9600-491b-a967-1af42e869efa" width="220"> | <img src="https://github.com/user-attachments/assets/d07e3bec-f223-4d49-a879-2c7a64f843c3" width="220"> | <img src="https://github.com/user-attachments/assets/36231890-177c-4a6f-8faf-0d1627496dcb" width="220"> |

| Bottom View | Rear View | Perspective |
|:-----------:|:---------:|:-----------:|
| <img src="https://github.com/user-attachments/assets/47117a61-1927-4884-a85a-d80c9e8139e6" width="220"> | <img src="https://github.com/user-attachments/assets/5d44d4db-c581-44e0-86bb-8d20cec6b4b8" width="220"> | <img src="PERSPECTIVE_VIEW" width="220"> |

---

# Components and Hardware

| Component | Quantity | Purpose | Status |
|------------|:-------:|------------------------------|:------:|
| LEGO EV3 Brick | 1 | Main controller | ✅ |
| EV3 Large Motor | 1 | Rear-wheel traction | ✅ |
| EV3 Medium Motor | 1 | Ackermann steering | ✅ |
| Ultrasonic Sensors | 5 | Distance measurement | ✅ |
| Arduino Nano | 1 | Sensor acquisition & I²C communication | ✅ |
| HuskyLens AI Camera | 1 | Obstacle detection | ✅ |
| Custom PCB | 1 | Power and signal distribution | ✅ |
| LEGO Wheels | 4 | Vehicle mobility | ✅ |
| 3D Printed Supports | Multiple | Sensor mounting | ✅ |

---
# Mechanical Design

The mechanical design of our robot was developed through multiple iterations, each focused on improving stability, repeatability, and ease of maintenance while remaining fully compliant with the World Robot Olympiad Future Engineers regulations.

Unlike our initial prototype, the final robot features a more robust chassis with a significantly improved weight distribution and a cleaner sensor layout. The redesign increased structural rigidity while providing additional space for electronics, resulting in a vehicle that resembles a compact SUV rather than a conventional LEGO car.

One of our primary design constraints was the maximum permitted robot size of **30 × 30 × 30 cm**. Throughout the development process we continuously verified the dimensions to ensure compliance.

### Final Dimensions

| Measurement | Value |
|--------------|-------|
| Length | **24 cm** |
| Width | **23 cm** |
| Height | **18 cm** |

The completed robot comfortably satisfies the competition requirements while providing sufficient internal space for electronics, sensor routing, and future upgrades.

---

## Weight Distribution

Achieving a balanced center of gravity was one of our main mechanical objectives.

Instead of placing every component near the front of the vehicle, we intentionally distributed the mass across the chassis.

### Main Design Decisions

- The EV3 Brick was positioned at the rear of the robot.
- The drive motor was installed close to the center of the chassis.
- The steering motor was mounted directly above the steering mechanism.
- The custom PCB was located near the sensor assembly to minimize cable lengths.
- The Arduino Nano was positioned adjacent to the PCB to simplify communication routing.

This configuration improves stability during acceleration, braking, and cornering while reducing unwanted chassis oscillations.

---

## Ackermann Steering System

The robot uses an Ackermann-inspired steering mechanism powered by an EV3 Medium Motor.

Unlike differential steering, the Ackermann geometry allows the vehicle to follow smoother trajectories by reducing tire slip during turns.

Rather than continuously rotating the steering motor, steering commands are generated using **absolute encoder positions**.

This approach provides several important advantages:

- Highly repeatable steering angles
- Faster response
- Improved trajectory accuracy
- Automatic steering centering
- Reduced cumulative positioning error

The steering angle is limited in software to prevent mechanical overtravel and protect the transmission.

---

## Rear-Wheel Drive

Traction is provided through a rear-wheel drive configuration.

This layout was selected because it offers several engineering advantages for the Future Engineers challenge:

- Better weight transfer during acceleration
- Simpler drivetrain
- Improved mechanical reliability
- Lower steering interference
- Easier maintenance

---

## Sensor Mounts

All ultrasonic sensors are installed using custom-designed 3D printed brackets.

These supports were specifically designed to:

- Improve alignment accuracy
- Reduce vibration
- Increase rigidity
- Simplify installation
- Ensure repeatable sensor positioning

By fixing every sensor in a rigid position, measurement consistency is significantly improved compared to directly attaching sensors to LEGO beams.

---

# Electronics

The robot combines LEGO electronics with custom embedded hardware in order to create a modular and reliable electrical architecture.

Instead of connecting every sensor directly to the EV3 Brick, the system uses an Arduino Nano together with a custom-designed PCB to simplify wiring and centralize sensor management.

This hybrid architecture reduces cable complexity while improving maintainability and electrical reliability.

---

## Electronic Architecture

```text
          Ultrasonic Sensors
       ┌────┬────┬────┬────┬────┐
       │    │    │    │    │    │
       └────┴────┴────┴────┴────┘
                 │
                 ▼
          Custom PCB
                 │
                 ▼
          Arduino Nano
                 │
              I²C Bus
                 │
                 ▼
            LEGO EV3
                 │
        Steering & Drive Motors
```

---

# Custom PCB

<p align="center">

<!-- TODO -->
<!-- Insert PCB Render -->

<img src="PCB_RENDER" width="500">

</p>

<p align="center">

<!-- TODO -->
<!-- Insert Real PCB -->

<img src="PCB_PHOTO" width="500">

</p>

One of the most significant engineering improvements introduced during the season was the development of a fully custom Printed Circuit Board (PCB).

The PCB was designed specifically for our robot to replace large bundles of individual wires with a compact and organized electrical distribution system.

Rather than acting solely as a connector board, it serves as the central interface between the ultrasonic sensors and the Arduino Nano.

---

## Why We Designed a Custom PCB

During early testing, we observed several issues caused by direct sensor wiring:

- Excessive cable clutter
- Loose connections
- Difficult maintenance
- Limited available EV3 ports
- Reduced mechanical organization

To solve these problems, we designed and manufactured a dedicated PCB specifically for this project.

---

## Main Functions

The PCB performs several important tasks:

- Power distribution
- Signal routing
- Sensor connectors
- Arduino Nano interface
- Simplified cable management
- Easy maintenance
- Improved electrical reliability

The board also allows every sensor to be disconnected independently without affecting the remaining electronics.

---

## PCB Advantages

Compared to individual wiring, the custom PCB provides:

- Cleaner internal organization
- Reduced assembly time
- Better troubleshooting
- Greater mechanical robustness
- Lower probability of accidental disconnections
- Professional electrical integration

---

# Communication System

Communication between the Arduino Nano and the EV3 Brick is performed through the **I²C protocol**.

Instead of dedicating multiple EV3 input ports to ultrasonic sensors, the Arduino collects sensor measurements and transmits the processed data through a single communication channel.

This architecture greatly simplifies the robot's electrical design.

```text
Ultrasonic Sensors
        │
        ▼
Arduino Nano
        │
      I²C
        │
        ▼
LEGO EV3 Brick
```

Advantages include:

- Reduced wiring complexity
- Fewer occupied EV3 ports
- Easier maintenance
- Improved scalability
- Cleaner software architecture

---

# Software Architecture

The robot software follows a modular architecture in which each subsystem is responsible for a specific task.

This separation simplifies debugging, maintenance, and future development while allowing every module to be tested independently.

```text
                 START
                   │
                   ▼
      Automatic Steering Calibration
                   │
                   ▼
         Ultrasonic Sensor Reading
                   │
                   ▼
          Sensor Calibration
                   │
                   ▼
           PD Controller
                   │
                   ▼
      Finite State Machine (FSM)
                   │
                   ▼
      Steering & Motion Commands
                   │
                   ▼
               EV3 Motors
```

---

## Software Modules

| Module | Function |
|----------|----------|
| Sensor Acquisition | Reads all ultrasonic sensors |
| Steering Calibration | Automatically centers the steering |
| Sensor Calibration | Removes mechanical offsets |
| PD Controller | Keeps the robot centered |
| Motion Controller | Controls vehicle movement |
| Finite State Machine | Selects robot behavior |
| Safety Functions | Prevents invalid steering angles |

The modular design allows individual components to be modified without affecting the remaining software, making future improvements significantly easier.
---
# Automatic Steering Calibration

Every autonomous run begins with a fully automatic steering calibration routine.

Rather than relying on manual alignment before each attempt, the robot determines its steering reference by detecting the mechanical limits of the steering mechanism. This guarantees that every run starts from the same steering position, improving repeatability and eliminating human error.

The calibration process follows these steps:

1. Rotate the steering motor toward the left mechanical limit.
2. Rotate toward the right mechanical limit.
3. Measure the total steering travel.
4. Calculate the midpoint of the steering range.
5. Move the steering motor to the calculated center.
6. Reset the motor encoder to zero.

```text
Left Limit
     │
     ▼
Right Limit
     │
     ▼
Measure Range
     │
     ▼
Calculate Center
     │
     ▼
Move to Center
     │
     ▼
Reset Encoder
```

This routine allows the robot to maintain consistent steering behavior throughout multiple consecutive runs without requiring manual adjustments.

---

# Sensor Calibration

Even when ultrasonic sensors are manufactured identically, small variations in mechanical assembly can introduce slight measurement differences.

To compensate for these tolerances, the robot performs an automatic sensor calibration at startup.

While positioned approximately at the center of the track, the software records the distance measured by both side ultrasonic sensors and computes an offset value.

```text
Sensor Offset

offset = Right Sensor - Left Sensor
```

During every control cycle, this offset is removed from the measured error.

```text
Corrected Error

error = (Right Distance - Left Distance) - Offset
```

This simple procedure significantly improves lane-centering accuracy while compensating for minor construction differences.

---

# PD Steering Controller

The steering controller is based on a **Proportional–Derivative (PD)** algorithm.

The controller continuously compares the distances measured by the left and right ultrasonic sensors.

Whenever the robot deviates from the center of the lane, the controller generates a steering correction proportional to the measured error.

The derivative component predicts the error variation, reducing oscillations and improving overall stability.

The controller equations are:

```text
error = (right_distance - left_distance) - sensor_offset

derivative = (error - previous_error) / dt

output = KP × error + KD × derivative
```

Current controller constants:

| Constant | Value |
|----------|------:|
| KP | 0.35 |
| KI | 0.00 |
| KD | 0.30 |

The integral term is intentionally disabled because ultrasonic sensors naturally introduce small fluctuations that could accumulate over time and reduce steering stability.

The controller output is converted directly into a steering angle while remaining inside predefined mechanical limits.

---

# Finite State Machine

The robot software is organized around a **Finite State Machine (FSM)**.

Instead of executing a single control algorithm throughout the entire run, the robot changes its behavior depending on the current driving situation.

This architecture makes the software easier to maintain, extend, and debug.

Current FSM states include:

```text
START
   │
   ▼
CALIBRATION
   │
   ▼
OPEN CHALLENGE
   │
   ├───────────────┐
   ▼               │
STRAIGHT           │
   │               │
   ▼               │
TURN               │
   │               │
   └───────────────┘
```

Future versions will include additional states dedicated to obstacle detection, overtaking maneuvers, and dynamic speed control.

---

# Engineering Decisions

Every major design choice was based on practical testing and iterative improvements.

| Engineering Decision | Reason |
|----------------------|--------|
| Ackermann Steering | Produces smoother and more realistic turning geometry while reducing wheel slip. |
| Rear-Wheel Drive | Improves traction and simplifies the drivetrain. |
| Encoder-Based Steering | Provides repeatable steering angles and automatic calibration. |
| Five Ultrasonic Sensors | Increases environmental awareness and measurement redundancy. |
| Arduino Nano Coprocessor | Offloads sensor management from the EV3 Brick. |
| I²C Communication | Reduces EV3 port usage and simplifies wiring. |
| Custom PCB | Improves electrical reliability and cable organization. |
| 3D Printed Sensor Mounts | Increases structural rigidity and measurement consistency. |
| Modular Software Architecture | Simplifies debugging and future upgrades. |
| PD Controller | Provides fast and stable lane-centering performance without unnecessary complexity. |

---

# Current Performance

Current testing demonstrates the following results:

- Stable lane-centering performance.
- Smooth steering corrections.
- Reliable automatic steering calibration.
- Consistent multi-lap repeatability.
- Improved electrical reliability after PCB integration.
- Reduced wiring complexity.
- Stable communication between the Arduino Nano and EV3.
- Robust mechanical assembly suitable for repeated testing.

Although software optimization is still in progress, the robot already demonstrates a reliable hardware platform for future development.

---

# Future Improvements

The current robot represents the foundation for future development.

Planned improvements include:

- Complete Obstacle Challenge implementation.
- Full HuskyLens integration.
- Dynamic speed controller.
- Enhanced Finite State Machine.
- Sensor fusion techniques.
- Improved obstacle avoidance algorithms.
- Additional software optimization.
- Further mechanical refinement.
- Final cable management improvements.

---

# Engineering Journal

The complete engineering process has been documented chronologically in a dedicated journal.

Every hardware modification, software improvement, engineering decision, and design iteration is described in detail.

📄 **Engineering Journal**

```
docs/engineering_journal.md
```

---

# Repository Structure

```text
.
├── docs
│   ├── engineering_journal.md
│   ├── mechanical_design.md
│   ├── electronics.md
│   └── software.md
│
├── images
│   ├── robot
│   ├── pcb
│   ├── team
│   └── development
│
├── models
│   ├── chassis.stl
│   ├── sensor_mount.stl
│   └── pcb
│
├── src
│   ├── EV3-G
│   ├── Arduino
│   └── Pseudocode
│
└── README.md
```

---

# Development Timeline

| Date | Milestone |
|------|-----------|
| 4 Jul 2026 | Initial PD controller prototype |
| 8 Jul 2026 | PCB manufacturing |
| 10 Jul 2026 | PCB assembly and testing |
| 13 Jul 2026 | FSM implementation |
| 21 Jul 2026 | I²C communication completed |
| 27 Jul 2026 | Final hardware integration |
| 28 Jul 2026 | Final robot assembly |

For a complete description of each milestone, please refer to the **Engineering Journal**.

---

# Acknowledgements

We would like to thank our mentors, teachers, and everyone who supported the development of this project throughout the WRO 2026 season.

Their guidance, encouragement, and technical advice have been essential in helping us transform an initial concept into a functional autonomous vehicle.

---

# Conclusion

The current version of the **Los Grises Jr** robot is the result of an iterative engineering process involving mechanical design, electronics development, embedded programming, and autonomous control.

Compared to our earliest prototypes, the final vehicle incorporates a custom-designed PCB, optimized weight distribution, encoder-based Ackermann steering, automatic steering calibration, and a modular software architecture that significantly improves reliability and repeatability.

Future work will focus on completing the Obstacle Challenge while preserving the robustness achieved during Open Challenge testing.

The team remains committed to continuously improving both the hardware and software, applying engineering principles throughout every stage of development.

---

<p align="center">

**Team Los Grises Jr**

*World Robot Olympiad 2026 – Future Engineers*

</p>


