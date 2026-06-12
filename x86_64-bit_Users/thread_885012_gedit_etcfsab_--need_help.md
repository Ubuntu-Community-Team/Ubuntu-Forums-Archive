---
title: "gedit etc/fsab --need help"
date: 2008-08-09
forum: x86 64-bit Users
---

### Post by gretarsson on 2008-08-09
Hi
my problem is I have 3hdd in my pc and one of them have M.vista but first I had mount problem with ntfs  and not now but my extra disk (250Gb) think he is 500Gb and he copy files from my 500Gb and he say size is 500Gb even he is only 250Gb (see photo) but I change 2 last line in fstab and I think that is my problem but I was trying to auto mount my disk when I boot up.
My hdd disk are:
250Gb sda = File system ubuntu
500Gb sdb1 = M.vista
250Gb sdc2 = extra (empty hdd)

---

### Post by ministoat on 2008-08-09
I had to fix my fstab lately - I posted about this here: [http://ubuntuforums.org/showthread.php?t=861258](http://ubuntuforums.org/showthread.php?t=861258)

although all the information that you need is actually in this thread:

[how to fstab](http://ubuntuforums.org/showthread.php?&t=283131)

---

### Post by Yellow Pasque on 2008-08-09
The problem is that you're mounting both of them to /media/disk. Mount one to a different directory.

---

