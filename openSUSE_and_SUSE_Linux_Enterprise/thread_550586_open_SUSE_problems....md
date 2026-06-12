---
title: "open SUSE problems..."
date: 2007-09-14
forum: openSUSE and SUSE Linux Enterprise
---

### Post by Dark Star on 2007-09-14
Hey All
Just shifted to open Suse :p way lighter than Ubuntu but the problem am facing ..
[LIST=1]
[*]Hard Drive partition are not mounted except the file system :p:mad: Also Opening File System Open System Moniter :(
[*]Cannot change resolution 1280 x 1024 after doing that my moniter goes out of frequency :o Not the case with any other distros :confused:
[*]How to install codec :shock:[/LIST]Regards rest later won't explore Suse much just for my sister daily work and to listen a bit music 

Regardss

Also how to install .rpm file simple method will be appreciated :guitar:

---

### Post by Dark Star on 2007-09-14
Can some1 help me :(

---

### Post by scxtt on 2007-09-14
1. you'll have to post **sudo fdisk -l** and the contents of **/etc/fstab** to get help w/ this.
2. most likely need to make sure the HorizSync and VertRefresh definitions in /etc/X11/xorg.conf are correct.
3. no idea, never used SuSE much, doesn't it use Yast (~= Synaptic)?

installing rpms can be as easy as: sudo rpm -Uvh <name of rpm>.rpm

---

### Post by Dark Star on 2007-09-14
Dude how can I post sudo fdisk -l it is saying 
```

shashwat@linux-ii7w:~> sudo fdisk -l
root's password:
sudo: fdisk: command not found
shashwat@linux-ii7w:~>

```

Am pretty disappoined with open Suse 10.2 :\

---

### Post by joeca0304 on 2007-09-14
Try this:

su - (then enter your password)
fdisk -l

---

### Post by dca on 2007-09-14
try /sbin/fdisk -l as root...

---

### Post by RedDwarf on 2007-09-14
- System->Partitioner YaST module is everything you need to set which partitions will be mounted and how will be mounted.
- Hardware->Graphics Card and Monitor is everything you need to configure your monitor HorizSync and VertRefresh.
- [http://opensuse-community.org/Restricted_Formats/10.2](http://opensuse-community.org/Restricted_Formats/10.2). And with 10.3 will be just a single click: [http://opensuse-community.org/Restricted_Formats/10.3](http://opensuse-community.org/Restricted_Formats/10.3)

---

### Post by joeca0304 on 2007-09-14
By the way if you are looking for suse help you may want to try:

[www.suseforums.net](www.suseforums.net)

There's a wealth of information available there.

---

