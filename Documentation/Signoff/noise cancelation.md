# Noise Cancelation and Amplification Subsystem

## Function of the system
The function of the subsystem is to familiarize users with the application of noise cancellation and amplification. Using code to manipulate the original sound, users will be able to select whether the output sound is canceled or amplified. This will introduce the user how circuitry can influence the output gain of a signal. 
## Constraints
| No. | Constraints | Origin |
|-----|-------------|---------|
|1.   | The gain shall not exceed 85 dB to prohibit distortion  | System constraint|
|2. |   | Safety constraint|
|3. | Speakers shall output between 20 Hz and 20 kHz | Listening range for humans |


# Buildable schematic

![image](https://github.com/abdoulm366/TTU-Capstone--Electrical-Class-Kit/assets/158213085/e5c88f2e-6473-499e-a9cd-9c09a2c15362)
Kicad schematic:  Figure 1 

This schematic shows how the user will interpret the subsystem. The subsystem will not consist of any hardware components expect the speakers, push buttons, and the switch. Once the user inputs a resistance value (which represents the feedback resistor) it will be sent to the Arduino where code simulates the desired circuit’s gain equation. Using this found value, it will then be sent to the second speaker where the user will hear the change in sound. 


# Analysis

There are two main parts to this subsystem: a non-inverting circuit to represent amplification and an inverting circuit to represent noise cancelation. In this subsystem there will be two speakers with push buttons to toggle on and off. The first speaker will output a 1 kHz sound while the second speaker will output the sound the user is testing. There will be a SPDT switch to control which circuit the user is testing. To make this subsystem interactive users will input a resistor as a feedback resistor for the circuit. Using a code to equate the gain equation, will allow minimum hardware for this subsystem.  

The spdt on-off-on switch was chosen to toggle between the inverting and non-inverting circuit, so students will be able to easily control which circuit to use. The on-off-on function is what determined this switch over others. This is due to its ability to send a signal easily to the desired output and has an off function when the subsystem is not in use [1]. The speakers were chosen based on the size compadibility and the frequency range. 


## Noise Amplification Portion

The non-inverting circuit will be demonstrated with R1 = 2.2 kΩ and the feedback resistor R with possible values of 220 Ω, 470 Ω, 1kΩ, 1.5kΩ, and 2.2kΩ. These resistors were chosen for two reasons: to keep the speakers from playing a distorted sound and clipping. Clipping will not be a problem since there is no hardware circuitry for this subsystem, but as good practice there will not be any representation of circuitry that would result in clipping. To find the gain for a non-inverting circuit users will use the equation 1 + Rf/R1 [4]. 


*In all LT spice simulations the blue wave is Vin and the green wave is Vout*

![nonivertingMINRf](https://github.com/abdoulm366/TTU-Capstone--Electrical-Class-Kit/assets/158213085/1160a88c-6cab-49ee-a6a1-81b6e126ea80)
  LT spice simulation with minimum feedback resistance: Figure 2



![noninvertingMAXRf](https://github.com/abdoulm366/TTU-Capstone--Electrical-Class-Kit/assets/158213085/5cc7ebd4-cf14-4c3b-a94c-2369389df630)
     LT spice simulation with maximun feedback resistance: Figure 3

    
### Noise Amplification Portion
The inverting circuit shown below is a representation of the circuit used to cancel the original output signal. To cancel a sine wave there needs to be an inverted signal (180-degree phase shift) at the same frequency. R1 of this circuit will be 2.2 kΩ and the feedback resistor is what the user choses. The possible values for Rf will be 470 Ω, 1kΩ, 1.5kΩ, 2.2kΩ, and 4.7 kΩ. Users will use the equation -Rf/R1 [4].

![invertingMINRf](https://github.com/abdoulm366/TTU-Capstone--Electrical-Class-Kit/assets/158213085/411b91f3-999a-424d-9009-39970d048f4c)


 LT spice simulation with minimun feedback resistor: Figure 4

![invertingMAXRf](https://github.com/abdoulm366/TTU-Capstone--Electrical-Class-Kit/assets/158213085/342344e4-f8c3-4e27-bec6-dc07ff941fdc)

 LT spice simulation with maxium feedback resistor: Figure 5

| Resistance (Ω) |  Non-Inverting  Gain | in dB | Inverting Gain | in dB |
|------------|---------------------|-------|----------------|-------|
|220 | 1.1 | 0.82 | N/A | N/A |
| 470 | 1.21 | 1.6 | 0.21 | -13.4 |
| 1000 | 1.45 | 3.25 | 0.45 | -6.85 |
| 1500 | 1.68 | 4.52 | 0.68 | -3.32 |
| 2200 | 2 | 6 | 1 | 0| 
| 4700 | N/A | N/A | 2.13 | 6.595 |

# BOM
| Device | Price | Quanity | Total Cost | Source |
|--------|-------|---------|------------|--------|
| push button | $1.95 | 2 | $3.90 | [3] |
| Mini Speaker | $3.15 | 2 | $6.30 | [2]
| SPDT switch | $5.15 | 1 | $5.15 | [1] |
Total cost for subsystem: 15.35 ( not including tax or shipping)

# References 

[1] Carling Technologies Toggle Switch, SPDT, 3 Connections, on/off/on, 3/4 Hp, 10A @ 250V AC, 15A @ 125V AC 2FC53-73-TABS | Zoro, www.zoro.com/carling-technologies-toggle-switch-spdt-3-connections-onoffon-34-hp-10a-250v-ac-15a-125v-ac-2fc53-73-tabs/i/G1588553/. 

[2] “CMS-28528N-L152 CUI Devices | Audio Products | DigiKey.” Digikey.Com, www.digikey.com/en/products/detail/cui-devices/CMS-28528N-L152/6137734. 

[3] Industries, Adafruit. “On-off Power Button / Pushbutton Toggle Switch.” Adafruit Industries Blog RSS, www.adafruit.com/product/1683. 

[4] Storr, Wayne. “Inverting Operational Amplifier - the Inverting Op-Amp.” Basic Electronics Tutorials, 4 Aug. 2022, www.electronics-tutorials.ws/opamp/opamp_2.html. 

