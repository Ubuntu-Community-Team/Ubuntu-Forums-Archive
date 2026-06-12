---
title: "minimac, radeon 9200, dri and xorg.conf"
date: 2006-01-16
forum: x86 64-bit Users (Pre April '08)
---

### Post by ashigabou on 2006-01-16
Hi,

I am happily using ubuntu on my minimac for almost one year, now. But recently, I noticed that xorg is not using direct rendering: as I would like to use a software which uses openGL, I need dri for acceptable performances.

I am using the ati graphic driver in xorg.conf, I am loading the dri module, but somewhat, glxinfo tells me that I am using indirect rendering. Where should I look to get direct rendering ?

---

### Post by Teroedni on 2006-01-18
since you have the 9200 
You should get the open source radeon driver

By the way:
How does the minimac works in Ubuntu 5.10?
Wants one myself:D

---

### Post by qball on 2006-01-19
[QUOTE=Teroedni]since you have the 9200 
You should get the open source radeon driver

By the way:
How does the minimac works in Ubuntu 5.10?
Wants one myself:D[/QUOTE]

There are 2 good things about the mini:
* It's quiet. you can leave it running during the night withouth keeping you up.
* It's small.

But It's alot of money for a small (low end) system. (I had a complete 64bit system for alot less).  And for me, macosX is a huge dissapointment. 
If I could do it over again, I wouldn't buy it. 
Now it's standing next to my hifi set serving music... it's a bit expensive for that because I can also use a router todo that.

---

### Post by slux on 2006-01-19
[QUOTE=qball]There are 2 good things about the mini:
* It's quiet. you can leave it running during the night withouth keeping you up.
* It's small.

But It's alot of money for a small (low end) system. (I had a complete 64bit system for alot less).  And for me, macosX is a huge dissapointment. 
If I could do it over again, I wouldn't buy it. 
Now it's standing next to my hifi set serving music... it's a bit expensive for that because I can also use a router todo that.[/QUOTE]


Why was OS X a disappointment for you? It's not my number one OS choice either but I find it pretty good. :)

Small size, low noise and Apple quality & design are part of the cost too. You may well be able to put together a gray box cheaper but then you're kind of missing the point. I find it pretty funny how people are comparing the new MacBook to Acers and Dells while it's more like a ThinkPad.

---

### Post by qball on 2006-01-20
[QUOTE=slux]Why was OS X a disappointment for you? It's not my number one OS choice either but I find it pretty good. :)

Small size, low noise and Apple quality & design are part of the cost too. You may well be able to put together a gray box cheaper but then you're kind of missing the point. I find it pretty funny how people are comparing the new MacBook to Acers and Dells while it's more like a ThinkPad.[/QUOTE]

I agree apple's hardware is often of good quality, I still consider my next laptop being a apple. (I have a thinkpad now).
Why I don't like mac osX, I guess it's very personal. But I constantly bump into small (and quiet often not so small) bugs, and the interface, after using it a while, isn't so consistent as you expect.  (Setting's are one time instant apply, the other time not, but you only see this when closing/switching tab in  the settings, (it pop's up a confirmation dialog). Keybindings are often weird, and I found them hard to find. mnemonics are missing and collide in even the most simple windows, etc)

But design wise, it are nice machines. and linux runs fine on it.

---

### Post by felix_stegerman on 2006-01-20
[QUOTE=ashigabou]I am happily using ubuntu on my minimac for almost one year, now. But recently, I noticed that xorg is not using direct rendering: as I would like to use a software which uses openGL, I need dri for acceptable performances.

I am using the ati graphic driver in xorg.conf, I am loading the dri module, but somewhat, glxinfo tells me that I am using indirect rendering. Where should I look to get direct rendering ?[/QUOTE]

Hi,

DRI works fine here. I've attached my xorg.conf.
Please note that I'm running Debian (sid), but AFAIK DRI should work with Breezy too.


Felix

---

