Zigbee CC2538 + CC2592 Multi Connect Board
==========================================

<img src="https://github.com/hallard/cc2538-multi-connect/raw/master/pictures/cc2538.png">

This is just a quick and dirty PCB breakout board, it could be done better, but the fact is that is does the jobs and it does well.

The first idea and project was made by @jonoxer with this Z2T aka Zigbee2Tasmota board. You can find original project [here](https://github.com/SuperHouse/Z2T). I won't take any credit on what already done, just used his works (thanks to open source) added new ZigBee chip and some features like:

- Easy to build and solder, 0805 CMS components, the trickiest is the CC2538 module
- just but what you need, not all components are needed (but ZigBee chip CC2538 at least)
- Can works in USB mode, connect to any equiped with USB port CPU (Computer, raspberry, router, ...)
- Can be pluged in Serial mode directly on Raspberry PI
- Can be pluged in Serial mode to any equiped with USB port CPU using FTDI like USB Serial adapturs
- Can be used in standalone mode by adding ESP8266 Wemos Mini D1 board with Tasmota Firmware
- Wired 4 Leds, and 3 are controlled by Z-Stack 3 firmware
- 2 push buttons for Reset / Boot mode (to be able to flash Z-Stack firmware on CC2538)
- JTAG connector (never used)
- SMA footpring for those needed 
- fit on classic Aliexpress cheap enclosures


Detailed Description
====================

This repo is not intented to be a reference for ZigBee stuff and how this ZigBee PCB is working. It's for makers who know what they do with DIY electronic boaards and associated software. Anyway everyone could do and use this board with further reading and some patience.

So there is no specific documentation, but you'll find below some references to start of course, please read carrefelly the following links before opening any issue.

- Starting point [discussion](https://github.com/Koenkk/zigbee2mqtt/discussions/1568) about this module on @Koenkk github
- Tasmota [ZigBee documentation](https://tasmota.github.io/docs/CC2530/)
- @jethome-ru Z-Stack [Firmware](https://github.com/jethome-ru/zigbee-firmware/tree/master/ti/coordinator/cc2538_cc2592) used and instruction to flash

To be honest, the easiest way I found to flash firmware is to use one FTDI USB Serial adapter (take care one with 3.3V regulator, not 5V) and [cc2538prog](https://github.com/1248/cc2538-prog) using WeMos Mini D1 header

<img src="https://github.com/hallard/cc2538-multi-connect/raw/master/pictures/cc-2538-flash.png">


Installation
============

Depending on final use you want and I won't describe all here since there is a huge mix of possibilities, I consider after reading, tpi know how and with what you want to use this board.

## Hardware 

- Standalone with WeMos Mini D1
- on Raspberry PI Serial
- on USB computer
- ...

## Sofware

- Tasmota
- ZigBee2Mqtt
- Zigpy
- ...


, ) you need to solder ;If you're using Battery clip connector, please isolate the A4/A5 and FTDI (V1.0 only) pads from clip because it will do shorts and prevent I2C to work.

I'm Using the [LMIC stack](https://github.com/matthijskooijman/arduino-lmic) as his with custom sketch, this one is under NDA for Ultra Low Power, So I can't provide it but you can use the one in example of LMIC.

You may need to disable debug of LMIC stack if missing.

I'm also changing the Bootloader to use optiboot and win 1.5K of flash code and setup the Brown Out Detect to 1.8V to be able to works under 2.7V. Please see this [Pro-Mini-ICSP-FTDI](https://github.com/hallard/Pro-Mini-ICSP-FTDI) repo if you need to flash your Arduino Pro Mini with this bootloader. You'll see in [bootloader](https://github.com/hallard/Pro-Mini-ICSP-FTDI/tree/master/bootloaders) folder, I've compiled some for various Speed and for 8MHz and 16MHz Crystal (I use the 250KBPS one, it's fast and reliable).

I've also created custom board definition for Arduino IDE so if using my bootloader, you'll have the board clock and serial speed selection in Arduino IDE, it located [here](https://github.com/ch2i/ch2i-arduino-boards)

Schematic
=========

<img src="https://github.com/hallard/cc2538-multi-connect/raw/master/pictures/c2538-multi-connect-sch.png">

Bill Of Material (BOM)
======================

Nothing fancy, all components are 0805 and/or PTH and can be ordered almost anywhere (digikey, mouser, radiospare, ...). 
use only what you need dependings on what you want to do. 


- This board [PCB](https://oshpark.com/shared_projects/3h5YvEEm) of course 
- cc2538 module take care check the footprint there are differents vendors with different footprints
- R5 any 1K 0805 SMD
- R6 any 1K5 0805 SMD
- C1 33uF (or plus) 1206 tantale capacitor (used one of my boxes, don't know ref)
- 2 x Tactile switch such as SKRPACE010 (4.2x3.2x2.5mm)
- If you want LEDs, 4 SMD 0805 Led plus associated resistor
  - R1 Red = 1K 0805 (Power)
  - R2 Green = 1K 0805 (not used by firmware yet)
  - R3 Blue R3 = 330 ohm 0805 (join mode)
  - R4 Pink or other = 330 Ohm 0805 (ZigBee communication)
- If wanted, PI Connector `2.54 mm 2x5 pin Female Double Row`
- If needed USB Breakout `micro USB to DIP adapter Converter 2,54 mm PCB Breakout`
- If needed 3.3V Regulator `DC 5V to 3.3V Step-Down Power Supply Module AMS1117-3.3` (if powered thru USB without WeMos for Example)
- If needed enclosure `Waterproof Plastic Clear Cover Enclosure Case 85*58*33MM`
- Loved this USB/Serial 3.3V [module](https://aliexpress.com/item/32664922086.html), very cheap and do all job but looks hard to find now, but still available on some places.

Text noted in `between like this one` means type text in google to find seller (Aliexpress, Ebay, ...)

Assembling Boards 
=================

<img src="https://github.com/hallard/cc2538-multi-connect/raw/master/pictures/cc2538.png">

You can order PCBs of this board at [oshpark][https://oshpark.com/shared_projects/3h5YvEEm]~~

- ~~[V1.2](https://www.PCBs.io/share/r1a3J) Classic I2C connector~~
- ~~[V1.1a](https://www.PCBs.io/share/8AGb2) Classic I2C connector~~
- ~~[V1.1a](https://www.PCBs.io/share/zjKdY) Grove I2C connector~~
- ~~[V1.0](https://www.PCBs.io/share/r3LdE)~~

PCBs.io was giveing me some reward when ordering my designed boards from their site. This was pretty good, because I useed these rewards to create and design new boards and order boards for a discounted price, but looks like PCBs.io is gone, I do not have any rewards from PCBs.io since August 2020 and my free order placed after are still not received, so my guess they are not on business anymore.

So you can order the board on [oshpark](https://oshpark.com). 

- [V1.0](https://oshpark.com/shared_projects/3h5YvEEm) 

It's a pitty after several discuss with OSHPark that I can't have any rewards for each people ordering my boards, this would allow me to order free PCB for shared projects and create new ones. For information my shared boards generated a total of **$285 162.00** orders at PCBs.io in 4 years, not bad at all :-)

Hoping one day OSHparks will thanks me giving them this market. 

As soldering CC2538 can be tricky, you can just solder needed pin marked with white dot on each. If not using JTAG or LED you can even solder less, check schematics.

Example of Assembled boards 
===========================

<img src="https://github.com/hallard/Mini-LoRa/raw/master/pictures/Mini-LoRa-FrontBig.jpg" alt="Fully assembled with sensors">


License
=======

<img alt="Creative Commons Attribution-NonCommercial 4.0" src="https://i.creativecommons.org/l/by-nc/4.0/88x31.png">   

This work is licensed under a [Creative Commons Attribution-NonCommercial 4.0 International License](http://creativecommons.org/licenses/by-nc/4.0/)    
If you want to do commercial stuff with this project, please contact [CH2i company](https://www.ch2i.eu/en#support) so we can organize an simple agreement.

Misc
====

See news and other projects on my [blog][1] 
 
[1]: https://hallard.me
[3]: https://www.PCBs.io

[20]: http://www.seeedstudio.com/depot/index.php?main_page=opl_info&opl_id=4
[21]: http://www.ebay.com/itm/170578495165
[22]: http://www.ebay.com/itm/351690376555
[23]: http://www.ebay.com/itm/351738196013
[24]: http://www.ebay.com/itm/371534934746
[25]: https://www.adafruit.com/products/1979
[26]: https://www.sparkfun.com/products/11114

[27]: http://www.ebay.com/itm/121929386506?var=420920026758
[28]: http://www.ebay.com/itm/371348168950
[29]: http://www.ebay.com/itm/351588181858


[40]: http://www.ebay.com/itm/262500056078
[41]: http://www.aliexpress.com/item/Free-Shipping-Good-Quality-ABS-Material-Transparent-Cover-IP66-Waterproof-Electrical-Switch-Box-125-125-75mm/32522255056.html
[42]: http://www.aliexpress.com/item/Temperature-and-humidity-Protective-sleeve-Accessories-PCB-for-SHT20-SHT21-SHT25/32695663191.html?spm=2114.13010208.99999999.264.dgLxek
[43]: http://www.ebay.com/itm/401000227934
[44]: http://www.ebay.com/itm/182181715511?var=483966356069
[46]: http://www.ebay.com/itm/391462862706
[47]: http://www.ebay.com/itm/232153789354?var=531358445664
[48]: http://www.ebay.com/itm/301856945402

[50]: https://octopart.com/bom-tool/MsqCYjTr