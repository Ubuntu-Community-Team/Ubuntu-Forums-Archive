---
title: "Booting off NTFS with ext3 loopback"
date: 2009-04-16
forum: x86 64-bit Users
---

### Post by rob.jackson.ky on 2009-04-16
I installed ubuntu using wubi and everything worked great.  Since then I made room for a etx3 partition and installed the 9.04 beta on it.  Just for fun I decided to play around with gentoo.  I created a gentoo.disk file along side the root.disk file on the ntfs partition.  I must be missing something in my kernel configuration because I can not get the / (root partition actually gentoo.disk) to mount.  The error is Can not open inital console.  Try passing INIT= at bootup.  Anyone know what I need in the kernel to mount the ntfs to /host and the loopback ext3 to /.

:(

---

