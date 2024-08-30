# Vehicle Lights signoff
## Function of subsystem 
The function of this subsystem is to demonstrate Electrical and Computer Engineering concepts through physical means using the car's lighting system. This will allow users to interact with the car's lights and see the physical changes of the lights based on the user's input.  

## Constraints
Table. 1 Constraints
|Description| Constraint | Source |
|-|-|-|
|Current Saftey / Standards |The LEDs in this subsystem shall take no more than 20 mA with 5% tolerance to prevent overcurrent damage and to ensure safe operation.| Datasheet Requirement  |
|Cost Considerations | Any components and equipment within this subsystem should not exceed $40 dollars and the subsystems total cost should not exceed $120 to help keep the project budget in the 400-900 range| Conceptual Design| 





      
## Buildable Schematic
![image](https://github.com/user-attachments/assets/c47e4d78-0a15-4318-b494-09bd6bab0013)

Figure 1. Car Lights Output Schematic. 


![image](https://github.com/user-attachments/assets/b08d7794-4854-4fa5-bc48-4e394aca1a2e)


Figure 2. PCB of the LEDs with current limiting resistors in series and mounting holes and screw terminals to connect inputs and any grounds.

![image](https://github.com/user-attachments/assets/2ba29565-6127-4d34-94f4-e0f350534df3)

Figure 3. PCB of the dip switch with CPU input to the switches and screw terminals to connect both the switch output and the input the switch allows through to the different LEDs.


![image](https://github.com/user-attachments/assets/10809dc4-c311-4016-81f0-750288931a8e)


Figure 4. 3D model of LEDs.

![image](https://github.com/user-attachments/assets/57745358-546d-46a9-8ac4-165cf79125cd)


Figure 5. 3D model of Dip SW 

## Analysis 

### Select Line / Enable Switches
![image](https://github.com/user-attachments/assets/e414383f-0a64-4c0d-b218-7a5033957ce9)



Figure 6. Select input / Enable Switches

Dip switches will be used to control the input sent to the LEDs. The reason behind using dip switches is to give the user a better learning experience by allowing them to slide the switch up representing a 1 and slide down representing 0, they will also be able to visualize it. Based on the user input through the switches the output of this subsystem will be affected accordingly. The switches will be configured to the Arduino 2560 within the input system and coded so the state will be read by the Arduino 2560 which is the master CPU. The CPU will process that data and send it out of a digital pin to the headlights. Below is a truth table that will represent the dip switches functionality. The dip switches will represent select lines to the coded functionality of a multiplexer. The dip switches will take in data from the Master CPU and to do that the switches will have solder wire holes so that the wires from the CPU can be soldered into the holes that are traced over to the input side of the switch. This is represented in Figure 5. as j4, j5, and j7. The Dip switch pins 4, 5, and 6 will all be connected into an 8-level terminal block where pin 6 needs to go to every LED because that will be the ON/OFF switch. This means pin 6 will have 4 of those terminals that will all be traced together, which is shown in the 3D model in Figure 5., and wire will be from those terminals to each current limiting resistor as needed. Pin 4 will have 2 of those terminals that are traced together since it will send its output to two LEDs to represent the turn signals. Pin 5 will also have two terminals traced together so it can represent the other turn signals.

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

Using this truth table, each of the different outputs in the table will correspond to different physical outputs on the car headlights. If the user does not slide switch one, the enable pin, then the car lights will be off no matter what state the other two switches are in. If the user slides the enable switch up activating the switch to a 1 and A and B are 0 then the lights will come on, representing the way car lights turn on and off by using a switch, this input will be coded as a default value just to turn on all the LEDs. From looking at the truth table, if the enable is 1, A is 0 and B is 1 then this means the lighting system is enabled, and this switch input will represent left turn signals. The next enabled input where A is 1 and B is 0 will also use the same method as the left turn signals but will represent the right turn signals of the car. The next enabled input will be A is 1 and B is 1 which will represent the brightness of the car headlights to show the differences that certain inputs have on the car's lights. 

This will also be coded using pulse width modulation to change the duty cycle so that it can output various voltages changing the brightness of the headlights. Pulse width modulation can be utilized to control both the intensity of the LED's light and the speed of the blinking. Pulse width modulation, or PWM, is a sqaure pulse that alternates between 0 volts and a nominal voltage. If the pulse's frequency is fast enough, the changes made to it will not be perceptible to the naked eye. These changes are as follows: changing the duty cycle, or the time for which the pulse is at the nominal voltage, will effectively lower the voltage seen to the naked eye at the LED. This will make the LED appear dimmer. The frequency can also be changed. If the frequency is lowered to a point at which the human eye can detect it, then it can be lowered or increased in order to change the rate at which the LED's "blink" when the blinker function is selected.



### LEDs
![image](https://github.com/user-attachments/assets/14f8d1ab-3d57-4118-b6e1-5be83de74506)


Figure 7. Car LEDs represent the ShareGoo LED Light Headlights/Taillights

The LEDs that will be used in this subsystem will be ShareGoo LED lights, headlights/taillights, white and red. These LEDs were chosen because they are cost-efficient and they do not consume much space. These LEDs will be sufficient to physically represent the headlights using white LEDs and tail lights using red LEDs to accurately represent the car lights. As you can see in Figure 4. each of the 4 LEDs will need its own small PCB with mounting holes so that they can be mounted at each corner of the car, to have a real representation of lights on a car. These LEDs will be small LEDs with a housing around them to help direct them into a beam like real car headlights. These LEDs are capable of operating on a voltage range of 3 volts to 7 volts allowing them to change brightness. These LEDs will be configured to an Arduino that is within the input system. As you can see in the Figure above the resistors will take in what switch pins 4, 5, and 6 output. A terminal block will take in inputs from the switch pins and then that terminal block will be traced to the resistor that is traced to the LEDs,  as seen in Figure 4. the 3D model. 


This simulation represents the pulse width modulation concept which controls the LEDs. This also proves that the overcurrent protection works as intended. 

![image](https://github.com/user-attachments/assets/86fb9523-2334-4013-a515-9cbc753ebdab)

Figure 8. PWM and overcurrent protection simulation. 





# BOM 
Table 3. BOM
|Item                                                         |	Distributor	    |Quantity |Part #	|Manufacturer |Price 	| Total price   |
|-------------------------------------------------------------|---------------|---------|-----------|---------------|----------------|-------------|
|ShareGoo 8Leds LED Light Headlights/Taillight                             |	Amazon.com	| 1	| ‎AS136   | ‎Treehobby | $8.89	  | $8.89         |
|Dip switch  (3 position)                     |	Mouser.com 	| 1	     |2454982-2 | TE Connectivity / Alcoswitch| $0.96	  | $0.96         |
|20 ft each 18 AWG copper wire with shielded protction(6 different color)                | Amazon.com	| 1	  |B085QD9DWP  | TUOFENG  | $16.49	| $16.49        |
|Resistors (250 ohms)                                |Digikey	| 8	 | 	CMF60250R00BHEB | 	Vishay Dale    | $0.94 | $7.52       |
|3 Position Wire to Board Terminal Block 		     |      Digikey   |  4 |	282834-3   |  TE Connectivity AMP Connectors | $2.54 | $10.16 |
|8 Position Wire to Board Terminal Block		     |Digikey         |  1 |  	282834-8 |     TE Connectivity AMP Connectors     | $8.65 |	 $8.65 |
|		                                                          |         |   |   |         | Total:  |	$52.67     |

## References 

[1] A000067-datasheet.pdf, https://docs.arduino.cc/resources/datasheets/A000067-datasheet.pdf (accessed Apr. 10, 2024).   

[2] T. Cooper, “All about leds,” Adafruit Learning System, https://learn.adafruit.com/all-about-leds/forward-voltage-and-kvl (accessed Apr. 10, 2024). 

[3] “What are the forward voltages of different leds?,” CircuitBread, https://www.circuitbread.com/ee-faq/the-forward-voltages-of-different-leds (accessed Apr. 9, 2024). 

 
