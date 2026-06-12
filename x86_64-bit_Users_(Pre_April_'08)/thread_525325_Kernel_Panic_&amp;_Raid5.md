---
title: "Kernel Panic &amp; Raid5"
date: 2007-08-14
forum: x86 64-bit Users (Pre April '08)
---

### Post by ikus060 on 2007-08-14
Hi,

 I setup a wild a go a server with 3 drive 250gb in software raid5. Since 4 month, the server start to crash randomly (it's what I thought). I got Kernel panic, read-only file system. By time, I came to understand that it's not a random crash. It's alway happen when the file system is under high demand.

In conclusion, I think it's a the source of all this crash become from my raid configuration. There is anything I can do to know if there is a problem with my configuration or if a HD is dead ?

---

### Post by ikus060 on 2007-08-19
I found a way to reproduce the problem all the time. I just have to run the bonnie tool on the array I have this error :
```
Aug 19 17:43:38 chloe kernel: [42957420.010000] kjournald starting.  Commit interval 5 seconds
Aug 19 17:43:38 chloe kernel: [42957420.060000] EXT3 FS on md0, internal journal
Aug 19 17:43:38 chloe kernel: [42957420.060000] EXT3-fs: mounted filesystem with ordered data mode.
Aug 19 17:59:14 chloe kernel: [42958355.790000] EXT3-fs error (device md0): ext3_free_blocks_sb: bit already cleared for block 74598712
Aug 19 17:59:14 chloe kernel: [42958355.800000] Aborting journal on device md0.
Aug 19 17:59:14 chloe kernel: [42958355.840000] ext3_abort called.
Aug 19 17:59:14 chloe kernel: [42958355.840000] EXT3-fs error (device md0): ext3_journal_start_sb: Detected aborted journal
Aug 19 17:59:14 chloe kernel: [42958355.850000] Remounting filesystem read-only
Aug 19 17:59:14 chloe kernel: [42958355.860000] EXT3-fs error (device md0) in ext3_reserve_inode_write: Journal has aborted
Aug 19 17:59:14 chloe kernel: [42958355.870000] EXT3-fs error (device md0) in ext3_truncate: Journal has aborted
Aug 19 17:59:14 chloe kernel: [42958355.880000] EXT3-fs error (device md0) in ext3_reserve_inode_write: Journal has aborted
Aug 19 17:59:14 chloe kernel: [42958355.900000] EXT3-fs error (device md0) in ext3_orphan_del: Journal has aborted
Aug 19 17:59:14 chloe kernel: [42958355.910000] EXT3-fs error (device md0) in ext3_reserve_inode_write: Journal has aborted
Aug 19 17:59:14 chloe kernel: [42958355.930000] __journal_remove_journal_head: freeing b_committed_data
```

So I google it and it's seem that it's not a isolated problem :
[http://forum.hardware.fr/hfr/OSAlternatifs/Hardware-2/corruption-ext3fs-logiciel-sujet_53854_1.htm](http://forum.hardware.fr/hfr/OSAlternatifs/Hardware-2/corruption-ext3fs-logiciel-sujet_53854_1.htm) (french)
[http://osdir.com/ml/linux.raid/2005-01/msg00154.html](http://osdir.com/ml/linux.raid/2005-01/msg00154.html)

But I still can't find a solution.

I pass fsck without sucess. 

Linux chloe 2.6.15-26-server #1 SMP Fri Sep 8 21:00:37 UTC 2006 i686 GNU/Linux

---

### Post by ikus060 on 2007-08-19
I update to Kernel 2.6.15-28-server  to see if it's make any diffrence

---

### Post by ikus060 on 2007-08-20
Do you suggest that I rebuild all the array with the same disk ??

---

