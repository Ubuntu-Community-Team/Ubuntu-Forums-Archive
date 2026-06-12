---
title: "very heavy trouble with Eps AcuLaser C1100"
date: 2009-03-20
forum: x86 64-bit Users
---

### Post by smiley_27 on 2009-03-20
hi there,

after two years i'  ve installed my system new. i've a 64bit machine and using ubuntu 8.10 64bit.
1 1/2 years ago i was contacted with gutsy gibbon (7.10 also 64bit). i've installed it and i was glad to change from win to linux. at that time i could install my printer (called in the title) and he printing like a charme. 
NOW, after my reinstall with intrepit 64bit i can't install my printer. i'  ve tried all the "how-to's" that i'  ve found in the internet ... the topic's in here, too.
but nothing makes my printer work. not even the DATA-LED is blinking. 
i' ve loaded down the drivers from avasys, installed them firstly by convert via ALIEN into *.tgz, then *.deb and then via dpkg and --force-architecture and "aa-complain cupsd" .. but the printer does not run. i'  ve tried to modify the "pstoalc110.sh" un the "/usr/bin/" folder ... the printer won' t run. i've tried to install the driver via source with c-m-mi but nothing' s going on. 
now my question to you .... is there anything that i've neglected? is there a trick in 8.10 to make this printer work?
i hope so much, that someone can help me. i'  ve tried so much, but nothing's work :(

at the last ... sorry for my english ... i know, that you are speak this language better than me - but i think you understand that, what i wrote.

regards from germany ... smiley

---

### Post by LowSky on 2009-03-20
Have you tried unplugging the printer and rebooting it.

---

### Post by ddales on 2009-03-22
I have a C900 and really had a hard time getting it to work.  The Drivers are not available and I had to use an opensource package from sourceforge.  You may be able to get it working with this since the 900 and 1100 are very similar.

[http://alc900-cups.sourceforge.net/](http://alc900-cups.sourceforge.net/)

---

### Post by a2z on 2009-03-22
I'm also new to Ubuntu. I'm running 8.10 64 bit. 
I just installed my Epson printer this morning. All while not hooked to the net. Luckily, I must have installed the right drivers from Synaptics Manager a few days ago. 
All I did was plug in the usb, power up the printer and Ubuntu found it right away! Try the CUPS drivers.

---

