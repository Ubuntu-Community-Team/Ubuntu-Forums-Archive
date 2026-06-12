---
title: "Installing my new compiled kernel 2.6.31-15"
date: 2009-11-05
forum: x86 64-bit Users
---

### Post by JustUser on 2009-11-05
Hi All,

I followed the following link to compile linux kernel to add ntrig driver.

[https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile)

Note: I got my kernel using git following the following link [URL="https://wiki.ubuntu.com/KernelTeam/KernelGitGuide"]
https://wiki.ubuntu.com/KernelTeam/KernelGitGuide[/URL]

Finally after too many hours of compiling :) I got the following packages:

linux-image-2.6.31-15-generic_2.6.31-15.49_amd64.deb
linux-image-2.6.31-15-virtual_2.6.31-15.49_amd64.deb
linux-libc-dev_2.6.31-15.49_amd64.deb
linux-headers-2.6.31-15-server_2.6.31-15.49_amd64.deb
linux-headers-2.6.31-15-generic_2.6.31-15.49_amd64.deb
linux-image-2.6.31-15-server_2.6.31-15.49_amd64.deb

I tried to install the first package BUT I got the following

> [SIZE=1]abdalla@abdalla-laptop:~$ sudo dpkg -i '/home/abdalla/linux-image-2.6.31-15-generic_2.6.31-15.49_amd64.deb' 
[sudo] password for abdalla: 
(Reading database ... 128164 files and directories currently installed.)
Preparing to replace linux-image-2.6.31-15-generic 2.6.31-15.49 (using .../linux-image-2.6.31-15-generic_2.6.31-15.49_amd64.deb) ...
Done.
Unpacking replacement linux-image-2.6.31-15-generic ...
Running postrm hook script /usr/sbin/update-grub.
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-15-generic
Found initrd image: /boot/initrd.img-2.6.31-15-generic
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows Vista (loader) on /dev/sda1
Found Windows Vista (loader) on /dev/sda2
done
Setting up linux-image-2.6.31-15-generic (2.6.31-15.49) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.31-15-generic
Not updating initrd symbolic links since we are being updated/reinstalled 
(2.6.31-15.49 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(2.6.31-15.49 was configured last, according to dpkg)
Running postinst hook script /usr/sbin/update-grub.
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-15-generic
Found initrd image: /boot/initrd.img-2.6.31-15-generic
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows Vista (loader) on /dev/sda1
Found Windows Vista (loader) on /dev/sda2
done
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms
 * Running DKMS auto installation service for kernel 2.6.31-15-generic          
 *  bcmwl (5.10.91.9+bdcom)...                                                  bcmwl (5.10.91.9+bdcom): Installing module.
  Kernel headers for 2.6.31-15-generic are not installed.  Cannot install this module.
  Try installing linux-headers-2.6.31-15-generic or equivalent.
                                                                         [B][COLOR=Red][fail]
[/COLOR][/B]  *  fglrx (8.660)...                                                            fglrx (8.660): Installing module.
  Kernel headers for 2.6.31-15-generic are not installed.  Cannot install this module.
  Try installing linux-headers-2.6.31-15-generic or equivalent.
                                                                         [COLOR=Red]**[fail]**[/COLOR]
run-parts: executing /etc/kernel/postinst.d/nvidia-common

abdalla@abdalla-laptop:~$ 
[/SIZE]when I try to install linux-header(linux-headers-2.6.31-15-generic_2.6.31-15.49_amd64.deb) I got
an error that [SIZE=1] linux-headers-2.6.31-15-generic not found[/SIZE]

Any advice

Thanks
Best Regards,
JustAUser

---

