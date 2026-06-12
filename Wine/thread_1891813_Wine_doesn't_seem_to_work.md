---
title: "Wine doesn't seem to work?"
date: 2011-12-06
forum: Wine
---

### Post by Drowz0r on 2011-12-06
Hello there all

I've tried wine with steam games, DC Universe and a bunch of other things but it just doesn't seem to work? I've tried doing the emulate desktop thing as well to see if that would help, but even with hours of changing settings, the closest I could get was one game in steam, an old one (day of defeat) to boot up, allow me to shoot and look around but had no keyboard movement :/

Is this normal for wine? Is there something more suited to gaming? I'm in ubuntu 11.10 and on wine 1.3

Thanks

---

### Post by BC59 on 2011-12-06
Yes and No. 

Many apps are working but the majority no. 

You can check [here]("http://appdb.winehq.org/") in the database which ones are working and how they did it:

[http://appdb.winehq.org/](http://appdb.winehq.org/)

---

### Post by BC59 on 2011-12-06
Sorry I forgot to answer to the second question.

Wine is **a** solution to play games on Linux but it's not **the** solution.

Other solutions include to install Windows XP in a Virtual machine, like VirtualBox or VMware and play the games there.

Another one is to retain the Windows in a double boot scheme and use the dark side of your computer to play games.

---

### Post by bluexrider on 2011-12-06
I find the best solution is to run Oracle and boot XP in the VM

> **BC59 said:**
> Sorry I forgot to answer to the second question.

Wine is **a** solution to play games on Linux but it's not **the** solution.

Other solutions include to install Windows XP in a Virtual machine, like VirtualBox or VMware and play the games there.

Another one is to retain the Windows in a double boot scheme and use the dark side of your computer to play games.

---

### Post by |{urse on 2011-12-06
Virtualbox wont run halo but wine will, go figure. A lot of getting windows games to work on wine is finding the correct driver for your videocard or chipset. you may also find that disabling all desktop effects (specifically disabling compositing) will magically fix some "directx on wine" issues. Also try installing your games via winetricks (if they are on the winetricks install list) and be sure to grab any updates for wine. 

you can get winetricks with > sudo apt-get install winetricks then launch it with 
> winetricks

---

### Post by BC59 on 2011-12-06
> **|{urse said:**
> you can get winetricks with  then launch it with

When installing the last version Wine1.3, Winetricks is installed automatically.

---

### Post by |{urse on 2011-12-07
Right on, good to know :)

---

### Post by Ghouli on 2011-12-08
For older 2d games playing in Windows VM is quite useful, I've been playing Close Combat The Longest Day campaign with my little brother since spring with XP in VMWare (didn't work in VirtualBox). Close Combat series suffers from flickering menubars when played with Wine, but with VMWare, they run perfectly fine (tested 3-5 and all the remakes, these games rule). Also Hearts of Iron 2 and King of Dragon Pass are regulars on my virtual XP. :)

---

### Post by Dlambert on 2011-12-08
> **Drowz0r said:**
> Hello there all

I've tried wine with steam games, DC Universe and a bunch of other things but it just doesn't seem to work? I've tried doing the emulate desktop thing as well to see if that would help, but even with hours of changing settings, the closest I could get was one game in steam, an old one (day of defeat) to boot up, allow me to shoot and look around but had no keyboard movement :/

Is this normal for wine? Is there something more suited to gaming? I'm in ubuntu 11.10 and on wine 1.3

Thanks

Stupid question, but is your graphics driver installed?

---

### Post by Drowz0r on 2011-12-19
Hello there

Sorry for the lateness in my reply. Bit busy lately with Christmas. Thanks for all the replies so far guys.

Well my graphics driver seems to be installed? I do get an error or notification about my graphics accelerator is not turned on or something but the driver seems fine. Though I've no idea how I turn this on :/

Steam seems to install and run fine now but not the games within it. I'll try some others.

---

