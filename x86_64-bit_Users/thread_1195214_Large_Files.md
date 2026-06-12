---
title: "Large Files"
date: 2009-06-23
forum: x86 64-bit Users
---

### Post by ve3rpm on 2009-06-23
I've been attempting to dupe my HDD to another HDD, and it seems that any file larger than 4 gig stops and tells me that the file is too large... Is this normal?  If it is, is there a work around?  Thanx in advance.

---

### Post by ajgreeny on 2009-06-23
What is the filesystem on the disk you are duplicating to as that may well be the problem?  fat32 has a file max of 4GB.  If that is the reason, you will need to reformat that drive to ntfs or a typical linux filesystem such as ext3.

---

### Post by ve3rpm on 2009-06-23
K, thanx that would be the problem... I'll fix it now.

---

### Post by ve3rpm on 2009-06-23
Why is it so hard to mark this as solved?

---

### Post by ajgreeny on 2009-06-23
Just edit your first post and in the title add SOLVED as the first word.  The Solved button has been missing for a long time now; shame, but this is the way to do it now.

---

