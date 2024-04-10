# Vehicle Lights signoff
## Function of subsystem 
The function of this subsystem is to allow users to interact with the car Headlights while also learning the concepts of electrical components and code. This subsystem will take different inputs at the same time from the input breadboard and Coding subsystems. It will use a microcontroller to take 4 inputs from those subsystems and send them to a multiplexer. The multiplexer will have an enable and two select lines that control what input is sent on through to the LEDs. The user will use inputs such as switches within the input breadboard subsystem to control the enable and select lines. 

## Constraints
### Derived from Shall statements

C1: The Kit shall operate at safe and compatible voltage levels for educational purposes.
- The kit needs to operate at safe voltages but also make sure that the voltages are compatible with the Arduino and other components used in this subsystem since ratings and compatability can be different. 


     

C2: The kit shall ensure proper safety features for any connections that are made making sure they are connected properly and there are limitations for current so there is no overcurrent for safety reasons.
- All Arduino and soldered components need to be safely and properly connected. The soldered components must be soldered correctly and firmly. Any wires used to connect the Arduino to the multiplexer and LEDs that are soldered also need to be properly connected for safety protection. Any LEDs or other current-limited components will need to have current-limiting resistors to prevent over-current. 


C3 & C9. The kit shall contain clear instructions, labeled components, user-friendly interface, and comprehensive materials such as a kit manual.
- The kit needs to have step-by-step instructions and labeled components when users are interacting with the headlights that way they know what values of the components they are playing with. This will allow them to understand and learn the concepts much easier. They also need to know what they are selecting when they use the mux select lines. 



### Derived from Socioeconomic Constraint 
-  Where the components used in this subsystem are bought from and the cost of them will be chosen wisely when ordering so that the cost of this kit does not become unaffordable. 
    - It is important that the cost of this kit is reduced as much as possible, because if the cost begins to get too expensive then the range of the audience that you gain becomes much smaller.
      
