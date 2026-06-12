---
title: "upgrade broke - perl shared lib error"
date: 2008-12-31
forum: x86 64-bit Users
---

### Post by ethort on 2008-12-31
Hi all.
I recently upgraded from 8.04 to 8.10. During the upgrade the process broke down.
When I try to apt-get upgrade I get the attached output telling me

> perl: error while loading shared libraries: libperl.so.5.8: cannot open shared object file: No such file or directory 

I have libperl5.10 installed.

sysinfo:
Release: Ubuntu 8.10 (interpid)
GNOME: 2.24.1
Kernel: 2.6.24-22-generic
CPU: AMD Athlon(tm) 64 Processor 3500+  2200MHz


Any help would be appreciated. 

FULL OUTPUT:
> user@user-desktop:~$ sudo apt-get upgrade 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
11 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up foomatic-filters (4.0.0~bzr177-0ubuntu1) ...
perl: error while loading shared libraries: libperl.so.5.8: cannot open shared object file: No such file or directory
dpkg: error processing foomatic-filters (--configure):
 subprocess post-installation script returned error exit status 127
Setting up hplip (2.8.7-0ubuntu6) ...
Creating/updating hplip user account...
perl: error while loading shared libraries: libperl.so.5.8: cannot open shared object file: No such file or directory
dpkg: error processing hplip (--configure):
 subprocess post-installation script returned error exit status 127
Setting up linux-image-2.6.27-9-generic (2.6.27-9.19) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.27-9-generic
Running postinst hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.27-9-generic
Found kernel: /boot/vmlinuz-2.6.24-22-generic
Found kernel: /boot/vmlinuz-2.6.24-21-generic
Found kernel: /boot/vmlinuz-2.6.24-19-generic
Found kernel: /boot/vmlinuz-2.6.24-18-generic
Found kernel: /boot/vmlinuz-2.6.24-17-generic
Found kernel: /boot/vmlinuz-2.6.24-16-generic
Found kernel: /boot/vmlinuz-2.6.22-14-generic
Found kernel: /boot/memtest86+.bin
perl: error while loading shared libraries: libperl.so.5.8: cannot open shared object file: No such file or directory
User postinst hook script [/sbin/update-grub] exited with value 127
dpkg: error processing linux-image-2.6.27-9-generic (--configure):
 subprocess post-installation script returned error exit status 127
Setting up bash-completion (20060301-4ubuntu1) ...
perl: error while loading shared libraries: libperl.so.5.8: cannot open shared object file: No such file or directory
dpkg: error processing bash-completion (--configure):
 subprocess post-installation script returned error exit status 127
Setting up ufw (0.23.2) ...
No apport report written because MaxReports is reached already
                                                              perl: error while loading shared libraries: libperl.so.5.8: cannot open shared object file: No such file or directory
dpkg: error processing ufw (--configure):
 subprocess post-installation script returned error exit status 127
Setting up gconf2-common (2.24.0-0ubuntu1) ...
No apport report written because MaxReports is reached already
                                                              perl: error while loading shared libraries: libperl.so.5.8: cannot open shared object file: No such file or directory
dpkg: error processing gconf2-common (--configure):
 subprocess post-installation script returned error exit status 127
Setting up libpaper1 (1.1.23+nmu1) ...
No apport report written because MaxReports is reached already
                                                              perl: error while loading shared libraries: libperl.so.5.8: cannot open shared object file: No such file or directory
dpkg: error processing libpaper1 (--configure):
 subprocess post-installation script returned error exit status 127
No apport report written because MaxReports is reached already
                                                              Setting up libsensors3 (1:2.10.7-1) ...
udev active, devices will be created in /dev/.static/dev/
perl: error while loading shared libraries: libperl.so.5.8: cannot open shared object file: No such file or directory
dpkg: error processing libsensors3 (--configure):
 subprocess post-installation script returned error exit status 127
Setting up r-base-core (2.7.1-2) ...
No apport report written because MaxReports is reached already
                                                              Setting R_PAPERSIZE_USER default to 'letter'
perl: error while loading shared libraries: libperl.so.5.8: cannot open shared object file: No such file or directory
dpkg: error processing r-base-core (--configure):
 subprocess post-installation script returned error exit status 127
No apport report written because MaxReports is reached already
                                                              Setting up samba-common (2:3.2.3-1ubuntu3.3) ...
perl: error while loading shared libraries: libperl.so.5.8: cannot open shared object file: No such file or directory
dpkg: error processing samba-common (--configure):
 subprocess post-installation script returned error exit status 127
Setting up tex-common (1.11) ...
No apport report written because MaxReports is reached already
                                                              perl: error while loading shared libraries: libperl.so.5.8: cannot open shared object file: No such file or directory
dpkg: error processing tex-common (--configure):
 subprocess post-installation script returned error exit status 127
Processing triggers for libc6 ...
No apport report written because MaxReports is reached already
                                                              ldconfig deferred processing now taking place
Processing triggers for menu ...
Errors were encountered while processing:
 foomatic-filters
 hplip
 linux-image-2.6.27-9-generic
 bash-completion
 ufw
 gconf2-common
 libpaper1
 libsensors3
 r-base-core
 samba-common
 tex-common
E: Sub-process /usr/bin/dpkg returned an error code (1)


---

### Post by ethort on 2009-01-01
Eventually, I did:

```
cp /usr/bin/perl /usr/local/bin/perl
```

and now the problem is no more.

Cheers,
e.

---

