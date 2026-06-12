---
title: "Installation problems."
date: 2006-04-23
forum: x86 64-bit Users (Pre April '08)
---

### Post by xmastree on 2006-04-23
I'm trying to install breezy on an iMac. Long story is in [this thread]("http://ubuntuforums.org/showthread.php?t=152612"), but to summarise, I've swapped out the hard disk and conencted the Mac to my monitor since this one has the flyback problem.

I can't load the live CD, it gets as far as setting up the desktop, window manager, but no further. It takes about fifteen minutes to reach this point, I think it's low on memory.

That's when i decided to install instead. During installation, all goes well until it's 'starting the partitioner'. It seems to reach 100%, then the screen blinks, and the partitioner restarts but stops at 52%.

The CD checks out in this PC where I made it, but just to be sure I made another on a different brand of disc. That's exactly the same.

Any ideas?

---

### Post by ssam on 2006-04-23
how much ram do you have?
are you using breezy or dapper?
could this be a hardware problem? swapping the hard disk wouldn't help if the ide is faulty. the live cd should work without a hard disk (though it would be able to use a swap partition).
does yellowdog install ok? maybe try and partition the disk with [http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page)

---

### Post by xmastree on 2006-04-23
I've got past that stage now. The IDE I fitted had a windows installation on it. I put it in a PC and deleted all partitions. That seems to have worked. It's currently installing...

I don't know how much RAM I have, and I don't know how to find out... This is my first experience with a Mac.

FWIW, it's a tray loader, 266MHz (I think, the cpu has ARX266SE). Underneath the CPU is what looks like 64MB, and there's another on the motherboard but from the markings the size isn't obvious. The original HD was a Seagate 20GB.

---

### Post by xmastree on 2006-04-23
So, i remove the CD, it reboots, and...
'**Please wait, Loading kernel**'

That's it.

---

### Post by dj_flx on 2006-04-23
Well, you've gotten farther than I did on my 233 Bondi.

[http://docs.info.apple.com/article.html?artnum=58669](http://docs.info.apple.com/article.html?artnum=58669) is the matrix for the CRT iMacs. The serial number sticker in the cable area on the side should give you the date it was made.

---

### Post by butlerwm on 2006-04-24
Three weeks worth of posts -- that's impressive.  I've done Ubuntu and Yellowdog installs on three Macs (iMac like the one you describe, an OldWorld G3, and this G4).  Partitioning has tended to be the biggest problem.  On the iMac the only thing that worked was similar to what you accomplished. The difference being that I wiped the drive in another Mac.  On both the G3 and the iMac it took multiple wipes and restarts before I was able to get Linux installed. To date, I've never been able to determine what the exact problem was. The only suggestion I have is get your hands on a Mac boot CD, get into the system, wipe the drive with the Mac utility and try another install.

---

### Post by xmastree on 2006-04-24
I looked at yellowdog, but it was taking forever to download... Is there a mini-distro available for mac? Like dsl or puppy?

---

### Post by jdp on 2006-04-24
I've tried booting on trayload iMacs with low RAM before, and it wasn't fun.  it was very slow to get them to even finish booting.  I know they had 64MB, and some may have had 96MB.  I've done 128MB on a few other systems, and it was slow but functioned.  I'd say check the RAM to be sure.  I've done 128MB and 256MB on slotloading iMacs and Ubuntu ran pretty well with more and more RAM.

---

