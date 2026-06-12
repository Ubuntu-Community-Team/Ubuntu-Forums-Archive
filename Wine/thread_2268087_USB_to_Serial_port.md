---
title: "USB to Serial port"
date: 2015-03-06
forum: Wine
---

### Post by julieneoz on 2015-03-06
Hi Ubuntu fans,

I am running Ubuntu 14.04 LTS and trying to get an opical probe CP210x (USB to Serial) on my machine.
I believe I was able to get the USB to serial installed:

#julien@donjon:/var/lock$ lsusb
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 03eb:8819 Atmel Corp. 
Bus 001 Device 003: ID 13d3:5195 IMC Networks 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 009: ID 10c4:ea60 Cygnal Integrated Products, Inc. CP210x UART Bridge / myAVR mySmartUSB light
Bus 003 Device 001: ID 1d6b:000julien@donjon:/var/lock$ dmesg |grep USB02 Linux Foundation 2.0 root hub

#julien@donjon:/var/lock$ dmesg |grep USB0
[14747.372288] usb 3-2: generic converter now attached to ttyUSB0


#julien@donjon:/var/lock$ ls -al /dev/ttyUSB0 
crwxrwxrwx 1 root julien 188, 0 Mar  6 17:38 /dev/ttyUSB0

#julien@donjon:/var/lock$ stty < /dev/ttyUSB0 
speed 9600 baud; line = 0;
kill = ^H; eof = <undef>; min = 0; time = 0;
ignbrk -brkint -icrnl -imaxbel
-opost -onlcr
-isig -icanon -iexten -echo -echoe -echok noflsh -echoctl -echoke
julien@donjon:/var/lock$ 
 A -    Serial Device      : /dev/ttyUSB0                              |
    | B - Lockfile Location     : /var/lock                                 |
    | C -   Callin Program      :                                           |
    | D -  Callout Program      :                                           |
    | E -    Bps/Par/Bits       : 9600 8N1                                  |
    | F - Hardware Flow Control : No                                        |
    | G - Software Flow Control : No                                        |
    |                                 


I can run putty and connect to /dev/ttyUSB0, but it doesn't seem that I can send any traffic through the /dev/ttyUSB0 port.

My plan is to run my application on WINE with the correct mapping (I think that is correct):

[EMAIL="julien@donjon:~/.wine"]julien@donjon:~/.wine[/EMAIL]/dosdevices$ ls -al
total 32
drwxrwxr-x 2 julien julien 4096 Mar  5 14:05 .
drwxrwxr-x 4 julien julien 4096 Mar  6 15:45 ..
lrwxrwxrwx 1 julien julien   10 Feb 27 21:59 c: -> ../drive_c
lrwxrwxrwx 1 julien julien   12 Mar  5 14:05 com3 -> /dev/ttyUSB0
lrwxrwxrwx 1 julien julien    8 Feb 27 21:59 d:: -> /dev/sr0
lrwxrwxrwx 1 julien julien    8 Mar  2 14:00 e:: -> /dev/sdc
lrwxrwxrwx 1 julien julien    9 Mar  2 14:00 f:: -> /dev/sdc1
lrwxrwxrwx 1 julien julien    1 Feb 27 21:59 z: -> /

I am keen to be able to test my USB to serial port on UBuntu before moving to WINE. Would you have any suggestion where I need to look at? I am running out of suggestion why I cannot send/see traffic to this port?

Thanks

---

### Post by Mark Phelps on 2015-03-06
Are you aware the Wine is NOT a Windows Emulator?  Wine is a hack in which some Windows DLLs (Dynamic Linked Libraries) were rewritten to replace Windows OS kernel calls with Linux OS kernel calls.  To the degree that a Windows apps uses only those DLLs, to the same degree, it is successful under Wine.  But more recent Windows apps use a variety of middleware that are not supported on Linux.

You could save some trouble by checking the WineHQ application compatibility tool for the app you want to run to see its rating.  Anything rated lower than Gold is going to be a waste of your time installing.

---

### Post by slickymaster on 2015-03-06
*Moved to the ***Wine*** sub-forum*

---

### Post by julieneoz on 2015-03-06
I understand the challenge of using wine but I am still keen to troubleshoot my usb to serial port, i don't think my post falls within wine sub-forum

---

### Post by julieneoz on 2015-03-06
forgot to mention that my application runs on Windows XP

---

### Post by raul-alvarez-fdz on 2015-03-27
Try adding your user to the group "dialout" (editing /etc/group).

---

