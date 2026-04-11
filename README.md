## This repository contains the official documentation of Team "Los Grises Jr" for the Future Engineers category at the World Robot Olympiad 2026.

Our project focuses on developing an autonomous vehicle capable of navigating dynamic environments using computer vision and precise steering control.

<p align="center">
  <img src="https://github.com/user-attachments/assets/6422e0d6-8cc2-4bbc-beaf-4bbada98c140" width="1000" />
</p>

---

## 👥 Team Members

### **Mateo Vásquez**  
**Role:** Electronics Specialist  

### **Ruth García**  
**Role:** Builder  

### **Renato Medina**  
**Role:** Programmer  

---

## 🤖 Robot Description

The robot is designed using an **Ackermann steering system**, which allows smooth and precise turns. This improves stability and control while navigating the field.

The Ackermann geometry ensures that each wheel follows an appropriate turning radius, reducing friction and increasing efficiency during curves.

It uses a front steering mechanism powered by a dedicated motor, enabling accurate directional control similar to real vehicles.

The robot is equipped with a **HuskyLens vision system**, capable of detecting and identifying colored objects such as red and green pillars. This allows the robot to make autonomous decisions in real time.

The structure is compact and optimized to maintain balance at different speeds. The placement of sensors and components ensures efficient detection and reliable performance.

---

## 🧩 Components and Hardware
| Component | Description | Image |
|-----------|-------------|-------|
| **45544 LEGO MINDSTORMS Education EV3 Core Set** | Forms the foundational structure and chassis. | <img src="https://github.com/user-attachments/assets/a725c977-b28b-4b5d-b95c-506c84cd6706" width="300"> |                       
| **Arduino Nano** | ATmega328-based microcontroller for control tasks. | <img src="https://github.com/user-attachments/assets/22e8f59c-909d-4ff2-b637-dc03e15f4de6" width="200"> |
| **DFRobot HuskyLens AI Camera** | AI-powered vision sensor capable of detecting colors, objects, and patterns in real time. | <img src="https://github.com/user-attachments/assets/fc513a62-31dd-4e8b-9117-27c28bc85ab0" width="200"> |
---

## 🧠 Strategy

The robot uses vision-based detection to identify red and green pillars and determine its path.

Based on the detected color, the robot dynamically adjusts its trajectory using the steering system, ensuring precise alignment and smooth navigation around obstacles.

The combination of computer vision and Ackermann steering allows efficient and stable autonomous performance during the competition.
