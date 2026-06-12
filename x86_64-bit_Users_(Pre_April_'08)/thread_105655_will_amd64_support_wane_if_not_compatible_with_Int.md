---
title: "will amd64 support wane if not compatible with Intel 64?"
date: 2005-12-18
forum: x86 64-bit Users (Pre April '08)
---

### Post by linuxted on 2005-12-18
Here's food for thought?

Since Intel is the "800lb Gorilla" and probably won't want to be subserviate to the AMD64 architecture, is it likely that Linux will have to have both AMD64 and Intel64 distributions?

Also, will AMD64 Linux support wane if not compatible with Intel 64?

Thanks

---

### Post by nalmeth on 2005-12-19
Please correct me if I'm wrong (most likely)

Don't 64-bit platforms support any 64-bit hardware?

I have Intel64 chip and was using Amd64 Ubuntu, and was experiencing problems, but I assumed they were because 64-bit software is not very developed yet.

Should I have used a different kernel (I'm happily on i386 now)

---

### Post by RAOF on 2005-12-19
Intel has already made a 64bit instruction set, called IA64.  The Itanium line of chips implements it.  Never heard of it?  They are (almost were) server chips.  But no one liked them, and they're dying a quiet death.

The 64bit Pentiums, with the EM64T or whatever Intel wants to call it, are implementing **AMD**'s 64bit x86 extensions, x86_64.  It is unlikely that they'll want to break this compatibility (in important) ways.  Any problems you have with Breezy64 on an Intel chip are much more likely buggy (or incomplete) software problems than problems with your chip.

---

### Post by DancingSun on 2005-12-20
[QUOTE=linuxted]Here's food for thought?

Since Intel is the "800lb Gorilla" and probably won't want to be subserviate to the AMD64 architecture, is it likely that Linux will have to have both AMD64 and Intel64 distributions?

Also, will AMD64 Linux support wane if not compatible with Intel 64?

Thanks[/QUOTE]
You may safely dismiss that thought.  AMD64 is no revolutionary architecture, it's just like what Intel's 32-bit 80386 architecture did to the 16-bit 8086 architecture 20 years ago.  Currently, Intel has a more advanced 64-bit architecture called IA-64 (which isn't natively compatible with software written for 80386), but when AMD played safe and came out with AMD64 and the market reponded favorably (because the old software can still run on the new architecture without compromise), Intel decided to unveil EM64T, which is their implementation of the AMD64 architecture, and to shift their focus from IA-64 to EM64T.

I think AMD64 will be with us for a looong time.  The market seems to like CPU architectures that are backwards compatible with the previous one, so even when it is time for AMD64 to die off, it's likely that the successor will be able to run software that was created for AMD64.  If IA-64 were to ever supplant AMD64, it would first need to be able to run AMD64-compatible software at a speed that it would provide a performance boost when compared to the existing chips (which is not the case right now).

Reference: [http://en.wikipedia.org/wiki/AMD_64#Market_analysis](http://en.wikipedia.org/wiki/AMD_64#Market_analysis)

---

