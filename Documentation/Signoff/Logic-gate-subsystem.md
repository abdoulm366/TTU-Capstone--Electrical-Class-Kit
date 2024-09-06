# Logic Gates Subsystem

##  Function of the System
The function of this subsystem is to introduce the concept of logic gates through an approachable way for someone with little to no experience using AND,OR and NOT gate. The subsystem will be user-friendly by using switches and LEDs to demonstrate these concepts and allow the user to interact with the inputs.


## Constraint

| Description | Constraints                                                   | Origin            |
| --- | --------------------------------------------------------------------- | -----------------|
| Current Safety | Current in the system shall be between 12 mA and 30 mA [3] | LED Constraint |
| Voltage regulation | System shall use 5v from the Arduino UNO to operate | Device Constraint |
|  Explicit  | Switches shall be labeled for a user-friendly interaction  | simplicity Constraint|
| Cost Limit  |Any components and equipment within this subsystem should not exceed $40 dollars and the subsystems total cost should not exceed $120 to help keep the project budget in the 400-900 range| Conceptual Design|

## Buildable schematic

![image](https://github.com/user-attachments/assets/726d0e72-cc31-455a-bc9a-9b4c88de9018)




The above image is a schematic of 5 switches and 2 LEDs connected to digital port 11, 12, and 13 of the Close Control Loop arduino subsystem, responsible for moving the car. The two switches in series represent an AND gate so output will be high only when both inputs are high. The two switches in parallel represent an OR gate so output will be high when at least one input is high, and the single switch represent the Not gate, output will be high when input is low and vice versa. The schematic focuses on the circuit design of the switches with respect to the overall diagram.


# Analysis
If we are analyzing the current constraint, it shall not be less thant 12 mA and no more than 50 mA as it is specified in the datasheet [1]. Excessive current can lead to component frying or malfunctionning the reason why we have this constraint in place. Since the arduino is operating on 5v [2], our subsystem will need 2 current limiting resistor to limit the current throught the LEDs. V = RI => R = $\frac{v}{I}$.     
V = 5V , I = 12 mA.   

R = $\frac{5}{0.012}$ = 417 ohms. To keep the current between 12mA and 30mA, a 300 ohm resistor is perfect because it brings the current to about 16mA with a voltage of 5V.

How will the Subsystem work? 
The user will interact with the switches sending signals to the arduino. There are five switches total. The single switch represents the NOT gate, responsible for moving the EV car backwards. It is connected to digital pin 11 of the arduino uno where appropriate codes will instruct it to do such things. The two switches in series represents the AND gate, current/signal will go through only when both switches are on, staying in the same definition spectrum of the "AND Gate". It is connected to digital pin 12 of the Arduino. They ( switches in series) move the car forward when both are on. Appropriate codes will also instruct the uno board to do so.
The last two switches in parallel represents the OR gate, current/signal will go through when at least one switch is on, staying in the same definition spectrum of the OR gate. It is Connected to digital pin 13 of the arduino. They (switches in parallel) also move the car foward when at least on switch is on.

So, how do we know which switches is responsible for moving the car when it is going foward. Well, that is the exact reason why we included LEDs in our subsystem. We have a total of two LEDs, each one of them is in series with the AND switches and the Or switches so that whichever group of switch is on, the respective LED will light up. From the user point of view it will tremendously help explain how logic gates works as they( user) will physically observe the differences and similarities between AND and OR gates.

|A|B|And|Or|
|-|-|---|--|
|0|0|0|0|
|0|1|0|1|
|1|0|0|1|
|1|1|1|1|

Table 1.

As we can see from table 1 above, there are two instances where OR and And are the same and two where they are different. The LEDs will physically show that OR and AND gates have the same output when the inputs are the same, and different outputs when the inputs are different.

Below are the truth table for NOT,AND and OR gates.

## AND Gate
The two switches in series represent an AND gate, output will be high only when both inputs are high.

| Input   | Input    | output   | 
| ------- | -------- | ---------|
| A       | B        | Y        |             
| 0       | 0        | 0        |
| 0       | 1        | 0        | 
| 1       | 0        | 0        | 
| 1       | 1        | 1        | 

## OR Gate

The two switches in parallel represent an OR gate, output will be high when at least one input is high.  

| Input   |   Input  | output   | 
| --------|----------| -------- |  
| A       | B        | Y        |             
| 0       | 0        | 0        |
| 0       | 1        | 1        | 
| 1       | 0        | 1        | 
| 1       | 1        | 1        | 

## NOT Gate

 The single switch represent the NOT gate.  
| Input      |  output  | 
| ---------- | -------- |  
| A          | Y        |            
| 0          | 1        |            
| 1          | 0        |




## BOM
| DEVICE                | Quantity | Price Per Unit | Total Price | Source |        Link|
| --------------------- | -------- | -------------- | ----------- | -------|------- |
| Switches              | 5       | $0.65          | $3.25       | Mouser | https://www.mouser.com/ProductDetail/CUI-Devices/DS04-254-1S-01BK?qs=wnTfsH77Xs41j%252BLlbi1wiw%3D%3D    |
| LED                   | 2       | $0.16          | $0.32       | Mouser |https://www.mouser.com/ProductDetail/Cree-LED/C5SMF-RJE-CT0W0BB1?qs=sGAEpiMZZMuCm2JlHBGefrW%252BuZaT7rx%2FrgviDEgrvNI%3D|
| 300 Ohms Resistor     | 2        | $0.10          | $0.20        |  mouser   |https://www.mouser.com/ProductDetail/KOA-Speer/MF1-4LCT52R301G?qs=91WPSIiQh9J0pu6y%252B4d0Wg%3D%3D|
 
 
 Total Cost: $3.77


# References
[1] https://www.mouser.com/datasheet/2/723/HB_C5SMF_RJF_RJE_GJF_GJE_BJF_BJE-3402153.pdf

[2]  “Arduino Uno REV3.” Arduino Online Shop, store-usa.arduino.cc/products/arduino-uno-rev3?gad_source=1&gclid=CjwKCAjwlbu2BhA3EiwA3yXyu4hsJT3p0tzEam3W_WHjW9Dal0CS2KojE_k9SLhoPBFiI5uEDC_3GxoCv1wQAvD_BwE. Accessed 28 Aug. 2024.

[3] https://www.ledsupply.com/blog/how-does-a-5mm-led-work/#:~:text=5mm%20LED%20Current.%20Now
