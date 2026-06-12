---
title: "SATA VIA 8237 RAID 0 problem"
date: 2006-08-01
forum: x86 64-bit Users (Pre April '08)
---

### Post by kartikk on 2006-08-01
:confused: 

I have the following config.

Sata Raid 0 array(2 80gb disks), 1 IDE 80gb HDD 1 GB RAM AMD 64 3000+



SATA RAID 0 array which has Windows XP & Windows x64bit installed.
I downloaded Ubuntu amd64 & installed it on the IDE drive. Installed perfectly well but grub cant see the RAID array & the system displays them as unallocated partitions. I REALLY need to boot into WinXP. 

1. Can someone please help me, how do I get the multiboot option so that grub can understand that two OS's are present on the RAID array. ?

2. I dont want to loose data on the RAID drives so is there a package/software which runs on 64bit ?

3. I'm a total newbie to Linux & after reading a lot of other posts I could not find any resonalbe working solutions.


PLEASE HELP #-o 

Thanks

---

### Post by RAOF on 2006-08-01
The wiki is your friend:  Check out the [FakeRaid Howto]("https://help.ubuntu.com/community/FakeRaidHowto").  It's exactly what you want.

---

