# Logic Gates Subsystem

##  Function of the System
The function of this subsystem is to introduce the concept of logic gates through an approachable way for someone with little to no experience using AND,OR and NOT gate. The subsystem will be user friendly by using switches to demonstrate these concepts and allow the user to interact with the inputs.


## Constraint

| No. | Constraints                                                           | Origin            |
| --- | --------------------------------------------------------------------- | -----------------|
| 1   | Current in the system can't be no less than 12mA  | Design Constraint |
| 2   | System shall receive between 7V to 12V from Close Loop Control System arduino to operate. [1] | Device Constraint |
| 3   |System shall have an output current no more than 16mA  | Design Constraint [1]|


## Buildable schematic


![image](https://github.com/user-attachments/assets/5044f9e4-5f47-4128-ade4-59e8ed7475dc)



The above image is a schematic of a 5 switches connected to digital port 11, 12, and 13 of the Close Control Loop arduino.   of dual 4 to 1 mux connected to 7 switches which translate the concept of logic gates.  The two switches in series represent an AND gate so output will be high only when both inputs are high. The two switches in parallel represent an OR gate so output will be high when at least one input is high. The schematic focuses on the design of the switches with respect to the overall  circuit design.


# Analysis

<sup>2</sup> System shall receive between 7V to 12V from Close Loop Control System to operate. The output of the system will be 2 arduino pins directly form the Close Loop Control system. Since the arduino is supplying 5V, the system will directly receives  power from the Close Loop Control Sytem. The Datasheet of the SN74LS153 specifies that the chip operates at a voltage between 4.75V to 5.5V. The 5V from the Arduino is within that range so this following specification will be met.

<sup>3</sup> System shall have an output current no more than 16mA. Keeping the output current under 16 mA (recommended in the datasheet) is he current regulator resistor whole purpose. with about 5v entering the mux, a 5k resistor will keep the resistor as low as 1 mA .The system can easily operate on a perf board powered by the Close Loop Control system. The resistor in the schematic is a current regulator resistor limiting the current flow through the multiplexer will ensure a maximum current rating less than 16 mA.

Logic gates are fundamental building blocks of digital circuits, performing logical  operations on one or more binary inputs and producing a single binary output. The system will not be using actual logic gates, but instead use switches and a 4 to 1 mux to explain the logic gates concept. The following truth tables will explain it better.

## AND Gate
The two switches in series represent an AND gate, output will be high only when both inputs are high. It is connected to the second input of the second multiplexer.

| Input   | Input    | output   | 
| ------- | -------- | ---------|
| A       | B        | Y        |             
| 0       | 0        | 0        |
| 0       | 1        | 0        | 
| 1       | 0        | 0        | 
| 1       | 1        | 1        | 

## OR Gate

The two switches in parallel represent an OR gate, output will be high when at least one input is high. It is connected to the third input of the second multiplexer and the enable input of the first multiplexer. 

| Input   |   Input  | output   | 
| --------|----------| -------- |  
| A       | B        | Y        |             
| 0       | 0        | 0        |
| 0       | 1        | 1        | 
| 1       | 0        | 1        | 
| 1       | 1        | 1        | 

## NOT Gate

 The single switch represent the NOT gate.  It is connected to the first input of the first multiplexer and the enable input of the second multiplexer.
| Input      |  output  | 
| ---------- | -------- |  
| A          | Y        |            
| 0          | 1        |            
| 1          | 0        |

## Dual 4 to 1 mux Truth table

| Select Line1| Select Line 2|Input 1 |Input 2   |Input 3 | Input 4| Output |
|------|------|-----|-----|----|----|----|
| S0   | S1   | A   | B   |C   |D   |Y   |
| 0    | 0    | 0   |X |  X |X  | 0 |
| 0    | 0    | 1   |X | X |X   | 1 |
| 0    | 1    | X   |0 | X | X | 0 |
| 0    | 1    | X   |1 |  X |X  | 1  | 
| 1    | 0    | X   | X| 0  |X  |  0 |    
| 1    | 0    | X   | X   | 1  |X  | 1  |
| 1    | 1    | X |  X  |  X | 0  | 0  | 
| 1    | 1    | X  |  X|  X | 1  |1  |           




## BOM
| DEVICE                | Quantity | Price Per Unit | Total Price | Source |
| --------------------- | -------- | -------------- | ----------- | -------| 
| Switches              | 7        | $0.65          | $4.55         | Mouser |
| LED                   | 2       | $1.13          | $1.13       | Mouser |
|  5k Resistor          | 1        | $0.29          | $0.29        |  Jameco    |
 
 
 Total Cost: $5.97
# References

[1] Ti, www.ti.com/lit/ds/symlink/sn74ls153.pdf?ts=1713912581496&ref_url=https%253A%252F%252Fwww.google.com%252F. Accessed 29 Apr. 2024. 

[2] SN74LS153N Texas Instruments | Mouser, www.mouser.com/ProductDetail/Texas-Instruments/SN74LS153N?qs=SL3LIuy2dWxINdb8Y9aA1A%3D%3D.

[3] DS04-254-2-01bk-Smt-Tr Cui Devices | Mouser, www.mouser.com/ProductDetail/CUI-Devices/DS04-254-2-01BK-SMT-TR?qs=wnTfsH77Xs4xXRFXKF0ssg%3D%3D.

[4] Metal Oxide Resistor 5k Ohm 5 Watt | Jameco Valuepro, www.jameco.com/z/RSF-MO5WS5KJBU-Jameco-Valuepro-Resistor-Metal-Oxide-5K-Ohm-5-Watt-5-_2274335.html. 
