---
title: "Win7 - MS Virtual PC"
date: 2009-06-25
forum: x86 64-bit Users
---

### Post by Oldgreygeek on 2009-06-25
Interestingly, when attempting to load the x86-64 iso Microsofts new Virtual PC (beta)  for Windows 7 64bit RC gives me the message :  This Kernal requires X66-64 cpu only got a I686.  Now thats cute, wonder is this an error with the win7 vpc beta or Ubunto?
This was todays download of 9.04 64 bit as well as vpc.  running an intel Q6700 quad4.
BTW the 32bit ubunto loads ok.

---

### Post by xrayman2k4 on 2009-06-25
Same here on Vista 64 with VPC2007 - I guess they never figured out how to emulate a x86-64 processor :P

---

### Post by BugBuster on 2009-06-26
I would recommend you guys check the BIOS settings to see if there is some setting that is related to AMD-V/ Intel EMT64.

I had this particular issue on Ubuntu 8.04 32-bit, Jaunty 64-bit and WinXP 32 bit simultaneously.However I could run 64-bit OS'es without any issues.

In my case I figured out that it was a faulty BIOS and so I downgraded the BIOS and that fixed it.

I am not saying you jump onto BIOS flashing.But BIOS is certainly one area that you could look into

Just to add..In my case it was VirtualBox and not VPC.

---

### Post by Th3_uN1Qu3 on 2009-06-26
Definitely check if virtualization is enabled in the BIOS, most brand-name computers come with it disabled. It's named Virtualization Technology or Hardware Virtualization.

---

### Post by jespdj on 2009-06-27
Why are you using Microsoft Virtual PC?

Use [VirtualBox](http://www.virtualbox.org/) - it runs on Ubuntu, is free and supports 32-bit as well as 64-bit host and guest operating systems. You can even run a 64-bit guest OS inside a 32-bit host OS. But for 64-bit you do need to have a 64-bit capable processor and you must have hardware virtualization support enabled (in the BIOS and also in the virtual machine).

I have 64-bit Windows 7 RC running in a VirtualBox VM on 64-bit Ubuntu 9.04, it runs fine.

---

### Post by bobince on 2009-06-27
You can also use old versions of Virtual PC, which don't require hardware support for virtualisation (Intel VT/AMD-V).

I don't know why MS have made the new Virtual PC completely reliant on VT, but hopefully this (especially its usage in Win7's Virtual XP Mode) will force Intel to stop pointlessly cutting out the VT feature on its CPUs as an artifical market segmentation strategy, and mobo makers to stop messing VT up with broken BIOSes.

But yeah, in general I prefer Virtualbox these days.

---

### Post by pcookei on 2009-06-27
Just downloaded Win7 RC 64bit, decided to install in a VM on Ubuntu 9.04 64bit. Virtualbox installs brilliantly. However when I come to run the install disc for Win7 it says I am not using a cpu that can use 64bit mode. My motherboard Bios does not appear to support hardware Virtualization, although the cpu is AMD Athlon X2 . Perhaps some kind person would direct me in the direction of success. Not a complete dunce, but old enough to know that the obvious is not always obvious.

---

### Post by philcamlin on 2009-06-27
very odd...:confused:

---

### Post by craig100 on 2009-08-08
HI, i've just downloaded the iso for Win 7 RC and can't install it into a new VM with VirtualBox 2.2 on Ubuntu 9.04 64 bit. What I get is "Loading Files" then "Starting Windows" then a Windows Boot Loader error "An unexpected error has occured" indicating an error code of "0xc0000225". I've set up the VM with VT extensions on, 2G RAM, 20G HD, audio on (Pulse Audio). Have tried the PCnet-FASTIII and Intel Pro 10/100 MT network adapters. Also tried installing from iso and DVD. Get the same result every time.

Does anyone know what could be causing this?

Craig

---

### Post by craig100 on 2009-08-08
I've now fixed the problem with help from another place.  What was needed was to switch on IO PIC and Nested Paging. Installation then went ahead ok.

Hope this helps someone.

Craig

---

