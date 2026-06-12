---
title: "Locks before I get past first screen!!"
date: 2005-09-29
forum: x86 64-bit Users (Pre April '08)
---

### Post by ironfistchamp on 2005-09-29
I just got a set of 64 discs and 386 discs. On another computer the 386 discs work fine. With this computer both sets fail to work. The Live and Install discs lock on the first screen. The one where you press enter to install or type server or something. Thats with the pressed discs.

If I use self burnt discs I get to the stage just before the partitioner and it locks at 45% of checking the discs.

Can anyone help. Computer specs below.


AMD 64 3200
GA-K8NXP-SLI
512Mb Samsung PC3200
40Gb Western Digital SATA drives x2
GIGABYTE 3d1 6600GT Dual graphics card
GIGABYTE Wireless LAN card
NEC DVD-Rewriter

Thanks for any help you can give me.

Ironfistchamp

---

### Post by DancingSun on 2005-09-29
Looking at your hardware configuration, I'm assuming you're trying to do a RAID setup?  Make sure it is setup properly in the BIOS, then try doing some search in the forums on installing Ubuntu on RAID SATA HDDs.

I'd recommend at least reading through this:
[https://wiki.ubuntu.com/FakeRaidHowto](https://wiki.ubuntu.com/FakeRaidHowto)

If you're sure that your RAID setup is correct and chose the correct options in the installer, try taking out one of your graphic cards and install again.

---

### Post by ironfistchamp on 2005-10-03
Hey its not RAID it is a dual boot with XP Home. They are set up as JBOD in the bios. The GPUs are both on one board. Its two or none. Any other help you can give me?

Thanks
Ironfistchamp

---

### Post by DancingSun on 2005-10-03
Is XP already installed?

---

### Post by ironfistchamp on 2005-10-03
Yes Home Ed SP2 other linux things have installed fine (but after that its not so great :p )

---

### Post by DancingSun on 2005-10-03
[QUOTE=ironfistchamp]Yes Home Ed SP2 other linux things have installed fine (but after that its not so great :p )[/QUOTE]
What do you mean by other Linux things? You installed other Linux distributions?  Are you installing both OSes on the same drive?

Where there any error messages when the installation froze?  Did it freeze at the same spot every time?

---

### Post by ironfistchamp on 2005-10-03
Hey sorry I was in a bit of a rush. Ill explain a bit better. Basically one hard drive has XP Home and the other has nothing on it. When i put the Install (or Live) disk in (this is the pressed disk from Ubuntu) it freezes just as the ubuntu banne comes up on screen and asks you to press enter or type server. Using my disks I made it gets to "Checking Disks" just before the partitioner and then locks at 45% everytime.

Could it be the SATA?

thanks
Ironfistchamp

---

### Post by DancingSun on 2005-10-03
[QUOTE=ironfistchamp]Could it be the SATA?[/QUOTE]
Could be, try searching for how to install Ubuntu on SATA drives.

---

### Post by crane on 2005-10-03
I'm having somewhat the same issues. I actually got the OS installed. Ubuntu and Suse both work good untill I leave it alone for a minute then the whole system locks up. WindowsXP runs without a hitch. 

I can log on and play games but if I let the computer sit for a couple of minute it locks. I think it is an issue with the Mother Board.

Gigabyte K8NS Ultra 929
Athlon 3000+
512 400ddr ( 2 x 256 )

---

### Post by DancingSun on 2005-10-03
[QUOTE=crane]I'm having somewhat the same issues. I actually got the OS installed. Ubuntu and Suse both work good untill I leave it alone for a minute then the whole system locks up. WindowsXP runs without a hitch. 
I can log on and play games but if I let the computer sit for a couple of minute it locks. I think it is an issue with the Mother Board.
Gigabyte K8NS Ultra 929
Athlon 3000+
512 400ddr ( 2 x 256 )[/QUOTE]
It's probably not the motherboard, since XP runs fine.  It's the drivers used in Ubuntu.

---

### Post by crane on 2005-10-03
[QUOTE=DancingSun]It's probably not the motherboard, since XP runs fine.  It's the drivers used in Ubuntu.[/QUOTE]

I didn't mean the mother board was faulty. I think the hard ware is fine. I think it just has issues with linux. Suse, Ubuntu, and Mepis all lock up.

---

### Post by DancingSun on 2005-10-03
[QUOTE=crane]I didn't mean the mother board was faulty. I think the hard ware is fine. I think it just has issues with linux. Suse, Ubuntu, and Mepis all lock up.[/QUOTE]
You'll need to pay attention to the symptoms that your system has.  Keep tabs on CPU usage, HDD activity, and memory usage.  Sometimes, a newer kernel will solve your problem.

If this is a hardware driver causing problems, you will need to try isolating the component that's causing the problem.  If you have the resources, you can swap the components out for another substitute, one by one and see if the issue still persists.  Your problem might be different from the guy having installation issues. But this method should be useful for sniffing out the hardware component that's causing problems.

---

### Post by victor_c26 on 2005-10-06
The Ubuntu/Kubuntu Live CDs keep hanging on me at the splash screen too. Knoppix and Suse ran just fine. Only Ubuntu/Kubuntu freezes on me. I'm trying to run the AMD64 build of both.

My specs:
Athlon 64 3500+ Venice Core
MSI MS-7093 Socket 939 ATi chipset Motherboard
1024GB Dual Channel PC-3200 DDR Ram kit
Seagate 250GB 7200RPM Sata150
Ati Xpress 200 Integrated chipset. (Soon to be an X800XL)

---

### Post by DancingSun on 2005-10-06
Looks like this really might have to do with the SATA drives...

I vaguely remember helping a guy out once that has similar problems in the installation help forum, where other distributions work, but not Ubuntu.  I think I ended up telling him to file a bug.  You guys might want to do that if he hasn't file the bug yet.

Have you tried the Breezy preview LiveCD?

---

### Post by victor_c26 on 2005-10-06
I haven't.

Does it have updated ATi drivers? I'm suspecting it might be an ATi driver issue.

---

### Post by DancingSun on 2005-10-06
I did a bit of searching on the forums for you guys, and found that one guy that had similar problems disabled "Cool 'n Quiet" from the mobo BIOS and that worked for him.

---

### Post by daniel49 on 2005-10-06
if you have a usb mouse or keyboard make sure that has been enabled in the bios as when I tried to install ubuntu the first time it was set to be handled by the OS and not the bios and would freeze. If you set it to let the bios handle it it worked fine for me.

---

### Post by DancingSun on 2005-10-06
[QUOTE=victor_c26]I haven't.

Does it have updated ATi drivers? I'm suspecting it might be an ATi driver issue.[/QUOTE]
For you it's likely to be an ATI issue, but not the first poster.

You could, in your xorg.conf, change the driver to "vesa".  Reboot, then install the drivers from ATI.  I remember reading about a post on this some where, do a search for it.

---

### Post by TheJoker on 2005-10-11
Guys,

I had a similar problem. It was the powernowd that was playing up.

[http://www.mail-archive.com/debian-x@lists.debian.org/msg37943.html](http://www.mail-archive.com/debian-x@lists.debian.org/msg37943.html)

Disable it as soon as you can by running
/etc/init.d/powernowd stop
and see if that works (sorry I don't know how to fix it so that you can disable it before it starts KDE or Gnome - I managed to login, and then quickly shut it down)

If it does work, uninstall it:
apt-get remove powernowd

DISCLAIMER: I haven't got this stuff written down but I found this out by googling for my kernel oops
and figuring it out from there:
cat /var/log/kern.log | grep -i "oops"

I also had to tinker with my startup options in Grub:
removed splash
added:
- noapic
- pci=usepirqmask

Good Luck!

---

### Post by popiet on 2006-01-17
thanks a lot, stopping powernowd worked for me too (I got freezes from time to time, quite often indeed).
I didn't remove "splash" from kernel options, I wil let you know (just for information) if I get new freezes.

---

