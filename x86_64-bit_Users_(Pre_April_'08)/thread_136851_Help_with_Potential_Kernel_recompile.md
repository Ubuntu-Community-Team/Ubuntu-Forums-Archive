---
title: "Help with Potential Kernel recompile"
date: 2006-02-26
forum: x86 64-bit Users (Pre April '08)
---

### Post by Vins on 2006-02-26
Hi guys,

**Problem**

I think I might need to recompile my kernel to ignore  SATA devices.  However I am a complet newb when it comes to Linux Operating Systems, not even sure how to install a program manually yet.

[INDENT]*_Specs_*[/INDENT]

CPU =  AMD Athlon 64 3000+ (754 pin)
MB = GigaByte GA-K8NS Pro
[INDENT]chipset= nVIDIA nForce3 250[/INDENT]
Mem = 512 MB 
Vid = nVIDIA FX 5750LE
CD Rom = Lite On 52X (IDE)
DVD combo = MSI (SATA)
HD1 = IDE 40GB Westrn Digital
HD2 = SATA 80GB Maxtor

[INDENT]Background[/INDENT]

I built this machine mainly for word processing, as I am a student - and gaming, as I am a geek. \\:D/  For about a year and a half this machine has been fine.  However the classes I am taking now, the work we do is done almost exclusively on unbuntu (for programming) or some thing else in the Physics labs, I forget. So I figured I would get a linux machine going to install Latex, Python, Java, and a C\C++ compiler, ya know, the stuff I use in classes and labs.

My First attempt was with Linspire 5.0, but even though the Live CD worked, when I tried to install it broke on my SATA HD.

So I decided to circumvent the whole thing, because I didn't want the chance of windows messing with my Linux stuff, and vice versa - with a couple of removable drive bays, so I can shut down plug in my window drive, or do the same with my Linux, and never the twain shall meet.  Linspire did not recognize or care about my SATA DVD combo drive, and so I just went without.

So with that Linspire ran fine, albeit w/o the DVD drive, but then I discovered it was a money sink and kinda stunk as a useful Linux OS. Sooooo, I decided to install unbuntu, I was given a 5.10 release and live package.

**Background Problem**

[INDENT]While installing ubuntu 5.10 was getting a timeout error [/INDENT]
when the installer would reach my SATA DVD combo drive. (maker = MSI) This was prior to the semi-GUI install screens, happens after I hit enter to proceed with install, and a long string of text would appear.  At one line, referring  to my SATA DVD combo drive the process would hang with a timeout 0xa0 error. Happens with LIVE! or Install Disks

**Background Solution**

[INDENT]disabled all Serial ATA support in BIOS, installation[/INDENT]
proceeds without any further issues.  Unbuntu installed and runs fine.

**The Point Being**

I do not want to have to go into the bios and disable SATA support everytime I boot ubuntu.  If at all possible I would like to modify the boot sequence for unbuntu such that when I swap my Windows drive for my Linux drive, Linux will run without stopping to change my BIOS conifguration.  I do not know if there is a driver, or lib pakage, or some easy-ish software solution. Even if there is I am not sure I have the Linux sophistcation to do it with out a step-by-step walkthrough. 

If there is not a easy-ish software solution, then I am afraid I will need to disable the point in my boot sequence where the SATA things are identified and attempted to by mounted.  I am not sure but isn't that a kernel issue?

So this is my dilemma, can anyone out there help me with a step by step on what I can do to get this working?  I would appreciate any help, in the simplest terms possible.  I have searched the formums and found a great deal on AMD 64 install issues, but I do not think they are applicable, as well as modifying for Video card enhancements, but again, I do not think that is correct either.  

Thank you all for your help,

Vins

---

