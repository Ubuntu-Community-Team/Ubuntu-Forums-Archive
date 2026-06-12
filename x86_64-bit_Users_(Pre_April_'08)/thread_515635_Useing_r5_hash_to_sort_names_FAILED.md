---
title: "Useing r5 hash to sort names FAILED"
date: 2007-08-02
forum: x86 64-bit Users (Pre April '08)
---

### Post by tripmix on 2007-08-02
Today there was a power failure and when I rebooted my computer I got the above error while booting after it had read my volume groups and stuff. I rebooted and got the same again.
I have several disks set up whit lvm using reiser-fs.
I haven't noticed anything bad happening but I really wonder what it means, cuz it don't sound good and I have over 1TB of media on those disks.
Please advice.

Looks like this:
```
kjournald starting.  Commit interval 5 seconds
EXT3 FS on hda4, internal journal
EXT3-fs: mounted filesystem with ordered data mode
ReiserFS: dm-0: found reiserfs format "3.6" with standard journal
ReiserFS: dm-0: using ordered data mode
ReiserFS: dm-0: journal params: device dm-0, size 8192, journal first block 18, max trans len 1024, max batch 900, max commit age 30, max trans age 30
ReiserFS: dm-0: checking transaction log (dm-0)
ReiserFS: dm-0: Using r5 hash to sort names
ReiserFS: dm-2: found reiserfs format "3.6" with standard journal
ReiserFS: dm-2: using ordered data mode
ReiserFS: dm-2: journal params: device dm-2, size 8192, journal first block 18, max trans len 1024, max batch 900, max commit age 30, max trans age 30
ReiserFS: dm-2: checking transaction log (dm-2)
ReiserFS: dm-2: Using r5 hash to sort names
ReiserFS: dm-4: found reiserfs format "3.6" with standard journal
ReiserFS: dm-4: using ordered data mode
ReiserFS: dm-4: journal params: device dm-4, size 8192, journal first block 18, max trans len 1024, max batch 900, max commit age 30, max trans age 30
ReiserFS: dm-4: checking transaction log (dm-4)
ReiserFS: dm-4: Using r5 hash to sort names
ReiserFS: dm-3: found reiserfs format "3.6" with standard journal
ReiserFS: dm-3: using ordered data mode
ReiserFS: dm-3: journal params: device dm-3, size 8192, journal first block 18, max trans len 1024, max batch 900, max commit age 30, max trans age 30
ReiserFS: dm-3: checking transaction log (dm-3)
ReiserFS: dm-3: Using r5 hash to sort names
ReiserFS: dm-1: found reiserfs format "3.6" with standard journal
ReiserFS: dm-1: using ordered data mode
ReiserFS: dm-1: journal params: device dm-1, size 8192, journal first block 18, max trans len 1024, max batch 900, max commit age 30, max trans age 30
ReiserFS: dm-1: checking transaction log (dm-1)
ReiserFS: dm-1: Using r5 hash to sort names
Failed!
```

---

