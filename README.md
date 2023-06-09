# PIC32CXBZ2_WBZ45x ZIGBEE BLE DEMO

<img src="Docs/IoT-Made-Easy-Logo.png" width=100>


> "IoT Made Easy!" 

Devices: **| PIC32CXBZ2 | WBZ45x |**<br>
Features: **| ZIGBEE | BLE |**


## ⚠ Disclaimer

<p><span style="color:red"><b>
THE SOFTWARE ARE PROVIDED "AS IS" AND GIVE A PATH FOR SELF-SUPPORT AND SELF-MAINTENANCE. This repository contains example code intended to help accelerate client product development. </br>

For additional Microchip repos, see: <a href="https://github.com/Microchip-MPLAB-Harmony" target="_blank">https://github.com/Microchip-MPLAB-Harmony</a>

Checkout the <a href="https://microchipsupport.force.com/s/" target="_blank">Technical support portal</a> to access our knowledge base, community forums or submit support ticket requests.
</span></p></b>

## Contents

1. [Introduction](#step1)
1. [Bill of materials](#step2)
1. [Software Setup](#step4)
1. [Harmony MCC Configuration](#step5)
1. [Board Programming](#step6)
1. [Run the demo](#step7)

## 1. Introduction<a name="step1">

This application enables the users to create a Zigbee BLE bridge device with BLE Transparent UART functionality and Zigbee Combined interface application. Once the device is connected to the MBD app the user can control the Zigbee network with his Mobile phone via MBD app. The user can trigger the Zigbee commissioning procedure and can create the Zigbee network using MBD app. Once the Zigbee devices joins this network, it will start reporting its attribute values to the coordinator which is also shown on the MBD app.

![](Docs/Hardware_Setup.PNG)

| Tip | Go through the [overview](https://onlinedocs.microchip.com/pr/GUID-A5330D3A-9F51-4A26-B71D-8503A493DF9C-en-US-2/index.html?GUID-668A6CB2-F1FB-438D-9E1E-D67AC3C1C132) for understanding few key Zigbee 3.0 protocol concepts |
| :- | :- |

## 2. Bill of materials<a name="step2">

| TOOLS | QUANTITY |
| :- | :- |
| [PIC32CX-BZ2 and WBZ451 Curiosity Development Board](https://www.microchip.com/en-us/development-tool/EV96B94A) | 3 |

## 3. Software Setup<a name="step4">

- [MPLAB X IDE ](https://www.microchip.com/en-us/tools-resources/develop/mplab-x-ide#tabs)

    - Version: 6.05
	- XC32 Compiler v4.10
	- MPLAB® Code Configurator v5.1.17
	- PIC32CX-BZ_DFP v1.0.107
	- MCC Harmony
	  - csp version: v3.13.1
	  - core version: v3.11.1
	  - CMSIS-FreeRTOS: v10.4.6
	  - dev_packs: v3.13.0
	  - wolfssl version: v4.7.0
	  - crypto version: v3.7.6
	  - wireless_pic32cxbz_wbz: v1.1.0
	  - wireless_zigbee: v5.0.0
	  - wireless_ble: v1.0.0

- Any Serial Terminal application like [TERA TERM](https://download.cnet.com/Tera-Term/3000-2094_4-75766675.html) terminal application

- [MPLAB X IPE v6.05](https://microchipdeveloper.com/ipe:installation)

## 4. Harmony MCC Configuration<a name="step5">

### Getting started with Multisensor application in WBZ451 Curiosity board 

| Tip | New users of MPLAB Code Configurator are recommended to go through the [overview](https://onlinedocs.microchip.com/pr/GUID-1F7007B8-9A46-4D03-AEED-650357BA760D-en-US-6/index.html?GUID-B5D058F5-1D0B-4720-8649-ACE5C0EEE2C0) |
| :- | :- |

**Step 1** - Connect the WBZ451 CURIOSITY BOARD to the device/system using a micro-USB cable.

**Step 2** - Create a [new MCC Harmony project](https://github.com/MicrochipTech/EA71C53A/blob/master/H3/wireless_apps_pic32cxbz2_wbz45/apps/docs/creating_new_mplabx_harmony_project.md#creating-a-new-mcc-harmony-project).

**Step 3** - The "MCC - Harmony Project Graph" below depicts the harmony components utilized in this project.

![](Docs/Project_graph.PNG)

- In Device resources, go to wireless->drivers->zigbee->Device types and select Combined Interface. Accept Dependencies or satisfiers, select "Yes". The Combined Interface configuration is depicted as follows.

![](Docs/CI.PNG)

- Add UART components needed for console logs and commands. Right click on the "⬦" in Zigbee console and add the satisfier and in the same way add SERCOM0 to the USART console. 

- The SERCOM0 UART configuration is depicted as follows.

![](Docs/SERCOM0.PNG)

- From Device resources, go to Wireless->Drivers->BLE and select BLE STACK. Accept Dependencies or satisfiers, select "Yes".The configuration is depicted as follows.

![](Docs/BLE1.PNG)

![](Docs/BLE2.PNG)

- From Device resources, go to Wireless->Drivers->BLE->Profiles and select TRANSPARENT Profile. Accept Dependencies or satisfiers. The configuration is depicted as follows.

![](Docs/Transparent_profile.PNG)

- From Device resources, go to Wireless->Drivers->BLE-> Services and select TRANSPARENT Service. Accept Dependencies or satisfiers.

![](Docs/Connection.PNG)

- From project graph, go to Plugins->PIN configuration and configure as follows.

![PIN Configuration](Docs/PIN_config.PNG)

**Step 4** - [Generate](https://onlinedocs.microchip.com/pr/GUID-A5330D3A-9F51-4A26-B71D-8503A493DF9C-en-US-1/index.html?GUID-9C28F407-4879-4174-9963-2CF34161398E) the code.
 
**Step 5** - In "app_user_edits.c", make sure the below code line is commented 

- "#error User action required - manually edit files as described here".

**Step 6** - Copy the mentioned files from this repository by navigating to the location mentioned below and paste it your project folder. 

| Note | This application repository should be cloned/downloaded to perform the following steps. |
| :- | :- |
| Path | firmware/src |

- Copy the "app_ble" folder, "app.c" and "app.h" which can be found by navigating to the following path: "...\firmware\src"
- Paste the folder under source files in your project folder (...\firmware\src).

**Step 7** - Clean and build the project. To run the project, select "Make and program device" button.

### Getting started with other Zigbee applications in WBZ451 Curiosity board 

- Extended Light and Multisensor application folders will be available in this [link](https://github.com/Microchip-MPLAB-Harmony/wireless_apps_pic32cxbz2_wbz45/tree/master/apps/zigbee).
- Follow the steps provided in the above mentioned link to program the board.

## 5. Board Programming<a name="step6">

### Program the precompiled hex file using MPLAB X IPE

- The application hex file can be found in the hex folder

- Follow the steps provided in the link to [program the precompiled hex file](https://microchipdeveloper.com/ipe:programming-device) using MPLABX IPE to program the pre-compiled hex image. 

### Build and program the application using MPLAB X IDE

Follow the steps provided in the link to [Build and program the application](https://github.com/Microchip-MPLAB-Harmony/wireless_apps_pic32cxbz2_wbz45/tree/master/apps/ble/advanced_applications/ble_sensor#build-and-program-the-application-guid-3d55fb8a-5995-439d-bcd6-deae7e8e78ad-section).

## 6. Run the demo<a name="step7">

- In this application, manual commissioning is used to create a Zigbee network.
- The Zigbee CI and BLE transparent UART application starts advertising and we can establish a BLE Connection using MBD app. 
- The user can control the Zigbee network with his Mobile phone connected to Zigbee CI device via BLE Link
- To trigger the commissioning procedures manually, the user has to issue the following console commands on BLE UART in MBD app as given below:

	- Network Steering – “invokeCommissioning 2 0” 
	- The device starts to search for a network to join.
	- Network Formation – “invokeCommissioning 4 0” 
	- If the device is a router or a coordinator it forms the network.
	- SetFBRole 0 - this command to be given on application endpoint acts as target.
	- Finding & Binding - “invokeCommissioning 8 0” 
	- This command shall be given for any the devices which needs to be bound for clusters.
	
- Reset the other Zigbee devices to join into this network.
- Once the network is established Extended light and Multisensor devices will start reporting their attribute values to Combined interface as shown in the video. 
- The Extende Light can be switched ON or OFF by issuing an onOff command from the CI as shown below.

![](Docs/zigbee-ble.gif)	

#### Note

The user can also use "Commissioning on startup" on the Combined Interface device to create a Zigbee network. The procedure to commission a Zigbee network is discussed in detail in this [link](https://onlinedocs.microchip.com/pr/GUID-A5330D3A-9F51-4A26-B71D-8503A493DF9C-en-US-2/index.html?GUID-7E62A1F7-3B35-4B5A-86DA-F5694100F9E8). 