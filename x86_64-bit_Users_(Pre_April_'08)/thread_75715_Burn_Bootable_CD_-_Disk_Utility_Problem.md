---
title: "Burn Bootable CD - Disk Utility Problem?"
date: 2005-10-14
forum: x86 64-bit Users (Pre April '08)
---

### Post by ctaggart on 2005-10-14
I have a PowerBook G4 with a DVD/CD RW superdrive.  I downloaded the Ubuntu 5.10 Live CD today via bittorrent and burnt the CD using OSX's Disk Utility.  The CD burned fined and passed verification, but did not boot.  Anything I need to do special or are there know issues with Apple's Disk Utility with making bootable CDs, as this article seems to point out: [http://www3.telus.net/public/lusseau/burnBootableCD.html](http://www3.telus.net/public/lusseau/burnBootableCD.html) ?

I've got Ubuntu 5.10 running on a desktop.  I guess I'll try out the burning software provided and see if I have better luck with creating a bootable CD for my PowerBook.  I hoping to be able to demonstrate Ubuntu from my laptop.

Cameron

---

### Post by Rxke on 2005-10-14
It seems to be a common, but quite unpredictable problem. Some people claim succes, others never get it working... I used Firestarter FX to burn a bootdisk under OSX, can't use the Disk Utility anyway, since it's an external SCSI writer (ancient machine)

---

### Post by ssam on 2005-10-14
you have to hold down 'c' while booting to boot from a cd.

---

### Post by div3rg3nt on 2005-10-15
Had a similar issue on my MDD G4. I found a process to make it work though:

1 - Boot into Open Firmware (hold Option-Command-letter O-Letter F)
2 - Not sure if this was necessary, but type 'dev cd' and it should come back with 'ok'
3 - Type 'shut-down' and the system will power down
4 - Hold down the 'C' key and turn your system on

FWIW I am running Open Firmware 3.

Let me know if it helps.

---

### Post by peebee on 2005-10-18
I have a lombard and just installed breezy

The first boot disks created didnt boot at all either. :confused: 
They were burnt under 5.0.4

I found that i had i had to reduce the speed at which i burnt the CD
down to 12x before it would boot and install. 

The default was maximum.

Cheers

---

### Post by ctaggart on 2005-10-18
[QUOTE=ssam]you have to hold down 'c' while booting to boot from a cd.[/QUOTE]

That was all it took to boot my Powerbook G4 from the CD for me.  Thanks!

---

