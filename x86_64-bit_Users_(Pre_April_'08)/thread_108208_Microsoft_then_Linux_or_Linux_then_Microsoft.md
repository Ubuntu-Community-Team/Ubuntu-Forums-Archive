---
title: "Microsoft then Linux or Linux then Microsoft"
date: 2005-12-25
forum: x86 64-bit Users (Pre April '08)
---

### Post by nami on 2005-12-25
Hi

I currently have 2 computers:

Computer 1:
- HDD - 250Gb - 2 Partitions with Windows 2000 and Windows XP
- CPU - AMD XP 1900 @ 1.6GHz
- RAM - 512Mb PC2700 
- GC - Nvidia TI4200 64Mb

Computer 2:
- HDD 40Gb - 1 Partition with Linux Ubuntu 5.10
- CPU - Intel Celeron @ 0.5GHz
- RAM - 768Mb PC333
- GC - ATI Rage Pro 8Mb

As you can see computer 1 has a lot more powerful than computer 2!  Things run really slow on computer 2 even the webpages take a lot longer to download than computer 1 even though I have a 2Mb cable connection.

So I was thinking about making ANOTHER partition on computer 1 and install Ubuntu on that.  But I am a little concerned.  As I already have Windows 2000 and Windows XP on computer 1, how will they get affected if I install Ubuntu on the same HDD?

So back to my original question, is it better to first install Microsoft Windows then Linux Ubuntu or Linux Ubuntu then Microsoft Windows?

In either case, how would I go about installing Linux Ubuntu alongside Microsoft Windows?

Appreciate any advice.

nami

---

### Post by TTL on 2005-12-25
First installing Windows, later installing Linux is easier,
because Windows automatically overwrites the MBR without asking during the installation (I REALLY hate that), in opposite Linux asks to do this and can install a bootloader where you can access the Windows installations.

You sould use (at least) one partition for Linux only.
So the main difficulties are:
First you need at least one partition for Linux (without Windows on it), if you have to repartition your HD this might be risky to the existing Installation - Backup data before you start!
Second prevend Windows from overwriting the MBR since this would make the Linux installation hard to start.
But once installed and configured Linux and Windows are working from a single harddrive without problems. (At least here on my laptop ;) )

---

### Post by dombleu on 2005-12-25
May I just add you are asking that on forum dedicated to PPC architecture?
Posting that question on a more general forum should get you more answers...

dom

[QUOTE=nami]Hi

I currently have 2 computers:

Computer 1:
- HDD - 250Gb - 2 Partitions with Windows 2000 and Windows XP
- CPU - AMD XP 1900 @ 1.6GHz
- RAM - 512Mb PC2700 
- GC - Nvidia TI4200 64Mb

Computer 2:
- HDD 40Gb - 1 Partition with Linux Ubuntu 5.10
- CPU - Intel Celeron @ 0.5GHz
- RAM - 768Mb PC333
- GC - ATI Rage Pro 8Mb

As you can see computer 1 has a lot more powerful than computer 2!  Things run really slow on computer 2 even the webpages take a lot longer to download than computer 1 even though I have a 2Mb cable connection.

So I was thinking about making ANOTHER partition on computer 1 and install Ubuntu on that.  But I am a little concerned.  As I already have Windows 2000 and Windows XP on computer 1, how will they get affected if I install Ubuntu on the same HDD?

So back to my original question, is it better to first install Microsoft Windows then Linux Ubuntu or Linux Ubuntu then Microsoft Windows?

In either case, how would I go about installing Linux Ubuntu alongside Microsoft Windows?

Appreciate any advice.

nami[/QUOTE]

---

### Post by nami on 2005-12-25
TTL - Thanks for the reply!

dombleu - I'm not sure how I managed to post here!  How do I get admin to move this post?

Thanks

nami

---

