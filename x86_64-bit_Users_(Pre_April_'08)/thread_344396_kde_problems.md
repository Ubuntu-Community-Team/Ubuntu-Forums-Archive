---
title: "kde problems"
date: 2007-01-22
forum: x86 64-bit Users (Pre April '08)
---

### Post by azlekayn on 2007-01-22
ok, i recently reinstalled ubuntu, 6.06LTS
it installs fine, have afew issues getting my nvidia drivers to work, but go them going in the end

now... i install KDE, only to relise i have no display manager, that section in periferals is just not there... Help? -_-;

---

### Post by Lil_Eagle on 2007-01-23
How did you install KDE?  Did you install the kubuntu-desktop from synaptic?  Did you perhaps download something and compile it?

The simplest way is to install kubuntu-desktop.  From a terminal session you can type:
```
sudo apt-get install kubuntu-desktop
```
That will install everything that normally comes with Kubuntu, including kdm which is the display manager, but even if you don't do it that way, you should still have gdm, which comes with ubuntu and can you can still use KDE.

---

