---
title: "does it have to be this hard?"
date: 2008-04-27
forum: x86 64-bit Users
---

### Post by Mgiacchetti on 2008-04-27
can someone give me a list of all the debs i need to install envyng-gtk (this would include all the depends for the whole lot)

64 bit 
ubuntu 8.04 (hardy)

---

### Post by starscalling on 2008-04-28
sudo apt-get install envyng-gtk
[sudo] password for neko:
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following extra packages will be installed:
  envyng-core gksu gnome-keyring libgksu2-0 libgtop2-7 libgtop2-common libvte-common
  libvte9 python-glade2 python-vte
Recommended packages:
  libpam-gnome-keyring python-gtk2-doc
The following NEW packages will be installed:
  envyng-core envyng-gtk gksu gnome-keyring libgksu2-0 libgtop2-7 libgtop2-common
  libvte-common libvte9 python-glade2 python-vte
0 upgraded, 11 newly installed, 0 to remove and 0 not upgraded.
Need to get 1442kB of archives.
After this operation, 10.1MB of additional disk space will be used.
Do you want to continue [Y/n]?


thats from kde... on a almost vanilla install...
if your trying to compile, try sudo apt-get build-dep <package>
also go to its homepage and look around, also inside there is often a README and an INSTALL which have good infoz

---

### Post by jocko on 2008-04-28
No, it does **not** have to be that hard. And it really **isn't**.
From your post I'm guessing you think you have to manually download all the debs?
Just open up synaptic (System --> Administration -->Synaptic Package Manager), search for the package you want to install and the dependencies will be taken care of automagically.
While in synaptic you may need to check under Settings --> Repositories that you have activated all the standard software sources (Main, Universe, Multiverse and restricted, otherwise you may not find all packages.

---

### Post by Mgiacchetti on 2008-04-28
> **jocko said:**
> No, it does **not** have to be that hard. And it really **isn't**.
From your post I'm guessing you think you have to manually download all the debs?
Just open up synaptic (System --> Administration -->Synaptic Package Manager), search for the package you want to install and the dependencies will be taken care of automagically.
While in synaptic you may need to check under Settings --> Repositories that you have activated all the standard software sources (Main, Universe, Multiverse and restricted, otherwise you may not find all packages.

all this from within windows?

---

### Post by pbpersson on 2008-04-28
> **Mgiacchetti said:**
> all this from within windows?

From within the version of Ubuntu you are using while in the GUI

---

### Post by jocko on 2008-04-28
> **Mgiacchetti said:**
> all this from within windows?

From windows? I'm not a psychic. As you didn't say so in the question, I had no idea you want to do it from windows. So is your internet connection just not working from ubuntu, or  do you actually not have any physical connection available?

You can [check here]("http://packages.ubuntu.com/hardy/envyng-gtk") what the dependencies are.

---

