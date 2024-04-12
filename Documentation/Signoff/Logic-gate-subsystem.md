# Logic Gates Subsystem

## Function of the System
The function of this subsystem is to move the car forward and backward as it familiarizes the user with the most common logic gates (AND, OR, NOT). This system is a critical part of the kit because it basically serves as an ignition key to the whole car. Forward and backward movement of the car will be the base of understanding logic gate definition.

## Constraint

| No. | Constraints                                                           | Origin            |
| --- | --------------------------------------------------------------------- | ----------------- |
| 1   |  System shall operate at less than 50V, safe voltage level suitable for educational purposes [1].        | Design Constraint |
| 2   |System shall be run through by a current less than 5mA. | Design Constraint |
| 3   | System shall include resistors ranging from 10 ohms to 100k ohms| Design Constraint | 
| 4   |System shall be able to receive input from the user through the DIP Switch | Design Constraint |
| 5   |System shall provide a clear understanding of the mentioned logic gates | Ethics Constraint |


<sup>1</sup>	The system shall operate at a voltage level that is less than 50 volts. This is a safety measure to ensure that the system is operating at a low voltage, which reduces the risk of electric shock or injury, especially in educational environment where users may not have extensive experience with electrical systems. The system's operating voltage level should be suitable for educational purposes, the voltage level should be appropriate for teaching and learning about electrical systems without posing significant safety risks to students or instructors.

<sup>2</sup> The system shall not allow more than 5 milliamperes of current to flow through it under normal operating conditions. This is likely specified to ensure safety, as higher currents can pose risks of electric shock or damage to components.

<sup>3</sup> 	The system shall be designed to accommodate the use of resistors with values anywhere between 10 ohms and 100k ohms. It will allow for flexibility in the design and make the system more interactive.

<sup>4</sup> 	The DIP switch is a type of electrical switch typically used in electronic devices for input purposes. It consists of a series of switches arranged in a compact package, where each switch can be independently toggled between two positions (on/off or high/low). By specifying input through a DIP switch, the requirement suggests that users will interact with the system by physically setting the positions of the switches on the DIP switch module. This allows users to provide input or configure the system by manipulating the switches directly.

<sup>4</sup>	The system aims to provide users with a basic or intermediate level of comprehension regarding logic gates.

## Buildable schematic

![image](https://github.com/abdoulm366/TTU-Capstone--Electrical-Class-Kit/assets/158105152/e0df9350-7d56-4a85-a781-1d4b1e99a01d)

# Analysis

### Power
The system could either be powered through a USB connection or through a 9V battery since the Arduino uno R3 allowed both methods.[3] Since the board needs to use the USB port in order to install the designed software, the subsystem will have to be programmed before being connected to the system's power supply to allow the subsystem to boot without being connected directly to a computer

### Logic Gates
Logic gates are fundamental building blocks of digital circuits, performing logical operations on one or more binary inputs and producing a single binary output. The system will collect these binary inputs through the DIP switch connected to the Arduino. Switch 1 through 5 is directly connected to digital pin 7 to 3 in that order. The DIP switch consists of a series of 5 switches arranged in a compact package. The first two switches, 1 and 2, will be the input of the AND gate. Switch 3 and 4 will be the input of the OR gate and switch 5 will be the input of the NOT gate. By playing with these switches and with clear instructions on how they are configured the user shall grasp the concept of Logic gates.

### Output
The output of this subsystem is a DC motor connected to the Arduino through a driver circuit since the motor cannot be driven directly from the Arduino board pins due risks of damage to the board components [3]. The driver circuit consists of a 270-ohm resistor, and npn transistor and a diode. The Transistor acts like a direct switch to the motor. 

## BOM
| DEVICE                | Quantity | Price Per Unit | Total Price |
| --------------------- | -------- | -------------- | ----------- |
| Arduino Uno R3        | 1        | $14.99         |             |
| Transistor (PN222A)   | 1        | $5.74          | $29.25      |
| Resistor              | 1        | N/A            | N/A         |
| Diode (1N4001)        | 10       | $1.50          | $1.50       |
| DC Motor              | 1        | $0.75          | $0.75       |
| DIP Swicth            | 1        | $0.68          | $0.68       |
| Total                 | $24.41   |

# References

[1]  “High Voltage Safety.” Safety, safety.ep.wisc.edu/hazards/high-voltage-safety. Accessed 3 Apr. 2024.

[2] “Arduino - DC Motor.” Online Tutorials, Courses, and eBooks Library, www.tutorialspoint.com/arduino/arduino_dc_motor.htm. Accessed 11 Apr. 2024. 

[3] Team, The Arduino. “Getting Started with Arduino Uno.” Arduino, www.arduino.cc/en/Guide/ArduinoUno/. Accessed 11 Apr. 2024. 
