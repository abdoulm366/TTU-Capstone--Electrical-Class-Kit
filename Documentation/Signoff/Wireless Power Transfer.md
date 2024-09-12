# Wireless Power Transfer

## Function 

The purpose of this subsystem is to power the vehicle through wireless power transfer and demonstrate basic concepts of power and energy through user interaction. The time of charge will be adjustable by the user, allowing them to analyze the different drive times of the car. This will allow the user to learn the basics of how power and energy behave through the use of wireless power transfer.

## Constraints

|Description    |Constraint                                                                                                            |Source                      |
|---------------|----------------------------------------------------------------------------------------------------------------------|----------------------------|
|Standard       |The system shall guard against live electrical components to eleminate accidental contact.                            |OSHA 1926.403(i)(2)(i)      |
|Voltage        |The output shall not exceed 4.2 V to ensure there is no overcharge of the battery.                                    |Datasheet/Digikey           | 
|Frequency      |The system shall operate between 110 kHz and 205 kHz to optimize charging capability.                                 |Datasheet/Wireless Charging |

<sup>1</sup> Accoriding to OSHA 1926.403(i)(2)(i), any voltage 50 V or higher must be enclosed in some manner so that any person cannot physically touch a component with this voltage level[4]. The subsystem shall guard against all live components to eleminate accidental contact since it will be used in an educational setting.

<sup>2</sup> According to the LTC4120 datasheet and Digikey, 4.2 V is the optimal charging voltage to prevent overcharging of the battery[2][3]. Overcharging the battery can cause safety concerns within the subsystem and cause damage to the battery. 

<sup>3</sup> For wireless charging applications, a frequency range of 110kHz to 205kHz is recommended to ensure optimal charging of low voltage batteries across short distances(1mm to 10mm)[3][5].

## Buildable Schematic
<img alt="image" src="https://github.com/user-attachments/assets/bd008e93-1c81-4821-b23c-f956f625ff8f">

Figure 1. Buildable Schematic

<img alt="Transmitter Inverter (kicad)" src="https://github.com/user-attachments/assets/29c4c7dc-35dc-4e57-9c9f-080858fabe5b">

Figure 2. Transmitter/Inverter

The input voltage for the transmitter will be 6 V DC. This DC value will be converted to an AC value using an inverting circuit while also increasing the frequency. Once the DC value is converted to AC, the power will be transmitted through a 4.95 uH inductive coil which is recommended in the datasheet[3]. 

<img alt="Receiver (kicad)" src="https://github.com/user-attachments/assets/addd2cfc-2452-46f2-a687-640ca4d04bbe">

Figure 3. Receiver/Full Bridge Rectifier/Charger

The receiver will receive the power from the transmitter through a 46 uH inductive coil which is recommended in the datasheet[3]. Once the power is received, a full bridge rectifier will covert the AC value back to DC which is required for the LTC4120. The LTC4120 will then output a suitable voltage and current to charge a lithium-ion battery explained below.

<img alt="Transmitter PCB" src="https://github.com/user-attachments/assets/50a11cb7-271c-4d25-9b9b-ac0c6c3c309d">

Figure 4. Transmitter Circuit PCB

<img alt="image" src="https://github.com/user-attachments/assets/aceb5a19-869c-48d9-af87-7efbb0381365">

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

<img alt="LTC4120 Output Voltage and Current" src="https://github.com/user-attachments/assets/bbf0b336-671c-49f4-bec8-f265616cffb9">

Figure 9. Output Voltage and Current

The figure above shows the current and voltage outputs for the battery charger. The batteries being charged will be four 3.7V lithium-ion batteries connected in parallel so that each battery will be charged at 4.2V. From the simulation, it is observed that the maximum voltage is 4.2V and the maximum current is 500mA; when the battery reaches full charge at 4.2V, it will stop charging. Furtheremore, two of the 3.7V batteries will power an arduino uno (7.4V) and the other two will charge an arduino atmega 2560 (7.4V) which require between 7V and 12V. The LTC4120 is the optimal chip for charging single cell batteries as it ensures a certain voltage and current output providing safety features. 

The table below represents various charge times with the associated run times. This will allow the user to see how energy is stored and exerted with a constant charging voltage of 4.2V and charging current of 500mA while allowing them to reach the desired run time by calculating the charge time. Since the charger will be charging four batteries in parallel with 500mA, each battery will receiver 125mA. The voltage of the battery will be 3.7V and the capacity will be 1000mAh. The consumption in this case will be 7.4V and 0.75mA. The formulas to find these values is as follows:

$$ChargeAddedto2Batteries = ChargeCurrent * \frac{ChargeTime(seconds)} {3600(seconds)} * 2$$

$$RunTime = \frac{ChargeAdded} {Consumption}$$

Calculation @ 60 Second Charge Time:

$$ChargeAddedto2Batteries = 125mA * \frac{60(seconds)} {3600(seconds)} * 2 = 4.17mAh$$

$$RunTime = \frac{4.17mAh} {75mA} = 3.33min = 200.40sec$$

Table 1. Run Times and Charge Time

|Charge Current Supplied(mA)    |Current Drawn(mA)  |Charge Time(sec)   |Runtime(sec)    |
|-------------------------------|-------------------|-------------------|----------------|
|125                            |75                 |60                 |200.40          |
|125                            |75                 |50                 |166.67          |
|125                            |75                 |40                 |133.33          |
|125                            |75                 |30                 |100.00          |
|125                            |75                 |20                 |66.67           |
|125                            |75                 |10                 |33.33           |



## B.O.M.

