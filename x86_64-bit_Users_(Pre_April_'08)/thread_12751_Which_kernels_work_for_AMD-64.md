---
title: "Which kernels work for AMD-64?"
date: 2005-01-26
forum: x86 64-bit Users (Pre April '08)
---

### Post by quackking on 2005-01-26
System: Shuttle SK83G Barebones system (mini case) with AMD64 3000+ and Maxstor 200 SATA drive.

I have had a lot of trouble with actual AMD64 installations (see some of the other threads here) but the standard, pressed-disk Warty i386 install works fine. 

I was wondering - when I do a dist-upgrade, or use Synaptic, it installs the newest *-386 kernel image. I have installed some other systems with AMD processors and they can also make use of the *-686 images. Can the AMD64 CPU be used with a *-686 kernel?

Sorry for this newbie question.

---

### Post by martijntje on 2005-01-28
i686 kernel should work just fine, and probably faster too :)

---

### Post by Tichondrius on 2005-01-31
[QUOTE=martijntje]i686 kernel should work just fine, and probably faster too :)[/QUOTE]

Only amd64 kernels are running in 64 bit !  Basically the kernel that came with the amd64 distribution. If you compile your own kernel, you can choose processor family - generic x86-64, Intel x86-64, or Athlon64, but they are all running the amd64 instruction set, which is the standard de-facto 64 bit instruction set extension for x86 platform.

---

### Post by tonym on 2005-02-05
[QUOTE=quackking]System: Shuttle SK83G Barebones system (mini case) with AMD64 3000+ and Maxstor 200 SATA drive.

I have had a lot of trouble with actual AMD64 installations (see some of the other threads here) but the standard, pressed-disk Warty i386 install works fine. 

I was wondering - when I do a dist-upgrade, or use Synaptic, it installs the newest *-386 kernel image. I have installed some other systems with AMD processors and they can also make use of the *-686 images. Can the AMD64 CPU be used with a *-686 kernel?

Sorry for this newbie question.[/QUOTE]
 I use the K7 kernel and have had no problems.

Tony Middleton

---

