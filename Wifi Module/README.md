The Toybox WiFi module consists of a single circuit board with a ESP12F module.  This board performs several functions:

- Wifi access point and connectivity/configuration.
- Connectivity back to the Toybox website to monitor for new prints and send print status updates for the browser and phone app.
- Coordinates storing prints on an included microSD card as a cache (see SD-Card-Info).
- Connects to the printer controller via a 4-pin cable.
	- This cable contains 5V, ground, transmit (TX), and receive (RX) 115200 baud Serial connection for printing and status updates (see Serial-UART-Info below)
- Connect and controls to the power button / LED (4-pin)

ESP12F
This soldered-on IC contains a ESP8266 WiFi module along with an antenna and 4MB EEPROM.  There is plenty of details of this module online.


Serial-UART-Info

The serial connectivity of the module varies greatly as the module boots and in operation, but it follows similar to any ESP12F.
Initial boot messages are visible at 9600 baud, which is the default of the ESP8266 boot loader,  Other messages are availble during boot
at 74880 baud.  The main connection to the printer controler is 115200, however that is encoded using an MKS serial protocol.  During
some operations, the baud rate for transfer may get shifted even up to 1958400 for higher data transfer.


SD-Card-Info

The SD card that came with my particular model was a standard 128MB micro SD.  It is partitioned with DOS MBR and partitioning, however the partition is not actually used as a filesystem.  The Wifi module appears top seek through the raw SD card to 51200 bytes then begins writing raw g-code text as a buffer when a print job is requested.
