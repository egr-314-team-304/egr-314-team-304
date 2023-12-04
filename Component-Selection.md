# Component Selection
--------------
## Table of Contents
- [Voltage Regulator](#voltage-regulator)
- [UV Light Sensor](#uv-light-sensor)
- [Humidity Sensor](#humidity-sensor)
- [Motor Driver](#motor-driver)
- [Temperature Sensor](#temperature-sensor)
- [Motor](#motor)
- [OpAmp](#opamp)
- [Home Page](index.md)
--------------
## Voltage Regulator

| Voltage Regulator | Pros          | Cons          |
| -------- | ------------- | ------------- |
| ![](Images/VR2.png) | - Higher voltage ceiling that can be stepped down.     | - Fixed output voltage which does not allow flexibility later on.     |
| TLS4120D0EPV33XUMA1 - Switching Regulator IC 3.3V 2A $4.95/ea | - Good switching frequency range using both Khz and Mhz ranges. Better on/off control.    | - Very large; utilizes more space and pads.    |
| [Link](https://www.digikey.com/en/products/detail/infineon-technologies/TLS4120D0EPV33XUMA1/12756107) |       |        |

--------------

Rationale: The second option provides a higher ceiling on the input voltage we can deliver if needed. While the fixed output voltage is not ideal, our current aim of 3.3V should be good to carry through the rest of the project for power needs. This also takes into account the max output current being the highest of the three at 2A. The cost is around the median for 3.3V regulators. The third option is great, but the cost just seems far too high with a low maximum current.

--------------
## UV Light Sensor

| UV Light Sensor | Pros          | Cons          |
| -------- | ------------- | ------------- |
| ![](Images/LS3.png) | - Has multifunctionlity adn is programmable for easier use     | - Higher cost than our usual light sensor     |
| SI1146-M01-GMR $4.43 | - Low power necessities     | - Has a limited range     |
| [Link](https://www.digikey.com/en/products/detail/silicon-labs/SI1146-M01-GMR/5271747) | - Works with our programs we want to use for our system     | - Needs calibration in orde to operate correctly     |

--------------

Rationale: Initially option one seemed the best of the three. Featuring specifically UV light sensitivity, which is exactly what we need, as wella s a low unit price it seemed like a clear winner. Unfortunately (or rather fortunately) we noticed it needed to be bought at large bulk, putting it out of our price range despite its ideal specifications. The third choice, while having the highest unit price and being primarily an IR proximity sensor, it also features a UV index sensor that would work well with our project. Additionally, it is much easier to use and readily accessible for outdoor use than option 2 which optimized for indoor use by default. 

-----------------
## Humidity Sensor

| Humidity Sensor | Pros          | Cons          |
| -------- | ------------- | ------------- |
| ![](Images/HS3.png) | - Simple to understand     | - A 2mmx2mm dimension makes it harder for us to install and make sure it works properly     |
| 1649-SHT45-AD1B-R2TR-ND $7.18 | - Only one output pin     | - More expensive. Considering we will need to by multiple in case some get lost or damaged due to their small size     |
| [Link](https://www.digikey.com/en/products/detail/sensirion-ag/SHT45-AD1B-R2/16360966) | - Given PCB build     | - Has a limited range     |

--------------

Rationale: The humanity sensor "SHT45-AD1B-R2" has a high resolution of 0.01% RH and 0.01°C, and a low power consumption of 0.4 µW at 1 measurement per second. It also has a fast response time of less than 1 second, and a long-term stability of less than 0.25% RH per year. Compared to other sensors of the same size, the "SHT45-AD1B-R2" offers better performance, reliability, and flexibility for different use cases.

----------------------
## Motor Driver

| Motor Driver | Pros          | Cons          |
| -------- | ------------- | ------------- |
| ![](Images/MD1.png) | - Logic inputs 3.3 V and 5.0 V TTL/CMOS-compatible  | - Complicated to use |
| IFX9201SGAUMA1 $3.79 | - Chopper current limitation  |  |
|  | - Short circuit shut down with latch behavior  |  |
|  | - Over Temperature shut down with latch behavior  |  |
|  | - VS undervoltage shutdown  |  |
| [Link](https://www.digikey.com/en/products/detail/infineon-technologies/IFX9201SGAUMA1/5415542) | - Open load detection in ON and OFF state |  |

--------------

Rationale: IFX9201SGAUMA1 features some useful safety and utility specifications while still being at a very competitive price. Features such as the short circuit shutdown, allowing for more electrical safety for the device, high reliability, and low standby current for power conservation can be very useful. Additionally the product uses SPI communication to meet the requirements of the project.

--------------------
## Temperature Sensor

| Temperature Sensor | Pros          | Cons          |
| -------- | ------------- | ------------- |
| ![](Images/TS3.png) | - Utilizes only 3 pads to conserve PCB space | - Analog only. Useful for this project, but lesser product overall if more data is needed or ADC is not used |
| MCP9700T-E/TT $0.30 | - Very cheap sensor | - Accuracy is not great at +/-2°C |
| [Link](https://www.digikey.com/en/products/detail/microchip-technology/MCP9700T-E-TT/1212510) |  |  |

--------------

Rationale: The temperature sensor MCP9700T-E/TT can measure temperature from -40°C to +125°C with an accuracy of ±4°C. It has a low operating current of 6µA and a low supply voltage of 2.3V to 5.5V which is perfect for our project. The output voltage of the sensor is directly proportional to the measured temperature, with a slope of 10mV/°C and an offset of 500mV. This makes it easy to interface with analog-to-digital converters or microcontrollers. 

--------------
## Motor

| Motor | Pros          | Cons          |
| -------- | ------------- | ------------- |
| ![](Images/M2.png) | - Easy to work with/easy communication | - Couldn't find on DigiKey |
| SKU:FIT048 7.99$ | - Part half of a team is working with in 455 |  |
| [Link](https://www.amazon.com/150RPM-Reduction-Gearbox-GA12-N20-Models/dp/B0BFQXFNTK/ref=asc_df_B0BFQXFNTK?tag=bingshoppinga-20&linkCode=df0&hvadid=80333201323909&hvnetw=o&hvqmt=e&hvbmt=be&hvdev=c&hvlocint=&hvlocphy=&hvtargid=pla-4583932720567818&th=1) |  |  |

--------------

Rationale: This motor is most ideal for our project because it has a full metal gearbox that provides high torque and durability. It also has a low noise level and a long service life which is needed for being close to ears. The 3mm shaft is great and also its ability to move smoothly and accurately.

--------------
## OpAmp

| OpAmp | Pros          | Cons          |
| -------- | ------------- | ------------- |
| ![](Images/OA1.png) | - Inexpensive and simple use | - High current output |
| LM324DR $0.37 | - Supply voltage 1.5V to 16V |  |
| [Link](https://www.digikey.com/en/products/detail/texas-instruments/LM324DR/555719) |  |  |

-------------

Rationale: The LM324DR has a very competitive price along with simple usage that will allow us to build the project quickly and efficiently. The simple design of the product also allows for easy testing and debugging in the design as well. Finally, the LM324DR has the ability to amplify up to 4 different signals, allowing us to reduce the amounts of components needed to amplify all of our light sensor signal outputs.

[Return to the top](#table-of-contents)
