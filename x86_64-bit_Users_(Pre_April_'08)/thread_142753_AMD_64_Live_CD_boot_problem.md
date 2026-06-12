---
title: "AMD 64 Live CD boot problem"
date: 2006-03-11
forum: x86 64-bit Users (Pre April '08)
---

### Post by xwing on 2006-03-11
Specs:
AMD64 X2 4400+
Asus A8N-E mobo (nForce 4 ultra)
2G Ram
200Gb SATA
nv 7800 GTX

Trying desperately to boot up the livecd but it always fails during boot at the stage where debian-installer components are being loaded from CD. I have tried to burn it on different media, but the problem persists. This is from an independent download (not ShipIt). The MD5 sum checks out just fine.

I have been able to install on VMWare server (the free version that just came out) and the cd works fine).

I tried doing a live-expert install so I could choose which modules to load (I figured I could detect the module that isn't loading from the CD and uncheck during selection process) but that hasn't worked either.

I have also downloaded the Ubuntu AMD 64 "install" CD, and it gives me a problem at the exact same point.

Any ideas?

---

### Post by calperin on 2006-03-22
[QUOTE=xwing]Specs:
AMD64 X2 4400+
Asus A8N-E mobo (nForce 4 ultra)
2G Ram
200Gb SATA
nv 7800 GTX

Trying desperately to boot up the livecd but it always fails during boot at the stage where debian-installer components are being loaded from CD. I have tried to burn it on different media, but the problem persists. This is from an independent download (not ShipIt). The MD5 sum checks out just fine.

I have been able to install on VMWare server (the free version that just came out) and the cd works fine).

I tried doing a live-expert install so I could choose which modules to load (I figured I could detect the module that isn't loading from the CD and uncheck during selection process) but that hasn't worked either.

I have also downloaded the Ubuntu AMD 64 "install" CD, and it gives me a problem at the exact same point.

Any ideas?[/QUOTE]Are you stopped on linux cd detection at 86%?

There is a huge problem with the ide-cd.ko driver, everybody has the same issue
:-?

---

### Post by xwing on 2006-03-22
Hi calperin, yes I did some searching around on the ubuntuforums and came across another post where the person (don't remember the link but remember reading it all too well ;-)) had the same problem (it seems to be a universal issue with Breezy as neither 32-bit not 64-bit live cds work with AMD64).
 
I have since downloaded Dapper flight 5, and its booting in fine with the Live CD. Almost makes me wish I had not done a "shipit" for Breezy. No foul though; I gave away all my CDs to friends.

---

### Post by bigmo on 2006-04-03
Same problem here... I almost have no hair left...
But I tried the Flight6 live CD and it is working like a charm...
It does even mess my display and I'm using an ATI card...

---

### Post by Bristen Bourque on 2006-04-26
[QUOTE=bigmo]Same problem here... I almost have no hair left...
But I tried the Flight6 live CD and it is working like a charm...
It does even mess my display and I'm using an ATI card...[/QUOTE]

is there something wrong with my Compaq if it works on mine? lol!  I was able to use the Live Ubuntu 5.10 and Live Kubuntu 5.10 (both i386 or 64bits)... it booted up fine... the only thing that I found is that for some reason, the painting did not always work correctly.. every once in a while I would get a line painted across my monitor... I have no idea what that's about... my PC is a "Compaq AMD Athlon 64 3400+ 2.4GHz (SR1475CL)".

Ubuntu/Kubuntu both appears to work perfectly on my old beater IBM ThinkPad (Celeron 500Mhz)...

Bristen.

---

### Post by xwing on 2006-04-26
[quote=Bristen Bourque]is there something wrong with my Compaq if it works on mine? lol!  I was able to use the Live Ubuntu 5.10 and Live Kubuntu 5.10 (both i386 or 64bits)... it booted up fine... the only thing that I found is that for some reason, the painting did not always work correctly.. every once in a while I would get a line painted across my monitor... I have no idea what that's about... my PC is a "Compaq AMD Athlon 64 3400+ 2.4GHz (SR1475CL)".

Ubuntu/Kubuntu both appears to work perfectly on my old beater IBM ThinkPad (Celeron 500Mhz)...

Bristen.[/quote]

I think the problem was with only certain types of AMD64 systems. Mine definitely had issues :confused:

---

### Post by Xoctor on 2006-05-29
I've tried a couple of the latest dapper releases in AMD 64 installation CD format, but they both freeze up at the 'loading kernel' stage.

The memtest on the CD works fine, and the CD is not corrupted, but none of the boot options that require the kernel to load work (normal install, 'safe' install, check CD).

My system is an AMD64 3200, 1gb, Asus A8N-CSM motherboard. Googling hasn't helped, other than to find this thread.

---

### Post by Xoctor on 2006-06-02
I found a solution: using the noapic nolapic kernel parameters works.

Its a shame to lose the power management features though.

---

### Post by steabert on 2006-06-09
Hi Xoctor,

I have exactly the same issue, freeze during "loading kernel"
on AMD64 X2 3800+ cpu and MSI neo4 FI motherboard

---

### Post by steabert on 2006-06-10
[QUOTE=Xoctor]I found a solution: using the noapic nolapic kernel parameters works.

Its a shame to lose the power management features though.[/QUOTE]

how and where exactly do I give these kernel parameters?

---

### Post by d3ik on 2006-06-10
[QUOTE=steabert]how and where exactly do I give these kernel parameters?[/QUOTE]

When the LiveCD splash screen first pops up, press 'F6' (I believe) to get a prompt containing the current parameters.  Then just edit/add parameters as needed.

---

### Post by steabert on 2006-06-11
[QUOTE=d3ik]When the LiveCD splash screen first pops up, press 'F6' (I believe) to get a prompt containing the current parameters.  Then just edit/add parameters as needed.[/QUOTE]

thnx, I will try some things!

---

