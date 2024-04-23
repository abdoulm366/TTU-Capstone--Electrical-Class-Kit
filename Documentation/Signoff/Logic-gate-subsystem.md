# Logic Gates Subsystem

## Function of the System
The function of this subsystem is to introduce the concept of logic gates through an approachable way for someone with little to no experience using AND,OR and NOT gate. The subsystem will be user friendly by using switches to demonstrate these concepts and allow the user to interact with the inputs.


## Constraint

| No. | Constraints                                                           | Origin            |
| --- | --------------------------------------------------------------------- | ----------------- |
| 1   |  System shall operate at less than 50V, safe voltage level suitable for educational purposes.  | Safety Constraint |
| 2   |System shall be run through by a current less than 30mA. | Device Constraint |
| 3   |System shall be able to receive input from the user through the Switch | Design Constraint |


## Buildable schematic

![image](https://github.com/abdoulm366/TTU-Capstone--Electrical-Class-Kit/assets/158105152/996cc577-d6e0-41cb-8813-b15bd53233d6)

The above image is a schematic of dual 4 to 1 mux connected to 7 switches which translate the concept of logic gates.  The two switches in series represent an AND gate so output will be high only when both inputs are high. The two switches in parallel represent an OR gate so output will be high when at least one input is high. The schematic focuses on the connection ports of the device with respect to the overall  circuit design.


# Analysis


<sup>1</sup>	The system shall operate at a voltage level that is less than 50 volts. This is a safety  measure to ensure that the system is operating at a low voltage, which reduces the risk of  electric shock or injury, especially in educational environments where users may not have  extensive experience with electrical systems.[1] 

<sup>2</sup> The system shall not allow more than 30 mA of current to flow through it under  normal operating conditions. This is specified to ensure safety, as higher currents  can pose risks of electric shock or damage to components. A current regulator resistor is used in the circuit to ensure the following specification is met.

<sup>3</sup> 	The switch is a type of electrical component used in electronic devices for input  purposes. The user will interact  with the system by physically setting the state of the switches. This allows users to provide input and configure the system by manipulating the switches directly. 


The system can easily operate on a perf board powered by the main power subsystem. The resistor in the schematic is a current regulator resistor limiting the current flow through the multiplexer will ensure a maximum current rating less than 30 mA. 
Logic gates are fundamental building blocks of digital circuits, performing logical  operations on one or more binary inputs and producing a single binary output. The system will not be using actual logic gates, but instead use switches and a 4 to 1 mux to explain the logic gates concept. 

The SN74LS153 is a dual 4-to-1 multiplexer, with two 4 to 1 mux intagrated. It is a combinational circuit that selects one of four input data lines and forwards it to a single output line based on the control inputs. Each multiplexer has four data inputs, two control inputs (A and B) shared together, and one output each. The control inputs determine which data input is routed to the output.

The two switches in series represent an AND gate, output will be high only when both inputs are high. It is connected to the second input of the second multiplexer.

| Input   | Input    | output   | 
| ------- | -------- | ---------|
| A       | B        | Y        |             
| 0       | 0        | 0        |
| 0       | 1        | 0        | 
| 1       | 0        | 0        | 
| 1       | 1        | 1        | 

The two switches in parallel represent an OR gate, output will be high when at least one input is high. It is connected to the third input of the second multiplexer. 

| Input   |   Input  | output   | 
| --------|----------| -------- |  
| A       | B        | Y        |             
| 0       | 0        | 0        |
| 0       | 1        | 1        | 
| 1       | 0        | 1        | 
| 1       | 1        | 1        | 

 The single switch represent the NOT gate.  It is connected to the first input of the first multiplexer and the enable input of the second multiplexer. The output is low when the input is high and is high when the input is low. The enable inputs of the multiplexers are active low input meaning that the mux will be active when they are low. Since the single switch is connected to the enable input of the second multiplexer, when it is on the second multiplexer will not be active alowing the first output of the first multiplexer to be on. 

| Input      |  output  | 
| ---------- | ---------|  
| A          | Y        |            
| 0          | 1        |            
| 1          | 0        |

The SN74LS153 is a dual 4-to-1 multiplexer, with 2 4 to 1 mux in it. It is a combinational circuit that selects one of four input data lines and forwards it to a single output line based on the control inputs. Each multiplexer has four data inputs, two control inputs (A and B) shared together, and one output each (Y). The control inputs determine which data input is routed to the output.

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
| 4 to 1 Mux (SN74LS153)| 1        | $1.13          | $1.13       | Mouser |
|  5k Resistor          | 1        | $0.29          | $0.29        |  Jameco    |
 
 
 Total Cost: $5.97
# References

[1]  “High Voltage Safety.” Safety, safety.ep.wisc.edu/hazards/high-voltage-safety.

[2] SN74LS153N Texas Instruments | Mouser, www.mouser.com/ProductDetail/Texas-Instruments/SN74LS153N?qs=SL3LIuy2dWxINdb8Y9aA1A%3D%3D.

[3] DS04-254-2-01bk-Smt-Tr Cui Devices | Mouser, www.mouser.com/ProductDetail/CUI-Devices/DS04-254-2-01BK-SMT-TR?qs=wnTfsH77Xs4xXRFXKF0ssg%3D%3D.

[4] Metal Oxide Resistor 5k Ohm 5 Watt | Jameco Valuepro, www.jameco.com/z/RSF-MO5WS5KJBU-Jameco-Valuepro-Resistor-Metal-Oxide-5K-Ohm-5-Watt-5-_2274335.html. 
