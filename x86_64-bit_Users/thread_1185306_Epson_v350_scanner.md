---
title: "Epson v350 scanner"
date: 2009-06-12
forum: x86 64-bit Users
---

### Post by avanrens on 2009-06-12
Hi, I have an Epson Perfection V350 Photo and would love to get it working in Ubuntu 9.04 64 bit. If anyone could help me in how to install the driver and programs to get it to work, this would be greatly appreciated.
Thank you.

---

### Post by The hobo on 2009-07-14
I have the same problem. I have tried Wine, X sane and I scan and all seem not working for me. It might work if you tried any of them but this particular brand is really causing problems for Ubuntu users. First start of by searching for it using you're terminal. Any of these commands will work:  sane-find-scanner , sudo sane-find-scanner , scanimage -L , sudo scanimage -L . I hope you have more luck then me!

---

### Post by avanrens on 2009-07-16
My Scanner works well out of VirtualBox

---

### Post by angelakrebs on 2009-07-30
> **The hobo said:**
> I have the same problem. I have tried Wine, X sane and I scan and all seem not working for me. It might work if you tried any of them but this particular brand is really causing problems for Ubuntu users. First start of by searching for it using you're terminal. Any of these commands will work:  sane-find-scanner , sudo sane-find-scanner , scanimage -L , sudo scanimage -L . I hope you have more luck then me!
[COLOR=Indigo]I have the same issue also and am having no luck. I am trying to install the Epson Perfection V350 Photo on Ubutu 9.04 on a Dell inspiron 1525 laptop. Used the suggested commands from the discussion above:[/COLOR]
[B]
     [COLOR=Indigo]sane-find-scanner[/COLOR][/B][COLOR=Indigo] yielded the following response:[/COLOR]
[I]     found USB scanner (vendor=0x04b8, product=0x012f) at libusb:002:005
       # Your USB scanner was (probably) detected. It may or may not be supported by
       # SANE. Try scanimage -L and read the backend's manpage.[/I]
[B]
  [COLOR=Indigo]   sudo sane-find-scanner[/COLOR][/B][COLOR=Indigo] yielded the following response:[/COLOR]
     found USB scanner (vendor=0x04b8 [EPSON], product=0x012f [EPSON Scanner]) at      libusb:002:005
       # Your USB scanner was (probably) detected. It may or may not be supported by
       # SANE. Try scanimage -L and read the backend's manpage
[COLOR=Indigo]Detected the brand of scanner... making some progress? [/COLOR][B]   
 [COLOR=Indigo]
     scanimage -L[/COLOR][/B][COLOR=Indigo] and** sudo scanimage -L** each yielded the following response:[/COLOR]
*     device `v4l:/dev/video0' is a Noname Laptop Integrated Webcam virtual device*
[COLOR=Indigo]Clearly this is not the right device... This is my built-in web cam. 

Can anyone tell me what I should try next to troubleshoot this issue? Any helpful suggestions would be greatly appreciated.[/COLOR]

---

### Post by cisk4me on 2009-08-07
I tried the product "Image Scan! for Linux" maintained by Avasys Corporation. I installed the package rather than compiling from source code.

Go to the link
[http://www.avasys.jp/english/linux_e/dl_scan.html](http://www.avasys.jp/english/linux_e/dl_scan.html)

and follow thru to the download area. I chose 

```
iscan_2.20.1-1.ltdl7_i386.deb
iscan-plugin-gt-f700_2.1.0-3_i386.deb
```
to use with Jaunty on a Dell XPS M1530 (I have a 32-bit installation).
There is a warning about boot problems, but I think this refers to
the previous version iscan_2.20.0. The plugin is needed to work with the v350.

If you download the files to say /home/fred, then the command to run
from a terminal is

```
$ sudo dpkg -i /home/fred/iscan_2.20.1-1.ltdl7_i386.deb
$ sudo dpkg -i /home/fred/iscan-plugin-gt-f700_2.1.0-3_i386.deb
```
The output I got is

```
Selecting previously deselected package iscan.
(Reading database ... 277913 files and directories currently installed.)
Unpacking iscan (from .../iscan_2.20.1-1.ltdl7_i386.deb) ...
Setting up iscan (2.20.1-1.ltdl7) ...

Processing triggers for menu ...
Processing triggers for man-db ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place

Selecting previously deselected package iscan-plugin-gt-f700.
(Reading database ... 277989 files and directories currently installed.)
Unpacking iscan-plugin-gt-f700 (from .../iscan-plugin-gt-f700_2.1.0-3_i386.deb) ...
Setting up iscan-plugin-gt-f700 (2.1.0-3) ...

Processing triggers for libc6 ...
```
You can check the install with Synaptic, doing a search for iscan.
I also have sane and xsane installed. The scanner is doing everything I want it to.

---

### Post by avanrens on 2009-09-29
I'm just using VirtualBox and it works fine.

---

### Post by nEJC on 2009-10-23
> **cisk4me said:**
> I tried the product "Image Scan! for Linux" maintained by Avasys Corporation. I installed the package rather than compiling from source code.

Go to the link ...

Thnx for this info, got it working flawlessly.
All I needed to set was write permission on usb bus (or I could only run xsane thru sudo)

To see where scanner is attached use **lsusb**

```

nejc@traxi:~$ lsusb 
Bus 001 Device 008: ID 04b8:012f Seiko Epson Corp. Perfection V350 (GT-F700)
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 08ff:2580 AuthenTec, Inc. AES2501 Fingerprint Sensor
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 03f0:171d Hewlett-Packard Wireless (Bluetooth + WLAN) Interface [Integrated Module]
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

scanner was at bus 1, device 8 - so I did
```

nejc@traxi:~$ sudo chmod a+w /dev/bus/usb/001/008

```

Now I can scan again! :D

---

