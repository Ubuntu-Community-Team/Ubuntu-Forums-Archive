---
title: "One solution for IDE HDD problems"
date: 2008-06-22
forum: x86 64-bit Users
---

### Post by phlembob on 2008-06-22
I think I have found one conflict, which has effected a good number of people using both SATA and IDE HDDs.  I had physically selected the IDE HDD (an older HDD) to master.  My SATA was SATA1 or master also.  I physically selected Slave on the IDE HDD.  Data is called up in Ubuntu without error and two times in a row the IDE HDD is seen as what it is.  The original problems changed with NTFS-3g installation, but was intermittently seen.  The "IDE HDD has a default name of scsi drive---can't mount of rename" was the problem's name that this answers.  It may answer other problems also.

---

