# Experimental Analysis: ECE EV Kit
The purpose of this document is to experimentally verify the most important design constraints of the project. Ten constraints have been designated as critical for the project's success, which are sourced from the detail design phase. Additionally, two constraints from conceptual design will be analyzed. Although there were several more constraints contained within the document, they will not be analyzed for various reasons, but they will be explained as to why they are now irrevelant.

### Experimental Analysis: Detail Design

*Safety:	The board must ensure that no voltages in excess of 50 volts are exceeded in any portion of the subsystem.	OSHA 1926.403(i)(2)(i)*

Within the system itself, the highest voltages are located within the wireless power transfer subsystem. With this being said, the voltages at the transmitter and receiver were analyzed using a multimeter. The voltages at the transmitter were recorded to be between 9.8V and 9.9V and the voltages at the receiver were recorded to be between 16V and 22V. The following measurements are recorded in pictures below. 

![image](https://github.com/user-attachments/assets/b8c4cc8c-bf84-443c-901b-99b94467b31c)
Figure 1. Transmitter Voltage

![image](https://github.com/user-attachments/assets/596f1e38-5ee2-4716-ba7b-2ddfc09011e0)
Figure 2. Receiver Voltage

*Frequency:	The system shall operate between 110 kHz and 205 kHz to optimize charging capability.	Datasheet/Wireless Charging*

Frquencies in the wireless power transfer subsystem are the most vital, considering that power will not be transmitted or received if the correct values are not obtained. Furtheremore, the recommended range is 110 kHz to 205 kHz which will not affect outside sources. Also, if the correct frequencies values are not obtained, there will be major power loss within the system. The frequency at the transmitter was measured to be roughly 126 kHz and the frequency at the receiver was measured to be roughly 127 kHz. Both of these values are well within the range. The measurements are recorded in the pictures below. 

![image](https://github.com/user-attachments/assets/6d08f2e1-ec3f-4d14-8c1a-ed3270a9e095)
Figure 3. Transmitter Frequency

![image](https://github.com/user-attachments/assets/989ccacc-682a-44ef-a389-fa2e8c505467)
Figure 4. Receiver Frequency

*Voltage:	The output shall not exceed 4.2 V to ensure there is no overcharge of the battery.	Datasheet/Digikey*

The output voltage of the wireless power transfer subsystem was designed to output no more than 4.2V in order to safely charge a 3.7V lithium ion battery. Although the subsytem will not be charging batteries as originally intended, the team still evaluated this constraint. The output voltage was measured to be between 1.7V and 2.2V which meets the constraint. The measurment is recorded in the picture below. 

![image](https://github.com/user-attachments/assets/e5f2c053-e1cc-497f-bc03-df0a7d22e63e)
Figure 5. Output Voltage

*Precision: The board must be able to detect differences of at least 1.5 times the values (100 ohms versus 150 ohms) for any electrical component and must be accurate to within 5 percent of the component’s true value*

The importance of this constraint is two-fold. For the first part, it is vital to the operation of the car that the breadboard can read several different values in a wide range.  This will ensure there are no "dead spots" in the value detection so that the system can properly respond to two different values that are relatively close. For the second part, the tolerance of the sensor circuit must be within 5% of the real value. This will make for a better user experience, as the breadboard will respond better if the resistances and capacitances being read are as accurate as possible.

![image](https://github.com/user-attachments/assets/393df9be-dc5c-45ca-9299-1aab82c6df93)

Figure 6: Measurement of a 100Ω resistor

![image](https://github.com/user-attachments/assets/8d44c769-44a1-4bf1-ba94-aa99b50a745f)

Figure 7: Measurement of a 150Ω resistor

|Breadboard Resistor Value|Multimeter Resistor Value| Difference (Percentage)|
|-|-|-|
|111Ω|98.8Ω|12.3%|
|21.6kΩ|21.5kΩ|0.4%|
|120kΩ|119.6kΩ|0.3%|

Figure 8: Table of resistor values measured by the circuit and a multimeter

As shown above, the breadbaord system is capable of detecting two unique component values that are within 1.5 times of each other. For the tolerances, the values are more than within the range of 5% of the real value. The only outlier is the 100Ω resistor. This resistor had an error of 12.3%, but this is actually acceptable. The minimum calculated resistance for the breadboard is 220Ω, so this value was below the threshold the breadboard was designed for. That explains the unusually high error value. 

*Speed: The board must be able to determine the component’s value within 1.25 seconds of it being changed to ensure smooth operation of the other systems*

As shown in both Figure 6 and Figure 7, the breadboard can make measurements in under 100ms. This value is well within the constraint of 1.25 seconds between readings, so, for both the speed and the precision of the measurement circuit of the project, the constraints have been met adequately.


*Constraint: The LEDs in this subsystem shall take no less than 3V and no more than 7V to prevent damage and to ensure safe and correct operation.*

This was the LED subsystem detail design constraint that was actually affecting to the project design.

![image](https://github.com/user-attachments/assets/c1bd52f7-f484-4c69-adbc-23132330d557)

Figure 9. Testing the voltage that the arduino is outputting to the LEDs 

As you can see in Figure 9. we tested the voltage using a multimeter to determine whether or not the voltage was outputting between 3-7 volts at which the LEDs operating range is. 

![image](https://github.com/user-attachments/assets/c1e4172b-194c-4aac-985f-e4e4662a8ae3)

Figure 10. The voltage that we measured and read at the LED input pins. 


The figure above shows that we measured within the 3-7 volt range and that proves that the constraint of no less than 3V and no more than 7V to prevent damage and to ensure safe and correct operation was met since the multimeter read 4.705 volts which is between 3 volts and 7 volts which is sufficient to operate the LEDs without also supplying to much power. 

![image](https://github.com/user-attachments/assets/0f404413-f10c-4217-8699-7dfbe2a07d9d)

Figure 11: Shows the cars error margin.

*Constraint: The system must detect if the car is veering off then immediately correct it and put it back on track. For this, the system must operate within the accepted error margin of 1.18 inches for effective correction.*

As shown in figure 11, the constraint from the closed loop control subsystem is a little off. The error margin is about 3 to 4 inches or 1.5 to 2 inches on each side of the IMU chip. It still allows for effective correction, but the car corrects itself in a wider area.

![image](https://github.com/user-attachments/assets/f29b57a7-ea5e-4e0a-b218-b2ac16bc090d)


Figure 12: Shows the testing of the cars speed.

![image](https://github.com/user-attachments/assets/cd99e899-ebef-4453-85ea-dc2e95bacbbf)


Figure 13: Shows the math to figure out the cars speed.

*Constraint: The kit's speed shall be limited to a max of -3 to 3 mph, since higher speeds may cause the car's motor to overheat.*

The constraint from the conceptual design says the car shall go no more than 3 mph forward and backward. As shown in figure 12 and 13, the team tested how many seconds it takes for the car to go 35 inches. The math is shown and the car goes 0.685 mph or 0.7 mph which meets the constraint.

*Constraint: The menu should allow easy navigation at any point with buttons such as "Return to Menu" or "Next" or "Back".*

The LCD screen will have a very user-friendly menu where any user can move back and forth through the menus without having to fully reset. The screen itself is set up so that it has an interactive menu that will say user manual, activities, etc. This allows the user to step their way into an activity or user manual so they know where they are at. It will step them through the menu with next, back, or challenge buttons so they can go forward or back out if needed. This is sufficient for this design to meet the easy navigation constraint. 










