---
title: "Qemu: could not open hard disk image. Help!"
date: 2006-06-19
forum: x86 64-bit Users (Pre April '08)
---

### Post by Xilon on 2006-06-19
I was just following a few guides on how to setup Qemu with WinXP... at first I tried [http://maconstuff.blogspot.com/2006/06/how-to-run-windows-xp-under-ubuntu.html](http://maconstuff.blogspot.com/2006/06/how-to-run-windows-xp-under-ubuntu.html) found via digg.com, but it didn't work:
```
$ qemu -boot d -hda winxp.img -cdrom /dev/cdrom -m 256 -localtime
qemu: could not open hard disk image 'winxp.img'
```
So I googled the problem and came across a [howto for 64bit Gentoo]("http://forums.gentoo.org/viewtopic-t-402060-highlight-qemusystemx8664.html") (I'm running amd64) so I tried the command found there instead:
```
p$ qemu-system-x86_64 -localtime -hda /media/Shared/winxp/winxp.img  -cdrom /dev/cdrom -m 256 -boot d
qemu: could not open hard disk image '/media/Shared/winxp/winxp.img'
```
Anyone know how to get this to work? or why this error occurs?

I am running AMD64, the image is created on a FAT32 "shared" drive with this command:```
$ qemu-img create winxp.img 4300M
```

---

### Post by rbalfour on 2006-06-19
usr/local/bin/qemu -boot c -hda /home/mod/Systems/winxp.img -m 386 -localtime -net user -net nic -usb -usbdevice tablet -kernel-kqemu

here is the command I use.

---

### Post by RAOF on 2006-06-19
[QUOTE=Xilon]...
I am running AMD64, the image is created on a FAT32 "shared" drive with this command:```
$ qemu-img create winxp.img 4300M
```[/QUOTE]
I'm pretty sure that's your problem.  FAT32 is a **rubbish** filesystem, and doesn't support files bigger than 2GB (or 4GB, I forget).  Since that's bigger than 4GB, your image either won't be created, or won't be created properly.

Either make the image smaller, or use a modern filesystem.  If you want it to be readable in windows, use EXT3 - the ext2 windows driver from [fs-driver.org](fs-driver.org) will give you read/write access to it.

---

### Post by gklinux on 2007-12-09
Hello,
I had the same problem, but the cause was different.
I created an image using the base_image option (qemu-img create base_image)
after, I renamed the directory containing the image and its base_image. Since this time, the image don't work.
I changed the name of the directory to the initial name and it's working correctly now.
If you use base images, remember that they are referred by an absolute path.

---

