---
title: "Installing 32bit applications (Opera) in 64bit Ubuntu 6.06"
date: 2006-12-08
forum: x86 64-bit Users (Pre April '08)
---

### Post by knight17 on 2006-12-08
I downloaded the [Ubuntu 6.06 version of Opera]("http://www.opera.com/download/index.dml?platform=linux").The file name is "opera_9.02-20060919.6-shared-qt_en_i386.deb"
When I clicked on the file to install it is showing me the following error :
 "Error Wrong architecture 'i386'"
Can someone help in how to do this please?:confused:

---

### Post by RockoTDF on 2006-12-08
> **knight17 said:**
> I downloaded the [Ubuntu 6.06 version of Opera]("http://www.opera.com/download/index.dml?platform=linux").The file name is "opera_9.02-20060919.6-shared-qt_en_i386.deb"
When I clicked on the file to install it is showing me the following error :
 "Error Wrong architecture 'i386'"
Can someone help in how to do this please?:confused:

At the top of this forum there is a sticky that has lots of good information about situations like this, including a specific command (which skips my mind) which forces installation of prorams of backward compatible architectures.

---

### Post by knight17 on 2006-12-09
Thanks, I will check it.

---

### Post by knight17 on 2006-12-09
Found a thread about [configuring Opera in AMD64]("http://ubuntuforums.org/showthread.php?t=75940")

---

### Post by chiisu on 2006-12-17
Cool, I was looking for this as well  :)

---

### Post by knight17 on 2006-12-18
But that topic is very old.I can't find a way to install Opera :(

---

### Post by BIGtrouble77 on 2006-12-18
```
sudo dpkg -i --force-architecture opera_9.02-20060919.6-shared-qt_en_i386.deb
```
BTW, you should download version 9.1 instead because flash9 no longer crashes.
[ftp://ftp.opera.com/pub/opera/linux/910/final/en/i386/static/opera-static_9.10-20061214.1-qt_en_i386.deb](ftp://ftp.opera.com/pub/opera/linux/910/final/en/i386/static/opera-static_9.10-20061214.1-qt_en_i386.deb)

---

