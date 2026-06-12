---
title: "xmore causes a segmantation fault"
date: 2007-07-19
forum: x86 64-bit Users (Pre April '08)
---

### Post by fakie_flip on 2007-07-19
I don't understand why xmore is not working. I was having problems with it. I tried reinstalling it, and the same thing still happens. Can anyone help?

```
chris@ubuntu:~/.Trash$ sudo dpkg --force-depends -P xmore 
dpkg: xmore: dependency problems, but removing anyway as you request:
 xbase-clients depends on xmore.
(Reading database ... 149924 files and directories currently installed.)
Removing xmore ...
Purging configuration files for xmore ...
chris@ubuntu:~/.Trash$ sudo apt-get install xmore 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  democracyplayer-data
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  xmore
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 7050B of archives.
After unpacking 86.0kB of additional disk space will be used.
Get:1 http://us.archive.ubuntu.com feisty/main xmore 1:1.0.1-0ubuntu1 [7050B]
Fetched 7050B in 0s (9809B/s)
Selecting previously deselected package xmore.
(Reading database ... 149919 files and directories currently installed.)
Unpacking xmore (from .../xmore_1%3a1.0.1-0ubuntu1_amd64.deb) ...
Setting up xmore (1.0.1-0ubuntu1) ...
chris@ubuntu:~/.Trash$ xmore /etc/apt/sources.list
Segmentation fault
chris@ubuntu:~/.Trash$ 
```

---

### Post by Cappy on 2007-07-19
```

xmore /etc/apt/sources.list
Segmentation fault (core dumped)

```

I've never used it and it looks like I never will =P

The man page has this in it:
```

ENVIRONMENT
       XPSERVERLIST
              ${XPSERVERLIST}  must  be  set, identifying the available Xprint
              servers.  See Xprint(7) for more details.

```

---

