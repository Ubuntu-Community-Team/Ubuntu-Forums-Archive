---
title: "Wine not working..."
date: 2014-11-11
forum: Wine
---

### Post by ENunn on 2014-11-11
Hello. I'm trying to install Wine on Ubuntu 14.04.1 32-bit. Here is what I'm seeing.

```
ubuntu@ubuntu:~$ sudo apt-get install wine1.6-i386
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'wine1.7-i386' instead of 'wine1.6-i386'
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 wine1.7-i386 : Depends: libmpg123-0 (>= 1.13.7) but it is not installable
                Depends: libopenal1 (>= 1:1.13) but it is not installable
                Depends: libopencl-1.1-1 but it is not installable
                Recommends: libcapi20-3 but it is not installable
                Recommends: libgif4 but it is not going to be installed
                Recommends: libosmesa6 but it is not going to be installed
                Recommends: unixodbc but it is not going to be installed
                Recommends: wine-gecko2.24 but it is not going to be installed
                Recommends: wine-mono4.5.2 but it is not going to be installed
E: Unable to correct problems, you have held broken packages.


```

Can someone please help me? :(

---

### Post by ian-weisser on 2014-11-11
Is there a reason you are specifying the 'wine1.6-i386' package? (instead of simply 'wine')

Are you following some instructions? If so, a link would be helpful.

---

### Post by Yulra on 2014-11-11
I'm just wondering if you've purged wine1.7...

---

### Post by QIII on 2014-11-12
*Moved to **Wine.***

---

