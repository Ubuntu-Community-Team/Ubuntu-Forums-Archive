---
title: "Software installations"
date: 2008-03-27
forum: Za Team - South Africa
---

### Post by xooku on 2008-03-27
Hello
Was ubuntu designed with the idea of updating from the net?!
I am currently running a server (server 7.10 with kubuntu gui) in a R&D environment detached from our domain - and like to keep it that way.

I'd like to setup and testrun my server with windows designed applications and explore the ease of migrating alltogether from a windows domain to linux environment if possible. I read most of the manuals and it seems quite simple exept for the fact that I'd like to do installations from cdrom and usb thumb drives, which is not clearly covered.

Tried installation of "Wine" from a thumb drive and CD and got errors "dependency is not satisfiable" ?? or " unknown package" or "package not found" ??
Is it incomplete or am I just not doing this right ?? 
Also tried the terminal window with 
```
sudo dpkg -i wine.deb
```
no luck...

I have the new release in both .tar.bz2 and .deb file format, any suggestions of someone who actually managed to do this without installing from the net??

---

### Post by erginemr on 2008-03-27
Your problem is two-fold:

1. Specific to your problem: To install Wine to a standard Ubuntu (may or may not be sufficient for Kubuntu) installation, you will need to download and install: **binfmt-support** and **libaudio2** as well.
[http://packages.ubuntu.com/gutsy/binfmt-support](http://packages.ubuntu.com/gutsy/binfmt-support)
[http://packages.ubuntu.com/gutsy/libaudio2](http://packages.ubuntu.com/gutsy/libaudio2)

Then, you should put them under the same folder and install all three (together with wine) with:
```
sudo dpkg -i *.deb
```2. Generally speaking: To download and install any application with its dependencies, you will either need a install the Ubuntu DVD version by following:
[http://ubuntuforums.org/showpost.php?p=4531029&postcount=6](http://ubuntuforums.org/showpost.php?p=4531029&postcount=6)

Or use a spare machine that has access to the web to install Ubuntu (or a virtual Ubuntu machine with VirtualBox under Windows will do) and follow this technique:
[http://ubuntuforums.org/showpost.php?p=4531159&postcount=8](http://ubuntuforums.org/showpost.php?p=4531159&postcount=8)

P.S. You can find the latest Wine Debian package at:
[http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html)

---

### Post by xooku on 2008-03-28
Thanks 
I installed the dependencies needed for Wine, and it's running.

---

