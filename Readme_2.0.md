# Los Grises Jr

# World Robot Olympiad 2026
## Future Engineers Category

<div align="center">

**Controller** • **Coprocessor** • **Vision** • **PCB** • **Software**

</div>

---

# Official Repository

This repository contains the complete engineering documentation of **Team Los Grises Jr** for the **World Robot Olympiad (WRO) 2026 – Future Engineers** category.

The objective of this repository is to document the complete development process of our autonomous vehicle, including its mechanical design, electronic architecture, embedded software, control algorithms, and the engineering decisions made throughout the season.

Rather than presenting only the final robot, this repository describes the complete design evolution, highlighting the challenges encountered, the solutions implemented, and the reasoning behind every major improvement.

---

# Table of Contents

- Team
- Project Overview
- Engineering Highlights
- Robot Specifications
- Vehicle Gallery
- Components and Hardware
- Mechanical Design
- Electronics
- Custom PCB
- Software Architecture
- Automatic Steering Calibration
- Sensor Calibration
- PD Steering Controller
- Finite State Machine
- Engineering Decisions
- Current Performance
- Future Improvements
- Engineering Journal
- Repository Structure

---

# Team

## Team Photo

*(Insert team photo here.)*

---

## Team Members

### Renato Medina
**Team Captain**

**Primary Responsibilities**

- Software Development
- Mechanical Design
- Embedded Programming
- System Integration
- Robot Architecture
- Project Documentation

**Age:** 14

---

### Paulina

**Mechanical & Electronics Designer**

**Primary Responsibilities**

- Mechanical Assembly
- Electronics Integration
- PCB Installation
- Robot Testing
- Structural Optimization

---

## Renato Medina

Renato serves as the team captain and leads the software and system integration of the project.

His responsibilities include the development of the robot's software architecture, autonomous navigation algorithms, embedded programming, mechanical design, and technical documentation.

His interest in robotics began through the **OnStage TMR** program, where he developed a strong passion for autonomous systems and engineering design. Since then, he has focused on combining software, electronics, and mechanical engineering to build reliable autonomous robots.

For the 2026 WRO season, his primary objective is to develop a robust autonomous vehicle while expanding his knowledge of embedded systems, control theory, and robotic engineering.

---

## Paulina

Paulina is responsible for the robot's mechanical construction and electronic integration.

Her work includes structural assembly, sensor installation, PCB integration, wiring organization, and mechanical validation throughout the development process.

Her contributions have been fundamental in transforming the initial prototype into a reliable competition-ready robot by improving both structural rigidity and assembly quality.

---

# Team Responsibilities

| Area | Renato | Paulina |
|:--------------------------|:------:|:-------:|
| Mechanical Design | ✅ | ✅ |
| Robot Assembly | ✅ | ✅ |
| Electronics Integration | | ✅ |
| PCB Installation | ✅ | ✅ |
| Software Development | ✅ | |
| EV3 Programming | ✅ | |
| Arduino Programming | ✅ | |
| Documentation | ✅ | ✅ |
| Testing & Validation | ✅ | ✅ |

---

# Project Overview

Our robot is a fully autonomous four-wheel vehicle developed for the **World Robot Olympiad Future Engineers** competition.

The platform combines an **Ackermann steering system**, **rear-wheel drive**, **five ultrasonic sensors**, a **HuskyLens AI vision camera**, an **Arduino Nano coprocessor**, and a **custom-designed PCB** to create a compact, modular, and reliable autonomous system.

Instead of connecting every sensor directly to the EV3 Brick, the robot employs a distributed electronic architecture in which the Arduino Nano acquires and processes sensor measurements before transmitting the required information through an I²C communication bus. This approach simplifies wiring, reduces EV3 port usage, and improves system maintainability.

The software is organized into independent modules responsible for steering calibration, sensor calibration, autonomous navigation, and motion control. A Finite State Machine (FSM) coordinates the robot's behavior while closed-loop PD controllers continuously adjust the steering according to the surrounding environment.

