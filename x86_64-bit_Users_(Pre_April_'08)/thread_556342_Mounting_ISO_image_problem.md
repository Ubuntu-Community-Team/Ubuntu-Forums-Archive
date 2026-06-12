---
title: "Mounting ISO image problem"
date: 2007-09-21
forum: x86 64-bit Users (Pre April '08)
---

### Post by Lonthong on 2007-09-21
On edubuntu (32bit), I have no problem but on 64 bit it just refused to mount

sudo modprobe loop
sudo mount -o loop /path to/iso /path to/mount point
instead of getting mounted, it returned with just ">"
the same command works perfectly on Edubuntu

Anyone knows howto do it in 64bit??

---

### Post by tszanon on 2007-09-21
Try specifying the filesystem type. If I recall correctly, you do it using the "-t" parameter.
sudo mount -t iso9660 -o loop <iso image> <mount point>

---

### Post by Lonthong on 2007-09-21
I tried that as well but result was the same.
Thanks anyway

---

### Post by dcstar on 2007-09-22
> **Lonthong said:**
> On edubuntu (32bit), I have no problem but on 64 bit it just refused to mount

sudo modprobe loop
sudo mount -o loop /path to/iso /path to/mount point
instead of getting mounted, it returned with just ">"
the same command works perfectly on Edubuntu

Anyone knows howto do it in 64bit??

A command that returns the ">" prompt usually means it has encountered a "\" character in the command string.

Try enclosing the path commands in quotes, or verify which particular shells you are using in both environments.

---

### Post by icechen1 on 2007-10-13
This tread may help
[http://www.techspot.com/vb/topic483.html](http://www.techspot.com/vb/topic483.html)

---

