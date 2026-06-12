---
title: "ia32-libs unment dependencies"
date: 2007-03-11
forum: x86 64-bit Users (Pre April '08)
---

### Post by winzo on 2007-03-11
Hi, just switched from FC6 to Ubuntu Edgy Eft AMD64. Having some trouble resolving dependencies for ia32-libs:

```
$ sudo apt-get install ia32-libs

...

The following packages have unmet dependencies:
[B]  ia32-libs: Depends: lib32stdc++6 but it is not going to be installed
             Depends: lib32gcc1 but it is not going to be installed
             Depends: lib32z1 but it is not going to be installed
             Depends: libc6-i386 but it is not going to be installed[/B]
E: Broken packages
```

The currently installed libc6 according to synaptic is 2.4-lubuntu12.3.  Specifically trying to install libc6-i386 as if it wasn't there, however, yeilds:

```
$ sudo apt-get install libc6-i386

...

The following packages have unmet dependencies:
  libc6-i386: Depends: libc6 (= 2.4-1ubuntu12) but 2.4-1ubuntu12.3 is to be installed
**E: Broken packages**

```

A good amount of Googling has turned up nothing, I haven't seemed to find anyone with a similar problem installing ia32-libs. And what is the Broken Packages error referring to?

---

### Post by kleeman on 2007-03-11
Do you have the edgy-updates repository enabled? It looks like libc6-i386 is the edgy version but libc6 is from edgy-updates

---

### Post by winzo on 2007-03-12
Thanks kleeman, that was it. Enabling 'Recommended updates' in Synaptic fixed it, I take it that is edgy-updates.

---

