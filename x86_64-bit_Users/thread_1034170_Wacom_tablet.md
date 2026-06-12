---
title: "Wacom tablet"
date: 2009-01-08
forum: x86 64-bit Users
---

### Post by demauk on 2009-01-08
I have followed every step in [Wacom Community Docs](https://help.ubuntu.com/community/Wacom) and every intruction has gone okay, and nothing was broken, but I still don't get my tablet working.

I'm going through option B, that is, through xorg.conf.

1. Installed the xorg drivers and wacom-tools both in version 8.1.6.
2. Plugged in the tablet.
3. lsusb correctly shows my tablet (graphire2)
4. Partial result from `ls -l /dev/input/` shows:

[INDENT]lrwxrwxrwx 1 root root         6 2009-01-08 00:01 tablet-graphire2-4x5 -> event6
lrwxrwxrwx 1 root root         6 2009-01-08 00:01 wacom -> event6
[/INDENT]

5. `grep -i wacom /var/log/Xorg.0.log` shows this:

[INDENT](II) config/hal: Adding input device Wacom Graphire2 4x5
(**) Wacom Graphire2 4x5: always reports core events
(**) Wacom Graphire2 4x5 device is /dev/input/event6
(**) Wacom Graphire2 4x5 is in absolute mode
(**) WACOM: suppress value is 2
(**) Wacom Graphire2 4x5: serial speed 9600
(II) XINPUT: Adding extended input device "Wacom Graphire2 4x5" (type: Wacom Stylus)
Wacom Graphire2 4x5 Wacom X driver grabbed event device
(==) Wacom using pressure threshold of 30 for button 1
(==) Wacom USB Graphire2 tablet speed=9600 (38400) maxX=10206 maxY=7422 maxZ=511 resX=2032 resY=2032  tilt=disabled
(==) Wacom device "Wacom Graphire2 4x5" top X=0 top Y=0 bottom X=10206 bottom Y=7422 resol X=2032 resol Y=2032
[/INDENT]

6. The relevant sections of my /etc/X11/xorg.conf file look *exactly* like the [Example Lines for /etc/X11/xorg.conf for Wacom]("https://help.ubuntu.com/community/WacomTroubleshooting") page (except I removed the lines about "pad" and "touch" InputDevices).
7. I hit Ctrl-Alt-Backspace, log in, and nothing. I've tried rebooting, too.

The tablet, mouse, and pen have all been tried in Windows and they work fine.

Any ideas would be greatly appreciated!

---

