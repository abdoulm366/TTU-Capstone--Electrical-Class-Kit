# Input Breadboard Subsystem
## Subsystem Function:
The breadboard subsystem serves as a method for the user to interact with the project. The user will be given several circuit components, including resistors, capacitors, and other circuit components. This subsystem will be integrated into the body of the car, so no separate housing is required. The blocks will contain real circuit components and will be designed so that they are easily interconnected. These components will be connected to a mutli-function sensor circuit. This circuit will analyze the circuit the user builds and will measure either the resistance or the capacitance. The circuit will then send that data to a microcontroller to be analyzed and utilized in the rest of the project. Using these sensor circuit is also safer, as there is no risk of accidentally putting too much current through a component and comprimising the subsystem.

## Constraints/Specification: 
| Description   | Constraints/Specification:   | Source |
|  -     |  -  |  -  |
| Safety  | The board must ensure that no voltages in excess of 50 volts are exceeded in any portion of the subsystem.                               | OSHA 1926.403(i)(2)(i)
| Precision    | The board must be able to detect differences of at least 1.5 times the values (100 ohms versus 150 ohms) for any electrical component and must be accurate to within 5 percent of the component’s true value                         | Conceptual Design
| Weight |The board must be light enough (less than 3 pounds) so that it does not contribute significantly to the weight of the car. | Conceptual Design
| Variety    | The circuit components provided must vary in their values enough so that the changes they make would be perceptible to the function of the project (100, 500, 1000, 10000 ohms, etc.)                         | Conceptual Design
| Speed | The board must be able to determine the component’s value within 1.25 seconds of it being changed to ensure smooth operation of the other systems.| Conceptual Design |

## Schematic:

