![SmartGatewayBanner](imgs/SmartGatewayBanner.png)


# Nebra Smart LoRa Gateway Manual

Last Updated 21st October 2020

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
* If the Gateway is located outside, that it is not Raining, Snowing or any other adverse weather that may cause damage when opening.

### 1.1 Mainboard Overview

#### 1.1.2 Mainboard Layout

![SmartGatewayBreakdown](imgs/smartGatewayBreakdown-sm.png)


##### 1.1.2.1 Layout Contents

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

##### 1.1.2.2 Status LEDS
The mainboard has 3 Status LEDs which do the following:
* 12V LED - Indicates the mainboard has power located near the jumper.
* 5V LED - Indicates the 5V regulator is operational located in the power section.
* 3V3 LED - Indicates the 3V3 regulator is operational located in the power section.


### 1.2 Daugherboard Overview


#### 1.2.1 Daughterboard (CM3) Overview
The standard daughterboard supports the Compute Module 3, Compute Module 3+ and Lite Variants.

While also compatible with the CM1 we recommend using the CM3 Lite or CM3+ / CM3 Lite for storage sizes.

![DaughterboardBreakdown](imgs/daughterboardBreakdown.png)

##### 1.2.1.1 Layout Contents
1. Daughterboard Connector - Connects to the Mainboard.
2. SO-DIMM connector - Raspberry Pi Compute Module connects here.
3. Power Regulator - Power Circuitry required for the compute module.
4. SD Card Slot - SD Card Slot for if a CM3/CM3+ Lite is used.
5. Micro USB Connector - Used to re-flash the EMMC on the Compute Module.
6. USB Switch - IC responsible to allow switching between Micro USB and Mainboard.
7. USB Jumper - Used to switch between normal operation and flash mode, ensure it is in position 1-2 for normal operation and 2-3 for programming.
8. Power Jumper - Allows the module to be powered from the Micro USB connector. Only connect when programming from PC and ensure mainboard is not connected.

##### 1.2.1.2 Status LEDS
The board has 2 Status LEDs which do the following:
* Power LED - Indicates the board has power. (Blue)
* ACT LED - Indicates Read / Write operations on the storage. (Green)



#### 1.2.2 Daugherboard (CM4) Overview
This section is reserved for potential future use, however currently there is no plans to make a CM4 compatible daughterboard due to power and thermal constraints.

#### 1.2.3 Storage Selection
There is multiple choices of storage selection you can choose, we are still confirming the media we plan to ship with as standard, currently it is most likely an SD Card.

We recommend that on the CM3 that the Lite variant is used with an SD card so that the storage size is at least 8GB, if EMMC is used we recommend the CM3+ 8GB Variant.

##### 1.2.3.1 EMMC storage
Depending on the Compute Module 3+ used you can have up to 32GB of EMMC storage onboard. EMMC storage has the advantage of being soldered onto the board, however is a longer process to re-flash and if damaged is not user replaceable.

The Daughterboard contains the USB Circuitry to allow the EMMC to be flashed via USB using the correct tools to boot the Compute Module into programming mode.

##### 1.2.3.2 SD Card
The Compute Module 3+ Lite variant has no onboard storage so requires some form to boot from which would typically be an SD card.

We highly recommend a good quality Industrial rated SD card is used, these offer near EMMC reliability while providing the benefits of easier re-programming and replacement in case of failure.

