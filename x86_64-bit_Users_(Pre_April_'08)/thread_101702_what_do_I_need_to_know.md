---
title: "what do I need to know?"
date: 2005-12-10
forum: x86 64-bit Users (Pre April '08)
---

### Post by Steve132 on 2005-12-10
I am installing a system for my friend, with an AMD64 3700+.  I was curious, what should I worry about with this system?  I am an experienced user of i386, but I don't understand the way the system interacts with i386 programs on an AMD64 kernal and version of Ubuntu.  

Basically, I guess I have a few questions: 
First, is it even possible to install the i386 version of Ubuntu on an AMD 64 architecture?  Like, I realize it wont be as fast, but is it doable to make the AMD chip act like an x86?  Or do I not even have a choice here, because of compatibility with motherboards and opcodes?

Second, if I do decide to install the AMD64 OS, will 32-bit versions of packages still be available/still be runnable?  Like the nvidia binary drivers and stuff?  What if a package is not yet on AMD64?  Can I install it anyway?

My friend is not a power user at all, and even though I am doing the intitial configuration and setup, is probably incapable of doing complex things to implement workarounds.  However, I would like his new computer to take advantage of the hardware.  Should I just use the i386 version and know it will be stable?  or should I attempt to set up the AMD64?  What do other people think?

---

### Post by hod139 on 2005-12-10
[QUOTE=Steve132]First, is it even possible to install the i386 version of Ubuntu on an AMD 64 architecture?  Like, I realize it wont be as fast, but is it doable to make the AMD chip act like an x86?  Or do I not even have a choice here, because of compatibility with motherboards and opcodes?[/QUOTE]
You can install the i386 version on x86_64 versions of AMD, like the Athlon64.  But not on an AMD Opteron because an Opteron is 64 bit only.  What do you mean, "it won't be as fast"?  The i386 build may even run slightly faster on an x86_96 chip than on a 32 bit chip.  Or do you mean i386 won't run as fast as AMD64?  That may be correct, but only in floating point intensive operations where the larger registers come into play.  I would sugest the AMD64 version for the AMD Athlon/Opteron chip though, simply because other kernel specific options have been tuned better, not just the register size. 

[QUOTE=Steve132] Second, if I do decide to install the AMD64 OS, will 32-bit versions of packages still be available/still be runnable?  Like the nvidia binary drivers and stuff?  What if a package is not yet on AMD64?  Can I install it anyway?
[/QUOTE]
You can not mix 32 bit binaries with 64 bit, so the 32-bit packages will not be available.  Most packages have been ported to AMD64 though.  If a package is not available you still have the option of building it yourself if the code is open, or begging the developers to build a AMD64 binary.

[QUOTE=Steve132]My friend is not a power user at all, and even though I am doing the intitial configuration and setup, is probably incapable of doing complex things to implement workarounds.  However, I would like his new computer to take advantage of the hardware.  Should I just use the i386 version and know it will be stable?  or should I attempt to set up the AMD64?  What do other people think?[/QUOTE]
I would choose the AMD64 bit version, unless you know of any specific packages he would need not available yet for AMD64.

---

