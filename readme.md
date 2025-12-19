# Programming the main controller board (USB-PD controller setup)

I am using a cheapo CH134A programmer board with an alligator clamp for SOIC-8. Example: https://a.co/d/9YnwEmc. This unit needed to be modded per the included instructions to work with an EEPROM chip running at 3.3v.

Binary file `USB_C_PD_controller.bin` was built using the TI Application Customization Tool at https://www.ti.com/tool/USBCPD-APPLICATION-CUSTOMIZATION-TOOL.

Choices used:
- Device Type: TPS25751
- Choose TPS 25751S under _Are you a 5V @ 3A power source (provider) only?_
- Highest supported USB Speed: USB 2
- Preferred data role: Device/Upstream Facing Port
- Support BC 1.2? No
- Liquid detection on Type C Connector? No
- Vendor ID and Desired Product ID: TI Vendor ID/0x0000 Product ID

After downloading the bin file from the tool, I used IMS_Prog which is a tool for Mac that will interface with the CH134A. On PC there are other tools, but you'll have to Google. IMS_Prog supposedly also works on Linux.

# Wiring

## 4-Pin Header to XLR
| 4 Pin Header | Wire Color  | Function  | XLR Pin Num  |
|---|---|---|---|
| 1  | Red  | Wind Gauge +12v  | 2  |
|  2 | Black  | Wind Gauge Pwr GND  | Shell  |
| 3  | Green  | Data RX from WG  | 3  |
|  4 |  White | Data GND  | 1  |

## 3-Pin Header to LP16 for RS232
| 3 Pin Header | Wire Color  | Function  | LP16 Pin Num  |
|---|---|---|---|
| 1  | Orange  | RXI  | 2  |
|  2 | White  | Data GND  | 3  |
| 3  | Blue  | TXO  | 1  |
