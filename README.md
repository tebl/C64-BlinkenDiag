# C64 BlinkenDiag

I was halfway through sketching out a new PCB based on the details found in an article on [tech.guitarsite.de](http://tech.guitarsite.de/c64_diag_dt_cart.html) before realizing it was already a PCB mentioned at the bottom, more specifically the one by [Diag64cart](https://github.com/svenpetersen1965/Diag64cart) by Sven Petersen (in turn based on [VersaCart64](https://github.com/bwack/Versa64Cart). I did however choose to introduce a few simple features of my own, mainly adding the option of disabling ROM boot - the method used was based on details found on [markus.brenner.de/cartridge](http://markus.brenner.de/cartridge). Secondly, I added a lot of LEDs in the hope that it might in some way be used to detect bus errors.

- [1> Building the unit](#1-building-the-unit)
  - [1.1> Soldering it together](#11-soldering-it-together)
  - [1.2> Assembling the unit](#12-assembling-the-unit)
  - [1.3> Testing it out](#13-testing-it-out)
- [2> Schematic](#2-schematic)
- [3> BOM](#3-bom)

# 1> Building the unit
Building the unit assumes you have at least minor experience soldering things together, recommended is at least a soldering station with adjustable temperature to get started - usually you'll want some 60/40 solder tin (if you can get that where you live). With the equipment sorted, now comes the shopping. So head on over to the [BOM](#3-bom)-section for some information on what you need, with ebay, AliExpress and similar sites you'll need to treat these as a starting search term and get what seems to match the gallery pictures.

## 1.1> Soldering it together

## 1.2> Assembling the unit
Insert ICs into the sockets as indicated, ensuring that the indent matches the orientation on the board - plugging them in the wrong way ensures that you'll have to order some more. Double-check before even considering plugging it into something, use the picture below as reference. Even more important, study the board under good lighting condition in order to determine whether any stray blobs of solder has ended up in the wrong place - you're supposed to fix your C64, not add to its growing list of problems!

At this point I've not mentioned the EEPROM socket - it is designed for a 28C256, not 27C256 as used in many similar designs (mainly because I hate using UV to erase things and I have enough of them). You'll need an EPROM Programmer to put the machine code onto the chip, the one I use is one of the cheaper options - the MiniPro TL866. Using the *MiniPro Programmer* software (or similar), click the button below *Select IC* and search for 28C256 - find the relevant manufacturer for the chips you have and select the exact chip name. Using *File --> Open...*, browse to a suitable HEX-file such as the one found in the software section of this project (ensure that you download the raw version of this file, not just right click and save as on the github page - as that would save a bunch of html instead of the actual file). Just use the default options for the dialog, then flash the contents into the chip using *Device --> Program*. If this fails, either on write or verification - recheck that you have the correct chip specified, alternatively try another one as ebay chips usually have one or two out of 10 that simply don't work.

The board when plugged into a C64 would more than likely hang out of the connector, if not 3d-printing a base then I recommend adding some M3 nylon hex standoffs to the bottom of the unit (these should be approximately 15mm in height) - these can either be F-F or M-F depending on what you have available. The cutouts for LEDs and switches have been designed for a spacing of 8mm between the main module and the faceplate, this should screw onto the 15mm ones you just installed on the bottom. Screw the faceplate onto the main module using standard M3x6mm nylon screws.

## 1.3> Testing it out
With all of the jumpers in their default position, meaning LED outputs are disabled, and the SPDT switches in their upper position - you should get a standard *Diagnostic Cartridge*. Put the **FUNCTION** switch in the lower position and you should get the normal dead test. **ROM_BANK**, when in its lower position will get you a different set of diagnostic tools - depending on the images you flashed your EEPROM with (I specified a 28C256 EEPROM for ease of changing out the contents).

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
| U2               | 74HCT540 (DIP-20), or 74HCT541 for non-inverting option        |    (1)|
| U3-U5            | 74HCT573 (DIP-20)                                              |    (3)|
| Mounting ***     | M3x8mm nylon HEX standoff (F-F)                                |    (4)|
| Mounting ***     | M3x15mm nylon HEX standoff (M-F)                               |    (4)|
| Mounting ***     | M3x6mm nylon hex screw                                         |    (4)|
| Mounting ***     | M3 nylon nut                                                   |    (4)|