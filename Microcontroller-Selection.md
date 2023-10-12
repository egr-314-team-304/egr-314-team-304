# Microcontroller Selection
-------------------------
## Design Considerations

### Team Project-Specific Requirements from Problem Definition and Block Diagram

| Criteria                                                | PIC Option 1        | PIC Option 2 | PIC Option 3 |
|---------------------------------------------------------|---------------------|--------------|--------------|
| How many GPIO Pins?                                     | 4                   | 16           | 30           |
| Built-in Analog to Digital Converter? How many?         | Yes, 1              | 13           | 16           |
| Built-in Hardware PWM? How many?                        | No                  | 5            | 5            |
| Built-in I2C? SPI? How many?                            | Yes, 2 (1 of each)  | 2/2          | 1/1          |
| Built-in UART? How many?                                | Yes, 1              | 2            | 1            |
| Other Required Built-In Features? (optional)            | -                   | -            | -            |

### Microcontroller Considerations

| Instructions                                           | PIC Option 1                                           | PIC Option 2                     | PIC Option 3                     |
|--------------------------------------------------------|-------------------------------------------------------|---------------------------------|---------------------------------|
| Part Number                                            | PIC18F26J53                                            | PIC32MX250F128B                 | PIC16F1938                       |
| Link (URL) to product page                             | [Link](https://www.microchip.com/en-us/product/PIC18F26J53#document-table) | [Link](https://www.microchip.com/en-us/product/pic32mx250f128b) | [Link](https://www.microchip.com/en-us/product/PIC16F1938) |
| Links (URL) to Data Sheets | [Link](https://ww1.microchip.com/downloads/aemDocuments/documents/OTH/ProductDocuments/DataSheets/30009964C.pdf) | [Link](https://ww1.microchip.com/downloads/en/DeviceDoc/PIC32MX1XX2XX%20283644-PIN_Datasheet_DS60001168L.pdf) | [Link](https://ww1.microchip.com/downloads/aemDocuments/documents/OTH/ProductDocuments/DataSheets/40001574D.pdf) |
| Links (URL) to Application Notes | [Link 1](https://www.microchip.com/en-us/application-notes/tb054), [Link 2](https://www.microchip.com/en-us/application-notes/tb055), [Link 3](https://www.microchip.com/en-us/application-notes/tb056), [Link 4](https://www.microchip.com/en-us/application-notes/tb057) | [Link 1](https://www.microchip.com/en-us/application-notes/an1044), [Link 2](https://www.microchip.com/en-us/software-library/pic32-peripheral-library) | [Link 1](https://www.microchip.com/en-us/application-notes/an1267.html), [Link 2](https://www.microchip.com/en-us/application-notes/an1302.html), [Link 3](https://ww1.microchip.com/downloads/en/Appnotes/01303A.), [Link 4](https://www.microchip.com/en-us/application-notes/an1333.html) |
| Links (URL) to Code Examples                           | [Link](https://ww1.microchip.com/downloads/aemDocuments/documents/OTH/ProductDocuments/CodeExamples/usbcombo.zip) | None                            | None                            |
| Links (URL) to External Resources                      | None                                                   | None                            | None                            |
| Production Unit Cost                                   | $4.78                                                  | $5.17                           | $2.76                           |
| Supply Voltage Range                                   | 2.0V - 3.6V                                            | 2.3V - 3.6V                     | 1.8V - 5.5V                     |
| Absolute Maximum Current for entire IC                 | 200mA                                                  | 200mA                           | 255mA                           |
| Maximum GPIO Pin Current (Source/Sink)                 | 25mA                                                   | 15mA                            | 25mA                            |
| 8-bit or 16-bit Architecture                            | 8-bit                                                  | 32-bit                          | 8-bit                           |
| Available IC Packages / Footprints                     | SPDIP, QFN, SSOP, SOIC                                 | TQFP, PDIP, SOIC                | SSOP, QFN, SPDIP, SOIC          |
| Supports External Interrupts?                          | Yes                                                    | Yes                             | Yes                             |
| In-System Programming Capability and Type              | ICSP                                                   | ICSP                            | ICSP                            |
| Programming Hardware, Cost, and URL | MPLAB PM3 - $1,361.13 - [Link](https://www.microchip.com/en-us/development-tool/DV007004) | MPLab - $20 - [Link](https://www.microchip.com/en-us/development-tool/PG164100) | MPLab - $20 - [Link](https://www.microchip.com/en-us/development-tool/PG164100) |
| Works with MPLAB® X Integrated Development Environment (IDE)? | Yes                     | Yes                             | Yes                             |
| Works with Microchip Code Configurator?                | Yes                                                      | Yes                             | Yes                             |

## Overall Pros and Cons

### Overall Pros
**PIC Option 1:** 
- Low power modes: Able to go to sleep when processing is not required.
- Built-in debugger: Helpful for debugging the circuit once soldered.

**PIC Option 2:** 
- Versatile: Supports various peripherals and applications.
- User-Friendly: Compatible with MPLAB tools for easy development.

**PIC Option 3:** 
- Lowest price choice
- Low power modes 
- Widest voltage range choice of the three

### Overall Cons
**PIC Option 1:** 
- Exact I2C/SPI: If changes are made and another is needed it does not support.
- Limited voltage range: If the circuit needs to change to use more voltage this may not work.

**PIC Option 2:** 
- Power-Hungry: Higher power consumption than 8/16-bit MCUs.
- Costly: More expensive than simpler MCUs.

**PIC Option 3:** 
- Only one I2C and SPI pins, they may be the same pins also so it may not be possible to have both
- No code examples

### Ranking
**PIC Option 1:** 2 PIC32MX250F128B  
**PIC Option 2:** 1 PIC18F26J53  
**PIC Option 3:** 3 PIC16F1938

## Final Microcontroller Choice: PIC32MX250F128B

Rationale: The choice was mostly between the first and second options as they both had two I2C and two SPI so there is wiggle room. The second option had more available I/O pins though and it had PWM controllers just in case this comes up as something we absolutely have to use for the motor in the future. The cost was slightly higher than option 1, but not enough to outweigh the positives. The third option is more of a bare-minimum for use. The greatest strengths to it are the larger voltage range and cheaper cost. However, only having one I2C and one SPI connection makes future-proofing more difficult.
