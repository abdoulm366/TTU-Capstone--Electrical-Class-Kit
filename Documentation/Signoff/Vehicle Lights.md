# Vehicle Lights signoff
## Function of subsystem 
The function of this subsystem is to allow users to interact with the car Headlights while also learning the concepts of electrical components and code. This subsystem will take different inputs at the same time from the input breadboard and Coding subsystems. It will use a microcontroller to take 4 inputs from those subsystems and send them to a multiplexer. The multiplexer will have an enable and two select lines that control what input is sent on through to the LEDs. The user will use inputs such as switches within the input breadboard subsystem to control the enable and select lines. 

## Constraints
### Derived from Shall statements

C1: The Kit shall operate at safe voltage levels such as no more than 50 volts in an educational setting to limit the risk of electrical shock and any other hazards. Voltages over 50 volts are not recommended because they can lead to severe injuries or even in some cases death,  if the kit goes above 50 volts then that could start to lead to dangerous voltage levels causing risk of exceeding the safe voltage range and causing component damage or more importantly causing harm [2].

-  This subsystem will consider this constraint since it will be dealing with voltages that are supplied to the subsystem's components. 
     

C2: The kit shall ensure proper safety features which will include solderable 18 AWG copper wire inside shielded protection making sure the wire is safe from connection to connection. The kit will also need to have current limiting resistors to make sure there are limitations for current so no current over 20mA will flow through this subsystem causing component damage or even vision damage from being to bright.

- This constraint is needed in this subsystem since the subsystem will use LEDs which typically take 20mA max [5].

The kit shall ensure compatibility so that all the components within the kit work together. This should include safe but compatible voltage and current ranges for all components. All of the components within this kit shall operate at the same voltage supplied no more than 50 volts max and current flowing from that voltage no more than 20mA. It shall also allow the components to properly work with control interfaces such as switches or push buttons. 

- This constraint is needed in this subsystem since it will be using an Arduino, a multiplexer, and LEDs together. It will also need to be compatible with the input breadboard subsystem components and code subsystem as it will take inputs from them. 



### Derived from Socioeconomic Constraint 
-  Where the components used in this subsystem are bought from and the cost of them will be chosen wisely when ordering so that the cost of this kit does not become unaffordable. 
    - It is important that the cost of this kit is reduced as much as possible, because if the cost begins to get too expensive then the range of the audience that you gain becomes much smaller.
      
