# Noise Cancelation and Amplification Subsystem

## Function of the system
The function of the subsystem is to familiarize users with the application of noise cancellation and amplification. Using code to manipulate the original sound, users will be able to select whether the output sound is canceled or amplified. This subsystem will introduce the user to how circuitry can influence the output gain of a signal. 
## Constraints
| No. | Constraints | Origin |
|-----|-------------|---------|
|1.   | The gain shall not exceed 91 dB to prohibit distortion  | System constraint|
|2. | Speakers shall output between 20 Hz and 20 kHz | Listening range for humans |


# Buildable schematic

![buildable](https://github.com/abdoulm366/TTU-Capstone--Electrical-Class-Kit/assets/158213085/6dd87019-54e7-4dee-9bad-8c25f63d6c66)

Kicad schematic:  Figure 1 

This schematic shows how the user will interpret the subsystem. The subsystem will not consist of any hardware components expect the speakers, push buttons, and the switch. Users will use resistors to influence the output gain of the second speaker by varying the feedback resistor. Once the user inputs a resistance value (via the input system) it will be sent to the Arduino where code simulates the desired circuit’s gain equation. Using this found value, it will then be sent to the second speaker where the user will hear the change in sound. 


# Analysis

There are two main parts to this subsystem: a non-inverting circuit to represent amplification and an inverting circuit to represent noise cancelation. In this subsystem there will be two speakers with push buttons to toggle on and off. The first speaker will output a 1 kHz sound while the second speaker will output the sound the user is testing. There will be a SPDT switch to control which circuit the user is testing. To make this subsystem interactive users will input a resistor as a feedback resistor for the circuit. Using a code to equate the gain equation, will allow minimum hardware for this subsystem.  

The spdt on-off-on switch was chosen to toggle between the inverting and non-inverting circuit, so students will be able to easily control which circuit to use. The on-off-on function is what determined this switch over others. This is due to its ability to send a signal easily to the desired output and has an off function when the subsystem is not in use [2]. The speakers were chosen based on the size compadibility and the frequency range. The speaker is rated at an impedance of 8 ohms, so there will be an 8 Ω resistor soldered in series with each speaker. 


## Noise Amplification Portion

The non-inverting circuit will be demonstrated with R1 = 2.2 kΩ and the feedback resistor R with remcommended values of 220 Ω, 470 Ω, 1kΩ, 1.5kΩ, and 2.2kΩ. These resistors are recommend for two reasons: to keep the speakers from playing a distorted sound and clipping. There will be code that will act as if its clipping the circuit if users decide to use higher rated resistors. To find the gain for a non-inverting circuit users will use the equation 1 + Rf/R1 [5]. 


*In all LT spice simulations the blue wave is Vin and the green wave is Vout*

<img width="800" alt="![nonivertingMINRf]" src="https://github.com/abdoulm366/TTU-Capstone--Electrical-Class-Kit/assets/158213085/1160a88c-6cab-49ee-a6a1-81b6e126ea80">

  LT spice simulation with minimum recommended feedback resistance: Figure 2



<img width="800" alt="![noninvertingMAXRf]" src="https://github.com/abdoulm366/TTU-Capstone--Electrical-Class-Kit/assets/158213085/5cc7ebd4-cf14-4c3b-a94c-2369389df630">

 LT spice simulation with maximun recommended feedback resistance: Figure 3

   *Below is proof that the recommended resistors will keep the gain within constraint 1*
<img width="500" alt = "![matlabNON]" src ="https://github.com/abdoulm366/TTU-Capstone--Electrical-Class-Kit/assets/158213085/5f41b0d5-cb4e-43b7-8938-8435b00311c2">

Figure 4: Matlab Graph of Non-Inverting Op-Amp Gain vs. Recommended Resistor Values

### Noise Cancelation Portion
The inverting circuit shown below is a representation of the circuit used to cancel the original output signal. To cancel a sine wave there needs to be an inverted signal (180-degree phase shift) at the same frequency. R1 of this circuit will be 2.2 kΩ and the feedback resistor is what the user choses. The recommened values for Rf will be 470 Ω, 1 kΩ, 1.5 kΩ, 2.2kΩ, and 4.7 kΩ. Users will use the equation -Rf/R1 [5].

<img width="800" alt="![invertingMINRf]" src = "https://github.com/abdoulm366/TTU-Capstone--Electrical-Class-Kit/assets/158213085/411b91f3-999a-424d-9009-39970d048f4c">


 LT spice simulation with minimun recommened feedback resistor: Figure 5

<img width="800" alt="![invertingMAXRf]" src ="https://github.com/abdoulm366/TTU-Capstone--Electrical-Class-Kit/assets/158213085/342344e4-f8c3-4e27-bec6-dc07ff941fdc">


 LT spice simulation with maxium recommended feedback resistor: Figure 6


*Below is proof that the recommended resistors will keep the gain within constraint 1*

<img width="500" alt="![matlabINV]" src ="https://github.com/abdoulm366/TTU-Capstone--Electrical-Class-Kit/assets/158213085/1c39f84a-e514-4a62-a6cb-c3094f8018de">

Figure 7: Matlab Graph of Inverting Op-Amp Gain vs. Recommended Resistor Values




# BOM
| Device | Price | Quanity | Total Cost | Source |
|--------|-------|---------|------------|--------|
| Push Button | $1.95 | 2 | $3.90 | [4] |
| Mini Speaker | $3.15 | 2 | $6.30 | [3]
| SPDT switch | $5.15 | 1 | $5.15 | [2] |
| 8 Ω resistor| $0.40 | 2 | $0.80 | [1] |

Total cost for subsystem: 16.15 ( not including tax or shipping)

# References 

[1] Carbon Film Resistor 1/4 Watt 2K Ohm | Jameco Valuepro, www.jameco.com/z/CF1-4W202JRC-Jameco-ValuePro-Resistor-Carbon-Film-2k-Ohm-1-4-Watt-5-_690937.html. 

[2] Carling Technologies Toggle Switch, SPDT, 3 Connections, on/off/on, 3/4 Hp, 10A @ 250V AC, 15A @ 125V AC 2FC53-73-TABS | Zoro, www.zoro.com/carling-technologies-toggle-switch-spdt-3-connections-onoffon-34-hp-10a-250v-ac-15a-125v-ac-2fc53-73-tabs/i/G1588553/. 

[3] “CMS-28528N-L152 CUI Devices | Audio Products | DigiKey.” Digikey.Com, www.digikey.com/en/products/detail/cui-devices/CMS-28528N-L152/6137734. 

[4] Industries, Adafruit. “On-off Power Button / Pushbutton Toggle Switch.” Adafruit Industries Blog RSS, www.adafruit.com/product/1683. 

[5] Storr, Wayne. “Inverting Operational Amplifier - the Inverting Op-Amp.” Basic Electronics Tutorials, 4 Aug. 2022, www.electronics-tutorials.ws/opamp/opamp_2.html. 

