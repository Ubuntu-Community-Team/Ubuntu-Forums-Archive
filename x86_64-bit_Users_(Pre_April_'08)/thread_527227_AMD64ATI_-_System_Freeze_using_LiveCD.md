---
title: "AMD64/ATI - System Freeze using LiveCD"
date: 2007-08-16
forum: x86 64-bit Users (Pre April '08)
---

### Post by zjd on 2007-08-16
Hi,

I've been trying to use Ubuntu for a few versions now but I keep having some problems. I think I've narrowed down my exact problem so hopefully we can figure out what's wrong! My system is as follows:

AMD64 3200
1GB Dual Channel DDR
ATI Radeon X800XL PCI-E
160GB IDE
350GB SATA

Since 6.04 I have tried using the LiveCD w/ Ubuntu, Kubuntu, and Xubuntu and always experience the same problem. I use the i386 regular version. To boot I have to use "irqpoll pci=noacpi noapic nolapic acpi=off" because I am on an AMD64. 

The problem is once in the desktop environment everything seems to freeze. By freeze I mean I cannot move the mouse or use the keyboard. Ctrl+Alt+Backspace will just get rid of everything on the desktop except for the background. No X restart at all. I have also tried Ctrl+Alt+F1 to get to a command line but that does not work either. The only way to get out is to do a hard reset BUT unlike normal hard resets which take 4-5 seconds to shut down, the system shuts down immediately. The mouse freeze occurs randomly I believe. It has happend within 10 seconds of booting up and I have been fine for as long as 10 minutes. But it always happens.

From reading other posts I imagine I may have to mess around with my xorg.conf and the ATI drivers. I am capable of that but I don't really know what I am looking for or how to further diagnose my problem. I am also limited because I have just been trying this out on the LiveCD. I'm not even sure if you can change drivers on that.

If anyone has any ideas that would be great or if you need more information let me know.

Thanks!

---

### Post by borodark on 2007-08-16
Try Ctrl-Alt-F8 and only then Ctrl-F1

---

### Post by zjd on 2007-08-16
Update:

I decided to install Ubuntu. I immediately switched to the Vesa driver and everything seemed to be working well and I set my personal record for longest up-time using Ubuntu (almost 30 minutes, previous best was under 10). 

I did notice something though. While using Firefox I got the usual freeze. But I noticed that my keyboard was still responding and the webpage finished loading! I could navigate the page using the keyboard. Still something more than my mouse is messed up. Restarting X still didn't work and Ctrl+Alt+F1 just takes me to a black screen with nothing on it. 

Hope this helps.

---

### Post by dabl on 2007-08-16
The fact that Ctrl-Alt key combinations seem not to work suggests there is something non-standard in your keyboard design.  The xorg configuration script ```
dpkg-reconfigure xserver.xorg
``` has a lot of flexibility to configure special keyboards, although the very newest products may not be represented.

In other words, if Ctrl-Alt-Backspace does not restart the X server, and Ctrl-Alt-F1 does not provide a console for CLI login, then there is clearly something amiss with the Ctrl or the Alt keypress output.

:)

---

