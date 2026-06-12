---
title: "[SOLVED] Setup"
date: 2008-09-17
forum: x86 64-bit Users
---

### Post by wfp on 2008-09-17
Wondering if some one could show me the best way to remove the 32bit ubuntu and replace it with 64-bit, sorry i am still a bit noobish.    Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5353    42997941    7  HPFS/NTFS
/dev/sda2            5354       18129   102623220    5  Extended
/dev/sda3           18130       19457    10667160    7  HPFS/NTFS
/dev/sda5            5354       17799    99972463+  83  Linux
/dev/sda6           17800       18129     2650693+  82  Linux swap / Solaris
 
So somehow i would just like to remove ubuntu from /dev/sda5 and install 64-bit ubuntu there.

---

### Post by Kilz on 2008-09-17
> **wfp said:**
> Wondering if some one could show me the best way to remove the 32bit ubuntu and replace it with 64-bit, sorry i am still a bit noobish.    Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5353    42997941    7  HPFS/NTFS
/dev/sda2            5354       18129   102623220    5  Extended
/dev/sda3           18130       19457    10667160    7  HPFS/NTFS
/dev/sda5            5354       17799    99972463+  83  Linux
/dev/sda6           17800       18129     2650693+  82  Linux swap / Solaris
 
So somehow i would just like to remove ubuntu from /dev/sda5 and install 64-bit ubuntu there.

The easiest way it to just use the install disk. During install there is a place to partition the disk. At that point you can tell the installer to delete that partition and use the space for the install.

---

### Post by Sef on 2008-09-17
> The easiest way it to just use the install disk. During install there is a place to partition the disk. At that point you can tell the installer to delete that partition and use the space for the install.

You only need to delete and reformat the root partition.  In your case that is sda5.

---

### Post by wfp on 2008-09-17
Great will give it a go thanks.

---

### Post by wfp on 2008-09-19
Thanks again for the help the install went really smooth. I just did what you said and deleted sda5 reformatted to ext3, set the mount point and finished. Thanks this is a new machine i have only had for a few days now. So i first installed 32-bit ubuntu and decided man i have a AMD X2 64 processor lets put these to use. Thanks :)

---

