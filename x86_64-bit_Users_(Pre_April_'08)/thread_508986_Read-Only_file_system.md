---
title: "Read-Only file system"
date: 2007-07-24
forum: x86 64-bit Users (Pre April '08)
---

### Post by ikus060 on 2007-07-24
Why ?

I reacive this error in the kernel log:
```

Jul 24 21:41:54 chloe kernel: [42997310.810000] EXT3-fs error (device md0): ext3_free_blocks_sb: bit already cleared for block 69279800
Jul 24 21:41:54 chloe kernel: [42997310.830000] Aborting journal on device md0.
Jul 24 21:41:54 chloe kernel: [42997310.920000] ext3_abort called.
Jul 24 21:41:54 chloe kernel: [42997310.930000] EXT3-fs error (device md0): ext3_journal_start_sb: Detected aborted journal
Jul 24 21:41:54 chloe kernel: [42997310.950000] Remounting filesystem read-only
Jul 24 21:41:54 chloe kernel: [42997310.950000] EXT3-fs error (device md0) in ext3_reserve_inode_write: Journal has aborted
Jul 24 21:41:54 chloe kernel: [42997310.970000] EXT3-fs error (device md0) in ext3_truncate: Journal has aborted
Jul 24 21:41:54 chloe kernel: [42997310.990000] EXT3-fs error (device md0) in ext3_reserve_inode_write: Journal has aborted
Jul 24 21:41:54 chloe kernel: [42997311.010000] EXT3-fs error (device md0) in ext3_orphan_del: Journal has aborted
Jul 24 21:41:54 chloe kernel: [42997311.020000] EXT3-fs error (device md0) in ext3_reserve_inode_write: Journal has aborted
Jul 24 21:41:54 chloe kernel: [42997311.180000] __journal_remove_journal_head: freeing b_committed_data
Jul 24 21:41:54 chloe last message repeated 24 times

```

At reboot I receive this : 
```

Jul 24 21:46:24 chloe kernel: [42949394.930000] EXT3-fs warning (device md0): ext3_clear_journal_err: Filesystem error recorded from previous mount: IO failure
Jul 24 21:46:24 chloe kernel: [42949394.930000] EXT3-fs warning (device md0): ext3_clear_journal_err: Marking fs in need of filesystem check.
Jul 24 21:46:24 chloe kernel: [42949394.980000] EXT3-fs warning: mounting fs with errors, running e2fsck is recommended
Jul 24 21:46:24 chloe kernel: [42949394.980000] EXT3 FS on md0, internal journal
Jul 24 21:46:24 chloe kernel: [42949394.980000] EXT3-fs: recovery complete.
Jul 24 21:46:24 chloe kernel: [42949394.980000] EXT3-fs: mounted filesystem with ordered data mode.

```

I was executing a rm -R foldername on the dick when it's append. I reboot, I rexecute the commend and it's go in read-only mode again.

The dick is a raid5 software volume.

---

### Post by kuja on 2007-07-24
Apparently there's a file system error. Try running fsck on the partition and seeing if it will fix it for you :)

---

