---
title: "white ibook g3 700 MHz internal modem?"
date: 2005-10-20
forum: x86 64-bit Users (Pre April '08)
---

### Post by Xappe on 2005-10-20
Hi,

I'm trying to figure out what type of modem I have in my ibook g3 (2 rev.2). So far without any luck. I hope someone here could give me some suggestions. 

lspci gives:
```
jon@ibook:~$ lspci
0000:00:0b.0 Host bridge: Apple Computer Inc. UniNorth/Pangea AGP
0000:00:10.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M6 LY
0001:10:0b.0 Host bridge: Apple Computer Inc. UniNorth/Pangea PCI
0001:10:17.0 ff00: Apple Computer Inc. KeyLargo/Pangea Mac I/O
0001:10:18.0 USB Controller: Apple Computer Inc. KeyLargo/Pangea USB
0001:10:19.0 USB Controller: Apple Computer Inc. KeyLargo/Pangea USB
0002:20:0b.0 Host bridge: Apple Computer Inc. UniNorth/Pangea Internal PCI
0002:20:0e.0 FireWire (IEEE 1394): Apple Computer Inc. UniNorth/Pangea FireWire
0002:20:0f.0 Ethernet controller: Apple Computer Inc. UniNorth/Pangea GMAC (Sun GEM)

```

lsusb:
```
jon@ibook:~$ lsusb
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 002: ID 1241:1177 Belkin F8E842-DL Mouse
Bus 001 Device 001: ID 0000:0000

```

Can't figure out where the modem is... (it should be there).
I even tried to install the linuxant hcfusb driver, but it returned "device not found"

Any help would be appreciated.

---

### Post by zenlunatic on 2005-10-20
I'm pretty sure its not a hardware modem if thats what you were wondering.  Last I heard their was non-free kernel patches (binary) for getting this modem operable under Linux.

---

### Post by Xappe on 2005-10-20
i've heard that it should be some type of conexant software modem (that's why I tried the linuxant drivers...I read somewhere that newworld ibook g3 should have the hcfusb modem). but shouldn't it be listed somewhere even though I don't have drivers/modules for it?

---

### Post by rapunzel on 2005-10-22
You will see the modem with lspci or lsusb only once it's initialized. For that you need the driver hcfusb from linuxant. But it's not very stable. I was able to install it and connect to the internet, but got a freeze when I tried to unload the driver or shut down the computer.

---

### Post by Xappe on 2005-10-23
I ended up with a "device not found" when trying the hcfusb driver as stated in the first post... :/

---

### Post by rapunzel on 2005-10-24
I followed the instructions on this page:

[http://www.terrasoftsolutions.com/support/solutions/ydl_2.3/winmodem.shtml](http://www.terrasoftsolutions.com/support/solutions/ydl_2.3/winmodem.shtml)

If I remember right I got something like 'device not found' too, after I did the MAKE INSTALL, I tried the command again (don't remember if the message came up once more) and after that the device could be found with lsusb.

---

