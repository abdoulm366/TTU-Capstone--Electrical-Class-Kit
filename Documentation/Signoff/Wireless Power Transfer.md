# Wireless Power Transfer

## Function 

The purpose of the wireless power transfer subsystem is to demonstrate wireless power and to power the gears and steering subsystems to allow the car to move. It will consist of transmitters inside of a designed housing or “mat” which the car will be able to navigate on, and a receiver on the bottom of the car, also in a designed housing, which receives the power from the transmitter and powers the mentioned subsystems.  

## Constraints

|Description    |Constraint                                                                                                  |Source              |
|---------------|------------------------------------------------------------------------------------------------------------|--------------------|
|Voltage        |The system shall step down the voltage to meet the requirements of the supplied subsystems.                 |[4]                 |
|Voltage        |The system shall convert AC to DC to supply the buck boost.                                                 |[4]                 |
|Precision      |Subsystems one and two shall receive no more than 12 V and 1 A.                                             |[2]                 |
|Safety         |The system shall operate in a safe and efficient distance range involving the transmitter and receiver.     |[3]                 |
|Ethics         |The system shall be designed so that energy consumption is within an acceptable range for this application. |[3]                 |
|Socioeconomic  |The system shall stay relevant to the budget of the project staying within an affordable range.             |Conceptual Design   |

## Buildable Schematic

<img width="518" alt="Transformer Buildable Schematic" src="https://github.com/abdoulm366/TTU-Capstone--Electrical-Class-Kit/assets/157627603/63c58ab3-b56c-4182-aa3d-8a8c8e944123">

Figure 1. Initial Power

<img width="520" alt="Buck Boost Buildable Schematic" src="https://github.com/abdoulm366/TTU-Capstone--Electrical-Class-Kit/assets/157627603/2df0cbfa-03bd-449a-860c-6ee5aa948c53">

Figure 2. Buck Boost

<img width="518" alt="Voltage Regulatos Buildable Schematic V2" src="https://github.com/abdoulm366/TTU-Capstone--Electrical-Class-Kit/assets/157627603/40ff8649-d44c-47a6-b8e6-5804030abfe6">

Figure 3. Voltage Regulators

## Analysis

<img width="959" alt="Wireless Power Transfer LTSpice V2" src="https://github.com/abdoulm366/TTU-Capstone--Electrical-Class-Kit/assets/157627603/1e7cc8da-90b3-4a33-ae87-6b86835cd381">

Figure 4. Wireless Power Transfer Subsystem

Figure 4 shows the circuit fully built in LTSpice. The system is further broken down and simulated in the following figures.

<img width="959" alt="Transformer LTSpice" src="https://github.com/abdoulm366/TTU-Capstone--Electrical-Class-Kit/assets/157627603/64b509d9-011a-4815-8669-50a13caab5fc">

Figure 5. Transformer

In figure 5, the first transformer is being simulated. The system will be powered by a standard wall outlet, the voltage will initially be 120 V with a frequency of 60 Hz. The purpose of the transformer is to step down the voltage to approximately 24 V. As seen above, this is accomplished. Furthermore, the transformer being used will be the TCT40-01E07AE [6]. Considering price and performance, this is the ideal transformer for this application. The above simulation is how this transformer will operate when placed in this system according to the datasheet. 

<img width="959" alt="Transmitter_Receiver_BridgeRectifier LTSpice" src="https://github.com/abdoulm366/TTU-Capstone--Electrical-Class-Kit/assets/157627603/5537cd92-4213-408e-b6e4-98fabc4e4fca">

Figure 6. Wireless Power Transfer 

In figure 6, the transmitter, receiver, and bridge rectifier are being simulated. The voltage source represents the output voltage of the transformer in figure 5. The transmitter and receiver are labeled above and represent the wireless power transfer. The turns ratio will be 1:1, keeping the voltage consistent and providing enough voltage to the next buck boost in the next figure. The bridge rectifier is being used to convert AC to DC in this case. This is needed because the power supply to the following subsystems needs to be DC. From the simulation, the primary voltage for the transmitter is an AC value by analyzing the graph, but the voltage at node Vout is a DC value as expected. The transmitter will be placed within a “mat” which the car will navigate on. This will allow for the transmitter to be protected and add a level of safety to the kit. Furthermore, the receiver will be places in a housing attached to the bottom of the car which will provide power to the buck boost. 


<img width="959" alt="Buck_Boost LTSpice" src="https://github.com/abdoulm366/TTU-Capstone--Electrical-Class-Kit/assets/157627603/f4e23e98-745e-417a-bee4-2fe7887afa58">

Figure 7. Buck Boost

