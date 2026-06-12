---
title: "svideo?"
date: 2006-04-15
forum: x86 64-bit Users (Pre April '08)
---

### Post by davidmaxwaterman on 2006-04-15
I'm using ubuntu on my Titanium Powerbook G4/800 DVI. I think it has an ATI card (says Radeon Mobility M7 LW in the 'device manager').
Edit:actually, /var/log/Xorg.0.log says :

```
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Color LCD"
(**) |   |-->Device "ATI Technologies, Inc. Radeon Mobility 9000 (M7 LW)"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(**) |-->Input Device "Synaptics Touchpad"
...
(--) PCI:*(0:16:0) ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500] rev 0, Mem @ 0xb8000000/27, 0xb0000000/16, I/O @ 0x0400/8, BIOS @ 0xf1000000/17
```

So, I'm not sure what to make of that...

I want to play some movies onto my TV using the svideo output. Worked fine on OS X.

Is there a way to make the svideo work?

Max.

---

### Post by gerbman on 2006-04-16
[QUOTE=davidmaxwaterman]I'm using ubuntu on my Titanium Powerbook G4/800 DVI. I think it has an ATI card (says Radeon Mobility M7 LW in the 'device manager').
Edit:actually, /var/log/Xorg.0.log says :

```
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Color LCD"
(**) |   |-->Device "ATI Technologies, Inc. Radeon Mobility 9000 (M7 LW)"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(**) |-->Input Device "Synaptics Touchpad"
...
(--) PCI:*(0:16:0) ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500] rev 0, Mem @ 0xb8000000/27, 0xb0000000/16, I/O @ 0x0400/8, BIOS @ 0xf1000000/17
```

So, I'm not sure what to make of that...

I want to play some movies onto my TV using the svideo output. Worked fine on OS X.

Is there a way to make the svideo work?

Max.[/QUOTE]Have you installed the fglrx drivers for your ATI card? If not, try [this]("http://wiki.cchtml.com/index.php/Ubuntu_Installation_Guide") guide. Then run ```
sudo fglrxconfig
```to generate your xorg.conf file. This has successfully set up s-video output on my ATI 9500 and x600 video cards, and I think your card is supported as well.

---

### Post by davidmaxwaterman on 2006-04-16
[QUOTE=gerbman]Have you installed the fglrx drivers for your ATI card? If not, try [this]("http://wiki.cchtml.com/index.php/Ubuntu_Installation_Guide") guide. Then run ```
sudo fglrxconfig
```to generate your xorg.conf file. This has successfully set up s-video output on my ATI 9500 and x600 video cards, and I think your card is supported as well.[/QUOTE]

Everything I can find about fglrx suggesting it is x86 and x86_64 only; not for powerpc. Are you running it on PowerPc? If so, where can I get the driver from - it doesn't seem to be in any of the repositories I have set up...

Max.

---

### Post by gerbman on 2006-04-16
[QUOTE=davidmaxwaterman]Everything I can find about fglrx suggesting it is x86 and x86_64 only; not for powerpc. Are you running it on PowerPc? If so, where can I get the driver from - it doesn't seem to be in any of the repositories I have set up...

Max.[/QUOTE]Oh sorry, you're right. I'm on x86. Whoops :-k

---

