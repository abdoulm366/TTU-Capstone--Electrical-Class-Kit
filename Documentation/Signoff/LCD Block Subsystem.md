# LCD Block Subsystem

## Subsystem Function:

The purpose of this subsystem is to help ease the user's understanding of the kit's functionalities, provide a digital user manual, provide the users with instructions or guided learnig via challenges and lessons and enable a digital interaction with the car. Hence, this LCD Block Subsystem serves as the primary interaction point between the user and the device as a whole. A graphical TFT LCD is used to facilitate this interaction. The subsystem includes a Fluid Gem Display (LCD) that is constantly in communication with the Microcontroller Unit (MCU) to display the framework's current status, menu options, and results. The main menu displayed on the LCD provides the user with multiple options, such as accessing a digital User Manual, a selection of challenges (e.g., changing the car headlights colors), and drawing in with an implanted game like Flappy Bird, thus referred to as 'Birduino'. This system will be placed on top of the car's hood for a easy access.

Described below is a more intuisive description of what the LDC is supposed to do/display. 
The display screens that shall be generated via the TFT LCD are as follows:


#### <ins>  Main Menu: </ins>

This shall be the display for the main menu. It will contain 3 buttons, the “User manual” which leads to a set of instruction on how to use the device, the “Challenge” section which provide actual task for the user to try, and the “Interact with car” section in which users can play with actual output on the car.

<p align="center">
  <img src="https://github.com/abdoulm366/TTU-Capstone--Electrical-Class-Kit/assets/125443044/aace3b95-d6e0-49a4-8a69-43f5fd51c149" height="500" />
</p>

#### <ins>  User Manual: </ins>

The presentation format will be just like a slide show. All the user will do is click on the button “Next” for the next slide until the last slide, where they will have to click on the button “Return to Menu” which will send them back to the main menu.

<p align="center">
  <img src="https://github.com/abdoulm366/TTU-Capstone--Electrical-Class-Kit/assets/125443044/d4384530-70ba-477c-89b3-c14eaab3a6b3" height="400" /> <img src="https://github.com/abdoulm366/TTU-Capstone--Electrical-Class-Kit/assets/125443044/0a1f932c-574e-4c36-93e4-4590253c9e5f" height="400" />
</p>

#### <ins>  Challenges: </ins>

This section will be coded to interact with the other Subsystem like the input bread board subsystem, the Logic Gates Subsystem, the Vehicle Lights and others. These challenges will create an aspect of the guided learning experience to the user. It shall introduce a problem or challenge to the user, provide hints, and after the user successfully completes the challenge it shall provide a check mark and explain the concept learned by the user. For example, let's concider a challenge such as “Have you tried driving the car in reverse?”. After the user clicks on this challenge, they would be refered to Logic Gates Subsystem, would be provided 3 hints about different logic gates like AND, OR, and NOT. After the user successfully changes the dirrection of the wheels, they would receive a check mark and be provided with an explaination of the concept learned using logic gates.

<p align="center">
  <img src="https://github.com/abdoulm366/TTU-Capstone--Electrical-Class-Kit/assets/125443044/8245bbfa-30cd-4bad-ba81-8be7aa4a7350" height="400" />  <img src="https://github.com/abdoulm366/TTU-Capstone--Electrical-Class-Kit/assets/125443044/716e4cc0-d68b-436b-8648-b1d8196a5772" height="400" />  <img src="https://github.com/abdoulm366/TTU-Capstone--Electrical-Class-Kit/assets/125443044/48ffc31f-f1dd-4918-9817-9d066de188aa" height="400" />
</p>

 #### <ins> Interact with car: </ins>

This submenu “Interact with the car” will have 4 parts, the car’s proximity sensor which will display the closest object to the car, the car’s head light control which will be able to change the car’s head light color, the birduino game which is an incoded game for the TFT LCD Touch Screen, the Fan ON/OFF which will turn on and off the car’s fan.

<p align="center">
  <img src="https://github.com/abdoulm366/TTU-Capstone--Electrical-Class-Kit/assets/125443044/a0fd1e55-b5d7-4bca-be09-41c6a98e0542" height="500" />
</p>

The first example is distance measuring with ultrasonic sensors. The sensor's output, or distance, is printed on the screen, and will allow the user to pick the units, centimeters or inches, with the touch screen.

<p align="center">
  <img src="https://github.com/abdoulm366/TTU-Capstone--Electrical-Class-Kit/assets/125443044/9341daf4-6e7f-4299-8d2d-67c7e083972a" height="500" />
</p>

The car’s head light control shall be done controlling an RGB LED with
three RGB sliders that will change it’s the color. For example, if we
begin to slide the blue slider, the LED will light up in blue and
increase the brightness as we approach the maximum setting. So the
sliders may range from 0 to 255, and we can use their combination to set
any color to the RGB LED.

<p align="center">
  <img src="https://github.com/abdoulm366/TTU-Capstone--Electrical-Class-Kit/assets/125443044/4d54b888-ebdf-4eae-965e-a7d0b8475299" height="500" />
</p>

The Birduino game is a copie of a mobile game called Flappy Bird. It
shall be played using the push button or directly on the touch screen.

