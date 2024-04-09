# Input Breadboard Subsystem
## Subsystem Function:
The breadboard subsystem serves as a method for the user to interact with the project. The user will be given several circuit components, including resistors, capacitors, and other circuit components. This subsystem will be built separately from the body of the “car”, as adjusting the circuit layout on a moving vehicle might prove to be a little troublesome.  The blocks will contain real circuit components and will be made in a way that no polarities can get mixed up, which eliminates any risk of overcurrent. Instead, these components will be connected to sensor circuits (resistive, capacitive, etc.). The circuits will send that data to a microcontroller to be analyzed and utilized in the rest of the project. Using these sensor circuits is also safer, as there is no risk of accidentally putting too much current through a component and comprising the subsystem. Also on this breadboard will be some switches, buttons, and other general input components. These will be hardwired in and control the outputs assigned to other subsystems.

## Constraints/Specification: 
| Description   | Constraints/Specification:   | Source |
|  -     |  -  |  -  |
| Safety  | The board must ensure that no voltages in excess of 50 volts are exceeded in any portion of the subsystem.                               | OSHA 1926.403(i)(2)(i)
| Precision    | The board must be able to detect differences of at least 1.5 times the values (100 ohms versus 150 ohms) for any electrical component and must be accurate to within 10 percent of the component’s true value                         | Conceptual Design
| Weight |The board must be light enough (less than 5 pounds) so that it can be held with minimal discomfort. | Conceptual Design
| Variety    | The circuit components provided must vary in their values enough so that the changes they make would be perceptible to the function of the project (100, 500, 1000, 10000 ohms, etc.)                         | Conceptual Design
| Speed | The board must be able to deduce the component’s value within 2 seconds of it being changed to ensure smooth operation of the other systems.| Conceptual Design |

## Schematic:

