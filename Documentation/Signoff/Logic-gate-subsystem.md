# Logic Gates Subsystem

##  Function of the System
The function of this subsystem is to introduce the concept of logic gates through an approachable way for someone with little to no experience using AND,OR and NOT gate. The subsystem will be user friendly by using switches to demonstrate these concepts and allow the user to interact with the inputs.


## Constraint

| No. | Constraints                                                           | Origin            |
| --- | --------------------------------------------------------------------- | -----------------|
| 1   | Current in the system can't be no less than 12mA  | Design Constraint |
| 2   | System shall receive between 7V to 12V from Close Loop Control System arduino to operate.| Device Constraint |
| 3   | Switches shall be labeled for a user friendly subsystem |  Constraint|


## Buildable schematic


![image](https://github.com/user-attachments/assets/5044f9e4-5f47-4128-ade4-59e8ed7475dc)



The above image is a schematic of a 5 switches connected to digital port 11, 12, and 13 of the Close Control Loop arduino. The two switches in series represent an AND gate so output will be high only when both inputs are high. The two switches in parallel represent an OR gate so output will be high when at least one input is high, and the single switch represent the Not gate. The schematic focuses on the circuit design of the switches with respect to the overall diagram.


# Analysis


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




## BOM
| DEVICE                | Quantity | Price Per Unit | Total Price | Source |
| --------------------- | -------- | -------------- | ----------- | -------| 
| Switches              | 5       | $0.65          | $3.25       | Mouser |
| LED                   | 2       | $1.13          | $1.13       | Mouser |
| 560 Ohms Resistor     | 2        | $0.29          | $0.29        |  Jameco    |
 
 
 Total Cost: $5.97
# References