In our testing the Sandisk Industrial cards last just as well as EMMC. [Model SDSDQAF3-008G-I](https://documents.westerndigital.com/content/dam/doc-library/en_us/assets/public/western-digital/product/embedded-flash/product-brief/product-brief-western-digital-industrial-sd-microsd.pdf)

##### 1.2.3.3 Net Boot
The Compute Module 3+ Lite when on a correctly configured network can load all of it's files off a correctly configured server resulting in a gateway that doesn't have any internal storage for the highest reliability / maintenance.

While possible to use, we are currently unable to offer support for this route.

##### 1.2.3.4 USB Boot
Finally the Compute Module 3+ Lite supports booting from USB, insert a suitable & correctly flashed USB drive into the USB Socket and it should boot from this if no SD card is inserted.

While possible to use, we are currently unable to offer support for this route.

### 1.3 Module Pinouts

#### 1.3.1 M-PCIE Pinout

The M-PCIE Connector is connected to the USB HUB for data, and has connection to the SIM slot in the following configuration.

#### 1.3.2 "RPi Style" Header Pinout
The Raspberry Pi Header takes the form factor of the 40 Pin Raspberry Pi header however is not fully electrically compatible. Due to GPIO pins being used on other parts of the board.

Only the first 24 Pins are wired, but are then in the same pinout as the Raspberry Pi header. The pinout is as follows.

![rpiHeader-Pinout](imgs/rpiHeader-pinout.png)

NC - Not Connected.

A majority of add-ons will work with this header, we recommend you check the pinout of the add-on you wish to use on <https://pinout.xyz/>


#### 1.3.3 LoRa Module Pinout
The LoRa Module Pinout takes the mechanical form factor of a M-PCIE module however is not electrically compatible, instead it is designed in the Pinout to be compatible with the following LoRa Modules:
* RAK833/SPI
* RAK2247/SPI
It is not compatible with the USB variant.

The electrical pinout is as follows:

| Pin#   | Name | Name | Pin#   |
| ----   | ---- | ---- | ----   |
|   1    | NC    | 3V3     |   2    |
|   3    | NC     | GND     |   4    |
|   5    | NC     | NC     |   6    |
|   7    | NC     | NC     |   8    |
|   9    | GND     | NC     |   10   |
|   11   | NC     | NC     |   12   |
|   13   | NC     | NC     |   14   |
|   15   | GND     | NC     |   16   |
|   17   | GND     | GND     |   18   |
|   19   | GPS_PPS     | NC     |   20   |
|   21   | GND     | Reset     |   22   |
|   23   | NC     | 3V3     |   24   |
|   25   | NC     | GND     |   26   |
|   27   | GND     | NC     |   28   |
|   29   | GND     | NC     |   30   |
|   31   | NC     | NC     |   32   |
|   33   | NC     | GND     |   34   |
|   35   | GND     | NC     |   36   |
|   37   | GND     | NC     |   38   |
|   39   | 3V3     | GND     |   40   |
|   41   | 3V3     | NC     |   42   |
|   43   | GND     | NC     |   44   |
|   45   | SPI_SCK     | NC     |   46   |
|   47   | SPI_MISO     | NC     |   48   |
|   49   | SPI_MOSI     | GND     |   50   |
|   51   | SPI_CS     | 3V3     |   52   |

NC - Not Connected.

The module in LoRa 1 is connected to the SPI1.0 bus, the module in LoRa 2 is connected to the SPI2.0 bus.
The module in LoRa 1 is reset via GPIO, and in LoRa 2 is reset via GPIO.
Both modules are connected to the GPS_PPS Signal provided by the on board GPS module.


#### 1.3.4 Daughterboard Connector Pinout
The Daughterboard connector is of our own specification, it allows us in the future to create new daughterboards for other SBCs.

The electrical pinout is as follows:

![daughterBoard-pinout](imgs/daughterBoard-pinout.png)

## Chapter 2 - Software Installation
For the Compute Module to boot up we require to flash the operating system onto the storage media.

In this section we'll show you how to flash the software onto both an SD Card or the RPi Compute Module's EMMC storage.

For full support we recommend using our IoT LoRa Gateway software designed for the best experience of the Gateway. You can run your own software however we then cannot provide full support if you have any issues, in this guide we'll assume that you're using our Software.

Finally to flash the software you will require a computer, with either a Micro SD Card reader if using SD Card or a Micro USB Cable if using the Compute Module's EMMC.

### 2.1 - Downloading the Software

First we need to download two bits of software, the Image containing the software that will run on the Pi and the tool to flash it.

In our experience we find Balena Etcher the best tool as it can write both SD cards and EMMC Modules which can be downloaded from <https://www.balena.io/etcher/>.

Once downloaded install the software ready for flashing.

Next download the latest release of our LoRa software from <https://github.com/PiSupply/iot-lora-image/releases>.
This currently is a beta release as we're still working on improving it for the Smart Gateway.

#### 2.1.1 - USB Boot Drivers
If you are planning on using the EMMC on a Compute Module and are on Windows you will require the Broadcom drivers for the compute module. Download this by going to <https://github.com/raspberrypi/usbboot/raw/master/win32/rpiboot_setup.exe> and then running the installer.

**Only do this step if using the EMMC on compute module.**

You may require to over-ride Windows Defender to install the library, to do this click more info then run which after you should get the install screen.

![RPiUSBSetup](imgs/rpi-2.png)

During setup you may get command line screens pop up while the driver is installing, this can take a while to install. Sometimes pressing enter on these screens is required.

Once setup is complete.

Now we're ready to flash, go to 2.2.1 for SD card of 2.2.2 for EMMC.

### 2.2.1 - Flashing a SD card

Begin by placing the micro SD card into the SD Card reader and plugging this into your computer.

Next launch Balena Etcher, you should be met with a screen like this.

![EtcherStart](imgs/etcher-1.png)

In the first section click Flash from file, then navigate to the location of where you downloaded the image from the previous step and select it.

Then in the select target section you'll need to select the SD Card you are using, click to change the media in the centre of the screen and select the media being used.

![EtcherReady](imgs/etcher-2.png)

Finally click flash, the software will now write the software to the card and then validate it is written correctly.

![EtcherDone](imgs/etcher-4.png)

### 2.2.2 - Flashing a Compute Module EMMC

Begin by first launching Balena Etcher, if you are on Linux you need to start it as root (Typically with sudo).

Next make sure the Compute Module is inserted into the daughterboard.

Then we need to set the jumpers to program it, move the jumper next to the PROG label to position 2-3, and ensure the 2 pin jumper JP4 is connected so it can power the Compute Module.

Before plugging in, In the first section of etcher click Flash from file, then navigate to the location of where you downloaded the image from the previous step and select it.

![EtcherReady](imgs/etcher-2.png)

After then connect the daughterboard to your computer with a Micro USB cable.

It may take a minute for it to download the required drivers, and then should start booting the compute module from the host computer ready for programming.

You can view the status of this in Etcher's target select.
![EtcherCM1](imgs/etcher-5.png)

Once ready, you can then select the compute module by checking the box next to it.
![EtcherCM2](imgs/etcher-6.png)

And then click flash, it'll take approximately 5-10 minutes and then you should be presented with this screen.

![EtcherDone](imgs/etcher-4.png)

### 2.3 - SSH Setup

As standard SSH is disabled for security reasons and for a majority of users SSH shouldn't need to be enabled.
However if you wish to enable it you can do the following.

1. Open your favourite text editor to create an empty file.
2. Go to save the file with it remaining empty.
3. Navigate to the Boot Partition of the SD Card or EMMC (Usually the only drive shown on windows).
4. Name the file "ssh" with no file endings and then save it to the partition.

SSH Should now automatically start on boot, note you must change the password for security.

## Chapter 3 - Hardware Assembly
### 2.0 Preliminary Steps
##### For this you will require the following hardware:
* The Smart Gateway Mainboard
* The Smart Gateway CM Daughterboard
* A Raspberry Pi Compute Module
* Mounting Posts & Screws
* Either [M20 Cable Gland](https://uk.pi-supply.com/products/general-cable-passthrough-gland-m20-x-1-5) or [RJ45 Ethernet Passthrough Gland](https://uk.pi-supply.com/products/rj45-ethernet-passthrough-gland-m20-x-1-5 )
* [N Type to UFL](https://uk.pi-supply.com/products/ufl-ipex-to-n-type-bulkhead) Bulkhead per Antenna Required.

##### We also recommend the following tools:
* Phillips Screwdriver
* MM Spanner
* MM Spanner
* Self Grip Pliers / Locking Pliers
* MM Hex Key

If you are planning to use a 3G/4G module we recommend for ease of installation that you insert the SIM Card into the SIM card slot before continuing as it's not easily accessible once mounted in the case. A Micro SIM card is supported.
![SmartGatewayBanner](imgs/simCard.jpg)

### 2.1 IP67 Case Assembly
If not using in our IP67 case you can skip this step.

#### Step 1 - Mounting Posts

First screw in the 4, 15MM high mounting posts into the case into the highlighted positions.

#### Step 2 - Ethernet or Cable Gland
Next we need to screw in either the Ethernet or Pass through Cable Gland.

First remove the cover nut at the bottom middle position of the case with an M20 spanner.

Then get the cable gland and carefully screw it in hand tight and then finally with an M20 spanner tighten it 1/4 of a turn to ensure the washer seals the connection.

#### Step 3 - N Connector Bulkheads
For this stage you'll need an N Type Bulkhead for each antenna required, this varies on setups.

* LoRa Module - 1 Connector per module.
* Onboard GPS - 1 Connector required to use.
* 3G/4G - 2 Connectors required for typical operation, 3 for GNSS support.
* Wi-Fi - Internal antenna is used, external will require 1 connector.

A maximum of 5 antennas is supported however in most cases 1-3 will be used, you can arrange the antennas in a pattern you prefer, we recommend the connector opposite to the module for that connector.

Remove the cover nut for the selected antenna with an M spanner and then keep in a safe place.

Then with your N Connector we recommend applying a slight bit of 3 In 1 Oil or WD40 to the thread, and then carefully screw through the case hand tight to begin with. Take care with the cable to ensure it doesn't get damaged.

Finally once hand tight with a self grip pliers carefully turn approximately 1/4 of a turn to ensure the washer seals the connection.

Repeat for each antenna.

#### Step 4 - Mainboard Fitting
Onto the mainboard, this fits in "upside down" where the RJ45 connector is facing the top of the case.

Connect the RJ45 connector with the cable running underneath the board, then finish placing inside the case ensuring none of the antenna connectors get trapped underneath.

Align into the case matching the mounting posts at the 4 locations, then with a screwdriver screw in each screw to begin with very loosely to finish aligning it up.

Finally tighten the screws to be hand tight, do not overtighten as this could damage the board.

### 2.2 Modules Fitting

#### 2.2.1 Daughterboard

For the Daughterboard carefully align the 60 pin header, with the module sitting in the footprint of the mainboard as shown.

It is important to ensure that the pins are aligned correctly and not misentered otherwise the module may get damaged.

If using an SD card, then insert the SD Card into the module. If using the EMMC Module then ensure no SD card is inserted as both cannot be used at the same time.
![SmartGatewayBanner](imgs/daughterSd.jpg)


Insert the Compute Module into the SO-DIMM connector aligning the notch, then carefully click the module into place ensuring both tabs either side are clicked in.

![SmartGatewayBanner](imgs/daughterCm3.jpg)

Finally ensure the jumpers are configured as followed:
* Storage Jumper (J) Position 1-2
* Power Jumper (J) not present.
![SmartGatewayBanner](imgs/daughterJumpers.jpg)


#### 2.2.2 LoRa Modules

To begin, fit the LoRa module into the LoRa Module 1 connector.
![SmartGatewayBanner](imgs/rak1.jpg)

Then carefully push down on the opposite side to click it into the retaining bracket.

![SmartGatewayBanner](imgs/rak2.jpg)

Finally connect the U.FL Connector to the N Type Bulkhead for the antenna highlighted in pink.

Repeat the steps for a second LoRa module in the LoRa Module 2 socket, however if only one module is used then the socket marked 1 should be used.

#### 2.2.3 4G Module Insertion

To begin, fit the 4G module into the MPCI-E connector.

Then carefully push down on the opposite side to click it into the retaining bracket.

Finally connect the 2 U.FL Connectors to the N Type Bulkhead for the antennas.

Repeat the steps for a second LoRa module in the LoRa Module 2 socket, however if only one module is used then the socket marked 1 should be used.


#### 2.2.4 GPS Module
The GPS module is already onboard the mainboard, so all that is required is if you are using it that the antenna is connected.

With the U.FL connector connect it to the connector next to the GPS module shown in this picture.

![SmartGatewayBanner](imgs/gpsAnt.jpg)

### 2.3 Connecting Antennas to the bulkheads.

### 2.4 Final connections & Power Up
Finally ensure the following:

* Either the Ethernet connector will be used for power or a DC Power supply is connected but not turned on.
* That the Power Jumper (JP1) is set to 1-2 for POE, or 2-3 for DC Power (Shown in pink below).
* All modules are fitted and clipped into place.

![SmartGatewayBanner](imgs/powerJumper.jpg)



## Chapter 4 - First Time Setup

### 4.1 First Power Up
Once everything is checked then first power up can proceed, to do this connect the external network cable to the bulkhead or turn on the power supply at it's source.

When powering up, you should see the 3 Power LEDs on the mainboard turn on, and then the Power LED on the daughterboard.

Shortly after the ACT led on the daughterboard should start blinking which indicates it's booting. The 2 LEDs on the Ethernet Jack should also light up with a successful network connection.

The gateway may take 10 minutes to complete it's first power up, during this it will boot up and first re-size the image to fit the storage size. After that it'll then reboot automatically and then start to download the latest software from the cloud including the latest up to date UI and LoRa packet forwarders.

### 4.2 Connecting to the Gateway
