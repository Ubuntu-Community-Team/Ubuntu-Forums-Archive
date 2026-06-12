---
title: "ia32-libs not downloading through apt-get/synaptic"
date: 2008-10-02
forum: x86 64-bit Users
---

### Post by mediahaze on 2008-10-02
Ok,

I am trying to setup my x64 heron 8.04 system to build android projects. 
The instructions to setup the build env calls for the ia32-libs but...

It will not install through the package managers and while I can download and install it manually, I would like to know why this is the case.

Here is the output of the install

```
gav@dell-desktop:~/Dev$ sudo apt-get install ia32-libs
[sudo] password for gav: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ia32-libs

```

Here is the package [http://packages.ubuntu.com/hardy/amd64/ia32-libs/download/](http://packages.ubuntu.com/hardy/amd64/ia32-libs/download/)

which can be found in repo

```
deb http://security.ubuntu.com/ubuntu hardy-security main universe
```

which is in my /etc/apt/sources.list ( extra comments removed )
```
gav@dell-desktop:~/Dev$ cat /etc/apt/sources.list
[COLOR="Silver"]deb http://archive.ubuntu.com/ubuntu/ hardy main restricted universe
deb-src http://archive.ubuntu.com/ubuntu/ hardy main restricted
deb http://archive.ubuntu.com/ubuntu/ hardy-updates main restricted universe
deb-src http://archive.ubuntu.com/ubuntu/ hardy-updates main restricted
deb http://archive.ubuntu.com/ubuntu/ hardy multiverse
deb-src http://archive.ubuntu.com/ubuntu/ hardy multiverse
deb http://archive.ubuntu.com/ubuntu/ hardy-updates multiverse
deb-src http://archive.ubuntu.com/ubuntu/ hardy-updates multiverse
deb http://archive.canonical.com/ubuntu hardy partner
deb-src http://archive.canonical.com/ubuntu hardy partner
deb http://ppa.launchpad.net/reacocard-awn/ubuntu/ gutsy main
deb-src http://ppa.launchpad.net/reacocard-awn/ubuntu/ gutsy main[/COLOR]
[COLOR="Red"]deb http://security.ubuntu.com/ubuntu/ hardy-security restricted main multiverse universe[/COLOR]

```

And ideas?

Thanks,

---

### Post by Yellow Pasque on 2008-10-02
That's odd. Are you sure you're running a 64-bit distro?
```
uname -a
```

---

### Post by mediahaze on 2008-10-02
Unless my disks got mixed up...I thought I grabed the x64 build.


```
Linux dell-desktop 2.6.24-19-generic #1 SMP Wed Aug 20 22:56:21 UTC 2008 i686 GNU/Linux
```

EDIT: However... given that my available memory is 3.46 Gig (Not 4) having the x86 build would not suprise me.
EDIT#2: Also the 32bit version of eclipse works on my system. /slapsforhead

Thanks :P

---

### Post by Yellow Pasque on 2008-10-02
Nope, you mixed up the disks. :lolflag:
> i686

---

### Post by peakshysteria on 2008-10-03
The Synaptic package manager should be a walk in the park.... :D What error do you get when trying Synaptic?

---

