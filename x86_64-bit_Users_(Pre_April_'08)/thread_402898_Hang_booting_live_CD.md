---
title: "Hang booting live CD"
date: 2007-04-06
forum: x86 64-bit Users (Pre April '08)
---

### Post by cfineman on 2007-04-06
Downloaded ISOs of the 32-bit and 64-bit LiveCD (MD5s check out).

I was able to boot up the 32-bit version and got the initial desktop

The 64-bit version locks at a Spalsh screen (B&W with Ubuntu logo with several vertical bars below).

My hardware:
[LIST]
[*]FX-55
[*]Asus A8N-SLI
[*]eVGA 7300
[*]2G Mem
[/LIST]

Pretty standard setup near as I can tell. Maybe the 7300 is gonna give me problems? BTW booting into "VGA Safe" mode didn't make a difference.

BTW, I get the same exact hang whether selecting Install from the boot menu or Check CD Contents.

I'll go with the 32-bit version if I need to but I was hoping for 64-bit goodness. Any thoughts?

---

### Post by Kilz on 2007-04-06
> **cfineman said:**
> Downloaded ISOs of the 32-bit and 64-bit LiveCD (MD5s check out).

I was able to boot up the 32-bit version and got the initial desktop

The 64-bit version locks at a Spalsh screen (B&W with Ubuntu logo with several vertical bars below).

My hardware:
[LIST]
[*]FX-55
[*]Asus A8N-SLI
[*]eVGA 7300
[*]2G Mem
[/LIST]

Pretty standard setup near as I can tell. Maybe the 7300 is gonna give me problems? BTW booting into "VGA Safe" mode didn't make a difference.

BTW, I get the same exact hang whether selecting Install from the boot menu or Check CD Contents.

I'll go with the 32-bit version if I need to but I was hoping for 64-bit goodness. Any thoughts?

This might point to the fact that the 64bit lice cd doesn't have the video driver on the disk. There is only so much room on a cd. You might want to try the alternate install cd if you just want to install. Then once installed, work on the driver.

---

### Post by FunnyLookinHat on 2007-04-06
Yea dude, use the 32 bit CD and you'll be golden.  The 64 bit distributions of linux out there these days are hardly useful when it really comes down to it.

---

### Post by cfineman on 2007-04-06
Ran across comments regarding APIC so I turned that off. Kinda surprised since my hardware is not that old but... can't argue with success... was installing when I left for work this morning

---

### Post by clblanchard on 2007-04-09
I have that problem with all live ubuntu cds.  I have to disable sli and remove one video card (7600)  after that it runs like a top.  after the install i just pop the card back in and install the nvidia drivers from their site and get my game on.

---

### Post by Kilz on 2007-04-09
> **FunnyLookinHat said:**
> Yea dude, use the 32 bit CD and you'll be golden.  The 64 bit distributions of linux out there these days are hardly useful when it really comes down to it.

It is truly SAD that a community team leader would come into the 64bit section and post FUD.

---

### Post by cfineman on 2007-04-09
> **Kilz said:**
> It is truly SAD that a community team leader would come into the 64bit section and post FUD.

Yeah, surprised me as well. Unfortunately, it somewhat effected my decision as I ended up installing the 32-bit version. I plan to go back to 64 bit once I get a bit more comfortable and de cide which distro I want. I feel like I paid my dues years ago (with a box full of slackware diskettes)... now I just want a distro that's easy to manage (with up-to-date packages) so I can get on to the task at hand... I just want a dev box I can experiment with.

---

### Post by Kilz on 2007-04-09
> **cfineman said:**
> Yeah, surprised me as well. Unfortunately, it somewhat effected my decision as I ended up installing the 32-bit version. I plan to go back to 64 bit once I get a bit more comfortable and de cide which distro I want. I feel like I paid my dues years ago (with a box full of slackware diskettes)... now I just want a distro that's easy to manage (with up-to-date packages) so I can get on to the task at hand... I just want a dev box I can experiment with.

If you ever want to change to the 64bit version, go for it. Its not difficult, but it will mean wiping the 32bit and starting over. Either version has great package management and installs very easily.

---

### Post by ronocdh on 2007-04-09
> **cfineman said:**
> Yeah, surprised me as well. Unfortunately, it somewhat effected my decision as I ended up installing the 32-bit version. I plan to go back to 64 bit once I get a bit more comfortable and de cide which distro I want. I feel like I paid my dues years ago (with a box full of slackware diskettes)... now I just want a distro that's easy to manage (with up-to-date packages) so I can get on to the task at hand... I just want a dev box I can experiment with.
As has been covered, it's a damn shame you experienced an attitude like that here. But don't worry, because I myself fell prey to it a while back; my 64-bit live CD wasn't booting, so but the 32-bit was, so I figured, "Screw it, I'll make sure SMP is running and then who cares." 

The plan was always to feel out the system and see what works, and once I got comfortable, upgrade. I've done that. It's worth it! So much luck to you, and I hope to see you posting around these parts again soon.

---

