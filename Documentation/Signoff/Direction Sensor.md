# Closed Loop Control

## Function of the system
The purpose of this subsystem is to drive and steer the vehicle. The subsystem will keep the car in the desired location while the car is moving. It will determine if the car has veered off course and adjust accordingly.

## Constraints
| Description | Constraints/Specification | Origin |
|-------------|---------------------------|--------|
| Voltage | The system shall operate with the correct voltage. The arduino uno is rated for 7V-12V. The motor driver shield is rated for 4.5V-13.5V, the IMU chip is rated for 3V-5V, and the TT DC motors are rated for 3-12V. | Datasheet Requirement |
| Current | The motor driver shield must be capable of supplying 210mA of current per bridge for the four motors, while also supporting the IMU chip's maximum draw of 12.3mA. | Datasheet Requirement |
| Cost Boundaries | Equipment/components should not surpass $35, with the total capped at $90 to ensure the project's final total falls within the $400 to $900 budget. | Conceptual Design |
| Response | The system must detect if the car is veering off then immediately correct it and put it back on track. For this, the system must operate within the accepted error margin of 0.030 meters for effective correction. | Function Requirement |

## Buildable Schematic

![image](https://github.com/user-attachments/assets/eaab8e0b-e845-4ae7-81f7-08fe98baca1a)

Figure 1: Buildable Schematic

The schematic in figure 1 shows an Arduino Uno, IMU chip, Motor driver shield, four motors, switch, and a connector. The middle component is the Arduino motor shield which is the motor driver for the motors. This shield has male pins that plug into the Arduino uno to where it connects and sits on top of it [8]. It has 4 bridges that are used for the 4 motors which are 0.1hp/74.5 watts a piece [3]. It also has SDA and SCL pins which are necessary for I2C communication. These pins allow it to interface with devices such as the IMU chip that communicate using the I2C protocol [1].

The bottom component is the IMU BNO055 chip [2]. The two communication pins on the IMU are labeled SDA and SCL and those go to the SDA and SCL pins of the shield [2]. The IMU can tell if the vehicle is speeding up, turning, or changing direction because it consists of accelerometer, gyroscope, and magnetometer sensors [4]. It can detect the orientation of the vehicle in space. This means it can determine whether the car is tilted to one side, leaning forward or backward, or facing in a certain direction [4]. To bring everything together, a program will need to be made for it. The vehicle has 4 wheels and to turn left to keep the car on track, the right wheels will speed up and to turn right the left wheels will speed up, which is called differential steering [9]. The IMU knows the orientation so by doing testing, the speed of the wheels can be figured out. Overall, an IMU chip allows the vehicle to drive the desired path anytime anywhere.

The system is a closed loop. Based on figure 2 below, the IMU sends signals through the shield to the Arduino uno. They run through the program algorithm and the commands go to the motor driver and motors. This is a closed loop because it then goes back to the IMU. The IMU reads the vehicles orientation which changes due to the motors/wheels. In this, there are feedback wires which are the IMU’s SDA and SCL wires that connect to the shield/Arduino uno. To explain and show the difference between an open loop and closed loop, the feedback wires have a wire connector that can be unplugged and plugged back in shown in figure 1. To show the open loop, it can be unplugged making the vehicle drive off on an undesired path. The vehicle will still drive, but it will not have information on the vehicle’s orientation.

![image](https://github.com/abdoulm366/TTU-Capstone--Electrical-Class-Kit/assets/158520642/e86b32e6-26a6-4bb8-ba92-c49487ed853b)
Figure 2: Closed Loop Block Diagram

## Analysis
Analyzing the voltage and current constraints: The system shall operate with the correct voltage and current. Overvoltage or excessive current can lead to malfunctions and overload. Overload can lead to overheating and other electrical hazards that can cause a safety factor. The IMU chip is rated for 3V to 5V and a maximum draw of 12.3 mA [2]. The arduino uno is rated for 7V to 12V [12].The motor driver shield is rated for 4.5V to 13.5V, which works for the arduino uno, and provides 1.2A per bridge [1]. The TT DC motors are rated for 3V to 12V and have a rating of 210 mA [3]. The TT motors rating works for the motor driver shields rating. Knowing and understanding the voltage and current specifications of each component ensures safe operation.

Analyzing the budget cost boundaries: To ensure budget constraints are followed, individual components shall not exceed $35, and the total shall not exceed $90. The $400-$900 budget must be kept in mind for this design. In addition, keeping costs low has good effects on the economy. It shall be cost-effective while also being high in quality. This system is crucial, so it needs to be reliable. 

Analyzing the response constraint: The systems specifications are chosen for effective operation. The IMU BNO055’s 100Hz sampling rate ensures a fast rate, keeping the vehicle on the desired path [2]. Motors operating at 300±10% rpm provide the necessary torque for corrective actions [3]. The accepted error margin of 0.030 meters is the desired level for corrections, minimizing the risk of the vehicle veering off course [11]. The calculations below show an explanation for the selection of these components and values.

The motors speed rating is 300±10% rpm for the 9V outside power source, which is approximately 290-310 rpm, and the wheels diameter is 2.6 inches [3].  Using the equation below, the approximate mile per hour can be figured out [10].

$\frac{rpm * wheel-diameter * π * 60}{63360} = \frac{300 * 2.16 * π * 60}{63360}$ = 2.32 mph (60 minutes in an hour)(63360 inches in a mile)

This is the speed for just the motors, not while they are on the vehicle. When on the vehicle, it will not go this speed due to the circumstances of the vehicles weight, wheel friction, terrain, etc. By doing calculations, we can find out the range of speed needed based on the 100Hz sampling rate and how much error is acceptable. By using the motors speed of 2.32 mph, the first step is finding the distance covered per sample:

$\frac{2.32 * 5280}{3600}$ = 3.402ft/s (1 mile = 5280ft) (1 hour = 3600 seconds)

Then, find the distance covered per sample: 

$3.402 \times \frac{1}{100}$ = 0.03402ft/sample (Velocity * Time Interval)

So every 100Hz sample the vehicle will cover 0.03402 feet. A margin of 30mm or 0.030 meters can be an accepted error [11]. By using this, we can calculate if 2.32 miles per hour works for the accepted error margin:

$2.32 \times  \frac{1609.34}{3600}$  = 1.104 m/s (1609.34 meters per mile)

$1.104 \times \frac{1}{100}$ = 0.0104 m/sample

Since the accepted error is 0.030 meters and the distance covered per sample is approximately 0.0104 meters, the vehicle will move within the accepted error margin each sample. The max mile per hour can be shown in the table below:

| Vehicle Speed (mph) | Distance Covered Per Sample (ft/sample) | Error Margin (m/sample) |
|--------------------|------------------------------------------|---------------------------|
| 1 | 0.0146 | 0.0047 |
| 2 | 0.0293 | 0.0089 |
| 2.32 | 0.0340 | 0.0104 |
| 3 | 0.0440 | 0.0134 |
| 4 | 0.0586 | 0.0179 |
| 5 | 0.0733 | 0.0235 |
| 6 | 0.0880 | 0.0268 |
| 6.71 | 0.0984 | 0.0300 |

Since the motors speed of 2.32 mph fit the constraint, any mile per hour less than 2.32 will also work. Using the same calculations for the table above, 6.71 is the max mph the car can go for the accepted error margin. With the IMU's 100Hz sampling rate, 0 to 6.71mph is the precise range that is appropriate and sufficient based on the 0.030 meters of error. This accepted error margin allows the vehicle a small amount of room to work with but is enough for the vehicle to stay on the desired path with the IMU’s 100Hz sampling rate [11].

## Bill of Materials (BOM)
| Item Name | Details | Quantity | Cost | Source |
|-----------|---------|----------|------|--------|
| Arduino Uno | Rev 3 | 1 | $27.60 | https://shorturl.at/bdoY9 |
| IMU Chip| BNO055| 1 | $29.95 | https://shorturl.at/djHIU |
| Arduino Motor Driver Shield | Adafruit| 1 | $6.39 | https://shorturl.at/swxW7 |
| DC motors/Wheels | TT Gearbox motors | 4 | $8.99 | https://shorturl.at/sIVY2  |
| Switch | CH755-ND | 1 | $1.41 | https://shorturl.at/hwAES |
| Connector | Unpluggable wire connector | 1 | $1.00 | https://shorturl.at/ikGU5 |
| Jumper Wires | Female/male wires 20 x 3" | 1 | $1.95 | https://shorturl.at/pAI05 |

Total cost for subsystem: $77.29 (not including tax or shipping)

## References 
[1] Ada, Lady. “Adafruit Motor Shield V2.” Adafruit Learning System, learn.adafruit.com/adafruit-motor-shield-v2-for-arduino/overview. Accessed 21 Apr. 2024. 

[2] Industries, Adafruit. “Adafruit 9-DOF Absolute Orientation IMU Fusion Breakout - BNO055.” Adafruit Industries Blog RSS, www.adafruit.com/product/4646?gad_source=1&gclid=CjwKCAjwrIixBhBbEiwACEqDJRxpEfCV4q0WhgjdSM4tUE4NWJBCDTxvNpl-DCeiDWauHM3nBt7YKhoC59YQAvD_BwE. Accessed 19 Apr. 2024. 

[3] Amazon.Com: DC 3V-12V TT Dual Shaft Gear Motor 1:48 with Tire Wheel Kit for UNO 4WD Arduino Robot Smart Car Eletronic DIY Toys, 4x TT Motor,4X Tire Wheel : Toys & Games, www.amazon.com/3V-12V-Dual-Shaft-Gear-Motor/dp/B08BZJSNZQ. Accessed 25 Apr. 2024. 

[4] Hayward, Laura. “Inertial Measurement Unit (IMU) - an Introduction.” Advanced Navigation, 8 Jan. 2024, www.advancednavigation.com/tech-articles/inertial-measurement-unit-imu-an-introduction/. 

[5] A000066-Datasheet.Pdf, docs.arduino.cc/resources/datasheets/A000066-datasheet.pdf. Accessed 16 Apr. 2024. 

[6] Tcrt5000.Pdf - Vishay, www.vishay.com/docs/83760/tcrt5000.pdf. Accessed 16 Apr. 2024. 

[7] BNO055 Intelligent 9-Axis Absolute Orientation Sensor, cdn-shop.adafruit.com/datasheets/BST_BNO055_DS000_12.pdf. Accessed 19 Apr. 2024.  

[8] Industries, Adafruit. “Adafruit Motor/Stepper/Servo Shield for Arduino v2 Kit.” Adafruit Industries Blog RSS, www.adafruit.com/product/1438. Accessed 21 Apr. 2024. 

[9] Wsurging, and Instructables. “Differential Steering Car with Arduino.” Instructables, Instructables, 29 Feb. 2020, www.instructables.com/Differential-Steering-Car-With-Arduino/. 

[10]Moubarak, Salam. “RPM Calculator - Rpm to Mph.” Omni Calculator, Omni Calculator, 18 Jan. 2024, www.omnicalculator.com/everyday-life/rpm. 

[11] “Line Following.” Line Following - SunFounder PiCar-S Documentation, docs.sunfounder.com/projects/picar-s/en/latest/line_following.html#:~:text=Rules%20for%20making%3A,distance%20of%20two%20nonadjacent%20probes&text=whole%20module%2C%20to%20prevent%20the,lines%20at%20the%20same%20time. Accessed 22 Apr. 2024. 

[12] “Arduino Uno REV3.” Arduino Online Shop, store-usa.arduino.cc/products/arduino-uno-rev3?gad_source=1&gclid=CjwKCAjwlbu2BhA3EiwA3yXyu4hsJT3p0tzEam3W_WHjW9Dal0CS2KojE_k9SLhoPBFiI5uEDC_3GxoCv1wQAvD_BwE. Accessed 28 Aug. 2024. 

