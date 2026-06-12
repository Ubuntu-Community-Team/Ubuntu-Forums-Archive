---
title: "wine 12.04.1 x64"
date: 2012-09-30
forum: Wine
---

### Post by echo6 on 2012-09-30
When ever I execute wine I get the following;

```
bash: /usr/bin/wine: cannot execute binary file
```

```
LSB Version:	core-2.0-amd64:core-2.0-noarch:core-3.0-amd64:core-3.0-noarch:core-3.1-amd64:core-3.1-noarch:core-3.2-amd64:core-3.2-noarch:core-4.0-amd64:core-4.0-noarch:cxx-3.0-amd64:cxx-3.0-noarch:cxx-3.1-amd64:cxx-3.1-noarch:cxx-3.2-amd64:cxx-3.2-noarch:cxx-4.0-amd64:cxx-4.0-noarch:desktop-3.1-amd64:desktop-3.1-noarch:desktop-3.2-amd64:desktop-3.2-noarch:desktop-4.0-amd64:desktop-4.0-noarch:graphics-2.0-amd64:graphics-2.0-noarch:graphics-3.0-amd64:graphics-3.0-noarch:graphics-3.1-amd64:graphics-3.1-noarch:graphics-3.2-amd64:graphics-3.2-noarch:graphics-4.0-amd64:graphics-4.0-noarch:printing-3.2-amd64:printing-3.2-noarch:printing-4.0-amd64:printing-4.0-noarch:qt4-3.1-amd64:qt4-3.1-noarch
Distributor ID:	Ubuntu
Description:	Ubuntu 12.04.1 LTS
Release:	12.04
Codename:	precise
```

This is a fresh install from 12.04.1

I have a friend who has 12.04.1 but from upgrade and wine is working.

Installed also;
wine1.4-amd64 wine1.4 wine1.4-i386
ia32-libs 
ia32-libs-multiarch

Any ideas?

---

### Post by echo6 on 2012-09-30
I decided to try and build from source!

[http://wiki.winehq.org/WineOn64bit](http://wiki.winehq.org/WineOn64bit)

Hmmm

```
chroot: failed to run command `/bin/bash': Exec format error
```

---

### Post by akoskm on 2012-09-30
Describe what you want to achieve and how are you trying to run wine.
Have you tried to run 
```

winecfg

```
in the terminal?
No point in building wine from source except if you want run it with custom patches.
Use apt-get.

---

