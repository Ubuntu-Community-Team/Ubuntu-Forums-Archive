---
title: "Rosetta stone 3.4.5 + wine, microphone not detected."
date: 2011-11-03
forum: Wine
---

### Post by firefish5000 on 2011-11-03
Hi (standard greeting), I have installed Rosetta stone and am having trouble getting the mic to work.(I know im not alone, but I have not found a fix that works with me)
I installed it using playonlinux, and have tried many different versions of wine in hopes of getting it to work. (1.3.30; 1.3.19; 1.3.11; 1.3.8; 1.2.3; 1.2.1; 1.2; 1.1.38)
I am running Ubuntu 11.10 with the gnome shell, I dont know what else to put if you think you know what to do to fix this or how to obtain information I need to tell you in order for you to help me further than please tell me. Thanks!

---

### Post by sir.hairo on 2011-11-09
1.3.15 works for me, while not any later :(

Keep older deb package :)

---

### Post by neosk8 on 2012-04-03
I got the same problem:

I can install, Update, load language but no mic detected...

Dell Studio 1356 with Uby11.10

---

### Post by gordintoronto on 2012-04-03
Can you record sound from the mic using Audacity? Sometimes these things have nothing to do with Wine.

---

### Post by neosk8 on 2012-04-04
of course I do.

Skype,audiacity  ecc ecc.

---

### Post by neosk8 on 2012-04-05
any tips?

---

### Post by oicacid on 2012-04-17
Went from windows to Ubuntu because of this rosetta stone DL, after days I got the application to work and load a language yet experienced the microphone issue as everyone else has. What finally worked for me was removing Wine 1.3 and the Beta release and installing Wine 1.2 using Ubuntu Software center. Microphone was recognized in the application just fine and works like a jiff-make sure to restart after uninstall and install. My solution I'm sure its not for all. 

Plug in microphone
Ubuntu 11.10
Rosetta 3.4.5 
Wine 1.2

---

### Post by MMagoo1 on 2012-07-01
Best Solution is here ;) Trust me: [http://askubuntu.com/questions/77210/how-to-change-the-default-audio-in-wine-to-alsa-only](http://askubuntu.com/questions/77210/how-to-change-the-default-audio-in-wine-to-alsa-only)

Just change Wine to Alsa and everything works fine.

---

### Post by ervinjn on 2013-05-12
I'm having the same problem.  I bought Rosetta Stone.  It opens fine in Wine, and I can hear just fine.  But the microphone doesn't work.
I ran winetricks from the command line and changed the sound to Alsa, as suggested.  Still, not working. Any ideas?  Thanks.
I'm also new to Linux.

---

### Post by neosk8 on 2013-05-12
vitualbox and win 7.


just my solution

---

### Post by Idahed on 2014-01-24
Hi.  I agree with neosk8;  use Oracle Virtual Box rather than Wine.  But be sure to select the ALSA sound engine in your Linux sound settings.  Also, be aware that Virtual Box/Win 7 can be a bit slow, but if you want to do Rosetta Stone, it's the only way I've been able to get the mic to work.  Also, rather than use the disc installation, use Rosetta Stone Totale, on line.  Yeah...it's $10/mo. but probably worth it.  Hope this helps y'all.

---

