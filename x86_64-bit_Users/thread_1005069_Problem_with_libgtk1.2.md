---
title: "Problem with libgtk1.2"
date: 2008-12-07
forum: x86 64-bit Users
---

### Post by TriggerIsHappy on 2008-12-07
```
I have downloaded this game N and haven't been able to play it. I keep getting this error about the libgtk.

eric@eric-laptop:~/Desktop/n_v1linux$ ./n_v14
./n_v14: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory

I've done some research and found somethings I thought I should try.

[CODE]eric@eric-laptop:~/Desktop/n_v1linux$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release amd64 (20080702.1)]/ hardy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ intrepid main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ intrepid-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ intrepid universe
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid universe
deb http://us.archive.ubuntu.com/ubuntu/ intrepid-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ intrepid multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid multiverse
deb http://us.archive.ubuntu.com/ubuntu/ intrepid-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu hardy partner
# deb-src http://archive.canonical.com/ubuntu hardy partner

# Line commented out by installer because it failed to verify:
# deb http://security.ubuntu.com/ubuntu hardy-security main restricted
# Line commented out by installer because it failed to verify:
# deb-src http://security.ubuntu.com/ubuntu hardy-security main restricted
# Line commented out by installer because it failed to verify:
# deb http://security.ubuntu.com/ubuntu hardy-security universe
# Line commented out by installer because it failed to verify:
# deb-src http://security.ubuntu.com/ubuntu hardy-security universe
# Line commented out by installer because it failed to verify:
# deb http://security.ubuntu.com/ubuntu hardy-security multiverse
# Line commented out by installer because it failed to verify:
deb http://security.ubuntu.com/ubuntu/ intrepid-security restricted main multiverse universe
deb http://us.archive.ubuntu.com/ubuntu/ intrepid-proposed restricted main multiverse universe
deb http://us.archive.ubuntu.com/ubuntu/ intrepid-backports restricted main multiverse universe
# deb-src http://security.ubuntu.com/ubuntu hardy-security multiverse
eric@eric-laptop:~/Desktop/n_v1linux$ uname -m
x86_64

```

[/CODE]

---

### Post by TriggerIsHappy on 2008-12-07
Sorry I screwed that posting up.

I just wanted to add that the game is N and this is where I got it from.

[http://www.harveycartel.org/metanet/downloads.html](http://www.harveycartel.org/metanet/downloads.html)

---

### Post by DirtDawg on 2008-12-07
Try installing libgtk1.2
```
sudo apt-get install libgtk1.2
```

---

### Post by TriggerIsHappy on 2008-12-09
I apologize... I failed to mention that I have already installed the Libgtk1.2 and am still having the error.

---

### Post by Kilz on 2008-12-09
> **TriggerIsHappy said:**
> Sorry I screwed that posting up.

I just wanted to add that the game is N and this is where I got it from.

[http://www.harveycartel.org/metanet/downloads.html](http://www.harveycartel.org/metanet/downloads.html)

The game is 32bit, as such it is looking for a 32bit library. The one you installed is 64bit. 
Never, ever, ever force install libraries, use [Getlibs]("http://ubuntuforums.org/showthread.php?t=474790&highlight=getlibs") to install them

---

### Post by TriggerIsHappy on 2008-12-09
Did the Getlibs and got this 


```
eric@eric-laptop:~$ getlibs /home/eric/Desktop/n_v1linux/n_v14
libgmodule-1.2.so.0: libglib1.2
libglib-1.2.so.0: libglib1.2ldbl
No match for libstdc++-libc6.2-2.so.3
libgmodule-1.2.so.0: libglib1.2
libglib-1.2.so.0: libglib1.2ldbl
libgmodule-1.2.so.0: libglib1.2
libglib-1.2.so.0: libglib1.2ldbl
The following i386 packages will be installed:
libglib1.2
libglib1.2ldbl
Continue [Y/n]? y
libglib1.2 was not found in your repositories
Make sure you have all repositories enabled and updated
Downloading ...
Installing libraries ...
eric@eric-laptop:~$ Desktop/n_v1linux/n_v14
Desktop/n_v1linux/n_v14: error while loading shared libraries: libstdc++-libc6.2-2.so.3: cannot open shared object file: No such file or directory
eric@eric-laptop:~$ getlibs /home/eric/Desktop/n_v1linux/n_v14
[COLOR="Red"]No match for libstdc++-libc6.2-2.so.3[/COLOR]
No packages to install

```

---

