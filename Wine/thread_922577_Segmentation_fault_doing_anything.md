---
title: "Segmentation fault doing anything"
date: 2008-09-17
forum: Wine
---

### Post by djbon2112 on 2008-09-17
I've got the latest Wine (I think) installed on my minimal server. However, whenever I try to do anything (wine <app>, winecfg, even wine --help) I get a Segmentation fault and nothing else. Any ideas?

---

### Post by PotOAt on 2008-09-17
hi,

i had the same problem on an gentoo-machine some time ago. it was beacause of defective ram.

hope this helps you

---

### Post by djbon2112 on 2008-09-17
It's a brand new server (with ECC Registered DDR2 RAM), with the Ubuntu Server install virtualized using ProxMox. But just about everything else works fine.

---

### Post by djbon2112 on 2008-09-17
Just tried installing 3 different version (repos, 1.1.4, 1.1.1), and all of them segfault. Is there a way to get more info about what's happening here?

EDIT: Tried one more thing, changing the amount of RAM that ProxMox is allocation the VM... went from 1024 to 768, and no change, which seems to indicate a problem other than the RAM. Could the fact I'm using a minimal install (literally just installing xorg, gnome-core and gdm on top of Ubuntu Server) have something to do with it? Is there a hidden package somewhere I'm missing? Wine does the same thing under SSH without a GUI too.

---

### Post by djbon2112 on 2008-09-17
Alright, I've been doing some more testing.

On a new bare Server system, install Wine and it works fine (just the cli). However, as soon as I install xorg, gnome-core, and gdm, it segfaults. If I uninstall those three (and autoremove the remaining stuff), it works again.

Here's as much as I can see of the errors I get from my ProxMox VNC when those three are installed (this is the size it gives me without being able to change it, and nothing else [piped to less, SSH remote, etc.] shows this output; because of that I also can't just copy the code, I need to take a screenshot):

[[IMG]http://img519.imageshack.us/img519/7802/cscreenshotconsoleforkvws0.png[/IMG]](http://imageshack.us)

---

### Post by djbon2112 on 2008-09-22
Just an update: removing gnome-core fixes the issue... going to try for kde-core, and failing that, XFCE.

---

### Post by djbon2112 on 2008-09-22
xubuntu-desktop also causes the segfaults. Does anyone have any ideas?

---

### Post by aoanla on 2008-09-23
There was a problem like this several months back with one version of the nvidia drivers and something in X, I believe.

I'll have a look and see if I can find the bug in the bug-tracker.

---

### Post by djbon2112 on 2008-09-23
> **aoanla said:**
> There was a problem like this several months back with one version of the nvidia drivers and something in X, I believe.

I'll have a look and see if I can find the bug in the bug-tracker.

That's odd... I'm not using any nVidia drivers (the physical chipset is ATi, and it's emulated with ProxMox). Though of course any help that can be provided I'd greatly appreciate!

---

