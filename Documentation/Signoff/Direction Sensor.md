# Direction Sensor Subsystem

## Function of the system
The purpose of this subsystem is to automatically steer the vehicle. The subsystem will keep the car in the desired location while the car is moving on the designated mat. It will determine if the car has veered off course and adjust accordingly.

## Constraints
| Description | Constraints/Specification | Source |
|-------------|---------------------------|--------|
| Safety | The system shall operate with the correct voltage and current. The motor driver is rated for 5V - 35V DC and 0-36mA. The IR Sensors are rated for 3.3V-5V and 23-43mA. The TT DC motors are recommended for 6-8V and 150-200mA. | [1], [3], [8] |
| Precision | The system must detect if the car is veering off then immediately correct it and put it back on track. The sensors response time must be between 1-50ms. | [4], [10] |
| Interference | The IR sensors shall not visually interfere with other subsystems.  | [2] |
| Socioeconomic | The system shall be cost effective relating to the project's budget constraints. | Conceptual Design |


## Build a Schematic
![image](https://github.com/abdoulm366/TTU-Capstone--Electrical-Class-Kit/assets/158520642/fd62d826-5fa5-4104-a595-721fcd8d69ec)
Figure 1: Buildable Schematic

![image](https://github.com/abdoulm366/TTU-Capstone--Electrical-Class-Kit/assets/158520642/4b0739e9-92ac-4bfe-9c06-44663526d7eb)

Figure 2: Prototype Schematic

The schematic in figure 1 shows the whole layout for the design. Starting from the left there are two circuits. These two circuits are the IR sensors (HW-201) [2]. Each one consists of the breadboard, amplifier IC’s, diodes, PNP transistor, capacitors, resistors, and the trimmer cermet which is the potentiometer. [8]. In figure 1, the L7812 is in place for the three pins each IR sensor has. When ordered, both IR sensors already come built so figure 2 shows a better understanding of the design by only showing the three pins by using a connector [2]. The three pins on the IR sensor are labeled VCC, GND, and OUT [2]. The Output for the top IR sensor is connected to the input/output pin D11. The Output pin for the bottom IR sensor is connected to the input/output pin D12. From the 5V pin on the motor driver, a single wire comes out and splits into three, two of them going to the VCC pins. From the GND on the motor driver, another wire splits into three and two of them go into the IR sensors ground pin [1].

The IR sensors are basically the vehicles eyes on the road. They work by emitting infrared (IR) light onto the ground and then detects how much of that light comes or bounces back [8]. The HW-201 has an IR emitter and IR receiver [8]. When it is directly over a black line, fewer light bounces back and when it's over a white area, more light reflects back. With the potentiometer, the reflection distance can be adjusted between 2cm to 30mm [8]. So, by mounting both side by side on the front of the vehicle the emitters will be close to the ground and will effectively detect the difference between the line and the surrounding area. Also, with its detection angle of 35 degrees [9]. By measuring the differences, the sensor can know if it is on the correct path or off it.

The motor driver in the schematic uses it’s four outputs for the two DC motors. The two motors shown in figures 1 and 2 are the front two of the vehicle. The front two wheels are the only ones that need to turn left and right to keep the car from veering off.  From the outside power supply, the positive goes through the switch, to turn off and on, then out and into the motor driver while the ground just goes straight to the motor driver. The rating for the motor driver is 5V-35V and the DC motors are 3V-12V but recommended is 6-8V [1][3]. The way this design works is the power source provides the necessary power to drive the DC motor, while the motor driver amplifies the signals from the Arduino uno to control the DC motor's operation using that power.

The program acts as the brain to make the car stay on its path. The program uses sensor readings with the motor control to create a closed-loop feedback system. It continuously monitors the car's position on the track and while it’s driving, adjusts to keep it on course. Without the program, the car would not be able to use the sensor data or control the motors effectively, making it unable to follow the desired path/line. In figure 3 below, a program outline can be made for this system.

![image](https://github.com/abdoulm366/TTU-Capstone--Electrical-Class-Kit/assets/158520642/e70078e5-8ad1-4e32-ba37-b63f1e1df173)

Figure 3: Program Outline


## Analysis
Analyzing the safety constraint: The system shall operate with the correct voltage and current. Overvoltage or excessive current can lead to malfunctions and overload. Overload can lead to overheating and other electrical hazards that can cause a safety factor. The two IR Sensors are rated for 3.3V-5V and 23-43mA [8]. The motor driver is rated for 5V - 35V DC and 0-36mA [1]. The TT DC motors are rated for 3V-12V but are recommended for 6-8V which is 150-200mA [3]. The TT motors rating works for the motor drivers rating. Understanding the voltage and current specifications of each component ensures safe operation.

Analyzing the precision constraint: The design of the mat is unknown, but the vehicle should be able to be put on any mat at anytime and go the correct path. The response time must be low, allowing the vehicle to stay on course with hard conditions such as sharper turns. The response time for the IR sensors is quicker than the eye can see being down to 1ms [4]. This is more than fast enough to keep the car on track. On the control algorithm side, the speed of the motors is set at the start of the program as shown in the block diagram in figure 3. The speed does not need to be too fast or it will turn the car too rapidly, and it does not need to be too slow or it won’t be able to keep the vehicle on path. Testing with the vehicle will allow the desired speed.

Analyzing the interference constraint:  The board for the IR sensor has a power light and an obstacle light on it. The obstacle light will show up when a certain light reflection is detected. The obstacle light is used to calibrate it and show when it is over a black line and when it’s not. By having lights on the front of the vehicle, it can interfere with another subsystem by looking like headlights. Covering this light is this best way to solve this but the light must still be seen so it can be calibrated and show that it functions correctly. By putting something removable such as a very small piece of electrical tape over the two lights, this can be solved. As long as nothing blocks the two emitters at the bottom of the IR sensors, everything can still function [2]. A small slit in the tape can be made in case it needs to be calibrated on the spot. This allows the light to be barely visible by the eye and allows the car to usable on any mat at any given time.

Analyzing the socioeconomic constraint: The budget of the project must be kept in mind for this design. It shall be cost-effective while also being high in quality. This system is a crucial part in the vehicles operation, so it needs to be reliable. 


## Bill of Materials (BOM)
| Item Name | Details | Quantity | Cost | Source |
|-----------|---------|----------|------|--------|
| Aduino Uno | Rev 3 | 1 | $27.60 | https://shorturl.at/bdoY9 |
| IR Sensors | HW-201 | 2 | $9.99 | https://shorturl.at/MPT08 |
| Motor Driver | L298N | 1 | $6.39 | https://shorturl.at/eGNW0 |
| DC motors | TT Gearbox motor | 2 | $6.99 | https://shorturl.at/ejpRV |
| Switch | CH755-ND | 1 | $1.41 | https://shorturl.at/hwAES |
| Jumper Wires | Female/male wires 20 x 3" | 1 | $1.95 | https://shorturl.at/pAI05 |

Total cost for subsystem: $54.33 (not including tax or shipping) 

## References 
[1] L298N Motor Driver.Pdf - Handson Technology, www.handsontec.com/dataspecs/module/L298N%20Motor%20Driver.pdf. Accessed 16 Apr. 2024. 

[2] Amazon.Com: Ir Infrared Obstacle Avoidance Sensor (2PCS) IR Transmitting and Receiving Tube Photoelectric Switch 3-Pin Compatible with AR-Duino Smart Car Robot : Electronics, www.amazon.com/Infrared-Avoidance-Transmitting-Receiving-Photoelectric/dp/B07PFCC76N. Accessed 17 Apr. 2024. 

[3] Amazon.Com: 2pcs DC Electric Motor 3-6V Dual Shaft Geared TT Magnetic ..., www.amazon.com/Aoicrie-Electric-Magnetic-Engine%EF%BC%8CDIY-Vibration/dp/B083BDW3FD. Accessed 16 Apr. 2024. 

[4] Yathishhhh. Arduino Forum, 19 Sept. 2023, forum.arduino.cc/t/can-you-guys-tell-me-the-response-time-frequency-of-tcrt5000-sensor-or-share-me-the-datasheet-of-mh-series-sensor-that-has-lm393-ic-with-tcrt5000-sen/1169865. 

[5] A000066-Datasheet.Pdf, docs.arduino.cc/resources/datasheets/A000066-datasheet.pdf. Accessed 16 Apr. 2024. 

[6] Tcrt5000.Pdf - Vishay, www.vishay.com/docs/83760/tcrt5000.pdf. Accessed 16 Apr. 2024. 

[7] Nawazi, Farwah. “Infrared Sensor/Detector Circuit.” Circuits DIY, 14 Sept. 2023, www.circuits-diy.com/infrared-sensor-detector-circuit/. 

[8] techZeero. “IR Sensor - IR Reveiver and Transmitter, Pinout, Specifications.” techZeero, 24 Sept. 2023, techzeero.com/sensors-modules/ir-sensor/. 

[9] Nawazi, Farwah. “HW201 Infrared (IR) Sensor Module.” Circuits DIY, 14 Sept. 2023, www.circuits-diy.com/hw201-infrared-ir-sensor-module/. 

[10] ahmedragia21. “Line Following Robot.” Electronics Forum (Circuits, Projects and Microcontrollers), Electronics Forum (Circuits, Projects and Microcontrollers), 13 Mar. 2008, www.electro-tech-online.com/threads/line-following-robot.37308/. 


