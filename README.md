# Modbus Terminal

<img src="Resources/icon.png" width="120">

## What is Modbus Terminal?

Modbus Terminal is a Modbus master for Android: it reads and writes registers and coils of PLCs, inverters, energy meters and any other Modbus slave, over Modbus TCP (Wi-Fi/Ethernet) or Modbus RTU through a USB-serial adapter.

You can download it from Google Play here:
* [Modbus Terminal](https://play.google.com/store/apps/details?id=com.edodm85.modbusterminal)


## Features

- Modbus TCP client and Modbus RTU over USB serial (USB OTG)
- Function codes 01, 02, 03, 04, 05, 06, 0F, 10, 16, 17
- Values in decimal (unsigned) or hexadecimal
- Raw frame console or table view with the address of every register and coil
- Modbus exceptions decoded by name, timeouts and incomplete responses reported
- Requests checked against the limits of the Modbus specification before sending
- Console with time, date or timestamp, and log recording to a text file
- The connection stays open in the background
- Light and dark theme, English and Italian
- No ads: cyclic send (polling every 100–2000 ms) is an optional one-time in-app purchase

## Supported USB-serial adapters

FTDI, Prolific PL2303, CH340/CH341 and USB CDC-ACM devices. Baud rate from 1200 to 921600, 7/8 data bits, parity None/Odd/Even/Mark/Space, 1/1.5/2 stop bits.



## How does it work?

1. Set the server IP address and port in *TCP Settings* and press CONNECT, or for Modbus RTU set the serial parameters in *Serial Settings*, plug the USB-serial adapter and press OPEN.

<p align="left">
<img src="Resources/screen5.png" width="300">
</p>

2. Choose the function code, the unit ID, the start address and the quantity (or the values to write, separated by "/") and press SEND.

<p align="left">
<img src="Resources/screen3.png" width="300">
<img src="Resources/screen2.png" width="300">
</p>


3. Read the response as raw frames in the console, or as a table of registers and coils.

<p align="left">
<img src="Resources/screen1.png" width="300">
<img src="Resources/screen4.png" width="300">
</p>



## Payload format

| Function | Payload field |
|---|---|
| 01, 02, 03, 04 (read) | quantity, e.g. `10` |
| 05 Write Single Coil | `0` or `1` |
| 06 Write Single Register | value, e.g. `1450` (negative values like `-1` are allowed) |
| 0F Write Multiple Coils | values separated by "/", e.g. `1/0/1/1` |
| 10 Write Multiple Registers | values separated by "/", e.g. `100/200/300` |
| 16 Mask Write Register | `andMask/orMask`, e.g. `240/5` |
| 17 Read/Write Multiple Registers | `readQuantity/writeAddress/value1/value2/...`, e.g. `3/30/7/8` |

In the settings you can choose whether addresses and values are written in decimal or in hexadecimal (`0x` prefix optional).



## License

> Copyright (C) 2026 edodm85.  
> Licensed under the Apache License, Version 2.0.  
> (See http://www.apache.org/licenses/LICENSE-2.0 for the whole license text.)
