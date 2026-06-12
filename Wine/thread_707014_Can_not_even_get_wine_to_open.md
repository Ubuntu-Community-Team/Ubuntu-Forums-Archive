---
title: "Can not even get wine to open"
date: 2008-02-25
forum: Wine
---

### Post by incogn(egro)ito on 2008-02-25
I have installed and uninstalled wine twice, but I keep getting the same error.
```
wine: creating configuration directory '/root/.wine'...
Segmentation fault (core dumped)
wine: wineprefixcreate failed while creating '/root/.wine'.
root@barry-desktop:~# wineserver: could not save registry branch to /root/.wine-cb7Y6H/system.reg : No such file or directory
wineserver: could not save registry branch to /root/.wine-cb7Y6H/user.reg : No such file or directory

```
Am I missing something. I am running Ubuntu 7.10 and Vista 64 bit.

---

### Post by Whiffle on 2008-02-25
Try running it not as root aka, without sudo.

---

### Post by Rome.konig on 2008-02-25
did you install wine through the repos? if not,,  remove the wine you have installed now, and install wine through synaptic. its usually works flawlessly from then.

---

### Post by incogn(egro)ito on 2008-02-25
installed from the repos actually. I don't know why it won't work :/

---

### Post by FrozenFox on 2008-02-25
The .deb in the repos for hardy is broken and segfaults like that, the one in gutsy may too. Just use another .deb, like from winehq or see the multitude of other wine 0.9.56 threads around for a working one.

---

