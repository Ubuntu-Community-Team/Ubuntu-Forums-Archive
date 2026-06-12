---
title: "what % of apps on gutsy x64 are compiled for 64bit?"
date: 2007-10-19
forum: x86 64-bit Users (Pre April '08)
---

### Post by syxbit on 2007-10-19
I'd heard that lots of apps are just x86 binaries
true?

---

### Post by John.Michael.Kane on 2007-10-19
> **syxbit said:**
> I'd heard that lots of apps are just x86 binaries
true?

In theory all applications listed in the Ubuntu repository should have a 64bit compiled counterpart. This of course is excluding applications, and drivers who source is closed. All one would have to do is simply look through the 64bit repository.

Example
conky (1.4.7-0ubuntu2) [universe]
Architectures available
amd64 	
i386 	
powerpc 	

When you install conky on 64bit the dependencies requested are compiled in 64bit as well. If you call conky on i386 the same packages have i386 counterparts. Same for would hold true for powerpc.

To find out if the package being installed calls for 32bit dependencies you can easly see that durring the install through synaptic. 

Take flash plugin it calls nspluginwrapper as well as ia32bit-libs  which clearly means this package is not compiled for 64bit, and requires 32bit libs, and a wrapper to get around not being natively compiled.

---

