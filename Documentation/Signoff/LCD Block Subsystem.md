# LCD Block Subsystem

## Subsystem Function:

The LCD Block Subsystem serves as the primary connection point for
client interaction within the device. A graphical showcase interface
will be used to facilitate consistent correspondence between the client
and the framework. The subsystem includes a Fluid Gem Display (LCD) that
is constantly in communication with the Microcontroller Unit (MCU) to
display the framework's current status, menu options, and results. The
main menu displayed on the LCD provides clients with multiple options,
such as accessing a computerized Client Manual, entering codes via an
associated keypad (Subsystem 8), selecting from a rundown of client
challenges (e.g., changing the car head lights colors), and drawing in
with an implanted game like Flappy Bird, thus referred to as 'Birduino'.

Below is are the different display screens that shall be generated via
the TFT LCD.

Main Menu:

![image](https://github.com/abdoulm366/TTU-Capstone--Electrical-Class-Kit/assets/125443044/9b32419c-6592-4c8c-b5fa-9236d051d3a5)


This shall be the display for the main menu. It will contain 4 buttons,
the “User manual” which leads to a set of instruction on how to use the
device, the “Challenge” section which provide actual task for the user
to try, the “learn to code” section which teaches the user how to code
using the keypad section (*Subsystem 7*), the “Interact with car”
section in which users can play with actual output on the car.

User Manual:

![image](https://github.com/abdoulm366/TTU-Capstone--Electrical-Class-Kit/assets/125443044/d4384530-70ba-477c-89b3-c14eaab3a6b3)
![image](https://github.com/abdoulm366/TTU-Capstone--Electrical-Class-Kit/assets/125443044/0a1f932c-574e-4c36-93e4-4590253c9e5f)


The presentation format will be just like a slide show. All the user
will do is click on the button “Next” for the next slide until the last
slide, where they will have to click on the button “Return to Menu”
which will send them back to the main menu.

Challenges:

This section will be coded to interact with the other Subsystem like the
input bread board subsystem. It shall contain a list of challenges such
as “Have you tried driving the car in reverse?”, “I am trying to park,
check the distance sensors of the car so I don’t hit anything”, etc…

![image](https://github.com/abdoulm366/TTU-Capstone--Electrical-Class-Kit/assets/125443044/95e91f05-4e2f-479c-a554-b7d963759f7b)
![image](https://github.com/abdoulm366/TTU-Capstone--Electrical-Class-Kit/assets/125443044/a0e06d4c-3769-41aa-8f76-c277b16a248e)


Learn to Code:

\*Discussed in substem 7\*

Interact with car:

The submenu “Interact with the car” will have 4 parts, the car’s
proximity sensor which will display the closest object to the car, the
car’s head light control which will be able to change the car’s head
light color, the birduino game which is an incoded game for the TFT LCD
Touch Screen, the Fan ON/OFF which will turn on and off the car’s fan.

![image](https://github.com/abdoulm366/TTU-Capstone--Electrical-Class-Kit/assets/125443044/a0fd1e55-b5d7-4bca-be09-41c6a98e0542)


The first example is distance measuring with ultrasonic sensors. The
sensor's output, or distance, is printed on the screen, and will allow
the user to pick the units, centimeters or inches, with the touch
screen.

![image](https://github.com/abdoulm366/TTU-Capstone--Electrical-Class-Kit/assets/125443044/9341daf4-6e7f-4299-8d2d-67c7e083972a)


The car’s head light control shall be done controlling an RGB LED with
three RGB sliders that will change it’s the color. For example, if we
begin to slide the blue slider, the LED will light up in blue and
increase the brightness as we approach the maximum setting. So the
sliders may range from 0 to 255, and we can use their combination to set
any color to the RGB LED.

![image](https://github.com/abdoulm366/TTU-Capstone--Electrical-Class-Kit/assets/125443044/4d54b888-ebdf-4eae-965e-a7d0b8475299)


The Birduino game is a copie of a mobile game called Flappy Bird. It
shall be played using the push button or directly on the touch screen.

![image](https://github.com/abdoulm366/TTU-Capstone--Electrical-Class-Kit/assets/125443044/747f0542-4bd5-4fb9-9e47-66f278e23ccb)


The fan represents the A/C unit of the car. It shall be turned on using
by pressing on the “Turn On Fan” button and turned off by pressing the
“turn Off Fan” button.

![image](https://github.com/abdoulm366/TTU-Capstone--Electrical-Class-Kit/assets/125443044/4d75f17c-c9ea-4969-92aa-f96c67de9c3b)


## Constraints/Specifications:

| Description       | Constraints/Specification:                                                                           | Source                         |
|-------------------|------------------------------------------------------------------------------------------------------|--------------------------------|
| Visibility        | The LCD must provide clear visibility in varying light conditions.                                   | Conceptual Design              |
| User Interface    | The menu should be intuitive, allowing easy navigation for all ages.                                 | User Experience Research       |
| Interactivity     | The system must register input from the keypad within 300ms to ensure responsive interaction.        | Performance Requirement        |
| Content           | The display content must be dynamic, supporting multiple languages and symbols for a wide user base. | Internationalization Standards |
| Power Consumption | The LCD and associated subsystems should optimize for low power usage to extend operational time.    | Power Management Guidelines    |

## Schematic:

The wiring diagram of the LCD, MCU and yield of the vehicle are shown in
the schematic below. The correspondence conventions (I²C, SPI) are
illustrated. The pin tasks are shown for the dependable information
transfer and the power supply channel of the vehicle. The design of
connection points for the client cooperation is shown in the schematic,
for example, the main menu route and the submenu route. The schema below
shows how the ground pin, the digital pins 8-13, and pin 14 are used.
Because the TFT Screen already uses the 5V pins, the divice will utilize
pin 13 as VCC by setting it to high in the setup part of the code.

![image](https://github.com/abdoulm366/TTU-Capstone--Electrical-Class-Kit/assets/125443044/fb07657a-feee-411d-9a1e-5a86ea94a2bc)


## Analysis:

These techniques not only effectively demonstrates the fundamental concepts of digital electronics but also offers a sensible framework for the user to experiment with and understand the aggregate of sensors, actuators, and graphical interfaces. An assessment of the LCD subsystem's overall performance includes assessing the refresh charge and response time to user inputs, making sure they meet the designed specs for a better user experience. The analysis consists of a review of strength intake beneath various operation modes (e.g., lively, idle, sleep) to align with the task's strength performance goals. In addition, user interface (UI) effects are analyzed to confirm easy navigation and ease of use, with adjustments made based totally on user feedback. Most the analysis shall be conducted via a test run coding format.

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

