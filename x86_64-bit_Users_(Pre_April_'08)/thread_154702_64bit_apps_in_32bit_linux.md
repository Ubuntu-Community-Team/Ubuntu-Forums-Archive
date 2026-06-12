---
title: "64bit apps in 32bit linux"
date: 2006-04-03
forum: x86 64-bit Users (Pre April '08)
---

### Post by dmb on 2006-04-03
Is it possible to run 64bit apps in a 32 bit kernel? Just curious. Is there a way to chroot and do this?

---

### Post by mcmillan on 2006-04-03
I don't think it's possible but I'm not certain. I know the other way is possible with chroot. I don't know the details of how that works to know if it would also work to have a chroot into 64bit. If you want to have 64bit why not install that version and setup the chroot for 32bit?

---

### Post by RS3York on 2006-04-04
The short answer is no.

If you need to run both 32-bit & 64-bit applications, then you should install a 64-bit version of (_)ubuntu and add a 32-bit chroot environment.

The long answer is you can run 64-bit guests on a 32-bit host with virtualisation technology (such as VMware) if you have the right processor (AMD64 and relatives). 

"[VMWare's] Workstation 5.5 introduces support for virtual machines with 64-bit guest operating systems, running on host machines with the following processors: AMD&#8482; Athlon&#8482; 64, revision D or later; AMD Opteron&#8482;, revision E or later; AMD Turion&#8482; 64, revision E or later, AMD Sempron&#8482;, 64-bit-capable revision D or later (experimental support); and Intel® EM64T VT-capable processors (experimental support)
...
64-bit guest operating system support added for Windows Vista x64 Edition (experimental), Windows Server 2003 SP1, Windows XP Pro, Red Hat Enterprise Linux 4, Red Hat Enterprise Linux 3, SUSE Linux 10, SUSE Linux Enterprise Server 9, SUSE Linux Pro 9.3, SUSE Linux Pro 9.2, SUSE Linux Pro 9.1, Solaris 10 (experimental), FreeBSD 5.3 (experimental), FreeBSD 5.4 (experimental), Ubuntu Linux 5.10 (experimental), Ubuntu Linux 5.04 (experimental)."
--http://www.vmware.com/support/ws55/doc/releasenotes_ws55.html

---

### Post by marvinthesad on 2006-07-01
[QUOTE=RS3York]The short answer is no.
[/QUOTE]

There is maybe another answer:
We run a 64-bit chroot environment (sarge debian-amd64) inside a 32-bit installation (sarge i386), BUT with the running kernel replaced with an amd64 kernel.

In debian we have to build an i386-package from the amd64-enabled kernel.

I'm at the moment trying to figure out, howto do this best in kubuntu.
Anyone heard of something like that? 

greetings.

---

