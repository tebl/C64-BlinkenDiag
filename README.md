# C64 BlinkenDiag
I was halfway through sketching out a new PCB based on the details found in an article on [tech.guitarsite.de](http://tech.guitarsite.de/c64_diag_dt_cart.html) before realizing it was already a PCB mentioned at the bottom, more specifically the one by [Diag64cart](https://github.com/svenpetersen1965/Diag64cart) by Sven Petersen (in turn based on [VersaCart64](https://github.com/bwack/Versa64Cart). I did however choose to introduce a few simple features of my own, mainly adding the option of disabling ROM boot - the method used was based on details found on [markus.brenner.de/cartridge](http://markus.brenner.de/cartridge). Secondly, I added a lot of LEDs in the hope that it might in some way be used to detect bus errors.

![C64 BlinkenDiag](https://github.com/tebl/c64-blinkendiag/raw/main/gallery/2021-03-16%2019.02.30.jpg)
![C64 BlinkenDiag](https://github.com/tebl/c64-blinkendiag/raw/main/gallery/2021-03-16%2023.21.34.jpg)

- [1> Building the unit](#1-building-the-unit)
  - [1.1> Soldering it together](#11-soldering-it-together)
  - [1.2> Assembling the unit](#12-assembling-the-unit)
  - [1.3> Testing it out](#13-testing-it-out)
- [2> Schematic](#2-schematic)
- [3> BOM](#3-bom)

# 1> Building the unit
Building the unit assumes you have at least minor experience soldering things together, recommended is at least a soldering station with adjustable temperature to get started - usually you'll want some 60/40 solder tin (if you can get that where you live). With the equipment sorted, now comes the shopping. So head on over to the [BOM](#3-bom)-section for some information on what you need, with ebay, AliExpress and similar sites you'll need to treat these as a starting search term and get what seems to match the gallery pictures.

## 1.1> Soldering it together
Every part already accounted for? Good, then let's start by not burning the house down (unless it obviously has more than one snake in it). Start by soldering in the resistors, there should only be a few of these on the board - follow it all up by tackling the resistor networks onto the boards, these are all the same type and you should match up the dot on them with the square hole. If you want to install sockets for all of the ICs, then that is good - if not, then please reconsider your life choices about now. Sockets need to match up with the markings on the PCB, indent on the socket should match the half-moon indent on the PCB (use machined sockets if you like that sort of thing).

![Build 001](https://github.com/tebl/c64-blinkendiag/raw/main/gallery/build_001.jpg)

Add the capacitors that are next to the sockets, these are only for decoupling and are not of the kind that is polarized - personally I tend to solder them in so that, if possible, you can see the printing on the side. The electrolytic capacitor on the bottom left corner, but we need to check that we have a component that will fit first - the faceplate will sit 8mm above the main PCB. If you have one that won't fit, you can lay it on its side instead of waiting for the slow boat from China. Note that this component is polarized, what this means is that you need to match the stripe with the filled in white space on the silkscreen.

![Build 002](https://github.com/tebl/c64-blinkendiag/raw/main/gallery/build_002.jpg)

Now we need to start the long and arduous task of soldering in all of those LEDs, but before we can do so - you  should probably check that they all work, the easiest way is to just use a CR2032 battery and putting it between the legs of the LED. Testing them will avoid soldering in one that is significantly more dim than the rest, especially if you originally got a whole shopping bag full of them for a single Dollar, Euro, Pound or whatever it is you usually fling at shopping attendants (please don't actually do this). One of the legs is called an anode and the other a cathode, but I can never remember which is which - so I'll just say that the short pin goes into the square hole. Only solder on one of the pins, then flip the board over again and heat up the pin by using your finger to push it flush against the board - this ensures that the faceplate will fit properly and you won't have a board where everything looks crooked.

![Build 003](https://github.com/tebl/c64-blinkendiag/raw/main/gallery/build_003.jpg)

SW1, 2 and 3 are a common AliExpress variety of SPDT 6-pin switches that needs some further explenation. The ones I've used here have a black base, the ones with a different colour will unfortunately not work as the pinouts have been shuffled around so ensure that you have the correct one ready to go. There is a square hole on the bottom that can be matched to the PCB illustration, so make sure that it goes into place with the hole at the top. There are also some keycaps floating around, but these fit rather loosely and I've taken to adding a drop of glue on the top of the switch to ensure that it doesn't go flying off. The reset switch is a more common momentary switch, the only requirement is that it is long enough to poke through the faceplate (6x6x9mm should fit, get a larger one if you require a bit than just barely).

## 1.2> Assembling the unit
Insert ICs into the sockets as indicated, ensuring that the indent matches the orientation on the board - plugging them in the wrong way ensures that you'll have to order some more. Double-check before even considering plugging it into something, use the picture below as reference. Even more important, study the board under good lighting condition in order to determine whether any stray blobs of solder has ended up in the wrong place - you're supposed to fix your C64, not add to its growing list of problems!

![Build 004](https://github.com/tebl/c64-blinkendiag/raw/main/gallery/build_004.jpg)

At this point I've not mentioned the EEPROM socket - it is designed for a 28C256, not 27C256 as used in many similar designs (mainly because I hate using UV to erase things and I have enough of them). You'll need an EPROM Programmer to put the machine code onto the chip, the one I use is one of the cheaper options - the MiniPro TL866. Using the *MiniPro Programmer* software (or similar), click the button below *Select IC* and search for 28C256 - find the relevant manufacturer for the chips you have and select the exact chip name. Using *File --> Open...*, browse to a suitable HEX-file such as the one found in the software section of this project (ensure that you download the raw version of this file, not just right click and save as on the github page - as that would save a bunch of html instead of the actual file). Just use the default options for the dialog, then flash the contents into the chip using *Device --> Program*. If this fails, either on write or verification - recheck that you have the correct chip specified, alternatively try another one as ebay chips usually have one or two out of 10 that simply don't work.

![Build 005](https://github.com/tebl/c64-blinkendiag/raw/main/gallery/build_005.jpg)

The board when plugged into a C64 would more than likely hang out of the connector at an angle, if not 3d-printing a base then I recommend adding some M3 nylon hex standoffs to the bottom of the unit (these should be approximately 16mm in height, alternatively you can combine two 8mm standoffs instead to get the same height) - these can either be F-F or M-F depending on what you have available. The cutouts for LEDs and switches have been designed for a spacing of 8mm between the main module and the faceplate, this should screw onto the 16mm ones you just installed on the bottom. Screw the faceplate onto the main module using standard M3x6mm nylon screws.

![Build 006](https://github.com/tebl/c64-blinkendiag/raw/main/gallery/build_006.jpg)

The voltmeter module, helpfully only coming with the text *voltage display* printed on them can be installed into the space allotted for it (I picked these up listed as a 0.36" voltage display module in various colours). It has wires sticking out of the bottom, so for the mounting I suggest using some longer M3 nylon screws and adding a nut directly below the module - then installing it on the board, adding two more nuts on the bottom of the main PCB to hold it into place.

## 1.3> Testing it out
With all of the jumpers in their default position, meaning LED outputs are disabled, and the SPDT switches in their upper position - you should get a standard *Diagnostic Cartridge*. Put the **FUNCTION** switch in the lower position and you should get the normal dead test. **ROM_BANK**, when in its lower position will get you a different set of diagnostic tools - depending on the images you flashed your EEPROM with (I specified a 28C256 EEPROM for ease of changing out the contents).

![Test 001](https://github.com/tebl/c64-blinkendiag/raw/main/gallery/test_001.jpg)


The final switch, labelled **ROM_DIS**, allows you to disable the cartridge detection routines in the C64 - similar to what is done with common cartridge expanders. When pushed the EEPROM is still electrically connected to the C64, but the PLA won't allow the C64 to boot from it - this is here so that you can observe the LED outputs on the machine, while still booting to the standard C64 bootup screen.

# 2> Schematic
The supplied KiCad files should be sufficient as both a schematic and as a  starting point for ordering PCBs (basically you could just zip the contents of the export folder and upload that on a fabrication site), the schematic is also available in [PDF-format](documentation/schematic) and this is what you'll need to print and work your way through this things don't work as expected after assembly.

# 3> BOM
Most parts should be easy to get a hold of from your favourite local electronic component shop, but given that I don't have access to such shops where I live so everything was based on whatever I could get cheapest from eBay/AliExpress (free shipping, but plan on waiting 3-4 weeks for delivery). Values listed in parenthesis are for features that are not required for basic cartridge functionality, but you should read through the section on [building the unit](#1-building-the-unit) to ensure that you're not missing out on anything cool. As always, plan on adding DIP-sockets in addition to the chips listed that have been listed.


| Reference        | Item                                                           | Count | Order  |
| ---------------- | -------------------------------------------------------------- | ----- | ------ |
| PCB              | Fabricate using Gerber files                                   |     1 | PCBWay
| Faceplate PCB    |                                                                |    (1)| PCBWay
| A1               | 0.36" Digital Voltmeter Module                                 |    (1)|
| C1               | 100nF ceramic capacitor (5mm pin spacing)                      |     1 |
| C2-C5            | 100nF ceramic capacitor (5mm pin spacing)                      |    (4)|
| C6               | 10uF 25v electrolytic capacitor (2mm pin spacing)              |    (1)|
| D1-D32           | 5mm LED, preferably non-clear variety                          |   (32)|
| JP1-JP4          | Male breakable pin header (3 pins)                             |    (4)|
| JP1-JP4 Jumpers  | 2.54mm pin header jumper (long type when used with faceplate)  |    (4)|
| R1,R2            | 10k ohm resistor                                               |     2 |
| RN1-RN4          | A331J 8x 330 ohm resistor network (SIP-9)                      |    (4)|
| SW1-SW3          | 6pin 8.5mm x 8.5mm latching switch                             |     3 |
| SW4              | 6x6x8mm momentary switch                                       |    (1)|
| U1               | 28C256 EEPROM (DIP-28)                                         |    (1)|
| U2 *             | 74HCT540 (DIP-20), or 74HCT541 for non-inverting option        |    (1)|
| U3-U5            | 74HCT573 (DIP-20)                                              |    (3)|
| Mounting **      | M3x8mm nylon HEX standoff (F-F)                                |    (4)|
| Mounting **      | M3x16mm nylon HEX standoff (M-F)                               |    (4)|
| Mounting **      | M3x6mm nylon screw                                             |    (4)|
| Mounting **      | M3 nylon nut                                                   |    (4)|
| Mounting ***     | M3 nylon nut                                                   |    (4)|
| Mounting ***     | M3x10mm nylon screw                                            |    (2)|


*) Quite a lot of the CPU signals are active low, the 74HCT540 will invert these signals so that the LED instead lights up when they are active. If you want these to reflect the actual signal, use the non-inverting variant of the chip instead (74HCT541).

**) The standoffs specified are the exact sizes required, but note that you could stack these to obtain the size you need - 8mm + 8mm usually equals 16mm (meaning you only need about 12 of them). Instead of buying the F-F standoffs separately, you could just cut off the screw part on the very bottom.

***) These are used to mount the voltmeter module, an extra nut is used between the module and PCB to avoid destroying the wires underneath the module.