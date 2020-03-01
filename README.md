# Nebra IoT Smart LoRa Gateway

Copied from https://learn.pi-supply.com/make/nebra-smart-lora-gateway-prototype-information/

LoRa (Long Range) is the smart, long-range, wireless transmission technology that is enabling the future of IoT (Internet of Things).
It’s very low power but is only suitable for very small amounts of data.
Making it ideal for sensors such as weather monitoring, air quality etc

Our IoT Smart LoRa Gateway allows you to set up an industrial LoRa Gateway with ease at a cost effective price compared to other solutions.
Pre-loaded with our software you can have your gateway running in under 1 hour*.

The IoT Smart LoRa Gateway utilises the Raspberry Pi Compute Module 3, RAKWireless mPCIe LoRa gateway concentrator and optionally a 4G Module to provide a customisable solution for your requirements.

It’s available in the following frequency variations:

868 MHz
915 MHz
Other frequencies may be available at special request. Currently utalising the semtech SX1301 chipset however designed to be able to upgraded in the future the modualrity of the design.

Fully soldered and assembled, plug in and power up and you’re ready to go! No compiling of software required Nebra LoRa Gateway Controller Software – Provides an easy to use user interface to setup and configure your gateway within minutes. The Nebra Smart LoRa Gateway also has been designed to have updates over the internet.

Features
Utilizes the Raspberry Pi Compute Module 3 bringing stable software support and updates at a higher industrial level of reliability over a normal Raspberry Pi.
Power Over Ethernet – Power your gateway using most POE switchs or injector compliant with 802.11af
DC Power – Or power the gateway with a 12V 1.25A Power Supply
Dual LoRa Card Support – Supports up to two LoRa cards for either redundancy, dual region or 16 channel support.
Optional 4G Module – Add 4G Backup for when uptime is crucial, our software can switch between both 4G and LAN within 1 Minute of connectivity loss.
Fits in our IP67 Outdoors Case – Ideal for running a gateway outdoors.
Technical Specifications
Powered By Raspberry Pi Compute Module 3/3+
Quad Core ARM Cortex-A53 1.2GHZ
1GB DDR2 RAM
4-8GB EMMC Flash Memory
Dual LoRa Module Support
Supports both single and dual configurations
Redundancy & Multi Frequency modes
RF Interface over a standard U.FL connector (Hirose U.FL-R-SMT) with an impedance of 50. The RF port suports both Tx and Rx
WAN Connectivity
Supports IE 48V POE Injectors & Switches
Supports 2 LoRa Modules
Provides 100Mbps Ethernet to the CM3
USB Socket for USB Wi-Fi Adapter
M-PCIE 4G Module Support (USB Mode)
Efficient Power Consumption
Peak draw of 15W
Power via 12V 1.25A or POE
Security
The software that runs on the Nebra Smart LoRa gateway has been designed with both Security & Setup Speed in mind.

 

While it uses a Raspberry Pi it has had multiple tweaks made to the software to improve the security from the standard Raspbian images available including:

Local Webserver uses SSL certificate generated on first boot. 
User is required to setup a username and password for each gateway
Random Linux Password generated for each gateway.
SSH is disabled as default.
If SSH is enabled, the default port has been changed to help prevent it being found on search engines such as Shodan
Packet Forwarders & Website UI are run in their own containers allowing separation.
Linux is setup for automatic security & kernel updates.
Packet Forwarder & Web UI are distributed using docker containers allowing updates.
Containers are updated each system boot.
Want to keep up to date?
Follow updates on our twitter account @NebraLTD  & The Pi Supply Discord Channel

Note: All features and specifications mentioned are to be confirmed before release and are subject to change

* Figure given based on figures with user testing & feedback.
