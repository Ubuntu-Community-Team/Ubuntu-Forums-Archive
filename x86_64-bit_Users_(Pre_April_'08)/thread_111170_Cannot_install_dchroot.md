---
title: "Cannot install dchroot"
date: 2006-01-01
forum: x86 64-bit Users (Pre April '08)
---

### Post by adana on 2006-01-01
I am trying to create a 32 bit chroot on my amd64 bit breezy.

But I get the following when trying to install dchroot:

 sudo apt-get install dchroot
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package dchroot


Any ideas?

Thanks!

---

### Post by John Jason Jordan on 2006-01-01
[QUOTE=adana]I am trying to create a 32 bit chroot on my amd64 bit breezy.

But I get the following when trying to install dchroot:

 sudo apt-get install dchroot
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package dchroot[/QUOTE]
Just this afternoon I tried the same thing. I followed the instructions at:
[http://doc.ubuntu-fr.org/installation/chroot32bits](http://doc.ubuntu-fr.org/installation/chroot32bits)
Apparently I got chroot installed, although I cannot be sure. The first thing I did was try to install Acrobat Reader 7.0 via Syanptic32. I managed to get Synaptic32 running and found Acrobat Reader 7.0. I even seem to have installed it. But I can't figure out for the life of me how to launch Acrobat Reader. Something about links, I think. But I'm too new at Linux to figure out what to do. In the meantime, there is a shell script and an executable. Double clicking on them does nothing.

But anyway, maybe the instructions at that French site will help you.

---

### Post by adana on 2006-01-01
Researching further, I think our problem is in the sources.list file from which ubuntu finds the location of packages.

By default it seems to look only at officially supported packages. I am concerned about opening up this restriction, so it would be nice if someone could advise us  where to safely get dchroot and other packages beyond the default ubuntu install, such as mplayer.

---

### Post by Suger on 2006-01-02
Enable universe and multiverse repositories in Synaptic

---

