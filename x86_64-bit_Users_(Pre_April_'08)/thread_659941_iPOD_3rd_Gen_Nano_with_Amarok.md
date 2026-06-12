---
title: "iPOD 3rd Gen Nano with Amarok"
date: 2008-01-06
forum: x86 64-bit Users (Pre April '08)
---

### Post by zephyrus17 on 2008-01-06
I've been trying sync it, and I believe I have, and I can copy the songs into the iPod. But the problem is that the iPod can't detect the songs at all, even though it detects that the HD is being used up. Plus, when looking at the iPod properties in Listen, it says "Firmware: Unknown"

I think I might have screwed up a configuration somewhere, and I am totally lost.
[http://lilserenity.wordpress.com/2007/12/22/virgin-mobile-praise-ubuntu-and-ipod-nano-3g/]("http://lilserenity.wordpress.com/2007/12/22/virgin-mobile-praise-ubuntu-and-ipod-nano-3g/") has a guide, but it doesn't work on my AMD64 CPU.

gtkpod detects the music files and filenames, though.

Help?

---

### Post by zephyrus17 on 2008-01-08
bump

---

### Post by andersja on 2008-01-08
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/libgpod/+bug/181340](https://bugs.launchpad.net/ubuntu/+source/libgpod/+bug/181340) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I've posted a request on launchpad: [https://bugs.launchpad.net/ubuntu/+source/libgpod/+bug/181340](https://bugs.launchpad.net/ubuntu/+source/libgpod/+bug/181340)
More information: [http://amarok.kde.org/wiki/Media_Device:IPod#My_iPod_does_not_show_any_music](http://amarok.kde.org/wiki/Media_Device:IPod#My_iPod_does_not_show_any_music)

---

### Post by 6568912 on 2008-01-09
dunno dunno,my ipod NaNo wont even work >_>i think i got wrong cables or something.......just PC wont see my <snip> IPOD! i say wha: Canonical please dudes build new mp3/mp4 player UbuntuPOD! :( i beg! please please#1

---

### Post by soxs on 2008-01-09
I myself own a 2gen iPod and evrything workx just fine.
The only hint I can give you, that you should try compiling amarok yourself. I've heard about that amarok is not ready for 3gen, at least the version ubuntu gives to you by the official repository. I'm sry that I can not provide any more information about that. At this point you must start researching yourself.
EDIT: this is somehow confiremd by the launchpad bugreport
so you have to get the new lib first and compile then latest amarok

---

### Post by khensucat on 2008-01-09
Remember that this is Apple's doing in the first place, and the community is playing catch-up - Apple broke the 3rd Gen's for Linux on purpose ;)

---

### Post by soxs on 2008-01-10
Allright, thios is caused by apple, encrypting firmware and changing stuff every new iPod gen. This kind anoyes me, they could have left their config stuff is it had been with zer0 effort. I guess this is some kind of vendetta gainst the non commercial opensource world.

---

### Post by gobbomaster on 2008-01-10
Great, I was really happy when I received my NANO today until I tried to get music on it.. Same problem as stated above, and I run GNOME, tried to install the newest Amarok which worked, also install lbgpod2 0.6.0 but it still doesn't work for me.. solutions?

---

### Post by 6568912 on 2008-01-14
Ipod rulez ... thats why i never gonna buy it again:)

---

### Post by zephyrus17 on 2008-01-19
> **soxs said:**
> I myself own a 2gen iPod and evrything workx just fine.
The only hint I can give you, that you should try compiling amarok yourself. I've heard about that amarok is not ready for 3gen, at least the version ubuntu gives to you by the official repository. I'm sry that I can not provide any more information about that. At this point you must start researching yourself.
EDIT: this is somehow confiremd by the launchpad bugreport
so you have to get the new lib first and compile then latest amarok

I'm not good at compiling ... at all.

I guess I'll have to wait, then. For now, I guess the only way is to dual boot. :S

Oh.. How do I install libgpod 0.6.0?

---

### Post by firecat53 on 2008-01-19
Did you try the instructions in [this thread]("http://ubuntuforums.org/showthread.php?t=619615&highlight=video+ipod")?  Seemed to work for a 6G Ipod Classic, which I think is in the same generation as the 3G nano. I'm running AMD64/Amarok.

Good luck! Scott

---

### Post by soxs on 2008-01-19
> **gobbomaster said:**
> Great, I was really happy when I received my NANO today until I tried to get music on it.. Same problem as stated above, and I run GNOME, tried to install the newest Amarok which worked, also install lbgpod2 0.6.0 but it still doesn't work for me.. solutions?

You first need libgpod and then compile NOT vice versa!

---

### Post by zephyrus17 on 2008-01-20
Where can I get libgpod? Synaptics only has it to 0.5.2 (i think),

Oh.. Never mind. saw Firecat53's link.

---

### Post by tafsen on 2008-01-22
Is it safe to upgrade the iPod software with iTunes?

---

### Post by khensucat on 2008-01-22
Would it work to run iTunes in a WinX VirtualBox?

---

