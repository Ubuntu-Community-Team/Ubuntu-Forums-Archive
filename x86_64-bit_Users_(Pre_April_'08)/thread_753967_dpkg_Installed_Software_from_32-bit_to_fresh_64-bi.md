---
title: "dpkg Installed Software from 32-bit to fresh 64-bit install?"
date: 2008-04-13
forum: x86 64-bit Users (Pre April '08)
---

### Post by Anthony M on 2008-04-13
I have been running 32-bit Ubuntu for about 6 months but now have an AMD X2 5200+ processor that is capable of running 64-bit. 

What I would like to know is, can I use

```
dpkg --get-selections > installed-software
```

Followed by

```
dpkg --set-selections < installed-software
```

to reinstall the packages I am currently running in 32-bit Hardy Heron? I have a separate Home partition, but would like to keep my software installs if possible.

---

### Post by Anthony M on 2008-04-14
Bump 8)

Does anybody know about this?

Thanks!

---

### Post by drs305 on 2008-04-14
I use the commands in 64-bit gutsy. 

The file generated and used is a simple text file with no special headers or identifiers at the top of the file.  Since all the command does is import package NAMES, if the names are the same it should install the same-named programs (albeit 64-bit) as long as they are in the 64-bit repositories. (Some names are bound to be different and you will probably have to check the error messages to see which ones didn't install.)

---

