# Noise Cancelation and Amplification Subsystem
The purpose of this subsystem is to familiarize students with the application of op amps. Students can build an inverting or non-inverting amplifier circuit with the LM741 chip depending on if they want the output to cancel or amplify the original signal.
## Constraints
| No. | Constraints | Origiin |
|-----|-------------|---------|
|1.   | must have input voltage of max 5.5 V | System Constraint|
| 2. | Bias current must be lower than 0.5 mA | System constraint|
|3. | Speakers shall output between 20 Hz and 20 kHz | Listening range for humans |

1.	The subsystem is going to be powered by the Arduino, and the maximum voltage the Arduino will output is 5.5 V.  

2.	For this kit to follow safety requirements, any circuit that the students build shall not be over 0.5 mA.


3.	Students shall be able to hear the speakers output because it is crucial for the purpose of the subsystem. 

# Buildable schematic
Noise Amplification Schematic
![image](https://github.com/abdoulm366/TTU-Capstone--Electrical-Class-Kit/assets/158213085/95166732-45a1-4eb1-afa2-22ed71d043ae)
Kicad schematic:  Figure 1 

Students will build the non-inverting operational amplifier circuit then hear the output difference between the signals easily via a push button connected to speaker 2. Figure 1 shows the Arduino powering the circuit, the first speaker playing the 1 kHz sine wave via an input pin from the Arduino, and the second speaker playing the signal after traveling through the non-inverting amplifier.

Noise Cancelation Schematic
![image](https://github.com/abdoulm366/TTU-Capstone--Electrical-Class-Kit/assets/158213085/e898a0b1-e7b7-4364-b6e1-2eb49b439ed6)
Kicad schematic:  Figure 2

Students will build an inverting operational amplifier circuit with the output playing through speaker two. 

# Analysis
Non-Inverting Circuit 
![image](https://github.com/abdoulm366/TTU-Capstone--Electrical-Class-Kit/assets/158213085/194ff1d5-a952-4309-af51-a0ffe399b073)
LT spice simulation:  Figure 3 

The non-inverting circuit students will build consists of components R1 = 20 KΩ and R2 = 20 KΩ, and the gain equates to Av = 1 + R2/R1 [4]. These value resistors will result in a gain of two for the amplification portion of the subsystem. With these chosen resistors there should never be a current greater than 0.25 mA, which follows constraint 2. 

Results of non-inverting amplifier
![image](https://github.com/abdoulm366/TTU-Capstone--Electrical-Class-Kit/assets/158213085/60b31682-d95b-410d-a7ae-58c25b92d611)
LT spice simulation:  Figure 4 

Figure 4 shows the input and output results of the circuit built in figure 3. The green wave represents a 1 kHz sine wave with an amplitude of 2, and the blue wave is the output signal of the non-inverting circuit. We can clearly see a gain of two between the blue and green signal. 

Inverting Circuit
![image](https://github.com/abdoulm366/TTU-Capstone--Electrical-Class-Kit/assets/158213085/8486bd58-3b49-4bdb-9575-2cbb0f5e6dbf)
LT spice simulation:  Figure 5 

Figure 5 is the circuit for the inverting amplifier circuit. The inverting circuit’s gain is found from the equation Av = -R2/R1, where in this case the gain is equal to -2 [4]. The negative signifies an inversion of the signal, a 180  ̊phase shift. 

Results of inverting amplifier 
![image](https://github.com/abdoulm366/TTU-Capstone--Electrical-Class-Kit/assets/158213085/70742cd2-1041-4fff-9dae-203ee6756978)
LT spice simulation:  Figure 6 

In the results from figure 6, the green wave represents the input signal of a 1 kHz sine wave with amplitude of 2, and the blue wave represents Vo from the circuit. From the graph, the blue wave is seen as the inverse of the input sine wave because of the inverting circuit. When these two signals are played simultaneously, students will hear speaker 1 become significantly weaker. This is because speaker 2 is outputting that signals inverse at a higher gain. 

# BOM
| Device | Price | Quanity | Total Cost |
|--------|-------|---------|------------|
| push button | $1.95 | 1 | $1.95 |
| LM741 op amp | $0.87 | 1 | $ 0.87 |
| Mini Speaker | $3.15 | 2 | $6.30 |
| 20 kΩ resistors | $0.10 | 10 | $1.00 |
| 40 kΩ resistors | $1.87 | 5 | $9.35 |
Total coast for subsystem: $19.47 ( not including tax or shipping)

# References 
[1] “CMS-28528N-L152 CUI Devices | Audio Products | DigiKey.” Digikey.Com, www.digikey.com/en/products/detail/cui-devices/CMS-28528N-L152/6137734. Accessed 9 Apr. 2024. 

[2] Industries, Adafruit. “On-off Power Button / Pushbutton Toggle Switch.” Adafruit Industries Blog RSS, www.adafruit.com/product/1683. Accessed 9 Apr. 2024. 

[3] “LM741 Operational Amplifier.” MIT.Edu, 2000, www.mit.edu/~6.301/LM741.pdf. 

[4] Storr, Wayne. “Inverting Operational Amplifier - the Inverting Op-Amp.” Basic Electronics Tutorials, 4 Aug. 2022, www.electronics-tutorials.ws/opamp/opamp_2.html. 