Throughout the season, every subsystem has been iteratively refined with three primary engineering objectives:

- Increase system reliability.
- Improve repeatability between runs.
- Simplify maintenance and future development.

---

# Engineering Highlights

The current version of the robot incorporates several engineering improvements developed specifically for the WRO Future Engineers challenge.

| Feature | Description |
|:-------------------------------|:------------------------------------------------|
| Steering System | Ackermann steering geometry |
| Drive System | Rear-wheel drive |
| Distance Sensors | Five ultrasonic sensors |
| Vision System | HuskyLens AI camera |
| Coprocessor | Arduino Nano |
| Custom Electronics | Custom-designed PCB |
| Communication | I²C architecture |
| Steering Calibration | Automatic encoder-based calibration |
| Navigation Controller | Closed-loop PD steering controller |
| Software Architecture | Modular software design |
| Decision System | Finite State Machine (FSM) |
| Sensor Mounts | Custom 3D-printed supports |
| Mechanical Design | Optimized weight distribution |
| Electrical Design | Organized cable management |

---

# Robot Specifications

| Specification | Value |
|:----------------------------|:--------------------------------|
| Competition | WRO Future Engineers 2026 |
| Robot Type | Autonomous Vehicle |
| Dimensions | 24 × 23 × 18 cm |
| Maximum Allowed Size | 30 × 30 × 30 cm |
| Steering System | Ackermann Steering |
| Drive System | Rear-Wheel Drive |
| Chassis | LEGO Mindstorms EV3 |
| Main Controller | LEGO EV3 Brick |
| Coprocessor | Arduino Nano |
| Vision System | HuskyLens AI Camera |
| Distance Sensors | Five Ultrasonic Sensors |
| Communication Protocol | I²C |
| Custom Electronics | Custom PCB |
| Sensor Mounts | 3D-Printed |

---
# Vehicle Gallery

The images below show the final competition vehicle from multiple perspectives.

These photographs illustrate the overall mechanical design, sensor placement, wiring organization, and integration of the different hardware subsystems.

> **Note:** A demonstration video will be added after the final validation tests have been completed.

| Top View | Right Side | Left Side |
|----------|------------|-----------|
| *(Image)* | *(Image)* | *(Image)* |

| Bottom View | Rear View | Front View |
|-------------|-----------|------------|
| *(Image)* | *(Image)* | *(Image)* |

---

# Components and Hardware

The robot combines LEGO components with custom-designed electronics to create a modular and reliable autonomous platform.

Each component was selected according to its functionality, reliability, and compatibility with the overall system architecture.

| Component | Quantity | Function | Status |
|:----------------------|:-------:|:---------------------------------------------|:------:|
| LEGO EV3 Brick | 1 | Main controller | ✅ |
| EV3 Large Motor | 1 | Rear-wheel traction | ✅ |
| EV3 Medium Motor | 1 | Ackermann steering | ✅ |
| Ultrasonic Sensors | 5 | Distance measurement | ✅ |
| Arduino Nano | 1 | Sensor acquisition and I²C communication | ✅ |
| HuskyLens AI Camera | 1 | Obstacle detection | ✅ |
| Custom PCB | 1 | Power and signal distribution | ✅ |
| LEGO Wheels | 4 | Vehicle mobility | ✅ |
| 3D Printed Supports | Multiple | Sensor mounting | ✅ |

---

# Mechanical Design

The mechanical structure of the robot was developed through multiple design iterations, each focused on improving structural rigidity, weight distribution, ease of maintenance, and overall driving performance.

Rather than modifying a single prototype, the robot evolved progressively as new engineering challenges were identified during testing. Every redesign addressed specific limitations observed in previous versions, resulting in a platform that is significantly more robust and reliable than the initial concept.

A major design constraint throughout development was compliance with the official **WRO Future Engineers** regulations, particularly the maximum robot dimensions of **30 × 30 × 30 cm**. Every iteration was carefully verified to ensure full compliance while maximizing the available internal space for electronics and future upgrades.