<p align="center">
  <img src="https://github.com/abdoulm366/TTU-Capstone--Electrical-Class-Kit/assets/125443044/747f0542-4bd5-4fb9-9e47-66f278e23ccb" height="500" />
</p>

The fan represents the A/C unit of the car. It shall be turned on using
by pressing on the “Turn On Fan” button and turned off by pressing the
“turn Off Fan” button.

<p align="center">
  <img src="https://github.com/abdoulm366/TTU-Capstone--Electrical-Class-Kit/assets/125443044/4d75f17c-c9ea-4969-92aa-f96c67de9c3b" height="500" />
</p>

## Constraints/Specifications:

| Description       | Constraints/Specification:                                                                           | Source                         |
|-------------------|------------------------------------------------------------------------------------------------------|--------------------------------|
| Visibility        | The LCD must provide clear visibility in varying light conditions.                                   | Conceptual Design              |
| User Interface    | The menu should be intuitive, allowing easy navigation for all ages.                                 | User Experience Research       |
| Interactivity     | The system must register input from the keypad within 300ms to ensure responsive interaction.        | Performance Requirement        |
| Content           | The display content must be dynamic, supporting multiple languages and symbols for a wide user base. | Internationalization Standards |
| Power Consumption | The LCD and associated subsystems should optimize for low power usage to extend operational time.    | Power Management Guidelines    |

## Schematic:

Below is the wiring diagram of the LCD, MCU and other aspects of the device are shown in the schematic below. The corresponding connections from the each appratus are illustrated as well. The pin's layout are shown depending on the power supply channel of the vehicle. The design below also includes the connection points that the the user can interact with like the headlights, the AC/fan and the distance sensor. For example, for the main menu using the TFT Touch Display, the schema below shows how the ground pin, the digital pins 8-13, and pin 14 are used in orther to create a connection with Arduino Mega board. Because the TFT Screen already uses the 5V pins, the device will utilize use pin 13 as VCC by setting it to high in the setup part of the code.

<p align="center">
  <img src="https://github.com/abdoulm366/TTU-Capstone--Electrical-Class-Kit/assets/125443044/583d6fb5-7fea-4e17-8545-a710e0a78faf" height="500" />
</p>

## Analysis:

This system does not only effectively demonstrates the fundamental concepts of digital electronics but also offers a more interactive digital framework for the user to experiment with. It uses sensors, actuators, and graphical interfaces to provide users with a better understanding of concepts of ECE. The LCD subsystem's overall performance includes assessing the correctness of users input or interractions with the system. In order to make sure that the designed specifications for a better user experience are met, a response time to user inputs will be evaluated. A deeper analysis shall be conducted to align with the task's performance goals. In addition, user interface (UI) effects are shall be analyzed to confirm easy navigation and ease of use. Most the analysis shall be conducted via a test run coding format.

## Subsystem Integration:

The integrating of the LCD Block Subsystem is done by pairing a 3.2" TFT
Touch Screen with a TFT LCD Arduino Mega Shield. A shield is
needed since the TFT Touch screen operates at 3.3V while the Arduino
Mega outputs at 5V. For the distance sensor, a HC-SR04 ultrasonic sensor
is needed. While for the headlights, an RGB LED with three resistors are
required. A push button is needed for the game and 2 Fans is needed for
the A/C subsystem.

## Testing & Validation:

Most of the testing shall be done within the code section and the
hardware using LT-spice or other circuit assimilators. This includes
unit tests for individual components, integration tests with the MCU and
keypad, and system-level user acceptance tests to validate
functionality, user interface design, and interactivity as per the
defined requirements.

## B.O.M.

| **Component Type:**                                         | **Quantity:** | **Link**      | **Price:** |
|-------------------------------------------------------------|---------------|---------------|------------|
| 3.2″ TFT Touch Display                                      | 1             | Amazon.com    | $ 25.99    |
| TFT Display Mega Shield                                     | 1             | Amazon.com    | $ 7.82     |
| Arduino Mega Board                                          | 1             | Amazon.com    | $ 48.90    |
| Ultrasonic Module HC-SR04                                   | 1             | Amazon.com    | $ 11.99    |
| Multiple Colour Colorful Angel Eye Lamp RGB LED Lights 17MM | 2             | aliexpress.us | $ 14.74    |
| RC Motor Cooling Fan                                        | 2             | Amazon.com    | $ 8.98     |
| Resistors pack                                              | 1             | Amazon.com    | $ 2.80     |
| Push On button pack                                         | 1             | digikey.com   | $ 1.97     |
|                                                             |               | Total:        | $125.16    |

## References:

\[1\] "Best Practices in LCD Interface Design", LCD Manufacturer
Guidelines,
\[https://visualhierarchy.co/user-interface-design-best-practices\]

\[2\] "Arduino TFT LCD Touch Screen Tutorial", HowToMechatronics,
available at:
\[https://howtomechatronics.com/tutorials/arduino/arduino-tft-lcd-touch-screen-tutorial/#google_vignette\](https://howtomechatronics.com/tutorials/arduino/arduino-tft-lcd-touch-screen-tutorial/#google_vignette).

