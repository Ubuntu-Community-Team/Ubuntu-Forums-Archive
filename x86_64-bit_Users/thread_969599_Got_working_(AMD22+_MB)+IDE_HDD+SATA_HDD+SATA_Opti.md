---
title: "Got working? (AMD2/2+ MB)+IDE HDD+SATA HDD+SATA Optical Drive ubuntu 8.10 Intrepid"
date: 2008-11-03
forum: x86 64-bit Users
---

### Post by amgalitz on 2008-11-03
If any one has successfully installed ubuntu 8.10 Intrepid with the follow (likely not too uncommon) configuration, would you kindly help by posting your setup? TIA muchly. 

AM2+/AM2 Motherboard (MB)
2 Or 4+GB RAM
IDE HDD as master (slave position either empty or with another HDD)
SATA HDD on SATA1 (if additional SATA drives, please post also)
SATA Optical drive on next SATA port (CDROM, DVD whatever)

If you got one working, but with an IDE optical drive and only HDD on the SATA ports, listing your setup would help too. If you don't know the more technical details, just the MB and Drive layout would help.

Information:
* Which processor?
* Which Motherboard?
* How much memory?
* How did you do it? 
-  what if any bios changes from default (likely SATA configuration)?
-  What added kernel options were needed, if any (from /boot/grub/menu.lst)?
-  Did you have to move drives around? SATA optical on SATA1, HDD on upper SATA ports

Also helpful (Thanks again!!)
* listing of /boot/grub/system.map file
* listing of /boot/grub/menu.lst
* output of "lspci" command at command prompt
* What happens to your drive assignments (sda, sdb etc) when you plug in a USB stick? (type at command prompt: "sudo df -h" or "sudo blkid". These are safe! 

If you are short of time, just that a given AMD2/AMD2+ motherboard did somehow boot Intrepid would help. Many people are having the first post-install boot fail at the (initramfs) stage. So little OS function is available that it is hard to trouble shoot then. 

I've started a thread on this here,
[http://ubuntuforums.org/showthread.php?t=968424](http://ubuntuforums.org/showthread.php?t=968424)
with all the troubleshooting steps done with an ASUS M3A78+4GB RAM(dual channel)+AMD64 4850e+IDE HDD+SATA HDD+SATA optical.

Here is another thread about similar issue with INTEL chipset!
[http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=968968](http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=968968)

It strikes me as useful to have a listing of successful installation configurations. I searched for such a thread to no avail using:
amd2+working, amd2+success, amd2+boot, amd2+initramfs
but if I missed one, please point out. Sure wish I found one when before I bought current MB!


Thanks so much!!

cheers

---

### Post by amgalitz on 2008-11-04
Nobody has made an AM2+/AM2 socket motherboard with IDE/PATA and SATA HDDs work with Intrepid yet or are you all glued to the election in the USA? I'm going to have to send my MB back soon and would really appreciate some advice. Googling hasn't worked.
I'm not feeling the love here<G>.

Cheers

---

### Post by cariboo on 2008-11-04
This is a pretty common configuration, I have everything but the sata optical drive, and everything just works.

System specs:

K9NGM2 motherboard
250Gb  Seagate IDE
169Gb  WD SATA
HL-DT-ST LG DVD/RW
2Gb  Ram

I also have two eSATA Seagate 169Gb hard drives attached, but not always turned on.
THe BIOS is set to performance defualt only change is boot order

Jim

---

### Post by amgalitz on 2008-11-08
My current working configuration

AM2+/AM2 Motherboard (MB)ASUS M3A78
2 Or 4+GB RAM
IDE Master = HDD 
IDE Slave = Either HDD or Optical drive
SATA HDD on SATA1
SATA Optical drive on next SATA port (CDROM, DVD whatever)

System boot fails to Busybox initramfs if the IDE slave is empty and Sata optical in place. Livecd session works however.
Sata in Bios is set to ACHI

---

### Post by sloggerkhan on 2008-11-08
See my sig. I have a similar computer:
M2NSE+ 2xAMD 2 SATA HD, 1 IDE HD 1 IDE DVD or something similar.
Not using intrepid, though.

---

### Post by randiroo76073 on 2008-11-08
I seem to be lucky in that respect, no major problems.
ASUS M2A-VM mATX, Athlon 64x2 5600, 4gb DDR2 800 dual channel, ATI Radeon X-1250[onboard] 
2 ide hdd's (80gb, 160gb)(ide 1&2)
2 sata optical (dvd rw, cd rw/dvdrom)(sata 1&2)
1 sata hdd (250gb)(sata 3)
various usb sticks (16mb to 8gb, 8gb has 8.10 32bit installed)
2 usb external hdds (100gb, 160gb, backups, always on but not mounted)
My usb's are plugged into a 7 port powered hub(hate to get to back plugs)

Except for boot order BIOS is stock.

---

