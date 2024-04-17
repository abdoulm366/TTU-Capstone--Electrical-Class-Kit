# Noise Cancelation and Amplification Subsystem

## Function of the system
The function of this subsystem is to demonstrate how to amplify or cancel an input signal. To show this, an Arduino uno will be used to input a 1 kHz sine wave and it will power the op amp circuit. The original sound will play from a speaker. A spdt (single pole double throw) switch will be used to toggle between a non-inverting amplifier circuit and an inverting amplifier circuit. After the signal goes through the desired circuit, the signal’s output will be sent to a second speaker. To be able to easily hear the difference between the sounds, a push button will be implemented to turn on/off the second speaker.  

## Constraints
| No. | Constraints | Origin |
|-----|-------------|---------|
|1.   | must have input voltage of max 5.5 V | System constraint|
|2. | Bias current must be lower than 500 mA | Safety constraint|
|3. | Speakers shall output between 20 Hz and 20 kHz | Listening range for humans |

1.	The subsystem is going to be powered by the Arduino, and the maximum voltage the Arduino will output is 5.5 V.  

2.	For this kit to follow safety requirements, any circuit shall not be over 500 mA.

3.	Students shall be able to hear the speakers output because it is crucial for the purpose of the subsystem. 

# Buildable schematic

![image](https://github.com/abdoulm366/TTU-Capstone--Electrical-Class-Kit/assets/158213085/e5c88f2e-6473-499e-a9cd-9c09a2c15362)
Kicad schematic:  Figure 1 

 In the subsystem there is an Arduino that powers the circuit with 5 V. With an input tone of 1 kHz, the speakers will always output sound in the listening range for people. The LM741 chip is used to control the tone’s output gain to the second speaker. When students use this subsystem there will be clear instructions and pictures on how to build and test the circuit. Including a summary of what each component is, picture of the circuit, picture of the output graph, and a summary on how the circuit operates. 


# Analysis

The LM741 op amp was chosen for its ability to build inverting and non-inverting circuits, the input voltage is compatible with the Arduino, its bandwidth is in the desired range, the group is familar working with the op amp, and it has built-in input and output overload protection [4]. 

The spdt on-off-on switch was chosen to toggle between the inverting and non-inverting circuit, so students will be able to easily control which circuit to use. The on-off-on function is what determined this switch over others. This is due to its ability to send a signal easily to the desired circuit and has an off function when the subsystem is not in use [1]. The speakers were chosen based on the size and the frequency range. The output voltage will be at 4 V and the maximum current is 500mA, so the total resistance turns out to be 8 Ω. The impedence of the speaker is 8 Ω so it will never be over the speakers rated impedence. 

Resistor values were chosen in the kΩ range so that constraint 2 is met accordingly. If resistor values are in the MΩ range they start to generate thermal noise and if resistors are in the Ω range the ciruit will draw more current. 

The non-inverting circuit and the inverting circuit will each be designed for a PCB board to be able to fit the subsystem in the car. The switch and push button will be labeled and placed next to the interface for simplicity. The speakers will both be placed near the back of the car because they need to be close together for the sound to be heard efficiently. 


Non-Inverting Circuit 
![image](https://github.com/abdoulm366/TTU-Capstone--Electrical-Class-Kit/assets/158213085/89489be4-bf4c-4252-a41c-27bf90fb769f)
 LT spice simulation:  Figure 2 

The non-inverting circuit consists of components R1 = 4.7 kΩ and R2 = 4.7 kΩ, and the gain equates to Av = 1 + R2/R1 [5]. These value resistors will result in a gain of two for the amplification portion of the subsystem. The graph shows the input and output results of the circuit built in figure 2. The green wave represents a 1 kHz sine wave with an amplitude of 2, and the blue wave is the output signal of the non-inverting circuit. With a gain of two, the signal will amplify the original sound. Keeping the gain around two will keep the distortion at a minimum. To do this, the components chosen will never result in an excessive gain. The manual will graphically show the difference between the input and output so students will be able see and hear the difference. 


Inverting Circuit
![image](https://github.com/abdoulm366/TTU-Capstone--Electrical-Class-Kit/assets/158213085/64b64969-e337-400e-966e-d4a0c7dd9327)
 LT spice simulation:  Figure 3 

Figure 3 is the circuit for the inverting amplifier circuit. The inverting circuit’s gain is found from the equation Av = -R2/R1, where in this case the gain is equal to -2 [5]. The negative signifies an inversion of the signal, a 180 degree phase shift. In the results from figure 3, the green wave represents the input signal of a 1 kHz sine wave with amplitude of 2, and the blue wave represents Vo from the circuit. From the graph, the blue wave is seen as the inverse of the input sine wave because of the inverting circuit. 

# BOM
| Device | Price | Quanity | Total Cost | Source |
|--------|-------|---------|------------|--------|
| push button | $1.95 | 1 | $1.95 | [3] |
| LM741 op amp | $0.87 | 2 | $ 1.74 | [4]
| Mini Speaker | $3.15 | 2 | $6.30 | [2]
| 4.7 kΩ resistors | $0.10 | 2 | $0.20 | [6] |
| 5 kΩ resistor | $0.10 | 1 | $0.10 | [6] |
| 10 kΩ resistor | $0.10 | 1 | $0.10 | [6] |
| SPDT switch | $5.15 | 1 | $5.15 | [1] |
Total cost for subsystem: $15.54 ( not including tax or shipping)

# References 

[1] Carling Technologies Toggle Switch, SPDT, 3 Connections, on/off/on, 3/4 Hp, 10A @ 250V AC, 15A @ 125V AC 2FC53-73-TABS | Zoro, www.zoro.com/carling-technologies-toggle-switch-spdt-3-connections-onoffon-34-hp-10a-250v-ac-15a-125v-ac-2fc53-73-tabs/i/G1588553/. 

[2] “CMS-28528N-L152 CUI Devices | Audio Products | DigiKey.” Digikey.Com, www.digikey.com/en/products/detail/cui-devices/CMS-28528N-L152/6137734. 

[3] Industries, Adafruit. “On-off Power Button / Pushbutton Toggle Switch.” Adafruit Industries Blog RSS, www.adafruit.com/product/1683. 

[4] “LM741 Operational Amplifier.” MIT.Edu, 2000, www.mit.edu/~6.301/LM741.pdf. 

[5] Storr, Wayne. “Inverting Operational Amplifier - the Inverting Op-Amp.” Basic Electronics Tutorials, 4 Aug. 2022, www.electronics-tutorials.ws/opamp/opamp_2.html. 

[6] Through Hole Resistors | Electronic Components Distributor DigiKey, www.digikey.com/en/products/filter/through-hole-resistors/53.
