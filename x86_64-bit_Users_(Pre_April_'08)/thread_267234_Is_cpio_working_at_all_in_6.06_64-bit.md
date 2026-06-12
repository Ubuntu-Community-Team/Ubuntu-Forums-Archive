---
title: "Is cpio working at all in 6.06 64-bit?"
date: 2006-09-28
forum: x86 64-bit Users (Pre April '08)
---

### Post by clevershark on 2006-09-28
I'm trying to use cpio to open one of those damned Oracle distribution files, but I don't think it's working at all. It's been on the same operation for about 15 minutes and this is the output I get from ps aux:

[user]     13131  0.0  0.0   3824   440 pts/0    S+   11:20   0:00 cpio -id as_linux_x86_101300_disk1.cpio

I've checked and I am using the latest version.

---

### Post by PrecpiceDevelopment on 2006-10-03
Not sure if you fixed your problem but try this:

cpio -idmv < file.cpio

Jerry

---

