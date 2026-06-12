---
title: "Can't install on AMD 64"
date: 2007-03-05
forum: x86 64-bit Users (Pre April '08)
---

### Post by johnerskine on 2007-03-05
Running the following

Dell E521
AMD Athlon 64 X2 Processor 5000 (2.60 Ghz, 512k)
Memory - Dual Channel 2GB (2X1024mb) 533 Mhz DDR2
Hard Drive - (500gb Serial ATA Non-Raid - 2X250gb) 7200 rpm Dual HDD Config

The machine is new, and I'm trying to install 6.10 Edgy

I've created an Edgy AMD 64 ISO image on CD (R) from a disc in a recent Linux Format, its offers the install choice, I click install, it unpacks the kernel, then freezes on a splash screen

Does the same with a downloaded Kubunto 6.10 Edgy ISO

On the other hand a Live DVD, running a 32 bit versio runs fine, and takes me as far as the partition stage - I stopped there as I've not resolved on a schema yet - I'm also concerned about what will happen if I install 32 bit on a 64 bit machine

Any ideas?

---

### Post by enopepsoo on 2007-03-05
running the 32 bit works fine on a 64 bit cpu.

It sounds like your install cd has a problem.  Try burning it again but with a slower speed, and if that doesn't work check the md5sum of your ISO.:KS

---

### Post by johnerskine on 2007-03-06
Thanks for the pointers.

I've burnt using K3B on my existing SuSE installation on another machine. K3B doesn'tr seem to offer different speeds.

Is the problem the type of CD (R) I'm using - it's a 52X?

Can I install at 32 bit, then upgrade to 64 bit using repositories?

---

### Post by Kilz on 2007-03-06
> **enopepsoo said:**
> running the 32 bit works fine on a 64 bit cpu.

That is not quite true. There is an ever growing population of people that have problems running the 32bit version on 64bit hardware. It is not the cure all some people make it out to be.

> **johnerskine said:**
> Thanks for the pointers.

I've burnt using K3B on my existing SuSE installation on another machine. K3B doesn'tr seem to offer different speeds.

Is the problem the type of CD (R) I'm using - it's a 52X?

Can I install at 32 bit, then upgrade to 64 bit using repositories?

No, you cant upgrade from the 32bit version to the 64bit version. Its a complete reinstall. I recommend using the alternate install cd for 64bit. It has a greater chance of success.

---

### Post by johnerskine on 2007-03-10
I still can't install, although I have now tried the following 

1. using the alternate install CD for AMD64 - no joy, just hangs
2. DVD's from the Linux store hangs at the same Kubuntu splash screen with 8/9 blue bars underneath

Any ideas?

Is there something I should disable in terms of hardware to see how it goes?

---

### Post by johnerskine on 2007-03-12
I've now tried OEM installation and text installation with Kubuntu DVD for AMD64 

On OEM installation its gets as far as 

"[28.6199553] libata version 1.20 loaded"

On text it also gets as far as 

"libata version 1.20 loaded"   

Hangs, with flashing cursor in both cases

Only other error message I get is slightly further up the screen

"[28.4543] drivers/rtc/hctosys.c unable to open rtc device (rtc.0)

Any ideas?

---

### Post by randara on 2007-03-12
Try with the option acpi=off

---

### Post by johnerskine on 2007-03-12
Thanks very much for this.

How do I set this? Is it in the BIOS?

---

### Post by randara on 2007-03-12
In the ubuntu cd main screen hit F1 to see the options, I think you could boot with something like** live acpi=off**

---

### Post by johnerskine on 2007-03-13
Thanks Randara - got a lot further after I put in ACPI=off

Still not working, but at least I have a new problem, the subject of another post!

Important to insert the whole command 

boot: install ACPI=off

at the prompt that you get when you hit F6 at the choose install options screen

---

