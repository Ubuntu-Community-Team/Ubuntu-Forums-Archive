---
title: "Unable to Access NTFS drives/partitions"
date: 2006-07-17
forum: x86 64-bit Users (Pre April '08)
---

### Post by amcquown on 2006-07-17
The drives are mounted fine, but trying to browse the hard drive I get "You do not have the permissions necessary to view the contents of "hda1"." How do I fix this? These are windows drives using NTFS. If it helps, I'm using ReiserFS, 6.06 Dapper. Properties say the drive contents are unreadable.

---

### Post by Jagot on 2006-07-17
Have a look here:

[https://help.ubuntu.com/5.10/ubuntu/faq/C/fg-windows-partitions.html](https://help.ubuntu.com/5.10/ubuntu/faq/C/fg-windows-partitions.html)

See if you're fstab matches up.

---

### Post by amcquown on 2006-07-17
That worked - they were pre-mounted without any read access. :mad:

---