---

## Final Dimensions

| Measurement | Value |
|:-----------|:------|
| Length | 24 cm |
| Width | 23 cm |
| Height | 18 cm |

The final design remains comfortably within the competition limits while providing sufficient space for the steering mechanism, electronic components, sensor routing, and future hardware improvements.

---

# Weight Distribution

A balanced center of gravity was considered one of the most important aspects of the mechanical design.

Instead of concentrating all components at the front of the vehicle, the mass was intentionally distributed across the chassis to improve stability during acceleration, braking, and cornering.

The main design decisions include:

- Positioning the EV3 Brick at the rear of the chassis.
- Installing the drive motor near the center of the vehicle.
- Mounting the steering motor directly above the steering linkage.
- Locating the custom PCB close to the ultrasonic sensors to minimize cable lengths.
- Placing the Arduino Nano adjacent to the PCB to simplify electrical routing.

This configuration reduces unwanted chassis oscillations, improves vehicle balance, and contributes to more consistent driving performance.

---

# Ackermann Steering System

The robot employs an Ackermann-inspired steering mechanism driven by an EV3 Medium Motor.

Unlike differential-drive robots, the Ackermann geometry enables smoother and more realistic vehicle motion by reducing tire slip during cornering and allowing both front wheels to follow more natural trajectories.

Steering commands are generated using the motor's encoder position rather than continuous motor rotation. This approach offers several important advantages:

- Highly repeatable steering angles.
- Accurate steering positioning.
- Faster steering response.
- Automatic steering centering.
- Reduced cumulative positioning error.

To protect the steering mechanism from mechanical overtravel, the steering angle is limited by software before motor commands are applied.

---

# Rear-Wheel Drive

Vehicle propulsion is provided by a rear-wheel-drive configuration powered by a single EV3 Large Motor.

This drivetrain was selected because it provides several practical advantages for the Future Engineers challenge:

- Better traction during acceleration.
- Reduced interference with the steering system.
- Simpler mechanical transmission.
- Improved reliability.
- Easier maintenance.

Separating the steering and traction systems also simplifies software control and makes vehicle behavior more predictable during autonomous navigation.

---

# Sensor Mounts

All ultrasonic sensors are installed using custom-designed 3D-printed brackets.

These supports were specifically designed to ensure that every sensor remains rigidly aligned throughout testing and competition.

Compared to mounting the sensors directly on LEGO beams, the printed brackets provide several advantages:

- Improved alignment accuracy.
- Increased structural rigidity.
- Reduced vibration.
- Simplified installation.
- Consistent sensor positioning.

Maintaining fixed sensor positions significantly improves measurement repeatability and contributes to more stable autonomous navigation.
# Electronics

The robot combines LEGO electronics with custom embedded hardware to create a modular, reliable, and easy-to-maintain electrical architecture.

Instead of connecting every sensor directly to the EV3 Brick, the system distributes processing tasks between two controllers. The EV3 Brick acts as the primary controller responsible for navigation, motion control, and decision-making, while an Arduino Nano operates as a dedicated coprocessor responsible for sensor acquisition and communication.

This distributed architecture reduces the computational load on the EV3, simplifies wiring, minimizes occupied input ports, and makes future hardware expansions considerably easier.

The result is a cleaner electrical system that improves reliability, maintenance, and debugging throughout the development process.

---

# Electronic Architecture

```
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
          LEGO EV3 Brick
                │
     Steering & Drive Motors
```

The architecture separates sensing, processing, and actuation into independent modules. This modular approach simplifies maintenance and allows each subsystem to be tested individually without affecting the rest of the robot.

---

# Custom PCB

One of the most significant improvements introduced during this season was the development of a custom Printed Circuit Board (PCB).

During the early stages of development, each ultrasonic sensor was connected individually using jumper wires. Although functional, this solution quickly became difficult to maintain as additional sensors and electronics were incorporated into the robot.

