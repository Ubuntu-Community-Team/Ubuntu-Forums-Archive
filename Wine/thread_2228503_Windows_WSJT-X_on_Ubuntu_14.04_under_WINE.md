---
title: "Windows WSJT-X on Ubuntu 14.04 under WINE"
date: 2014-06-07
forum: Wine
---

### Post by tm-hart on 2014-06-07
I am able to run WSJT-X version 1.3 for Windows on Ubuntu 14.04 using WINE version 1.6.  My setup information follow.  Key to operation is to create a symbolic link from /dev/ttyUSB0 to COM2.  For some reason, links to other devices do not seem to work (although I have not tried every possible option).  The following work with a Kenwood TS-590S transceiver.  

[COLOR="#0000CD"]**Ubuntu, Wine and WSJT-X**[/COLOR]

WSJT-X ver. 1.3 for Windows runs on Ubuntu Linux under WINE compatibility layer software.  During testing, contacts were made using the JT65 and JT9 modes.  The key hardware and software settings utilized are:

 [COLOR="#0000CD"]Software:[/COLOR]
- Ubuntu Linux version 14.04.
- Wine version 1.6.2.
- WSJT-X version 1.3 for Windows.

[COLOR="#0000CD"]Hardware:[/COLOR]
- Kenwood TS-590S.
- (1) HP desktop and (2) HP portable running Ubuntu 14.04.
- USB cable connecting computer to transceiver.

[COLOR="#0000CD"]Wine Setup:[/COLOR]
- Open a terminal and create the symbolic link “com2” in the “.wine/dosdevices” folder:
	# ln -s /dev/ttyUSB0 com2

[COLOR="#0000CD"]WSJT-X Configuration Panel settings:[/COLOR]
- PTT Method: CAT
- PTT Port: None
- Enable Cat: Kenwood TS590S
- CAT Port: com2
- Data Bits: 8
- Stop Bits: 1
- Serial Rate: 57600
- Polling Interval: 1
- Select: DTR, RTS and DATA
- Handshake = none.
- Audio In: USB Audio CODEC / Right
- Audio Out: USB Audio CODEC / Right

[COLOR="#0000CD"]Configuration Panel Tests Performed:[/COLOR]
- “Test CAT Control Button” = successful
- “Test PTT Button” = successful

---

