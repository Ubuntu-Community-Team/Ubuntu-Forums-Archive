---
title: "Repo broken ?"
date: 2008-04-10
forum: x86 64-bit Users (Pre April '08)
---

### Post by akwatve on 2008-04-10
Hello,

I was trying to install some packages (gcc-multilib to be specific) when i faced this problem.

gcc-multilib requires libc6-i386

But when I tried to install it I got :

```
(Thu Apr 10 00:13:16)~> sudo apt-get install libc6-i386
/* The usual messages */

The following packages have unmet dependencies:
  libc6-i386: Depends: libc6 (= 2.6.1-1ubuntu9) but 2.6.1-1ubuntu10 is to be installed
E: Broken packages
```

So I tried

```
(Thu Apr 10 00:13:29)~> sudo apt-get install libc6
Reading package lists... Done
Building dependency tree
Reading state information... Done
libc6 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
(Thu Apr 10 00:16:53)~>              

```

I am confused now. It seems apt is trying to install different versions of two softwares...

EDIT:
I tried changing the repo (assuming that the one i was using was culprit) but no use :(

---

### Post by warp99 on 2008-04-10
You have the gutsy- updates version of libc6 and trying to install the gusty-main version of libc6-i386:

```
:~$ apt-cache policy libc6
libc6:
  Installed: 2.6.1-1ubuntu10
  Candidate: 2.6.1-1ubuntu10
  Version table:
 *** 2.6.1-1ubuntu10 0
        500 http://us.archive.ubuntu.com gutsy-updates/main Packages
        100 /var/lib/dpkg/status
     2.6.1-1ubuntu9 0
        500 http://us.archive.ubuntu.com gutsy/main Packages

```
```
apt-cache policy libc6-i386
libc6-i386:
  Installed: 2.6.1-1ubuntu10
  Candidate: 2.6.1-1ubuntu10
  Version table:
 *** 2.6.1-1ubuntu10 0
        500 http://us.archive.ubuntu.com gutsy-updates/main Packages
        100 /var/lib/dpkg/status
     2.6.1-1ubuntu9 0
        500 http://us.archive.ubuntu.com gutsy/main Packages

```

So make sure you have the gutsy-updates repositories turned on. You should have a string in your sources file like this:

```
deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted

```

---

### Post by akwatve on 2008-04-10
Ahhhhhhhh
I was really scared about my installation. Now I get it...

Thanks  a lot

---

