---
title: "Wine in 7.10 is broken"
date: 2008-02-09
forum: Wine
---

### Post by krylon on 2008-02-09
I have a fresh install of Gutsy 7.10 amd64. First thing I wanted to install was Wine.

sudo apt-get install wine

Everything installed without error

After install I immediately  tried to run winecfg

```
krylon@krylon:~$ winecfg
wine: creating configuration directory '/home/krylon/.wine'...
Segmentation fault (core dumped)
wine: wineprefixcreate failed while creating '/home/krylon/.wine'.
krylon@krylon:~$ wineserver: could not save registry branch to /home/krylon/.wine-2r8NIz/system.reg : No such file or directory
wineserver: could not save registry branch to /home/krylon/.wine-2r8NIz/user.reg : No such file or directory

```

---

### Post by happyhamster on 2008-02-09
What do you get if you directly issue the command:

wineprefixcreate

- It should create the hidden .wine folder in your home dir. (Perhaps you first have to delete the .wine-2r8NIz folder first.)

---

