# Direction Sensor Subsystem

## Function of the system
This subsystem is designed so the car will go in a straight line and not veer off course. An IMU chip will be used to help the system know if it is by sending signals. When it senses its going off course, it tells the front two servo motors to adjust the wheels in a certain direction to keep the car on track. So basically, the subsystem makes sure the car goes where it is pointed and stays on that path. It is almost like having an automatic steering system in it.

## Constraints
The subsystems constraints are as follows:

1.	The weight distribution of the car will not be perfect. One side will weigh more than the other side and this must be accounted for. A car with more weight on one side will naturally turn that direction. So, the program will have to be written to adjust for this weight.

2.	When the physical part of the car is designed, a place for the IMU chip, even though it is small, must be planned out so it is not in the way of anything else. It also needs to be known that the wires need a mapped-out route to the motor and Arduino. So basically, the car needs a place for the IMU chip and wires to make sure it doesn’t disrupt other subsystems and the functionality of the car.

3.	The components must have the correct voltage and current levels provided by the power source. This constraint makes sure that everything works properly, operates safely, and does not malfunction.


4.	The IMU chip must be able to communicate with the microcontroller using a communicative language. The BNO055 IMU chip typically communicates using the Inter-Integrated Circuit (I2C) protocol, so this needs to be used. The microcontroller in use must also be able to communicate with this same data transfer technique. 

5.	Another constraint is the servo motor that will be used. The size of the motor and wheels needs to be thought of when building the design and frame of the car to make sure everything fits. Also based on the weight of the car, the motor needs to be powerful enough to move it the desired speed. 

6.	On the ethics side, it needs to be made sure that the subsystem prioritizes energy efficiency to conserve energy for other subsystems which should not be a problem. Also, making sure that who the materials come from, and any manufacturing process does not cause harm to the environment.

7.	The socioeconomic constraint focuses on everything being affordable so it can be purchased by anyone. It is important that financial concerns are not in the way of participation in this project. So knowing all prices will be added up, this subsystem needs to be cost effective with high quality.

## Build a Schematic
![image](https://github.com/abdoulm366/TTU-Capstone--Electrical-Class-Kit/assets/158520642/e751a513-c766-46b9-abf6-8da3bf055f8d)
Figure 1: Buildable Schematic

Note: Pins COM0 and COM1 on the IMU Chip (BNO055) are both SDA and SCL in the datasheet, which are communication lines [1]. Also, the signal pin on the servo motors should be connected to PWM pins on the board. For the two motors, it is pin 9 and 10 [4]. 
Note: The two servo motors shown in the buildable are the front two of the car. The front two wheels are the only ones that will turn left and right to keep the car from veering off.

## Analysis
![image](https://github.com/abdoulm366/TTU-Capstone--Electrical-Class-Kit/assets/158520642/3218949a-bab7-4310-8814-18999bf6aea0)

Figure 2: Program Outline

The primary function of this subsystem is to make sure the car goes in a straight line. Based on the buildable schematic, the two connected communication lines between the IMU Chip (BNO055) and Arduino uno is how the Arduino gets the signal [1]. The chip reads that the car is veering off path and lets the Arduino know. The Arduino also has a communication line from the motor which is the PWM. When the Arduino gets the signal from the IMU chip, it sends it to the servo motor to adjust the steering. This makes a closed loop design. But the program is what allows all of this to happen. When the signal passes through the Arduino, it is passing through the program and is sent to the motor/wheels. It is hard to know exactly what the program will look like right now with no testing, but a basic outline can be made which is pictured above in Figure 2.

For the constraints, the weight distribution will be adjusted in the program by doing tests and the location of each component will be mapped out in the cars frame design. The power source is another subsystem that will allow the correct voltage and current levels for the Arduino uno. The IMU chip (BNO055) is rated for 3 to 5 V which is perfect for the Arduino uno [2].  The Arduino uno can also communicate in I2C protocol which is what’s needed for the IMU chip [3]. The car is going to be built based on the motor/wheels purchased to make sure everything fits. With all the subsystem’s components together, the weight of the car is not expected to be heavy. The servo motor is rated for 5V, and it also has enough torque for the weight [4]. The wheels will also have a range of motion of 60 degrees to turn which is enough for the car to adjust and stay straight [4]. The wheels that come with the servo motor are too small, so the purchase of a set with a diameter of approximately 3 inches will work best for the car.

## Bill of Materials (BOM)
| Item Name | Details | Quantity | Description | Cost |
|-----------|---------|----------|-------------|------|
| Aduino Uno | Rev 3 | 1 | Microcontroller for the program | $27.60 |
| IMU Chip | BNO055 | 1 | The sensor for the design | $29.95 |
| Servo Motors | Deegoo MG996R Digital Servo Motor for Futaba JR RC | 4 | So the car can move and turn | $19.98 |
| Jumper Wires | adafruit Female/male wires 20 x 3" | 1 | To connect pins | $1.95 |
| Wheels | 80mm Rubber Wheels Match Gear Motor Servo Wheels Accessories | 4 | The servo motor pack comes with wheels, but the car design needs bigger ones | $20.88 |

Total cost for subsystem: $100.36 (not including tax or shipping) 

Note: This subsystem only uses the front two servo motors, but going ahead and buying a 4 pack is more cost effective.

## References 
[1] BNO055 Intelligent 9-Axis Absolute Orientation Sensor, cdn-   shop.adafruit.com/datasheets/BST_BNO055_DS000_12.pdf. Accessed 10 Apr. 2024.

[2] Industries, Adafruit. “Adafruit 9-DOF Absolute Orientation IMU Fusion Breakout - BNO055.” Adafruit Industries Blog RSS, www.adafruit.com/product/4646?gad_source=1&gclid=Cj0KCQjwq86wBhDiARIsAJhuphnxW2m_SwgnKcs4Gez7tfCW300PDQiXQyLZ4vT5_kNyDr93Mq30HIaApBfEALw_wcB. Accessed 10 Apr. 2024. 

[3] “Inter-Integrated Circuit (I2C) Protocol.” Docs.Arduino.Cc, docs.arduino.cc/learn/communication/wire/. Accessed 10 Apr. 2024. 

[4] “Servo Motor Basics with Arduino.” Docs.Arduino.Cc, docs.arduino.cc/learn/electronics/servo-motors/. Accessed 10 Apr. 2024. 


