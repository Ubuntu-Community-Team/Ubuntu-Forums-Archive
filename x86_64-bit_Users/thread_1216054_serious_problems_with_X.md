---
title: "serious problems with X"
date: 2009-07-17
forum: x86 64-bit Users
---

### Post by dd1linux on 2009-07-17
I had ubuntu 9.04 running perfectly fine for about 4-6 months until one day the X server wouldn't start.  I tried everything I knew (I had run into the problem before), and then read the stickies, but none of the advice has worked out. So i have a fresh install and I am running 9.04 now without the nvidia drivers, and everything else works fine.  However, no matter which way I try to install the nvidia drivers, I get X failure.  Errors including (in boot order):

-2.89991 [ACPI] Expected reference element, found none (i dont think this  ones the problem.)

-[8.190340]powernow-k8: Your BIOS does not support ACPI_PSS in a way that linux understands .... please see .... for help ....

-no devices detected

-no screens found

I have two 8600GT's with two monitors plugged into only one of the graphics cards ( I suspect this may be causing some trouble, but I dont know why, as it never has before)

I have tried installing the 180 nvidia driver through synaptic, terminal, and several other ways.  Also, it is not a hardware issue, because windows runs perfectly fine.  I ran into many problems when I first started using linux that were somewhat like this(dealing with the X server), but I cannot fix this one!  Any help would be greatly appreciated.   

P.S.:  If you need any more system info or more exact error messages, please let me know.

---

### Post by d4rk5h4dow5 on 2009-09-07
> **dd1linux said:**
> I had ubuntu 9.04 running perfectly fine for about 4-6 months until one day the X server wouldn't start.  I tried everything I knew (I had run into the problem before), and then read the stickies, but none of the advice has worked out. So i have a fresh install and I am running 9.04 now without the nvidia drivers, and everything else works fine.  However, no matter which way I try to install the nvidia drivers, I get X failure.  Errors including (in boot order):

-2.89991 [ACPI] Expected reference element, found none (i dont think this  ones the problem.)

-[8.190340]powernow-k8: Your BIOS does not support ACPI_PSS in a way that linux understands .... please see .... for help ....

-no devices detected

-no screens found

I have two 8600GT's with two monitors plugged into only one of the graphics cards ( I suspect this may be causing some trouble, but I dont know why, as it never has before)

I have tried installing the 180 nvidia driver through synaptic, terminal, and several other ways.  Also, it is not a hardware issue, because windows runs perfectly fine.  I ran into many problems when I first started using linux that were somewhat like this(dealing with the X server), but I cannot fix this one!  Any help would be greatly appreciated.   

P.S.:  If you need any more system info or more exact error messages, please let me know.

Make any headway on this cause Im getting the same problem running two 7600gt cards that are SLI'd in Windows 7 I tried turning off acpi but that didn't seem to work 

I was givin this so it might work for you im still in the same spot. [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

this only happens after going to the nvidia 180 / 185 drivers ohh and I also tried the 173 version as well.

---

