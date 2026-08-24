## Engineering Journal
---

### 4 July 2026 – Initial Prototyping & Basic Control Code
We developed the first version of our steering and traction control system for the Open Challenge. The software implemented a PD (Proportional–Derivative) controller using two ultrasonic sensors to keep the robot centered inside the lane. We selected a PD controller because it provides a fast and stable response while avoiding the unnecessary complexity of an integral term for this stage of development.

---

### 8 July 2026 – PCB Manufacturing
To reduce wiring complexity, eliminate loose connections, and improve signal integrity across all sensor channels, we designed a custom PCB for sensor routing and sent it to a manufacturer in China for production.

---

### 10 July 2026 – Hardware Integration
The custom PCB arrived and was successfully assembled. Initial bench tests confirmed reliable power distribution and clean communication signals for the sensor array, significantly improving the electrical reliability and organization of the robot.
---

### 13 July 2026 – Advanced Control Software & FSM Implementation

We developed the first beta version of our Finite State Machine (FSM) in MicroPython. The system switches between different driving states, including straight-line PD centering and an asymmetrical open-loop curve-following mode. We implemented an FSM because we believed the robot required decision-making capabilities beyond a traditional feedback controller, allowing it to adapt its behavior according to different driving situations.
---

### 21 July 2026 – Hardware Delay
We continued testing with the beta version of our software while waiting for additional cables that had been ordered and were scheduled to arrive on 22 July 2026.
---

## 21 July 2026 – I²C Communication Development
We programmed the communication system for our custom PCB using the I²C protocol, allowing multiple ultrasonic sensors to communicate efficiently through a simplified wiring architecture.

### 27 July 2026 – Pre-final Hardware Integration
Today, we integrated the sensor multiplexer into the robot, allowing us to remove almost all cables connected to the numbered EV3 input ports. As a result, only one of the original four sensor ports is now required.

We also installed custom 3D-printed mounts for the ultrasonic sensors, improving their alignment, rigidity, and overall integration with the chassis.

Finally, due to development time constraints and the need for rapid testing, we decided to migrate the control software back to EV3-G (EV3 Blocks). To maintain transparency and reproducibility, we will include both the original source code and a pseudocode version in the Source Code (src) section of our repository.
---
### **28 July 2026 – Final Hardware Integration and *The Robot***

Today, we completed the full assembly of our robot and successfully integrated the custom PCB, ultrasonic sensors, and all major hardware components. With its larger structure, it now looks more like an SUV than a regular car.

At first, we were concerned about the robot's dimensions because the competition rules require it to stay within **30 × 30 × 30 cm**. Fortunately, the final measurements are approximately **24 × 23 × 18 cm**, well within the allowed limits.

Another important concern was the robot's center of gravity. To improve stability, we placed the EV3 Brick at the rear of the chassis while positioning the drive motors near the center, resulting in a more balanced weight distribution.

On the software side, we have already developed a significant portion of the codebase. However, the most important milestone still lies ahead: making everything work together reliably. We believe that, with the hardware now complete, software development and testing will be more straightforward. We hope our programmer continues putting in the same level of dedication so that the robot performs as expected in the coming tests.

---
**24 August 2026** – I²C Communication Problems and Hardware Bottleneck

After several weeks of development, I²C became a major problem for us because the Arduino Nano we were using was defective. The board was missing its factory bootloader, and for some reason, we were unable to reinstall it. We tried everything we knew, including several alternative workarounds, but after four weeks, nothing worked.

The solution was to purchase a new Nano. We confirmed that the software itself was working by testing it with a borrowed Nano that did not have the same issue. This allowed us to conclude that the original board was faulty rather than the software being the source of the problem.

Now, we are waiting for the new Nano so we can continue testing the programs and resume the I²C integration.
