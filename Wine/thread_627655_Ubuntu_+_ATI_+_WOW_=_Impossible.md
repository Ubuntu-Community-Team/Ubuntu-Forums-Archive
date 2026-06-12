---
title: "Ubuntu + ATI + WOW = Impossible?"
date: 2007-11-30
forum: Wine
---

### Post by psmul on 2007-11-30
I am trying to work with linux for quite some time now altough I cannot say I am experienced.
I own a ATI x1950 and got the driver and everthing working (at least, Cedega test = ok)

The only thing keeping me on Windows is my addiction to WOW >.< and since I keep hearing so much about ATI drivers improving I wanted to give it another shot. 
Sadly enough I could not get WOW working, not with Wine or Cedega. I don't need any specific howto's cause trust me, iv'e read them all! [-X

All I want to ask is if there is anyone out there who has WOW (or any other equally visual game) running on Ubuntu that owns an ATI card. If so please tell me what u used and how much u needed to tweak.


	[-o<

---

### Post by John_Henry on 2007-11-30
Greetings! I am new to linux myself.
 I had Ubuntu/Windows dual boot for a short time for WoW also.

 I have a Radeon x1950

I actually did manage to get wow working acceptably 
(Only issue was FPS)

For a week or so anyway, Having Jumped the gun and ditched the last of Windows, now its broken again lol.

The best I achieved, was preaty good, I had some FPS issues, especially in outlands, or with to many people around. (Shat runs about 12 fps, hellfire 20) Azeroth averages 40ish


After playing OK for a couple weeks, Things went to hell a few days ago.

My UI Icons corrupted, (Easily Fixed with steps from Troubleshooting)

My minimap shows solid White indoors, and Clear/Invisible Outdoors but quest givers and tracked things still correctly display their relative location where the minimap should be.
(Still no fix)

Terrain now has a checkerboard grid on it, criss cross lines on sand, dirt whatever, (all zones)
Water(mostly just outlands) looks like crap, A big lightblue/darkblue checkerboard.


so its still playable I guess, its just that now, in addition to playing with crappy FPS my minmap is busted and therain/water look like crap(technical audio/video term)

Almost enough to reinstall Vista... ICK

EDIT:
For what its worth, what little success I have had comes from straight wine. no crossover/cedega



<system>
Intel Quad Core @ 2.4 per core
2GB DDR2, 667 MHz, (PC2-5300)
ATI Radeon X1950 CrossFire video card with 512 MB
Integrated Intel 8-Channel (7.1) Audio

[http://support.gateway.com/s/PC/R/1009475/1009475sp4.shtml](http://support.gateway.com/s/PC/R/1009475/1009475sp4.shtml)
</system>

---

### Post by psmul on 2007-11-30
Ok

thanks for the info. I was advised by some to use Cedega, but ill try it with wine again. Ill post reply in a few days orso

---

### Post by Macros42 on 2007-11-30
> **John_Henry said:**
> Almost enough to reinstall Vista... ICK


For the price of Vista you'd get a decent nvidia card. I play WoW in Ubuntu without any problems. FPS is 101 as I'm looking at it on my twinview system. Admittedly with an 8800GTS but even a lower end Radeon would be good enough for WoW. Used to play it with a 9800 Pro on a much lower spec machine.

[edit] In Wine btw.

---

### Post by John_Henry on 2007-11-30
> **Macros42 said:**
> For the price of Vista you'd get a decent nvidia card. I play WoW in Ubuntu without any problems. FPS is 101 as I'm looking at it on my twinview system. Admittedly with an 8800GTS but even a lower end Radeon would be good enough for WoW. Used to play it with a 9800 Pro on a much lower spec machine.

[edit] In Wine btw.

I already Own Vista (REinstall) :P  and I have it running again,  althought framerate is still crap.

---

### Post by RogueXXV on 2008-08-21
Good Day this seems to be the closest problem to my problem that I can find around here and that I can reply too o.0 I tried to reply to [Dual Card Thread]("http://ubuntuforums.org/showthread.php?t=717567&highlight=ATI+quad+crossfire") but its archived and still NOT SOLVED :(, I have 4 YES 4 ATI 3870s in Quad-Crossfire mode, I hear that crossfire is not available in Ubuntu, but can I at least find all my cards? When I install I can only do dual head and even then can't seem to get all 4 up and running. I'm SUPER-noobish to this operating system and have been being helped by a pretty savey Ubuntu guy but hes never had the situation of 4 cards. So any and all help would be appreciated. If you have an entire... (dang now I cant even remember the name of the file)... xorg (that's it) file lay out for even a working Dual or Tri Card set up it would be greatly appreciated. I have the 4 working with Vista 64 bit cuz its the only thing that will see them all and all my 8gig o ram... but I would sooo love to get rid o my M$ crap. So again any assistance would be greatly appreciated.

Thanks
Rogue

---

### Post by Macros42 on 2008-08-21
[http://pastebin.com/m487cdf70](http://pastebin.com/m487cdf70)

This is for a dual nVidia setup with separate X sessions. Hope it helps.

---

### Post by Eviljim on 2008-08-22
Try here

[http://wiki.cchtml.com/index.php/Main_Page]("http://wiki.cchtml.com/index.php/Main_Page")

---