Long cable runs increased assembly time, complicated troubleshooting, and reduced the overall mechanical organization of the vehicle.

To address these issues, we designed a dedicated PCB specifically for this project.

Rather than acting only as a breakout board, the PCB serves as the electrical backbone of the robot, centralizing power distribution, signal routing, and sensor connections while providing a dedicated interface for the Arduino Nano.

This significantly improves assembly quality while reducing wiring complexity and the probability of accidental disconnections.

---

## Why We Designed a Custom PCB

The PCB was developed after identifying several limitations in the original wiring approach:

- Excessive cable clutter.
- Loose electrical connections.
- Difficult maintenance.
- Limited EV3 input ports.
- Poor internal organization.

Replacing individual wiring with a dedicated PCB resulted in a cleaner, more reliable, and easier-to-maintain electrical system.

---

## Main Functions

The custom PCB performs several essential functions within the robot:

- Power distribution.
- Signal routing.
- Ultrasonic sensor connections.
- Arduino Nano interface.
- I²C communication routing.
- Simplified cable management.
- Easier maintenance.

Each ultrasonic sensor can be disconnected independently without affecting the remaining electronics, making diagnostics and repairs considerably faster during testing.

---

## PCB Advantages

Compared to the previous wiring solution, the custom PCB provides several engineering advantages:

- Cleaner internal organization.
- Reduced assembly time.
- Faster troubleshooting.
- Greater mechanical robustness.
- Lower probability of accidental disconnections.
- Improved electrical reliability.
- Simplified future hardware upgrades.

Beyond improving aesthetics, the PCB increases the repeatability and maintainability of the entire electrical system, making it better suited for repeated competition runs.

---
# Communication System

Communication between the Arduino Nano and the LEGO EV3 Brick is established through the I²C protocol.

Instead of connecting each ultrasonic sensor directly to the EV3, the Arduino Nano continuously acquires data from all five sensors, organizes the measurements, and transmits the processed information through a single I²C channel.

This architecture significantly reduces the number of occupied EV3 input ports while simplifying both the electrical wiring and the software responsible for sensor management.

```
Ultrasonic Sensors
        │
        ▼
   Arduino Nano
        │
  Reads all sensors
        │
Processes measurements
        │
      I²C Bus
        │
        ▼
   LEGO EV3 Brick
        │
 Decision & Control
        │
        ▼
 Steering and Drive Motors
```

By separating sensor acquisition from vehicle control, the EV3 can dedicate its processing resources to navigation and decision-making while the Arduino handles low-level communication with the sensors.

This modular architecture offers several engineering advantages:

- Reduced wiring complexity.
- Lower EV3 port usage.
- Simplified software development.
- Improved scalability.
- Faster troubleshooting.
- Easier hardware maintenance.

---

# Software Architecture

The robot software was designed following a modular architecture, where each subsystem performs a specific task independently.

Instead of implementing all functionalities within a single program, the software is divided into specialized modules responsible for sensing, calibration, control, and navigation.

This organization simplifies debugging, improves code readability, and allows individual modules to be modified or tested without affecting the remaining system.

The complete execution sequence is illustrated below.

```
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
     Finite State Machine (FSM)
                   │
                   ▼
   Select Navigation Controller
                   │
          ┌────────┴────────┐
          ▼                 ▼
    Turn Controller   Corridor Controller
          │                 │
          └────────┬────────┘
                   ▼
          Steering Commands
                   │
                   ▼
            EV3 Motors
```

Each module has a clearly defined responsibility within the navigation process.

| Module | Function |
|:--------------------------|:------------------------------------------------|
| Sensor Acquisition | Reads the five ultrasonic sensors through the Arduino Nano |
| Steering Calibration | Automatically centers the steering mechanism |
| Sensor Calibration | Compensates for installation offsets |
| Finite State Machine | Selects the navigation strategy |
| Turn Controller | PD controller optimized for cornering |
| Corridor Controller | PD controller optimized for straight corridors |
| Motion Controller | Controls vehicle speed and steering |
| Safety Functions | Prevents invalid steering commands |

