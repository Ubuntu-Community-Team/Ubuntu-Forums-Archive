---
title: "Blank Screen at boot"
date: 2007-08-12
forum: x86 64-bit Users (Pre April '08)
---

### Post by nicktheawesome on 2007-08-12
I have looked around on the forum, and I've found similar problems. I've tried their solution and it doesn't seem to work.

I have a PNY nvidia 8800gts (640 MB), Acer AL2216W (1680x1050) running through DVI, a second monitor-Dell CRT Trinitron-19" running out of a DVI port through a DVI-VGA converter, 64 bit Fiesty.

My computer used to boot up. It would only run 1024x768 or lower resolution, so I am working on fixing that. I did the sudo dpkg-reconfigure xserver-xorg a few times and now all I get is a blank screen during boot, and thats all it does. I can boot into recovery mode, but I can't really use the command line.

My end goal is to have  dual monitor setup with the Acer being the primary. Any help would be appreciated. I tried to include as much information as possible about the problem but I don't really know where to start.

Another problem I'm having, although far less important is having no sound. I get sound when I run windows XP, but not with Ubuntu. I used to have a Sabayon install, and that had the correct resolution and everything, but it was too cluttered for me. 

Thanks guys.

Other system info if it helps:
Intel Core 2 Quad Q6600
Evga Nvidia 680i Mobo
4 gigs RAM
PNY nvidia Geforce 8800GTS (640 MB)
WD 10k RPM Raptor 150 GB
Ultra 800 Watt power supply

---

### Post by buckrodgers on 2007-08-13
Ubuntu bheaves a bit silly if it is unhappy of the /etc/X11/xorg.conf settings,

in recovery mode look in your /var/log/ the logfile for Xorg and search for any line starting with (EE)...  which will tell you the error.

To get dual screen you need to get the Nvidia drivers, you can go there for the method

[http://www.robdian.co.uk/content/view/56/](http://www.robdian.co.uk/content/view/56/)

cheers

---

### Post by nicktheawesome on 2007-08-13
Hey thanks!

---

