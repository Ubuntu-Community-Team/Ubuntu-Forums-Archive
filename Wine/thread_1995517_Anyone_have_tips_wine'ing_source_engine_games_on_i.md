---
title: "Anyone have tips wine'ing source engine games on intel HD graphics?"
date: 2012-06-03
forum: Wine
---

### Post by Mahkoe on 2012-06-03
I have attempted to install portal 2 on every ubuntu distro since 10.10 and a few times on a few arch and gentoo based systems with no luck. I recently found out why I'm getting bad results while others can run it flawlessly; because I'm not only using embedded graphics, but *intel* embedded graphics. 

**Driver:**
My driver (according to the system details dialog) is intel ironlake mobile, and underneath it says "Experience: Standard" (whatever that means). I have 64 megs video memory.

**Software:**
I am currently running wine 1.5.5 and PlayOnLinux 4.0.17, on Ubuntu 12.04 64bit

**I have tried:**
(Note that these were all tried between wine 1.27 and wine 1.5.5)
Installing it without the help of a program or front-end in 64bit
Installing it with winetricks in 64bit and 32bit
Installing it in PlayonLinux which claims in 32bit (I haven't tried it in 64bit in POL)
Running the files from my windows partition with wine
Running something called skidrow on the installation (I still don't know what it is, but someone claimed it would help)
I have tried all of the above with the disc installer, and once in playonlinux and once with winetricks with the painfully long 11GB steam download. I have toyed with several wine configurations and startup configurations for portal 2, including the dxlevel 81 and trying it with and without glsl support, and modifying various things in the wine registry.

**Results:**
My results have been mixed over time. Sometimes, steam crashed before anything else. Sometimes, Portal 2 crashed before starting. Sometimes, when I did manage to get the game running, the in-game lighting or whatever didn't work, meaning I couldn't see anything. Every time I managed to get to the portal menu, I could never see the text, so I would be guessing at what I was clicking.

**Other hardware:**
Intel i3-370m processor
Gateway mb and BIOS
4GB DDR3 RAM
Atheros wireless (with ath9k module and wext driver), broadcom ethernet

At this point, the only thing keeping me from wiping windows forever and regaining those 30 extra gigs is the fact I can't get portal 2 working. So, after about 18 months of frustration, I decided it was finally time to go to the ubuntuforums. Does anyone have any tips, or has anyone ever had these problems and know a solution?

---

### Post by Mahkoe on 2012-06-03
For some reason, the forum system created two of this post. Since I'm not sure what to do in this situation, I'm just gonna link to the other one. Hope I'm not making any faux pas
[http://ubuntuforums.org/showthread.php?p=11995242#post11995242](http://ubuntuforums.org/showthread.php?p=11995242#post11995242)

---

