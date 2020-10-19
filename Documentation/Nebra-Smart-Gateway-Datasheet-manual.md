# Nebra Smart LoRa Gateway Manual

Last Updated 19th October 2020

### Disclaimers
Copyright (C) 2020 Nebra LTD.
Changes to the specifications and features in this manual may be made by Nebra without prior notice.

Specifications and information provided in this maual are for informational use only. Nebra LTD. assumes no responsibility or liability for any errors or inaccuracies that may appear in this manual including the product & / or software.

All trademarks mentioned in this manual are property of their respective owners.

This product contains copyrighted software which are released under multiple open source licenses including but not limited to the GNU GPL, LGPL, and MIT BSD licenses. Such software is provided without warranty. Copies of these licenses are included in the software itself in further detail.

For the latest up to date information, please visit our Github Repository at https://github.com/NebraLtd/Smart-LoRa-Gateway/

## Contents


## Chapter 1 - Hardware Overview

### 1.0 Safety Precautions
Before proceeding please do the following:

* When handling the equipment, take appropriate ESD measures including using a grounding strap or a safely grounded object to avoid damage from static electricity.
* Hold all modules by the edges and avoid touching any components on them.
* If you remove a module place it into the anti-static bag that came with the hardware.
* Before installing or removing any modules or part of the hardware, ensure that any power has been switched off and disconnected including the Ethernet cable if powered via POE.


### 1.1 Mainboard Overview

#### 1.1.2 Mainboard Layout


##### Layout Contents

1. DC Barrel Jack - 2MM Pin, 6.5MM Barrel centre positive. Recommended PSU 12V @1.5A.
2. LAN Connector - RJ45 Connector wired to the Ethernet & POE Modules.
3. Power Jumper - 3 Pin jumper to select power source, place in position 1-2 for POE, or 2-3 for DC Jack.
4. POE Module - Negotiates 802.11AF compliant connection and outputs 12V DC into the power section.
5. Power Section - Takes the 12V power source and regulates it down to 5V & 3V3 rails.
6. Ethernet Controller - 10/100 Ethernet to USB 2.0 Adaptor, Maxlinear XR22800IL32-F. Connected to USB Hub.
7. USB Hub - 4 Port USB Hub, wired to Ethernet controller, USB port & M-PCIE connector.
8. USB Port - USB 2.0 Type A Connector, recommended max power 250mA.
9. "Raspberry Pi" Header - 40 Pin RPi style header, please note only the first 24 pins are wired. (Refer to 1.1.X)
10. M-PCIE connector - M-PCIE Connector wired up to USB for connectivity, has Micro SIM Card connected to it.
11. Micro Sim Card Slot - For use with 3G/4G Module in M-PCIE slot
12. Lora Module Connector - Designed for use with select M-PCIE LoRa Concentrators, these only have wired up SPI, plus GPS PPS from the GPS Module.
13. GPS Module - NEO-6M GPS module, connected to UART1 on the compute module. Plus PPS signal to LoRa modules for accurate timings.
14. Daughterboard Connector - Connects to Compute Module Daughterboard.

##### Status LEDS
The mainboard has 3 Status LEDs which do the following:
* 12V LED - Indicates the mainboard has power.
* 5V LED - Indicates the 5V regulator is operational.
* 3V3 LED - Indicates the 3V3 regulator is operational.


### 1.2 Daugherboard Overview


#### 1.2.1 Daughterboard (CM3) Overview
The standard daughterboard supports the Compute Module 3, Compute Module 3+ and Lite Variants.


**Layout Contents**
1. Daughterboard Connector - Connects to the Mainboard.
2. SO-DIMM connector - Raspberry Pi Compute Module connects here.
3. Power Regulator - Power Circuitry required for the compute module.
4. SD Card Slot - SD Card Slot for if a CM3/CM3+ Lite is used.
5. Micro USB Connector - Used to re-flash the EMMC on the Compute Module.
6. USB Switch - IC responsible to allow switching between Micro USB and Mainboard.
7. USB Jumper - Used to switch between normal operation and flash mode, ensure it is in position 1-2 for normal operation and 2-3 for programming.
8. Power Jumper - Allows the module to be powered from the Micro USB connector. Only connect when programming from PC and ensure mainboard is not connected.

**Status LEDS**
The board has 2 Status LEDs which do the following:
* Power LED - Indicates the board has power. (Blue)
* ACT LED - Indicates Read / Write operations on the storage. (Green)



#### 1.2.2 Daugherboard (CM4) Overview
This section is reserved for future use

#### 1.2.3 Storage Selection
There is multiple choices of storage selection you can choose, we are still confirming the media we plan to ship with as standard, currently it is most likely an SD Card.

##### 1.2.3.1 EMMC storage
Depending on the Compute Module 3+ used you can have up to 32GB of EMMC storage onboard. EMMC storage has the advantage of being soldered onto the board, however is a longer process to re-flash and if damaged is not user replaceable.

The Daughterboard contains the USB Circuitry to allow the EMMC to be flashed via USB using the correct tools to boot the Compute Module into programming mode.

##### 1.2.3.2 SD Card
The Compute Module 3+ Lite variant has no onboard storage so requires some form to boot from which would typically be an SD card.

We highly recommend a good quality Industrial rated SD card is used, these offer near EMMC reliability while providing the benefits of easier re-programming and replacement in case of failure.

In our testing the Sandisk Industrial cards last just as well as EMMC.

##### 1.2.3.3 Net Boot
The Compute Module 3+ Lite when on a correctly configured network can load all of it's files off a correctly configured server resulting in a gateway that doesn't have any internal storage for the highest reliability / maintenance.

##### 1.2.3.4 USB Boot
Finally the Compute Module 3+ Lite supports booting from USB, insert a suitable & correctly flashed USB drive into the USB Socket and it should boot from this if no SD card is inserted.

### 1.3 Module Pinouts

#### M-PCIE Pinout

The M-PCIE Connector is connected to the USB HUB for data, and has connection to the SIM slot in the following configuration.

#### "RPi Style" Header Pinout
The Raspberry Pi Header takes the form factor of the 40 Pin Raspberry Pi header however is not fully electrically compatible. Due to GPIO pins being used on other parts of the board.

Only the first 24 Pins are wired, but are then in the same pinout as the Raspberry Pi header. The pinout is as follows.

A majority of add-ons will work with this header, we recommend you check the pinout of the add-on you wish to use on <https://pinout.xyz/>

#### LoRa Module Pinout
The LoRa Module Pinout takes the mechanical form factor of a M-PCIE module however is not electrically compatible, instead it is designed in the Pinout to be compatible with the following LoRa Modules:
* RAK833
* RAK2247

The electrical pinout is as follows:


#### Daughterboard Connector Pinout
The Daughterboard connector is of our own specification, it allows us in the future to create new daughterboards for other SBCs.

The electrical pinout is as follows:


## Chapter 2 - Hardware Assembly

## Chapter 3 - Software Setup

## Chapter 4 - First Time Setup
