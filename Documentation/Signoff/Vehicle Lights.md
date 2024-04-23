# Vehicle Lights signoff
## Function of subsystem 
The function of this subsystem is to demonstrate Electrical and Computer Engineering concepts through physical means using the car's lighting system. This will allow users to interact with the car's lights and see the physical changes of the lights based on the user's input.  

## Constraints
Table. 1 Constraints
|Description| Constraint | Source |
|-|-|-|
|Multiplexer Voltage Safety  |The Multiplexer shall take 5 volts with a 10% tolerance, no more or less than that for this subsystem to prevent any damage to the multiplexer and ensure safe and sufficient operation.| Datasheet Requirement |
|Current Saftey / Standards |The LEDs in this subsystem shall take 15mA with a 5% tolerance, no more than that to prevent overcurrent damage and to ensure safe operation.| Datasheet Requirement  |
|Cost Considerations | Any components and equipment within this subsystem should not exceed $55 dollars and the subsystems total cost should not exceed $175 to help keep the project budget in the 400-900 range| Conceptual Design| 





      
## Buildable Schematic
![Screenshot (322)](https://github.com/abdoulm366/TTU-Capstone--Electrical-Class-Kit/assets/157627496/0826285e-c91f-42e8-a395-ecd25681fa3b)


Figure 1. Car Lights Output Schematic. 

![Screenshot (317)](https://github.com/abdoulm366/TTU-Capstone--Electrical-Class-Kit/assets/157627496/c1c1b6a9-e22a-4866-91fc-0fe491469af4)

Figure 2. Multiplexer PCB with mounting holes. 


![Screenshot (324)](https://github.com/abdoulm366/TTU-Capstone--Electrical-Class-Kit/assets/157627496/1aa214e4-13d5-42b5-ac81-800569ba72db)



Figure 3. PCB of the LEDs with current limiting resistors in series and mounting holes and screw terminals to connect inputs and grounds.

![Screenshot (325)](https://github.com/abdoulm366/TTU-Capstone--Electrical-Class-Kit/assets/157627496/8ee4c605-6f6b-40a5-a641-cb9cb3a28cad)

Figure 4. 3D model of LEDs and Multplexer PCBs.

## Analysis 

### Multiplexer
![image](https://github.com/abdoulm366/TTU-Capstone--Electrical-Class-Kit/assets/157627496/89394064-4bc7-4da3-8cb0-3c5bbf387919)

Figure 5. SN74LV4052ADBR Multiplexer

The SN74LV4052ADBR multiplexer was chosen because it allows the user to interact with the subsystem itself, and it is also compatible with the other components within this subsystem since it can operate at 5 volts and outputs more than enough current needed. The multiplexer voltage saftey constraint will be met by following datasheet requirements and limiting the input voltage to the Multiplexer to 5 volts. This will be met since the Arduino mega 2560 is only capable of outputting 5 volts maximum from its 5 volt port according to its datasheet information [1]. Since the Arduino Atmega 2560 can only output 5 volts maximum the constraint has been met and there is no need to consider any extra precautions for the multiplexer's voltage safety. 
The current safety constraint requirement will also be met by using current limiting resistors to make sure that no more than 15mA with a 5 % tolerance will flow through to the LEDs. The multiplexer datasheet also states that the multiplexer can output 50mA [4], so there needs to be current limiting resistors calculated and implemented for extra safety measures and to ensure that the LEDs can still operate smoothly. The inputs seen on the schematic can be seen in the Input bread-board subsystem as that is where the Arduino will be sending inputs from. 
 As Figure 2. shows the Multiplexer will have its own PCB that will be mounted somewhere in the center of the cab of the car near the Arduino so that the output of the multiplexer can still be connected to the front and back lights without taking up more space.  

Below are the current limitation calculations that will make sure that the constraint of 15mA with 5% tolerance is met. 

The LEDs being used range from 3 volts to 7 volts but the multiplexer can only output 5 volts since that is what it will draw. 

Resistance to get 15mA for LEDs.

$R  = \frac{5 - 4.0}{0.015}$

$200 Ω  = \frac{5 - 4.0}{0.015}$

$R = 65 Ω$ 

$R  = \frac{5 - 3.0}{0.015}$

$R = 133.3 Ω$ 

Resistance of the calculated 65 Ω shall keep the current flow to the LEDs safe, preventing damage since 5 volts is the max the LEDs will operate at for this subsystem. 


The truth table below represents the functionality of the SN74LV4052A multiplexers:

Table 2. Mux 1 functionality. 
|INH | B | A | 1Y0 | 1Y1 | 1Y2 | 1Y3 |                                               
|-|-|-|-|-|-|-|
| 0 | 0 | 0 | 1 | 0 | 0 | 0 |                        
| 0 | 0 | 1 | 0 | 1 | 0 | 0 |
| 0 | 1 | 0 | 0 | 0 | 1 | 0 |
| 0 | 1 | 1 | 0 | 0 | 0 | 1 |
| 1 | X | X | X | X | X | X |

Table 3. Mux 2 functionality. 
|INH | B | A | 2Y0 | 2Y1 | 2Y2 | 2Y3 |                                               
|-|-|-|-|-|-|-|
| 0 | 0 | 0 | 1 | 0 | 0 | 0 |                        
| 0 | 0 | 1 | 0 | 1 | 0 | 0 |
| 0 | 1 | 0 | 0 | 0 | 1 | 0 |
| 0 | 1 | 1 | 0 | 0 | 0 | 1 |
| 1 | X | X | X | X | X | X |

### Select Line / Enable Switches
![image](https://github.com/abdoulm366/TTU-Capstone--Electrical-Class-Kit/assets/157627496/7b1153e0-8184-4d8b-8c49-61c1156ea3d0)

Figure 6. Select Line / Enable Switches

The multiplexer select lines will be dip switches. The reason the dip switches have been chosen for the select lines is that they can be coded to provide the user an experience where they can slide the switches up, representing 1 and if the user slides them down, it represents a 0. This allows the users to select A and B and remain in the same states until they slide the switch again so that it will not frequently change the input being passed through without the user's desire.  These switches also operate on 5 volts so they are compatible for this subsystem. The Dip switches will be configured to an Arduino used in the input subsystem to limit the number of MCU's being used. 

### LEDs
![image](https://github.com/abdoulm366/TTU-Capstone--Electrical-Class-Kit/assets/157627496/c5ac830f-2bb1-4990-865d-90e1dc553631)

Figure 7. Car LEDs represent the ShareGoo LED Light Headlights/Taillights

The LEDs that will be used in this subsystem will be ShareGoo LED lights, headlights/taillights, white and red. These LEDs were chosen because they are cost-efficient and they are not space-consuming, taking up less room. These LEDs will be sufficient to physically represent the headlights using white LEDs and tail lights using red LEDs to accurately represent the car lights. As you can see in Figure 3. each of the 4 LEDs will need its own small PCB with mounting holes so that they can be mounted at each corner of the car, to have a real representation of lights on a car. These LEDs will be small LEDs with a housing around them to help direct them into a beam like real car headlights. These LEDs are capable of operating on a voltage range of 3 volts to 7 volts allowing them to change brightness and not just operate on one voltage. 


# BOM 
Table 4. BOM
|Item                                                         |	Location	    |Quantity |	Price 	| Total price   |
|-------------------------------------------------------------|---------------|---------|---------|---------------|
|ShareGoo 8Leds LED Light Headlights/Taillight                             |	Amazon.com	| 1	      | $8.89	  | $8.89         |
|Arduino Mega 2560	                                          | Amazon.com	  | 1	      | $48.90	| $48.90        |
|SN74LV4052A multiplexer |	Ti.com	      | 2	      | $0.948	  | $0.948         |
|Dip switch  (3 position)                     |	Mouser.com 	| 1	      | $1.47	  | $1.47         |
|Full-size Perma proto boards	                                | Adafruit.com	| 2	      | $39.90	| $39.90        |
|20 ft each 18 AWG copper wire with shielded protction(6 different color)                | Amazon.com	| 1	      | $16.49	| $16.49        |
|Resistors (200 ohms)                                | Mouser.com	| 8	      | $4.56 | $4.56       |
|		                                                          |               |         | Total:  |	$121.15      |

## References 

[1] A000067-datasheet.pdf, https://docs.arduino.cc/resources/datasheets/A000067-datasheet.pdf (accessed Apr. 10, 2024).   

[2] C++ data types, https://www.w3schools.com/cpp/cpp_data_types.asp (accessed Apr. 14, 2024).

[3] T. Cooper, “All about leds,” Adafruit Learning System, https://learn.adafruit.com/all-about-leds/forward-voltage-and-kvl (accessed Apr. 10, 2024). 

[4] Ti, https://www.ti.com/lit/ds/symlink/sn74lv4052a.pdf (accessed Apr. 16, 2024). 

[5] “What are the forward voltages of different leds?,” CircuitBread, https://www.circuitbread.com/ee-faq/the-forward-voltages-of-different-leds (accessed Apr. 9, 2024). 

 
