# Closed Loop Control

## Function of the system
The purpose of this subsystem is to drive and steer the vehicle. The subsystem will keep the car in the desired location while the car is moving on the designated mat. It will determine if the car has veered off course and adjust accordingly.

## Constraints
| Description | Constraints/Specification | Source |
|-------------|---------------------------|--------|
| Voltage | The system shall operate with the correct voltage. The motor driver shield is rated for 4.5V to 13.5V, the IMU chip is rated for 3V-5V, and the TT DC motors are recommended for 6-8V.  | [1], [3], [8] |
| Current | The motor driver shield must be capable of supplying 150mA of current per bridge for the four motors, while also supporting the IMU chip's maximum draw of 12.3mA. | [1], [3], [8] |
| Precision | The system must detect if the car is veering off then immediately correct it and put it back on track. The IMU's sampling rate must be around 100Hz to achieve the speed. | [4] |
| Socioeconomic | The system shall be cost effective relating to the project's budget constraints. | Conceptual Design |


## Build a Schematic

![image](https://github.com/abdoulm366/TTU-Capstone--Electrical-Class-Kit/assets/158520642/f186c00e-0bcb-49e3-a64d-ee6b35e7c89a)

Figure 1: Buildable Schematic

The schematic in figure 1 shows an IMU chip, Motor driver shield, four motors, and a switch. The top component is the Arduino motor shield which is the motor driver for the motors. This shield has male pins that plug into the Arduino uno to where it connects and sits on top of it [8]. It has 4 bridges that are used for the four motors which are 0.1hp/74.5 watts a piece [3]. It also has SDA and SCL pins which are necessary for I2C communication. These pins allow it to interface with devices such as the IMU chip that communicate using the I2C protocol [1].

The bottom component is the IMU BNO055 chip [2]. The two communication pins on the IMU are labeled SDA and SCL and those go to the SDA and SCL pins of the shield [2]. The IMU can tell if the vehicle is speeding up, turning, or changing direction because it consists of accelerometer, gyroscope, and magnetometer sensors [4]. It can detect the orientation of the vehicle in space. This means it can determine whether the car is tilted to one side, leaning forward or backward, or facing in a certain direction [4]. To bring everything together, a program will need to be made for it. The vehicle has 4 wheels and to turn left the right wheels will speed up and to turn right the left wheels will speed up, which is called differential steering [9]. The vehicle must be able to drive and turn on any pad or terrain. The IMU knows the orientation so by doing testing, the speed of the wheels can be figured out. Overall, an IMU chip allows the vehicle to drive the desired path anytime anywhere.

The system is a closed loop. Based on figure 2 below, the IMU sends signals through the shield to the Arduino uno. They run through the program algorithm and the commands go to the motor driver and motors. This is a closed loop because it then goes back to the IMU. The IMU reads the vehicles orientation which changes due to the motors/wheels. In this there are feedback wires which are the IMU’s wires (SDA and SCL) that connect to the shield/Arduino uno. To explain and show the difference between an open loop and closed loop, the feedback wires have a wire connector that can be unplugged and plugged back in shown in figure 1. To show the open loop, it can be unplugged making the vehicle drive off on an undesired path. The vehicle will still drive, but it will not have information on the vehicle’s orientation.

![image](https://github.com/abdoulm366/TTU-Capstone--Electrical-Class-Kit/assets/158520642/e86b32e6-26a6-4bb8-ba92-c49487ed853b)
Figure 2: Closed Loop Block Diagram

## Analysis
Analyzing the voltage and current constraints: The system shall operate with the correct voltage and current. Overvoltage or excessive current can lead to malfunctions and overload. Overload can lead to overheating and other electrical hazards that can cause a safety factor. The IMU chip is rated for 3V-5V and a maximum draw of 12.3 mA [2]. The motor driver shield is rated for 4.5V to 13.5V and provides 1.2A per bridge [1]. The TT DC motors are rated for 3V-12V but are recommended for 6-8V and has a rating of 150 mA [3]. The TT motors rating works for the motor driver shields rating. Knowing and understanding the voltage and current specifications of each component ensures safe operation.

Analyzing the precision constraint: The design of the mat is unknown, but the vehicle should be able to be put on any mat at any time and go the correct path. The IMU has a sampling rate of 100Hz meaning it takes samples or measurements 100 times a second [2]. This speed will allow the vehicle to make quick adjustments to stay on course. On the control algorithm side, the speed of the motors is set in the program. The vehicles speed does not need to be too fast, or it will turn the car too rapidly. Testing with the vehicle will allow the needed speed.

Analyzing the socioeconomic constraint: The budget of the project must be kept in mind for this design. It shall be cost-effective while also being high in quality. This system is a crucial, so it needs to be reliable. 



## Bill of Materials (BOM)
| Item Name | Details | Quantity | Cost | Source |
|-----------|---------|----------|------|--------|
| Arduino Uno | Rev 3 | 1 | $27.60 | https://shorturl.at/bdoY9 |
| IMU Chip| BNO055| 1 | $29.95 | https://shorturl.at/djHIU |
| Arduino Motor Driver Shield | Adafruit| 1 | $6.39 | https://shorturl.at/swxW7 |
| DC motors/Wheels | TT Gearbox motors | 4 | $9.99 | https://shorturl.at/pCJW0 |
| Switch | CH755-ND | 1 | $1.41 | https://shorturl.at/hwAES |
| Connector | Unpluggable wire connector | 1 | $1.00 | https://shorturl.at/ikGU5 |
| Jumper Wires | Female/male wires 20 x 3" | 1 | $1.95 | https://shorturl.at/pAI05 |

Total cost for subsystem: $78.29 (not including tax or shipping)


## References 
[1] Ada, Lady. “Adafruit Motor Shield V2.” Adafruit Learning System, learn.adafruit.com/adafruit-motor-shield-v2-for-arduino/overview. Accessed 21 Apr. 2024. 

[2] Industries, Adafruit. “Adafruit 9-DOF Absolute Orientation IMU Fusion Breakout - BNO055.” Adafruit Industries Blog RSS, www.adafruit.com/product/4646?gad_source=1&gclid=CjwKCAjwrIixBhBbEiwACEqDJRxpEfCV4q0WhgjdSM4tUE4NWJBCDTxvNpl-DCeiDWauHM3nBt7YKhoC59YQAvD_BwE. Accessed 19 Apr. 2024. 

[3] Amazon.Com: 2pcs DC Electric Motor 3-6V Dual Shaft Geared TT Magnetic ..., www.amazon.com/Aoicrie-Electric-Magnetic-Engine%EF%BC%8CDIY-Vibration/dp/B083BDW3FD. Accessed 16 Apr. 2024. 

[4] Hayward, Laura. “Inertial Measurement Unit (IMU) - an Introduction.” Advanced Navigation, 8 Jan. 2024, www.advancednavigation.com/tech-articles/inertial-measurement-unit-imu-an-introduction/. 

[5] A000066-Datasheet.Pdf, docs.arduino.cc/resources/datasheets/A000066-datasheet.pdf. Accessed 16 Apr. 2024. 

[6] Tcrt5000.Pdf - Vishay, www.vishay.com/docs/83760/tcrt5000.pdf. Accessed 16 Apr. 2024. 

[7] BNO055 Intelligent 9-Axis Absolute Orientation Sensor, cdn-shop.adafruit.com/datasheets/BST_BNO055_DS000_12.pdf. Accessed 19 Apr. 2024.  

[8] Industries, Adafruit. “Adafruit Motor/Stepper/Servo Shield for Arduino v2 Kit.” Adafruit Industries Blog RSS, www.adafruit.com/product/1438. Accessed 21 Apr. 2024. 

[9] Wsurging, and Instructables. “Differential Steering Car with Arduino.” Instructables, Instructables, 29 Feb. 2020, www.instructables.com/Differential-Steering-Car-With-Arduino/. 

