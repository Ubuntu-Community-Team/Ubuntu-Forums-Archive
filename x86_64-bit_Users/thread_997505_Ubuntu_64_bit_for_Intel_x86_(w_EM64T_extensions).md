---
title: "Ubuntu 64 bit for Intel x86 (w/ EM64T extensions)"
date: 2008-11-29
forum: x86 64-bit Users
---

### Post by cosmini on 2008-11-29
hi all,

it appears that 64 bit Ubuntu installs is available only for the AMD architecture.  I have tried to install it on a vmware based on an Intel 64 bit (EM64T) architecture, a Dell laptop and it complained that the type of CPU is not supported.

Being a newbie Linux user, moreso an even newer Ubuntu one, I was wondering if it is possible to build a kernel for EM64T architecture and/or what would it take to do so.  

Basically, I'd like to install MySQL 64bit on top of a 64bit laptop of Intel x86 (w/ EM64T extensions), otherwise I'm stuck in a 32bit worlds, which, for large databases is not exactly what I had in mind.  Do I have to go out and get an AMD based machine and if so, is there a particular chipset that is supported -- this as a last resort?  ;-(

thx much for any suggestions,
Cos

---

### Post by wd5gnr on 2008-11-30
This should work. AMD64 should be the same as Intel's normal 64-bit mode (formerly EM64T) although not IA64 which is a whole different thing.

[http://en.wikipedia.org/wiki/X86-64](http://en.wikipedia.org/wiki/X86-64)

Could it be a VMWare issue?

---

### Post by scottmac112 on 2008-11-30
Check in the BIOS and make sure that EM64T isn't turned off. Though I don't even know if that sort of thing can be turned off. I'm using an AMD machine. See if there's an option.

---

### Post by cosmini on 2008-11-30
thanks all,
I will look into the BIOS as well as VMWare setup params and take it from there... if others got it to work w/ EM64T chipsets....

thx a big bunch,
Cos

---

### Post by bford16 on 2008-11-30
> **cosmini said:**
> hi all,

it appears that 64 bit Ubuntu installs is available only for the AMD architecture.  

I thought the 64bit Ubuntu was 'generic' except for IA64, whatever that is...

---

### Post by Reiger on 2008-11-30
I think the problem is your VmWare: you should check the settings of your virtual machine and make sure Virtual Address Extension (or whatever it is called) is turned on; otherwise VmWare will pretend to be a 32bit machine -- and 64bit software simply won't run on 32bit architectures. ;) 

This is based on experience with Virtual Box, but the key point probably still applies: your VmWare is pretending to be a 32bit machine which you need to fix by enabling some kind of 'virtual address extension' thing.

AMD64 is AMD's implementation of 64bit systems that maintains compatibility with 32bit software. Intel originally had its own implementation but apparently it failed to deliver so they switch to what is pretty much the same thing as AMD64. Only they call it EMT. EDIT: AMD64 as software architecture therefore (pretty much) means "Intel 64bit/AMD 64bit" compatible, also known as x86_64. This applies to Intel's Core2Duo (E), Centrino Dual-Core, Pentium Dual-Core and Core2Quad (Q) lines; dunno about Core i7.

---

