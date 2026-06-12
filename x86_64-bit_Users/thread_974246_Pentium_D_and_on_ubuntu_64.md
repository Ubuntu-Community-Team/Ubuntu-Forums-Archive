---
title: "Pentium D and on ubuntu 64"
date: 2008-11-07
forum: x86 64-bit Users
---

### Post by Shady3D on 2008-11-07
i am a windows XP x64 user and i want to convert to Linux, so i downloaded Ubuntu 8.10 x64, and then booted from the CD but a few second and it makes exception then nothing happens, so i tried Ubuntu x86 it worked with no problem.

also i tried to run the Ubuntu x64 with virtual machine, also the same problem and tells me the processor don't support x64 mode.

so i checked for that and i found Pentium D supports x64, and i am Autodesk Maya user and it only supports x64 in Linux

so what can i do.:confused::confused::confused:

---

### Post by dabl on 2008-11-07
Yep, Intel's specs for the Pentium D show "EM64T", so that means it is 64-bit.

Prolly you made a bad CD.  Refresher:

1. Verify the md5sum of your downloaded ISO

2. Burn speed is 4X, and use DAO mode if you can

3. Sometimes you make a coaster anyway, and sometimes the lens on your optical drive can use cleaning.

---

### Post by saru411 on 2008-11-07
Isn't Pentium D EMT64 and not AMD64. I'm not sure if I'm correct on this matter but I know the 2 aren't the same.

---

### Post by Coreigh on 2008-11-07
Is it possible that although the CPU is 64bit, the system is not fully 64bit compatible or compliant?

---

### Post by dabl on 2008-11-07
AFAIK, EM64T = 64-bit = AMD64.

I don't think it (the Pentium D) would even run on a motherboard that's not designed to support a 64-bit CPU and its RAM, so it should be ready for the 64-bit OS (as it was for 64-bit Windows XP).  ;-)

---

### Post by Shady3D on 2008-11-07
so the CPU is 64 but my motherboard is not compatible or what.

---

### Post by dabl on 2008-11-07
> **Shady3D said:**
> so the CPU is 64 but my motherboard is not compatible or what.

Sorry -- I wasn't clear.  Your hardware should run the 64-bit Ubuntu just fine.  I think your problem must be a bad CD burn or something like that, not an incompatibility with your hardware.  :)

---

### Post by Shady3D on 2008-11-07
so i made another CD and tried but the same problem.

---

### Post by dabl on 2008-11-07
> **Shady3D said:**
> so i made another CD and tried but the same problem.

Try F4 and choose "Safe Graphics" mode.

---

### Post by Shady3D on 2008-11-08
i tried all this and the same error goes every time early exeption and some hexa numbers

---

### Post by Artemis3 on 2008-11-08
If your processor doesn't support 64 bit, it will tell you at boot just like you see in the virtual machine.

So this is another problem.
Be more specific: Motherboard, video, etc.

When booting from CD, there is an option to check integrity, use this choice once.

The Debian/Ubuntu "amd64" architecture actually also means "emt64", i guess this is simply because AMD made it first, and intel followed later.

---

### Post by Shady3D on 2008-11-08
well i don't think that the GPU will affect but for the 

motherboard its: 
manufacturer >> abit 
model >> AW8 (intel i955-ICH) 1.0
chipset >> Intel i955x
southberg >> Intel 82801GB (ICG7/R)
LPCIO >> Winbond W83627EHF

and the processor is Pentium D 945
package socket 775 LGA
and instruction set is >> MMX,SEE,SEE2,SEE3,EM64T

if u need more info tell me.

also i found a program or something like that from VMWare to check if i can host a guest x64 and it told me that i cant host so is it for just visualization or in general and how come i am using x64 version of windows and having so much trouble with Linux.

---

### Post by Shady3D on 2009-09-13
the problem was that i had 3GB's of memory and thats what was doing the problem

---

