<div align="center">

# 🏎️ LOS GRISES JR
## World Robot Olympiad 2026  
### Future Engineers Category
<p align="center">
  <img src="https://github.com/user-attachments/assets/6422e0d6-8cc2-4bbc-beaf-4bbada98c140" width="700" />
</p>

<br>

![WRO 2026](https://img.shields.io/badge/WRO-2026-005BBB?style=for-the-badge)
![Future Engineers](https://img.shields.io/badge/Future_Engineers-Category-00A86B?style=for-the-badge)
![LEGO EV3](https://img.shields.io/badge/Main_Controller-LEGO_EV3-F7C600?style=for-the-badge)
![Arduino Nano](https://img.shields.io/badge/Coprocessor-Arduino_Nano-00979D?style=for-the-badge)
![Custom PCB](https://img.shields.io/badge/Electronics-Custom_PCB-6A5ACD?style=for-the-badge)
![HuskyLens](https://img.shields.io/badge/Vision-HuskyLens_AI-FF4500?style=for-the-badge)

<br>

---

# 📷 Final Competition Robot

**Insert final robot hero image here**

*(Recommended image: front three-quarter view showing the complete vehicle)*

---

### Official Engineering Repository

Documentation of Team Los Grises Jr's autonomous vehicle developed for:
**World Robot Olympiad 2026 — Future Engineers Category**


---

</div>


# 🚗 Project Overview

Our robot is a fully autonomous four-wheel vehicle designed for the **World Robot Olympiad 2026 Future Engineers competition**.

The objective of this project is to develop a reliable autonomous vehicle capable of navigating the competition environment through a combination of:

- Mechanical engineering.
- Embedded electronics.
- Autonomous control algorithms.
- Sensor processing.
- Software architecture.
- Iterative testing and optimization.


The final platform combines:

| System | Implementation |
|:---|:---|
| Steering | Ackermann steering geometry |
| Drive System | Rear-wheel drive |
| Main Controller | LEGO Mindstorms EV3 Brick |
| Coprocessor | Arduino Nano |
| Vision System | HuskyLens AI Camera |
| Distance Measurement | Five ultrasonic sensors |
| Communication | I²C protocol and UART protocol |
| Electronics | Custom-designed PCB |
| Control Algorithm | Adaptive Dual PD Controller |
| Decision System | Finite State Machine |


---

# ⚡ Quick System Overview

<div align="center">

```
                 ┌──────────────────┐
                 │ HuskyLens Camera │
                 └────────┬─────────┘
                          │
                          ▼

┌────────────────┐    ┌──────────────┐
│ Ultrasonic     │───▶│ Custom PCB   │
│ Sensors (x5)   │    └──────┬───────┘
└────────────────┘           │
                             ▼

                      ┌────────────┐
                      │ Arduino    │
                      │ Nano       │
                      └─────┬──────┘
                            │
                          I²C
                            │
                            ▼

                    ┌──────────────┐
                    │ LEGO EV3     │
                    │ Controller   │
                    └──────┬───────┘
                           │

             ┌─────────────┴─────────────┐
             ▼                           ▼

      Steering Motor              Drive Motor

```

</div>


The robot uses a distributed architecture where each subsystem performs a specific role:

- The **Arduino Nano** manages sensor acquisition and communication.
- The **EV3 Brick** performs navigation decisions and motion control.
- The **Custom PCB** organizes power distribution and signal routing.
- The **software architecture** coordinates calibration, sensing, and autonomous driving.


---

# 📑 Table of Contents

- [👥 Team](#-team)
- [🚗 Project Overview](#-project-overview)
- [⚡ Quick System Overview](#-quick-system-overview)
- [⭐ Engineering Highlights](#-engineering-highlights)
- [📊 Robot Specifications](#-robot-specifications)
- [📸 Vehicle Gallery](#-vehicle-gallery)
- [🔩 Components and Hardware](#-components-and-hardware)
- [🛠 Mechanical Design](#-mechanical-design)
- [⚡ Electronics](#-electronics)
- [🔌 Custom PCB](#-custom-pcb)
- [💻 Software Architecture](#-software-architecture)
- [🎯 Steering Calibration](#-automatic-steering-calibration)
- [📡 Sensor Calibration](#-sensor-calibration)
- [🎮 Dual PD Controller](#-dual-pd-steering-controller)
- [🔄 Finite State Machine](#-finite-state-machine)
- [🧠 Engineering Decisions](#-engineering-decisions)
- [📈 Current Performance](#-current-performance)
- [📓 Engineering Journal](#-engineering-journal)
- [📂 Repository Structure](#-repository-structure)
- [🏁 Conclusion](#-conclusion)


---

# 👥 Team


## 📷 Team Photo

<div align="center">

**Insert official team photograph here**

</div>


---

# 👨‍💻 Renato Medina
<p align="center">
<img width="350" height="350" alt="Image" src="https://github.com/user-attachments/assets/dd9e997b-65a7-4909-8207-ea3630b5aff4" />
</p>

## Team Captain

| Information | Details |
|:---|:---|
| Age | 14 |
| Role | Team Captain and Programmer |
| Main Areas | Software, Embedded Systems, Integration |


### Responsibilities

- 💻 Software Development
- 🤖 Autonomous Navigation Algorithms
- ⚙️ Mechanical Design
- 🔧 Robot Integration
- 🧠 System Architecture
- 📚 Technical Documentation
- 🔌 Embedded Programming


---

### About Renato

Renato serves as the **Team Captain** and leads the software architecture, autonomous navigation development, project documentation, and system integration of the robot.

His robotics journey began through the **OnStage TMR program**, where he developed a strong interest in autonomous systems, embedded programming, and engineering design.

Since then, he has focused on combining:

- Software development.
- Electronics.
- Mechanical design.
- Control systems.

to create reliable robotic platforms.

For the WRO 2026 season, his objective is to develop a highly reliable autonomous vehicle while expanding his knowledge of embedded systems, control theory, and robotic engineering.

---

# 👩‍🔧 Paulina

## Mechanical & Electronics Designer


| Information | Details |
|:---|:---|
| Role | Mechanical & Electronics Designer |
| Main Areas | Assembly, Electronics, Testing |


### Responsibilities

- 🔩 Mechanical Assembly
- ⚡ Electronics Integration
- 🔌 PCB Installation
- 🧪 Robot Testing
- 📐 Structural Optimization
- 🛠 Cable Organization


---

### About Paulina

Paulina is responsible for the robot's mechanical construction and electronic integration.

Her work focuses on:

- Structural assembly.
- Sensor installation.
- PCB integration.
- Mechanical validation.
- Hardware reliability.


Her contributions have been fundamental in transforming the initial prototype into a competition-ready autonomous vehicle with improved stability and maintainability.


📷 **Insert Paulina working on assembly image here**


---

# 🤝 Team Responsibilities


| Area | Renato | Paulina |
|:---|:---:|:---:|
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

# ⭐ Engineering Philosophy


> [!IMPORTANT]
>
> The development of Los Grises Jr is based on continuous engineering improvement.
>
> Every subsystem has been tested, analyzed, modified, and optimized with three main objectives:
>
> - Increase reliability.
> - Improve repeatability.
> - Simplify maintenance.


---

# ⭐ Engineering Highlights


The current robot incorporates multiple engineering improvements developed specifically for the **WRO Future Engineers Challenge**.


| Feature | Implementation |
|:---|:---|
| Steering System | Ackermann steering geometry |
| Drive System | Rear-wheel drive |
| Sensors | Five ultrasonic sensors |
| Vision | HuskyLens AI camera |
| Coprocessors | 2 Arduino Nano |
| Electronics | Custom PCB |
| Communication | I²C architecture |
| Steering Calibration | Automatic encoder-based calibration |
| Control | Adaptive Dual PD controller |
| Navigation | Finite State Machine |
| Software | Modular architecture |
| Sensor Mounting | Custom 3D printed supports |
| Mechanical Design | Optimized weight distribution |


---

<div align="center">

# 📊 Robot Specifications


<div align="center">

| Specification | Value |
|:---|:---|
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
| Sensor Supports | 3D Printed |
| Programming Languages | EV3-G & Arduino C++ |

</div>


---

# 📸 Vehicle Gallery


The following images show the final competition vehicle from different perspectives.

These photographs demonstrate:

- Mechanical construction.
- Sensor placement.
- Electronics integration.
- Cable organization.
- Overall vehicle design.


<div align="center">


| Front View | Top View | Right Side |
|:---:|:---:|:---:|
| 📷 | 📷 | 📷 |
| Insert image | Insert image | Insert image |


| Left Side | Rear View | Bottom View |
|:---:|:---:|:---:|
| 📷 | 📷 | 📷 |
| Insert image | Insert image | Insert image |


</div>


> [!NOTE]
>
> A demonstration video will be added after the final validation tests are completed.


---

# 🔩 Components and Hardware


The robot combines LEGO components with custom embedded electronics to create a modular and reliable autonomous platform.

Each component was selected according to:

- Reliability.
- Compatibility.
- Mechanical integration.
- Software requirements.
- Long-term maintainability.


| Component | Quantity | Function | Status |
|:---|:---:|:---|:---:|
| LEGO EV3 Brick | 1 | Main controller | ✅ |
| EV3 Medium Motor | 1 | Rear-wheel traction | ✅ |
| EV3 Medium Motor | 1 | Ackermann steering | ✅ |
| Ultrasonic Sensors | 5 | Distance measurement | ✅ |
| Arduino Nano | 1 | Sensor acquisition and communication | ✅ |
| HuskyLens AI Camera | 1 | Vision processing | ✅ |
| Custom PCB | 1 | Power and signal distribution | ✅ |
| LEGO Wheels | 4 | Vehicle mobility | ✅ |
| 3D Printed Supports | Multiple | Sensor mounting | ✅ |


---

# 🛠 Mechanical Design


## Design Evolution


The mechanical structure of the robot was developed through multiple iterations focused on:

- Structural rigidity.
- Weight distribution.
- Driving stability.
- Maintenance accessibility.
- Competition compliance.


Rather than modifying only a single prototype, the robot evolved progressively through testing and engineering improvements.

Every redesign addressed specific limitations discovered during previous experiments.

The result is a compact autonomous vehicle designed for reliability and repeatability.


---

## 📷 Mechanical Design Overview


<div align="center">

**Insert chassis evolution image here**

</div>


---

# 📏 Final Dimensions


| Measurement | Value |
|:---|:---:|
| Length | 24 cm |
| Width | 23 cm |
| Height | 18 cm |


The final design remains within the official WRO Future Engineers limit of:

```
30 × 30 × 30 cm
```


The available internal space allows integration of:

- EV3 electronics.
- Arduino coprocessor.
- Custom PCB.
- Sensor wiring.
- Steering mechanism.


---

# ⚖️ Weight Distribution


Achieving a balanced center of gravity was one of the main mechanical objectives.


Instead of concentrating all components in one area, the mass was intentionally distributed throughout the chassis.


## Main Design Decisions


| Component | Position |
|:---|:---|
| EV3 Brick | Rear section |
| Drive Motor | Center area |
| Steering Motor | Above steering mechanism |
| Custom PCB | Near sensor assembly |
| Arduino Nano | Adjacent to PCB |


This configuration improves:

- Acceleration stability.
- Braking behavior.
- Cornering performance.
- Mechanical reliability.


---

# 🔄 Ackermann Steering System


The robot uses an Ackermann-inspired steering mechanism powered by an EV3 Medium Motor.


Unlike differential steering systems, Ackermann geometry allows the vehicle to follow more realistic turning trajectories by reducing tire slip.


## Steering Control Method


The steering motor is controlled using encoder positions instead of continuous rotation.


This provides:

✅ Repeatable steering angles  
✅ Faster response  
✅ Automatic steering centering  
✅ Reduced positioning error  


---

## Steering Protection


The software limits the maximum steering angle to prevent:

- Mechanical overtravel.
- Transmission stress.
- Unnecessary motor load.


---

# 🚗 Rear-Wheel Drive


The vehicle uses a rear-wheel-drive configuration powered by an EV3 Large Motor.


This architecture was selected because it provides several advantages:


| Advantage | Result |
|:---|:---|
| Better weight transfer | Improved acceleration |
| Independent steering system | Less interference |
| Simpler drivetrain | Increased reliability |
| Easier maintenance | Faster repairs |


Separating propulsion and steering makes vehicle behavior more predictable during autonomous navigation.


---

# 📡 Sensor Mounts


All ultrasonic sensors are installed using custom-designed 3D printed brackets.


<div align="center">

📷 **Insert sensor mount image here**

</div>


The supports were designed to:


- Maintain precise alignment.
- Reduce vibration.
- Improve rigidity.
- Simplify installation.
- Guarantee repeatable sensor positioning.


Compared with direct LEGO mounting, the printed supports significantly improve measurement consistency.


---

# ⚡ Electronics


The robot combines LEGO electronics with custom embedded hardware to create a modular electrical architecture.


The system is divided into two main processing units:


| Controller | Responsibility |
|:---|:---|
| LEGO EV3 Brick | Navigation, decision making, motor control |
| Arduino Nano | Sensor acquisition and communication |


This distributed architecture provides:

- Reduced wiring complexity.
- Lower EV3 port usage.
- Easier debugging.
- Better scalability.


---

# 🔌 Electronic Architecture


<div align="center">


```
          Ultrasonic Sensors
              │ │ │ │ │
              ▼ ▼ ▼ ▼ ▼

          ┌────────────┐
          │ Custom PCB │
          └─────┬──────┘
                │

          ┌────────────┐
          │ Arduino    │
          │ Nano       │
          └─────┬──────┘
                │
              I²C

                │

          ┌────────────┐
          │ LEGO EV3   │
          │ Brick      │
          └─────┬──────┘

                │

      Steering Motor + Drive Motor

```

</div>


The architecture separates:

- Sensor acquisition.
- Data communication.
- Decision making.
- Vehicle control.


This modular approach allows each subsystem to be tested independently.


---

# 🔌 Custom PCB


One of the most important improvements during development was the creation of a custom Printed Circuit Board.


During early testing, sensors were connected individually using loose wiring.

Although functional, this approach caused:


❌ Cable clutter  
❌ Difficult maintenance  
❌ Loose connections  
❌ Limited organization  


To solve these problems, a dedicated PCB was designed specifically for this robot.


---

## PCB Functions


The custom PCB provides:


| Function | Purpose |
|:---|:---|
| Power distribution | Organized electrical supply |
| Signal routing | Cleaner connections |
| Sensor interfaces | Easy sensor replacement |
| Arduino interface | Simplified communication |
| Cable management | Improved organization |


---

## PCB Advantages


Compared with individual wiring, the PCB provides:


✅ Cleaner internal organization  
✅ Faster assembly  
✅ Easier troubleshooting  
✅ Higher mechanical reliability  
✅ Reduced accidental disconnections  
✅ Better future expansion capability  


---

<div align="center">


**Software Architecture • Calibration Systems • Dual PD Controller • FSM • Engineering Decisions • Future Improvements • Repository Structure**

</div>

💻 Software Architecture

The robot software was designed using a modular architecture, where each subsystem has a specific responsibility.
Instead of implementing all functionalities inside a single program, the system is divided into independent modules for:
* Sensor acquisition (Ultrasonics, Gyroscope & Vision).
* Calibration.
* Decision making (FSM & Turn Counting).
* Motion control.
* Autonomous parking.

This organization improves:
✅ Code readability
✅ Debugging efficiency
✅ Testing capability
✅ System scalability

🧩 Software Execution Flow

```
    A[START: Calibrate Steering & Reset Gyro to 0°] --> B[Read Sensors: Ultrasonics, Gyro Heading, HuskyLens]
    B --> C{Turn_Count == 12?}
    C -->|YES| D[BREAK LOOP: Execute Reverse Parking Routine]
    C -->|NO| E{front_dist < Critical_Distance?}
    E -->|YES: Emergency| F[Safety Override: Reverse & Re-align]
    E -->|NO: Drive Mode| G{Driving Condition / Corner Detected?}
    G -->|Corridor State| H["Corridor PD: Target Heading = 0° + Vision Offset"]
    G -->|Corner State| I["Turn PD: Target Heading = Target + 90° | Turn_Count + 1"]
    H --> J[Apply Motors Command]
    I --> J
    F --> J
    J --> B
    D --> K[END PROGRAM]
```

🎯 Automatic Steering Calibration

Every autonomous run begins with an automatic steering calibration routine.
The objective is to guarantee that every attempt starts from the same steering reference position.
Instead of manually aligning the steering system, the robot automatically determines the mechanical limits using the motor encoder and resets the EV3 Gyroscope to absolute 0°.

Advantages:
✅ Consistent steering position
✅ Elimination of manual adjustments
✅ Reliable absolute heading for the gyroscope

📡 Sensor Calibration & Fusion

Even identical ultrasonic sensors may produce small differences. The robot performs an automatic sensor calibration routine at startup to calculate offsets.
Furthermore, to eliminate drift caused by missing walls or track irregularities, the raw distance errors from the ultrasonic sensors are fused with the EV3 Gyroscope angle.

Heading Error Calculation:
Heading_Error = Target_Angle - Current_Gyro_Angle

Fused Error Entry:
Fused_Error = Heading_Error + Lateral_Sensor_Offset

👁️ AI Vision & Obstacle Avoidance

For the Obstacle Challenge, the robot integrates a HuskyLens AI Camera programmed to detect colored pillars.

If Red is detected: The system adds a positive offset to the target, forcing the robot to pass the pillar on the right side.

If Green is detected: The system adds a negative offset, forcing the robot to pass on the left side.
This vision data modifies the lateral control dynamically without interrupting the forward momentum.

🎮 Adaptive Dual PD Steering Controller

The steering system uses a closed-loop Proportional-Derivative controller that switches automatically depending on the driving situation.

🔄 Turn Controller (Corner Mode)
When the robot detects an approaching corner (via diagonal sensors), it updates its Gyro target by 90° and prioritizes smooth cornering.

KP: 1.6

KD: 0.2

Forward Speed: 65

Steering Limit: ±20

➡️ Corridor Controller (Straight Mode)
When inside a long corridor, maintaining a perfect 0° heading and lane-centering becomes the priority.

KP: 3.0

KD: 0.2

Forward Speed: 35

Steering Limit: ±40

Control Equation:
error = (Target_Angle - Current_Heading) + (right_distance - left_distance) + Vision_Offset
derivative = error - previous_error
output = (KP × error) + (KD × derivative)

🔄 Finite State Machine (FSM) & Autonomous Parking

The robot's navigation is governed by a Finite State Machine that now includes a strict lap-tracking protocol.

🅿️ 12-Turn Counting Logic
Since the WRO track requires completing 3 full laps (12 corners total), the FSM relies on the Gyroscope to increment a Turn_Count variable every time a 90° turn is successfully executed.

When Turn_Count == 12, the FSM triggers the Reverse Parking Routine:

Deceleration Pulse: Speed drops to 15% for 0.4 seconds to gently enter the parking zone.

Stabilization: Full stop for 0.2 seconds to settle the chassis.

Reverse Parking: The vehicle applies reverse power (-30%) for 1.5 seconds, utilizing the Gyro heading to back cleanly and perfectly straight into the parking area.

´´´
INICIO
    // FASE 1: Inicialización
    Calibrar_Direccion_Automaticamente()
    Reiniciar_Giroscopio(0°)
    Turn_Count ← 0
    Target_Angle ← 0
    Inicializar_HuskyLens()

    // FASE 2: Bucle de Carrera
    MIENTRAS programa_en_ejecución HACER
        front_dist, laterales, diagonal ← LeerUltrasonicosI2C()
        current_heading ← LeerGiroscopio()
        color_visto ← LeerHuskyLens()

        // Lógica de Obstáculos
        SI color_visto == ROJO ENTONCES Offset_Visión ← +45
        SINO SI color_visto == VERDE ENTONCES Offset_Visión ← -45
        SINO Offset_Visión ← 0

        // Condición de Estacionamiento
        SI Turn_Count == 12 ENTONCES
            ROMPER BUCLE
        FIN SI

        // FSM y Control PID
        SI front_dist < Distancia_Critica ENTONCES
            Reversa_Emergencia(-50, 1.75s)
        SINO
            SI Detecta_Esquina(diagonal) ENTONCES
                Target_Angle ← Target_Angle + 90
                Turn_Count ← Turn_Count + 1
                Error ← (Target_Angle - current_heading) + diagonal + Offset_Visión
                Aplicar_PD(Error, KP=1.6, Vel=65)
            SINO
                Error ← (Target_Angle - current_heading) + laterales + Offset_Visión
                Aplicar_PD(Error, KP=3.0, Vel=35)
            FIN SI
        FIN SI
    FIN MIENTRAS

    // FASE 3: Secuencia de Estacionamiento
    Motor_Avance(Velocidad=15, Tiempo=0.4s)
    Frenar(Tiempo=0.2s)
    Motor_Avance(Velocidad=-30, Tiempo=1.5s) // Reversa recta
    Apagar_Motores()
FIN

---

# 🧠 Engineering Decisions


Every major engineering decision was based on testing, analysis, and continuous improvement.


| Decision | Reason | Benefit |
|:---|:---|:---|
| Ackermann Steering | More realistic vehicle geometry | Smoother turns |
| Rear-Wheel Drive | Separates propulsion and steering | Better reliability |
| Encoder Steering | Absolute position control | Repeatable angles |
| Five Ultrasonic Sensors | Increased environmental awareness | Better perception |
| Arduino Nano Coprocessor | Dedicated sensor processing | Reduced EV3 workload |
| I²C Communication | Single communication channel | Cleaner architecture |
| Custom PCB | Organized electronics | Improved maintenance |
| 3D Printed Mounts | Fixed sensor position | Better measurements |
| Modular Software | Independent modules | Easier development |
| Dual PD Controller | Adaptive driving behavior | Better stability |


---

# 📈 Current Performance


Current testing demonstrates that the robot provides reliable autonomous behavior.


Achievements:


✅ Stable lane-centering  
✅ Smooth steering corrections  
✅ Automatic steering calibration  
✅ Consistent multi-run performance  
✅ Stable Arduino-EV3 communication  
✅ Improved electrical reliability after PCB integration  
✅ Strong mechanical structure for repeated testing  


The current platform provides a reliable foundation for completing future competition objectives.


---

# 📓 Engineering Journal


The complete engineering process is documented in a dedicated engineering journal.


The journal includes:


- Mechanical iterations.
- Hardware modifications.
- Software development.
- Testing procedures.
- Engineering decisions.
- Performance analysis.


📄 Engineering Journal:

```
docs/engineering_journal.md
```


---

# 📂 Repository Structure


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

# 📅 Development Timeline


| Date | Milestone |
|:---|:---|
| 4 Jul 2026 | Initial PD controller prototype |
| 8 Jul 2026 | PCB manufacturing |
| 10 Jul 2026 | PCB assembly and testing |
| 13 Jul 2026 | FSM implementation |
| 21 Jul 2026 | I²C communication completed |
| 27 Jul 2026 | Final hardware integration |
| 28 Jul 2026 | Final robot assembly |


---

# 🙏 Acknowledgements


We would like to thank our mentors, teachers, and everyone who supported the development of this project throughout the WRO 2026 season.


Their guidance, technical advice, and encouragement were essential in transforming an initial concept into a functional autonomous vehicle.


---

# 🏁 Conclusion


The current version of the **Los Grises Jr autonomous vehicle** represents the result of an iterative engineering process involving:

- Mechanical design.
- Electronics development.
- Embedded programming.
- Control theory.
- Autonomous navigation.


Compared with the earliest prototypes, the final platform incorporates:


✅ Custom-designed PCB  
✅ Arduino Nano coprocessor  
✅ Ackermann steering system  
✅ Automatic steering calibration  
✅ Adaptive Dual PD controller  
✅ Modular software architecture  
✅ Improved mechanical reliability  


The project continues evolving toward the completion of the remaining WRO challenges while maintaining the engineering principles that guided the entire development process:


> **Reliability, repeatability, and continuous improvement.**


---

<div align="center">

# 🏎️ Team Los Grises Jr

## World Robot Olympiad 2026  
## Future Engineers Category

</div>
