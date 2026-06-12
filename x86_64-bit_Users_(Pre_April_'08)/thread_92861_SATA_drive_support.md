---
title: "SATA drive support"
date: 2005-11-20
forum: x86 64-bit Users (Pre April '08)
---

### Post by vansouza on 2005-11-20
Hi.. new to Ubuntu here.. it worked on my AMD64 with IDE drives but I bought a new pc... HPa1250n which has an AMD 64x2 chip and SATA drives... the install seems to hang right there... Can any one help... Thanks...  Van

---

### Post by vansouza on 2005-11-20
I ran the install again and it haults at this point:
Running /etc/hotplug/usb.rc

So I guess it is not the SATA drives... still need help however...:confused:

---

### Post by adeh on 2005-11-21
Are you doing a clean install? Is there something remarkable about your USB subsystem? Most likely that line is not really the problem, but something deeper is causing instability.

---

### Post by joris.brus on 2005-11-22
I have a sata drive.. no problems here.
That really sucks.. I know the feeling.. I had a similar issue which turned out to be that my burned ubunty image was corrupt. (shitty cd)

---

### Post by megamania on 2005-11-23
[QUOTE=joris.brus]I have a sata drive.. no problems here.
That really sucks.. I know the feeling.. I had a similar issue which turned out to be that my burned ubunty image was corrupt. (shitty cd)[/QUOTE]

Almost same thing here: I was going crazy and then found out that my cd reader (not the cd itself) was breaking down...

---

### Post by vansouza on 2005-11-23
The CD was sent to me by Ubuntu... actually they sent 5 CDs... the computer is not even a week old so I think it is not the CD drive or the CD media... any other suggestions... I have a USB mouse if that causes issues... Thanks... Van

---

### Post by trinaryouroboros on 2005-11-24
[QUOTE=vansouza]The CD was sent to me by Ubuntu... actually they sent 5 CDs... the computer is not even a week old so I think it is not the CD drive or the CD media... any other suggestions... I have a USB mouse if that causes issues... Thanks... Van[/QUOTE]

If you are using any USB devices, the obvious approach would be to disconnect them entirely since it seems to get hung at the hotplug subsystem. 

This shouldn't have anything to do with the SATA drive itself, unless of course if you have SATA RAID setup - in which case follow these instructions:

[https://wiki.ubuntu.com/FakeRaidHowto](https://wiki.ubuntu.com/FakeRaidHowto)

If your keyboard and/or mouse are connected via USB, I would suggest trying to borrow someone's ps/2 mouse and keyboard, or get your own for the sake of troubleshooting or upgrading in the future (they're usually dirt cheap for ps/2 standard keyboards and mice).

I've had issues intermittently with USB devices when trying to install even Windows XP, so it's your best bet to borrow a PS/2 mouse for testing. At worst case scenario, you may have to disable the USB support from the BIOS itself during the startup of your computer.

Also, you technically do not need the mouse to install Ubuntu - however, you will want a mouse to obviously navigate Gnome or KDE, etc. when it's installed. 

**You could try to install without the mouse, and then try shutting it completely down, unplugging the power cord for 15 seconds from the back of the computer, plugging in the USB mouse, and starting up the computer again.**

If that doesn't do the trick, then all you'll get is a USB Device error during your bootup process, in which case you may need to go further in regards to troubleshooting if you want to use the USB mouse with Ubuntu, although I believe this is a rare problem.

The biggest problem I've seen, if anything, is just simply getting USB External Harddrives and Game controllers past the hotplug subsystem. The rule of thumb is that some USB equipment powers off of the USB port, as well as maintains it's connection data-wise even well after shutting down the computer from the operating system level. Usually, if a problem happens where the USB Device is unknown to the loading operating system, you can try the unplugging trick mentioned above to resolve the issue.

One step at a time.

---

### Post by knowmad on 2005-11-25
This PC has one of those multi card readers w/ usb, right?  For arguments sake, try to unplug that... then try the install.  Let us know how this goes!

---

### Post by mgmiller on 2005-12-06
1 other thing you can try is disabling legacy USB support in your BIOS.  I do this in my AMD64 3200+ Breezy box and I even do this for my WinXP boxes to improve USB reliability.

---

