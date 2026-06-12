---
title: "installing drivers"
date: 2006-03-19
forum: x86 64-bit Users (Pre April '08)
---

### Post by who_cares on 2006-03-19
Okay, I need to install [this]("http://www.nvidia.com/object/linux_display_amd64_1.0-8178.html")this driver.
I'm logged in as root like it wants but when I try to run it it expects me to have "binutils" installed so it can use something called "ld"

I have downloaded binutils 2.16 from [here](http://www.gnu.org/software/binutils/) but I have no clue how to do this.

Any help would be wonderful

---

### Post by gborzi on 2006-03-19
Why don't you install the precompiled binutils ?
~$ sudo apt-get install binutils
BTW, there is a good howto for installing the latest nvidia drivers here
[http://www.ubuntuforums.org/showthread.php?t=75074&highlight=8178](http://www.ubuntuforums.org/showthread.php?t=75074&highlight=8178)

---

### Post by drl on 2006-03-19
Hi, who_cares.

I'm guessing that **ld** will be the least of your work here.  I'd guess that you're going to need **gcc** et al -- I noticed that the compiler and friends were not installed by default on my system.  That, in turn, means that you'll probably need to enable a few other repositories.

If you decide to continue, the **binutils** package is available from the repositories, once you get them enabled.  The *Ubuntu 5.10 Starter Guide* from Help is a good first start.

It might be useful for you to post the purpose of your need to install the driver, because someone may have an alternative suggestion, or more guidance.

It's possible that the run file from nvidia may do most of the work, but I am skeptical.  In any event, I wish you the best of luck.  I suggest you keep track of your activities in the event you need to ask for more help ... cheers, drl

( edit 1: typos )

---

### Post by who_cares on 2006-03-19
[QUOTE=gborzi]BTW, there is a good howto for installing the latest nvidia drivers here
[http://www.ubuntuforums.org/showthread.php?t=75074&highlight=8178](http://www.ubuntuforums.org/showthread.php?t=75074&highlight=8178)[/QUOTE]
okay, I'm tried method 1 and ran:
```
sudo apt-get install nvidia-glx nvidia-settings linux-restricted-modules-`uname -r`
```
it said the package nvidia-settings is not available

---

### Post by gborzi on 2006-03-20
nvidia-settings is in the restricted repository. You have to enable it (the repository), by editing your /etc/apt/sources.list or from Synaptic package manager:
Settings -> Repositories, select one binary repository whose distribution is breezy and eventually add restricted to the sections.

---

### Post by who_cares on 2006-03-20
I have sources.list open, what do I need to change?

---

### Post by gborzi on 2006-03-21
Please look at the ubuntu or kubuntu FAQ Guide here [http://help.ubuntu.com/](http://help.ubuntu.com/) to learn the basics of how to add repositories.

---

### Post by drl on 2006-03-21
Hi.

Unsubscribed from this thread ... cheers, drl

---

