---
title: "[SOLVED] Long boot due to fsck"
date: 2008-02-19
forum: x86 64-bit Users (Pre April '08)
---

### Post by randiroo76073 on 2008-02-19
Hi all, not quite sure where this goes, Admins feel free to move.
Every time I boot I get this msg/bootscreen, had some other problems but managed to work thru them :) This one I haven't the foggyest of what to do & it makes for a long boot/reboot. How do I settle the differences between boot sector & backup ?  Am running Gutsy 7.10 amd64 fully updated as of 02-18-08, any help is appreciated,[9 month old newbie] Have other issues but will post separately, 1 step at a time! :)


Log of fsck -C -R -A -a 
Mon Feb 18 15:24:06 2008

fsck 1.40.2 (12-Jul-2007)
dosfsck 2.11, 12 Mar 2005, FAT32, LFN

..................................................................................
There are differences between boot sector and its backup.
Differences: (offset:original/backup)
  430:4e/52, 431:54/65, 432:4c/6d, 433:44/6f, 434:52/76, 435:20/65, 436:69/20
  , 437:73/64, 438:20/69, 439:6d/73, 440:69/6b, 442:73/20, 443:69/6f
  , 444:6e/72, 445:67/20, 446:ff/6f, 447:0d/74, 448:0a/68, 449:44/65
  , 450:69/72, 451:73/20, 452:6b/6d, 453:20/65, 454:65/64, 455:72/69
  , 456:72/61, 457:6f/2e, 458:72/ff, 459:ff/0d, 460:0d/0a, 461:0a/44
  , 462:50/69, 463:72/73, 464:65/6b, 465:73/20, 466:73/65, 467:20/72
  , 468:61/72, 469:6e/6f, 470:79/72, 471:20/ff, 472:6b/0d, 473:65/0a
  , 474:79/50, 475:20/72, 476:74/65, 477:6f/73, 478:20/73, 479:72/20
  , 480:65/61, 481:73/6e, 482:74/79, 483:61/20, 484:72/6b, 485:74/65
  , 486:0d/79, 487:0a/20, 488:00/74, 489:00/6f, 490:00/20, 491:00/72
  , 492:00/65, 493:00/73, 494:00/74, 495:00/61, 496:00/72, 497:00/74
  , 498:00/0d, 499:00/0a, 506:bf/cb, 507:cc/d8
  Not automatically fixing this.
...................................................................................

/dev/hdb1: 17240 files, 1311777/2092383 clusters
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
/dev/hdb2: 29387 files, 1445768/2092391 clusters
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
/dev/hda15: 132983 files, 2043348/5704302 clusters
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
/dev/hdb3: 165604 files, 2139741/4603887 clusters
Gutsy_h: clean, 33220/2626560 files, 2959995/5242880 blocks
Parsix_r: clean, 137286/1966080 files, 724827/3931900 blocks
Parsix_h: clean, 159133/2626560 files, 1896316/5242880 blocks (check in 5 mounts)
/dev/hda7: clean, 104243/1966080 files, 575251/3931900 blocks
/dev/hda8: clean, 35/2626560 files, 126629/5242880 blocks
/dev/hda9: clean, 11/1966080 files, 104098/3931900 blocks
/dev/hda10: clean, 11/2626560 files, 126483/5242880 blocks
/dev/hda11: clean, 11/1966080 files, 104098/3931900 blocks
/dev/hda12: clean, 11/2626560 files, 126483/5242880 blocks
/dev/hda13: clean, 11/1966080 files, 104098/3931900 blocks
/dev/hda14: clean, 159150/2626560 files, 1896465/5242880 blocks

Mon Feb 18 15:25:27 2008
----------------

---

### Post by CRCarl on 2008-02-20
First a fix - 

(assuming your windows fat32 partition is on /dev/hdb1)

sudo dosfsck -ar /dev/hdb1

Choose to make the original the backup (option 1 I think), and then choose "Y".

Second - Why do you have so many fat32 partitions being mounted?

C

---

### Post by Kilz on 2008-02-20
While I cant help with the errors, you might want to check out [AutoFsck]("https://wiki.ubuntu.com/AutoFsck"). It will let you change the check from startup to shutdown. That way checks happen as you are walking away from the computer instead of when you are in a hurry to use it.

---

### Post by randiroo76073 on 2008-02-20
Thanks for replies guys will chk both out :)
@ CRCarl, I still have 98se & XP onboard due to help forums. Currently have Gutsy-64, Hardy-32, Parsix-32, GoblinX-32, all with root & home. Have always been multi-partitioned for backup reasons[hard Win lesson]

@ Kilz, now that definitely makes more sense to me, I would[most of time] rather be walking away :)

---

### Post by Kilz on 2008-02-20
Forgot to add, when you install it it will add Periodic Disk Checking to the System > Administration menu. It isnt called AutoFsck there.

---

### Post by randiroo76073 on 2008-02-20
Success as to the boot msg :) Thanks CRCarl!
@ Kilz, not so happy a ending on chnging when fsck kicks in, have installed/reinstalled 3 times and no worky on my machine, I set it to do chk on shutdown and it still does it on startup.  No msgs that tell me why, no msgs on install, no msgs on use, just doesn't work :(  Guess I'll chk with author ???

---

