---
title: "Cannot get alsa to work"
date: 2005-08-09
forum: x86 64-bit Users (Pre April '08)
---

### Post by Steve1961 on 2005-08-09
Please help.  I've just upgraded my ubuntu distro to the 64 bit version and can't get alsa to work - and xmms won't work with anything else.  I tried Gandalf's How to but when I try to apt-get the alsa package - sudo apt-get install libesd-alsa0 - I get a message saying it doesn't exist in the repository.  This fix worked fine in the 32 bit version of ubuntu, so I think I'm missing a repository.  The output from the repository file is below.  Am I missing something?

deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release amd64 (20050407)]/ hoary main restricted


deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) hoary main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary universe main restricted multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) hoary universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

---

### Post by DancingSun on 2005-08-09
Hehe, add the repository in [this thread](http://ubuntuforums.org/showthread.php?t=48905&page=1), and then try that how-to again.

Ubuntu64 is still missing a lot of the packages from the backports repository, which is why that how-to doesn't work when you tried it.

Actually, it doesn't look like you have the backports repository in your sources.list at all.  The backports project has just become official and they are starting to provide packages for AMD64, so be sure to add this:
```
deb http://archive.ubuntu.com/ubuntu hoary-backports main universe multiverse restricted
```

---

### Post by Steve1961 on 2005-08-10
Thanks for this, I'll give it a try and let you know.  Is there anything else missing from my repository list.  It looks smaller than the one in the 32 bit version but I can't remember the details?

---

### Post by Steve1961 on 2005-08-14
OK this worked.  Thatnks for this

---

