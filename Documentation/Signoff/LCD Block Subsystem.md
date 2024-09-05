# LCD Block Subsystem

## Subsystem Function:

The purpose of this subsystem is to help ease the user's understanding of the kit's functionalities, provide a digital user manual, provide the users with instructions or guided learning via challenges and lessons and enable a digital interaction with the car. Hence, this LCD Block Subsystem serves as one of the primary interaction points between the user and the device. 

## Constraints/Specifications:

| Description       | Constraints/Specification:                                                                           | Source                         |
|-------------------|------------------------------------------------------------------------------------------------------|--------------------------------|
| Visibility        | The LCD must provide clear visibility indoors and outdoors with a brightness level of at least 350 nits.                   |  Interaction Design principles [3]             |
| User Interface    | The menu should allow easy navigation at any point with buttons such as "Return to Menu" or "Next" or "Back".    | User interface design [4]       |
| Interactivity     | The system must register input from the keypad within 300ms to ensure responsive interaction.        | Performance Requirement [6]        |
| Environmental and social responsibility      |  The system must contain, on average, a minimum of 2% of any combination of postconsumer recycled plastic, ITE-derived post-consumer recycled plastic, or bio-based plastic, measured as a percentage of the total amount of plastic (by weight) in the product. | IEEE Standard [5] |

## Schematic:

<p align="center">
  <img height="500" src="https://github.com/user-attachments/assets/c0f25b5e-4768-4269-bc80-2b662ee9ff2b">
</p>

## PCB

<h4 align="center"> Detached TFT Touch Screen PCB: </h4>
<p align="center">
  <img src="https://github.com/user-attachments/assets/4d0e4fa3-629b-47f3-a7d5-7ee838f0ec79" height="250" /> <img src="https://github.com/user-attachments/assets/6ee923e9-a58c-4bb3-9260-fdcdef5994c2" height="250" />  
</p>

<h4 align="center"> Temporary Arduino Mega connection, Ultrasonic Module and A/C unit PCB </h4>
<p align="center">
  <img src="https://github.com/user-attachments/assets/4f981a9f-bd85-4858-a974-a7ee6826db9f" height="300" />  <img src="https://github.com/user-attachments/assets/5397b58f-9536-4f3e-81bf-abd5b8746f1b" height="300" />  
</p>

## Analysis:

Above is the wiring schematic diagram of the LCD, MCU and other aspects of the device. The corresponding connections from each apparatus are illustrated as well. The pin layouts are shown depending on the power supply channel of the vehicle provided by the Power Subsystem. The schematic diagram includes the connection points with which the user can interact, like the headlights, the AC/fan and the distance sensor. For example, for the main menu using the TFT Touch Display, the schema below shows how the ground pin, the digital pins 8-13, and pin 14 are used in order to create a connection with the Arduino Mega board. Because the TFT Screen already uses the 5V pins, the device will use pin 13 as VCC by setting it too high in the setup part of the code.

Described below is a more intuitive description of what the LDC is supposed to do/display. 
The display screens that shall be generated via the TFT LCD are as follows:

<h4 align="center"> Main Menu and User Manual: </h4>
This shall be the display for the main menu. It will contain 3 digital buttons, the “User Manual” which leads to a set of instructions on how to use the device, the “Challenges” section which provides actual tasks for the user to try, and the “Interact with car” section in which users can play with actual output on the car. The presentation format will be just like a slide show. All the user will do is click on the button “Next” for the next slide until the last slide, where they will have to click on the button “Return to Menu” which will send them back to the main menu.

<p align="right">
  <img src="https://github.com/abdoulm366/TTU-Capstone--Electrical-Class-Kit/assets/125443044/aace3b95-d6e0-49a4-8a69-43f5fd51c149" height="300" />  <img src="https://github.com/abdoulm366/TTU-Capstone--Electrical-Class-Kit/assets/125443044/d4384530-70ba-477c-89b3-c14eaab3a6b3" height="300" />  <img src="https://github.com/abdoulm366/TTU-Capstone--Electrical-Class-Kit/assets/125443044/0a1f932c-574e-4c36-93e4-4590253c9e5f" height="300" />
</p>

<h4 align="center"> Challenges: </h4>
This section will be coded to interact with the other subsystems like the input breadboard subsystem, the Logic Gates Subsystem, the Vehicle Lights and others. These challenges will create an aspect of the guided learning experience for the user. It shall introduce a problem or challenge to the user, provide hints, and after the user successfully completes the challenge it shall provide a checkmark and explain the concept learned by the user. For example, let's consider a challenge such as “Have you tried driving the car in reverse?”. After the user clicks on this challenge, they will be referred to the Logic Gates Subsystem and would be provided 3 hints about different logic gates like AND, OR, and NOT. After the user successfully changes the direction of the wheels, they would receive a checkmark and be provided with an explanation of the concept learned using logic gates.

<p align="center">
  <img src="https://github.com/abdoulm366/TTU-Capstone--Electrical-Class-Kit/assets/125443044/8245bbfa-30cd-4bad-ba81-8be7aa4a7350" height="300" />  <img src="https://github.com/abdoulm366/TTU-Capstone--Electrical-Class-Kit/assets/125443044/716e4cc0-d68b-436b-8648-b1d8196a5772" height="300" />  <img src="https://github.com/abdoulm366/TTU-Capstone--Electrical-Class-Kit/assets/125443044/48ffc31f-f1dd-4918-9817-9d066de188aa" height="300" />
</p>

 <h4 align="center"> Interact with car: </h4>
This submenu “Interact with the car” will have 4 parts, the car’s proximity sensor which will display the closest object to the car, the car’s headlight control which will be able to change the car’s headlight color, the Birduino game which is an encoded game for the TFT LCD Touch Screen, the Fan ON/OFF which will turn on and off the car’s fan.