## Buildable Schematic
![image](https://github.com/abdoulm366/TTU-Capstone--Electrical-Class-Kit/assets/157627496/81937c99-f397-4b4f-adb2-835c6079c4a8)
Figure 1. Car lights output schematic. 

This buildable schematic is the car lights output in its entirety. First the big block is a Arduino at mega 2560. The 2560 will take in the inputs from the input breadboard subsystem and the code subsystem and read those values, then it will use code to send those values out of a port into the multiplexers. The at mega will also work the switches that drive the multiplexer’s select lines. The switches will be hooked into a port on the at mega 2560 and that port will be coded so the Arduino can take in the switches inputs. Then the Arduino will be coded to read in the state of the select line switches wherever they are connected. This will allow the mux to select which of its inputs goes through based off the truth table in table 1 down below in the analysis section. 

The second smaller block will be a 74153 series IC chip. It is a dual 4-1 multiplexer which will be used to distribute four inputs for the left head/rear/turn lights to the first 4-1 and the other four inputs will be for the right head/rear/turn lights that will go to the second 4-1. The multiplexer will take its four inputs from the Arduino mega 2560 and then the user will use the switches to select a certain sequence to allow only one of the four inputs to go through the multiplexer. Based on which input the user has selected the multiplexer to send through, the multiplexer will then send the output of that to the LEDs. The multiplexer will be set up so that the first two inputs are supposed to turn all four of the LEDS on. This would be the inputs taken from either the input breadboard subsystem resistance showing differences in brighter(high-beam) and dimmer (low-beam) LEDs or code inputs that change the dimness and brightness. This would allow users to see the difference between resistance values and the concepts of series and parallel and also interact with code to see how code can change LED brightness just like resistance can. The last two inputs of the multiplexer should be the left and right turn signal inputs which would be similar to the resistance concept, except it would be capacitance and code this time instead of resistance, and capacitance would show the difference in the speed of blinking LEDs. 

The 74153 multiplexer and the LEDs will both be soldered and then wired appropriately to each other as they should be. It is important that when soldering these and wiring them up the team makes sure to do it safely and to make sure all components are connected correctly and securely to make sure it is safe. 

## Analysis 
C1 & C2: Analyzing safe and compatible voltage levels and Safety features such as firm connections and limiting current flow:

Current limitations calculations 

Red 5mm LEDs forward voltage is between 1.8 V and 2.1 V and 20mA max. so 2.0 V and 15mA would be a safe range [4].
Resistance needed to get 15mA for a red LED. 

$R  = \frac{5 - 2.0}{0.015}$

$200 Ω  = \frac{5 - 2.0}{0.015}$

$R = 200 Ω$

Yellow 5mm LEDs are typically 2.0 volts and 20mA max so a safe range would be 2 volts and 15mA [4].

$R  = \frac{5 - 2.0}{0.015}$

$200 Ω  = \frac{5 - 2.0}{0.015}$

$R = 200 Ω$

resistance of 200 Ω seems to be the value that will keep the current flow to the LEDs safe and compatible. 

The calculations above and the datasheets of the at mega 2560 and the dual 4-1 multiplexer all agree that 5 volts is a safe and compatible voltage level for this subsystem. The atmega operates at and outputs 5 volts [1]. 

The dual 4 to 1 multiplexer can take in 5 volts and output 5 volts [3].

The dual multiplexer then will send that 5 volts to the resistances calculated to break down the voltage and limit to much current flow to the LEDs so that the 5 volts is safe and compatible to use.
To further analyze this constraint 2 past the current limits, the select line switches, LEDs and multiplexer will all be soldered firm to an Adafruit perma-proto board so that the connections are firm and not just plugged into where they could fall out or be wiggled out causing short circuits. Any wires that will be running from the at mega 2560 to the perma-proto boards will all be securely zip-tied together or tied together with a clamp in the same path so that the wires aren’t just freely out, in the way, or being pulled on. The end of the wires that will be connected to the LEDs and multiplexer will also be soldered to the correct pins and terminals firmly so that they cannot be ripped or wiggled out. This all will be organized and easy to get to incase of trouble. It will also help eliminate problems in the future. The perma-proto board is a breadboard but instead of solderless it is one you must solder your components to [2].



C3 & C9:
This subsystem will have a set of step-by-step clear instructions so that the user can have an idea of what’s going on instead of just throwing the demonstration straight at them with absolutely no background or experience. The team will need to create a manual for the kit that has small, printed copy pictures of all the components and their values that are inside this kit that are usable by the user so that when they are plugging and playing or interacting with something they are not just clueless. 

This subsystems part of the manual will have a background explanation of the purpose of this demonstration and outcomes at the beginning of the page that it is on. The reason for this is so that users can read the background explanation and outcomes they should gain from this and have an idea of what is going to be studied in this demonstration. 

The components that will be used in this subsystem such as switches will be labeled as Switches so that the user knows that they are using switches and not think they are just a push button. The multiplexer will also be a labeled component since the user will be interacting with it and its select lines that way when they use the select line switches they know those switches interacted with the multiplexer. They will be able to gain knowledge on why they pressed them and how it works by following the step-by-step instructions, reading the background explanation, reading outcomes, and also visualizing what happens based on their input from the LED outputs. So, this subsystem's part of the manual will be very organized and informative so that the users are not just clueless of what is happening. 

The users will also have Hints about what they should be seeing within some of the instructions so that can help them see if they are getting the correct results and if they are not then they know they messed up helping them learn from their mistakes and how to fix them as well. This gives the user a full learning experience instead of just the correct answer every time and not actually learning the concept. 





Table 1. Truth table for first 4 to 1 multiplexer for the Multiplexer chip.
| S1 | S0 | 1CO | 1C1 | 1C2 |1C3 |   
|----|----|-----|-----|----|-----|
| 0  | 0  | 1   | 0   | 0  | 0   |
| 0  | 1  | 0   | 1   | 0  | 0   |
| 1  | 0  | 0   | 0   | 1  | 0   |
| 1  | 1  | 0   | 0   | 0  | 1   |

Table 2. truth table for second 4 to 1 Multiplexer for the Multiplexer chip.
| S1 | S0 | 2CO | 2C1 | 2C2 |2C3 |   
|----|----|-----|-----|----|-----|
| 0  | 0  | 1   | 0   | 0  | 0   |
| 0  | 1  | 0   | 1   | 0  | 0   |
| 1  | 0  | 0   | 0   | 1  | 0   |
| 1  | 1  | 0   | 0   | 0  | 1   |

The truth tables above are for Figure 2. inputs when the multiplexer is enabled (switch3 = 0). If the multiplexer becomes (switch3 =1) then the entire output will be zero, no matter what at all. Figure 2. is just below. select zero and one will work both multiplexers on the chip and both multiplexers work the same as seen in the truth table. 
 

![image](https://github.com/abdoulm366/TTU-Capstone--Electrical-Class-Kit/assets/157627496/277d1751-a9cb-4d97-86da-0119f2b9648e)
Figure 2. Multiplexer functionality truth table test. 

Figure 2. is the Multiplexer truth table analysis. Just to add to good instructions and background information something along the line of this will be added to the manual like the truth table with a picture of the setup. The truth table will be explained how it works and the picture would be added just to show the general setup and give an explanation of just the multiplexer alone, its function to give the users an idea, and to show how the multiplexer works by itself, so they get a better understanding. The picture also shows the labels of the chip so they can look at it and the truth table to see which chip pin will be activated based on their select line choice.  

This subsystem requires the multiplexer to follow a datasheet truth table, and this is the diagram built to test and confirm the functionality of the multiplexer to convince that it will be safe and compatible to work for this output demonstration, only allowing the user to send 1 selected input through to the output. The datasheet for it has a active low and active high inhibit pin so I recreated the truth table from the datasheet with just binary zeros and ones for an easier understanding since the user will only use active low inputs. You can find this inhibit pin and truth table information in the datatsheet [3]. 

The third switch that is hooked to the at mega will be used on the demonstration as a disable/enable. If the switch is not pressed the multiplexer will remain active. If the switch is pressed and goes into a high state (a one), then the entire multiplexer will be disabled setting everything to zero no matter what the user selects since inputs will always be active low. This will represent an enable switch which will be labeled and explained in the instructions section so that the user knows exactly how it works and what it will do. If they do not know its functionality and press it, then nothing will work leaving them frustrated and confused. This will be a switch that is labeled and explained already so they know that it shuts the multiplexer off. 

This figure and explanation is a good example of something that could be used inside a manual for background information or to give the user a visualization of what they are using select lines for. In the actual informational manual, everything would be labeled in the picture close to this and then the subsystems that send inputs to it would have to help take care of explaining and labeling the inputs that are not labeled here. 

         
socioeconomic constraint: when the team goes to order for this subsystem they will consider the best options they have to get these components and if the team has to order them then they will find the best websites and cheapest places to buy packs of components or multiple components that can't be bought in packs, to ensure that they get the best prices and deals for each piece keeping the cost down. The B.O.M will show the best websites found and the prices for each individual component needed that came from that website to show that the subsystem cost is reasonable and keeps the project's budget in range. 


BOM 
|Item                                                         |	Location	    |Quantity |	Price 	| Total price   |
|-------------------------------------------------------------|---------------|---------|---------|---------------|
|Diffused Red 5mm LED (25 pack)                               |	Adafruit.com	| 1	      | $4.00	  | $4.00         |
|Diffused yellow 5mm LED 	                                    | Sparkfun.com	| 10	    | $4.50	  | $4.50         |
|Arduino Mega 2560	                                          | Amazon.com	  | 1	      | $48.90	| $48.90        |
|SN74LS153N Dual 4-Line To 1-Line Data Selectors/Multiplexers |	Ti.com	      | 3	      | $2.50	  | $2.50         |
|Tactile Button switch (6mm) x 20 pack                        |	Adafruit.com 	| 1	      | $2.50	  | $2.50         |
|Full-size Perma proto boards	                                | Adafruit.com	| 2	      | $39.90	| $39.90        |
|		                                                          |               |         | Total:  |	$102.30       |

## References 

[1] ATMEGA640/1280/1281/2560/2561 datasheet, https://ww1.microchip.com/downloads/en/devicedoc/atmel-2549-8-bit-avr-microcontroller-atmega640-1280-1281-2560-2561_datasheet.pdf (accessed Apr. 10, 2024). 

[2] Lady Ada, “Breadboards for Beginners,” Adafruit Learning System, https://learn.adafruit.com/breadboards-for-beginners/perma-protos (accessed Apr. 9, 2024). 

[3] Ti, https://www.ti.com/lit/ds/symlink/sn74ls153.pdf (accessed Apr. 10, 2024). 

[4] “What are the forward voltages of different leds?,” CircuitBread, https://www.circuitbread.com/ee-faq/the-forward-voltages-of-different-leds (accessed Apr. 9, 2024). 


