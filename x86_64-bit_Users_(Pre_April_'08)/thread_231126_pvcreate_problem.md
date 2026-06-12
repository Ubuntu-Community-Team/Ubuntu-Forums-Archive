---
title: "pvcreate problem"
date: 2006-08-07
forum: x86 64-bit Users (Pre April '08)
---

### Post by sles on 2006-08-07
Hello!

This is 6.06 amd64:

root@dm:~# pvcreate /dev/sda5
  Physical volume "/dev/sda5" successfully created
root@dm:~# pvcreate /dev/sda5
  Failed to write physical volume "/dev/sda5"
root@dm:~# pvcreate /dev/sda5
  Physical volume "/dev/sda5" successfully created

Then:

root@dm:~# vgcreate vg00 /dev/sda5
  No physical volume label read from /dev/sda5
  /dev/sda5 not identified as an existing physical volume
  Unable to add physical volume '/dev/sda5' to volume group 'vg00'.


Is this pvcreate or sata driver problem?

---

### Post by sles on 2006-08-07
Now I know that this is problem in ubuntu's kernel.
All works OK with Xen's 2.6.16.
Hope this will be fixed in next ubuntu kernel :-)

---

### Post by Kilz on 2006-08-07
> **sles said:**
> Now I know that this is problem in ubuntu's kernel.
All works OK with Xen's 2.6.16.
Hope this will be fixed in next ubuntu kernel :-)

If you found something that needs to be fixed, [fill out a bug report.]("https://help.ubuntu.com/community/ReportingBugs")

---

### Post by janl on 2006-08-19
I got around it by giving the full path:

pvcreate /dev/sda6
vgcreate thevg /dev/evms/sda6

---

