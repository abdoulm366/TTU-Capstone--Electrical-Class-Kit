# Wireless Power Transfer

## Function 

The purpose of this subsystem is to power the vehicle through wireless power transfer and demonstrate basic concepts of power and energy through user interaction. The time of charge will be adjustable by the user, allowing them to analyze the different drive times of the car. This will allow the user to learn the basics of how power and energy behave through the use of wireless power transfer.

## Constraints

|Description    |Constraint                                                                                                            |Source                      |
|---------------|----------------------------------------------------------------------------------------------------------------------|----------------------------|
|Standard       |The system shall operate at less than 50 V to ensure safety in an educational setting.                                |OSHA 1926.403(i)(2)(i)      |
|Voltage        |The output shall not exceed 4.2 V to ensure there is no overcharge of the battery.                                    |Datasheet/Digikey           | 
|Frequency      |The system shall operate between 110 kHz and 205 kHz to optimize charging capability.                                 |Datasheet/Wireless Charging |

<sup>1</sup> Accoriding to OSHA 1926.403(i)(2)(i), any voltage 50 V or higher must be enclosed in some manner so that any person cannot physically touch a component with this voltage level[4]. The subsystem shall be kept below the 50 V level to ensure that no accidental shocks occurs.

<sup>2</sup> According to the LTC4120 datasheet and Digikey, 4.2 V is the optimal charging voltage to prevent overcharging of the battery[2][3]. Overcharging the battery can cause safety concerns within the subsystem and cause damage to the battery. 

<sup>3</sup> For wireless charging applications, a frequency range of 110kHz to 205kHz is recommended to ensure optimal charging of low voltage batteries across short distances(1mm to 10mm)[3][5].

## Buildable Schematic
<img alt="Buildable Schematic (kicad)" src="https://github.com/user-attachments/assets/18b81dab-d601-441b-89df-d1cd5ac9d027">

Figure 1. Buildable Schematic

<img alt="Transmitter Inverter (kicad)" src="https://github.com/user-attachments/assets/29c4c7dc-35dc-4e57-9c9f-080858fabe5b">

Figure 2. Transmitter/Inverter

The input voltage for the transmitter will be 6 V DC. This DC value will be converted to an AC value using an inverting circuit while also increasing the frequency. Once the DC value is converted to AC, the power will be transmitted through a 4.95 uH inductive coil which is recommended in the datasheet[3]. 

<img alt="Receiver Rectifier Charger (kicad)" src="https://github.com/user-attachments/assets/a2154664-7ce4-4c35-875c-13ed771d8742">

Figure 3. Receiver/Full Bridge Rectifier/Charger

The receiver will receive the power from the transmitter through a 46 uH inductive coil which is recommended in the datasheet[3]. Once the power is received, a full bridge rectifier will covert the AC value back to DC which is required for the LTC4120. The LTC4120 will then output a suitable voltage and current to charge a lithium-ion battery explained below.

<img alt="Transmitter PCB" src="https://github.com/user-attachments/assets/50a11cb7-271c-4d25-9b9b-ac0c6c3c309d">

Figure 4. Transmitter Circuit PCB

<img alt="Receiver PCB" src="https://github.com/user-attachments/assets/b20597b1-cc5a-4b72-80e0-01baaa87279c">

Figure 5. Recever Circuit PCB 

## Analysis

<img alt="LTSpice Schematic" src="https://github.com/user-attachments/assets/d0fd5b86-2a61-4ab7-9d91-f145a504229f">

Figure 6. Wireless Charging Subsystem

The above figure shows the subsystem in its entirety in LTSpice. The circuit is made up of a DC voltage source, an inverting circuit to convert DC to AC while increasing the frequency, a transmitter, a receiver, a full bridge rectifier to convert AC to DC, and an LTC4120 ic chip. The DC voltage source will be a common replaceable battery that can be easily changed with minimal safety risk. The inverting circuit is used to convert the DC power supply to AC while boosting the frequency to a value between 110kHz and 205kHz. The full bridge rectifier is used to convert the AC value from the receiver back to a DC value which is the input for the LTC4120 chip. The LTC4120 chip is used for consistent and safe battery charging capabilities. 

<img alt="Transmitter Voltage" src="https://github.com/user-attachments/assets/5b848bde-5b67-4d1e-b686-af320e112580">

Figure 7. Transmitter Voltage

The above figure shows the voltage at the transmitter which is between 18V and 19V. The 6V DC input is converted to AC by using an inverting circuit. This configuration also allows for the frequency to reach an optimal value of 133.86 kHz which is calculated below.

$$F_{T} = \frac{1}{2*\pi*\sqrt{C_{T}*L_{T}}}$$

$$F_{T} = 134.54\ kHz$$

Furthermore, this simulation proves that the voltage stays around 18V-19V, well below the 50 V maximum requirement located in the constraints. The circuit component values in the transmitter were used from the datasheet’s recommended values for the LTC4120 [3]. As for the coupling coefficient, the datasheet has a recommended range of 1mm to 10mm; at 1mm, the coupling coefficient is 0.35 and at 10mm, the coupling coefficient is 0.19. For this application, we use the worst-case scenario of 0.19 for all simulations since there will be an expected air gap. The air gap will be kept between the mentioned range. 

