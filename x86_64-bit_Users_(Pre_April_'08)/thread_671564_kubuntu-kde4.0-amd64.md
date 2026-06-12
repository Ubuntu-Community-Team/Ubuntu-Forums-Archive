---
title: "kubuntu-kde4.0-amd64"
date: 2008-01-18
forum: x86 64-bit Users (Pre April '08)
---

### Post by aatiis on 2008-01-18
Hi,

Does anyone know when will the amd64 KDE4 remastered Kubuntu be released?

---

### Post by Yellow Pasque on 2008-01-19
Probably in April when Hardy Heron (Ubuntu 8.04) is released.

---

### Post by aatiis on 2008-01-19
What is taking so long? If packaging is the problem, I can help with building amd64 packages, if the source packages are ready (aren't they?)

---

### Post by Yellow Pasque on 2008-01-19
You can get an alpha version here:
[https://wiki.kubuntu.org/HardyHeron/Alpha2/Kubuntu](https://wiki.kubuntu.org/HardyHeron/Alpha2/Kubuntu)

---

### Post by Yellow Pasque on 2008-01-19
> What is taking so long? If packaging is the problem, I can help with building amd64 packages, if the source packages are ready (aren't they?)
KDE4 just came out recently and the next Ubuntu release is scheduled in April. Ubuntu does not use a "rolling release" model for development; if you want that, try Arch Linux or another rolling release distro.

---

### Post by cjazz on 2008-01-19
It's true that KDE4 will most likely have its official introduction to the Kubuntu universe in April with the Hardy release. However, according to a site at

[http://kubuntu.org/announcements/kde-4.0.php](http://kubuntu.org/announcements/kde-4.0.php)

you can add "deb [http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu](http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu) gutsy main" to your /etc/apt/sources.list, do "sudo apt-get update" and install kde4-core, which should install KDE 4 alongside the existing KDE 3.5 packages for a comfortable test drive. Be sure to read and apply the instructions yourself.

---

