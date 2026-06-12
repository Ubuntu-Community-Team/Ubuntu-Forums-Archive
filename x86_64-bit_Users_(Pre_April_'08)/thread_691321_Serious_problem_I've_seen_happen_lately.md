---
title: "Serious problem I've seen happen lately"
date: 2008-02-08
forum: x86 64-bit Users (Pre April '08)
---

### Post by xithilinx on 2008-02-08
Okay I'm not exactly sure what's going on, but when installing certain files onto my computer via the sudo apt-get install option, I get some weird errors which are just making me a bit unsteady. Even though the error exist I don't have any problem installing the software, only a feeling that something is horribly wrong and I should do something about it. 

E.x Installing pychess

 sudo apt-get install pychess
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  pychess
0 upgraded, 1 newly installed, 0 to remove and 4 not upgraded.
1 not fully installed or removed.
Need to get 411kB of archives.
After unpacking 1737kB of additional disk space will be used.
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe pychess 0.6.1-1ubuntu1 [411kB]
Fetched 411kB in 1s (291kB/s)   
Selecting previously deselected package pychess.
(Reading database ... 193728 files and directories currently installed.)
Unpacking pychess (from .../pychess_0.6.1-1ubuntu1_all.deb) ...
Setting up linux-image-2.6.22-14-generic (2.6.22-14.51) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.22-14-generic
/usr/sbin/mkinitramfs: 13: getopt: not found
Terminating...
update-initramfs: failed for /boot/initrd.img-2.6.22-14-generic
Failed to create initrd image.
dpkg: error processing linux-image-2.6.22-14-generic (--configure):
 subprocess post-installation script returned error exit status 2
Setting up pychess (0.6.1-1ubuntu1) ...

Errors were encountered while processing:
 linux-image-2.6.22-14-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

Please help I really do enjoy ubuntu and am really hoping that I won't have to reinstall suddenly or have a system crash or something.

---

### Post by JoshuaRL on 2008-02-08
I'm not sure exactly what the issue is, but I notice that it says 4 packages not upgraded.  So try:
```
sudo apt-get update
sudo apt-get upgrade
```

And I would also suggest going into Synaptic and fix anything in the broken filter.  And trying the following could only help:

```

sudo apt-get -f install
sudo dpkg --configure -a

```

---

### Post by xithilinx on 2008-02-09
The bad thing about this error is if I try any of those commands it always returns back the same exact error I got in message one. :\

---

### Post by tgalati4 on 2008-02-09
It looks like a kernel upgrade when bad.  Post the output of:

>uname -a

Perhaps if you run an older version of the kernel, which should show up in your boot-up GRUB list, then you may be able to create the proper initrd file for the latest kernel.

---

### Post by Heinzelotto on 2008-02-09
it seems like you should force installing the linux-image package
sudo dpkg -i --force-all /var/cache/apt/archives/linux-image-2.6.22-14-generic....... (complete the filename of your package here)

---

### Post by xithilinx on 2008-02-09
> **tgalati4 said:**
> It looks like a kernel upgrade when bad.  Post the output of:

>uname -a

Perhaps if you run an older version of the kernel, which should show up in your boot-up GRUB list, then you may be able to create the proper initrd file for the latest kernel.

Linux ithilin 2.6.22-14-generic #1 SMP Thu Jan 31 23:33:13 UTC 2008 x86_64 GNU/Linux

---

### Post by Cappy on 2008-02-09
Try
```
sudo apt-get install util-linux
```

getopt is in the necessary util-linux package. You may have uninstalled it if you installed the redundant linux32 package. util-linux includes linux32 so there is not reason to install the linux32 package.

---

### Post by xithilinx on 2008-02-09
I think you've fixed my problem, Thanks Cappy! 

Here were the results

Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.22-14-generic
Not updating initrd symbolic links since we are being updated/reinstalled 
(2.6.22-14.47 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(2.6.22-14.47 was configured last, according to dpkg)
Running postinst hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.22-14-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms

---

