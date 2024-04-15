# Vehicle Lights signoff
## Function of subsystem 
The function of this subsystem is to allow users to interact with the car Headlights while also learning the concepts of electrical components and code. This subsystem will take different inputs at the same time from the input breadboard and Coding subsystems. It will use a microcontroller to take 4 inputs from those subsystems and send them to a multiplexer. The multiplexer will have an enable and two select lines that control what input is sent on through to the LEDs. The user will use inputs such as switches within the input breadboard subsystem to control the enable and select lines. 

## Constraints
|description| Constraint | source |
|-|-|-|
| variable type |The Arduino mega 2560 in this subsystem shall convert a string of numbers that range from 0 - 1,000,000 into floats to store decimal values for better precision.| [2] C++ data types, https://www.w3schools.com/cpp/cpp_data_types.asp (accessed Apr. 14, 2024).  |
|Multiplexer voltage safety |The Multiplexer shall take 5 volts with a 10% tolerance, no more or less than that for this subsystem to prevent any damage to the multiplexer and ensure safe and sufficient operation.| datasheet requirement |
|current safety |The LEDs in this subsystem shall take 15mA with a 5% tolerance, no more than that to prevent overcurrent damage and to ensure safe operation.| datasheet requirement  |
| Socioeconomic | Any components and equipment within this subsystem should not exceed $55 dollars and the subsystems total cost should not exceed $175 to help keep the project budget in the 400-900 range| conceptual design| 






      
## Buildable Schematic
![Screenshot (299)](https://github.com/abdoulm366/TTU-Capstone--Electrical-Class-Kit/assets/157627496/351241f0-9788-490b-9e3b-a66a7b40a01c)

Figure 1. Car lights output schematic. 

This buildable schematic is the car lights output in its entirety. First the big block is a Arduino at mega 2560. The 2560 will take in the inputs from the input breadboard subsystem and the code subsystem and read those values, then it will use code to send those values out of a port into the multiplexers. The at mega will also work the switches that drive the multiplexer’s select lines. The switches will be hooked into a port on the at mega 2560 and that port will be coded so the Arduino can take in the switches inputs. Then the Arduino will be coded to read in the state of the select line switches wherever they are connected. This will allow the mux to select which of its inputs goes through based off the truth table in table 1 down below in the analysis section. 

The second smaller block will be a 74153 series IC chip. It is a dual 4-1 multiplexer which will be used to distribute four inputs for the left head/rear/turn lights to the first 4-1 and the other four inputs will be for the right head/rear/turn lights that will go to the second 4-1. The multiplexer will take its four inputs from the Arduino mega 2560 and then the user will use the switches to select a certain sequence to allow only one of the four inputs to go through the multiplexer. Based on which input the user has selected the multiplexer to send through, the multiplexer will then send the output of that to the LEDs. The multiplexer will be set up so that the first two inputs are supposed to turn all four of the LEDS on. This would be the inputs taken from either the input breadboard subsystem resistance showing differences in brighter(high-beam) and dimmer (low-beam) LEDs or code inputs that change the dimness and brightness. This would allow users to see the difference between resistance values and the concepts of series and parallel and also interact with code to see how code can change LED brightness just like resistance can. The last two inputs of the multiplexer should be the left and right turn signal inputs which would be similar to the resistance concept, except it would be capacitance and code this time instead of resistance, and capacitance would show the difference in the speed of blinking LEDs. 



The 74153 multiplexer and the LEDs will both be soldered and then wired appropriately to each other as they should be. It is important that when soldering these and wiring them up the team makes sure to do it safely and to make sure all components are connected correctly and securely to make sure it is safe. 

## Analysis 

Analyzing the Variable type constraint: 
The Arduino shall take in a string value input and then convert that into a floating-point value.  This will be met by using C++ language to code the Arduino functions atof() or toFloat() to convert from string into a float value. This will allow the Arduino then to convert the value and output it as a floating-point value so that the number is a lot more precise using decimal places instead of rounding off to the near whole value. 

Analyzing the multiplexer voltage Saftey: This constraint will be met by following datasheet requirements and limiting the input voltage to the Multiplexer to 5 volts. This will be met since the Arduino mega 2560 is only capable of outputting 5 volts maximum from its 5 volt port according to its datasheet information [1]. since the Arduino mega can only output 5 volts maximum the the constraint has been met and there is no need to consider any extra precautions for the multiplexer's voltage safety. 

Analyzing the current safety constraint:
The current that flows Through the LEDs shall not exceed 15mA with a 5% tolerance, and to meet this requirement the subsystem will use current limiting resistors to make sure that no more than 15mA with a 5 % tolerance will flow through to the LEDs. The Multiplexer Datasheet also states that the Multiplexer can only output 16mA according to its datasheet[4], so not a huge jump. There still needs to be current limiting resistors calculated and implemented for extra safety measures and to ensure that the LEDs can still operate smoothly. 

below are the Current limitations calculations that will make sure that the constraint of 15mA with 5% tolerance is met. 

Red 5mm LEDs forward voltage is between 1.8 V and 2.1 V and 20mA max. so 2.0 V and 15mA would be a safe range [3][5].
Resistance to get 15mA for a red LED.

$R  = \frac{5 - 2.0}{0.015}$

$200 Ω  = \frac{5 - 2.0}{0.015}$

$R = 200 Ω$

Yellow 5mm LEDs are typically 2.0 volts and 20mA max so a safe range would be 2 volts and 15mA [3][5].

$R  = \frac{5 - 2.0}{0.015}$

$200 Ω  = \frac{5 - 2.0}{0.015}$

$R = 200 Ω$

resistance of 200 Ω seems to be the value that will keep the current flow to the LEDs safe preventing damage. 


A little functionality analysis on the buildable schematic explanation of the Multiplexer :

The truth tables below are for Figure 2. inputs when the multiplexer is enabled (switch3 = 0). If the multiplexer becomes (switch3 =1) then the entire output will be zero, no matter what as seen in the truth tables. select zero and one will work both multiplexers on the chip and both multiplexers work the same as seen in the truth table. The select lines of the multiplexer will be controlled by tactile push button switches. 

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
  



BOM 
|Item                                                         |	Location	    |Quantity |	Price 	| Total price   |
|-------------------------------------------------------------|---------------|---------|---------|---------------|
|Diffused Red 5mm LED (25 pack)                               |	Adafruit.com	| 1	      | $4.00	  | $4.00         |
|Diffused yellow 5mm LED 	                                    | Sparkfun.com	| 2	    | $0.90	  | $0.90         |
|Arduino Mega 2560	                                          | Amazon.com	  | 1	      | $48.90	| $48.90        |
|SN74LS153N Dual 4-Line To 1-Line Data Selectors/Multiplexers |	Ti.com	      | 3	      | $2.50	  | $2.50         |
|Tactile Button switch (6mm) x 20 pack                        |	Adafruit.com 	| 1	      | $2.50	  | $2.50         |
|Full-size Perma proto boards	                                | Adafruit.com	| 2	      | $39.90	| $39.90        |
|20 ft each 18 AWG copper wire with shielded protction(6 different color)                | Amazon.com	| 1	      | $16.49	| $16.49        |
|Resistors (pack of 25 200 ohms)	                                | Adafruit.com	| 2	      | $5.78 | $5.78        |
|		                                                          |               |         | Total:  |	$120.97       |

## References 

[1] A000067-datasheet.pdf, https://docs.arduino.cc/resources/datasheets/A000067-datasheet.pdf (accessed Apr. 10, 2024).   

[2] C++ data types, https://www.w3schools.com/cpp/cpp_data_types.asp (accessed Apr. 14, 2024).

[3] T. Cooper, “All about leds,” Adafruit Learning System, https://learn.adafruit.com/all-about-leds/forward-voltage-and-kvl (accessed Apr. 10, 2024). 

[4] Ti, https://www.ti.com/lit/ds/symlink/sn74ls153.pdf (accessed Apr. 10, 2024). 

[5] “What are the forward voltages of different leds?,” CircuitBread, https://www.circuitbread.com/ee-faq/the-forward-voltages-of-different-leds (accessed Apr. 9, 2024). 

 