This modular structure makes future improvements considerably easier, since each subsystem can evolve independently without requiring major modifications to the rest of the software.

---

# Automatic Steering Calibration

To ensure consistent steering behavior, every autonomous run begins with an automatic steering calibration routine.

Rather than relying on manual alignment before each attempt, the robot determines the center position of the steering mechanism automatically using the motor encoder.

The calibration procedure consists of locating both mechanical limits of the steering system, measuring the total steering travel, calculating the midpoint, and finally positioning the steering motor at the calculated center.

This process guarantees that every run starts from the same steering reference, eliminating operator-dependent errors and improving repeatability.

The calibration sequence is shown below.

```
Left Mechanical Limit
         │
         ▼
Right Mechanical Limit
         │
         ▼
Measure Steering Range
         │
         ▼
Calculate Center Position
         │
         ▼
Move to Center
         │
         ▼
Reset Encoder
```

After calibration, the steering encoder is reset to zero, establishing a common reference for all subsequent steering commands.

This routine provides several advantages:

- Consistent steering alignment before every run.
- Improved trajectory repeatability.
- Elimination of manual adjustments.
- Reduced cumulative steering errors.
- Increased navigation accuracy.

Because the steering reference is generated automatically, the robot maintains stable behavior even after repeated testing sessions or mechanical disassembly.
# Sensor Calibration

Although the ultrasonic sensors are identical models, small variations in their installation and mechanical positioning can introduce slight measurement differences.

To compensate for these tolerances, the robot performs an automatic sensor calibration during initialization.

While the robot is positioned approximately at the center of the track, the distances measured by the left and right ultrasonic sensors are recorded. The difference between these measurements is stored as a correction offset.

```
Sensor Offset

offset = Right Sensor − Left Sensor
```

During every control cycle, this offset is removed from the measured error before the steering controller is executed.

```
Corrected Error

error = (Right Distance − Left Distance) − Offset
```

By compensating for installation tolerances, the controller receives a more accurate estimate of the vehicle's lateral position, resulting in smoother steering corrections and improved lane-centering performance.

The calibration procedure also reduces the need for manual sensor alignment after maintenance or hardware modifications.

---

# Dual PD Steering Controller

The steering system is controlled by a closed-loop **Proportional-Derivative (PD)** controller.

Instead of using a single set of control parameters throughout the entire course, the robot implements **two independent PD controllers**, each optimized for a different driving condition.

The active controller is selected dynamically according to the distance measured by the ultrasonic sensors through the I²C communication system.

This adaptive strategy allows the vehicle to prioritize speed during turns while maintaining higher steering accuracy when driving through straight corridors.

---

## Controller Selection

At every control cycle, the EV3 reads the distance measurements provided by the Arduino Nano.

If the measured distance is **80 cm or less**, the robot switches to **Turn Mode**.

Otherwise, it operates in **Corridor Mode**.

```
           Read I²C Sensors
                  │
                  ▼
      Is Distance ≤ 80 cm?
          │             │
        YES             NO
          │             │
          ▼             ▼
    Turn Controller  Corridor Controller
```

---

## Turn Controller

When the measured distance is **80 cm or less**, the robot assumes that it is approaching a corner.

In this mode, the controller is configured to allow smooth steering corrections while maintaining a relatively high forward speed.

Controller parameters:

| Parameter | Value |
|-----------|------:|
| KP | 1.6 |
| KI | 0.0 |
| KD | 0.2 |
| Forward Speed | 65 |
| Steering Limit | ±20 |

The reduced steering limit prevents excessive steering angles, producing smoother trajectories and reducing oscillations while negotiating corners.

---

## Corridor Controller

When the measured distance is greater than **80 cm**, the robot enters Corridor Mode.

In this state, maintaining the vehicle centered within the lane becomes the primary objective.

