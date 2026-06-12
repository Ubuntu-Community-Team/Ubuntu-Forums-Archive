---
title: "raid ide and ahci"
date: 2008-11-28
forum: x86 64-bit Users
---

### Post by zukez on 2008-11-28
system spec
ASUS P5Q
INTEL CORE 2 DUO E8400 3.00 GHZ LGA775 - 1333 FSB - BOX
1x SEAGATE BARRACUDA 7200.11 ST3320613AS 320GB SATA2

got this mainboard because of the 8sata ports
for my future raid file server.

after getting some issues during ubuntu 8.10 live cd and alternate cd, (the creation of swap space in partition#5 of SCSI8 (0,0,0) (sda) failed), disk wasnt showing up on gparted either, then i found this threat :
[http://ubuntuforums.org/showthread.php?t=943848](http://ubuntuforums.org/showthread.php?t=943848)
witch solves the issue by setting the storage sata in the bios to AHCI instead of RAID or IDE.

since this will be a 3 x Raid1 system (6 sata disks) am i not forced to use "RAID" storage cofiguration in the bios?
should i avoid ubuntu and go for freeNAS instead?

ps: new to linux

---

### Post by psusi on 2008-11-29
You should read [https://wiki.ubuntu.com/FakeRaidHowto](https://wiki.ubuntu.com/FakeRaidHowto).  The bios raid option is done with software and can be tricky to get working right in linux.  If you don't need it to be able to dual boot with windows, it is best to ignore the feature ( leave it set to AHCI or just don't go into the bios raid utility and create a raid ) and use the conventional linux software raid.

---

### Post by zukez on 2008-12-01
Thank you for your answer, i quess that onboard stuff was a bad choise, better go with 3ware cards next time.
I will have to consider my options now, cheers.

---

### Post by vhozard on 2008-12-01
Indeed it was not the best choice, BUT I have an Asus P5Q-Pro and after a lot of hassling I got ubuntu 8.10 (64 bit) to install with the BIOS RAID.
Windows Vista is also installed on the same BIOS RAID and I can even read/write the Vista partitions from ubuntu. The procedure to install ubuntu is a little tricky, but I can tell you how to do it. I don't have much time right now, but if you want to know howto do it email me: [email]vhozard@gmail.com[/email]

Greets Vhozard,

---

### Post by zukez on 2008-12-01
cheers vhozard, well i thing that wont be nessesary
i installed ubuntu with bios set to ahci, 
if i really need a raid i might go for software raid, although
hardware is better. Or i might wait for them to fix this in the upcoming ubuntu releases.

do you know any good backup software, for scheduled backups?

---

### Post by vhozard on 2008-12-02
Ah, I understand. That's fine :)
Backup software? Well, you can try [[COLOR="Blue"]_SBackup_[/COLOR]]("https://help.ubuntu.com/community/BackupYourSystem/SimpleBackupSuite"). It's a commonly used backup-system.

Greets Vhozard,

---

### Post by zukez on 2008-12-03
good stuff, im happy with this os ;) 
cheers

---

