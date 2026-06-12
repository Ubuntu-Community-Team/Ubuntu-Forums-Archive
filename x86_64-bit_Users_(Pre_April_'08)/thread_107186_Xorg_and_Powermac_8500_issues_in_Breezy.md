---
title: "Xorg and Powermac 8500 issues in Breezy"
date: 2005-12-22
forum: x86 64-bit Users (Pre April '08)
---

### Post by 8-bitDesigner on 2005-12-22
Okay, I've been trying to get Breezy working on an old G3 upgraded Powermac 8500 for a month or so, now, and after hours of troubleshooting and poking around, I've gotten it installed.

But the X server doesn't want to start.

So here's my question, can xserver-xorg work on a Powermac 8500's Control video card? I've done a dpkg-reconfigure xserver-xorg and twiddled with the settings a bit, but I can't get the X server to start up.

I'm using fbdev on the Powermac's internal video card with a 15'' Solarism LCD. When dpk-reconfigure asked me for PCI information, I just hit enter, I added 4096 when it asked about memory, and gave the default values for a 15'' LCD (1024x768x70 hz).

Also, I'm a bit of a linux n00b, so if someone could point me to the actual commands used to restart the X server, that would save me a lot of needless rebooting to test my settings. ;)

Cheers

---

### Post by linear on 2005-12-22
The command to restart Gnome would be:

sudo /etc/init.d/gdm restart

---

### Post by 8-bitDesigner on 2005-12-29
Okay, I've figured it out! For posterity (and should I ever need to reinstall) here's what's up:

First I did a "sudo dpkg-reconfigure xserver-xorg" and went through the configuration process. The kicker here, and why it wasn't working before, is that the Control onboard video for Mac 7500/8500 systems only seems to accept 15-bit color. So when it asks for colour depth during the install process, 8 and 15 seem to be valid, but anything else, and the Gnome Display Manager fails on boot.

Second, I had to configure the PCI bus correctly. It's covered everwhere else, but I'll run through it here. In the console, use "lspci" to scan your PCI bus. Apple's Control video shows up as an unrecognized video/VGA adapter. Find the PCI address of your video device and pay attention to the last three number pairs. Mine was "01:0b:00. Now, convert this to decimal and enter it in the form of "PCI:xx:xx:xx", which was "PCI:01:11:00".

When it asks you about video memory, just enter in kb the amount of video RAM you have. For the 8500 this will either be 2mb or 4mb which is 2048kb or 4096kb respectively.

Once I cleared that up, I restarted Gnome Display Manager and it started up perfectly.

---