## Buildable Schematic
![Screenshot (292)](https://github.com/abdoulm366/TTU-Capstone--Electrical-Class-Kit/assets/157627496/4463bf4c-523b-470c-8d2a-c2df3b45e132)

Figure 1. Car lights output schematic. 

This buildable schematic is the car lights output in its entirety. First the big block is a Arduino at mega 2560. The 2560 will take in the inputs from the input breadboard subsystem and the code subsystem and read those values, then it will use code to send those values out of a port into the multiplexers. The at mega will also work the switches that drive the multiplexer’s select lines. The switches will be hooked into a port on the at mega 2560 and that port will be coded so the Arduino can take in the switches inputs. Then the Arduino will be coded to read in the state of the select line switches wherever they are connected. This will allow the mux to select which of its inputs goes through based off the truth table in table 1 down below in the analysis section. 

The second smaller block will be a 74153 series IC chip. It is a dual 4-1 multiplexer which will be used to distribute four inputs for the left head/rear/turn lights to the first 4-1 and the other four inputs will be for the right head/rear/turn lights that will go to the second 4-1. The multiplexer will take its four inputs from the Arduino mega 2560 and then the user will use the switches to select a certain sequence to allow only one of the four inputs to go through the multiplexer. Based on which input the user has selected the multiplexer to send through, the multiplexer will then send the output of that to the LEDs. The multiplexer will be set up so that the first two inputs are supposed to turn all four of the LEDS on. This would be the inputs taken from either the input breadboard subsystem resistance showing differences in brighter(high-beam) and dimmer (low-beam) LEDs or code inputs that change the dimness and brightness. This would allow users to see the difference between resistance values and the concepts of series and parallel and also interact with code to see how code can change LED brightness just like resistance can. The last two inputs of the multiplexer should be the left and right turn signal inputs which would be similar to the resistance concept, except it would be capacitance and code this time instead of resistance, and capacitance would show the difference in the speed of blinking LEDs. 

The 74153 multiplexer and the LEDs will both be soldered and then wired appropriately to each other as they should be. It is important that when soldering these and wiring them up the team makes sure to do it safely and to make sure all components are connected correctly and securely to make sure it is safe. 

## Analysis 
C1 & C2: Analyzing safe voltage levels and Safety features such as firm connections, protected wires and limiting current flow:

Current limitations calculations 

Red 5mm LEDs forward voltage is between 1.8 V and 2.1 V and 20mA max. so 2.0 V and 15mA would be a safe range [7].
Resistance needed to get 15mA for a red LED. 

$R  = \frac{5 - 2.0}{0.015}$

$200 Ω  = \frac{5 - 2.0}{0.015}$

$R = 200 Ω$

Yellow 5mm LEDs are typically 2.0 volts and 20mA max so a safe range would be 2 volts and 15mA [7].

$R  = \frac{5 - 2.0}{0.015}$

$200 Ω  = \frac{5 - 2.0}{0.015}$

$R = 200 Ω$

resistance of 200 Ω seems to be the value that will keep the current flow to the LEDs safe and compatible. 

The calculations above and the datasheets of the at mega 2560 and the dual 4-1 multiplexer all agree that 5 volts supplied will be enough voltage to drive this output subsystem which meets the requiremnet of being below 50 volts max. 

The atmega operates at and outputs 5 volts accoring to the datasheet  [1]. 

The dual 4 to 1 multiplexer can take in 5 volts and output 5 volts according to it's datasheet [6].

The dual multiplexer then will send that 5 volts to the resistances calculated to break down the voltage and limit to much current flow to the LEDs so that the 5 volts is safe and compatible to use.
To further analyze this constraint 2 past the current limits, the select line switches, LEDs and multiplexer will all be soldered firm to an Adafruit perma-proto board so that the connections are firm and not just plugged into where they could fall out or be wiggled out causing short circuits. Any wires that will be running from the at mega 2560 to the perma-proto boards will all be securely zip-tied together or tied together with a clamp in the same path so that the wires aren’t just freely out, in the way, or being pulled on. The end of the wires that will be connected to the LEDs and multiplexer will also be soldered to the correct pins and terminals firmly so that they cannot be ripped or wiggled out. This all will be organized and easy to get to incase of trouble. It will also help eliminate problems in the future. The perma-proto board is a breadboard but instead of solderless it is one you must solder your components to [3].


Analyzing the compatibility of the components. 
As stated in the voltage analysis the Atmega and dual 4 to 1 mux both are operatable at 5 volts which is well in the safe range. It also means that both of these components are voltage compatible with each other. The LEDs will use the calculated resistances above in the current limitation analysis to allow 5 volts to be used by limiting the current to 15 mA to meet compatibility requirements and to stay below the 50 volts and 20 mA maximum safety limits. 

For the control interface the switches can also operate anywhere from 5-24 VDC and 1-50 mA's according to their data sheet [4].

That allows the tactile push button switches to be compatible with the kit since it is a safe voltage range and can operate at the same ratings as the other components that it will interact with such as the Arduino and multiplexer.


The truth tables below are for Figure 2. inputs when the multiplexer is enabled (switch3 = 0). If the multiplexer becomes (switch3 =1) then the entire output will be zero, no matter what as seen in the truth tables. select zero and one will work both multiplexers on the chip and both multiplexers work the same as seen in the truth table. The select lines of the multiplexer will be controlled by the tactile push button switches. 

Table 1. Truth table for first 4 to 1 multiplexer for the Multiplexer chip.
|enable | S1  | S0  | 1CO | 1C1 | 1C2 |1C3 |   
|-------|-----|-----|-----|-----|-----|----|
| 0     | 0   | 0   | 1   | 0   | 0   | 0  |
| 0     | 0   | 1   | 0   | 1   | 0   | 0  |
| 0     | 1   | 0   | 0   | 0   | 1   | 0  |
| 0     | 1   | 1   | 0   | 0   | 0   | 1  |
| 1     | 0   | 0   | 0   | 0   | 0   | 0  |
| 1     | 0   | 1   | 0   | 0   | 0   | 0  |
| 1     | 1   | 0   | 0   | 0   | 0   | 0  |
| 1     | 1   | 1   | 0   | 0   | 0   | 0  |



Table 2. truth table for second 4 to 1 Multiplexer for the Multiplexer chip.
|enable | S1  | S0  | 1CO | 1C1 | 1C2 |1C3 |   
|-------|-----|-----|-----|-----|-----|----|
| 0     | 0   | 0   | 1   | 0   | 0   | 0  |
| 0     | 0   | 1   | 0   | 1   | 0   | 0  |
| 0     | 1   | 0   | 0   | 0   | 1   | 0  |
| 0     | 1   | 1   | 0   | 0   | 0   | 1  |
| 1     | 0   | 0   | 0   | 0   | 0   | 0  |
| 1     | 0   | 1   | 0   | 0   | 0   | 0  |
| 1     | 1   | 0   | 0   | 0   | 0   | 0  |
| 1     | 1   | 1   | 0   | 0   | 0   | 0  |

 

![image](https://github.com/abdoulm366/TTU-Capstone--Electrical-Class-Kit/assets/157627496/277d1751-a9cb-4d97-86da-0119f2b9648e)
Figure 2. Multiplexer functionality truth table test. 
  

This subsystem requires the multiplexer to follow a datasheet truth table, and this is the diagram built to test and confirm the functionality of the multiplexer to convince that it will be compatible to work for this output demonstration, only allowing the user to send 1 selected input through to the output. The datasheet for it has a active low and active high inhibit pin so I recreated the truth table from the datasheet with just binary zeros and ones for an easier understanding since the user will only use active low inputs. You can find this inhibit pin and further truth table information in the datatsheet [6]. 

The third switch that is hooked to the at mega will be used on the demonstration as a disable/enable which is represented in the truth table that it is compatible and functional. If the switch is not pressed the multiplexer will remain active. If the switch is pressed and goes into a high state (a one), then the entire multiplexer will be disabled setting everything to zero no matter what the user selects since inputs will always be active low as seen in the truth tables.  

         
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
|20 ft each 18 AWG copper wire with shielded protction(6 different color)                | Amazon.com	| 1	      | $16.49	| $16.49        |
|Resistors (pack of 25)	                                | Adafruit.com	| 2	      | $5.78 | $5.78        |
|		                                                          |               |         | Total:  |	$124.57       |

## References 

[1] A000067-datasheet.pdf, https://docs.arduino.cc/resources/datasheets/A000067-datasheet.pdf (accessed Apr. 10, 2024).  

[2] Engr. M. A. Raza, “What is the safe limit of DC-voltage for humans to touch? - electrical engineering,” X, https://electricalengineeringx.com/what-is-the-safe-limit-of-dc-voltage-for-humans-to-touch/#What_is_the_Safe_Limit_of_DC-Voltage_for_humans_to_touch (accessed Apr. 10, 2024). 

[3] Lady Ada, “Breadboards for Beginners,” Adafruit Learning System, https://learn.adafruit.com/breadboards-for-beginners/perma-protos (accessed Apr. 9, 2024).

[4] Tactile switch - B3F, https://cdn-shop.adafruit.com/datasheets/B3F-1000-Omron.pdf (accessed Apr. 11, 2024).

[5] T. Cooper, “All about leds,” Adafruit Learning System, https://learn.adafruit.com/all-about-leds/forward-voltage-and-kvl (accessed Apr. 10, 2024). 

[6] Ti, https://www.ti.com/lit/ds/symlink/sn74ls153.pdf (accessed Apr. 10, 2024). 

[7] “What are the forward voltages of different leds?,” CircuitBread, https://www.circuitbread.com/ee-faq/the-forward-voltages-of-different-leds (accessed Apr. 9, 2024). 

 
