## Engineering journal

## 4/July/2026: Initial Prototyping & Basic Control Code
We developed a foundational steering and traction system for the open challenge. This code implements a basic PD (Proportional-Derivative) controller utilizing two ultrasonic sensors to maintain a central position in the hallway. We implement the PD because is the best option to use a controller as this type, we dont use the I, because we use anti-windup integral.



---

## 8/July/2026: PCB Manufacturing
To reduce wiring complexity, eliminate loose connections, and optimize signal integrity across all four sensor channels, we designed and ordered a custom routing PCB from a manufacturer in China today.

---

## 10/July/2026: Hardware Integration
The custom PCB arrived and was successfully populated. Bench tests confirm seamless power distribution and clean signal lines for our sensor array, significantly improving structural reliability.

---

## 13/July/2026: Advanced Control Software & FSM Implementation
We developed a beta of Finite State Machine (FSM) in MicroPython. It switches states between straight line PID centering and an asymmetrical curve-tracing open loop. 
We developed this because we think the robot needs a type of intelligence, no the classical PID only.


---

## 21/July/2026
We used a beta version of the previous code because we were waiting for some cables that had been ordered and were scheduled to arrive on July 22, 2026

---
## 21/July/26 
We also programmed the system using the I²C communication protocol for the PCV ordered from China



## 27/07/26 – Today, we integrated the sensor multiplexer into the robot, allowing us to remove almost all the cables from the numbered ports, leaving only one of the original four letter ports in use.

## We also integrated 3D-printed mounts for the ultrasonic sensors into the robot. Additionally, due to time constraints and ease of development, we decided to return to using EV3-G (EV3 Blocks). However, we will provide the code in pseudocode, along with the original source code file in the src (source code) section.
