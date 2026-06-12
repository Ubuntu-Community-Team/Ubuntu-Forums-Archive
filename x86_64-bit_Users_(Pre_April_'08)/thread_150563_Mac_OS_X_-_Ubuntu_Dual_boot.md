---
title: "Mac OS X - Ubuntu Dual boot"
date: 2006-03-26
forum: x86 64-bit Users (Pre April '08)
---

### Post by mer45 on 2006-03-26
I was able to set up my new Mac Mini to dual boot to Ubuntu one the first partition and Mac OS X on the second.  I'd like to be able to see the files from one side to the other.  Help??

---

### Post by grazie on 2006-03-26
From Ubuntu, to mount the OSX partition```
# sudo mkdir /mnt/osx
# sudo mount -t hfsplus /dev/hd?? /mnt/osx
```Use ```
# sudo mac-fdisk -l
```to discover your OSX partition device (/dev/hd?? above). If you want to mount on boot, add an entry to /etc/fstab.

From OSX, assuming you've used the default Ext3 filesystem for Ubuntu, you need to add an Ext2 driver - details at [http://sourceforge.net/projects/ext2fsx/]("http://sourceforge.net/projects/ext2fsx/")

---

### Post by mer45 on 2006-03-26
Yikes!  Did I mention I'm a linux newbie?  I tried your instructions but got an error message after the second sudo command....

"sudo mount -t /dev/hda2 /mnt/osx"

"wrong fs type, bad option, bad superblock on /dev/hda2,
missing codepage or other error
In some cases useful info is found in syslog - try
dmesg | tail or so"

Yikes!

---

### Post by mer45 on 2006-03-26
Wait....forget that.  I got it.  Now I just need to figure out how to give myself permissions as root?  Thanks!

---

### Post by autocrosser on 2006-03-26
Take a look back thru my prior posts--I'll post a current copy of my /etc/fstab for you--

First--
you need to be root in a terminal  (code is   sudo)

Next--
sudo mkdir /mnt/osx

then-
sudo gedit /etc/fstab

use what your partition # is --for example /dev/hda5
& add it to your fstab--make sure you follow my example fstab

Reboot

I would then go into OSX & make a folder the has "no permissions"  use it to exchange between your two systems--the easiest is the "Shared" folder in your "User" area.

DO NOT MAKE YOUR WHOLE SYSTEM ACCESSABLE--you can garble OSX with ease;)

---

