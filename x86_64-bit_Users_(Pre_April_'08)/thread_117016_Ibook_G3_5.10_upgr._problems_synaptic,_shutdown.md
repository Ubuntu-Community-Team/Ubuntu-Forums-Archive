---
title: "Ibook G3 5.10 upgr. problems: synaptic, shutdown"
date: 2006-01-14
forum: x86 64-bit Users (Pre April '08)
---

### Post by Focx on 2006-01-14
Hi,

I upgraded my Ibook G3 500mhz to the new 5.10 via CD, and it worked without any problems. Yet, after rebooting, Synaptic refuses to run (but update manager still runs). Also, when I try to shut down or reboot, the system goes down until "shutting down", then stops and when I press enter I have the console login (nice, but unwanted ;D)... any ideas?

---

### Post by ssam on 2006-01-14
if you run
```
gnome-sudo synaptic
```
in a terminal is there an error message?

---

### Post by Focx on 2006-01-15
I tried that: it reports nothing, even in the terminal, it just stops. when started with sudo instead of gnome-sudo it reports a segmentation fault (...). Furthermore, when trying to update the sources list via update manager, it reporst it can't get a full lock because some application is running already that blocks it (yet, neither synaptic or apt is running or visible via ps). This is getting kind of wierd :D

---

### Post by ssam on 2006-01-16
apt uses a locking system to stop you trying to run it several times at once (which could mess up its database). maybe it has been left locked.

can you try running
```
sudo mv /var/lib/apt/lists/lock /var/lib/apt/lists/lock.old
```
to remove the lock file

---

### Post by Focx on 2006-01-17
Did that, there indeed was a lock file, but it still gave me the message. And when trying to ignore that, the update process refuses to start (I guess it can't load synaptic again).

I also tried to remove the lock files for aptitude and dpkg, no effect. I wonder how the update broke my synaptic?

---

### Post by Focx on 2006-01-17
Ok, I finished downloading and installing new updates apt-get found after the upgrade, and used apt-get dist-upgrade for it as it demanded. after rebooting (new kernel version), synaptic is running again. yay! (but still: ??) maybe synaptic needed one of the upgraded packages... the shutdown also works now.

---

