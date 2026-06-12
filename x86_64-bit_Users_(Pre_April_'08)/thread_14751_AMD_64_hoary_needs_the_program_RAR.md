---
title: "AMD 64 hoary needs the program RAR"
date: 2005-02-09
forum: x86 64-bit Users (Pre April '08)
---

### Post by luna6 on 2005-02-09
Anybody has the program RAR for hoary x86_64? If so please let me know which repository it is on. I installed unrar but it fails to extract rar files, always says extraction failed. From what I could read it seems the program RAR is also needed. This is really annoying because I frequently use this program and have to reboot in fedora core 3 to use the program...thanks..

---

### Post by Dylanby on 2005-02-09
Running Warty.

A quick search shows it should be in Hoary multiverse.

---

### Post by luna6 on 2005-02-09
hmm i dont see it in my synaptic....this is my sources.list.... am i missing a repository?

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse

---

### Post by luna6 on 2005-02-09
also when i run sudo apt-get install rar...i get this


sudo apt-get install rar
Reading Package Lists... Done
Building Dependency Tree... Done
Package rar is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package rar has no installation candidate

---

### Post by AndersAA on 2005-02-09
I dont have it either :/

---

### Post by minio on 2005-02-09
I think that rar is not in any ubuntu repository, only unrar-nonfree. But the unrar works for me OK on warty.

---

### Post by luna6 on 2005-02-10
thanks..did install the unrar non free version which works fine for me...whew no more rebooting in fc3 for me....by the way do you know exactly why it is non-free? meaning it will expire or something? thanks...

---

### Post by Dylanby on 2005-02-10
My mistake, I guess only the i386 package is in Hoary.
Sorry about that.

---

### Post by minio on 2005-02-10
[QUOTE=luna6]thanks..did install the unrar non free version which works fine for me...whew no more rebooting in fc3 for me....by the way do you know exactly why it is non-free? meaning it will expire or something? thanks...[/QUOTE]
It won't expire it's freeware, but you are not allowed to use it's source to create rar archiver. More at /usr/share/doc/unrar-nonfree/copyright  :wink:

---

### Post by TechZilla on 2006-06-22
unrar-nonfree will extract all types of rar archives, the free version wont extract version3 of the rar format ( so i have heard)

if you want to create rar archives you need to install the rar command line program for linux, get it from rarlabs.com  (it is in a tar.gz tarball.)

it is officially compiled for X86 but it works w/out issues for me (debian AMD64)

but honestly i now use .7z for most things now as it is GNU LGPL and can be naitivly compiled for amd64 the 7zip package is called p7zip

---

