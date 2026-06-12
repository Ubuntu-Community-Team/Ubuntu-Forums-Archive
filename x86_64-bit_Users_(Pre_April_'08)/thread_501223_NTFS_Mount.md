---
title: "NTFS Mount"
date: 2007-07-15
forum: x86 64-bit Users (Pre April '08)
---

### Post by sfarber on 2007-07-15
Hello.
I have a NTFS Partitions mounted on my system (Done automaticly by the installer).
The problem is that I can't write files to that partition, only read files from it.

Is that a mount command to be able to wrtie files to NTFS partition?

---

### Post by KMFDM on 2007-07-15
> **sfarber said:**
> Hello.
I have a NTFS Partitions mounted on my system (Done automaticly by the installer).
The problem is that I can't write files to that partition, only read files from it.

Is that a mount command to be able to wrtie files to NTFS partition?

i think you need  driver called ntfs-3g. [www.ntfs-3g.org](www.ntfs-3g.org)

---

### Post by Vajra Vrtti on 2007-07-15
In Feisty:
[LIST=1]
[*]Install package **ntfs-config**.
[*]Open *System Tools -> NTFS Configuration Tool*.
[*]Enable NTFS *write* support
[/LIST]

---

