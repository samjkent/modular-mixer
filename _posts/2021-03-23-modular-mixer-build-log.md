---
layout: post
title:  "Modular Mixer Build Log 1"
categories: audio diy mixer eurorack
---

First mistake was to order my parts from Mouser, 2 weeks later they've been 
FedEx'd from Texas and it's time to discover the hardware mistakes.

## PSU Board

Soldered the Meanwell DC-DC Converter to the PCB and hooked up a power supply to
 the input. The 12V, -12V, and 5V LEDs lit up briefly, and then turned off. The 
PSU showed 19V and 0.00A.

Replacing the underspecced [1N4148W](https://datasheet.lcsc.com/szlcsc/1811061725_ST-Semtech-1N4148W_C81598.pdf)
 diode with a short fixed this. The DC-DC convertor will survive reverse 
polarity so this diode was unecessary to start with.

![PSU](/audio/assets/psu.jpg)

## LM3914 PLCC Package

During the first build the PLCC package wasn't soldered correctly. Supposedly a
package that is socket and SMD compatible, but it's a definitely a pain to do by
 hand.

Need to desolder this one and redo it with a bit more care.

![PLCC](/audio/assets/plcc.jpg)

*note* - not sure I'd use this IC again.. although the alternatives are a uC 
with an ADC, or an array of OP amps with a resistor ladder.

## LM3914 Forgotten VDD Connection

The schematic for the VU meter is missing a power connection across the LED
anodes. Need to think of a tidy way to add a wire across for the first boards.

Untested due to the dodgy PLCC soldering mentioned above.

![Missing VDD](/audio/assets/missing-vdd.png)
![Bodge Wire VDD](/audio/assets/bodge-vdd.jpg)

## SMD resistors on unassembled side

After checking and approving the Schematics, PCBs, and component list, I noticed
 that R103 and R104 (10k resistors) were on the front side on the PCB and were 
not going to be assembled in the factory.

![R103 and R104](/audio/assets/unassembled-smd.png)

Ordered some 10k 0402 resistors and manually fitted them

![Soldering 0402](/audio/assets/0402.jpg)
![Soldered 0402](/audio/assets/0402-soldered.jpg)

## Input Gain / Send Pots are Anti-Clockwise

Pins 1 and 3 need swapping. The input gain maxes out at only 2x which isn't a 
huge amount. Maybe 50k Input Gain pots to crank the tracks.

## Cue switch is reversed

All cue switches need to have the same orientation, plus the LEDs aren't working

The switch is a pretty bad solution. An Analog Switch IC may be a better option. 
One SPDT switch/button can control the ICs. Example IC: £0.0451 [BL1551](https://datasheet.lcsc.com/szlcsc/Shanghai-Belling-BL1551_C82528.pdf)

## Channel PCBs are too short

The channel PCBs are too short and the screw holes don't line up perfectly.
It's possible to screw it in, but it doesn't quite fit, and leaves very little 
clearance for components.

![Short PCBs](/audio/assets/short-pcb.jpg)

## Headphone Amp - PNP the wrong way round

Plugging in the master channel can result in some magic smoke - the PNP 
transistors in the headphone amplifier are the wrong way round. Some visible 
damage on Q803

![Transistor](/audio/assets/transistor.png)
![Transistor Magic Smoke](/audio/assets/blown-transistor.jpg)

### Actually transistor pins are all incorrect

Wiring through hole transistors on flying wires results in a working headphone amplifier

![Transistor Pinout](/audio/assets/transistor-pins.png)

## Cue / Master mix fader doesn't work
This is a fxcking stupid circuit - not sure what I was thinking
![CueMaster](/audio/assets/transistor-pins.png)