Controller parameters:

| Parameter | Value |
|-----------|------:|
| KP | 3.0 |
| KI | 0.0 |
| KD | 0.2 |
| Forward Speed | 35 |
| Steering Limit | ±40 |

Compared with Turn Mode, the proportional gain is increased and a larger steering range is permitted. This enables the robot to react more aggressively to lateral deviations and maintain accurate lane centering.

---

## Control Algorithm

The steering correction is computed using the following equations:

```
error = (right_distance − left_distance) − sensor_offset

derivative = error − previous_error

output = (KP × error) + (KD × derivative)
```

The integral term is intentionally disabled because ultrasonic sensors naturally introduce measurement fluctuations that may accumulate over time without providing significant improvements in steering performance.

Before applying the steering command, the controller output is limited according to the active navigation mode.

```
Turn Mode
Maximum Steering = ±20

Corridor Mode
Maximum Steering = ±40
```

Finally, the steering command is sent to the steering motor while the drive motor maintains the corresponding forward speed for the selected mode.

This adaptive controller provides a good balance between cornering smoothness and lane-centering accuracy while keeping the control algorithm computationally simple and highly repeatable.

---

# Finite State Machine

The navigation software is organized around a **Finite State Machine (FSM)**.

Instead of executing a single control strategy throughout the entire run, the robot continuously evaluates its environment and selects the controller that best matches the current driving condition.

The state transitions are based on the distance measurements received from the Arduino Nano through the I²C communication bus.

```
                 START
                   │
                   ▼
     Automatic Steering Calibration
                   │
                   ▼
         Read I²C Sensor Data
                   │
                   ▼
      Distance ≤ 80 cm ?
          │                 │
        YES                 NO
          │                 │
          ▼                 ▼
     TURN MODE       CORRIDOR MODE
          │                 │
          └────────┬────────┘
                   ▼
       Update Steering & Drive
                   │
                   ▼
           Read Sensors Again
                   │
                   └──────────────► Repeat
```

This architecture separates high-level decision-making from low-level vehicle control.

The FSM determines **which controller should be active**, while each PD controller computes the steering correction using its own set of parameters.

This modular organization simplifies debugging, improves software readability, and makes future extensions—such as obstacle avoidance, dynamic speed control, or vision-based navigation—significantly easier to implement without modifying the existing control architecture.
# Engineering Decisions

Every major design choice was based on iterative testing, quantitative observations, and continuous refinement throughout the development process.

Rather than selecting components or algorithms solely based on theoretical considerations, each subsystem was evaluated experimentally and improved according to its performance during real-world testing.

The table below summarizes the most important engineering decisions and the reasoning behind each one.

| Engineering Decision | Reason | Benefit |
|:-------------------------------|:---------------------------------------------------------|:---------------------------------------------------------|
| Ackermann Steering | Provides realistic steering geometry with reduced wheel slip. | Smoother and more accurate cornering. |
| Rear-Wheel Drive | Separates propulsion from steering. | Improved traction and simplified drivetrain. |
| Encoder-Based Steering | Enables absolute steering position control. | High repeatability and automatic centering. |
| Five Ultrasonic Sensors | Expands environmental perception. | Increased measurement redundancy and reliability. |
| Arduino Nano Coprocessor | Offloads sensor acquisition from the EV3. | Reduced computational load and simpler software. |
| I²C Communication | Consolidates sensor data into a single interface. | Lower EV3 port usage and cleaner wiring. |
| Custom PCB | Centralizes power and signal routing. | Improved electrical organization and easier maintenance. |
| 3D-Printed Sensor Mounts | Maintains fixed sensor alignment. | Greater measurement consistency and reduced vibration. |
| Modular Software Architecture | Separates software into independent modules. | Easier debugging, maintenance, and scalability. |
| Dual PD Controller | Adapts steering behavior to different driving conditions. | Improved stability in both turns and straight corridors. |

---

# Current Performance

