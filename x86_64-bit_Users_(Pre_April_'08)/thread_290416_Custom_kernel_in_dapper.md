---
title: "Custom kernel in dapper"
date: 2006-11-01
forum: x86 64-bit Users (Pre April '08)
---

### Post by mune on 2006-11-01
I use the kernel
```
$ uname -a
Linux lello 2.6.15-27-amd64-generic #1 SMP PREEMPT Sat Sep 16 01:50:50 UTC 2006 x86_64 GNU/Linux
```
on Ubuntu Dapper

I own a mobile phone with WinMobile and following the instructions for the sync (multisync+module for since+module for evolution) but when when "depprobe" the module ipaq it crashes (I found it in the syslog; ipaw is required by since-serial).

The module crashes so I thought to rebuild the kernel (and all the modules).

To create a new kernel I did the following:
- downloaded the deb with the appropriate kernel sources which create a deb in /usr/src (linux-source-2.6.15.tar.bz2);
- downlpaded the package kernel-package;
```
$ cd /usr/src/linux-source-2.6.15/
```
- copied the configuration of the kernel I am using
```
$ sudo cp /boot/config-2.6.15-27-amd64-generic .config
```
```
$ sudo make-kpkg clean
```
```
$ sudo make-kpkg kernel_image --append_to_version "-mune"
```
```
$ cd ..
```
```
$ sudo dpkg -i
kernel-image-2.6.15.7-ubuntu1-mune_10.00.Custom_amd64.deb
```

I reboot the system and I found the new kernel in the grub choises (dpkg added it in menu.lst of grub), but the system doesn't boot complaing about being unable to use /dev/sda3.

Have you any ides of what I'm doing wrong?

Thanks

Fede

---

### Post by John.Michael.Kane on 2006-11-01
Have a read. take your pick of which one fits your need's....
[http://ubuntuforums.org/showthread.php?t=217657&highlight=compiling+kernel](http://ubuntuforums.org/showthread.php?t=217657&highlight=compiling+kernel)
[http://ubuntuforums.org/showthread.php?t=157560&highlight=compiling+kernel](http://ubuntuforums.org/showthread.php?t=157560&highlight=compiling+kernel)
[http://ubuntuforums.org/showthread.php?t=85064&highlight=compiling+kernel](http://ubuntuforums.org/showthread.php?t=85064&highlight=compiling+kernel)
[http://ubuntuforums.org/showthread.php?t=219669&highlight=compiling+kernel](http://ubuntuforums.org/showthread.php?t=219669&highlight=compiling+kernel)
[http://ubuntuforums.org/showthread.php?t=56835&highlight=compiling+kernel](http://ubuntuforums.org/showthread.php?t=56835&highlight=compiling+kernel)
[http://ubuntuforums.org/showthread.php?t=84174&highlight=compiling+kernel](http://ubuntuforums.org/showthread.php?t=84174&highlight=compiling+kernel)

---

