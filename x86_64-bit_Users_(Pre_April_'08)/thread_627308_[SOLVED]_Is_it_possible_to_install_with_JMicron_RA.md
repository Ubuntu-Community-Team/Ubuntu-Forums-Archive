---
title: "[SOLVED] Is it possible to install with JMicron RAID?"
date: 2007-11-29
forum: x86 64-bit Users (Pre April '08)
---

### Post by mozkill on 2007-11-29
I just failed in installing 7.10-x64 Gutsy on my Asus P5K-E motherboard.  I have one optical CDROM attached to my JMicron SATA controller as well as 2 Seagate 1TB drives (presumably in a RAID mirror which is what the bios tells me).

After installation on device /dev/hdb (/dev/hdc is the mirrored drive and Ubuntu does not give me the option of install on that one) Ubuntu installs the boot loader on hd0 (which is assume is part of /dev/hdb?) and then asks for a reboot.

After the system tries to restart it tells me that no boot loader is found.  Basically, I am not exactly sure what happened here.  It appears that the RAID worked and that Ubuntu install detected /dev/hdb as the primary drive in the raid mirror.

Can anyone offer any ideas for me here?  Is there a guide anywhere that covers install on ASUS motherboards?

---

### Post by Jouke74 on 2007-11-30
HD0 can also be HDA, what is the total harddisk set-up, and from which drive did you start up before?

---

### Post by nxt on 2007-11-30
I had the same problem - my problem concerned the PATA connector. When a disk was connected into to PATA it kept shifting its ID every boot - therefor all my SATA disk had a diffrent number every boot. This prevented the system to reach the grub in it's correct place. So I left the PATA connector empty during install and everything worked fine.

(In defense of Ubuntu I must say, I had the same problem when I installed my XP partition. This is supposed to be a problem caused by certain types of motherboards...)

---

### Post by mozkill on 2007-11-30
> I had the same problem - my problem concerned the PATA connector. When a disk was connected into to PATA it kept shifting its ID every boot - therefor all my SATA disk had a diffrent number every boot. This prevented the system to reach the grub in it's correct place. So I left the PATA connector empty during install and everything worked fine.

I have these drives connected:
1. DVD-ROM - SATA1
2. Seagate 1TB - SATA4
3. Seagate 1TB - SATA5
4. WD 100GB - ATA1

Thanks for the suggestion!  I did notice that was also happening to me since I tried to install 3 times.  The drives were mapped to different devices each time I rebooted the system.   I'll temporarily disconnect the ATA 100 and try the install again.  I will post tomorrow and let you know what happened.

---

### Post by mozkill on 2007-12-01
I couldnt get the RAID working on the ASUS P5K-E motherboard.   When the SATA drives are in RAID mode, the OS is not bootable.   I had to put the drives in IDE mode until I can get a 3Ware hardware raid card.

---

### Post by saru411 on 2007-12-01
linux software raid works well. you should try it......your jmicron raid is FAKEraid. FAKEraid used system resources to function. as for the raid card i would recommend playing attention and getting the correct one.....alot of those card you are looking at are meant for server mobos and will not fit on your asus pc board. hardware raid is fast but the linux software raid will be more than fast enough for you i would imagine. plus if the hardward card breaks and its discontinued you will not easily be able to rebuild your raid array. if you use linux software raid you will be able to take your hdds to whatever system you want. for instance if you mobo dieds and asus stops offerning the pk5 you can get a differnt board, plug it in and be ready to go. just always makes sure to make a seperate for your /home folder and your library should be super safe!

cheers

---

### Post by mozkill on 2007-12-13
UPDATE ON WHAT HAPPENED:

The 3Ware 9650 card worked ONLY if I booted Linux from the RAID.   With the ASUS P5k-E  I was unable to boot from the 100GB PATA/IDE drive that I had .  The Bios was unable to recognize that the IDE drive was bootable while the 1TB 3Ware raid mirror was enabled.

Now I run XP on the computer with the 3Ware raid and ASUS P5K-e  and I boot from the IDE.  Windows XP evidently has no problem here (where ubuntu obviously did).

Instead, I run Ubuntu 7.10 on my other computer, which is described in my "signature".

---

### Post by crjackson on 2007-12-14
> **mozkill said:**
> UPDATE ON WHAT HAPPENED:

The 3Ware 9650 card worked ONLY if I booted Linux from the RAID.   With the ASUS P5k-E  I was unable to boot from the 100GB PATA/IDE drive that I had .  The Bios was unable to recognize that the IDE drive was bootable while the 1TB 3Ware raid mirror was enabled.

Now I run XP on the computer with the 3Ware raid and ASUS P5K-e  and I boot from the IDE.  Windows XP evidently has no problem here (where ubuntu obviously did).

Instead, I run Ubuntu 7.10 on my other computer, which is described in my "signature".

I hope you filed a bug report on launchpad so that this can be fixed in future releases?

---

### Post by mozkill on 2007-12-14
ok, i reported it:  [https://bugs.launchpad.net/ubuntu/+source/grub/+bug/176448](https://bugs.launchpad.net/ubuntu/+source/grub/+bug/176448)

---

