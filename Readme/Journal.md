Engineering Journal

4 July 2026 – Initial Prototyping & Basic Control Code
We developed the first version of our steering and traction control system for the Open Challenge. The software implemented a PD (Proportional–Derivative) controller using two ultrasonic sensors to keep the robot centered inside the lane. We selected a PD controller because it provides a fast and stable response while avoiding the unnecessary complexity of an integral term for this stage of development.

8 July 2026 – PCB Manufacturing
To reduce wiring complexity, eliminate loose connections, and improve signal integrity across all sensor channels, we designed a custom PCB for sensor routing and sent it to a manufacturer in China for production.

10 July 2026 – Hardware Integration
The custom PCB arrived and was successfully assembled. Initial bench tests confirmed reliable power distribution and clean communication signals for the sensor array, significantly improving the electrical reliability and organization of the robot.

13 July 2026 – Advanced Control Software & FSM Implementation
We developed the first beta version of our Finite State Machine (FSM) in MicroPython. The system switches between different driving states, including straight-line PD centering and an asymmetrical open-loop curve-following mode. We implemented an FSM because we believed the robot required decision-making capabilities beyond a traditional feedback controller, allowing it to adapt its behavior according to different driving situations.

21 July 2026 – Hardware Delay
We continued testing with the beta version of our software while waiting for additional cables that had been ordered and were scheduled to arrive on 22 July 2026.

21 July 2026 – I²C Communication Development
We programmed the communication system for our custom PCB using the I²C protocol, allowing multiple ultrasonic sensors to communicate efficiently through a simplified wiring architecture.

27 July 2026 – Final Hardware Integration
Today, we integrated the sensor multiplexer into the robot, allowing us to remove almost all cables connected to the numbered EV3 input ports. As a result, only one of the original four sensor ports is now required.

We also installed custom 3D-printed mounts for the ultrasonic sensors, improving their alignment, rigidity, and overall integration with the chassis.

Finally, due to development time constraints and the need for rapid testing, we decided to migrate the control software back to EV3-G (EV3 Blocks). To maintain transparency and reproducibility, we will include both the original source code and a pseudocode version in the Source Code (src) section of our repository.
