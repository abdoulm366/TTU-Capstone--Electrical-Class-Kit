# Wireless Power Transfer

## Function 

The purpose of the wireless power transfer subsystem is to simply demonstrate how wireless power works and to also provide power to the gears, steering, and energy/power demonstration subsystems. It will consist of a transmitter inside of a designed housing or pad which the car will be able to move on and a receiver on the bottom of the car which receives the power from the transmitter and powers the subsystems mentioned above.  The main power supply will be a typical wall outlet which will provide 120 V and 60 Hz [1]. The voltage here will be too high for this system, so a transformer will be used to step down this voltage to 24 V and 1 A [4]. The following subsystems will require DC power; therefore, this subsystem will use a full-bridge rectifier to convert AC to DC. From this, there will be a transmitter and receiver built to transfer this power wirelessly from the pad to the car. A buck boost will be used to create an output of 12 V and will be connected to a voltage regulator for each of the mentioned subsystems [2]. Having a voltage regulator for each subsystem will ensure that each subsystem has the correct power supply [3]. 

## Constraints

C1. The system shall step down the voltage to meet the requirements of the supplied subsystems.

C2. Subsystems one and two shall receive no more than 12 V and 1 A.

C3. Subsystem three shall receive between 2.5 V - 5 V and no more than 1 A.

C4. The system shall use durable and reliable parts. 

C5. The system shall operate in a safe and efficient distance range. 

C6. The system shall comply with safety standards and regulations.

Ethical Constraints

C7. The system shall be designed so that energy consumption is within an acceptable range for this application.

Socioeconomic Constraints

C8. The system shall stay relevant to the budget of the project staying within an affordable range.

## Buildable Schematic

<img width="518" alt="Transformer Buildable Schematic" src="https://github.com/abdoulm366/TTU-Capstone--Electrical-Class-Kit/assets/157627603/63c58ab3-b56c-4182-aa3d-8a8c8e944123">

Figure 1. Initial Power

<img width="520" alt="Buck Boost Buildable Schematic" src="https://github.com/abdoulm366/TTU-Capstone--Electrical-Class-Kit/assets/157627603/2df0cbfa-03bd-449a-860c-6ee5aa948c53">

Figure 2. Buck Boost

<img width="520" alt="Voltage Regulators Buildable Schematic" src="https://github.com/abdoulm366/TTU-Capstone--Electrical-Class-Kit/assets/157627603/42800173-ce7f-4624-9a2e-667d377beeb4">

Figure 3. Voltage Regulators

## Analysis

<img width="959" alt="Wireless Power Transfer LTSpice" src="https://github.com/abdoulm366/TTU-Capstone--Electrical-Class-Kit/assets/157627603/9802aed2-61aa-451d-a064-6e94a4457dac">

Figure 4. Wireless Power Transfer Subsystem

Figure 4 shows the circuit fully built in LTSpice. The system is further broken down and simulated in the following figures.

<img width="959" alt="Transformer LTSpice" src="https://github.com/abdoulm366/TTU-Capstone--Electrical-Class-Kit/assets/157627603/64b509d9-011a-4815-8669-50a13caab5fc">

Figure 5. Transformer

In figure 5, the first transformer is being simulated. Since the system will be powered by a standard wall outlet, the voltage will initially be 120 V. The purpose of the transformer is to step down the voltage to approximately 24 V. As seen above, this is accomplished. Furthermore, the transformer being used will be the TCT40-01E07AE [4]. Considering price and performance, this is the ideal transformer for this application. The above simulation is how this transformer would operate when placed in this system according to the datasheet. 

<img width="959" alt="Transmitter_Receiver_BridgeRectifier LTSpice" src="https://github.com/abdoulm366/TTU-Capstone--Electrical-Class-Kit/assets/157627603/5537cd92-4213-408e-b6e4-98fabc4e4fca">

Figure 6. Wireless Power Transfer 

