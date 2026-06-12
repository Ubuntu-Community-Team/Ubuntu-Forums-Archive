---
title: "Updated today and now the Mouse doesn't work"
date: 2009-09-09
forum: x86 64-bit Users
---

### Post by jkonrad on 2009-09-09
I'm 9.04 x64 on a simple AMD plateform. I have been using the machine daily for about 3 weeks. Everything is working very well.

However, today I suddenly have an unstable system. It appears like the mouse is lagging? It's hard to explain. Sometimes I click and nothing happens. Then it might activate a different part of my screen. The keyboard seems fine, but the mouse is completely hit or miss. The cursor moves as it should, but clicking or scrolling does not work.

The only difference today is update-manager asked to install updates and I clicked "yes". Now, the system is broken. I'm not even sure what updates were installed. I've been updating every time it's asked, so what it installed would be what was released today.

If anyone knows a bit more about this kind of error, but needs more info, please ask. I'll try to figure out how to navigate to a terminal and dig out stuff from there. Very odd. I was really enjoying this OS

---

### Post by ajgreeny on 2009-09-09
You can tell what was updated in Update Manager by opening synaptic and going to File > History.

On my system there was the following:-

Upgraded the following packages:
gnome-terminal (2.26.0-0ubuntu2) to 2.26.0-0ubuntu2.1
gnome-terminal-data (2.26.0-0ubuntu2) to 2.26.0-0ubuntu2.1
libpam-modules (1.0.1-9ubuntu1) to 1.0.1-9ubuntu1.1
libpam-runtime (1.0.1-9ubuntu1) to 1.0.1-9ubuntu1.1
libpam0g (1.0.1-9ubuntu1) to 1.0.1-9ubuntu1.1
sun-java6-bin (6-14-0ubuntu1.9.04) to 6-16-0ubuntu1.9.04
sun-java6-jre (6-14-0ubuntu1.9.04) to 6-16-0ubuntu1.9.04
sun-java6-plugin (6-14-0ubuntu1.9.04) to 6-16-0ubuntu1.9.04

I see no reason why these should cause any problem, but perhaps you had other things as well.

---

### Post by jkonrad on 2009-09-09
My mouse will let me navigate as far as showing the History screen, but I cannot in anyway activate the scroll bar so all I see is;

gnome-terminal (2.26.0-0ubuntu2) to 2.26.0-0ubuntu2.1
gnome-terminal-data (2.26.0-0ubuntu2) to 2.26.0-0ubuntu2.1
libpam-modules (1.0.1-9ubuntu1) to 1.0.1-9ubuntu1.1
libpam-runtime (1.0.1-9ubuntu1) to 1.0.1-9ubuntu1.1

Oh, wait, I can tab over and use the arrow keys. Looks almost the same, so the list would finish with

libpam0g (1.0.1-9ubuntu1) to 1.0.1-9ubuntu1.1
sun-java6-bin (6-14-0ubuntu1.9.04) to 6-16-0ubuntu1.9.04
sun-java6-jre (6-14-0ubuntu1.9.04) to 6-16-0ubuntu1.9.04

It does not show the sun-java6-plugin update. I can't see how that would affect anything.

Also, I'm not even sure it was the update that "broke" the system. It's the only thing different today from yesterday, that's all. I've tried changing mice. I've restarted lots. I don't even know where to begin.

Can I uninstall all things related to the mouse and re-install them?

---

### Post by jkonrad on 2009-09-09
I think it's hardware. As in, my mainboard. I was using a usb mouse (or mice). Now I'm using a ps2 mouse and it's working. Something must have happened to my usb. So, nothing with the update and nothing with ubuntu. Sorry, I don't usually suspect hardware, but since it's working perfectly now and before was randomly failing I must suspect the hardware.

Thanks to those who gave it some thought.

---

### Post by cenit1 on 2009-09-16
I have the same problem with the mouse and I see that the day before I had many updates, and I have in common the same than you.

gnome-terminal (2.26.0-0ubuntu2) to 2.26.0-0ubuntu2.1
gnome-terminal-data (2.26.0-0ubuntu2) to 2.26.0-0ubuntu2.1
libpam-modules (1.0.1-9ubuntu1) to 1.0.1-9ubuntu1.1
libpam-runtime (1.0.1-9ubuntu1) to 1.0.1-9ubuntu1.1
libpam0g (1.0.1-9ubuntu1) to 1.0.1-9ubuntu1.1
sun-java6-bin (6-14-0ubuntu1.9.04) to 6-16-0ubuntu1.9.04
sun-java6-jre (6-14-0ubuntu1.9.04) to 6-16-0ubuntu1.9.04
sun-java6-plugin (6-14-0ubuntu1.9.04) to 6-16-0ubuntu1.9.04

I reboot the system several times... and I had always problems with the mouse when I start Vuze, and I think that Vuze is making problems with the mouse. **Please, try to repeat this in your computer with any Java program**... because maybe that's the problem.

My mouse is labtec and is wireless... and I had other problems with it, but... now... it's automatic... Just start Vuze... and the mouse start to don't click... but the right click sometimes works!!!

Cenit

---

### Post by jkonrad on 2009-09-16
Well, I can't get my mouse to fail now. Before it would do so all the time. I've run a few java applets would that count? 

Just for kicks, try putting the usb receiver in an entirely different port and let me know if that changes anything.

I have since been able to get my usb mouse working again, but on a different motherboard header. So any of the four usb ports hooked into the original usb header would not work, but changing to a different set (like on the back) worked just fine. Very strange.

---

### Post by cenit1 on 2009-09-16
Oki... I suppose that if you change your mouse to a different USB port and now it's working... it's because is a different problem. 

I tried everything... I change the USB port... I connect another USB mouse, and now with the PS2 mouse... at the same time of the USB... it's working weel.

I'll try more options on the next reboot.

Thanks anyway for your time!

---

### Post by jkonrad on 2009-09-16
I think I do have a different problem, but did you say the ps/2 mouse is working well? That might point to a different problem too.

Remember, four of my ports went "bad" after the update. I think I had a hardware failure, but changing to a different usb header (like front ports instead of back ports) did fix the issue I was having.

Sorry I can't help.

---

