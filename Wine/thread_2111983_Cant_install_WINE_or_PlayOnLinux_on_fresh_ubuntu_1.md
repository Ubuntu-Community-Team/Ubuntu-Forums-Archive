---
title: "Cant install WINE or PlayOnLinux on fresh ubuntu 12.10 instalation !"
date: 2013-02-03
forum: Wine
---

### Post by Imo97 on 2013-02-03
Hi, i know there are many threads like that, but anything didnt worked for me, and i have a fresh instalation of 12.10 ubuntu. I tried install it from software center, this is what message i get (WINE) :

```
Package dependencies cannot be resolved. 
Details: 
The following packages have unmet dependencies:

wine1.4: PreDepends: dpkg (>= 1.15.7.2~) but 1.16.7ubuntu6 is to be installed
         Depends: libc6 (>= 2.14) but 2.15-0ubuntu20 is to be installed
         Depends: wine1.4-amd64 (= 1.4.1-0ubuntu1) but 1.4.1-0ubuntu1 is to be installed
         Depends: wine1.4-i386 (= 1.4.1-0ubuntu1) but it is not going to be installed

```and if i tried PlayOnLinux:
```
The following packages have unmet dependencies:

playonlinux: 
```So guys, can you help me ? :confused:

---

### Post by howefield on 2013-02-03
Thread moved to the "*Wine*" forum.

---

### Post by Karlchen on 2013-02-03
Hello, Imo97.

Personally, I always use Synaptic in order to install software. On Ubuntu 12.10 installing Wine1.4 with the help of Synaptic was as trivial as
+ marking "Wine1.4" for installation
+ accepting all the found and suggested dependent software packages as well
+ pressing the [Apply] button and
+ showing a little patience.

As Ubuntu does not bring along Synaptic by default, Synaptic can be installed this way inside a terminal window: ```
sudo apt-get update
sudo apt-get install synaptic
```In case you do not feel like switching from the Software Centre to Synaptic just in order to install Wine1.4, you might install Wine1.4 inside a terminal window by executing these commands: ```
sudo apt-get update
sudo apt-get --install-suggests install wine1.4
```HTH,
Karl
--
P.S.:
Wine 1.4 runs fine on my Ubuntu12.10 x86 by the way.

---

