---
title: "[Solved] installing wine on 12.04 (amd64)"
date: 2013-02-21
forum: Wine
---

### Post by phorminx on 2013-02-21
Today I installed ubuntu 12.04 on my new computer (amd64). Right now, I have really the default installation, nothing added, nothing removed, it's all the way it comes by default.

Yet when I try to install wine, the software center says that it needs to remove pretty much all the installation of the X window system (the packages xserver-...), plus a few libraries.

What is wrong here?? (I have been a happy user of wine for many years with ubuntu 8.04 and 10.04.)

---

### Post by mc4man on 2013-02-21
Have a read here, install the package I mention & then you'll be good to go
[http://ubuntuforums.org/showpost.php?p=12518320&postcount=1](http://ubuntuforums.org/showpost.php?p=12518320&postcount=1)

---

### Post by phorminx on 2013-02-22
Thanks, I'll try that. So I was not making a silly mistake but things ARE seriously broken.

---

### Post by phorminx on 2013-03-04
I just want to confirm that installing libgl1-mesa-glx-lts-quantal:i386 did solve all my problems with wine: afterwards I could install wine without problems, and it is running fine, too. - Thanks for your help.

---

