# Wireless Power Transfer

## Function 

The purpose of this subsystem is to demonstrate wireless charging, energy, and power concepts through user interaction. The voltage will be adjustable by the user to control different charge rates, allowing them to analyze different drive times of the car depending on the power supply and time of charge. This will allow the user to learn how power and energy behave through the use of wireless charging. 

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

<img alt="Buildable Schematic" src="https://github.com/abdoulm366/TTU-Capstone--Electrical-Class-Kit/assets/157627603/dd56d908-6b70-4ba4-98d0-8b24588693f0">

Figure 1. Buildable Schematic

## Analysis

![image](https://github.com/abdoulm366/TTU-Capstone--Electrical-Class-Kit/assets/157627603/df4e5f93-ae17-48fb-9132-d69406a39b37)

Figure 2. Wireless Charging Subsystem

The above figure shows the subsystem in its entirety in LTSpice. The circuit is made up of a DC voltage source, regulator circuit to convert DC to AC while increasing the frequency, a transmitter, a receiver, a full bridge rectifier to convert AC to DC, two LTC4120 ic chips, and a battery. The DC voltage source will be a common replaceable battery that can be easily changed with minimal safety risk. The regulator circuit is used to convert the DC power supply to AC while boosting the frequency to a value between 110kHz and 205kHz. The full bridge rectifier is used to convert the AC value from the receiver back to a DC value which is the input for the LTC4120. The LTC4120 is used for the transmitter and allows for consistent and safe battery charging capabilities. The LTC4120 will consistently output 4.2 volts for battery charging. A rheostat will be implemented at the output to allow the user to adjust the voltage and see the affects of different voltages and charging times. 

![image](https://github.com/abdoulm366/TTU-Capstone--Electrical-Class-Kit/assets/157627603/19ad7fb9-8ee3-4233-a013-f09f02d4f2e3)

Figure 3. Transmitter Voltage

The above figure shows the voltage at the transmitter. The 5 V DC input is converted to AC by using a configuration of zener diodes and transistors. This configuration also allows for the frequency to reach an optimal value of 133.86 kHz which is calculated below.

$$F_{T} = \frac{1}{2*\pi*\sqrt{C_{T}*L_{T}}}$$

$$F_{T} = 133.86\ kHz$$

Furthermore, this simulation proves that the voltage stays around 15 V, well below the 50 V maximum requirement located in the constraints. The circuit component values in the transmitter were used from the datasheet’s recommended values for the LTC4120 [3]. As for the coupling coefficient, the datasheet has a recommended range of 1mm to 10mm; at 1mm, the coupling coefficient is 0.35 and at 10mm, the coupling coefficient is 0.19. For this application, we use the worst-case scenario of 0.19 for all simulations since there will be an expected air gap. The air gap will be kept between the mentioned range. 

![image](https://github.com/abdoulm366/TTU-Capstone--Electrical-Class-Kit/assets/157627603/ea3ddb5f-6593-4f51-bc2e-d2c13811aa17)

Figure 4. Receiver Voltage

The figure above shows the voltage at the receiver after the full bridge rectifier. The AC from the transmitter has been transformed back to DC for an input of roughly 15 V. The 15 V meets the requirement from the datasheet for the LTC2140’s input which requires between 12.5 V and 40 V as an input. The capacitors C2S1, C2S2, C2P1, and C2P2 were chosen based off the datasheet while maintaining an efficient frequency which is calculated below.

$$F_{CS,CP} = \frac{1}{2*\pi*\sqrt{\left( C_{2P} + C_{2S} \right)*L_{R}}}$$

$$F_{CS,CP} = 125.9\ kHz$$

![image](https://github.com/abdoulm366/TTU-Capstone--Electrical-Class-Kit/assets/157627603/9504bfb0-be64-4f70-bd80-4d6e6701b1da)

Figure 5. Output Voltage and Current

The figure above shows the current and voltage outputs for the battery charger. The battery being charged will be a 9 V lithium-ion battery which is capable of being charged at a maximum of 4.2 V and 1 A. From the simulation, the maximum voltage is right at 4.2 V and 1 A. The LTC4120 is the optimal chip for charging batteries as it ensures a certain voltage and current output providing extra safety features. 

![image](https://github.com/abdoulm366/TTU-Capstone--Electrical-Class-Kit/assets/157627603/13f02cae-23ed-4f2c-8878-42156d3b4c80)

Figure 6. Rheostat

The above figure is a representation of how a rheostat works, which is similar to a potentiometer but can operate at very low resistances. The purpose of the rheostat is to allow the user to adjust the voltage for charging the battery. It will essentially allow the user to increment the resistance by 1Ω which will lower the voltage. The voltages analyzed in LTSpice are below in the graphs which calculate the estimated run time corresponding to the energy stored in the battery. The formula is also below.

$$T = \frac{{(Voltage \times Time) \times 1000}}{{1000000 \times 60}}$$

Figure 7. Run Time at 60 Seconds Charge Time

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

Figure 8. Run Time at 50 Seconds Charge Time

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

Figure 9. Run Time at 40 Seconds Charge Time

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

Figure 10. Run Time at 30 Seconds Charge Time

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

Figure 11. Run Time at 20 Seconds Charge Time

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

Figure 12. Run Time at 10 Seconds Charge Time

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

