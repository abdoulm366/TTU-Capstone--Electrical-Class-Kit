# Noise Cancelation and Amplification Subsystem

## Function of the system
The function of the subsystem is to familiarize users with the application of noise cancellation and amplification. Using code to manipulate the original sound, users will be able to adjust whether the output sound is canceled or amplified. This will show the user how circuitry can influence the output gain of a signal to either amplify or cancel the signal through simple op amps. 
## Constraints
| No. | Constraints | Origin |
|-----|-------------|---------|
|1.   | The gain shall not exceed 92 dB to prohibit distortion  | System constraint|
|2. | Speakers shall output between 20 Hz and 20 kHz | Listening range for humans |


# Buildable schematic
![InterpretedSS](https://github.com/user-attachments/assets/8c6bd14c-94e5-442c-97e4-c89278b7b0eb)

Kicad schematic: Interpted Hardware

The spdt switch was chosen to toggle between the inverting and non-inverting circuit, so students will be able to easily control which circuit to use. The speaker chosen was based on the size compadibility and the frequency range. 

The subsystem will be used to show users how circuitry in basic op amps ( inverting And non inverting ) will affect the output. Students will be familiarized with these two op amps by manipulating the feedback resistor to change the circuits output gain. Students will then be able hear the different outputs by the speaker depending on input from the feedback resistor and which circuit is being used.  The hardware for this subsystem will consist of a spdt switch, a speaker, and a push button to toggle the speaker on/off. Using the input breadboard subsystem students will be able to plug in various resistor types for the feedback resistor. Instead of using two op amps for this subsystem, code will simulate the gain via the feedback resistor chosen by the user and output a percentage of the volume level to match the output gain.

![ActualSS](https://github.com/user-attachments/assets/5a23d714-1475-4d38-b9b6-7ae7e6cea743)

Kicad schematic: Actual Hardware

 Above demonstrates how the subsystem will work. Users first decide which circuit they will experiment with, then users will be able to plug in the various reccommended resistors to the input breadboard system to hear changes in the circuits output volume. During the experiment users will be able to mathmatically find the circuits gain and will be able to determine the sound level before hearing the output. 
 
# Analysis

There are two main parts the user will interpret in this subsystem: a non-inverting circuit to represent amplification and an inverting circuit to represent noise cancelation. Limited to the resistors being used in the breadboard subsystem, I determined the reference resistor is 470 Ω and the user will be able to experiement with 470 Ω, 1 kΩ, and 470 and 1000 Ω in parallel (320 Ω). These values will give a realistic gain that is rated for the speaker, do not cause distortion, and will be coded with volume level intensity to simulate noise amplification or noise cancelation. In doing this, users will be able to calculate the gain for each experiement and have an accurate approximation of the volume level. If the user decides to use different resistors outside of the reccomended values, an error will show saying the circuit built distorts the speaker's output. 

To accurately relay volume control for each experiment the reference resistor is set to 470 Ω which will be used in all calculations for the gain. The max volume is set with the feedback resistor of 1 kΩ because that will give the largest increase in gain. Using the equation to find the decibal level from the gain, 20log(Av), I am able to accurately simulate the volume level for each circumstance. Knowing an increase of 3 dB gives the impression of "doubling the sound level" I was able to back track from the max volume down to find the volume level that closely fits the remaining resistors. 


## Noise Amplification Portion

 To find the gain for a non-inverting circuit users will use the equation 1 + Rf/R1 [5]. 

| Resistance | Gain | Volume Control |
|-----------|-------|----------------|
| 320 ohms | 1 + 320/470 = 1.68| 50% |
| 470 ohms | 1 + 470/470 = 2| 60% |
| 1k ohms | 1 + 1000/470 = 3.13| 100% |



### Noise Cancelation Portion
The inverting circuit shown below is a representation of the circuit used to cancel the original output signal. To cancel a sine wave there needs to be an inverted signal (180-degree phase shift) at the same frequency. R1 of this circuit will be 470 Ω and the feedback resistor is what the user choses. The recommened values for Rf will be 470 Ω, 1 kΩ, and 2 kΩ. Users will use the equation -Rf/R1 [5].

| Resistance | Gain | Volume Control |
|------------|------|----------------|
| 320 ohms | - 320/470 = -1| 40% |
| 470 ohms | - 470/470 = -2.12| 30% |
| 1k ohms | - 1000/470 = -4.25 | 10% |

## Housing

## Coding portion
For this subsytem to work, code will be implemented to simulate the gain of the circuit in use. WIth the arduino there is a function named "volume.setvolume()". For example to get half the volume control the line of code is volume.setvolume(0.5). For max volume it would write volume.setvolume(1.0). With this it is simple to simulate volume control for each feedback resistor and circuit. 

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

