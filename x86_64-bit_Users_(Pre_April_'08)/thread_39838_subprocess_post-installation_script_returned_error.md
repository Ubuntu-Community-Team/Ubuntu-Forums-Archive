---
title: "subprocess post-installation script returned error exit status 2"
date: 2005-06-06
forum: x86 64-bit Users (Pre April '08)
---

### Post by kevkiwi on 2005-06-06
Hi,

Just installed Ubuntu Linux 5.04 : The Hoary Hedgehog Release on my AMD64 machine and keep getting an error message whenever I use apt-get.  Here is an example:

kevin@ubuntu-dev:~$ sudo apt-get install clamav
Reading package lists... Done
Building dependency tree... Done
Suggested packages:
  unrar lha clamav-docs
Recommended packages:
  arj unzoo
The following NEW packages will be installed:
  clamav
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B/57.7kB of archives.
After unpacking 197kB of additional disk space will be used.

Preconfiguring packages ...
Selecting previously deselected package clamav.
(Reading database ... 59104 files and directories currently installed.)
Unpacking clamav (from .../clamav_0.83-2ubuntu1_amd64.deb) ...
Setting up linux-image-2.6.10-5-amd64-generic (2.6.10-34.1) ...
File descriptor 3 left open
File descriptor 4 left open
File descriptor 5 left open
File descriptor 6 left open
File descriptor 7 left open
    Finding all volume groups
  No volume groups found
/usr/sbin/mkinitrd: /dev/evms/.nodes/sdb8: Cannot find LVM device
Failed to create initrd image.
dpkg: error processing linux-image-2.6.10-5-amd64-generic (--configure):
 subprocess post-installation script returned error exit status 2
Setting up clamav (0.83-2ubuntu1) ...
Errors were encountered while processing:
 linux-image-2.6.10-5-amd64-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

Can anyone tell this Linux novice what this means and how to correct it?

Cheers,
Kevin

---

### Post by nictuku on 2005-06-24
I have exactly the same issue.

It's not a 64 architecture issue. I belive it's related to software RAID setup and mkinitrd wrong gessing.


# apt-get install linux-image-2.6.11-1-686-smp
Reading package lists... Done
Building dependency tree... Done
linux-image-2.6.11-1-686-smp is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up linux-image-2.6.11-1-686-smp (2.6.11-0.2) ...
File descriptor 3 left open
File descriptor 4 left open
File descriptor 5 left open
File descriptor 6 left open
File descriptor 7 left open
    Finding all volume groups
  No volume groups found
/usr/sbin/mkinitrd: /dev/evms/.nodes/sda5: Cannot find LVM device
Failed to create initrd image.
dpkg: error processing linux-image-2.6.11-1-686-smp (--configure):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 linux-image-2.6.11-1-686-smp
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

