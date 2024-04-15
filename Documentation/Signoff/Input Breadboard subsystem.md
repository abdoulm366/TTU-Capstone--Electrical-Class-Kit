# Input Breadboard Subsystem
## Subsystem Function:
The breadboard subsystem serves as a method for the user to interact with the project. The user will be given several circuit components, including resistors, capacitors, and other circuit components. This subsystem will be integrated into the body of the car, so no separate housing is required. The blocks will contain real circuit components and will be made in a way that no polarities can get mixed up, which eliminates any risk of overcurrent. Instead, these components will be connected to sensor circuits (resistive, capacitive, etc.). The circuits will send that data to a microcontroller to be analyzed and utilized in the rest of the project. Using these sensor circuits is also safer, as there is no risk of accidentally putting too much current through a component and comprising the subsystem. Also on this breadboard will be some switches, buttons, and other general input components. These will be hardwired in and control the outputs assigned to other subsystems.

## Constraints/Specification: 
| Description   | Constraints/Specification:   | Source |
|  -     |  -  |  -  |
| Safety  | The board must ensure that no voltages in excess of 50 volts are exceeded in any portion of the subsystem.                               | OSHA 1926.403(i)(2)(i)
| Precision    | The board must be able to detect differences of at least 1.5 times the values (100 ohms versus 150 ohms) for any electrical component and must be accurate to within 5 percent of the component’s true value                         | Conceptual Design
| Weight |The board must be light enough (less than 3 pounds) so that it does not contribute significantly to the weight of the car. | Conceptual Design
| Variety    | The circuit components provided must vary in their values enough so that the changes they make would be perceptible to the function of the project (100, 500, 1000, 10000 ohms, etc.)                         | Conceptual Design
| Speed | The board must be able to determine the component’s value within 1.25 seconds of it being changed to ensure smooth operation of the other systems.| Conceptual Design |

## Schematic:

![Blocks](https://github.com/abdoulm366/TTU-Capstone--Electrical-Class-Kit/assets/158489186/036b846e-c349-44a9-a0fa-7b752ba558e2)

Figure 1: Blocks

![Sensor](https://github.com/abdoulm366/TTU-Capstone--Electrical-Class-Kit/assets/158489186/7d827dbc-f07f-4d91-a223-57d7c0215520)


Figure 2: Sensor Circuit

The schematic is divided up into two separate pieces. The first piece (Figure 1) is comprised of all the blocks the user will be able to insert into the sensor circuit (Figure 2) along with the connector values. These values were chosen so that the user would have a wide range of resistances and capacitances to choose from. The titles of each block describe what is contained inside.
The gold pieces in both the blocks and the sensor circuit represent contacts to allow the flow of current between the blocks and the sensor circuit when they are connected. The component blocks are slotted into the connector block before the whole assembly is inserted into the appropriate sensor circuit. This single block allows full plug and play functionality. Based on which values are read, the MCU's will read that data and send it off to the next one. Then, the final MCU will preform the necessary adjustments to the data and send that data off to other parts of the project. While the schematic won't show it, the connector block will be built into an L-shape. The top left corner is the origin of the connections. Any connections read to the immediate right of it will be read as a series connection, and any connection below the main block (into the schematic's z axis) will be read as a parallel connection. This allows for maximum interactivity, as the user can make any arrangement they want before they insert the connector block into the circuit. It can also be noted that the housing for this subsystem will be its own seperate design, but it was necessary to show a rough approximation in order to get the point across for this subsystem's work.

## Analysis:

The analysis for this subsystem is straightforward. Simple voltage division equations can be used to determine the reading of the output voltage. This equation, in its general form reads, $V\_{\\text{out}} = V\_{s}(\\frac{R\_{\\text{block}}}{{R\_{\\text{reference}} + R}\_{\\text{block}}})$. The calculated output voltage will not be necessary for the sake of the Uno, as it will read and convert this voltage to a corresponding resistance value. As shown in the artice and video [2], the circuit can detect any resistance up to 10 Mega Ohms, which is more than the max value allowed by the blocks. As a result, the analysis is already complete, as the ciruit is already proven to be able to achieve the desired result(s). Since the input voltage is so low, there is little to no risk of any overcurrent in any part of the resistor circuit.

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

As can be seen above in the table and the pictures, the time never exceeds 1.2 seconds, so the constraint of working within 2 seconds is easily met. The closest any of the values come to exceeding this value is the 10μF capacitor value, but ample time is provided for it to still be read and utilized by the subsytem.  The times are also different enough that there’s no chance of mistaking one value for another. Another point of reference is that the time in milliseconds is equal to 1.16 times the capacitance given in μF. As a result, a simple C program will be sufficient to determine the capacitance based on the time alone, given the same resistane and input voltage.

Considering the weight constraint (which was no more than 3 pounds), the design is sufficient enough to fulfill that constraint. The heaviest component is easily the Arduino Uno [4]. The Uno weighs in at 25 grams a unit, and at 3 units, the total weight is approximately 0.16 pounds. Considering that no other component even approaches that weight, the entire subsysystem is easily under the weight limit, and passes this constraint.

Lastly, the diode block is the easiest to both understand and calculate. Since the diode is a binary-acting device, its output voltage is either high or zero. Most diodes have a 0.7 voltage drop, and since the Peak Inverse Voltage is far less than even 5 volts, all it will have to do is block current going the other way. The analog in port will then find that the voltage is zero, and appropriate adjustments can be made to affect the rest of the project. 

## B.O.M.
| Component Type: | Quantity: | Link                      | Price:   |
|-----------------|-----------|---------------------------|----------|
| Resistors       | 1         | https://shorturl.at/svDE8 | $ 13.99  |
| Capacitors      | 1         | https://shorturl.at/cCFLT | $ 16.99  |
| Diodes          | 1         | https://shorturl.at/fswBG | $ 9.99   |
| Breadboard      | 3         | https://shorturl.at/xzG47 | $ 16.50  |
| Arduino Uno     | 3         | https://shorturl.at/hnxN1 | $ 82.80  |
| Max 4167    | 3         | https://shorturl.at/EQUY7    | $ 18.54 |
| Resistors (1% tolerance)    | 1         | https://shorturl.at/ajrDO      | $ 9.99  |
|                 |           | Total:                    | $ 168.80|

## Citation:
[1] “1926.403 - general requirements.,” Occupational Safety and Health Administration, https://www.osha.gov/laws-regs/regulations/standardnumber/1926/1926.403 (accessed Mar. 31, 2024). 

[2] M. Cheich, “Build your own ohmmeter!,” Programming Electronics Academy, https://www.programmingelectronics.com/ohmmeter/ (accessed Apr. 9, 2024). 

[3] Max4617/MAX4618/ max4619 | data sheets, https://www.analog.com/media/en/technical-documentation/data-sheets/MAX4617-MAX4619.pdf (accessed Apr. 9, 2024). 

[4] “Arduino Uno REV3,” Arduino Online Shop, https://store-usa.arduino.cc/products/arduino-uno-rev3 (accessed Apr. 12, 2024). 