<img alt="Receiver Voltage" src="https://github.com/user-attachments/assets/a8a23e1b-bb81-455d-9108-0e50a9b30c71">

Figure 8. Receiver Voltage

The figure above shows the voltage at the receiver after the full bridge rectifier. The AC from the transmitter has been transformed back to DC for an input of roughly 20V. The 20V meets the requirement from the datasheet for the LTC2140’s input which requires between 12.5 V and 40 V as an input. The capacitors C2S1, C2S2, C2P1, and C2P2 were chosen based off the datasheet while maintaining an efficient frequency which is calculated below.

$$F_{CS,CP} = \frac{1}{2*\pi*\sqrt{\left( C_{2P} + C_{2S} \right)*L_{R}}}$$

$$F_{CS,CP} = 129.44\ kHz$$

<img width="959" alt="LTC4120 Output Voltage and Current" src="https://github.com/user-attachments/assets/bbf0b336-671c-49f4-bec8-f265616cffb9">

Figure 9. Output Voltage and Current

The figure above shows the current and voltage outputs for the battery charger. The battery being charged will be a 9-12V lithium-ion battery which is capable of being charged at 4.2 V. From the simulation, the maximum voltage is 4.2V and the maximum current is 500mA. The LTC4120 is the optimal chip for charging batteries as it ensures a certain voltage and current output providing extra safety features. 

