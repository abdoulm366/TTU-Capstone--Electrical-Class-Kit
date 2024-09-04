# Vehicle Lights signoff
## Function of subsystem 
The function of this subsystem is to demonstrate Electrical and Computer Engineering concepts through physical means using the car's lighting system. This will allow users to interact with the car's lights and see the physical changes of the lights based on the user's input.  

## Constraints
Table. 1 Constraints
|Description| Constraint | Source |
|-|-|-|
|Current Saftey / Standards |The LEDs in this subsystem shall take no less than 3V and no more than 7V to prevent damage and to ensure safe and correct operation.| Datasheet Requirement  |
|Cost Considerations | Any components and equipment within this subsystem should not exceed $40 dollars and the subsystems total cost should not exceed $120 to help keep the project budget in the 400-900 range| Conceptual Design| 





      
## Buildable Schematic
![image](https://github.com/user-attachments/assets/9b348fd7-a210-49a5-b284-93a1722614b5)


Figure 1. Car Lights Output Schematic. 




## Analysis 


### LEDs

The LEDs that will be used in this subsystem will be ShareGoo LED lights, headlights/taillights, white and red. These LEDs were chosen because they are cost-efficient and they do not consume much space. These LEDs will be sufficient to physically represent the headlights using white LEDs and tail lights using red LEDs to accurately represent the car lights. Each Led will be mounted at the corners of the car just like a normal car so they have that real representation of lights on a car. These LEDs will be small 5mm LEDs with a housing around them to help direct them into a beam like real car headlights. These LEDs are capable of operating on a voltage range of 3 volts to 7 volts allowing them to change brightness. These LEDs will be configured to an Arduino Atmega that is within the input system, the headlights will be connected to PWM/DPIO pin D2 and will be coded so that they will operate as expected and also be able to interact with the HMI within the LCD block subsystem. These LEDs have built in resistance to protect overcurrent damage, as long as the voltage supplied to the LEDs stays within the 3 to 7 volts range then the built in resistance will protect any overcurrent damage. According to the datasheet the arduino Atmega can only supply either 3.3 volts or 5 volts which both would be in the range of 3 volts and 7 volts, but for this project the Arduino Atmega will be using the 5 volt rail. Since the Arduino will only be supplying out 5 volts to this subsystem at all times, this means the constraint of keeping the voltage supplied to the LEDs between 3 and 7 volts to protect from overcurrent damage and to make sure of safe and correct operation is met. 

This will be coded using pulse width modulation to change the duty cycle so that it can output various voltages changing the brightness of the headlights since the Digital pins are a constant 5 volts no matter what. Pulse width modulation can be utilized to control both the intensity of the LED's light and the speed of the blinking. Pulse width modulation, or PWM, is a square pulse that alternates between 0 volts and a nominal voltage. If the pulse's frequency is fast enough, the changes made to it will not be perceptible to the naked eye. These changes are as follows: changing the duty cycle, or the time for which the pulse is at the nominal voltage, will effectively lower the voltage seen to the naked eye at the LED. This will make the LED appear dimmer. The frequency can also be changed. If the frequency is lowered to a point at which the human eye can detect it, then it can be lowered or increased in order to change the rate at which the LED's "blink" when the blinker function is selected.


For the cost consideration constraint of no more than $120 of the subsystem was also met since it totaled to be $7.94.  

This simulation in Figure 5. represents the pulse width modulation concept which controls the LEDs. 

![image](https://github.com/user-attachments/assets/86fb9523-2334-4013-a515-9cbc753ebdab)

Figure 2. PWM simulation. 


# BOM 
Table 2. BOM
|Item                                                         |	Distributor	    |Quantity |Part #	|Manufacturer |Price 	| Total price   |
|-------------------------------------------------------------|---------------|---------|-----------|---------------|----------------|-------------|
|ShareGoo 4 LED Light Headlights Taillight Kit                          |	Amazon.com	| 1	| ‎B07FR9BVS5   |‎ ShareGoo | $7.94	  | $7.94        |
|		                                                          |         |   |   |         | Total:  |	$7.94    |

## References 

[1] A000067-datasheet.pdf, https://docs.arduino.cc/resources/datasheets/A000067-datasheet.pdf (accessed Apr. 10, 2024).   

[2] Scully, T. (2019, December 4). How does a 5mm led work?. LEDSupply Blog. https://www.ledsupply.com/blog/how-does-a-5mm-led-work/#:~:text=5mm%20LED%20Current.%20Now

[3] T. Cooper, “All about leds,” Adafruit Learning System, https://learn.adafruit.com/all-about-leds/forward-voltage-and-kvl (accessed Apr. 10, 2024). 

[4] “What are the forward voltages of different leds?,” CircuitBread, https://www.circuitbread.com/ee-faq/the-forward-voltages-of-different-leds (accessed Apr. 9, 2024). 


