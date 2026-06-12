---
title: "Hfsplus Performance/Reliability"
date: 2006-05-05
forum: x86 64-bit Users (Pre April '08)
---

### Post by sciurus on 2006-05-05
What's the status of HFS+ support in Linux? Is the speed comparable to native linux filesystems? Is it dependable enough to use in a production environment? Are there any quirks (other than no journaling), or can it safely be swapped back and forth between OS X and linux?

Here's what I was able to turn up with google. 

1)Maintained by Brad Boyer
patch for kernel 2.4.x series
no updates since 2003
[http://sourceforge.net/projects/linux-hfsplus](http://sourceforge.net/projects/linux-hfsplus)

2)Maintained by  Roman Zippel
based on Brad's work
for 2.4.x and 2.6.x kernels
no update since 2004
"full read and write access and has a better perfomance. It also supports hard links and the resource fork is accessible via /rsrc."
[http://www.ardistech.com/hfsplus/](http://www.ardistech.com/hfsplus/)

3) Maintained by ?
part of 2.6.x kernel series
development is ongoing, for instance 2.6.16 added support for case-sensitive HFS+ filesystems
no support for journals yet
referred to at [http://gentoo-wiki.com/HOWTO_hfsplus](http://gentoo-wiki.com/HOWTO_hfsplus)

---

### Post by deathshadow on 2006-05-06
This is mostly anecdotal based on my own experience, and the results may be off since the Mac I do most of my testing on is a toilet seat iBook 333 with heat sinks added to the CPU and northbridge (THE HORROR!!! Heat sinks in a iBook!?!) overclocked to 433.

HFS is on the whole faster than ext2, and handles physical disk errors WAY better - BUT, I would not use it as my primary linux filesystem because there are permission 'quirks' that pop up from time to time, and it is less efficient on disk space use. 

It is NOT faster than ext3 (which ubuntu now defaults to) or ReiserFS - and if I was looking for a way to boost linux filesystem performance, I'd likely go with one of those two - especially since their codebase for linux is more mature and as such more reliable.

On a Mac though, it's nice to have the support so your linux OS can read the files on the OS X / MacOS side of things and it's great for mass storage.

---

### Post by slux on 2006-05-06
[QUOTE=deathshadow]
...HFS is on the whole faster than ext2...

...It is NOT faster than ext3...
[/QUOTE]

That doesn't sound right. ext3 pretty much just adds journalling and should be consistently slower than ext2 because keeping a journal adds some overhead.

---

### Post by deathshadow on 2006-05-06
[QUOTE=slux]That doesn't sound right. ext3 pretty much just adds journalling and should be consistently slower than ext2 because keeping a journal adds some overhead.[/QUOTE]

Except the journalling makes file OPENS faster because you can find the file and it's pieces/parts on the drive FASTER (journalling provides a better indexing system). Does make writes slower though.

It's also faster if anything goes WRONG since it has checks and balances in it that WORKS instead of ext2 with it's 'retry for five minutes of 100% IOWAIT' just from one bad sector which it will mark bad, then try to reclaim on every reboot. (You want to talk about BAD error handling)

Generally if you are opening and reading lots of small files (Mp3's, images and web cache for example), ext3 is better speed-wise... if you are working on one big file with flat access (mysql table), ext2 is better - at least, that's what it seems like to me. Never underestimate the power of a h-tree on your filesystem when it comes to actually FINDING files...

Besides, have you seen the performance difference on the LOCATE command?

---

### Post by regeya on 2006-11-27
> **slux said:**
> That doesn't sound right. ext3 pretty much just adds journalling and should be consistently slower than ext2 because keeping a journal adds some overhead.

It may not SOUND right, and in a textbook situation you're right, but the reality is that ext3 is actually faster than ext2.  Apparently they reduced a number of CPU usage problems and now ext3 outperforms ext2.  Plus if you have a large number of files in a dir and have dir_index enabled (and have done fsck -fDy, if it was an existing filesystem before you enabled dir_index) it's loads faster.  Reading /usr/share/doc used to be painful on ext2-based filesystems.  Now on ext3 partitions it's no big deal.

BTW, I got to this thread b/c I tried running SplitForks on an existing hfs+ partition, and tried to copy to an ext3 partition.  The transfer was painfully slow and ate all available cycles.  I have no idea if it was a controller issue or a filesystem code issue.  I don't think it was a hardware issue; I compliled a monolithic-ish kernel with support for the Sonnet card's chipset, and transfer rates are insanely fast under MacOS.  But this is on a MacOS 9/ASIP install that keeps going wonky, and I have a $0 budget for replacing OS 9.

---

### Post by RAOF on 2006-11-27
The kernel HFS+ driver works fine for me and my iPod (I like having actual permissions support on my portable hard-drive ;)).

**However**: There's no fsck.hfsplus shipped anywhere that I could find (or mkfs.hfsplus, but that's less important).  So, if you ever fail to cleanly unmount your drive, you'll lose write-support (the kernel driver refuses to mount a dirty drive read/write).  You can build the Apple fsck.hfsplus linked to on the Gentoo site, but you need to build a 32bit binary - it's not 64bit safe.

---

