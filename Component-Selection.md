# Component Selection
--------------
# Voltage Regulator

| Solution | Pros          | Cons          |
| -------- | ------------- | ------------- |
| Example1 | - Relatively cheap compared to other 3.3V regulators.    | - Maximum Vin is 6V (5.5V recommended); the input of our power budget. No extra room.     |
|          | - Small footprint on PCB so it is easier to fit with other components into smaller space.     | - Adjustable output voltage only goes from 1 to 3.3V so most of the range does not work for this project.    |
|          | - Small footprint on PCB so it is easier to fit with other components into smaller space.     |    |
| Example2 | - Higher voltage ceiling that can be stepped down.     | - Fixed output voltage which does not allow flexibility later on.     |
|          | - Good switching frequency range using both Khz and Mhz ranges. Better on/off control.    | - Very large; utilizes more space and pads.    |
|          |       |      |
| Example3 | - Output voltage is adjustable from 3.3V to 20V in case the power rail needs editing later on.     | - Output current is limited to 500mA maximum with a 380mA recommended.    |
|          | - Capable of both stepping-up and stepping-down the input voltage.     | - Far more expensive than most other 3.3V capable regulators.    |
|          |      |     |
--------------
Choice: Option 2
-
Rationale: The second option provides a higher ceiling on the input voltage we can deliver if needed. While the fixed output voltage is not ideal, our current aim of 3.3V should be good to carry through the rest of the project for power needs. This also takes into account the max output current being the highest of the three at 2A. The cost is around the median for 3.3V regulators. The third option is great, but the cost just seems far too high with a low maximum current.

--------------
# UV Light Sensor

| Solution | Pros          | Cons          |
| -------- | ------------- | ------------- |
| Example1 | - Senses specifically UV light, eliminating the chances of other light waves interfering with the signal.      | - A 2mm x 2mm dimension will make it harder to install and make sure its working   |
|          | - Great price for our project.      | - Will make the piece hard to attach properly.    |
|          |     |      |
| Example2 | - Surface mount which is necessary for our system design   | - Component takes a higher understanding of light sensors     |
|          | - Mainly used for UV light which is what we want for our system     | - A 2mmx2mm dimension makes it harder for us to install and make sure it works properly     |
|          | - Given PCB outline makes it easier to understand how to install and get running    | -Also reads ambient light so that could effect our UV light readings    |
| Example3 | - Has multifunctionlity adn is programmable for easier use     | - Higher cost than our usual light sensor     |
|          | - Low power necessities     | - Has a limited range     |
|          | - Works with our programs we want to use for our system     | - Needs calibration in orde to operate correctly     |
--------------
Choice: Option 3
-
Rationale: Initially option one seemed the best of the three. Featuring specifically UV light sensitivity, which is exactly what we need, as wella s a low unit price it seemed like a clear winner. Unfortunately (or rather fortunately) we noticed it needed to be bought at large bulk, putting it out of our price range despite its ideal specifications. The third choice, while having the highest unit price and being primarily an IR proximity sensor, it also features a UV index sensor that would work well with our project. Additionally, it is much easier to use and readily accessible for outdoor use than option 2 which optimized for indoor use by default. 

-----------------
# Humidity Sensor

| Solution | Pros          | Cons          |
| -------- | ------------- | ------------- |
| Example1 | - Pro 1.1     | - Con 1.1     |
|          | - Pro 1.2     | - Con 1.2     |
|          | - Pro 1.3     | - Con 1.3     |
| Example2 | - Pro 2.1     | - Con 2.1     |
|          | - Pro 2.2     | - Con 2.2     |
|          | - Pro 2.3     | - Con 2.3     |
| Example3 | - Pro 3.1     | - Con 3.1     |
|          | - Pro 3.2     | - Con 3.2     |
|          | - Pro 3.3     | - Con 3.3     |
--------------
# Motor Driver

| Solution | Pros          | Cons          |
| -------- | ------------- | ------------- |
| Example1 | - Pro 1.1     | - Con 1.1     |
|          | - Pro 1.2     | - Con 1.2     |
|          | - Pro 1.3     | - Con 1.3     |
| Example2 | - Pro 2.1     | - Con 2.1     |
|          | - Pro 2.2     | - Con 2.2     |
|          | - Pro 2.3     | - Con 2.3     |
| Example3 | - Pro 3.1     | - Con 3.1     |
|          | - Pro 3.2     | - Con 3.2     |
|          | - Pro 3.3     | - Con 3.3     |
--------------
# Temperature Sensor

| Solution | Pros          | Cons          |
| -------- | ------------- | ------------- |
| Example1 | - Pro 1.1     | - Con 1.1     |
|          | - Pro 1.2     | - Con 1.2     |
|          | - Pro 1.3     | - Con 1.3     |
| Example2 | - Pro 2.1     | - Con 2.1     |
|          | - Pro 2.2     | - Con 2.2     |
|          | - Pro 2.3     | - Con 2.3     |
| Example3 | - Pro 3.1     | - Con 3.1     |
|          | - Pro 3.2     | - Con 3.2     |
|          | - Pro 3.3     | - Con 3.3     |
--------------
# Motor

| Solution | Pros          | Cons          |
| -------- | ------------- | ------------- |
| Example1 | - Pro 1.1     | - Con 1.1     |
|          | - Pro 1.2     | - Con 1.2     |
|          | - Pro 1.3     | - Con 1.3     |
| Example2 | - Pro 2.1     | - Con 2.1     |
|          | - Pro 2.2     | - Con 2.2     |
|          | - Pro 2.3     | - Con 2.3     |
| Example3 | - Pro 3.1     | - Con 3.1     |
|          | - Pro 3.2     | - Con 3.2     |
|          | - Pro 3.3     | - Con 3.3     |
--------------
# OpAmp

| Solution | Pros          | Cons          |
| -------- | ------------- | ------------- |
| Example1 | - Pro 1.1     | - Con 1.1     |
|          | - Pro 1.2     | - Con 1.2     |
|          | - Pro 1.3     | - Con 1.3     |
| Example2 | - Pro 2.1     | - Con 2.1     |
|          | - Pro 2.2     | - Con 2.2     |
|          | - Pro 2.3     | - Con 2.3     |
| Example3 | - Pro 3.1     | - Con 3.1     |
|          | - Pro 3.2     | - Con 3.2     |
|          | - Pro 3.3     | - Con 3.3     |
