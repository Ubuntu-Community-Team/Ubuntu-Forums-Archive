---
title: "LInux Update Help Needed."
date: 2007-12-21
forum: x86 64-bit Users (Pre April '08)
---

### Post by Ron Byers on 2007-12-21
I am having a problem with a routine update. How do I find out what  the following error means and how to fix it. 

/var/cache/apt/archives/linux-image-2.6.22-14-generic_2.6.22-14.47_amd64.deb: files list file for package `libnss3-0d' is missing final newline

---

### Post by Cappy on 2007-12-22
Googling for "files list file for package is missing final newline" brings up:
[http://ubuntuforums.org/showthread.php?t=12737](http://ubuntuforums.org/showthread.php?t=12737)

Another page recommended that you delete the file in /var/lib/dpkg/info/
That would be
```
sudo rm /var/lib/dpkg/info/linux-image-2.6.22-14*list
```
and then remove the package and install it back.

---

### Post by Ron Byers on 2007-12-22
Thanks Cappy, :KS

 It was a little more complicated than your first suggestion (which I had tried before coming here) but your recommended thread contained a fix that involved replacing a different file.  Your information was very helpful.  A file had become corrupt in a hard crash.

---

