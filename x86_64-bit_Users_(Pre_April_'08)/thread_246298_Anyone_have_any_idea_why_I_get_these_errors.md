---
title: "Anyone have any idea why I get these errors"
date: 2006-08-29
forum: x86 64-bit Users (Pre April '08)
---

### Post by AA_J on 2006-08-29
Anyone have any idea why I get these errors on an upgrade from Breezy to Dapper? Thanks


root@ubuntu:/etc/apt# apt-get dist-upgrade
Reading package lists... Done
Building dependency tree... Done
Calculating upgrade... Done
The following packages have been kept back:
  cpp cpp-4.0 g++ g++-4.0 gcc gcc-4.0 libc6-dev libstdc++6-4.0-dev
0 upgraded, 0 newly installed, 0 to remove and 8 not upgraded.


root@ubuntu:/etc/apt# apt-get upgrade
Reading package lists... Done
Building dependency tree... Done
The following packages have been kept back:
  cpp cpp-4.0 g++ g++-4.0 gcc gcc-4.0 libc6-dev libstdc++6-4.0-dev
0 upgraded, 0 newly installed, 0 to remove and 8 not upgraded.


root@ubuntu:/etc/apt# uname -rn
ubuntu 2.6.12-9-amd64-generic

---

### Post by AA_J on 2006-08-29
have also tried

root@ubuntu:/etc/apt# aptitude dist-upgrade
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
The following packages have been kept back:
  cpp cpp-4.0 g++ g++-4.0 gcc gcc-4.0 libc6-dev libstdc++6-4.0-dev
0 packages upgraded, 0 newly installed, 0 to remove and 8 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done

---

### Post by funchords on 2006-08-29
Do you have anything in /etc/apt/preferences

---

