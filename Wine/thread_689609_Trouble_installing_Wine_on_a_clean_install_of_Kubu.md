---
title: "Trouble installing Wine on a clean install of Kubuntu Gutsy"
date: 2008-02-06
forum: Wine
---

### Post by person_99 on 2008-02-06
I just installed Kubuntu clean off the disk, and installed my Nvidia drivers .
I also want wine.

I tried following the instructions above, but when I typed the "gksudo" command, it said: ```
The program 'gksudo' is currently not installed.  You can install it by typing:
sudo apt-get install gksu
bash: gksudo: command not found

```

The deb commands don't exist either.

I tried the sudo apt-get install gksu, but I then got ```
 Reading package lists... Done
Building dependency tree
Reading state information... Done
Package gksu is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  libgksuui1.0-1 libgksu2-0
E: Package gksu has no installation candidate

```

Can anyone help me with this?

---

### Post by gsmanners on 2008-02-06
I'm pretty sure KDE uses kdesu rather than gksudo.

---

