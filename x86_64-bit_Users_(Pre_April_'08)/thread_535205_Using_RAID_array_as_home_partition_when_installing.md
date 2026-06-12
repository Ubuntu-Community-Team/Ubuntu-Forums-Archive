---
title: "Using RAID array as /home partition when installing AMD64 Ubuntu?"
date: 2007-08-26
forum: x86 64-bit Users (Pre April '08)
---

### Post by Ketsuban on 2007-08-26
I am looking to install Ubuntu but am running into some trouble with my RAID array.

The motherboard is an Abit KN9-SLI, which has the RAID controller on the motherboard itself. I currently have the hard drives set up as follows.

Windows identifies drive C (sda1) as an 80GB hard drive, and drive D as a 1.36TB drive; this is actually two 750GB drives (identified by Linux as sdb1 and sdb2) in a RAID0 array.

I'd like to use the 80GB drive partitioned up for swap and / and the RAID array for /home, but Linux refuses to recognise the RAID array, insisting instead that sdb1 and sdb2 are separate drives. I don't want to use software RAID because my motherboard has a perfectly good RAID controller already. What should I do?

---

### Post by livestockPimp on 2007-08-26
your choices I believe are only software RAID, without knowing the exact model of mobo you have.
All mother boards that come out with "built-in RAID" are only semi hardware and need windows controllers to run (they are still software based). If you have a very expensive XEON you may actually have onboard hardware RAID but I am doubting this is the case.

---

### Post by livestockPimp on 2007-08-26
ah, sorry I missed that model of the mobo,
anyway [http://www.dizwell.com/prod/node/883](http://www.dizwell.com/prod/node/883) is an article about RAID on motherboards. this may/may not help.

---

