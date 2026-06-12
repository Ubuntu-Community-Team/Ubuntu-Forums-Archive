---
title: "apt-get install stunnel4"
date: 2007-03-16
forum: x86 64-bit Users (Pre April '08)
---

### Post by kaushalshriyan on 2007-03-16
tmp$sudo apt-get install stunnel4
Reading package lists... Done
Building dependency tree... Done
The following packages will be upgraded:
 stunnel4
1 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
1 not fully installed or removed.
Need to get 0B/93.2kB of archives.
After unpacking 94.2kB of additional disk space will be used.
(Reading database ... 281592 files and directories currently installed.)
Preparing to replace stunnel4 2:4.090-1 (using
.../stunnel4_2%3a4.140-5ubuntu1_i386.deb) ...
Document `stunnel4' is not installed, cannot remove.
Unpacking replacement stunnel4 ...
Setting up stunnel4 (4.140-5ubuntu1) ...
Installing new version of config file /etc/stunnel/stunnel.conf ...
Installing new version of config file /etc/init.d/stunnel4 ...
Adding system user `stunnel4'...
*** glibc detected *** free(): invalid pointer: 0xf7fb6154 ***
/var/lib/dpkg/info/stunnel4.postinst: line 45:  2578 Aborted
     $ADDUSER --system --disabled-password --disabled-login --home
/var/run/stunnel4 --no-create-home --group $USER
dpkg: error processing stunnel4 (--configure):
 subprocess post-installation script returned error exit status 134
Errors were encountered while processing:
 stunnel4
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

