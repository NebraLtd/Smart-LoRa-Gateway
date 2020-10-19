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


**Layout Contents**

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


### 1.2.A Daughterboard (CM1/CM3) Overview

### 1.2.B Daugherboard (CM4) Overview
**This section is reserved for future use**

###

## Chapter 2 - Hardware Assembly

## Chapter 3 - Software Setup

## Chapter 4 - First Time Setup
