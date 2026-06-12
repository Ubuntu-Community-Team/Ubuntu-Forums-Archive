---
title: "are there any downsides to 64bit besides flash?"
date: 2007-07-04
forum: x86 64-bit Users (Pre April '08)
---

### Post by syxbit on 2007-07-04
i can't live without flash. (i know you can install firefox32 and do it that way)
but once gnash becomes good, i might switch
are there any other issues?

---

### Post by jamesford on 2007-07-04
i havent had any other issues and flash works just fine in 64 bit browser with nspluginwrapper

---

### Post by jespdj on 2007-07-04
Getting Flash to work in 64-bit Firefox is very easy with [nspluginwrapper](http://gwenole.beauchesne.info/en/projects/nspluginwrapper/help).

---

### Post by nss0000 on 2007-07-04
SY:

Recounting what I read on this NG -- and my own experience with DAPPERx64 --  usr issues  with x64U vary greatly ... consider cpu, mobo, U_version and 'toys' all to influence your own experience. Some "stuff" is just not well_supported in x64U.

Decide up-front if you can directly use the superior processing power & coincident multi_cpu support of a x64U version. 
I have both x32DAPPER & x64DAPPER installed on different kit ... and while the x32 kit is quick and smooth and without issue, it gathers dust. 

nss
****

---

### Post by syxbit on 2007-07-04
so all the stuff in the repo's (like thunderbird firefox etc..) is all compiled for x64?

---

### Post by John.Michael.Kane on 2007-07-04
You may want to read this [Please Read First Advantages and Disadvantages of 64bit. (Plus install Guides)]("http://ubuntuforums.org/showthread.php?t=368607")

---

### Post by incubus on 2007-07-04
> **syxbit said:**
> so all the stuff in the repo's (like thunderbird firefox etc..) is all compiled for x64?

Yes, if you install Ubuntu x86_64, all packages you get from the repositories are compiled for 64 bit.  That doesn't necessarily mean that their source codes have been *optimized* for 64 bit, but in general the binaries should be faster.

But so, what is the issue of running 64 bit and having Firefox 32 bit?  It seems to me that you win in all situations and stay the same in only one (Firefox).  Alternatively, many people report that nspluginwrapper works pretty well now.

incubus

---

### Post by RAOF on 2007-07-05
> **incubus said:**
> ...That doesn't necessarily mean that their source codes have been *optimized* for 64 bit, but in general the binaries should be faster.
...

Generally, of course, there **is** no 64bit optimisation to be done.  x86-64 is faster than IA32 only because IA32 has some horrible limitations that x86-64 doesn't.

---

### Post by incubus on 2007-07-05
> **RAOF said:**
> Generally, of course, there **is** no 64bit optimisation to be done.  x86-64 is faster than IA32 only because IA32 has some horrible limitations that x86-64 doesn't.

True, good point.

---

### Post by mcook2 on 2007-07-06
If you want support for some wireless networking cards - Linksys WUSB54G V1 USB ID 00192234 in my case - you will not be able to use ndiswrapper because it needs a 64-bit driver, and few such are available.

Also, the driver download page of the for-fee Linuxant driver says it requires a 64-bit driver compiled for x86-64 AMD.  I think even fewer of these may be available.

---

