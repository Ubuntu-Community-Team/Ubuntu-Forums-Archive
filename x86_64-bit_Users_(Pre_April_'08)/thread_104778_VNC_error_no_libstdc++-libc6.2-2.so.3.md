---
title: "VNC error: no libstdc++-libc6.2-2.so.3"
date: 2005-12-16
forum: x86 64-bit Users (Pre April '08)
---

### Post by Jakykong on 2005-12-16
Hi!
well i'm new-ish ... the absolute beginner's forum i guess is more for questions before you ever get familiar with the system... which didn't take me long :-D but i'm still a beginner so bear with me (thanks).

I'm trying to get VNC up and running. unpacked the binaries and ran vncinstall /usr/bin to copy the files ... however, when i run vncconfig it gives me this error:
```
vncconfig: error while loading shared libraries: libstdc++-libc6.2-2.so.3: cannot open shared object file: No such file or directory

```

I tried app-get install libstdc++... but that didn't work ... couldn't find the package.
Obviousely a library is missing that vnc requires to run.
So, anyone able to tell me where to get that library and how to install it?
THANKS!

---

### Post by dcast on 2005-12-16
IF those libraries are missing you can probably get them here:

[http://packages.debian.org/stable/](http://packages.debian.org/stable/)

---

### Post by PMO6022 on 2005-12-16
apt-file will tell you what package a particular file is in.  See [http://www.debian.org/doc/manuals/apt-howto/ch-search.en.html#s-apt-file]("http://www.debian.org/doc/manuals/apt-howto/ch-search.en.html#s-apt-file")
```
pmorris@ubuntu:~ $ apt-file search libstdc++-libc6.2-2.so.3
libstdc++2.10-dbg: usr/lib/debug/libstdc++-libc6.2-2.so.3
libstdc++2.10-glibc2.2: usr/lib/libstdc++-libc6.2-2.so.3
``` 
Try installing libstdc++2.10-glibc2.2

---

### Post by Jakykong on 2005-12-17
[QUOTE=PMO6022]apt-file will tell you what package a particular file is in.  See [http://www.debian.org/doc/manuals/apt-howto/ch-search.en.html#s-apt-file]("http://www.debian.org/doc/manuals/apt-howto/ch-search.en.html#s-apt-file")
```
pmorris@ubuntu:~ $ apt-file search libstdc++-libc6.2-2.so.3
libstdc++2.10-dbg: usr/lib/debug/libstdc++-libc6.2-2.so.3
libstdc++2.10-glibc2.2: usr/lib/libstdc++-libc6.2-2.so.3
``` 
Try installing libstdc++2.10-glibc2.2[/QUOTE]

apt-file doesen't exist on my system (gonna check Adept next see if i missed something ...)

libstdc++2.10-glibc2.2 wasn't found from any of my sources ...

so... what do i do now?

---

### Post by PMO6022 on 2005-12-17
It's in universe.  Also, you have to install apt-file yourself.  See the link in my previous post.

---

### Post by Jakykong on 2005-12-17
[QUOTE=PMO6022]It's in universe.  Also, you have to install apt-file yourself.  See the link in my previous post.[/QUOTE]

apt-get doesen't seem to know universe either...
(and i read your link ... it didn't say anything about getting apt-file ... so now i'm totally confused :-))

i don't want to sound like a total idiot, but really, all i've ever used of linux before was a little bit of knoppix ... i'm dropping windows almost completely (only usin' it for a few games and to load stuff to and from my pocketPC)
Thanks for your help so far!

---

### Post by PMO6022 on 2005-12-18
Ok.  Check out this link: [http://www.psychocats.net/linux/sources.php]("http://www.psychocats.net/linux/sources.php") for how to enable the additional repositories.  Once you have done that, a simple```
sudo apt-get install libstdc++2.10-glibc2.2
``` will install it and any dependancies.

You don't really need apt-file, it is just a nice tool for discovering to which package a particular file belongs.  If you want it, it is in the universe repository.  If you do install it, you need to periodically run```
sudo apt-file update
```to keep it up to date with changes in the repos.

Good luck!

---

### Post by BobSongs on 2006-01-24
For me it was indeed the installation of libstdc++2.10-glibc2.2. That's what helped me get dynu working properly. Thanks.

---

### Post by Saubazi on 2006-07-09
I just had a same problem with amd64 but I am not able to solve it.
I can't find libstdc++2.10-glibc2.2

I have seached packages.ubuntu.com but I can't find the package other than for i386 but not for amd64?

---

### Post by mkw87 on 2006-07-23
> **Saubazi said:**
> I just had a same problem with amd64 but I am not able to solve it.
I can't find libstdc++2.10-glibc2.2

I have seached packages.ubuntu.com but I can't find the package other than for i386 but not for amd64?

Were you ever able to figure out how to get around this issue?  I am currently stuck with the same problem and cannot figure it out.  Thanks.

---

### Post by jim.guenzel on 2006-09-02
the code executed in terminal:
sudo apt-get install libstdc++2.10-glibc2.2 
worked for me. VNC 4.2.6 works now
Thank you!
Jim

---

### Post by 2lt.chronic on 2006-09-03
on amd64 I just --force-all the install on the i386 package (its still backward-compatible). nxclient/vnc worked.

---

### Post by goldaryn on 2006-09-21
[SIZE="3"]**PMO6022**:Thanks for the SUPER pointer about apt-file!![/SIZE]

If anyone is still having issues here, here's a step-by-step:

1) Update your sources.list: [UbuntuGuide:How_to_add_extra_repositories]("http://ubuntuguide.org/wiki/Dapper#How_to_add_extra_repositories")
[or here for edgy]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_add_extra_repositories)
2) sudo apt-get update

3) sudo apt-get install apt-file

4) sudo apt-file update

5) sudo apt-file search libstdc++-libc6.2-2.so.3

my results are 
libstdc++2.10-dbg: usr/lib/debug/libstdc++-libc6.2-2.so.3
libstdc++2.10-glibc2.2: usr/lib/libstdc++-libc6.2-2.so.3

Hence

6) sudo apt-get install libstdc++2.10-glibc2.2

---

### Post by mkgs on 2007-05-31
> **PMO6022 said:**
> apt-file will tell you what package a particular file is in.  See [http://www.debian.org/doc/manuals/apt-howto/ch-search.en.html#s-apt-file]("http://www.debian.org/doc/manuals/apt-howto/ch-search.en.html#s-apt-file")
```
pmorris@ubuntu:~ $ apt-file search libstdc++-libc6.2-2.so.3
libstdc++2.10-dbg: usr/lib/debug/libstdc++-libc6.2-2.so.3
libstdc++2.10-glibc2.2: usr/lib/libstdc++-libc6.2-2.so.3
``` 
Try installing libstdc++2.10-glibc2.2

I also had the same problem when running Eclipse TPTP New Agent Controller, your post helped me to solve this issue. Thanks a lot, also thanks for apt-file I did not know that.

---

### Post by gmatt on 2008-06-10
I have my universe repository enabled in source.list but I can't find the package 

libstdc++2.10-glibc2.2

here is my sources.list:

```
# deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/ hardy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://archive.ubuntu.com/ubuntu/ hardy main restricted multiverse
deb-src http://archive.ubuntu.com/ubuntu/ hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu/ hardy-updates main restricted multiverse
deb-src http://archive.ubuntu.com/ubuntu/ hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu/ hardy universe
deb-src http://archive.ubuntu.com/ubuntu/ hardy universe
deb http://archive.ubuntu.com/ubuntu/ hardy-updates universe
deb-src http://archive.ubuntu.com/ubuntu/ hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://ca.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
# deb-src http://ca.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu hardy partner
deb-src http://archive.canonical.com/ubuntu hardy partner

deb http://archive.ubuntu.com/ubuntu/ hardy-security main restricted multiverse
deb-src http://archive.ubuntu.com/ubuntu/ hardy-security main restricted
deb http://archive.ubuntu.com/ubuntu/ hardy-security universe
deb-src http://archive.ubuntu.com/ubuntu/ hardy-security universe
```

---

### Post by RROY on 2008-06-22
You can find libstdc++2.10-glibc2.2 here, I had the missing library problem trying to use RealVNC, this install fixes it:

[http://packages.ubuntu.com/dapper/i386/libstdc++2.10-glibc2.2/download](http://packages.ubuntu.com/dapper/i386/libstdc++2.10-glibc2.2/download)

---

