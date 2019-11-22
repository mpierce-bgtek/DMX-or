# DMX-OR
DMX off ramp module
Introduction
The DMX-OR or DMX off ramp is a device which captures 8 channels of a DMX universe and transmits the data at lower speed (19,200) out its serial port.

DMX is a high speed (25O kbits) control bus used to control dimmers.  Its speed and other timing requirements are difficult to deal with natively in the Raspberry pi and other similar devices.  The DMX Off Ramp module can handle the timing requirements and will retransmit some of the data at a speed that the Pi and other devices can handle.

Generally a device does not need to use all of the 512 channels of data simultaneously, so the DMX Off Ramp module captures eight channels of data at any start address specified by the DIP switch and retransmits it out the serial port at 19200.

Physical Description
The DMX Off Ramp mdodule is a standard Raspberry PI hat size and mounts on top of the Raspberry Pi and connects to the I/O connector.  It provides a DMX input and DMX output connector and a 10 way DIP switch for setting the 9 bit DMX address.

THere are two LEDs on the board.
  DMX data
  

Firmware
The firmware in the DMX-OR transmits 9 bytes of data as 8 bytes of DMX data and one byte as EOF.  The data speed is 19200 bps formatted as 1 start, 8 data, 1 stop.  Although the DMX data can range from 0 to FF hex, the module limits the DMX data to FE so that FF can be used as a special character to mark the end of the packet.

so the data is 
Byte 1 - DMX 1 - 0 to FE hex
Byte 2 - DMX 2 - 0 to FE hex
Byte 3 - DMX 3 - 0 to FE hex
Byte 4 - DMX 4 - 0 to FE hex
Byte 5 - DMX 5 - 0 to FE hex
Byte 6 - DMX 6 - 0 to FE hex
Byte 7 - DMX 7 - 0 to FE hex
Byte 8 - DMX 8 - 0 to FE hex
Byte 9 - EOF always FF hex.

