# BGM111 External Programmer 

An external programming adapter for Silicon Labs BGM111 devices.

## What you need to know

Pinouts for the external programming headers on the BGM111 WSTK can be found in UG122.

[UG122: Blue Gecko Wireless Starter Kit with BGM111 Module](https://www.google.com/url?sa=t&rct=j&q=&esrc=s&source=web&cd=1&cad=rja&uact=8&ved=0ahUKEwjrmtf0zvjMAhVE72MKHVwzDXkQFggdMAA&url=https%3A%2F%2Fwww.silabs.com%2FSupport%2520Documents%2FRegisteredDocs%2FUG122.pdf&usg=AFQjCNE2OhnjrMbEJHGlx0I69SfRVHJmWA)

### External Programming headers on the BGM111 WSTK

![BGM111_WSTK_Debug_Connector](/images/BGM111_WSTK_Debug_Connector.png =540x)

![BGM111_WSTK_Simplicity_Connector](/images/BGM111_WSTK_Simplicity_Connector.png =540x)

### Process

The minimum pins required to program a BGM111 module are:
| Signal | BGM111 Pin | WSTK Pin |
| --- | --- | --- |
| Reset |  | Debug 10 |
| +3.3V |  | Debug 1 & Simplicity 1 |
| GND |  | Debug 3,5,15,17,19 & Simplicity 7,9,11,13,15 |
| SWCLK |  | Debug 4 |
| SWDIO |  | Debug 2 |

(_NOTE:_ It is important to note that Vdevice on the Debug connector is a refernce voltage for the prorammer and is insufficient to power a target BGM111. Power must be taken from the VMCU pin of the Simplicity connector.)

### Tag Connect

This adapter is designed to work with [Tag-Connect](http://www.tag-connect.com/).
Specifically, [TC2030-MCP-NL](http://www.tag-connect.com/TC2030-MCP-NL) (because of its small footprint) or [TC2030-MCP](http://www.tag-connect.com/TC2030-MCP).

A retaining clip for the TC2030-MCP-NL can be [found here](http://www.tag-connect.com/TC2030-CLIP).

### Ordering Boards

You can order these boards from OSH Park:

<a href="https://oshpark.com/shared_projects/8CRzoYDR"><img src="https://a800d827b6de8403a51e-6ffc2e718631809086ea40332b2055f7.ssl.cf1.rackcdn.com/assets/badge-5b7ec47045b78aef6eb9d83b3bac6b1920de805e9a0c227658eac6e19a045b9c.png" alt="Order from OSH Park"></img></a>

Or use the included Gerber files to have them manufactured elsewhere.

### Schematic

![BGM111_External_Programmer_Schematic](/images/BGM111_External_Programmer_Schematic.png)

(_NOTE:_ The pinouts on the Debug and Simplicity connectors appear to be flipped horizontally in the schematic as they are mounted on the *bottom* of the adatper board.)

### Layout

![BGM111_External_Programmer_Layout](/images/BGM111_External_Programmer_Layout.png)

## License

[MIT License](LICENSE) © [Operator](https://github.com/EmbeddedDesign)