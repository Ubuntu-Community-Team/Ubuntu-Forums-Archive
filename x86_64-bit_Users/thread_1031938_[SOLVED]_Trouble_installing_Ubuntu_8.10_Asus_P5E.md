---
title: "[SOLVED] Trouble installing Ubuntu 8.10 Asus P5E"
date: 2009-01-05
forum: x86 64-bit Users
---

### Post by s13_mills on 2009-01-05
Hi all,

Having serious trouble getting 64 bit Intrepid to install on my main computer - graphical installer reports "File did not match its copy on the CD..." errors, clicking retry (sometimes several times for the same file) results in the installer completing, but often on boot it will complain of "crc" errors and will not boot. If it does manage to boot, I have continuous problems with updates etc!

The problems seem to be related to inaccurate copying of text files  that apt requires - an example was a bracket around the wrong way in a version number which caused apt to fail to upgrade a package.

I have tried changing the disk mode from AHCI to IDE in bios - no change. Any other suggestions are welcome!

Hardware is:
Asus P5E motherboard (Bios version 0502)
Core2Duo 2.66GHz 1333MHz FSB
80GB Seagate (Operating System) in sata port 1
Pioneer DVR-212 in sata port 2
750GB Seagate in sata port 3
Pioneer DVR-212 in sata port 4
1TB Seagate in sata port 5
Nvidia 8600GT 512MB 
2 x 2GB Transcend DDR2 Ram
Hauppauge Nova-s plus
Marvell mrv8000 based wireless

Also worth noting that I tried a WD 80GB drive in sata port 1 for the OS drive - no change. Anyone with any experience with this kind of problem, your help would be GREATLY appreciated!

Thanks in advance,

Mills

---

### Post by s13_mills on 2009-01-05
In running memtest86+, I noticed it had registerd my ram as operating at 400MHz, when it is DDR2 800? Could this be an issue? Memtest completed successfully, no errors

---

### Post by tboneDX on 2009-01-06
I don't know what to do about your install not working, but ddr-800 memory should be operating at 400mHz (ddr stands for double data rate, i.e. 400mHz=effective 800 mHz)

edit: umm, maybe the CD didn't burn right or something, try burning a new one/checking your current one for problems.  I believe there is an option to do that when you boot from CD.

---

### Post by s13_mills on 2009-01-06
Thank you for that, useful to know! I installed UNetBootin on another PC and made a flash drive to install - still had some errors installing (so not a CD/DVD issue, must be on the HDD side of things) but managed to get a functional desktop from which I am typing now - still very keen to eliminate these random errors though, anyone out there with some ideas I can try now I have the working system?

---

### Post by s13_mills on 2009-01-06
An interesting development last night when I powered the computer down - after the shutdown splash there was text with a lot of read/write errors in sector xxxxxx on /dev/sda (operating system drive) What are the odds I tried two faulty drives though? Should I try installing to a port other than sata port 1?

---

### Post by s13_mills on 2009-01-09
Well, I've managed to get everything working pretty much how I want it - I still have a persistent "corrupt package tarfile" error for acroread though. Not the end of the world though - now I just need help with the wireless!

---

