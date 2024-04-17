# Vehicle Lights signoff
## Function of subsystem 
The function of this subsystem is to use a microcontroller to output data to a dual 4 to 1 multiplexer. The multiplexer will have an enable and two select lines that control which one of the four inputs is sent through to the LEDs. The select lines of the multiplexer will be switches which will be configured to pins on the Arduino and coded.  The LEDs will then react based on what the input sent tells them to do. 

## Constraints
Table. 1 constraints
|description| Constraint | source |
|-|-|-|
| Resistance variable type range |The Arduino mega 2560 in this subsystem shall convert a char string of resistance numbers that range from 0 - 1,000,000 into floats to store decimal values for better precision.| [2] C++ data types, https://www.w3schools.com/cpp/cpp_data_types.asp (accessed Apr. 14, 2024).  |
| Capacitance Variable type range |The Arduino mega 2560 in this subsystem shall convert a string of Capacitance numbers that range from 1nF to 1mF into floats to store decimal values for better precision.|[2] C++ data types, https://www.w3schools.com/cpp/cpp_data_types.asp (accessed Apr. 14, 2024).  |
|Multiplexer voltage safety |The Multiplexer shall take 5 volts with a 10% tolerance, no more or less than that for this subsystem to prevent any damage to the multiplexer and ensure safe and sufficient operation.| datasheet requirement |
|current safety |The LEDs in this subsystem shall take 15mA with a 5% tolerance, no more than that to prevent overcurrent damage and to ensure safe operation.| datasheet requirement  |
| Socioeconomic | Any components and equipment within this subsystem should not exceed $55 dollars and the subsystems total cost should not exceed $175 to help keep the project budget in the 400-900 range| conceptual design| 






      
## Buildable Schematic
![Screenshot (301)](https://github.com/abdoulm366/TTU-Capstone--Electrical-Class-Kit/assets/157627496/47991235-d246-4766-9161-b56f84a5202c)


Figure 1. Car lights output schematic. 

This buildable schematic is the car lights output in its entirety. First, the big block is an Arduino Atmega 2560 which was chosen to do the string to float conversions and output them to the multiplexer, the Arduino Atmega was chosen because it had a sufficient number of pins and is compatible with C language. This allows the Arduino Atmega to be able to convert strings to floating point values successfully using C language. The second smaller block will be an SN74LV4052A series IC chip. It is a dual 4-1 multiplexer which will be used to distribute four inputs for the left head/rear/turn lights to the first 4-1 and the other four inputs will be for the right head/rear/turn lights that will go to the second 4-1. This multiplexer chip was chosen for compatibility reasons with the Arduino and LEDs which is seen in the analysis of how it can be compatible with the other components within this subsystem. It also is to allow the user to use switches to interact with a multiplexer and its functionality only allowing one input the Arduino sends to go through at a time. As the functionality stated the select lines of the multiplexer will be switches, the switches chosen for this will be tactile push buttons so that when it is pushed the code reads its state and sends that to the select lines. To change the state of a switch back from 1 to 0 it has to be pushed again. The SN74LV4052A multiplexer and the LEDs will both be soldered to a PCB generated. The Arduino will be mounted inside of the cab toward the top middle and the PCB's for the LEDs will be mounted in the front end of the chassis(headlights) and rear end of the chassis (tail lights). 

## Analysis 

Analyzing the resistance Variable type constraint: 
This constraint will be met by using Arduino ide software and C language to code the Arduino function atof() to convert from string into a float value. This will allow the Arduino then to convert the value and output it as a floating-point value so that the number is a lot more precise using decimal places instead of rounding off to the near whole value. These functions will allow us to convert the range 0 - 1M ohms char strings into floats. 

Analyzing the capacitance Variable type constraint: 
The Arduino will also be coded with the same function of C language on the Arduino ide software to convert the capacitance ranges of 1nF to 1mF from char strings into a floating-point value to ensure better accuracy by storing numbers with decimals instead of having to round off and causing less accurate values. 

Analyzing the multiplexer voltage Saftey: This constraint will be met by following datasheet requirements and limiting the input voltage to the Multiplexer to 5 volts. This will be met since the Arduino mega 2560 is only capable of outputting 5 volts maximum from its 5 volt port according to its datasheet information [1]. Since the Arduino Atmega 2560 can only output 5 volts maximum the the constraint has been met and there is no need to consider any extra precautions for the multiplexer's voltage safety. 

Analyzing the current safety constraint:
This requirement will be met by using current limiting resistors to make sure that no more than 15mA with a 5 % tolerance will flow through to the LEDs. The Multiplexer Datasheet also states that the Multiplexer can output 50mA [4], so there definitely needs to be current limiting resistors calculated and implemented for extra safety measures and to ensure that the LEDs can still operate smoothly. 

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

The truth table below represents the functionality of the the SN74LV4052A multiplexers:

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

# BOM 
Table 4. BOM
|Item                                                         |	Location	    |Quantity |	Price 	| Total price   |
|-------------------------------------------------------------|---------------|---------|---------|---------------|
|Diffused Red 5mm LED (25 pack)                               |	Adafruit.com	| 1	      | $4.00	  | $4.00         |
|Diffused yellow 5mm LED 	                                    | Sparkfun.com	| 2	    | $0.90	  | $0.90         |
|Arduino Mega 2560	                                          | Amazon.com	  | 1	      | $48.90	| $48.90        |
|SN74LV4052A multiplexer |	Ti.com	      | 2	      | $0.948	  | $0.948         |
|Tactile Button switch (6mm) x 20 pack                        |	Adafruit.com 	| 1	      | $2.50	  | $2.50         |
|Full-size Perma proto boards	                                | Adafruit.com	| 2	      | $39.90	| $39.90        |
|20 ft each 18 AWG copper wire with shielded protction(6 different color)                | Amazon.com	| 1	      | $16.49	| $16.49        |
|Resistors (pack of 25 200 ohms)	                                | Adafruit.com	| 2	      | $5.78 | $5.78        |
|		                                                          |               |         | Total:  |	$119.42       |

## References 

[1] A000067-datasheet.pdf, https://docs.arduino.cc/resources/datasheets/A000067-datasheet.pdf (accessed Apr. 10, 2024).   

[2] C++ data types, https://www.w3schools.com/cpp/cpp_data_types.asp (accessed Apr. 14, 2024).

[3] T. Cooper, “All about leds,” Adafruit Learning System, https://learn.adafruit.com/all-about-leds/forward-voltage-and-kvl (accessed Apr. 10, 2024). 

[4] Ti, https://www.ti.com/lit/ds/symlink/sn74lv4052a.pdf (accessed Apr. 16, 2024). 

[5] “What are the forward voltages of different leds?,” CircuitBread, https://www.circuitbread.com/ee-faq/the-forward-voltages-of-different-leds (accessed Apr. 9, 2024). 

 