|Item                              |Distributor |Quantity |Part Number             |Manufacturer                      |Price   |Total Price |
|----------------------------------|------------|---------|------------------------|----------------------------------|--------|------------|
|AA Batteries                      |Amazon      |1        |B003SI0TD4              |Duracell                          |$8.70   |$8.70       |
|4xAA Battery Pack                 |Adafruit    |1        |830                     |Adafruit                          |$2.95   |$2.95       |
|68uH Inductor                     |Digikey     |2        |445-6568-2-ND           |TDK Corporation                   |$1.15   |$2.30       |
|150nF Capacitor                   |Digikey     |1        |P10969-ND               |Panasonic Electronic Components   |$0.44   |$0.44       |
|100nF Capacitor                   |Digikey     |1        |EF2104-ND               |Panasonic Electronic Components   |$0.40   |$0.40       |
|33nF Capacitor                    |Digikey     |1        |P14577-ND               |Panasonic Electronic Components   |$0.31   |$0.31       |
|Transmitter 4.95uH Coil           |Digikey     |1        |445-172646-ND           |TDK Corporation                   |$7.44   |$7.44       |
|100ohm Resistor                   |Digikey     |2        |541-4010-2-ND           |Vishay Dale                       |$0.10   |$0.20       |
|10nF Capacitor                    |Digikey     |2        |490-4516-2-ND           |Murata Electronics                |$0.10   |$0.20       |
|Transmitter Mosfet                |Digikey     |2        |SI4850EY-T1-GE3TR-ND    |Vishay Siliconix                  |$1.70   |$3.40       |
|SK34SMA-3G   Diode                |Digikey     |5        |4878-SK34SMA-3GTR-ND    |Diotec Semiconductor              |$0.40   |$2.00       |
|BZX84C16-7-F Diode                |Digikey     |2        |BZX84C16-FDITR-ND       |Diodes Incorporated               |$0.15   |$0.30       |
|Receiver 46uH Coil                |Digikey     |1        |445-172409-ND           |TDK Corporation                   |$4.03   |$4.03       |
|4.7nF Capacitor                   |Digikey     |2        |P15431-ND               |Panasonic Electronic Components   |$0.43   |$0.86       |
|22nF Capacitor                    |Digikey     |2        |P14259-ND               |Panasonic Electronic Components   |$0.88   |$1.76       |
|1.5nF Capacitor                   |Digikey     |1        |P10472-ND               |Panasonic Electronic Components   |$1.08   |$1.08       |
|10uF Capacitor                    |Digikey     |1        |445-4042-2-ND           |TDK Corporation                   |$0.30   |$0.30       |
|470kohm Resistor                  |Digikey     |2        |541-4081-2-ND           |Vishay Dale                       |$0.10   |$0.20       |
|2.2uF Capacitor                   |Digikey     |1        |445-5157-2-ND           |TDK Corporation                   |$0.17   |$0.17       |
|15uH Inductor                     |Digikey     |1        |2457-LPS4018-153MRC-ND  |Coilcraft                         |$1.19   |$1.19       |
|3.01kohm Resistor                 |Digikey     |1        |541-5387-2-ND           |Vishay Dale                       |$0.10   |$0.10       |
|1Mohm Resistor                    |Digikey     |1        |541-3965-2-ND           |Vishay Dale                       |$0.10   |$0.10       |
|10kohm Resistor                   |Digikey     |1        |541-3959-2-ND           |Vishay Dale                       |$0.10   |$0.10       |
|1.35Mohm Resistor                 |Digikey     |1        |TNPW12061M35BETA-ND     |Vishay Dale                       |$0.66   |$0.66       |
|22uF Capacitor                    |Digikey     |1        |445-1436-2-ND           |TDK Corporation                   |$0.33   |$0.33       |
|3.7V Lithium-ion Battery          |Amazon      |2        |B0D9R1SJ8Y              |IEVEDIVB                          |$21.88  |$43.76      |
|3.7V Battery Holder               |Amazon      |1        |B07CWKGZXW              |Ltvystore                         |$4.99   |$4.99       |
|                                  |            |         |                        |                                  |Total:  |$88.27      |

## References

[1] DigiKey’s North American Editors. (2016, August 2). Inductive versus resonant wireless charging: A truce may be a designer’s best choice. DigiKey. https://www.digikey.com/en/articles/inductive-versus-resonant-wireless-charging#:~:text=The%20Qi%20specification%20calls%20for%20an%20AC%20frequency,to%20120%20W%29%20for%20the%20%E2%80%9Cmedium%20power%E2%80%9D%20chargers. 

[2] DigiKey’s North American Editors. (2016b, September 1). A designer’s guide to lithium (li-ion) battery charging. DigiKey. https://www.digikey.com/en/articles/a-designer-guide-fast-lithium-ion-battery-charging?utm_adgroup=General&utm_source=bing&utm_medium=cpc&utm_campaign=Dynamic+Search_EN_RLSA&utm_term=digikey&utm_content=General&utm_id=bi_cmp-384476624_adg-1302921504343623_ad-81432643449113_dat-2333232393680005%3Aaud-807631101%3Aloc-190_dev-c_ext-_prd-&msclkid=a47310e72a021b0d165d76ce42b58086 

[3] LTC4120-4120-4.2.PDF. (n.d.). https://www.analog.com/media/en/technical-documentation/data-sheets/ltc4120-4120-4.2.pdf 

[4] 1926.403 - general requirements. Occupational Safety and Health Administration. (n.d.). https://www.osha.gov/laws-regs/regulations/standardnumber/1926/1926.403 

[5] Wireless charging in consumer applications. (n.d.-b). https://www.st.com/content/dam/AME/2019/developers-conference-2019/presentations/STDevCon19_6.1_Wireless_Charging.pdf 

