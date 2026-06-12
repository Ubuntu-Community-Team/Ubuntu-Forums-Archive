---
title: "Cannot Read DVD from Hardy"
date: 2008-08-09
forum: x86 64-bit Users
---

### Post by lawkie on 2008-08-09
Hi All,

I am running Ubuntu 8.04 and I cant read ANY DVD that I put into my DVD reader (Asus Quiettrack).

Cd's are no problem, only DVD's ... normal retail ones.
Mounting manually doesnt work too. Here is my dmesg.

root@MainFrame:/# mount /media/cdrom0/ -o unhide
mount: block device /dev/scd0 is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/scd0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


dmesg: 

[252585.346981] sr0: rw=0, want=5886696, limit=4
[252585.346983] attempt to access beyond end of device
[252585.346985] sr0: rw=0, want=5886472, limit=4
[252585.346987] attempt to access beyond end of device
[252585.346989] sr0: rw=0, want=1252, limit=4
[252585.346992] attempt to access beyond end of device
[252585.346993] sr0: rw=0, want=1028, limit=4
[252585.346995] UDF-fs: No partition found (1)
[252585.356738] attempt to access beyond end of device
[252585.356743] sr0: rw=0, want=68, limit=4
[252585.356747] isofs_fill_super: bread failed, dev=sr0, iso_blknum=16, block=16
root@MainFrame:/# 

root@MainFrame:/# uname -a
Linux MainFrame 2.6.24-19-generic #1 SMP Fri Jul 11 21:01:46 UTC 2008 x86_64 GNU/Linux

I installed all the latest patches ... anyone who can help me out? Is this a bug??

Kind regards,

Lawkie

---

### Post by silkstone on 2008-08-09
Do you have libdvdcss2 installed?

If not, first enable the Medibuntu repositories...

```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list

wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```

Then...

```
sudo apt-get install libdvdcss2
```

---

### Post by cdtech on 2008-08-09
Also, could you post your "/etc/fstab" file....

Thanks.

---

### Post by lawkie on 2008-08-10
root@MainFrame:/# apt-get install libdvdcss2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libdvdcss2 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

root@MainFrame:/# cat /etc/fstab 
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=d364fa59-7bb9-4c1f-b329-385351ff6d0e /               xfs     relatime        0       1
# /dev/sdb1
#UUID=f2129838-e78a-4e27-a030-7837a23d4508 /ENC            ext3    relatime        0       2
# /dev/md2
UUID=9e4c77c9-9823-4ddc-afd4-d988f45ff6e6 /Storage        ext3    relatime        0       2
# /dev/sdb2
#UUID=813766ee-1856-4c00-9ea4-9bc8aa6dd89f /SWAP           ext3    relatime        0       2
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0


Does noone else has this problem?
Can you guys read and mount normal dvd's?
It's really weird .. I never encountered this ...
Thanks for the help so far but unfortunately the problem still exists.

Kind regards,

Lawkie

---

