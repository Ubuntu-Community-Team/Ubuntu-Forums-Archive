---
title: "difference between MBR and boot block"
date: 2007-12-04
forum: x86 64-bit Users (Pre April '08)
---

### Post by karmo on 2007-12-04
hi everyone
i don't understand which is the difference between MBR and boot block of the partition!
can someone explain me clearly?
i didn't found any document about boot block....

---

### Post by tszanon on 2007-12-04
From [http://www.computerhope.com/jargon/m/mbr.htm:](http://www.computerhope.com/jargon/m/mbr.htm:)
> MBR is also sometimes referred to as the master boot block and is the first sector  of the computer hard disk drive used to determine what partition  a computer will boot.

The partition boot sector keeps the program that's used to boot the system.
Is it clear? While the boot sector of the partition actually boots the system, MBR holds which partition (boot sector) should be used to boot the system.

(first time I tried to answer this I was like "easy, the difference between them is....er...I don't know. Let me search."). :)

Which leads to another question: when the system installer asks if we want to install grub to MBR or the partition, and we answer MBR, what really happens? I think it installs the program in the partition boot sector and rewrites MBR to make that partition the current boot partition.

---

### Post by sethvath on 2007-12-04
An analogy: MBR is like the start key of your car, Boot block is the engine. 

MBR holds the information, Boot block does the heavy lifting.

---

### Post by tszanon on 2007-12-04
> **sethvath said:**
> An analogy: MBR is like the start key of your car, Boot block is the engine. 

MBR holds the information, Boot block does the heavy lifting.
Good, easy to understand analogy. Thanks!

---

### Post by psusi on 2007-12-04
The MBR is the first sector of the whole disk, and contains the partition table.  Under MSDOS, it also contains enough code to load the boot sector from the active partition and run that.  Grub usually just installs the boot code directly in the MBR and doesn't bother loading a boot sector from a partition.

---

