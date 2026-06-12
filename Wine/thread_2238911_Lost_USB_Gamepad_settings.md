---
title: "Lost USB Gamepad settings"
date: 2014-08-10
forum: Wine
---

### Post by Heinrich_Evers on 2014-08-10
Okay, so about a week ago I had wine-1.7.25

 working fine and dandy with my gamepad controller support so I could play my Need for Speed games in Linux.

I really don't know what I may have done to break my gamepad support but I did install playonlinux and crossover as well as q4wine.

I'm not sure which one may have broken my previous gamepad settings so I'm posting here.

using wine control shows that I have no gamepads recognized by wine. They work in regular linux with my emulators.

Wine recognizes my USB keyboard and mouse.

when I do lsusb this is what displays:

Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 004: ID 1b1c:0c04 Corsair 
Bus 007 Device 003: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 007 Device 006: ID 041e:30da Creative Technology, Ltd 
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 0c0b:b157 Dura Micro, Inc. (Acomdata) 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 006: ID 124b:4d01 Nyko (Honey Bee) Airflo EX Joystick
Bus 005 Device 005: ID 045e:001e Microsoft Corp. IntelliMouse Explorer
Bus 005 Device 004: ID 124b:4d01 Nyko (Honey Bee) Airflo EX Joystick
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0bc2:3001 Seagate RSS LLC 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 011 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 010 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 009 Device 002: ID 1058:0748 Western Digital Technologies, Inc. My Passport 1TB USB 3.0
Bus 009 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub





I want to get both Nyko Honeybee devices to work with wine again.

Bus 005 Device 004: ID 124b:4d01 Nyko (Honey Bee) Airflo EX Joystick
and
Bus 005 Device 006: ID 124b:4d01 Nyko (Honey Bee) Airflo EX Joystick

UPDATE*

I did a demsg | grep 'AIRFLO' and this is the output I get.

[    3.848889] input: Honey Bee           AIRFLO              as /devices/pci0000:00/0000:00:13.0/usb5/5-3/5-3:1.0/input/input14
[    3.849054] hid-generic 0003:124B:4D01.0002: input,hidraw1: USB HID v1.00 Joystick [Honey Bee           AIRFLO             ] on usb-0000:00:13.0-3/input0
[144609.205524] usb 8-2: Product: AIRFLO             
[144609.213094] input: Honey Bee           AIRFLO              as /devices/pci0000:00/0000:00:06.0/0000:04:00.0/usb8/8-2/8-2:1.0/input/input24
[144609.213233] hid-generic 0003:124B:4D01.000C: input,hidraw5: USB HID v1.00 Joystick [Honey Bee           AIRFLO             ] on usb-0000:04:00.0-2/input0
[146735.427603] usb 4-1: Product: AIRFLO             
[146735.440652] input: Honey Bee           AIRFLO              as /devices/pci0000:00/0000:00:12.0/usb4/4-1/4-1:1.0/input/input25
[146735.440813] hid-generic 0003:124B:4D01.000D: input,hidraw5: USB HID v1.00 Joystick [Honey Bee           AIRFLO             ] on usb-0000:00:12.0-1/input0
[146747.066421] usb 4-2: Product: AIRFLO             
[146747.079476] input: Honey Bee           AIRFLO              as /devices/pci0000:00/0000:00:12.0/usb4/4-2/4-2:1.0/input/input26
[146747.079672] hid-generic 0003:124B:4D01.000E: input,hidraw1: USB HID v1.00 Joystick [Honey Bee           AIRFLO             ] on usb-0000:00:12.0-2/input0


wine control shows nothing, and wine control joy.cpl is completely empty
Can someone help me restore my wine gamepad functionality?

---

### Post by Heinrich_Evers on 2014-08-24
bump

---

### Post by Heinrich_Evers on 2014-09-14
Still not one type of suggestion to help me out with this problem? Man.....   It's not like I'm lazy, I scoured the winehq forum for hours looking for anything even close to the issue.

Well... So much for actual help, I'll just re-install Linux and it will work. I was really hoping to avoid this issue but removing and re-installing Wine doesn't help and neither does down-grading to wine 1.6.2.

Thanks guys.........

---

### Post by EuclideanCoffee on 2014-09-15
Why don't you just use PlayOnLinux next time? It configures wine settings for each virtual drive, making it possible to run 1.6.2 and 1.7.25 on one computer. It'll also install drivers for gamepad through a builtin library.

---

### Post by Heinrich_Evers on 2014-09-15
> **ruze said:**
> Why don't you just use PlayOnLinux next time? It configures wine settings for each virtual drive, making it possible to run 1.6.2 and 1.7.25 on one computer. It'll also install drivers for gamepad through a builtin library.

Because I want it to be executable from the XBMC Advanced launcher addon for an HTPC and to do this with playon I need to be able to launch the program with playon with a batch file.


Like this:

!#/bin/sh


cd /$HOME/.wine/drive_c/Program\ Files\ \(x86\)/Electronic\ Arts/Need\ for\ Speed\ Carbon/


wine nfsc.exe

My problem is that it worked like this before with no issues and I'm really trying to reset the default back to what it was that allowed the USB gamepad to be recognized by Wines default prefix.

[IMG]http://i1373.photobucket.com/albums/ag388/Heinrich_Evers/Screenshotfrom2014-09-15100323_zps37c47c5e.png[/IMG]

---

### Post by Heinrich_Evers on 2014-11-08
##############UPDATE#############

I solved my own issue after a long time reading and its a simple fix.

in Winetricks, dinput and dinput8 are known to cause issues with USB mouse support; however, they didn't mention anything about gamepads.

The Wine community suggests removing the prefix used to install the game causing the problem but I think this is overkill since simply editing the prefix in winecfg and removing dinput and dinput8 from the native *.dll library will fix the problem.

Kudos to me for not relying on playonlinux, having control over your prefixes and knowing what you build can be more helpful than relying on pre-made configs to do it for you. :cool:

---

