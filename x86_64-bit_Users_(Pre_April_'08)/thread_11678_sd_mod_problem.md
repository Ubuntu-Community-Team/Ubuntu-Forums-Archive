---
title: "sd_mod problem"
date: 2005-01-18
forum: x86 64-bit Users (Pre April '08)
---

### Post by coldcargo on 2005-01-18
Hi!

When a'm finally made up my mind on wich linux distribution to use, it dosen't work to install.

I have an HP Pavilion with AMD64 3400+ processor and dvd-reader and a dvdrecorder (dual layer).

In the initial installation phase when it's detecting my hardware I get this message:

Detecting hardware to find CD-ROM drivers
                                  91%
Loading module 'sd_mod' for 'SCSI disk support'.....

It just hangs forever. It works fine with my Pentium4 computer.

I have no problems with booting on cd-rom's and I have set Plug&Play OS value to no in BIOS. I have tried to unchecked some kernel modules (I guess) in the section Mount CD-ROM using the expert mode to install ubuntu. I dont know if I unchecked the righ ones or not, or if it would work at all. 

I hope that some one else has exirensed somesthing like this and got it to work of cause, or if someone knowes what to do.

//Tanks.

---

### Post by poofyhairguy on 2005-01-18
[QUOTE=coldcargo]Hi!

When a'm finally made up my mind on wich linux distribution to use, it dosen't work to install.

I have an HP Pavilion with AMD64 3400+ processor and dvd-reader and a dvdrecorder (dual layer).

In the initial installation phase when it's detecting my hardware I get this message:

Detecting hardware to find CD-ROM drivers
                                  91%
Loading module 'sd_mod' for 'SCSI disk support'.....

It just hangs forever. It works fine with my Pentium4 computer.

I have no problems with booting on cd-rom's and I have set Plug&Play OS value to no in BIOS. I have tried to unchecked some kernel modules (I guess) in the section Mount CD-ROM using the expert mode to install ubuntu. I dont know if I unchecked the righ ones or not, or if it would work at all. 

I hope that some one else has exirensed somesthing like this and got it to work of cause, or if someone knowes what to do.

//Tanks.[/QUOTE]

That happened to me....I bet the solution won't make you happy. I had to change out the drive I was installing from. For me it was simple, pop out the drive for another I had sitting around... then it worked fine. Do you have two drives? If so, try installing from the other one!

Maybe someone else has a better solution.

---

### Post by coldcargo on 2005-01-18
[QUOTE=poofyhairguy]That happened to me....I bet the solution won't make you happy. I had to change out the drive I was installing from. For me it was simple, pop out the drive for another I had sitting around... then it worked fine. Do you have two drives? If so, try installing from the other one!

Maybe someone else has a better solution.[/QUOTE]

Thanks for your fast replay, but it seems to be the hard way as you suggested. But I have to study BGP to night, so it has to bee tomorrow unless some one else has an easier solution.

/coldcargo

---

### Post by coldcargo on 2005-01-21
[QUOTE=coldcargo]Thanks for your fast replay, but it seems to be the hard way as you suggested. But I have to study BGP to night, so it has to bee tomorrow unless some one else has an easier solution.

/coldcargo[/QUOTE]

I installed Hoary insted, so now it works so far :-)

Does anyone know how to make warty support SATA disks during install I would like to know howto?

/coldcargo

---

### Post by carlopiana on 2005-02-01
Hi, 

I had the same problem. I worked this out this way:
[list]
[*]went on a new console (atl+f2)
[*]inserted the scsi mode (modeprobe sd_mod)
[*]restarted the cd recognition process
[*]noted where it hanged now (a Sis module, one of the first, think is the raid controller)
[*]Supposed that this was the module which indeed caused the problem, and disabled it in the "expert" mode (select it at bootstrap)
[*]Worked!!!
[/list]  :D

---

### Post by carlopiana on 2005-02-01
Yeah. worked, but in the next phase, either I load the sata_sis module or I cannot see the HD, which is not exactly what I wanted. That's strange, because on a Suse 9.1 on the same machine the sata_sis and sd_mod work together in perfect armony... :(

Sorry for the stupid answer given before... :/

---

### Post by nzjrs on 2005-02-05
[QUOTE=carlopiana]Hi, 

I had the same problem. I worked this out this way:
[list]
[*]went on a new console (atl+f2)
[*]inserted the scsi mode (modeprobe sd_mod)
[*]restarted the cd recognition process
[*]noted where it hanged now (a Sis module, one of the first, think is the raid controller)
[*]Supposed that this was the module which indeed caused the problem, and disabled it in the "expert" mode (select it at bootstrap)
[*]Worked!!!
[/list]  :D[/QUOTE]


Hey, I am having the exact same problem, coincidentally i tried the same solution as you, and even got the same result - it dodnt work!!!

See:
[http://www.ubuntuforums.org/showthread.php?t=13127](http://www.ubuntuforums.org/showthread.php?t=13127)
[http://www.ubuntuforums.org/showthread.php?t=14110](http://www.ubuntuforums.org/showthread.php?t=14110)
[https://bugzilla.ubuntu.com/show_bug.cgi?id=1440](https://bugzilla.ubuntu.com/show_bug.cgi?id=1440)

I also have suse9.2 instaled and it works a charm. 

Dammit!!!

---

### Post by carlopiana on 2005-02-07
I also have SuSE 9.2, and worked as a charm only when I downgraded the Kernel to 2.6.4 or so (but maybe the problem was with the SIS SATA drivers, I guess they were in the non-GPL packet which I deselected). Perhaps the problem is there, or maybe with the Maxtor disc, who knows!).

That's annoying, though

Carlo

---

### Post by nikorn on 2005-02-21
Think I can illuminate on this. It appears to be something to do with partition tables. I began installing ubuntu on my own computer with my drive chock-full of NTFS partitions... I got past the loading of the sd_mod module fine, but when using the ubuntu partition tool I decided I needed to make more intricate changes, resizing etc. with a different utility, so left the installer and did so.

I then went back to ubuntu and had exactly the same problem as you. I'm guessing if I spend a few long hours moving data around in a trial and error process I would be able to get past the 92% hang again, but decided instead to try hoary instead  :wink: 

That said, warty supported my sata disk fine until I messed about with the partitions on my drive, so I'm sure there must be a way round the problem.

---

### Post by my64 on 2005-02-21
[QUOTE=coldcargo]I installed Hoary insted, so now it works so far :-)

Does anyone know how to make warty support SATA disks during install I would like to know howto?

/coldcargo[/QUOTE]

Warty works fine with SATA disk (at least for me).
However, if you want grub to boot on your SATA disk, and if your SATA disk is second and your ATA disk first, then you need to add  this in your GUB conf:

root  (hd1,0)
map (hd1) (hd0)
map (hd0) (hd1)

---

