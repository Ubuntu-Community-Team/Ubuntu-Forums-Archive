---
title: "Can't install Wine 1.7.4 from PPA"
date: 2013-10-19
forum: Wine
---

### Post by nu2linux6 on 2013-10-19
Hi,

Is anyone else having problems installing Wine 1.7.4 from the PPA? Every time I try to install on 64 bit Quantal I get the following error: 

The following packages have unmet dependencies.
 wine1.7 : Depends: wine1.7-amd64 (= 1.7.4-0ubuntu4) but it is not going to be installed
           Depends: wine1.7-i386 (= 1.7.4-0ubuntu4)
E: Unable to correct problems, you have held broken packages.

The wine1.7-i386 package it's complaining about is not shown in Synaptic. Any help would be much appreciated!

---

### Post by father_ted on 2013-11-02
Im having this problem as well. tried all the usual permutations of apt-get with no success.

The following packages have unmet dependencies.
 wine1.7 : Depends: wine1.7-amd64 (= 1.7.4-0ubuntu4~saucy1) but it is not going to be installed
           Depends: wine1.7-i386 (= 1.7.4-0ubuntu4~saucy1)
E: Unable to correct problems, you have held broken packages.

---

### Post by ian-weisser on 2013-11-02
You should notify the PPA maintainer.
PPAs are not community-supported software. They are *only* supported by the PPA maintainer.

---

### Post by father_ted on 2013-11-07
I spoke to the maintainer. The solution was the following for me

[COLOR=#000000][FONT=times new roman]sudo apt-get install wine1.7-i386[/FONT][/COLOR]
[COLOR=#000000][FONT=times new roman]followed by[/FONT][/COLOR]
[COLOR=#000000][FONT=times new roman][SIZE=2]sudo apt-get install wine1.7

i am now up and running. all is well.[/SIZE][/FONT][/COLOR]

---

### Post by braytac on 2013-11-11
> **father_ted said:**
> I spoke to the maintainer. The solution was the following for me

[COLOR=#000000][FONT=times new roman]sudo apt-get install wine1.7-i386[/FONT][/COLOR]
[COLOR=#000000][FONT=times new roman]followed by[/FONT][/COLOR]
[COLOR=#000000][FONT=times new roman][SIZE=2]sudo apt-get install wine1.7

i am now up and running. all is well.[/SIZE][/FONT][/COLOR]

That has not worked for me :/. 

> The following packages have unmet dependencies: wine1.7 : Depends: wine1.7-i386 (= 1.7.4-0ubuntu4~saucy1) but it is not installable
           Recommends: fonts-droid but it is not going to be installed
           Recommends: ttf-mscorefonts-installer but it is not installable
           Recommends: fonts-horai-umefont but it is not going to be installed
           Recommends: fonts-unfonts-core but it is not going to be installed
           Recommends: winbind but it is not going to be installed
E: Unable to correct problems, you have held broken packages.




Although the apt-get install wine1.7, I'm running in a chroot within uck. 
I gather that: 
"Depends: wine1.7-i386 (= 1.7.4-0ubuntu4 ~ saucy1) but it is not installable" 
, is due to the architecture. Then it occurred to me to add the i386 architecture with dpkg --add-architecture i386

dpkg --add-architecture i386 && apt-get update && apt-get install wine1.7

, and that works for me (~200mb 32 bits libs deps )

---

### Post by seanmckenna on 2014-04-12
I tried to run 
[COLOR=#000000][FONT=times new roman]sudo apt-get install wine1.7-i386
but got this message

[/FONT][/COLOR]ubuntu@ubuntu:~$ sudo apt-get install wine1.7-i386
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package wine1.7-i386 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source


E: Package 'wine1.7-i386' has no installation candidate
ubuntu@ubuntu:~$ 

help!

---

