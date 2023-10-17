# Software Proposal
------------------

![Concept 1 Image](Images/software_proposal.png)
 For our software proposal, the first major set of actions is the fan control. The control of the fan depends on two parameters. First, the humidity of the envioronment. If the environment exceeds a cirtain threshold it will lower the temperature threshold requirement for the fan to activate. This way, the fan will turn on at a lower temperature on a day that is both hot and humid, as the humidity will factor into how hot it feels. If the temperture threshold is reached, an interupt will activate to turn on the hat. The next vital component to the software proposal is checking for a toggle in the light sensor readings. If the light sensor readings toggle from one high and one low to the other way around, the hat brim will spin to match the toggled high light sensor position. It should be noted that the brim will only spin with a full toggle, if both sensors read a high value, the light won't spin.
