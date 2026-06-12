---
title: "Wine"
date: 2005-09-11
forum: x86 64-bit Users (Pre April '08)
---

### Post by nEXzEr on 2005-09-11
Wine won't install I've tried the "sudo apt-get install wine" but it keeps saying that the package doesn't exist (I've used the guide from winehq.com but that doesn't work either)

---

### Post by dave9191 on 2005-09-11
Have you added extra repositories as outlined in the ubuntuguide.org? If not, then you don't have the repository that has the wine package.

Dave

---

### Post by nEXzEr on 2005-09-11
Yes I have those aswell.

---

### Post by dave9191 on 2005-09-11
Well this is my repository list 

```
deb http://gb.archive.ubuntu.com/ubuntu hoary main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu hoary main restricted
deb http://gb.archive.ubuntu.com/ubuntu hoary-updates main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu hoary-updates main restricted
deb http://gb.archive.ubuntu.com/ubuntu hoary universe
deb-src http://gb.archive.ubuntu.com/ubuntu hoary universe
deb http://security.ubuntu.com/ubuntu hoary-security main restricted
deb-src http://security.ubuntu.com/ubuntu hoary-security main restricted
deb http://security.ubuntu.com/ubuntu hoary-security universe
deb-src http://security.ubuntu.com/ubuntu hoary-security universe
deb http://backports.ubuntuforums.org/backports hoary-extras main universe multiv
erse restricted
deb http://archive.ubuntu.com/ubuntu/ hoary universe
deb http://archive.ubuntu.com/ubuntu/ hoary multiverse
deb http://security.ubuntu.com/ubuntu/ hoary-security multiverse
```

And wine is a package in one of these. So sudo apt-get install wine works. After adding repositories to the list, always do a apt-get update. 

dave

---

### Post by negatory on 2005-09-12
Wine isn't available for the amd64 platform and IIRC it can't be built on it.
It works great trough a 32bit chroot!I use it all the time.
Hope that helps.
Pedro Carrico

---

