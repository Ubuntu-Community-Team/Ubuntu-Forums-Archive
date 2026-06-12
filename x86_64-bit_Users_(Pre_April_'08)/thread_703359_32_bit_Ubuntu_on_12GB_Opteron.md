---
title: "32 bit Ubuntu on 12GB Opteron?"
date: 2008-02-21
forum: x86 64-bit Users (Pre April '08)
---

### Post by kmand on 2008-02-21
Tried this in the install forum with no reply, but thought there may be some info here.

We want to run a 32 bit Ubuntu kernel on a 12GB dual processor Opteron server (Sun V20Z). The box is going to serve remote desktops (Sunray) and there are some driver issues that dictate a 32 bit kernel.

Is this possible and still make use of the 12GB (with 4GB limits per address space)?

We tried booting the standard desktop Gutsy 32 bit distribution disk, and the boot fails falling into an initramfs prompt. Do we need a different distribution disk?

---

Aside from the 32 bit issue, is a desktop or server distribution appropriate? It needs to serve full featured remote desktop , but will mainly be a client for other services.

---

### Post by tgalati4 on 2008-02-21
You might try installing using the Alternate CD or Server CD.  The Live CD is really for common desktop hardware.

As far as splitting up 12 GB, someone else with virtual machine experience will have to answer.  A standard 32-bit install will address about 3.2 GB--the rest reserved for system resources.

What prevents you from running a 64-bit server version of Linux?

---

### Post by kmand on 2008-02-21
>What prevents you from running a 64-bit server version of Linux?

The Sunray software is designed for 32 bit, in particular the Sunray specific PAM module is 32 bit only.

---

### Post by felker2 on 2008-02-21
> **kmand said:**
> >What prevents you from running a 64-bit server version of Linux?

The Sunray software is designed for 32 bit, in particular the Sunray specific PAM module is 32 bit only.

Sunray is available in both 32 and 64-bit, see [http://www.sun.com/software/sunray/techspecs.jsp](http://www.sun.com/software/sunray/techspecs.jsp) saying:

> 
Sun Ray Software 4 09/07 runs on the following versions of the Linux operating system:

    * SuSE Linux Enterprise Server (SLES) 9 with Service Pack 3 (32-bit and 64-bit)
    * Red Hat Enterprise Linux Advanced Server (RHEL AS) 4 Update 3 (32-bit and 64-bit)


However, the bad thing is that Sun Ray apparently is *not* supported on Ubuntu.


Apart from all this, you can run 32-bit apps on a 64-bit OS. So you can install 64-bit Linux and have 12 GB RAM available, and then start a 32-bit app on that.

---

### Post by kmand on 2008-02-21
The 64 bit Sunray support is pretty RHEL 4 and SLES 9 specific. Unfortunately those are enterprise releases with thin and dated desktop support. We want to run Ubuntu since it has rich and up to date desktop applications.

For the remote desktops the 64 bit address spaces are not relevant, and 32 bit is fine. So the question is can we boot a 32bit ubuntu on Opteron which will use 12GB of ram divided amoung multiple users.

---

### Post by Kilz on 2008-02-21
> **kmand said:**
> The 64 bit Sunray support is pretty RHEL 4 and SLES 9 specific. Unfortunately those are enterprise releases with thin and dated desktop support. We want to run Ubuntu since it has rich and up to date desktop applications.

For the remote desktops the 64 bit address spaces are not relevant, and 32 bit is fine. So the question is can we boot a 32bit ubuntu on Opteron which will use 12GB of ram divided amoung multiple users.

None of the stock 32bit kernels will not see that much ram.

---

### Post by jespdj on 2008-02-21
Doesn't the kernel of 32-bit Ubuntu Server have built-in support for [PAE](http://en.wikipedia.org/wiki/Physical_Address_Extension), which means that if you have a processor that supports it, it could access up to 64 GB of memory?

---

### Post by kmand on 2008-02-21
> **jespdj said:**
> Doesn't the kernel of 32-bit Ubuntu Server have built-in support for [PAE](http://en.wikipedia.org/wiki/Physical_Address_Extension), which means that if you have a processor that supports it, it could access up to 64 GB of memory?

I wondered about this. Does PAE on a 32 bit kernel work with real 64 bit processors like Opteron, or just the 32 bit processors like the Pentium and Athalon cpu's with an extension mode?

---

### Post by crjackson on 2008-02-21
I don't know much about the server kernel, but I've read where others have compiled custom kernels in Ubuntu 32 to support PAE.

Come to think if it, shouldn't that be standard?

---

### Post by felker2 on 2008-02-22
> **kmand said:**
> I wondered about this. Does PAE on a 32 bit kernel work with real 64 bit processors like Opteron, or just the 32 bit processors like the Pentium and Athalon cpu's with an extension mode?

You could just boot a Ubuntu live CD and see what happens (and report it back here). The nice thing about Ubuntu and other OSS: you can just try. it out for free! ;-)

BTW: you can easily see if your CPU supports PAE. Here's the result for my Core Duo:


sander@fujitsu:~$ cat /proc/cpuinfo | grep pae
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx constant_tsc pni monitor est tm2 xtpr
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx constant_tsc pni monitor est tm2 xtpr
sander@fujitsu:~$

So apparently even my Core Duo does PAE!

---

### Post by fjgaude on 2008-02-22
Here's what I get from my Intel Core 2, 45nm E8400:

frank@sunshine:~$ cat /proc/cpuinfo | grep pae
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm syscall nx lm constant_tsc pni monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr lahf_lm
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm syscall nx lm constant_tsc pni monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr lahf_lm

Wow, lots of things besides PAE, eh?

---