![image](https://github.com/abdoulm366/TTU-Capstone--Electrical-Class-Kit/assets/157627603/13f02cae-23ed-4f2c-8878-42156d3b4c80)

Figure 12. Rheostat

The above figure is a representation of how a rheostat works, which is similar to a potentiometer but can operate at very low resistances. The purpose of the rheostat is to allow the user to adjust the voltage for charging the battery. It will essentially allow the user to increment the resistance by 1Ω which will lower the voltage. The voltages analyzed in LTSpice are below in the graphs which calculate the estimated run time corresponding to the energy stored in the battery. The formula is also below.

$$T = \frac{{(Voltage \times Time) \times 1000}}{{1000000 \times 60}}$$

Table 1. Run Time at 60 Seconds Charge Time

|Voltage(V)      |Time(sec)     |Runtime(sec)    |
|----------------|--------------|----------------| 
|4.2             |60            |15.12           |
|3.81            |60            |13.716          |
|3.43            |60            |12.348          |
|3.05            |60            |10.98           |
|2.67            |60            |9.612           |
|2.29            |60            |8.244           |
|1.9             |60            |6.84            |
|1.52            |60            |5.472           | 
|1.14            |60            |4.104           |
|0.76            |60            |2.736           |
|0.38            |60            |1.368           |

Table 2. Run Time at 50 Seconds Charge Time

|Voltage(V)      |Time(sec)     |Runtime(sec)    |
|----------------|--------------|----------------| 
|4.2             |50            |12.60           |
|3.81            |50            |11.43           |
|3.43            |50            |10.29           |
|3.05            |50            |9.15            |
|2.67            |50            |8.01            |
|2.29            |50            |6.87            |
|1.9             |50            |5.70            |
|1.52            |50            |4.56            | 
|1.14            |50            |3.42            |
|0.76            |50            |2.28            |
|0.38            |50            |1.14            |

Table 3. Run Time at 40 Seconds Charge Time

|Voltage(V)      |Time(sec)     |Runtime(sec)    |
|----------------|--------------|----------------| 
|4.2             |40            |10.08           |
|3.81            |40            |9.14            |
|3.43            |40            |8.23            |
|3.05            |40            |7.32            |
|2.67            |40            |6.40            |
|2.29            |40            |5.49            |
|1.9             |40            |4.56            |
|1.52            |40            |3.48            | 
|1.14            |40            |2.73            |
|0.76            |40            |1.82            |
|0.38            |40            |0.91            |

Table 4. Run Time at 30 Seconds Charge Time

|Voltage(V)      |Time(sec)     |Runtime(sec)    |
|----------------|--------------|----------------| 
|4.2             |30            |7.56            |
|3.81            |30            |6.85            |
|3.43            |30            |6.17            |
|3.05            |30            |5.49            |
|2.67            |30            |4.80            |
|2.29            |30            |4.12            |
|1.9             |30            |3.42            |
|1.52            |30            |2.73            | 
|1.14            |30            |2.05            |
|0.76            |30            |1.36            |
|0.38            |30            |0.68            |

Table 5. Run Time at 20 Seconds Charge Time

|Voltage(V)      |Time(sec)     |Runtime(sec)    |
|----------------|--------------|----------------| 
|4.2             |20            |5.04            |
|3.81            |20            |4.57            |
|3.43            |20            |4.11            |
|3.05            |20            |3.66            |
|2.67            |20            |3.20            |
|2.29            |20            |2.74            |
|1.9             |20            |2.28            |
|1.52            |20            |1.82            | 
|1.14            |20            |1.36            |
|0.76            |20            |0.91            |
|0.38            |20            |0.45            |

Table 6. Run Time at 10 Seconds Charge Time

|Voltage(V)      |Time(sec)     |Runtime(sec)    |
|----------------|--------------|----------------| 
|4.2             |10            |2.52            |
|3.81            |10            |2.28            |
|3.43            |10            |2.05            |
|3.05            |10            |1.83            |
|2.67            |10            |1.60            |
|2.29            |10            |1.37            |
|1.9             |10            |1.14            |
|1.52            |10            |0.91            | 
|1.14            |10            |0.68            |
|0.76            |10            |0.45            |
|0.38            |10            |0.22            |



## B.O.M.

|Item                                 |Location       |Quantity |Price      |Total Price |
|-------------------------------------|---------------|---------|-----------|------------|
|22 uF Capacitor                      |Digikey        |2        |$1.82      |$3.64       |
|150 nF Capacitor                     |Jameco         |1        |$0.19      |$0.19       |
|100 nF Capacitor                     |Jameco         |1        |$0.19      |$0.19       |
|33 nF Capacitor                      |Jameco         |1        |$0.39      |$0.39       |
|10 nF Capacitor                      |Jameco         |2        |$0.19      |$0.38       |
|22 nF Capacitor                      |Digikey        |1        |$0.27      |$0.27       |
|4.7 nF Capacitor                     |Mouser         |2        |$0.49      |$0.98       |
|1.5 nF Capacitor                     |Jameco         |1        |$0.12      |$0.12       |
|10 uF Capacitor                      |Jameco         |1        |$0.55      |$0.55       |
|2.2 uF Capacitor                     |Jameco         |2        |$0.19      |$0.38       |
|0.022 uF Capacitor                   |Jameco         |2        |$0.19      |$0.38       |
|68 uH Inductor                       |Mouser         |2        |$0.52      |$1.04       |
|33 uH Inductor                       |Jameco         |2        |$1.11      |$2.22       |
|1 k Resistor                         |Digikey        |2        |$0.10      |$0.20       |
|1.01 Meg Resistor                    |Jameco         |2        |$0.05      |$0.10       |
|1.35 Meg Resistor                    |Jameco         |2        |$0.04      |$0.08       |
|3.01 k Resistor                      |Jameco         |2        |$0.06      |$0.12       |
|477 k Resistor                       |Jameco         |2        |$0.06      |$0.12       |
|BAT54 Zener Diode                    |Mouser         |5        |$0.42      |$2.10       |
|BZX84C15L Zener Diode                |Mouser         |2        |$0.14      |$0.28       |
|SI4470DY Transistor                  |Mouser         |2        |$1.58      |$3.16       |
|YXQ 25W Rheostat                     |Amazon         |1        |$8.99      |$8.99       |
|1.5 V AA Battery                     |Amazon         |1        |$4.75      |$4.75       |
|4xAA Battery Holder                  |Amazon         |1        |$7.49      |$7.49       |
|9 V Lithium-ion Battery              |Amazon         |1        |$23.49     |$23.49      |
|9 V Lithium-ion Battery Holder       |Amazon         |1        |$5.99      |$5.99       |
|22 AWG Copper Wire (75 Feet)         |Amazon         |1        |$4.88      |$4.88       |
|                                     |               |         |Total:     |$72.48      |

## References

[1] DigiKey’s North American Editors. (2016, August 2). Inductive versus resonant wireless charging: A truce may be a designer’s best choice. DigiKey. https://www.digikey.com/en/articles/inductive-versus-resonant-wireless-charging#:~:text=The%20Qi%20specification%20calls%20for%20an%20AC%20frequency,to%20120%20W%29%20for%20the%20%E2%80%9Cmedium%20power%E2%80%9D%20chargers. 

[2] DigiKey’s North American Editors. (2016b, September 1). A designer’s guide to lithium (li-ion) battery charging. DigiKey. https://www.digikey.com/en/articles/a-designer-guide-fast-lithium-ion-battery-charging?utm_adgroup=General&utm_source=bing&utm_medium=cpc&utm_campaign=Dynamic+Search_EN_RLSA&utm_term=digikey&utm_content=General&utm_id=bi_cmp-384476624_adg-1302921504343623_ad-81432643449113_dat-2333232393680005%3Aaud-807631101%3Aloc-190_dev-c_ext-_prd-&msclkid=a47310e72a021b0d165d76ce42b58086 

[3] LTC4120-4120-4.2.PDF. (n.d.). https://www.analog.com/media/en/technical-documentation/data-sheets/ltc4120-4120-4.2.pdf 

[4] 1926.403 - general requirements. Occupational Safety and Health Administration. (n.d.). https://www.osha.gov/laws-regs/regulations/standardnumber/1926/1926.403 

[5] Wireless charging in consumer applications. (n.d.-b). https://www.st.com/content/dam/AME/2019/developers-conference-2019/presentations/STDevCon19_6.1_Wireless_Charging.pdf 

