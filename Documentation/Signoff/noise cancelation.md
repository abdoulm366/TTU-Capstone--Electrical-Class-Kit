# Noise Cancelation and Amplification Subsystem

## Function of the system
The function of the subsystem is to familiarize users with the application of noise cancellation and amplification. Using code to manipulate the original sound, users will be able to select whether the output sound is canceled or amplified. This subsystem will introduce the user to how circuitry can influence the output gain of a signal. 
## Constraints
| No. | Constraints | Origin |
|-----|-------------|---------|
|1.   | The gain shall not exceed 102 dB to prohibit distortion  | System constraint|
|2. | Speakers shall output between 20 Hz and 20 kHz | Listening range for humans |


# Buildable schematic
![InterpretedSS](https://github.com/user-attachments/assets/00b7eb15-efe6-4784-a8f2-fca2f529d168)
Kicad schematic: Interpted Hardware

The subsystem will be used to show users how circuitry in basic op amps ( inv. And non inv.) will affect the output. Students will be familiarized with these two op amps by manipulating the feedback resistor to change the circuits output gain. Students will then be able hear the different outputs by the speaker depending on input from the feedback resistor and which circuit is being used.  The hardware for this subsystem will consist of a spdt switch, a speaker, and a push button to toggle the speaker on/off. The switch will control if the user wants to experiment with the inverting op amp or the non-inverting op amp. Using the input breadboard subsystem students will be able to plug in various resistor types for the feedback resistor. Instead of using two op amps for this subsystem, code will simulate the gain from the feedback resistor chosen by the user and output a percentage of the volume level to match the output gain.

![ActualSS](https://github.com/user-attachments/assets/bfd17467-42c3-4b9c-8970-9f809c49141d)
Kicad schematic: Actual Hardware

# Analysis

There are two main parts to this subsystem: a non-inverting circuit to represent amplification and an inverting circuit to represent noise cancelation. The reference resistor is 470 ohms and the user will be able to experiement with 470, 1k, and 2k ohms. These values will give a realistic gain that is rated for the speaker and will be coded with volume level intensity to simulate noise amplification or noise cancelation. In doing this, users will be able to calculate the gain for each experiement and have an accurate approximation of the volume level via the op amp circuit. If the user decides to use different resistors outside of the reccomended values, an error will show saying it is not a safe circuit for the speaker. 

The spdt on-off-on switch was chosen to toggle between the inverting and non-inverting circuit, so students will be able to easily control which circuit to use. The speaker chosen was based on the size compadibility and the frequency range. 

## Coding portion
For this subsytem to work, code will be implemented to simulate the gain of the circuit in use. WIth the arduino there is a function named "volume.setvolume()". For example to get half the volume control the line of code is volume.setvolume(0.5). For max volume it would write volume.setvolume(1.0). With this it is simple to simulate volume control for each feedback resistor and circuit. To accurately relay a volume control for each experiment I have set a reference resistor as 470 ohms which will be used in all calculations for the gain. KNowing an increase of 3 dB is a doubling of sound intensity, I have set the tone of the 470 omh resistance for the amplifier to be 50%. The gain for this particular part equates to 2, and that is 3 dB less than the gain of the 2 kΩ which relates to 100% tone. Using this proportion I was able to find out the sound intensity for a 1 kΩ feedback resistor accurately. 
## Noise Amplification Portion

 To find the gain for a non-inverting circuit users will use the equation 1 + Rf/R1 [5]. 

| Resistance | Gain | Volume Control |
|-----------|-------|----------------|
| 470 ohms | 1 + 470/470 = 2| 50% |
| 1k ohms | 1 + 1000/470 = 3.13| 71% |
| 2k ohms | 1 + 2000/470 = 5.25 | 100% |



### Noise Cancelation Portion
The inverting circuit shown below is a representation of the circuit used to cancel the original output signal. To cancel a sine wave there needs to be an inverted signal (180-degree phase shift) at the same frequency. R1 of this circuit will be 470 Ω and the feedback resistor is what the user choses. The recommened values for Rf will be 470 Ω, 1 kΩ, and 2 kΩ. Users will use the equation -Rf/R1 [5].

| Resistance | Gain | Volume Control |
|------------|------|----------------|
| 470 ohms | - 470/470 = -1| 40% |
| 1k ohms | - 1000/470 = -2.12| 30% |
| 2k ohms | - 2000/470 = -4.25 | 10% |




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