Testing of the current robot demonstrates that the implemented architecture provides consistent and repeatable autonomous behavior.

The combination of mechanical improvements, modular electronics, and adaptive control algorithms has significantly increased the robot's overall reliability compared to earlier prototypes.

Current achievements include:

- Stable lane-centering performance.
- Smooth steering corrections.
- Reliable automatic steering calibration.
- Consistent repeatability between multiple runs.
- Stable I²C communication between the Arduino Nano and the EV3 Brick.
- Improved electrical reliability after PCB integration.
- Simplified maintenance due to modular wiring.
- Robust mechanical assembly suitable for repeated testing.

Although software optimization is still ongoing, the current platform provides a reliable foundation for both the Open Challenge and future development of the Obstacle Challenge.

---

# Future Improvements

While the current robot successfully meets the objectives established for this stage of development, several improvements are planned for future iterations.

These enhancements focus on increasing navigation accuracy, expanding autonomous capabilities, and improving overall system performance.

Planned developments include:

- Complete implementation of the Obstacle Challenge.
- Full integration of the HuskyLens vision system.
- Dynamic speed adaptation based on track conditions.
- Expanded Finite State Machine with additional navigation states.
- Sensor fusion techniques combining ultrasonic and vision data.
- Enhanced obstacle avoidance algorithms.
- Further optimization of the steering controller.
- Additional mechanical refinements.
- Improved cable management and electrical integration.

The modular architecture adopted throughout this project allows these improvements to be incorporated with minimal impact on the existing software and hardware.

---

# Engineering Journal

The complete engineering process has been documented chronologically in a dedicated engineering journal.

Each development stage, hardware modification, software improvement, and design decision has been recorded to provide a comprehensive overview of the project's evolution.

The journal includes:

- Design iterations.
- Mechanical modifications.
- Electronic improvements.
- Software development milestones.
- Testing procedures.
- Engineering decisions.
- Performance evaluations.

📄 **Engineering Journal**

```
docs/engineering_journal.md
```

---

# Repository Structure

```
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

The repository is organized to separate documentation, software, CAD models, and visual resources, making navigation straightforward for judges, collaborators, and future development.

---

# Development Timeline

| Date | Milestone |
|:------------|:---------------------------------------------|
| 4 Jul 2026 | Initial PD controller prototype |
| 8 Jul 2026 | PCB manufacturing |
| 10 Jul 2026 | PCB assembly and validation |
| 13 Jul 2026 | Finite State Machine implementation |
| 21 Jul 2026 | I²C communication completed |
| 27 Jul 2026 | Final hardware integration |
| 28 Jul 2026 | Final robot assembly |

A detailed description of each milestone is available in the Engineering Journal.

---

# Acknowledgements

We would like to express our sincere gratitude to our mentors, teachers, and everyone who supported the development of this project throughout the WRO 2026 season.

Their guidance, technical advice, and continuous encouragement have been fundamental in transforming an initial concept into a reliable autonomous vehicle.

Their support has played a significant role in both our technical growth and our understanding of the engineering design process.

---

# Conclusion

The current version of the **Los Grises Jr** robot represents the result of an iterative engineering process driven by continuous testing, systematic evaluation, and incremental improvements.

Throughout the season, every subsystem—including the mechanical structure, embedded electronics, control algorithms, and software architecture—has been refined with the objective of maximizing reliability, repeatability, and maintainability.

Compared to our earliest prototypes, the final robot incorporates a custom-designed PCB, an Arduino Nano coprocessor, automatic steering calibration, encoder-based Ackermann steering, modular software architecture, and an adaptive dual PD steering controller.

Although development is still ongoing, the current platform provides a robust foundation for completing both the Open Challenge and the Obstacle Challenge.

As we continue testing and refining the system, we remain committed to applying sound engineering principles to every stage of the design process while continuously improving both the hardware and software of our autonomous vehicle.

---

<div align="center">

# Team Los Grises Jr

**World Robot Olympiad 2026 – Future Engineers**

</div>


