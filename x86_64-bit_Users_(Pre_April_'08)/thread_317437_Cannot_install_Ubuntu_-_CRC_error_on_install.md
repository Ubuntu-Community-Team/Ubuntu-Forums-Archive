---
title: "Cannot install Ubuntu - CRC error on install?"
date: 2006-12-12
forum: x86 64-bit Users (Pre April '08)
---

### Post by Gelupah on 2006-12-12
Hi,

I've been using Ubuntu for a while now, and have had a few problems related to my config:

A64, Asus K8V SE Mobo, Ati 9800 pro card

Most of the problems, to do with the mobo and graphics card, have been "delt with", until recently. When I tried upgrading to edgy, from an alternate CD, it failed miserably, so I formatted and thought I'd reinstall. However, the following occurs:

- (fact) I cannot boot up a liveCD as I have an ATI graphics card and get black screen upon boot otherwise --> using altrnate install
- The ubuntu alternate install will show up with a menu, install in text mode, oem, etc... However selecting an option will decompress vmlinuz (or something like that), another file, and will then halt, with some sort of CRC error and a few words (soon to be posted).
- I have tried burning 3 copies of the CD, based on ISOs from different computers - the CDs (and my drive) are fine
- I have deleted all my partitions on my HD, and have started from scratch 3 times (I'm desperate, and the HD is also fine)
- M$ win XP installs and runs fine (never thought I would say that about it!)
- Different versions of Ubuntu come up with the same problem (5.10 and 6.06 is it?), with the crashing at the very beginning of the install procedure.
- HOWEVER: Kubuntu install runs fine. But once Kubuntu installed, it freezes ALL the time. It is totally unreliable, it cannot be used at all.
- I have tried reseting / changing bios options. Nothing is overclocked.

Now... I;m pretty keen on getting ubuntu edgy eft back on my PC! Unfortunately, I cannot give the exact CRC error code at the mo, as I have no internet connection at home these days, but will copy/paste it asap. In the meantime I would really appreciate any help or advice you might have on the matter!

Thanks for you patience reading this!

Tony

---

### Post by Kilz on 2006-12-12
> **Gelupah said:**
> Hi,

I've been using Ubuntu for a while now, and have had a few problems related to my config:

A64, Asus K8V SE Mobo, Ati 9800 pro card

Most of the problems, to do with the mobo and graphics card, have been "delt with", until recently. When I tried upgrading to edgy, from an alternate CD, it failed miserably, so I formatted and thought I'd reinstall. However, the following occurs:

- (fact) I cannot boot up a liveCD as I have an ATI graphics card and get black screen upon boot otherwise --> using altrnate install
- The ubuntu alternate install will show up with a menu, install in text mode, oem, etc... However selecting an option will decompress vmlinuz (or something like that), another file, and will then halt, with some sort of CRC error and a few words (soon to be posted).
- I have tried burning 3 copies of the CD, based on ISOs from different computers - the CDs (and my drive) are fine
- I have deleted all my partitions on my HD, and have started from scratch 3 times (I'm desperate, and the HD is also fine)
- M$ win XP installs and runs fine (never thought I would say that about it!)
- Different versions of Ubuntu come up with the same problem (5.10 and 6.06 is it?), with the crashing at the very beginning of the install procedure.
- HOWEVER: Kubuntu install runs fine. But once Kubuntu installed, it freezes ALL the time. It is totally unreliable, it cannot be used at all.
- I have tried reseting / changing bios options. Nothing is overclocked.

Now... I;m pretty keen on getting ubuntu edgy eft back on my PC! Unfortunately, I cannot give the exact CRC error code at the mo, as I have no internet connection at home these days, but will copy/paste it asap. In the meantime I would really appreciate any help or advice you might have on the matter!

Thanks for you patience reading this!

Tony

Just one question, did you check the md5sum of the images before you burned them. The md5sum will tell you if you have a good iso file to begin with. If the file is corrupt , it will produce bad install cd's.
Second, you learned a lesson I learned long ago. Dont upgrade an existing install. Leave it alone and install fresh. That way if there are problems, you can boot into the working install. XP may install fine, but we all know its downhill from there.

---

### Post by Gelupah on 2006-12-12
Hi

Out of curiosity - how do I check the md5sum and compare it?

I don't think that's the problem though, as I tried installing ubuntu 5.10 and 6.06 again, and I encounter the same errors :|

What's wrong with my hardware!? And why will Kubuntu install, but not run? It doesn't seem to make sense to me...

Thanks for the advice though!

---

### Post by Kilz on 2006-12-12
> **Gelupah said:**
> Hi

Out of curiosity - how do I check the md5sum and compare it?

I don't think that's the problem though, as I tried installing ubuntu 5.10 and 6.06 again, and I encounter the same errors :|

What's wrong with my hardware!? And why will Kubuntu install, but not run? It doesn't seem to make sense to me...

Thanks for the advice though!

[Here is the wikipedia md5sum page]("http://en.wikipedia.org/wiki/Md5sum"). It has examples on how to do it. It may not be the problem, but its worth making sure it isnt the problem because it is an easy thing to check.

---

### Post by Gelupah on 2006-12-13
OK thanks - the cd is fine.

But I still get the following error message:

> 
vmlinuz........................... 
initrd...............................
Decompressing Linux... done
Booting the Kernel
[45.72.1632] crc error
[45.72.2284] kernel panic - not syncing: VFS: unable to mount root folder on unkown-block (1,0)
[45.722334] _


Any ideas what this might mean? Thanks!

---

### Post by Gelupah on 2006-12-15
- Bump - 

Any ideas anyone please? Would love to get ubuntu back!

---

### Post by factor on 2006-12-18
do a memory test, the third option of the boot cd. I had the same problem friday, in my case it was a bad ram module, i removed it and it all works ok now.

Regards.

---

### Post by Gelupah on 2006-12-24
Thanks for the idea - I tested the RAM modules, they are fine. I really have no clue to what may be causing this. Surely it can't be related to the fact my drive is SATA? Or could it?

---

### Post by factor on 2006-12-26
well, both of my drives are SATA and the problems was the ram, not the drive, but maybe it's a drivers thing, who knows. i don't know more than you, if you find the answer post it, it helps the community.

---

