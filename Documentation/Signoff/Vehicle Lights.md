# Vehicle Lights signoff
## Function of subsystem 
The function of this subsystem is to demonstrate Electrical and Computer Engineering concepts through physical means using the car's lighting system. This will allow users to interact with the car's lights and see the physical changes of the lights based on the user's input.  

## Constraints
Table. 1 Constraints
|Description| Constraint | Source |
|-|-|-|
|Current Saftey / Standards |The LEDs in this subsystem shall take no more than 30 mA with 5% tolerance to prevent overcurrent damage and to ensure safe operation.| Datasheet Requirement  |
|Cost Considerations | Any components and equipment within this subsystem should not exceed $55 dollars and the subsystems total cost should not exceed $175 to help keep the project budget in the 400-900 range| Conceptual Design| 





      
## Buildable Schematic
![Screenshot (331)](https://github.com/abdoulm366/TTU-Capstone--Electrical-Class-Kit/assets/157627496/49e58fe5-f79f-4d77-b639-a3ca8ae347ac)

Figure 1. Car Lights Output Schematic. 


![Screenshot (328)](https://github.com/abdoulm366/TTU-Capstone--Electrical-Class-Kit/assets/157627496/d3876f99-20f8-4d8c-9553-25ba3aa63a5f)


Figure 2. PCB of the LEDs with current limiting resistors in series and mounting holes and screw terminals to connect inputs and grounds.


![Screenshot (329)](https://github.com/abdoulm366/TTU-Capstone--Electrical-Class-Kit/assets/157627496/0ca7a289-744e-4c3f-abbd-902888bc37fb)

Figure 3. 3D model of LEDs.

## Analysis 

### Select Line / Enable Switches
![Screenshot (332)](https://github.com/abdoulm366/TTU-Capstone--Electrical-Class-Kit/assets/157627496/c541203a-d3cf-4507-8a1c-0317dd3936fb)


Figure 4. Select input / Enable Switches

Dip switches will be used to control the input sent to the LEDs. The reason behind using dip switches is to give the user a better learning experience by allowing them to slide the switch up representing a 1 and slide down representing 0, they will also be able to visualize it. Based on the user input through the switches the output will be affected accordingly. The switches will be configured to the Arduino within the input system and coded so the state will be read by the Arduino. Below is a truth table that will represent the dip switches functionality. The dip switches will represent select lines to the coded functionality of a multiplexer. 

Table 2. Dip switches functionality. 
|Enable pin 1| A pin 2 | B pin 3| Output Enable pin 6 | Output A pin 5 | Output B pin 4|                                              
|-|-|-|-|-|-|
| 0 | 0 | 0 | 0 | 0 | 0 |                   
| 0 | 0 | 1 | 0 | 0 | 0 | 
| 0 | 1 | 0 | 0 | 0 | 0 | 
| 0 | 1 | 1 | 0 | 0 | 0 | 
| 1 | 0 | 0 | 1 | 0 | 0 | 
| 1 | 0 | 1 | 1 | 0 | 1 | 
| 1 | 1 | 0 | 1 | 1 | 0 | 
| 1 | 1 | 1 | 1 | 1 | 1 |

Using this truth table, each of the different outputs in the table will correspond to different physical outputs on the car headlights. If the user does not slide switch one, the enable pin, then the car lights will be off no matter what state the other two switches are in. If the user slides the enable switch up activating the switch to a 1 then the lights will come on, representing the way car lights turn on and off by using a switch, this input will be coded as a default value just to turn on all the LEDs. From looking at the truth table, if the enable is 1 and B is 1 then this means the lighting system is enabled, and this switch input will represent right turn signals which will be coded using pulse width modulation. This allows changing the duty cycle and frequency. Changing the duty cycle will lower the voltage which allows it to output various voltages, and changing the frequency of the wave will allow it to show the differences in blinking speeds and slow it down enough that the user can visualize the changes on the output based on the given input. The next enabled input where A is 1 and B is 0 will also use the same method as the left turn signals but will represent the right turn signals of the car. The next enabled input will be A is 1 and B is 1 which will represent the brightness of the car lights to show the differences that certain inputs have on the car's lights. This will also be coded using pulse width modulation to change the duty cycle so that it can output various voltages changing the brightness of the headlights. 



### LEDs
![image](https://github.com/abdoulm366/TTU-Capstone--Electrical-Class-Kit/assets/157627496/c5ac830f-2bb1-4990-865d-90e1dc553631)

Figure 5. Car LEDs represent the ShareGoo LED Light Headlights/Taillights

The LEDs that will be used in this subsystem will be ShareGoo LED lights, headlights/taillights, white and red. These LEDs were chosen because they are cost-efficient and they do not consume much space. These LEDs will be sufficient to physically represent the headlights using white LEDs and tail lights using red LEDs to accurately represent the car lights. As you can see in Figure 2. each of the 4 LEDs will need its own small PCB with mounting holes so that they can be mounted at each corner of the car, to have a real representation of lights on a car. These LEDs will be small LEDs with a housing around them to help direct them into a beam like real car headlights. These LEDs are capable of operating on a voltage range of 3 volts to 7 volts allowing them to change brightness. 


Below is a simulation proving that current limiting resistors of 145 ohms will meet the maximum current constraint by keeping the current from exceeding 30mA with a 5% tolerance. This simulation also represents the pulse width modulation concept using high frequencies. 

![Screenshot (333)](https://github.com/abdoulm366/TTU-Capstone--Electrical-Class-Kit/assets/157627496/ffbf80a8-b81d-4981-9ab2-78da86bb2b70)





# BOM 
Table 3. BOM
|Item                                                         |	Location	    |Quantity |	Price 	| Total price   |
|-------------------------------------------------------------|---------------|---------|---------|---------------|
|ShareGoo 8Leds LED Light Headlights/Taillight                             |	Amazon.com	| 1	      | $8.89	  | $8.89         |
|Dip switch  (3 position)                     |	Mouser.com 	| 1	      | $1.47	  | $1.47         |
|20 ft each 18 AWG copper wire with shielded protction(6 different color)                | Amazon.com	| 1	      | $16.49	| $16.49        |
|Resistors (145 ohms)                                | Mouser.com	| 8	      | $4.56 | $4.56       |
|		                                                          |               |         | Total:  |	$31.41     |

## References 

[1] A000067-datasheet.pdf, https://docs.arduino.cc/resources/datasheets/A000067-datasheet.pdf (accessed Apr. 10, 2024).   

[2] T. Cooper, “All about leds,” Adafruit Learning System, https://learn.adafruit.com/all-about-leds/forward-voltage-and-kvl (accessed Apr. 10, 2024). 

[3] “What are the forward voltages of different leds?,” CircuitBread, https://www.circuitbread.com/ee-faq/the-forward-voltages-of-different-leds (accessed Apr. 9, 2024). 

 
