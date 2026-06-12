---
title: "old mac?"
date: 2005-11-04
forum: x86 64-bit Users (Pre April '08)
---

### Post by oldmanstan on 2005-11-04
does anyone know if ubuntu would successfully run on one of those old powerpc macs, like vintage 1994 type stuff?

---

### Post by Rxke on 2005-11-05
probably not, these are so called 'old world' macs, and while it is often possible to get linux running on them, in most cases it involves a lot of internet searching for tweaks and way arounds. The Open Firmware stuff is often the biggest stumbling block in making the older Macs bootable, for starters... Then there is the 'issue' of Ubuntu needing fairly recent machines to run on (smoothly) esp. memory requirements... 
Say anything from the 'coloured' macs and more recent. Anyhow, I believe oldworld macs are not officially supported by Ubuntu, probably because they can't guarantee it will work...

---

### Post by autocrosser on 2005-11-05
If you are really set on running Linux on a early PPC unit, I'd look at YellowDog Linux (a RPM/Redhat distro)--also, Google for linux on the unit you want to run--some oldworld units are "sort-of" easy to setup--some require the blood from your left toe & two sprigs of Wolf's Bane:D

I've toyed with setting up a early 8100 (the 61 & "Pizzabox Performas"/7x/81 series) as a server (almost easy)--the 5x & some 6x Performa units are almost impossible to make work--the 85-8600/95-9600 series would be a fair bet along with the Beige G3's. YellowDog has a list & links to working/non-working series sites---

Best of luck--I still like the "old" units--spent thousands of hours working with them:D

---

### Post by jessecurry on 2005-11-06
[QUOTE=oldmanstan]does anyone know if ubuntu would successfully run on one of those old powerpc macs, like vintage 1994 type stuff?[/QUOTE]

I just got Ubuntu(5.04) up and running on a Beige G3, it was fairly painless... and knowing what I know now would be entirely painless. Granted, the Beige is from 1997, not '94, but they are relatively inexpensive if you wanted to buy one. If you are buying I'd recommend a B&W G3 since they can be had for under $50 on ebay.

There are some other distros that I've heard work well on the older hardware, I think that they all use BootX.

---

### Post by farruinn on 2005-11-06
You got a beige G3 to boot using quik? I would be interested to hear how you did it.  I've always had to use BootX on this model.

oldmanstan: What exact model are you looking at?

---

### Post by Rxke on 2005-11-07
Yes, details are always welcome. You might even go the whole mile and add it to the list of Ubuntu-able machines here: [http://ubuntuppc.info/](http://ubuntuppc.info/)

---

### Post by oldmanstan on 2005-11-07
[QUOTE=farruinn]oldmanstan: What exact model are you looking at?[/QUOTE]

It is a Performa 6214CD PowerPC.  Saw it lying in someone's trash and HAD to stop and pick it up.  Works just fine booting from the HD into MacOS and whatnot.  I am just recently beginning to collect old computers and parts so it was a nice addition, however, since it is fully functional I thought it might be fun to get some use out of it, even if it was just as a novelty.

Oh, ps, I was a year off on my guess of the year, I looked it up, this model was introduced in 1995, not 1994.

---

### Post by Rxke on 2005-11-07
Hmmm... 8Mb is not enough by far... 1Gb HD won't get you very far either, 75MHz: ouch ...
Even Yellow Dogs older 3.10 doesn't support it: [http://www.terrasoftsolutions.com/support/hardware/others.shtml](http://www.terrasoftsolutions.com/support/hardware/others.shtml) (Scroll down to the very bottom)

---

### Post by jessecurry on 2005-11-08
[QUOTE=farruinn]You got a beige G3 to boot using quik? I would be interested to hear how you did it.  I've always had to use BootX on this model.

oldmanstan: What exact model are you looking at?[/QUOTE]

No, I've been using BootX, I guess that it does kinda sound like I used something else... I wonder if it'd be possible to drop BootX, I might see if I have another HD laying around... maybe I could work on it.

To the OP: you may want to try mklinux or netbsd for that older machine.

---

### Post by pvz on 2005-11-08
You have a Nubus-mac, which makes things more complicated. For details on your model see:
[http://lowendmac.com/ppc/6200.shtml](http://lowendmac.com/ppc/6200.shtml)
Your best option is to run Debian on it, the latest Sarge is supported but only with a 2.4.x kernel.
See the Linux/PPC for Powermacs project page for more info on how to proceed: [http://nubus-pmac.sourceforge.net](http://nubus-pmac.sourceforge.net)
and of course my own site which is dedicated to various old computers running mostly Debian, and with quite a few old Macs between them :-)
[www.petrvz.net](www.petrvz.net)

Getting more memory would be your first priority, followed by a bigger HD. It could be a nice little file/webserver if you can get it going, probably not too much use as a desktop machine. Old hardware is fun, keep us posted about your progress..

---

### Post by Rxke on 2005-11-08
Whoa, pvz, that's serious nifty stuff you got there on your site! 8)

---

### Post by pvz on 2005-11-08
[QUOTE=Rxke]Whoa, pvz, that's serious nifty stuff you got there on your site! 8)[/QUOTE]

Thanks.. Space is becoming an issue, though :-P

---

### Post by oldmanstan on 2005-11-08
[QUOTE=pvz]and of course my own site which is dedicated to various old computers running mostly Debian, and with quite a few old Macs between them :-)
[www.petrvz.net](www.petrvz.net)

Getting more memory would be your first priority, followed by a bigger HD. It could be a nice little file/webserver if you can get it going, probably not too much use as a desktop machine. Old hardware is fun, keep us posted about your progress..[/QUOTE]

I will definitely post again when (and if) I can get it going.  Thanks for the advice!  Also, GREAT page you have there, I love old computers, somehow the old ones always seem classier (or something) than news ones.

---

### Post by xequence on 2005-11-08
[QUOTE=pvz]You have a Nubus-mac, which makes things more complicated. For details on your model see:
[http://lowendmac.com/ppc/6200.shtml](http://lowendmac.com/ppc/6200.shtml)
Your best option is to run Debian on it, the latest Sarge is supported but only with a 2.4.x kernel.
See the Linux/PPC for Powermacs project page for more info on how to proceed: [http://nubus-pmac.sourceforge.net](http://nubus-pmac.sourceforge.net)
and of course my own site which is dedicated to various old computers running mostly Debian, and with quite a few old Macs between them :-)
[www.petrvz.net](www.petrvz.net)

Getting more memory would be your first priority, followed by a bigger HD. It could be a nice little file/webserver if you can get it going, probably not too much use as a desktop machine. Old hardware is fun, keep us posted about your progress..[/QUOTE]

Your site is very cool. Ive always though old hardware was cool... Just the retroness of it. I am going to install some OS, not sure what, on my 70 mhz pentium with 16 MB RAM ;)

---