![Blocks](https://github.com/abdoulm366/TTU-Capstone--Electrical-Class-Kit/assets/158489186/3742b745-e42a-4e8e-bf62-34e6e8e66ad5)

Figure 1: Blocks

![Sensor](https://github.com/abdoulm366/TTU-Capstone--Electrical-Class-Kit/assets/158489186/444aa9f5-9170-4d9a-8af3-6043f7a8efde)

Figure 2: Sensor Circuit

The schematic is divided up into two separate pieces. The first piece (Figure 1) is comprised of all the blocks the user will be able to insert into the sensor circuit (Figure 2) along with the connector values. These values were chosen so that the user would have a wide range of resistances and capacitances to choose from. The titles of each block describe what is contained inside.
The gold pieces in both the blocks and the sensor circuit represent contacts to allow the flow of current between the blocks and the sensor circuit when they are connected. The connector blocks are used to demonstrate series and parallel connections.  The user will take two of the blocks (either resistor or capactior) and slot them into the appropiate connector block. Then, they will take the connector block and slot it into the appropiate port of the sensor circuit. 
Once the connector block is placed in the appropriate slot (left to right = Resistor, Capacitor, and Diode), then the reference circuit built into the sensor is completed, and that voltage is picked up and transmitted to one of the Uno’s analog input pins. Once the MCU receives this data, it will make adequate adjustments to other various parts of the project depending on what value was read in.

## Analysis:

The analysis for this subsystem is straightforward. Simple voltage division equations can be used to determine the reading of the output voltage. This equation, in its general form reads, $V\_{\\text{out}} = V\_{s}(\\frac{R\_{\\text{block}}}{{R\_{\\text{reference}} + R}\_{\\text{block}}})$. The calculated output voltage will not be necessary for the sake of the Uno, as it will read and convert this voltage to a corresponding resistance value. As shown in the artice and video [2], the circuit can detect any resistance up to 10 Mega Ohms, which is more than the max value allowed by the blocks. As a result, the analysis is already complete, as the ciruit is already proven to be able to achieve the desired result(s).

The block resistors have a lower tolerance than the reference resistors (as can be seen above). This is because the reference resistors need to be as close as possible to their listed resistance value as posible, so that the voltage divider equation can work. The circuit for resistance sensing uses a mux [3] and some C code to automatically select which value to place in series with the block resistor, so that the user can make any arrangement of resistors they want.

The next bit of analysis necessary is for the capacitor sensing. The capacitor (in a dc circuit) will charge up to a point where then it will block any more current from flowing through it. While many approaches can be taken to measure capacitance, this project will utilize a simple method that is as follows: the capacitor will slowly increase in voltage until it hits the 5-volt threshold. However, if we know the time from 0.2 volts (accounting for the circuit when there is no capacitor inserted) to 3.5 volts, then we can use the elapsed time between these two points to determine which capacitor was plugged in. This can be simulated in LTSpice, which is where these figures will come from. Attached below are simulations of all the circuits, followed by a table laying out the times.


![image](https://github.com/abdoulm366/TTU-Capstone--Electrical-Class-Kit/assets/158489186/5dc354bf-c9c1-49ff-8b07-c48eca29c22b)


Figure 3: 0.1 μF circuit

![image](https://github.com/abdoulm366/TTU-Capstone--Electrical-Class-Kit/assets/158489186/239efe6f-3f0c-4735-b720-566b50e39156)


Figure 4: 1 μF circuit


![image](https://github.com/abdoulm366/TTU-Capstone--Electrical-Class-Kit/assets/158489186/315764e9-08bc-44a6-b7dd-8d323679bde5)


Figure 5: 10 μF circuit

![image](https://github.com/abdoulm366/TTU-Capstone--Electrical-Class-Kit/assets/158489186/ea1c76eb-4a8f-4092-9e80-2571e07cd163)


Figure 6: 2 μF circuit

![image](https://github.com/abdoulm366/TTU-Capstone--Electrical-Class-Kit/assets/158489186/27749972-32b5-4057-b7d4-1673173140a3)


Figure 7: 0.5 μF circuit

![image](https://github.com/abdoulm366/TTU-Capstone--Electrical-Class-Kit/assets/158489186/a3ce240c-72c6-4ad7-a606-84274be2a3ed)


Figure 8: 5 μF circuit

| *V*<sub>*S*</sub> (V) | *R*<sub>reference</sub> (Ω) | Capacitance (μF) | Time (ms)  |
|-----------------------|-----------------------------|------------------|------------|
| 5                     | 100k                        | 0.1              | 11.62      |
| 5                     | 100k                        | 1                | 120.18     |
| 5                     | 100k                        | 10               | 1.16\*10^3 |
| 5                     | 100k                        | 2                | 232.56     |
| 5                     | 100k                        | 0.5              | 58.12      |
| 5                     | 100k                        | 5                | 580.85     |

As can be seen above in the table and the pictures, the time never exceeds 1.2 seconds, so the constraint of working within 2 seconds is easily met. The times are also different enough that there’s no chance of mistaking one value for another. Another point of reference is that the time in milliseconds is equal to 1.16 times the capacitance given in microFarads. As a result, a simple line of C code will be able to determine the capacitance based on the time alone, given the same resistane and input voltage.

Lastly, the diode block is the easiest to both understand and calculate. Since the diode is a binary-acting device, its output voltage is either high or zero. Most diodes have a 0.7 voltage drop, and since the Peak Inverse Voltage is far less than even 5 volts, all it will have to do is block current going the other way. The analog in port will then find that the voltage is zero, and appropriate adjustments can be made to affect the rest of the project.

## B.O.M.
| Component Type: | Quantity: | Link                      | Price:   |
|-----------------|-----------|---------------------------|----------|
| Resistors       | 1         | https://shorturl.at/svDE8 | $ 13.99  |
| Capacitors      | 1         | https://shorturl.at/cCFLT | $ 16.99  |
| Diodes          | 1         | https://shorturl.at/fswBG | $ 9.99   |
| Breadboard      | 3         | https://shorturl.at/xzG47 | $ 16.50  |
| Arduino Uno     | 1         | https://shorturl.at/hnxN1 | $ 27.60  |
| PLA Filament    | 1         | https://rb.gy/h0clh3      | $ 27.98  |
| Max 4167    | 1         | https://shorturl.at/EQUY7    | $ 6.18 |
| Resistors (1% tolerance)    | 1         | https://shorturl.at/ajrDO      | $ 9.99  |
|                 |           | Total:                    | $ 129.22|

## Citation:
[1] “1926.403 - general requirements.,” Occupational Safety and Health Administration, https://www.osha.gov/laws-regs/regulations/standardnumber/1926/1926.403 (accessed Mar. 31, 2024). 

[2] M. Cheich, “Build your own ohmmeter!,” Programming Electronics Academy, https://www.programmingelectronics.com/ohmmeter/ (accessed Apr. 9, 2024). 

[3] Max4617/MAX4618/ max4619 | data sheets, https://www.analog.com/media/en/technical-documentation/data-sheets/MAX4617-MAX4619.pdf (accessed Apr. 9, 2024). 






