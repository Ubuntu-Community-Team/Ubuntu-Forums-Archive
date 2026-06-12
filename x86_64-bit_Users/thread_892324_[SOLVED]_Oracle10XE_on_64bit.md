---
title: "[SOLVED] Oracle10XE on 64bit"
date: 2008-08-17
forum: x86 64-bit Users
---

### Post by 4ugeistr on 2008-08-17
Is it possible to install Oracle 10g Express Edition under 64bit Ubuntu 8.04?
Oracle presents only the i386 debian packages....

***LATER***
sorry guys, it was reckless of me to make this thread. i should have dug deeper and tried harder before doing so. 
moreover, the topic is duped, and not singularily.

architecture forcing appeared to be just a single command
> sudo dpkg --force-architecture -i oracle-xe_10.2.0.1-1.0_i386.deb

during the installation the only problem i encountered was the unsufficient swap memory which i extended with **GParted**
Oracle requests 1024Mb swap
actually, i had an 1000Mb swap partition after an OS install, but eventually it turned out to be 950 =)

everything works fine except for some GUI glitches in APEX

Ubuntu rocks!

---

### Post by JBringolf on 2009-05-27
I also had no problem installing xe under amd64 but cannot get PHP5 to recognize oci8 - anyone have any hints on this.

---

### Post by pixel :-) on 2009-05-27
they should be both 32bit?

---

### Post by JBringolf on 2009-05-27
Yes - the problem is after installing xe and it is working fine - I try to get PHP5 to load oci8 and following directions I find on line it breaks xe so I cannot connect.


oracleXE: error while loading shared libraries: libaio.so.1: cannot open shared object file: No such file or directory
ERROR:
ORA-12547: TNS:lost contact

---

