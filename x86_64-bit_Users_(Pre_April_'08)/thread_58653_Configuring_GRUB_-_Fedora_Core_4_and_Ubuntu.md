---
title: "Configuring GRUB - Fedora Core 4 and Ubuntu"
date: 2005-08-21
forum: x86 64-bit Users (Pre April '08)
---

### Post by ExSpectator on 2005-08-21
I had a system with WinXP and Fedora Core 4 both installed on a SATA hdd.  The processor is an athlon64.  I just added an IDE hdd, and installed Ubuntu for the amd64 architecture on it.  Nothing else is on the drive.  I did not install the bootloader, since i wanted to keep using grub from FC4.  I added this to my menu.lst file in FC4:

title Ubuntu
	root (hd1,0)
	kernel /boot/vmlinuz root=/dev/hdd1 ro quiet splash
	initrd /boot/initrd.img
	savedefault
	boot


When I try to boot into Ubuntu, it decompresses the kernel but then says:

pivot_root: No such file or directory
/sbin/init: Cannot open dev/console: No such file
kernel Panic- not syncing: Attempted to kill init!

I have rather limited experience with Linux.  Am i doing something wrong in my GRUB configuration, or is something else wrong?  If you want to see the rest of my menu.lst file, i'll post it as well.

---

### Post by Corbelius on 2005-08-21
Google is a good friend [http://www.google.it/search?q=%2Fsbin%2Finit%3A%20Cannot%20open%20dev%2Fconsole%3A%20No%20such%20file&ie=UTF-8&oe=UTF-8](http://www.google.it/search?q=%2Fsbin%2Finit%3A%20Cannot%20open%20dev%2Fconsole%3A%20No%20such%20file&ie=UTF-8&oe=UTF-8)

---

