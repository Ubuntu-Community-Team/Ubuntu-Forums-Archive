---
title: "Edgy Eft Installation: Disk Boot Failure on 64 bit"
date: 2006-10-28
forum: x86 64-bit Users (Pre April '08)
---

### Post by Amd4200 on 2006-10-28
First of all my configuration:

1) Motherboard Foxconn NF4UK8AA Nforce 4 Ultra sock. 939
2) Amd Athlon64 4.200+ X2 Dual Core boxed 939
3) 1 Gb Ram DDR400 ( timings default )
4) Asus Geforce 7600GT 256 Mb (PCI-Express 16x)
5a) Hard Disk Western Digital 80Gb 7.200 rpm 8 Mb buffer IDE -----> Blank
5b) Hard Disk Seagate Barracuda 200Gb SATA-I 8 Mb buffer ---> Windows XP Professional
5c) Hard Disk Seagate Barracuda 200Gb SATA-I 8 Mb buffer ---> full of important things for me
6) Bios boot sequence : a) western digital, b) Seagate 1 XP Prof
7) Bios: ACPI and APIC activated

The problem is very simple: I try to install Edgy Eft 6.10 and, after a strange message at the beginning of the procedure (tell about your hw vendor - it's an error but i don't know about what beacuse the scrolling is very fast), the system hangs at the 92% of the installation for something like 10 minutes. After this long wait the procedure goes on. It askes me if i want to use Grub because of the presence of Xp Professional and then reboot....but there's no presence of Ubuntu !!!!!!!!!!!!

I tried to disable the SATA Disks from bios in order to make the machine boot only with the Western Digital disk used dedicated to Ubuntu but the message is: DISK BOOT FAILURE....as the installation has done nothing at all.....

---

### Post by Amd4200 on 2006-10-28
I've just tried to install without the sata disks, leaving phisically from my case and only with the Western Digital EIDE Disk inside...

I've tried the alternate and the desktop version but nothing...the same problem and the same error

DISK BOOT FAILURE ](*,) ](*,) ](*,) ](*,)

---

### Post by Amd4200 on 2006-10-29
Nobody can help me???

Nobody has an idea about this?

---

### Post by kuja on 2006-10-29
I've heard of a similar issue before, and I forget how exactly they fixed it. I'll look it up. Meanwhile, try completely disconnecting either all of the SATA drives, or all of the IDE drives, and do the installation. It should let you then.

---

### Post by Amd4200 on 2006-10-30
> **kuja said:**
> I've heard of a similar issue before, and I forget how exactly they fixed it. I'll look it up. Meanwhile, try completely disconnecting either all of the SATA drives, or all of the IDE drives, and do the installation. It should let you then.

I've already tried! But the problem is always the same...

How is it possible??? It's a normal system with an ide disk !!!

---

### Post by kuja on 2006-10-30
[http://ubuntuforums.org/showthread.php?t=216039&highlight=boot](http://ubuntuforums.org/showthread.php?t=216039&highlight=boot)

This thread looks like it may be related. Try the steps that they suggest and see if it helps.

---

### Post by mrhealthpatriot on 2006-11-01
No, the problem is not with booting. It is during the installation.
I accidently installed the server cd of Edgy Eft, which worked fine. 6.06 alternate installed fine. Just not 6.10.

---

### Post by Amd4200 on 2006-11-02
> **mrhealthpatriot said:**
> No, the problem is not with booting. It is during the installation.
I accidently installed the server cd of Edgy Eft, which worked fine. 6.06 alternate installed fine. Just not 6.10.

You're saying the problem is during the installation...uhm...i think this is true !

Do u think i need to install the server edgy eft version?

---

