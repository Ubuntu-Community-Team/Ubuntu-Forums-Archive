---
title: "fglrx driver install on AMD64"
date: 2004-11-07
forum: x86 64-bit Users (Pre April '08)
---

### Post by Stendec on 2004-11-07
Hi,


apt-get install fglrx-driver does not seem to find any packages for the AMD64 architecture!

Is there someone out there who has managed to get the ATI driver installed and willing to share this?

---

### Post by conchobar on 2004-11-08
Sadly, ATI hasn't released the package for AMD 64. Anyone have some inside info on just when ATI plans to get that out? I'm about ready to just rip out my Radeon 9800 Pro and trade it in for an Nvidia card!

---

### Post by wazoo42 on 2004-11-08
I second that idea.  I have a 9800aiw that isn't doing me much good right now.  Ugh, what a shame.  I keep leaving feedback asking what I can do for 3D support, here is the link if you would like to do the same.

[http://apps.ati.com/linuxDfeedback/index.asp](http://apps.ati.com/linuxDfeedback/index.asp)

---

### Post by daniels on 2004-11-09
ATI have a bunch of things they need to do to update fglrx, including giving it proper Composite support so it can work with X11R6.8 and above.  There is currently no publicly known timetable for a new driver drop.

---

### Post by HiddenWolf on 2004-11-10
I sent an e-mail last night to ATI, informing them of my decision that my next GFX card is going to be an Nvidia solution.

And I'm a lucky one, I've got a 9200, which is supported by DRI, or the 'ati' module in Xfree.

Not that it helps, but perhaps 10.000 of us mailing that would make a difference.

---

### Post by xkcdmagic8 on 2004-11-16
ATI support in UBUNTU LINUX [ Debian Based ] is sub par. [ Not only in this distrubution ] It's hard enough installing this FGLRX driver - it seems to think im using a 9500 GENERIC when im using a 9700 PRO. It gives me no 3d, when it does it give me 3000 fps in GLXGEARS whereas my friends OLD nvidia card can easily reach 11,000 fps. The preformace and usibility of these drivers are under any margin. Theses issues are leading many people to choose NVIDIA for their next card. Maybe a Nvidia 6800 GL.

My email :)

---

### Post by conchobar on 2004-11-16
Luckily, I read somewhere (maybe this board or Planet AMD64?) that ATI's releasing a new driver for us in December, which they claim will be comparable in quality to the Windows drivers. Yes, Windows quality drivers, no more feature ripped betas. I'll give them this chance. If they're lying...I'm setting my Radeon aflame. ;)

But on the flipside, If ATI delivers, who's up for starting a UT2004 Ununtu clan??

Come to think it would, that be really fun to arrange a team game with teams decided by what distro they run. Find out once and for all that Gentoo users can't last in battle because they get distracted by compilation!

---

### Post by daniels on 2004-11-16
[QUOTE=nitinshantharam]ATI support in UBUNTU LINUX [ Debian Based ] is sub par. [ Not only in this distrubution ] It's hard enough installing this FGLRX driver - it seems to think im using a 9500 GENERIC when im using a 9700 PRO. It gives me no 3d, when it does it give me 3000 fps in GLXGEARS whereas my friends OLD nvidia card can easily reach 11,000 fps. The preformace and usibility of these drivers are under any margin. Theses issues are leading many people to choose NVIDIA for their next card. Maybe a Nvidia 6800 GL.[/QUOTE]But why do you choose glxgears as a benchmark? Look at a game, see how it looks and plays, and judge based on that. Honestly, do you notice the difference? Do you sit there watching glxgears for hours and notice the FPS leap? If not, then it's a pointless benchmark -- the only useful watermark is 'is this better in situations I actually use it for, e.g. games'.

---

