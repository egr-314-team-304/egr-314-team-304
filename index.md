# Cool Hat Project

## Team 304

## Team Members
- **Kezmen Lozevski**
- **Tim Drafz**
- **Jose Aguilar**
- **Ivan Makarenko**
- **Roshan Patel**

## Preparation Date: 12/3/2023

## ASU, EGR 314, Kevin Nichols
## Table of Contents
- [Introduction](#)
- [Mission Statement](#Mission-Statement)
- [Humidity Sensor](#humidity-sensor)
- [Motor Driver](#motor-driver)
- [Temperature Sensor](#temperature-sensor)
- [Motor](#motor)
- [OpAmp](#opamp)
- [Home Page](index.md)
## Mission Statement
When starting this project, our team came up with a simple and concise mission statement.

__Our goal is to create a device that utalizes multiple unique sensors to take input from its environment 
to perform a meaningful or beneficial task.__


---
## Team Charter
Our group set out to consider what benefits we hoped to find through the creation of a succesful project.  we thought of how a succesful design and implementation could benefit us personally, more then just the scope of the class. This would be the foundation of our team charter, a set of common goals for our team to allign with and strive for. 
- Gain more insight into creating electronic systems utilizing industry-level software such as Orcad Cadence, and MPlab.
- Gaining more experience in the design and construction of different serial sensing and actuation circuits.
- Demonstrating a neat project to friends and family.
- Expanding our project resume with an interesting design that conveys what we learned throughout the course.
- Gaining more confidence and familiarity with electrical systems, in general, to give us a higher repertoire of skills when handling future electrical system tasks.

---



## [Team Organization](team-organization.md)
Team communication and synergy, as well as a consistant working schedual are vital components to creating a succesful project. To ensure we could acheive these provisions we set out to find what times we could all meet up to schedual meetings, and established our main modes of team communication. 

---

## [User Needs and Benchmarking](user-needs-benchmarking.md)
After our design ideation and choosing an idea concept we were happy with, we set out to benchmark similar ideas that were out in the market, as well as to observe the complaints and positive feedback these ideas received. This was useful, as it gave us insight into what worked well and was well received, as well as giving us foresight on what could go wrong with our design and mistakes to avoid in our product design.

---

## [Design Ideations](design-ideation.md)
After our insightful brainstorming session, our team embarked on a journey to amalgamate our collective ideas and channel them into innovative project concepts. We meticulously synthesized the various suggestions and insights from the brainstorming, resulting in the formulation of three distinct and cohesive product designs. Each design reflects our team's commitment to innovation and our aim to meet the envisioned objectives.

----

## [PIC Code](pic.md)
A link to the final MPLAB X code created for the project. Includes images from MPLAB X MCC Harmony.

----

## [ESP32 Code](esp32.md)

-------------

## [Design Selection](Design-Selection.md)
Our team is designing a smart hat with temperature and light sensors to monitor its internal environment. If the temperature goes beyond a set limit, an integrated fan turns on for cooling. The hat's brim also rotates to shield the wearer from direct sunlight, regardless of the sun's position. This tech-infused hat ensures optimal comfort and adaptability for outdoor activities.

----

## [Block Diagram](Block-Diagram.md)

The block diagram explains how the PCB will function with all the components at a hardware scale. The diagram explains that the board will be supplied with 12V, but the regulator reduces it to 3.3V for operation. The light, temperature, and humidity sensors will communicate through I2C (two components will be using the same I2C pin for communication without interference), while the motor driver runs on SPI. The user can see the data through an OLED Display and through a device via WiFi on the ESP32 module. 

![Image](Images/BlockDiagram.png)

---

## [Component Selection](Component-Selection.md)

Once we had a good idea of what we had in mind for our project design, we set out to choose the components that would allow us to build our vision. To do so, we listed out the major components that would be needed including the voltage regulator, UV light sensor, humidity sensor, motor driver, temperature sensor, and the motor. To better ensure we had a good selection of each component, we set out to find at least three candidates for each component. This would allow us to compare different choices and component properties to find what best fits our needs, rather than choosing a component and trying to fit our project around it. 

---

## [Power Budget](Power-Budget.md)

The power budget is an important detail in the design process. It is designed to help calculate the needed voltages and current to keep all components running with the risk of shorting anything from over-voltage or current. In this case, the three sensors being used in our PCB will use 3.3V from a 12V power source. It mentions our use of the regulator that will allow for the safe operation of the peripherals. The motor Driver will use a higher voltage which will be considered when designing the final PCB.

---

## [Microcontroller Selection](Microcontroller-Selection.md)
Similarly to the component selection, our team set out to find multiple microcontroller candidates. This would promote flexibility and consideration in our design. By comparing and contrasting each microcontroller's attributes, we could better identify which microcontroller best fits the needs and specifications of our project design.


![Image](Images/PIC32MX.PNG)
 
After considering our choices, we went for the PIC32MX250F128B. 

---

## [Hardware Proposal](Hardware-Proposal.md)
Once our components and microcontrollers had been selected, we needed to put them all together. First, each team member created a design for an individual subsystem. These subsystems consisted of the motor controller, the power regulator, and the light, temperature, and humidity sensors. From there, all the subsystems needed to be put together into a single schematic. Some of the issues that arose were figuring out how to connect all the components to the single microcontroller. One solution to use fewer pins was to connect the light sensor and temperature sensor to the same I2C pins and use different addresses as a way to separate their communications. Finishing the hardware proposal was an important milestone in creating our final product, as it creates the blueprint for the physical PCB and component connections. 

---

## [Software Proposal](Software-Proposal.md)
Once we have decided all of the physical components of our design and have a good idea of how they fit together, we were ready to start thinking of how they work together. While we still didn't have physical hardware to code yet, a software proposal is useful for envisioning how all the components being designed would work together logically. Additionally, a good software proposal is a good foundation for the code when it is time to start developing it. 

---

## Lessons Learned
One of the biggest lessons learned was to give more investigation into the microcontroller selection. While the PIC32 that we chose had many advantages for use in what we wanted to do, it had the downside of using MPLAB Harmony only. This added additional learning, and the code used in MCC on other PICs did not actually work for this. Along with this the PIC32 we had was internally shorted on the Vdd pin to Vss. We should have had each member order samples from Microchip, but only had one. When this one failed we only had a DIP version to fall back on. To add onto the need to investigate more, it would have been better to go with a PIC that had more pins. We had a couple extra, but the amount needed by the motor controller we chose ended up increasing what was used. This made the OLED pins move to the ESP32 and complicated actual pin selection for the final design as some pins could not be changed. A 40 pin PIC would have probably been ideal for ease.

For final demonstration the voltage regulator would not output any desired voltage, and the most likely culprit for this was a miscalculation for the input/output loads based on our design. Additional inductors or capacitors on the input line may have been required due to the line being split going into the regulator and the motor controller directly. To note during troubleshooting, a bypass capacitor on both the input/output were changed to 10uF to induce more and this did not resolve the issue. For this reason we felt that we may have needed to calculate using more inductors as the signal was probably too rough for the regulator to work.


## Apendix

## [Presentation 1](presentation-1.md)

## [Team Checkpoint](checkpoint-1.md)