![image](https://github.com/user-attachments/assets/0a17e418-f76e-490b-8765-7d6f1f1254d8)

Figure 1: Blocks

![image](https://github.com/user-attachments/assets/d7c95d66-61b5-4f2a-b868-5d4e9cfcfb96)

Figure 2: Sensor Circuit

![image](https://github.com/user-attachments/assets/6fecc7a7-fa65-459f-a8aa-245366106651)


Figure 3: PCB Schematic

![image](https://github.com/user-attachments/assets/280ceb92-4e71-4c0f-8e00-799e44e9eb2f)


Figure 4: PCB 3D view

The schematic is divided up into two separate pieces. The first piece (Figure 1) is comprised of all the blocks the user will be able to insert into the sensor circuit (Figure 2) along with the connector values. These values were chosen so that the user would have a wide range of resistances and capacitances to choose from. The titles of each block describe what is contained inside.

The blocks are simple plastic shells that contain the circuit components. The user will connect the legs of the components into the spring loaded terminal blocks in order to make the circuits. They will have resistor blocks, capacitor blocks, a diode block, and three blank connector blocks.

The sensor circuit is made up of a 3x3 grid with a circuit in and a circuit out pin. The selector switch has 3 modes: resistance, off, and capacitance. The user is expected to build their circuit while the switch is set to "off". They will be given blocks containing various circuit components, of which they can insert into the circuit and build up circuits utilzing the traces connecting the terminal blocks together. Then, once the final connection back to the voltage out pin has been made, then they may flip the switch to the correct position depending on what components they used. The circuit is designed to only read resistance or capacitace separately, so no RC circuits may be made in this grid. However, there is a diode block that can be utilized in both circuits, to varying effects depending on the configuration of the circuit.

The PCB above shows the required circuitry. The Arduino Mega 2560 will be mounted to the car body itself, with the shield attatched to the top. Then, all of the schematic connections from the arduino will be made by soldering to the shield. The grid will operate as follows: Male to Female Jumper Wires will be soldered to the pads in the PCB on the right, where the female ends will be mounted to a plastic housing on top of the car. This will serve as the pseudo-breadboard for the user to interact with.

## Analysis:

The analysis for this subsystem is straightforward. Simple voltage division equations can be used to determine the reading of the output voltage. This equation, in its general form reads, $V\_{\\text{out}} = V\_{s}(\\frac{R\_{\\text{block}}}{{R\_{\\text{reference}} + R}\_{\\text{block}}})$. The calculated output voltage will not be necessary for the sake of the Uno, as it will read and convert this voltage to a corresponding resistance value. As shown in the article and video [2], the circuit can detect any resistance up to 10 Mega Ohms, which is more than the max value allowed by the blocks. As a result, the analysis is already complete, as the ciruit is already proven to be able to achieve the desired result(s). Since the input voltage is so low, there is little to no risk of any overcurrent in any part of the resistor circuit. One additional calculation that was necessary was to ensure that no resistor fell below 200 Ohms. The reason for this design choice is so that if the capacitance mode is selected by accident, then no resistor configuration would burn up because of the power limit (0.5 W). This equation can be simply read as  $P = V^{2}/R$. Using this equation with the values P = 0.125 Watts and V = 5 volts, the resulting minimum resistance is 200 Ω. With this value and the resistors selected, the minimum resistor value can be no less than 220 Ω. Concerning the possibility of max resistance, (which would be approximately 1.17 MΩ), the mux would most likely select the 5 MΩ resistor for its voltage comparison. As long as the input resistance is lower than the highest resistance, the Ohmmeter will make an accurate assesment of the resistance of the circuit.

The block resistors have a lower tolerance than the reference resistors (as can be seen above). This is because the reference resistors need to be as close as possible to their listed resistance value as posible, so that the voltage divider equation can work. The circuit for resistance sensing uses a mux [3] and some C code to automatically select which value to place in series with the block resistor, so that the user can make any arrangement of resistors they want.

The next bit of analysis necessary is for the capacitor sensing. The capacitor (in a dc circuit) will charge up to a point where then it will block any more current from flowing through it. While many approaches can be taken to measure capacitance, this project will utilize a simple method that is as follows: the capacitor will slowly increase in voltage until it hits the 5-volt threshold. However, if we know the time from 0.2 volts (accounting for the circuit when there is no capacitor inserted) to 3.5 volts, then we can use the elapsed time between these two points to determine which capacitor was plugged in. This can be simulated in LTSpice, which is where these figures will come from. Attached below are simulations of all the circuits, followed by a table laying out the times. 


![image](https://github.com/abdoulm366/TTU-Capstone--Electrical-Class-Kit/assets/158489186/5dc354bf-c9c1-49ff-8b07-c48eca29c22b)


Figure 5: 0.1 μF circuit

![image](https://github.com/abdoulm366/TTU-Capstone--Electrical-Class-Kit/assets/158489186/c6d303ce-f706-4971-bd66-3132f5d75c3f)


Figure 6: 0.15 μF circuit


![image](https://github.com/abdoulm366/TTU-Capstone--Electrical-Class-Kit/assets/158489186/63ab379e-22c2-47a2-a040-43550a67634c)


Figure 7: 0.22 μF circuit

![image](https://github.com/abdoulm366/TTU-Capstone--Electrical-Class-Kit/assets/158489186/5037d911-ac15-420a-aafa-fb8a65481dc7)


Figure 8: 0.68 μF circuit

![image](https://github.com/abdoulm366/TTU-Capstone--Electrical-Class-Kit/assets/158489186/a1f8ea64-e7f4-468f-92d8-5314a4fc9a1e)


Figure 9: 1 μF circuit

![image](https://github.com/abdoulm366/TTU-Capstone--Electrical-Class-Kit/assets/158489186/fb33e4d8-661a-40e9-b27c-fdc1a37ff8c4)

Figure 10: 2.2 μF circuit

| *V*<sub>*S*</sub> (V) | *R*<sub>reference</sub> (Ω) | Capacitance (μF) | Time (ms)  |
|-----------------------|-----------------------------|------------------|------------|
| 5                     | 100k                        | 0.1              | 11.62      |
| 5                     | 100k                        | 0.15                | 18.04     |
| 5                     | 100k                        | 0.22               | 25.45 |
| 5                     | 100k                        | 0.68                | 78.95    |
| 5                     | 100k                        | 1              | 116.02      |
| 5                     | 100k                        | 2.2                | 255.43    |

As can be seen above in the table and the pictures, the time never exceeds 1.2 seconds, so the constraint of working within 2 seconds is easily met.  The times are also different enough that there’s no chance of mistaking one value for another. Another point of reference is that the time in milliseconds is equal to 1.16 times the capacitance given in μF. As a result, a simple C program will be sufficient to determine the capacitance based on the time alone, given the same resistane and input voltage.

Considering the weight constraint (which was no more than 3 pounds), the design is sufficient enough to fulfill that constraint. The heaviest component is easily the Arduino Mega [4]. The Mega weighs in at 1.31 ounces. Considering that no other component even approaches that weight, the entire subsysystem is easily under the weight limit, and passes this constraint.

Lastly, the effect of the diode is the easiest to both understand and calculate. Since the diode is a binary-acting device, its output voltage is either high or zero. Most diodes have a 0.7 voltage drop, and since the Peak Inverse Voltage is far less than even 5 volts, all it will have to do is block current going the other way. The analog in port will then find that the voltage is zero, and appropriate adjustments can be made to affect the rest of the project. 

## B.O.M.
|Item                              |Distributor |Quantity |Part Number             |Manufacturer                      |Price   |Total Price |
|----------------------------------|------------|---------|------------------------|----------------------------------|--------|------------|
|Arduino Mega R3                   |Amazon      |1        |B01H4ZLZLQ              |Arduino                           |$29.99  |$29.99      |
|Arduino Mega R3 Shield                  |Amazon      |1        |B081DW6JXB             |Dingyu                         |$15.24  |$15.24      |
|Male to Female Jumper Wire               |Amazon      |1        |B01EV70C78              |Elegoo                           |$6.98  |$6.98      |
|Resistor Pack                   |Amazon      |1        |B08FHPKF9V              |Bojack                           |$13.99  |$13.99      |
|Capacitor Pack                   |Amazon      |1        |B07PBQXQNQ              |Bojack                           |$16.99  |$16.99      |
|DPDT Switch                   |Digikey      |1        |100DP1T1B1M2QEH              |E-Switch                           |$3.68  |$3.68      |
|Max 4617|Digikey      |1        |MAX4617CPE              |Analog Devices Inc.                           |$7.38  |$7.48      |
|Diodes                  |Amazon      |1        |B07YG8K1R9              |Bojack                           |$9.99  |$9.99      |
|1% tolerance resistors                  |Amazon      |1        |B0CDWVLTM1              |Allecin                           |$9.99  |$9.99      |
|                                  |            |         |                        |                                  |Total:  |$114.33      |


## Citation:
[1] “1926.403 - general requirements.,” Occupational Safety and Health Administration, https://www.osha.gov/laws-regs/regulations/standardnumber/1926/1926.403 (accessed Mar. 31, 2024). 

[2] M. Cheich, “Build your own ohmmeter!,” Programming Electronics Academy, https://www.programmingelectronics.com/ohmmeter/ (accessed Apr. 9, 2024). 

[3] Max4617/MAX4618/ max4619 | data sheets, https://www.analog.com/media/en/technical-documentation/data-sheets/MAX4617-MAX4619.pdf (accessed Apr. 9, 2024). 

[4] “Arduino Mega,” Arduino Online Shop, https://store-usa.arduino.cc/products/arduino-mega?selectedStore=us (accessed Apr.22, 2024). 