In figure 6, the transmitter, receiver, and bridge rectifier are being simulated. The voltage source represents the output voltage of the transformer in figure 5. The transmitter and receiver are labeled above and represent the wireless power transfer. The turns ratio will be 1:1, keeping the voltage consistent and providing enough voltage to the next buck boost in the next figure. The bridge rectifier is being used to convert AC to DC in this case. This is needed because the power supply to the following subsystems needs to be DC. From the simulation, the primary voltage for the transmitter is an AC value by analyzing the graph, but the voltage at node Vout is a DC value as expected. 

<img width="959" alt="Buck_Boost LTSpice" src="https://github.com/abdoulm366/TTU-Capstone--Electrical-Class-Kit/assets/157627603/f4e23e98-745e-417a-bee4-2fe7887afa58">

Figure 7. Buck Boost

To ensure that voltages and currents are consistent and correct, the buck boost is being used. This drops the voltage from 24 V to 12 V and the current goes to 500 mA [2]. The inductor, capacitor, and resistor values are from the datasheet. The only values that are changed are the resistors connected to FB and PVout. Manipulating these values will result in a different voltage and current. These values were adjusted until the desired values were found. 

<img width="959" alt="Voltage Regulator 1 LTSpice" src="https://github.com/abdoulm366/TTU-Capstone--Electrical-Class-Kit/assets/157627603/7a7e824c-69b8-4ca2-bacd-c4defdd753f7">

Figure 8. Voltage Regulator 1

<img width="959" alt="Voltage Regulator 2 LTSpice" src="https://github.com/abdoulm366/TTU-Capstone--Electrical-Class-Kit/assets/157627603/27e86f93-dd82-4465-9721-e8ce7db848f0">

Figure 9. Voltage Regulator 2

There are three subsystems which need to be powered from this subsystem. Firstly, the output for the gears and steering are considered. Both subsystems require between 7 V and 12 V with a maximum of 1 A. Using the voltage regulators in figures 8 and 9, the values were set up based on the datasheet except for the resistor values connected to SW and FB. These values were manipulated to find the desired values for the output. From the simulations in figures 8 and 9, the voltage and current values are 9 V and 500 mA which is correct for the application. 

<img width="959" alt="Voltage Regulator 3 LTSpice" src="https://github.com/abdoulm366/TTU-Capstone--Electrical-Class-Kit/assets/157627603/319efdad-88e1-4003-ac1e-184d8db7f5ef">

Figure 10. Voltage Regulator 3

For the third subsystem, the output is required to be between 2.5 V and 5V and no more than 1 A. As discussed above, the component values are from the datasheet and only the two resistor values were changed to get the desired values. From the simulation in figure 10, the output voltage is 3.5 V, and the current is 500 mA. 

## B.O.M.

|Item                   |Location       |Quantity |Price      |Total Price     |
|-----------------------|---------------|---------|-----------|----------------|
|TCT40-01E07AE          |Digikey        |1        |$17.12     |                |
|LTC3114-1              |Mouser         |1        |$10.95     |                |
|LTC3621                |Mouser         |3        |$8.11      |                |
|Diode(1N914)           |Digikey        |4        |$0.10      |                |
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
|                       |               |         |Total:     |$61.51          |

## References

[1] A beginner’s Guide to Power Quality · open power quality. Open Power Quality. (n.d.). https://openpowerquality.org/docs/intro-power-quality.html 

[2] LTC3114-1. LTC3114-1 Datasheet and Product Info | Analog Devices. (n.d.). https://www.analog.com/en/products/ltc3114-1.html 

[3] LTC3621. LTC3621 Datasheet and Product Info | Analog Devices. (n.d.). https://www.analog.com/en/products/ltc3621.html 

[4] TCT40-01E07AE Triad magnetics | Mouser. (n.d.). https://www.mouser.com/ProductDetail/Triad-Magnetics/TCT40-01E07AE/?qs=b1anAsPanWze5LUZnt24Jw%3D%3D 
