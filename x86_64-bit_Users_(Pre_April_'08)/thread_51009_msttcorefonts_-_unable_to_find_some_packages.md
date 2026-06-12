---
title: "msttcorefonts - unable to find some packages"
date: 2005-07-22
forum: x86 64-bit Users (Pre April '08)
---

### Post by juhis on 2005-07-22
can somebody please help me. 

i'm totally new to ubuntu/linux. 
when trying to use apt-get install mssttcorefonts (and whole lot other apt-get-tips i read from the unofficial guide and elsewhere) program says it can't find packages, or some packages hint to the packages i'm looking for. synaptic can find some of these "missing packages" (not msttcorefonts). i have enabled multiverse and universe repositories. 

juhis

---

### Post by Tamir on 2005-07-22
[QUOTE=juhis]can somebody please help me. 

i'm totally new to ubuntu/linux. 
when trying to use apt-get install mssttcorefonts (and whole lot other apt-get-tips i read from the unofficial guide and elsewhere) program says it can't find packages, or some packages hint to the packages i'm looking for. synaptic can find some of these "missing packages" (not msttcorefonts). i have enabled multiverse and universe repositories. 

juhis[/QUOTE]
 what packages? name them please.

---

### Post by juhis on 2005-07-22
well, apt-get usually doesn't find any packages i'm trying. in addition to msttcorefonts, mplayer-amd64 is another, realplayer, some multimedia codecs like gstreamer0.8-lame
 w32codecs
libdivx4linux
lame
mjpegtools

the names of the packages are maybe changed?

---

### Post by negatory on 2005-07-22
Post your /etc/apt/sources.list please...maybe we can see what the problem is by looking there.
Thanks
Pedro Carrico

---

### Post by newbie2 on 2005-07-22
[QUOTE=juhis]well, apt-get usually doesn't find any packages i'm trying. in addition to msttcorefonts, mplayer-amd64 is another, realplayer, some multimedia codecs like gstreamer0.8-lame
 w32codecs
libdivx4linux
lame
mjpegtools

the names of the packages are maybe changed?[/QUOTE]
[http://www.columbia.edu/~jr2075/gstreamer-lame-how-to.html](http://www.columbia.edu/~jr2075/gstreamer-lame-how-to.html)
[http://amd64.ubuntuguide.org/](http://amd64.ubuntuguide.org/)
[http://ubuntuforums.org/archive/index.php/t-21219.html](http://ubuntuforums.org/archive/index.php/t-21219.html)
also use the search tool on this forum and google to find what u look for ;-)

---

### Post by juhis on 2005-07-27
[QUOTE=negatory]Post your /etc/apt/sources.list please...maybe we can see what the problem is by looking there.
Thanks
Pedro Carrico[/QUOTE]


my sources.list looks like this: 
deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release amd64 (20050407)]/ hoary main restricted


## Uncomment the following two lines to fetch updated software from the network
deb [http://fi.archive.ubuntu.com/ubuntu](http://fi.archive.ubuntu.com/ubuntu) hoary main restricted
deb-src [http://fi.archive.ubuntu.com/ubuntu](http://fi.archive.ubuntu.com/ubuntu) hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://fi.archive.ubuntu.com/ubuntu](http://fi.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://fi.archive.ubuntu.com/ubuntu](http://fi.archive.ubuntu.com/ubuntu) hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://fi.archive.ubuntu.com/ubuntu](http://fi.archive.ubuntu.com/ubuntu) hoary universe
deb-src [http://fi.archive.ubuntu.com/ubuntu](http://fi.archive.ubuntu.com/ubuntu) hoary universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

## Backports
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted




Problem might be in addresses containing fi.archive...etc?

Juhis

---

### Post by DancingSun on 2005-07-28
[QUOTE=juhis]Problem might be in addresses containing fi.archive...etc?Juhis[/QUOTE]
Could be, but since you're using Ubuntu AMD64, 32-bit packages should not be available for you.  For example, not having w32codecs is normal.

I also see that you don't have the following lines for multiverse:

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse

---

### Post by hod139 on 2005-07-28
Check out this thread
[http://ubuntuforums.org/showthread.php?t=48905](http://ubuntuforums.org/showthread.php?t=48905)

---

### Post by juhis on 2005-08-01
[QUOTE=DancingSun]Could be, but since you're using Ubuntu AMD64, 32-bit packages should not be available for you.  For example, not having w32codecs is normal.

I also see that you don't have the following lines for multiverse:

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse[/QUOTE]

yeah, added those to repository and now it works. thanks.

---

