---
title: "Can't get edgy64 cd to boot"
date: 2006-10-24
forum: x86 64-bit Users (Pre April '08)
---

### Post by shame on 2006-10-24
I got a new 64 bit comp and I've installed 32bit versions of suse and kanotix ok but now I'm want to have a go with ubuntu 64bit.
I'm using the last edgy cd but it fails to boot with an error regarding usplash.
If I delete the splash entry in the grub menu it goes a bit further but stops  
and the last line it displays is the hard drive information but it does display the info without an error so I don't know if it's a drive problem or a problem with whatever was going to be displayed next.
I know edgy is due to be released in a few days but I don't want to download it to find it just doesn't like my hardware so I want to try to get this one working first.

Some info that might help:
AMD Athlon 64 x2
nVidia GeForce 7600 GS graphics
Hard drives:
Channel 1 Master: ATA Hard Drive
Channel 2 Master: DVDRW
Channel 2 Slave:  CDRW
Channel 3 Master: SATA Hard Drive

I've tried various combinations of disconnecting drives/switching jumpers etc but there's no improvement.
The SATA drive came with the new comp and the ATA one is from my old one, which I'm using for backups.
The above configuration is based on the SATA drive in it's original postition and the ATA one added, neither have jumpers on them.

I've also tried changing the boot order of the drives in bios.

<EDIT>
Just to add, I know very little about 64 bit or dual core

---

### Post by John.Michael.Kane on 2006-10-24
Are you booting with the live-cd or Alternate Text based Cd

Also have you tried booting with just your DVD and Sata?


There was a case of users who had a hard time installing with an IDE HDD mixed with a Sata HDD [http://ubuntuforums.org/showthread.php?t=216039&highlight=boot](http://ubuntuforums.org/showthread.php?t=216039&highlight=boot)

---

### Post by shame on 2006-10-24
I'm using the livecd.
Using only the sata and dvd drives still didn't work but I tried adding some cheat codes I noted in the thread you linked and it now boots after adding acpi=off to the grub line.

---

