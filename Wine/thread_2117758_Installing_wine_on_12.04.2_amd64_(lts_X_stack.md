---
title: "Installing wine on 12.04.2 amd64 (lts X stack"
date: 2013-02-19
forum: Wine
---

### Post by mc4man on 2013-02-19
On new 12.04.2 **64 bit** installs with the **lts-quantal X stack** ATM wine will not be initially installable, apt will not install, synaptic will remove all of the lts X packages & generally bork your install if not fixed before a log out or restart.
The issue is an open bug so until fixed installing this **First** will allow wine to be installed
```
sudo apt-get install libgl1-mesa-glx-lts-quantal:i386 
```

tracked here
[https://bugs.launchpad.net/ubuntu/+source/apt/+bug/1130419](https://bugs.launchpad.net/ubuntu/+source/apt/+bug/1130419)

---

### Post by r00st3r3 on 2013-02-19
Wine works for me right out of the box from the software center.

:twisted:

---

### Post by mc4man on 2013-02-19
> **r00st3r3 said:**
> Wine works for me right out of the box from the software center.

:twisted:
And you can confirm you are on a new 12.04.2 amd64 install, (released yesterday),  with lts-quantal X packages installed?
As screen shows software center will remove the lts-quantal X packages (& do a poor job of replacing all the needed ones

---

