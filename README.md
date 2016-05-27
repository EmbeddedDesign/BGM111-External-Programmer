# BGM111 External Programmer 

An external programming adapter for Silicon Labs BGM111 devices.

## What you need to know

Pinouts for the external programming headers on the BGM111 WSTK (Wireless Starter Kit) can be found in UG122.

[UG122: Blue Gecko Wireless Starter Kit with BGM111 Module](https://www.google.com/url?sa=t&rct=j&q=&esrc=s&source=web&cd=1&cad=rja&uact=8&ved=0ahUKEwjrmtf0zvjMAhVE72MKHVwzDXkQFggdMAA&url=https%3A%2F%2Fwww.silabs.com%2FSupport%2520Documents%2FRegisteredDocs%2FUG122.pdf&usg=AFQjCNE2OhnjrMbEJHGlx0I69SfRVHJmWA)

### External Programming headers on the BGM111 WSTK

<img src="https://raw.githubusercontent.com/EmbeddedDesign/BGM111-External-Programmer/master/images/BTM111_WSTK_Header_Location.png" width="540">

<img src="https://raw.githubusercontent.com/EmbeddedDesign/BGM111-External-Programmer/master/images/BGM111_WSTK_Debug_Connector.png" width="540">

<img src="https://raw.githubusercontent.com/EmbeddedDesign/BGM111-External-Programmer/master/images/BGM111_WSTK_Simplicity_Connector.png" width="540">

### Process

The minimum pins required to program a BGM111 module are:

| Signal | BGM111 Pin (PAD) | WSTK Pin |
| --- | --- | --- |
| Reset | 30 | Debug 10 |
| +3.3V | 29 | Debug 1 & Simplicity 1 |
| GND | 1,12,20,31 | Debug 3,5,15,17,19 & Simplicity 7,9,11,13,15 |
| SWCLK | 21 (PF0) | Debug 4 |
| SWDIO | 22 (PF1) | Debug 2 |

(**NOTE:** It is important to note that Vdevice on the Debug connector is a reference voltage for the programmer and is insufficient to power a target BGM111. Power must be taken from the VMCU pin of the Simplicity connector.)

### energyAware Commander

Often referred to in documentation as **eACommander** (because of its executable name eACommander.exe), this tool is used to program the flash on a BGM111 target.

eACommander is included as part of the BGM SDK.

[The latest version can be found here](https://www.silabs.com/products/wireless/bluetooth/Pages/blue-gecko-bluetooth-module-getting-started.aspx).


Depending upon where you have installed the BGM SDK, the eACommander folder can be found relative to the install path.

<img src="https://raw.githubusercontent.com/EmbeddedDesign/BGM111-External-Programmer/master/images/eACommander_Path.png">

(**NOTE:** Your WSTK should be connected to a host computer and your BGM111 target should be connected to the WSTK prior to starting eACommander.)

The eACommander executable:

<img src="https://raw.githubusercontent.com/EmbeddedDesign/BGM111-External-Programmer/master/images/eACommander_executable.png">

If your WSTK is properly connected to and detected by your host computer, eACommander should display the serial number of the on-board SEGGER J-Link debugger at the top of the screen:

<img src="https://raw.githubusercontent.com/EmbeddedDesign/BGM111-External-Programmer/master/images/eACommander_J-Link.png">

Press the "Connect" button.
This should result in the "Board Information" box automatically populating with the information of the attached WSTK board:

<img src="https://raw.githubusercontent.com/EmbeddedDesign/BGM111-External-Programmer/master/images/eACommander_WSTK_Connected.png">

Change the "Debug Mode:" drop-down menu selection to "Out".
This should result in the "MCU Information" box automatically populating with the information of the attached BGM111 target device:

<img src="https://raw.githubusercontent.com/EmbeddedDesign/BGM111-External-Programmer/master/images/eACommander_Debug_Mode_Out.png">

Select the "Flash" menu item from the left scroll bar.
Select the binary file you wish to flash with the "Browse..." button in the "Flash EFM32" box.
Press the "Flash EFM32" button.

<img src="https://raw.githubusercontent.com/EmbeddedDesign/BGM111-External-Programmer/master/images/eACommander_Flash.png">

For whatever reason, it occasionally takes a few tries to get a target device to program successfully.

If you encounter errors:
* Ensure that the power switch on the WSTK is in "AEM" mode
  * Ensure that your target board is not consuming too much power
  * The target board is powered through the WSTK's onboard LDO and drawing too much power may result in a brownout
* Retry pressing the "Flash EFM32" button
* "Disconnect" and "Connect" the J-Link debugger using the button in the top-left of eACommander
* Disconnect everything and repeat the above steps

### Tag Connect

This adapter is designed to work with [Tag-Connect](http://www.tag-connect.com/).

Specifically, [TC2030-MCP-NL](http://www.tag-connect.com/TC2030-MCP-NL) (because of its small [footprint](http://www.tag-connect.com/Materials/TC2030-MCP-NL%20PCB%20Footprint.pdf)) or [TC2030-MCP](http://www.tag-connect.com/TC2030-MCP).

Tag-Connect footprints for most common CAD packages can be [found here](http://www.tag-connect.com/tag-connect-downloads).

A retaining clip for the TC2030-MCP-NL can be [found here](http://www.tag-connect.com/TC2030-CLIP).

### Ordering Boards

You can order these boards from OSH Park:

<a href="https://oshpark.com/shared_projects/8CRzoYDR"><img src="https://a800d827b6de8403a51e-6ffc2e718631809086ea40332b2055f7.ssl.cf1.rackcdn.com/assets/badge-5b7ec47045b78aef6eb9d83b3bac6b1920de805e9a0c227658eac6e19a045b9c.png" alt="Order from OSH Park"></img></a>

Or use the included Gerber files to have them manufactured elsewhere.

### BOM

The Bill of Materials for this board consists of only three components.

| Designator: | Quantity: | Cost: | Part Number:   | Note:   | Footprint: | Link: |
| :-- | :-- | :-- | :-- | :-- | :-- | :-- |
| J1 | 1 | $0.4400 | 54601-906WPLF | RJ12 Jack | http://portal.fciconnect.com/Comergent//fci/drawing/c-bmj-0082.pdf | http://www.newark.com/fci/54601-906wplf/cat3-rj12-modular-jack-6-position/dp/51M7960?ost=54601-906WPLF&selectedCategoryId=&categoryName=All+Categories&categoryNameResp=All+Categories |
| P1, P2 | 2 | $3.2400 | FLE-110-01-G-DV | 2x20 Female Header, 1.27mm Pitch | http://www.farnell.com/cad/320900.pdf | http://www.newark.com/samtec/fle-110-01-g-dv/board-board-connector-socket-20/dp/11P4413 |

### Schematic

![BGM111_External_Programmer_Schematic](/images/BGM111_External_Programmer_Schematic.png)

(**NOTE:** The pinouts on the Debug and Simplicity connectors appear to be flipped horizontally in the schematic as they are mounted on the *bottom* of the adapter board.)

### Layout

![BGM111_External_Programmer_Layout](/images/BGM111_External_Programmer_Layout.png)

### Adapter mounted on WSTK

![BGM111_WSTK_Adapter_Top](/images/BGM111_WSTK_Adapter_Top.jpg)

(**NOTE:** The adapter may need to be seated slightly askew to properly mate with the headers on the WSTK. This is due to the uneven height of the Debug and Simplicity connectors on the WSTK.)

![BGM111_WSTK_Adapter_Side](/images/BGM111_WSTK_Adapter_Side.jpg)

## License

[MIT License](LICENSE) © [Operator](https://github.com/EmbeddedDesign)