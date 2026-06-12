---
title: "Live CD boot stuck on initramfs/busybox"
date: 2008-08-01
forum: x86 64-bit Users
---

### Post by John_5 on 2008-08-01
The ubuntu 8.04.1 x86_64 live cd fails to boot and gets stuck on busybox with the prompt: '(initramfs)' with some limited commands.

Help please!!

---

### Post by John Jason Jordan on 2008-08-01
> **John_5 said:**
> The ubuntu 8.04.1 x86_64 live cd fails to boot and gets stuck on busybox with the prompt: '(initramfs)' with some limited commands.
Can you say what make and model of computer you have, including details about what hardware and options are in it?

---

### Post by John_5 on 2008-08-01
> **John Jason Jordan said:**
> Can you say what make and model of computer you have, including details about what hardware and options are in it?

Yes, it's a HP Compaq Presario CQ50-100 notebook.
-AMD Turion 2ghz dual core 64 bit
-2gb of RAM
-NVIDIA GeForce 8200M G

---

### Post by John Jason Jordan on 2008-08-02
> **John_5 said:**
> Yes, it's a HP Compaq Presario CQ50-100 notebook.
-AMD Turion 2ghz dual core 64 bit
-2gb of RAM
-NVIDIA GeForce 8200M G
Thanks for the additional information.

If HP's site is correct, that computer has an HD-DVD drive. Is that correct? 

HD-DVD drives are designed to allow up to about three times the data of a standard 4 GB DVD drive. They are in competition with blu-ray.

Assuming I have the type of drive correct, I have a couple of suspicions. One is that there is something about that drive (which is unusual) that is causing problems with reading the live CD or DVD that you are trying to boot from. Did you download the Ubuntu ISO and burn it to a CD or DVD using this computer? If not, that is the first thing I would try. Maybe this drive doesn't like reading disks created on another computer.

Another suspicion is that there is something bad about the live CD or DVD. Re-burning it is a cheap and quick thing to do. It is even possible that the ISO you downloaded is corrupt. Check the MD5 sums to make sure it is intact. 

Another thing to try is to choose a different boot option from the startup screen. There are numerous command-line options that you can add (although I suspect they should not be necessary), and you can also try to load some of the other options on the menu. Loading while watching the command line is a good way to see any error messages. I suggest this because at the moment we are scrambling to find some clue as to what might be wrong.

Another thing to try is other distros that have live CDs. Fedora has a reputation of being pretty plug and play, as does OpenSuse, both of which are available in 64-bit versions. Not that I want to lose you to Ubuntu, but if live CDs from other distros work OK, that gets us one step closer to figuring out what is wrong. If they don't either, then we might be more inclined to suspect a hardware incompatibility (the drive).

I hope some of that helps or at least gets you closer to figuring out the problem.

---

### Post by John_5 on 2008-08-02
> **John Jason Jordan said:**
> Thanks for the additional information.

If HP's site is correct, that computer has an HD-DVD drive. Is that correct? 

HD-DVD drives are designed to allow up to about three times the data of a standard 4 GB DVD drive. They are in competition with blu-ray.

Assuming I have the type of drive correct, I have a couple of suspicions. One is that there is something about that drive (which is unusual) that is causing problems with reading the live CD or DVD that you are trying to boot from. Did you download the Ubuntu ISO and burn it to a CD or DVD using this computer? If not, that is the first thing I would try. Maybe this drive doesn't like reading disks created on another computer.

Another suspicion is that there is something bad about the live CD or DVD. Re-burning it is a cheap and quick thing to do. It is even possible that the ISO you downloaded is corrupt. Check the MD5 sums to make sure it is intact. 

Another thing to try is to choose a different boot option from the startup screen. There are numerous command-line options that you can add (although I suspect they should not be necessary), and you can also try to load some of the other options on the menu. Loading while watching the command line is a good way to see any error messages. I suggest this because at the moment we are scrambling to find some clue as to what might be wrong.

Another thing to try is other distros that have live CDs. Fedora has a reputation of being pretty plug and play, as does OpenSuse, both of which are available in 64-bit versions. Not that I want to lose you to Ubuntu, but if live CDs from other distros work OK, that gets us one step closer to figuring out what is wrong. If they don't either, then we might be more inclined to suspect a hardware incompatibility (the drive).

I hope some of that helps or at least gets you closer to figuring out the problem.

Thankyou for all this help -- I've tried several different distros since the last couple of hours and Fedora has managed to slightly work.

---

### Post by John_5 on 2008-08-03
> **John_5 said:**
> Thankyou for all this help -- I've tried several different distros since the last couple of hours and Fedora has managed to slightly work.

Problem solved, thanks!

---

### Post by EzEatNCSU on 2008-08-18
I've got a similar laptop (I think) - a Compaq Presario CQ50-115NR.  3GB RAM, 200GB HDD, nVidia card, AMD Turion X2 64 RM-70, with a DVD+-RW drive.  I can get the 32-bit version of Ubuntu 8.04 up with little problem as far as booting up the liveCD is concerned, but the 64-bit version boots up to the start screen with nothing else happening.  I would like to run the 64-bit version ('cause I plan on getting an extra GB of RAM, and that would enable me to access it), so if somebody can be of assistance, it would be greatly appreciated.  Thanks much! :)

---

### Post by lekidos on 2008-08-18
I am havign a similar problem, posted in another thread, but may as well try here.

My specs are as follows:

Intel Core 2 Duo 4500 processor
PNY GeForce 8600 GT video device
Biostar T-P35D2-A7 motherboard
and a 400GB SATA Hard Drive from Western Digital

With the 32-bit, I can get into Live Session, but when I go to install, it doesn't detect my hard drive, which I have into 6 partitions, the 6th, 76Gb, hoping to reserver for Ubuntu  (all of which are currently NTFS)


I've tried playing with BIOS to get SATA to register in the 32-bit gui install, and to no avail.   (I remember having a similar issue with installing WinXP for the first time, ended up needing a Floppy Disk Drive with SATA controller driver)

---

### Post by natrik on 2009-02-23
> **John_5 said:**
> Problem solved, thanks!

DUDE!  What was the solution?   Please share.

---

### Post by akashexe on 2009-02-24
Hey guys how did u guys workaround this

I have 2 cd roms on my comp. When i disconnect the IDE cable to dvd rom it works fine.

However after installing wen i reconnect it does not work and throws up the busybox command prompt

---

### Post by John_5 on 2009-06-06
The trick is to burn the CD on the same computer you're going to use it on :D

---