To ensure that voltages and currents are consistent and correct, the buck boost is being used. This drops the voltage from 24 V to 12 V and the current goes to 500 mA [4]. The inductor, capacitor, and resistor values are from the datasheet. The only values that are changed are the resistors connected to FB and PVout. Manipulating these values will result in a different voltage and current. These values were adjusted until the desired values were found. 

<img width="959" alt="Voltage Regulator 1 LTSpice V2" src="https://github.com/abdoulm366/TTU-Capstone--Electrical-Class-Kit/assets/157627603/f734df7c-9319-4036-9766-4d0e9fa92b45">

Figure 8. Voltage Regulator 1

<img width="959" alt="Voltage Regulator 2 LTSpice V2" src="https://github.com/abdoulm366/TTU-Capstone--Electrical-Class-Kit/assets/157627603/0a42ec89-68ac-448e-bff8-ef6895878cd6">


Figure 9. Voltage Regulator 2

There are two subsystems which need to be powered from this subsystem. Considering the output for the gears and steering, both subsystems require between 7 V and 12 V with a maximum of 1 A. Using the voltage regulators in figures 8 and 9, the values were set up based on the datasheet except for the resistor values connected to SW and FB. These values were manipulated to find the desired values for the output. From the simulations in figures 8 and 9, the voltage and current values are 9 V and 500 mA which is correct for the application. 

## B.O.M.

|Item                   |Location       |Quantity |Price      |Total Price     |
|-----------------------|---------------|---------|-----------|----------------|
|TCT40-01E07AE Transformer          |Digikey        |1        |$17.12     |                |
|LTC3114-1 Buck Boost             |Mouser         |1        |$10.95     |                |
|LTC3621 Voltage Regulator                |Mouser         |3        |$8.11      |                |
|Diode(1N914) (Full Bridge Rectifier)          |Digikey        |4        |$0.10      |                |
|10µF Capacitor         |Jameco         |2        |$0.17      |                |
|33nF Capacitor         |Jameco         |1        |$0.35      |                | 
|4700pF Capacitor       |Jameco         |1        |$0.05      |                |
|4.7µF Capacitor        |Jameco         |1        |$0.29      |                |
|68nF Capacitor         |Jameco         |2        |$0.29      |                |
|30µF Capacitor         |Jameco         |1        |$0.35      |                |
|1µF Capacitor          |Jameco         |3        |$0.15      |                |
|22pF Capacitor         |Jameco         |3        |$0.19      |                |
|22µF Capacitor         |Jameco         |3        |$0.11      |                |
|6.8µH Inductor         |Jameco         |1        |$0.91      |                |
|4.7 µH Inductor        |Jameco         |3        |$1.17      |                |
|20kΩ Resistor          |Digikey        |1        |$0.10      |                |
|27.4kΩ Resistor        |Digikey        |1        |$0.10      |                |
|16.9kΩ Resistor        |Digikey        |1        |$0.10      |                |
|190kΩ Resistor         |Digikey        |1        |$0.17      |                |
|140kΩ Resistor         |Digikey        |2        |$0.10      |                |
|10kΩ Resistor          |Digikey        |2        |$0.10      |                |
|500kΩ Resistor         |Digikey        |1        |$0.31      |                |
|100kΩ Resistor         |Digikey        |1        |$0.52      |                |
|18 AWG Copper Wire (Transmitter/Receiver)     |Amazon     |1     |$13.10     |
|                       |               |         |Total:     |$74.61          |

## References

[1] A beginner’s Guide to Power Quality · open power quality. Open Power Quality. (n.d.). https://openpowerquality.org/docs/intro-power-quality.html 

[2] Agarwal, T. (2019, August 1). Arduino Mega 2560 board: Specifications, and Pin Configuration. ElProCus. https://www.elprocus.com/arduino-mega-2560-board/ 

[3] Kesler, M. (n.d.). Highly Resonant Wireless Power Transfer: Safe, Efficient, and Over Distance. WiTricity. https://7144078.fs1.hubspotusercontent-na1.net/hubfs/7144078/media/Highly-Resonant-Wireless-Power-Transfer.pdf 

[4] LTC3114-1. LTC3114-1 Datasheet and Product Info | Analog Devices. (n.d.). https://www.analog.com/en/products/ltc3114-1.html 

[5] LTC3621. LTC3621 Datasheet and Product Info | Analog Devices. (n.d.). https://www.analog.com/en/products/ltc3621.html 

[6] TCT40-01E07AE Triad magnetics | Mouser. (n.d.).https://www.mouser.com/ProductDetail/Triad-Magnetics/TCT40-01E07AE/?qs=b1anAsPanWze5LUZnt24Jw%3D%3D 
