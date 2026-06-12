---
title: "upgrade from i386 to amd64"
date: 2008-03-17
forum: x86 64-bit Users (Pre April '08)
---

### Post by Jim_1981 on 2008-03-17
I want to go from the i386 version of gutsy to the amd64 one. My questions are these:

1) Do I need to reinstall or can I just use apt to install the amd64 kernel?

2) Are there any compatibility issues with packages? The only software I've installed that isn't in the repositories is mathematica, which has one version for all flavours of linux.

3) How much difference with there be? I do use my computer for number crunching as well as general web browsing (boinc, mathematica and numerical solution of maths problems in C++ to name a few things) 

Cheers :)

---

### Post by NightwishFan on 2008-03-17
You need to reinstall. Yes it is faster. Flash is iffy but it works. Read the sticky.

---

### Post by fjgaude on 2008-03-17
> **Jim_1981 said:**
> I want to go from the i386 version of gutsy to the amd64 one. My questions are these:

1) Do I need to reinstall or can I just use apt to install the amd64 kernel?

[COLOR="Blue"]You have to fresh install the 64-bit version, as all the support programs are 64-bit, not just the kernel.[/COLOR]

2) Are there any compatibility issues with packages? The only software I've installed that isn't in the repositories is mathematica, which has one version for all flavours of linux.

[COLOR="Blue"]It's just fine now a-days.[/COLOR]

3) How much difference with there be? I do use my computer for number crunching as well as general web browsing (boinc, mathematica and numerical solution of maths problems in C++ to name a few things)

[COLOR="Blue"]Everything looks and feels the same between the two versions.[/COLOR]

Cheers :)

Let us know how you make out.

---

### Post by Jim_1981 on 2008-03-17
Cheers very much :) The reason I ask is my computer at work is a fairly lowly celeron 430 system and my home one is a athlon 64 3700+. My home computer is a bit faster, but not all that much -  I expected my home computer to show the work one a clean pair of heels.

---

### Post by shane2peru on 2008-03-17
Jim,

Make sure you DO NOT keep your /home partition config files.  That will greatly downgrade your 64bit experience!  I did it, and it wasn't good, many problems, you must start with a clean /home NO HIDDEN files that start with a .  Kind of a pain, but it will be worth it.

Shane

**EDIT:**  I second the other fellows suggestion, read the sticky, it has great setup instructions.

---

### Post by jespdj on 2008-03-18
> **Jim_1981 said:**
> 3) How much difference with there be? I do use my computer for number crunching as well as general web browsing (boinc, mathematica and numerical solution of maths problems in C++ to name a few things)
Especially for number crunching you would get a performance gain of up to 20-30% with the 64-bit version compared to 32-bit.

---

