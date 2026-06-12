---
title: "What does these errors mean?"
date: 2005-12-12
forum: x86 64-bit Users (Pre April '08)
---

### Post by spencer on 2005-12-12
Hi, I have Ubuntu Breezy installed on a Power Mac G4. When Ubuntu is booting, I get the following errors:

```
Invalid Rom signature 1111 should be oxaa55.
```

I have a few of the following regarding the insmod but will use one for now.

```
Insmod: Can't read '/lib/modules/2.6.12-9-Powerpc/kernel/drivers/video/console/bitblit.ko' No such file or directory.
```

What do these errors mean? 

Also, When I make it to the desktop Ubuntu doesn't see my Macally USB mouse. It works if I unplug it and reattach. How can I fix that? 

Thanks!

-spencer

---

### Post by Rxke on 2005-12-12
Errors are no big deal, I think, the f last ones i have too since going from Hoary to Breezy, but it looks like nothing is affected by it (but I'm not doing much graphical stuff) I'm on a G3 BTW....

---

### Post by ssam on 2005-12-12
i think most people get that top error message, i can't remeber the reason for it, but you don't need to worry.

not so sure about the second one, but if everything works fine i would not worry.

as for the mouse. can you post the last few lines of the output of
```
dmesg
```
after pluggin the mouse in.
(if you run dmesg first, remember the last line, plug in mouse, run it again, and post what ever is new.)

---

### Post by spencer on 2005-12-12
Nothing seems to be affected Ubuntu runs fine, I'm just curious. As far as the output I get with 'dmesg', here it is:

```
s Inc Rage 128 PF/PRO AGP 4x TMDS
[  127.541508] agpgart: Putting AGP V2 device at 0000:00:0b.0 into 1x mode
[  127.541530] agpgart: Putting AGP V2 device at 0000:00:10.0 into 1x mode
[  132.270780] Bluetooth: Core ver 2.7
[  132.270813] NET: Registered protocol family 31
[  132.270822] Bluetooth: HCI device and connection manager initialized
[  132.270852] Bluetooth: HCI socket layer initialized
[  132.363591] Bluetooth: L2CAP ver 2.7
[  132.363612] Bluetooth: L2CAP socket layer initialized
[  132.429330] Bluetooth: RFCOMM ver 1.5
[  132.429366] Bluetooth: RFCOMM socket layer initialized
[  132.429397] Bluetooth: RFCOMM TTY layer initialized

```

Thanks

-spencer

---

