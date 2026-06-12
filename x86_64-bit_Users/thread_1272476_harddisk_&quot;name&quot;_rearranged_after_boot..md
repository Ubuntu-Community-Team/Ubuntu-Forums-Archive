---
title: "harddisk &quot;name&quot; rearranged after boot."
date: 2009-09-22
forum: x86 64-bit Users
---

### Post by SudoLight on 2009-09-22
Hi there,

I have a 8.04.3 server running on a asus p5bvc-4l. The server is primarily used as a samba server.

I have set up one old 100 GB harddisk as boot and system disk and two 1TB disks setup as SW raid0 named md0.

In normal condition the sdc1 is the boot disk (100GB) and the SW Raid0 disks are sdb1 and sdc1.
  
The problem is sometimes after boot the sda1 and sdb1 (the two 1TB disks) are rearranged during the boot. Which means they are now referred to as sdb1 and sdc1. And the boot disk has now become sda1 or sdb1. And as a result the SW raid0 fails.

Does anyone know how to solve this problem?

thanks in advance.

---

### Post by BbUiDgZ on 2009-09-22
> **SudoLight said:**
> Hi there,

I have a 8.04.3 server running on a asus p5bvc-4l. The server is primarily used as a samba server.

I have set up one old 100 GB harddisk as boot and system disk and two 1TB disks setup as SW raid0 named md0.

In normal condition the sdc1 is the boot disk (100GB) and the SW Raid0 disks are sdb1 and sdc1.
  
The problem is sometimes after boot the sda1 and sdb1 (the two 1TB disks) are rearranged during the boot. Which means they are now referred to as sdb1 and sdc1. And the boot disk has now become sda1 or sdb1. And as a result the SW raid0 fails.

Does anyone know how to solve this problem?

thanks in advance.

i can't help but also have the same trouble with a ubuntu 8.04 Desktop machine with three hds, everything was fine untill i mounted one of the discs for a samba share "/shared" 

now when the device id changes i need to remount sda1 or sdb1 as "/shared"

also note one of my drives is ata and the other sata.

---

### Post by SudoLight on 2009-09-22
I also tried to "fix it" the first time I saw the problem, leading into total fubar of md0. Later I found out that normally doing a second reboot, the disks come up in the right order. 

But it's a bit annoying that I have to check if the md0 is running or not.

I don't know if it makes any difference, but the sda1 and sdb1 are sataII, and the sdc1 is an old pata.

---

### Post by dcstar on 2009-09-23
> **SudoLight said:**
> I also tried to "fix it" the first time I saw the problem, leading into total fubar of md0. Later I found out that normally doing a second reboot, the disks come up in the right order. 

But it's a bit annoying that I have to check if the md0 is running or not.

I don't know if it makes any difference, but the sda1 and sdb1 are sataII, and the sdc1 is an old pata.

You might be able to replace sdX designations with UUIDs, see if you can do this.

---

### Post by SudoLight on 2009-09-23
Do you mean to rebuild the array with UUIDs?

---

### Post by 3L33T on 2009-09-23
> **SudoLight said:**
> 
  
The problem is sometimes after boot the sda1 and sdb1 (the two 1TB disks) are rearranged during the boot.

Hmmmm, I thought this only happens to USB drives.

Take a look at [THIS ARTICLE]("http://bit.ly/E8CUZ").  It shows how to disable

---

