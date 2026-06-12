---
title: "Gutsy AMD64 Sometimes Loads"
date: 2008-01-07
forum: x86 64-bit Users (Pre April '08)
---

### Post by ndest964 on 2008-01-07
Hi, I'm new to Linux/Ubuntu.  I just built a new pc and loaded Windows XP and Ubuntu 7.10 on it.  Windows XP works perfectly, Ubuntu also works perfectly... when it loads that is.  When starting my pc Grub loads up fine, I choose Ubuntu and sometimes it loads, other times I just get a black screen, and still other times my whole computer just reboots.  Any ideas?  My hardware is pretty new, I suspect that it may be my video drivers, I have a Nvidia 8800gts (512) and was able to successfully load the drivers from Nvidia via [Envy]("http://albertomilone.com/nvidia_scripts1.html").  

Other stats: 
Abit IP-35 PRO Mobo
Core 2 Duo cpu
2 Gigs Crucial Ballistics 1066 ddr2  
Nvidia 8800gts (512)
Dual SATA DVD Burners
SATA HDD

Like I said earlier, once I'm in everything works like a champ, just getting in doesn't always happen, very irritating as I'm trying to dump Windoze with the exception of gaming.

Any help would be appreciated.

Thanks!
Nick

---

### Post by Joe Jarvis on 2008-01-07
> **ndest964 said:**
> I suspect that it may be my video drivers

One of the times that you successfully boot it, install the ssh server.  Then, when you get the black screen, try to ssh in to the box.  If you can successfully do that, that may point to a display problem.  You should also be able to check logs and test the machine in its broken state.

---

### Post by docorange on 2008-01-07
Try to uninstall the envy drivers, and try to install those you get with ubuntu restricted manager. With those you should get worst performances from your video card, but your system should be much more stable
docorange

---

### Post by ndest964 on 2008-01-08
Do the drivers from Ubuntu restricted manager support the 8800gts (512)?  Its a fairly new card, I think it came out sometime in early December.  I don't wanna install them and have it not work altogether.  The drivers that Envy installs are direct from Nvidia btw. 

Thanks,
Nick

---

### Post by 6568912 on 2008-01-09
yes it should support 8800 series >_> but you should check nvidia.com for confirmation of that first....lets say i give 70% that it will work:lolflag:

---

### Post by ndest964 on 2008-01-10
Ok, I edited Grub's menu.lst, changed splash to nosplash, and upon bootup it told me to try adding the irqpoll option, so I added that and it seems to help.  Not 100%, the system still reboots on startup sometimes, but not nearly as often, so it looks like I'm getting closer.

---

### Post by linuxrock on 2008-01-10
Wich os did you install first?

---

### Post by ndest964 on 2008-01-10
I installed Windows XP first, getting both up and running was really easy, I did the manual partition option on the Ubuntu installer, it was pretty straightforward.

Nick

---