<p align="center">
  <img src="https://github.com/abdoulm366/TTU-Capstone--Electrical-Class-Kit/assets/125443044/a0fd1e55-b5d7-4bca-be09-41c6a98e0542" height="300" />  <img src="https://github.com/abdoulm366/TTU-Capstone--Electrical-Class-Kit/assets/125443044/9341daf4-6e7f-4299-8d2d-67c7e083972a" height="300" />  <img src="https://github.com/abdoulm366/TTU-Capstone--Electrical-Class-Kit/assets/125443044/4d54b888-ebdf-4eae-965e-a7d0b8475299" height="300" />
</p>

The first example is distance measuring with ultrasonic sensors. The sensor's output, or distance, is printed on the screen and will allow the user to pick the units, centimeters or inches, with the touch screen.

The car’s headlight control shall be done by controlling an RGB LED with
three RGB sliders that will change its color. For example, if we
begin to slide the blue slider, the LED will light up in blue and
increase the brightness as we approach the maximum setting. So the
sliders may range from 0 to 255, and we can use their combination to set
any color to the RGB LED.

The Birduino game is a copy of a mobile game called Flappy Bird. It
shall be played using the push button or directly on the touch screen.

<p align="center">
  <img src="https://github.com/abdoulm366/TTU-Capstone--Electrical-Class-Kit/assets/125443044/747f0542-4bd5-4fb9-9e47-66f278e23ccb" height="300" />  <img src="https://github.com/abdoulm366/TTU-Capstone--Electrical-Class-Kit/assets/125443044/4d75f17c-c9ea-4969-92aa-f96c67de9c3b" height="300" />
</p>

The fan represents the A/C unit of the car. It shall be turned on using by pressing on the “Turn On Fan” button and turned off by pressing the “Turn Off Fan” button.

This system demonstrates the fundamental concepts of digital electronics but also offers a more interactive digital framework for the user to experiment with. It uses sensors, actuators, and graphical interfaces to provide users with a better understanding of the concepts of ECE. The LCD subsystem's overall performance includes assessing the correctness of users' input or interactions with the system. In order to make sure that the designed specifications for a better user experience are met, a response time to user inputs will be evaluated. A deeper analysis shall be conducted to align with the task's performance goals. In addition, user interface (UI) effects shall be analyzed to confirm easy navigation and ease of use. Most of the analysis shall be conducted via a test run coding format.

The LCD Block Subsystem is integrated by pairing a 3.2" TFT touchscreen with a TFT LCD Arduino Mega Shield. A shield is needed since the TFT Touch screen operates at 3.3V while the Arduino Mega outputs at 5V. An HC-SR04 ultrasonic sensor is required for the distance sensor. The headlights' functionalities and details are incorporated into the Headlight Subsystem. A push button is needed to turn ON and Off the screen. Also, 2 Fans are needed for the A/C unit.

Most of the testing shall be done within the code section and the hardware using LT-spice or other circuit assimilators. This includes unit tests for individual components, integration tests with the MCU and keypad, and system-level user acceptance tests to validate functionality, user interface design, and interactivity as per the defined requirements.

## B.O.M.

| **Component Type:**                                         | **Quantity:** | **Link**      | **Price:** | **Part Number:** | **Manufacturer:** |
|-------------------------------------------------------------|---------------|---------------|------------|------------|------------|
| 3.2″ TFT Touch Display                                      | 1             | Amazon.com    | $ 21.98    |   ASIN:	B086ZK6VG5 | DIYmalls |
| TFT Display Mega Shield                                     | 1             | Amazon.com    | $ 7.82     | ASIN	‎B075H25WZT | Walfront |
| Ultrasonic Module HC-SR04                                   | 1             | Amazon.com    | $ 1.99    | ASIN ‏ : ‎ B07KNTQ4C2| Reland Sung |
| RC Motor Cooling Fan                                        | 2             | Amazon.com    | $ 8.98     | ASIN ‏ : ‎ B08F9VZ2X3 | ShareGoo |
| Push On button pack                                         | 3             | digikey.com   | $ 0.3    | TS02-66-60-BK-260-LCR-D | CUI Devices |
|                                                             |               |               |            | Total:        | $41.07    |

## References:

\[1\] "Best Practices in LCD Interface Design", LCD Manufacturer
Guidelines,
\[https://visualhierarchy.co/user-interface-design-best-practices\]

\[2\] "Arduino TFT LCD Touch Screen Tutorial", HowToMechatronics,
available at:
\[https://howtomechatronics.com/tutorials/arduino/arduino-tft-lcd-touch-screen-tutorial/#google_vignette\](https://howtomechatronics.com/tutorials/arduino/arduino-tft-lcd-touch-screen-tutorial/#google_vignette).

[3] Philips, M. (2017, June 1). Boost your UX with these successful Interaction Design principles: Toptal®. Toptal Design Blog. https://www.toptal.com/designers/interactive/interaction-design-principles#:~:text=Constraints%20in%20design%20make%20sure,and%20consequently%20influence%20the%20user. 

[4] Nielsen, J. (2024, February 20). 10 usability heuristics for user interface design. Nielsen Norman Group. https://www.nngroup.com/articles/ten-usability-heuristics/ 

[5] IEEE SA - IEEE Standard for Environmental and Social Responsibility Assessment of computers and displays. IEEE Standards Association. (n.d.). https://standards.ieee.org/standard/1680_1-2018.html 

[6] Proculus Technologies Co., Ltd. (2024, January 4). How to improve performance of LCD displays. https://www.proculustech.com/how-to-improve-performance-of-lcd-displays.html 
