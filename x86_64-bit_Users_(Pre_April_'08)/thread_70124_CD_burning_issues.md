---
title: "CD burning issues"
date: 2005-09-28
forum: x86 64-bit Users (Pre April '08)
---

### Post by rfreidel on 2005-09-28
I am a long time Linux/FreeBSD user that just put together a X2 3800+ system on an Asus A8n-E mainboard, running 2.6.12-9-amd64-k8-smp. I have both a cd burner and a  dvd burner on the ide controller, and run off a sata disk.
Problem is I can't seem to burn a cd.
When I do a sudo cdrecord --scanbus, all I see is the sata disk. I have tried k3b, it see's both cd writer's, but cannot burn to either. I have tried every other cd burning app available.
Only thing I can figure out is that the 2.6.12-9-amd64-k8-smp kernel lacks support for atapi cd burners. 
Does any one know if there is support in the kernel? Maybe I am just going about it incorrectly. But I did burn a cd when i had gentoo installed.

---

### Post by rfreidel on 2005-09-29
I discovered the proper module hadn't been installed. All I had to do was

sudo modprobe pktcdvd

Then I could burn a cd with graveman... interesting to note, k3b still didn't work.

---

### Post by DancingSun on 2005-09-29
I thought Nautilus supports CD-burning internally, no?
I haven't use the Nautilus CD-burning support yet (I think you just drag files to the CD/DVD-Burner's window), but GNOMEBaker works pretty nicely.  I've been using it to burn additional copies of the Ubuntu install and Live CD.

---

### Post by rfreidel on 2005-09-30
Normally it does, but the module hadn't been loaded. It works fine since I added the module name to /etc/modules.

---

