# Hardware Proposal

## Schematic 
![Concept 1 Image](Images/team-design.png)

Our hardware design utalizes the PIC3232MX250F128B to control and collect data from all of our components. The three sensors are connected using I2C while the motordriver uses SPI to communicate with the PIC. To accomodate for pin availability, we connected the light sensor and temperature sensor on the same I2C pins and will uses different signal addresses to distinguish information from the two. 
## Bill of Materials
![Image](Images/314_BOM.png)

[Home Page](index.md)
