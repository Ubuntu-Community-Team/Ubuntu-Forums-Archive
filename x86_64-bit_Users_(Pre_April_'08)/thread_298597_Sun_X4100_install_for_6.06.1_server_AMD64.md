---
title: "Sun X4100 install for 6.06.1 server AMD64"
date: 2006-11-13
forum: x86 64-bit Users (Pre April '08)
---

### Post by ke han on 2006-11-13
I am trying to install Ubuntu 6.06.1 server AMD64 on a Sun X4100.  The two 73 GB SAS drives are configured standard as RAID-1 by the LSI MPT card.  This config is recongnized by both Solaris 10 and Centos 4.4 installers.  
When I try installation with the Ubuntu 6.06.1 server AMD64 ISO, the install "locks up" when it tries to start the partitioning process.
Any ideas?
thanks, ke han

---

### Post by simply_marcus on 2006-11-16
I did it this way, try the same:

Leave the hd's "unRAIDed"
Install Dapper on /dev/sda
Built Kernel 2.6.18 with megaraid, megaraid_sas, _mm, _mbox support
Start Kernel 2.6.18 and checked if modules are loaded
reboot, create RAID, migrate data to RAID
start up and hope its done ;-)

Theres a new ISO inbetween having a 2.6.18 kernel, but i didn't manage to install this one, it failed with error "modprobe runaway loop in binfmt-464c" or sth like that..

---

