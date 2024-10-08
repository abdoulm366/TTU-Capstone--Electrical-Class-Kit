# Logic Gates Subsystem

##  Function of the System
The function of this subsystem is to introduce the concept of logic gates through an approachable way for someone with little to no experience using AND,OR and NOT gate. The subsystem will be user-friendly by using switches and a single LED to demonstrate these concepts and allow the user to interact with the inputs. The car will be able to be set into mode through the primary screen with the two modes being AND and OR. The two modes will move the car forward and when the user flip the Not gate switch it will invert the ouput of either mode making the car go backward.


## Constraint

| Description | Constraints                                                   | Origin            |
| --- | --------------------------------------------------------------------- | -----------------|
| Current regulation | Current through the LED shall be no less than 15 mA [3] | LED Constraint |
| Voltage regulation | System shall use 5v from the Arduino UNO to operate | Device Constraint |
|  Explicit  | Switches shall be labeled for a user-friendly interaction  | simplicity Constraint|
| Cost Limit  |Any components and equipment within this subsystem should not exceed $40 dollars and the subsystems total cost should not exceed $120 to help keep the project budget in the 400-900 range| Conceptual Design|

## Buildable schematic
![image](https://github.com/user-attachments/assets/51ad26e2-d074-4c35-a2c9-f11e91a238be)






The above image is a schematic of 3 switches, a current limiting resitor and a LED connected to digital port 10, 11, 12, and 13 of the Close Control Loop arduino subsystem, responsible for moving the car. Switch 1 and 2 can be either AND or OR depending on the mode. They are respectively connected to digital port 11 and 12 of the arduino. Switch 3 is the inverter, inverting either AND or OR gate depending on the mode selcted. It is connected to digital pin 10 of the arduino. The LED will serve as an output indicating when the car is in movement, connected to digital pin 13 of the arduino.


# Analysis
If we are analyzing the current constraint, it shall not be less thant 15 mA as it is specified in the datasheet [1]. Since the arduino is operating on 5v [2], and the foward voltage of the LED is 2.2V [1], our actual voltage is 5V - 2.2V = 3.8V. Our subsystem will need a current limiting resistor to limit the current throught the LEDs. V = RI => R = $\frac{v}{I}$.     
V = 3.8V, I = 15 mA.   

R = $\frac{3.8}{0.015}$ = 253 ohms. To keep the current above 15mA, a 220 ohm resistor is perfect because it brings the current to about 17.7mA with a voltage of 3.8V. Moreover, this current is foward biased through the LED.

How will the Subsystem work? 
The user will interact with the primary screen first and then the switches. Selecting which mode to go into through the screen, the user will then interact with the switches to move the car. In AND mode the car drives forward when switch 1 and 2 are flipped. This simulates an AND gate inside the micro-controller. If switch 3 if flipped, the output of the AND gate is inverted. In OR mode the car drives forward when switch 1 or 2 are pressed. This simulates an OR gate inside the micro-controller. If switch 3 if flipped the output of the OR gate is inverted. The LED output will turn on whenever the car is moving indicating that a gate is being used. 



### Truth table for NOT,AND and OR gates.

## AND Gate
The two switches in series represent an AND gate, output will be high only when both inputs are high.

| Input   | Input    | output   | 
| ------- | -------- | ---------|
| A       | B        | Y        |             
| 0       | 0        | 0        |
| 0       | 1        | 0        | 
| 1       | 0        | 0        | 
| 1       | 1        | 1        | 

## OR Gate

The two switches in parallel represent an OR gate, output will be high when at least one input is high.  

| Input   |   Input  | output   | 
| --------|----------| -------- |  
| A       | B        | Y        |             
| 0       | 0        | 0        |
| 0       | 1        | 1        | 
| 1       | 0        | 1        | 
| 1       | 1        | 1        | 

## NOT Gate

 The single switch represent the NOT gate.  
| Input      |  output  | 
| ---------- | -------- |  
| A          | Y        |            
| 0          | 1        |            
| 1          | 0        |

## PCB Layout

![image](https://github.com/user-attachments/assets/786d235c-17eb-4e40-896e-4b721865623e)

Above demonstrates how the subsystem will be configured on a pcb. All the hardware for this subsystem will be implemented on the main input breadboard PCB.



## BOM
| DEVICE                | Quantity | Price | manufacture | Location |        Part Number|
| --------------------- | -------- | -------------- | ----------- | -------|------- |
| double Switch         | 1       | $0.57         | Same Sky     | Digikey |2223-DS04-254-2-02BK-SMT-ND  |
| Single switch         |  1       |$0.67            |Same Sky             | Digikey | 2223-DS04-254-2-01BK-SMT-ND     |
| LED                   | 1      | $0.18          | 	Würth Elektronik      | Digikey |732-5006-ND|
| 220 Ohms Resistor     | 1        | $0.10          | YAGEO     |  Digikey  |220QBK-ND|
 
 
 Total Cost: $2.21


# References
[1] https://www.mouser.com/datasheet/2/723/HB_C5SMF_RJF_RJE_GJF_GJE_BJF_BJE-3402153.pdf

[2]  “Arduino Uno REV3.” Arduino Online Shop, store-usa.arduino.cc/products/arduino-uno-rev3?gad_source=1&gclid=CjwKCAjwlbu2BhA3EiwA3yXyu4hsJT3p0tzEam3W_WHjW9Dal0CS2KojE_k9SLhoPBFiI5uEDC_3GxoCv1wQAvD_BwE. Accessed 28 Aug. 2024.

[3] https://www.ledsupply.com/blog/how-does-a-5mm-led-work/#:~:text=5mm%20LED%20Current.%20Now

[4] Digikey |https://www.digikey.com/en/products/detail/same-sky/DS04-254-2-02BK-SMT/11310860

[5] https://www.digikey.com/en/products/detail/same-sky/DS04-254-2-01BK-SMT/11310848

[6] Digikey |https://www.digikey.com/en/products/detail/w%C3%BCrth-elektronik/151031SS06000/4489982

[7] https://www.digikey.com/en/products/detail/yageo/CFR-25JB-52-220R/1295



