---
title: "Anyone have VLC working with Ubuntu 5.10 64 Bit"
date: 2005-10-31
forum: x86 64-bit Users (Pre April '08)
---

### Post by greenfrog on 2005-10-31
Anyone have a sucessful install of VLC with libdvdcss2 working?
If so please let the rest of us know how to get running.
Thanks

---

### Post by youngster1 on 2005-11-02
1) Install VLC using Synaptic

2) Downlad and install libdvdcss2 using the following process:

Go to [ftp://ftp.nerim.net/debian-marillat/pool/main/libd/libdvdcss/](ftp://ftp.nerim.net/debian-marillat/pool/main/libd/libdvdcss/)
get the following files:
libdvdcss2_1.2.9-0.0_amd64.deb
libdvdcss2-dev_1.2.9-0.0_amd64.deb

$ sudo dpkg -i libdvdcss2_1.2.9-0.0_amd64.deb
$ sudo dpkg -i libdvdcss2-dev_1.2.9-0.0_amd64.deb

---

