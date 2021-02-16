Zigbee CC2538 + CC2592 Multi Connect Board
==========================================

<img src="https://github.com/hallard/cc2538-multi-connect/blob/main/pictures/cc2538-boards.png">

This is just a quick and dirty PCB breakout board, it could be done better, but the fact is that is does the jobs and it does well. It has been designed with free version of Eagle Cad PCB (V7.7).

The first idea and project was made by @jonoxer with this Z2T aka Zigbee2Tasmota board. You can find original project [here](https://github.com/SuperHouse/Z2T). I won't take any credit on what already done, just used his work (thanks to open source) added new ZigBee chip and some features like:

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

<img src="https://github.com/hallard/cc2538-multi-connect/blob/main/pictures/cc2538-flash.png">

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

Schematics
==========

<img src="https://github.com/hallard/cc2538-multi-connect/blob/main/pictures/c2538-multi-connect-sch.png">

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

<img src="https://github.com/hallard/cc2538-multi-connect/blob/main/pictures/cc2538-boards.png">

[PCBs.io](https://www.pcbs.io/) was giveing me some reward when ordering my designed boards from their site. This was pretty good, because I useed these rewards to create and design new boards and order boards for a discounted price, but looks like PCBs.io is gone, I do not have any rewards from PCBs.io since August 2020 and my free order placed after are still not received, so my guess they are not on business anymore.

So you can order the board on [oshpark](https://oshpark.com). 

- [V1.0](https://oshpark.com/shared_projects/3h5YvEEm) 

It's a pitty after several discuss with OSHPark that I can't have any rewards for each people ordering my boards, this would allow me to order free PCB for shared projects and create new ones. For information my shared boards generated a total of **$285 162.00** orders at PCBs.io in 4 years, not bad at all :-)

Hoping one day OSHparks will thanks me giving them this market. 

As soldering CC2538 can be tricky, you can just solder needed pin marked with white dot on each. If not using JTAG or LED you can even solder less, check schematics.

Example of Assembled boards 
===========================


**Standalone With WeMos Mini D1**
<img src="https://github.com/hallard/cc2538-multi-connect/blob/main/pictures/cc2538-wemos.jpg" alt="Fully assembled with WeMos Mini D1">

**In USB Mode (with USB firmware)**
<img src="https://github.com/hallard/cc2538-multi-connect/blob/main/pictures/cc2538-usb.jpg" alt="Fully assembled, standalone mode">

**Packaged into enclosure**
<img src="https://github.com/hallard/cc2538-multi-connect/blob/main/pictures/cc2538-enclosure.png" alt="With enclosure">

License
=======

I kept the original one so

Copyright 2020 SuperHouse Automation Pty Ltd www.superhouse.tv

The hardware portion of this project is licensed under the TAPR Open Hardware License (www.tapr.org/OHL). The "license" folder within this repository contains a copy of this license in plain text format.

The software portion of this project is licensed under the Simplified BSD License. The "licence" folder within this project contains a copy of this license in plain text format.

Misc
====

See news and other projects on my [blog][1] 
 
[1]: https://hallard.me
