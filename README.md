## This repository contains the official documentation of Team "Los Grises Jr" for the Future Engineers category at the World Robot Olympiad 2026.

<p align="center">
  <img src="https://github.com/user-attachments/assets/6422e0d6-8cc2-4bbc-beaf-4bbada98c140" width="700" />
</p>

---

##  Team Members

### **Mateo Vásquez**  
**Role:** Electronics Specialist

**Age:** 14
---
### **Ruth García**  
**Role:** Builder

**Age:** 15
---
### **Renato Medina**  
**Role:** Programmer

**Age:** 14
---
##  Project Overview
---
This repository contains the official documentation of Team “Los Grises Jr” for the Future Engineers category at the World Robot Olympiad 2026.

Our project focuses on the development of an autonomous vehicle capable of navigating dynamic environments using computer vision and an advanced steering control system.

The design combines mechanical precision, real-time vision processing, and feedback control algorithms to achieve stable and accurate navigation.


##  Robot Description

The robot is built using an Ackermann steering system, similar to real-world vehicles.

🔧 Why Ackermann Steering?

The Ackermann geometry was selected instead of a differential drive system because:

It reduces lateral wheel slip
Improves trajectory accuracy in curves
Provides more realistic and stable motion

This is especially important in environments with tight turns and obstacles.

A dedicated motor controls the steering mechanism, allowing precise angle adjustments.
---
## Vehicle Photo

<div align="center">

| Front | Back |
|:--:|:--:|
|<img src= "https://github.com/user-attachments/assets/6dc00e73-723c-4a87-8fed-caf3bb0b516d" width="300"/> | <img src="https://github.com/user-attachments/assets/db47e1fc-15cf-4bf6-9bda-90c15ac27a30" width="300"/> |
| Bottom | Left |
| <img src="https://github.com/user-attachments/assets/adfcbc35-594a-4e53-b164-27f303c28fb5" width="300"/> | <img src= "https://github.com/user-attachments/assets/e4b8b09b-9287-48da-9303-3b7f5d03bd47" width= 300 /> |
| Right | Top |
|<img src= "https://github.com/user-attachments/assets/afbd04f9-7306-40f3-8b8c-13dbfa76661c" width= 300 /> | <img src= "https://github.com/user-attachments/assets/d506e87b-5d23-4b30-8219-bd6e11727323"  width= 300 /> |
---
##  Components and Hardware
| Component | Description | Image |
|-----------|-------------|-------|
| **45544 LEGO MINDSTORMS Education EV3 Core Set** | Forms the foundational structure and chassis. | <img src="https://github.com/user-attachments/assets/a725c977-b28b-4b5d-b95c-506c84cd6706" width="300"> |                       
| **Arduino Nano** | ATmega328-based microcontroller for control tasks. | <img src="https://github.com/user-attachments/assets/22e8f59c-909d-4ff2-b637-dc03e15f4de6" width="200"> |
| **DFRobot HuskyLens AI Camera** | AI-powered vision sensor capable of detecting colors, objects, and patterns in real time. | <img src="https://github.com/user-attachments/assets/fc513a62-31dd-4e8b-9117-27c28bc85ab0" width="200"> |
---

##  Strategy

The robot uses vision-based detection to identify red and green pillars and determine its path.

Based on the detected color, the robot dynamically adjusts its trajectory using the steering system, ensuring precise alignment and smooth navigation around obstacles.

The combination of computer vision and Ackermann steering allows efficient and stable autonomous performance during the competition.
---
## **Vision System**

The robot uses a HuskyLens AI camera connected to an Arduino Nano.

Capabilities:
Detects red and green pillars
Tracks object position in real time
Sends processed data to the control system
Design Considerations:
Elevated placement improves field of view
Enables early detection
Reduces reaction delay
---
## **Control System Architecture**

The system is divided into two main subsystems:

1. Vision Processing (Arduino Nano)
Receives data from HuskyLens
Processes object position and color
Sends relevant data to EV3
2. Motion Control (EV3)
Receives processed data
Controls:
Steering motor
Drive motor
---
## System Architecture
HuskyLens → Arduino Nano → EV3 → Motors

A custom PCB was developed to:

Improve connection stability
Reduce wiring complexity
Increase reliability during runs
---
## Navigation Strategy

The robot uses a vision-based navigation strategy:

Detect a colored pillar
Determine its horizontal position
Calculate steering correction
Navigate around the obstacle
Behavior Logic:
Object centered → move forward
Object left → steer left
Object right → steer right

If no object is detected:

The robot continues using the last known steering value temporarily
## Steering Control (PID)

To achieve stable and precise steering, a PID controller is used.
---
## Control Objective

Minimize the deviation between the detected object and the center of the robot’s trajectory.

## Implementation

Error is calculated as:

error = x_object - x_center

PID output is mapped to the steering motor angle
Runs continuously for real-time correction
---
 ##Tuning Process
---
The PID controller was tuned experimentally:

Kp adjusted for responsiveness
Kd added to reduce oscillations
Ki introduced to eliminate steady-state error
Observations:
High Kp caused oscillations
Adding Kd improved stability
Ki reduced persistent alignment error
---

## Performance 

Improved stability compared to proportional-only control
Reduced oscillations during turns
Faster response to object position changes

## **Challenges**
---
Integrating EV3 and Arduino systems
Achieving stable Ackermann steering control
Managing noise and variability in vision detection
Tuning PID parameters for different speeds
** Development Status**

** Mechanical design completed**

** Programming optimization in progress**

**Future Improvements**

**Finalize PID tuning**

**Improve detection robustness**

**Optimize speed vs stability balance**

---
### Conclusion
---
**The Los Grises Jr robot integrates:**

Realistic Ackermann steering
Intelligent vision processing
Advanced PID control

This combination allows the robot to achieve stable, precise, and adaptive navigation, making it a strong candidate for high-level performance in the WRO Future Engineers competition.
