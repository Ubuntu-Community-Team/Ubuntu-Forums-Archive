---
title: "NFS - anyone else having problems?"
date: 2005-08-13
forum: x86 64-bit Users (Pre April '08)
---

### Post by cakey on 2005-08-13
I've been trying to setup NFS on Ubuntu64.  As far as I know I've got everything I need installed.  When I try to set it up with Webmin I get this message:  

The NFS server executable was not found on your system. The NFS package does not appear to be installed.

It IS installed and according to top its running.  

Any help would be greatly appreciated.  Thanks .

---

### Post by nad on 2005-08-13
You need to have both the nfs-common and nfs-kernel-server packages installed on any computer in order to use nfs in both directions.

---

