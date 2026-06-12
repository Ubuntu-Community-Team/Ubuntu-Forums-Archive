---
title: "Genreally slow performance (especially scrolling)"
date: 2009-01-28
forum: x86 64-bit Users
---

### Post by lilbill on 2009-01-28
Hi all
I have Ubuntu 8.10 64 bit installed clean on a new hdd.  My specs:
AMD Athlon 5800+ X2
Corsair DDR2 800 2Gb
Foxconn MB with AMD 780 chipset
ATI Radeon 3200HD integrated graphics 

I experience generally slow performance throughout the system.  The most notable times are when I do GUI stuff like moving a window (there is a cpu usage spike, one core goes up to 50%).  Scrolling through anything is painful.  Firefox is barely useable.  I tried Opera, while faster it is still very slow and choppy redrawing noticably (excessive processor usage here too!) even simply viewing text or a page source. 

I have a couple screenlets and have the desktop effects on Normal with no special compiz features enabled.

I have installed the chipset drivers 8.12 straight from ATI(I think I did this properly, maybe not) but that is no help.

Computational tasks run in Maple are fine and compilation is nice and fast.

Any help would be greatly appreciated!!
It really feels like the processor is taking the brunt of the gpu's duties.  Is mine underpowered or what else should I check...my Windows installation on this machine is much more responsive.

~lilbill

---

### Post by utnubuuser on 2009-01-28
Yeah,  kinda unusual.  With those kinds of system specs, your machine should be screamin' along.
Can't really offer help, 'cause my system is very Plain-Jane and my configuration experience is equally unsophisticated.  But from all the posts I've read,  I'd right away start looking for another driver for the ATI card. And look for postings related ot ATI cards.
Good luck.

---

### Post by lilbill on 2009-01-28
Yeah that's what I thought...I've tried the drivers from apt and this one from ati and neither made an improvement.  I'll keep looking! Thanks!
Is it normal that these kind of things(visual like scrolling, viewing websites and guis) are slower than in windows?

---

### Post by lilbill on 2009-01-31
bump for my slow UI performance

---

### Post by thriftee on 2009-01-31
Since nobody else answered, I'd try reinstalling all the ATI video drivers (via synaptic) and then restarting the system.

I had the same problem with my dual nvidia cards, and that's what finally solved it.  My Firefox screens were scrolling so slow I could watch them move about 3 lines at a time every second or so.

I'm a noob with ubuntu and linux so I'm only answering because I had similar troubles and you didn't get any suggestions from the experts.

PS: it looks like you installed drivers directly from ATI.  I think I'd --uninstall them and use native drivers specifically set up for ubuntu.  That should be best if you have the option.

PSS: I just looked, and its not like nvidia where we have the option of using native drivers setup for ubuntu.  I guess that means you either need to run the xorg ones or the code directly from ATI like you installed.  LOL, I'll learn more when my dual Radeon 7000 VE arrives next week.

---

### Post by lilbill on 2009-02-02
Thaks for the advice...I reinstalled the drivers once but I will try again.  [-o<
Good luck with the 7000 VE

---

### Post by tkmn on 2009-02-03
Hi.

I use Ubuntu 8.04 64 bit on a system with 780G graphics.

I had the same problem as you with the ATI drivers that came with 8.04. Installing the 8.12 drivers solved the problem for me.

If nothing else works you could try the new 9.1 drivers.

[http://ati.amd.com/support/drivers/linux64/linux64-radeon.html](http://ati.amd.com/support/drivers/linux64/linux64-radeon.html)

---

### Post by lilbill on 2009-02-04
I'll check those out tkmn...thanks

---

### Post by lilbill on 2009-02-04
Thanks for the heads up on the new drivers!  There has been a noticeable performance increase.  The problem remains but is diminished (even in Firefox!!!)

---

### Post by Doc Hoss on 2009-02-06
I just built a new 64bit box and am having the same problem...but I have integrated Nvidia graphics.  Maybe not the graphics card then?  Anyone else have ideas what could be causing this?  

Brand-spanking new fresh install, just running sluggish and one core or the other (of dual core proc) sitting around 45-50 percent use.  "top" says it's Xorg that's eating up cycles.  That help?

---

### Post by lilbill on 2009-02-06
Glad to see I'm not alone...not glad that you have problems just that I didn't screw up the build/install.  Any ideas folks?

---

### Post by milesinnz on 2009-02-07
Yep, same problem here.

AMD X2 6000 and as I sit here typing this, one processor is at 100% usage!

yet there is nothing in the process list which is showing anything over 5%?

opps, and now the processor which was running at 100% has dropped back and the other is now 100%

I am sure this problem was not there on my original 8.10 install - so maybe it has to to with some update???

current kernel is 8.6.27-7

---

### Post by milesinnz on 2009-02-07
Using the command (line) TOP (CPU usage) Xorg is at the top. It is near 100% when monitor is running, when I close monitor, Xorg drops to below 10%

The application "monitor" certainly seems to cause Xorg some grief! and thus it is difficult to confirm just what is going on as monitor seems to cause a lot of the trouble.

---

### Post by theadmira1 on 2009-02-07
core i7 and Asus 4870X2 with dual Asus 21.5 screens... the rig is no slouch and i have the exact same problem... i have tried uninstalling and reinstalling 4 different drivers... the ati catalyst from amd/ati worked but only for a week then it went back to this junk... the only setup i can get working right now is the proprietery driver run by catalyst and quite frankly its worthless for over $1500 in parts...

---

### Post by lilbill on 2009-02-08
Bump...any ideas on things we should check?

---

### Post by milesinnz on 2009-02-09
I recently installed 8.10 and using NVIDIA onboard video and the NVIDIA drivers. I had the problem of poor scrolling performance (impossible to use really). I wrestled for a long time with the drivers, got myself in a real mess, reinstalled the system again and have not had any trouble at all.

Like they say, go figure.

But be aware, I seem to have a problem with "monitor", it will use 100% of one of the processors, so I am not using monitor until there is some sort of fix.

I use "top" from the command line.

---

### Post by theadmira1 on 2009-02-11
so i just reinstalled the new 9-1 driver from ati... but i did it all command line via sudo su... everything is workin awesome!! no slow refresh or any of that!!

---

### Post by lilbill on 2009-02-11
Congrats!!  It made some good improvements here too.

---

### Post by lilbill on 2009-02-28
Sorry to revive this...but I've just installed KDE to try it out and the problem scrolling is much less, especially in firefox.  Maybe the problem resides with Compiz.

---

