---
title: "warcraft runs at 100% CPU"
date: 2008-01-02
forum: Wine
---

### Post by potatan on 2008-01-02
Hi,

When I load World of Warcraft the CPU jumps from an average of 10-20% up to 100% and stays there pretty constantly whilst playing.  This doesn't seem to affect gameplay most of the time, but occasionally I get a complete lock up for about 3 seconds.  The screen freezes and the sound stutters during this time.

These lockups are slightly more frequent in an instance.

I'm running 32 bit Gutsy 7.10 on an AMD 64 3500+ with 2GB RAM, using an Nvidia GeForce 7600 GS. 

I have disabled all my Addons to see if that helps, and it doesn't.  I have also added the Wine registry edit suggested elsewhere.

Any ideas?

Many thanks.

---

### Post by potatan on 2008-01-04
Bump

---

### Post by billybigrigger on 2008-02-21
This seems to be nearly the exact problem I face, except the stuttering happens virtually continuously from the moment of launch.  Needless to say the game is unplayable at this point.  I began to suspect it was a cpu during monitoring of cpu usage from launch of the game.  It stays pegged at or near 100% cpu usage with the identical behaviors as described by OP, but almost constantly as I mentioned.

I have applied all tweaks and followed as many guides/how to's/wikis as I could.

I just recently installled Ubuntu 7.10, on the same system which i previously played World of Warcraft under Windows XP for many many months.

Software:

Ubuntu: 7.10
Wine: 9.55
WoW: unknown, but current as of this post's date. (2,3,,,,)
Video Driver:  Nvidia 100.14.19, as installed by Restricted Drivers Manager

Harware:
AMD 3500+ 2,2 ghz
Nvidia Gforce 7600 GT, running dual display (VGA + DVI)
Running Ubuntu install and WoW off of IDE/PATA hd (also tested off of SATA windows install HD with same results)

Anyhelp or comments greatly appreciated.

(btw loving Ubuntu, and the community, hoping to go single boot soon)

---

### Post by GrayMagiker on 2008-03-25
I have the same issue.  

As soon as wow is launched it is reported as taking %100 (or near there) of the CPU.  

Dual Core Athelon 5600
NVIDIA 5200 with restricted drivers installed 
Ubuntu 7.10 Fully patched

I have installed the drivers recommended by "Envy" as suggested elsewhere, and it makes no noticeable difference.  

I am using Openbox, because the wine site says  Gnome/Metacity/Compiz interferes with wine.  

Neither Changing resolution nor toggling the virtual desktop in winecfg helps.  

Attached x.org and the error output from wine, in case it might be of help to someone.

---

### Post by javafiend on 2008-03-26
I think I'm having the same issue.  I have a dual core AMD 64 and during and after running WoW, core 1 is at 100%.  Core 2 is fine.

---

### Post by DanielJackins on 2008-03-27
I believe this is because Wine tries to run the games using as much CPU as possible so it runs better

---

