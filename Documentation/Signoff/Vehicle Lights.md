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
![image](https://github.com/user-attachments/assets/06f8ab6e-4cad-4b62-a8f8-ee3809c5b50d)

Figure 1. Car Lights Output Schematic. 


![image](https://github.com/user-attachments/assets/ccd981f5-6700-47b6-8ae1-a11b937ae01e)



Figure 2. PCB of the LEDs with current limiting resistors in series and mounting holes and screw terminals to connect inputs and any grounds.



![image](https://github.com/user-attachments/assets/0e934ec0-bf42-4e22-abeb-0efa6ba2484d)


Figure 3. 3D model of LEDs.


## Analysis 


### LEDs
![image](https://github.com/user-attachments/assets/b5114886-1eb9-420b-ac61-0f3790194200)



Figure 4. Car LEDs represent the ShareGoo LED Light Headlights/Taillights

The LEDs that will be used in this subsystem will be ShareGoo LED lights, headlights/taillights, white and red. These LEDs were chosen because they are cost-efficient and they do not consume much space. These LEDs will be sufficient to physically represent the headlights using white LEDs and tail lights using red LEDs to accurately represent the car lights. As you can see in Figure 4. each of the 4 LEDs will need its own small PCB with mounting holes so that they can be mounted at each corner of the car, to have a real representation of lights on a car. These LEDs will be small LEDs with a housing around them to help direct them into a beam like real car headlights. These LEDs are capable of operating on a voltage range of 3 volts to 7 volts allowing them to change brightness. These LEDs will be configured to an Arduino Atmega that is within the input system, the headlights will be connected to PWM pins D2, D3, D4, and D5 and will be coded so that they will operate as expected and also be able to interact with the HMI within the LCD block subsystem. Each LED-resistor network will have terminal blocks on the PCB as well so that the wire connected straight from the Arduino pins can be connected to the PCB and traced to the resistor/positive terminal of the LED and the ground wire can be connected and traced to the negative terminal of the LED. 

This will also be coded using pulse width modulation to change the duty cycle so that it can output various voltages changing the brightness of the headlights. Pulse width modulation can be utilized to control both the intensity of the LED's light and the speed of the blinking. Pulse width modulation, or PWM, is a square pulse that alternates between 0 volts and a nominal voltage. If the pulse's frequency is fast enough, the changes made to it will not be perceptible to the naked eye. These changes are as follows: changing the duty cycle, or the time for which the pulse is at the nominal voltage, will effectively lower the voltage seen to the naked eye at the LED. This will make the LED appear dimmer. The frequency can also be changed. If the frequency is lowered to a point at which the human eye can detect it, then it can be lowered or increased in order to change the rate at which the LED's "blink" when the blinker function is selected.

This simulation represents the pulse width modulation concept which controls the LEDs. This also proves that the overcurrent protection works as intended. 

![image](https://github.com/user-attachments/assets/86fb9523-2334-4013-a515-9cbc753ebdab)

Figure 5. PWM and overcurrent protection simulation. 





# BOM 
Table 2. BOM
|Item                                                         |	Distributor	    |Quantity |Part #	|Manufacturer |Price 	| Total price   |
|-------------------------------------------------------------|---------------|---------|-----------|---------------|----------------|-------------|
|ShareGoo 8Leds LED Light Headlights/Taillight                             |	Amazon.com	| 1	| ‎AS136   | ‎Treehobby | $8.89	  | $8.89         |
|20 ft each 18 AWG copper wire with shielded protction(6 different color)                | Amazon.com	| 1	  |B085QD9DWP  | TUOFENG  | $16.49	| $16.49        |
|Resistors (250 ohms)                                |Digikey	| 8	 | 	CMF60250R00BHEB | 	Vishay Dale    | $0.94 | $7.52       |
|2 Position Wire to Board Terminal Block 		     |      Digikey   |  4 |	282834-3   |  TE Connectivity AMP Connectors | $1.70 | $6.80 |
|		                                                          |         |   |   |         | Total:  |	$39.70    |

## References 

[1] A000067-datasheet.pdf, https://docs.arduino.cc/resources/datasheets/A000067-datasheet.pdf (accessed Apr. 10, 2024).   

[2] T. Cooper, “All about leds,” Adafruit Learning System, https://learn.adafruit.com/all-about-leds/forward-voltage-and-kvl (accessed Apr. 10, 2024). 

[3] “What are the forward voltages of different leds?,” CircuitBread, https://www.circuitbread.com/ee-faq/the-forward-voltages-of-different-leds (accessed Apr. 9, 2024). 

 
