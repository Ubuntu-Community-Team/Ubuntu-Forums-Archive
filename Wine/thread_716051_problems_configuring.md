---
title: "problems configuring"
date: 2008-03-05
forum: Wine
---

### Post by Caesum on 2008-03-05
I try and run and configure wine, a directory .wine has been created with some files and subdirectories, but no graphical option thing started up and the winecfg just does this:

```

caesum@Caesum:~$ winecfg
wine: creating configuration directory '/home/caesum/.wine'...
Segmentation fault (core dumped)
wine: wineprefixcreate failed while creating '/home/caesum/.wine'.
caesum@Caesum:~$ wineserver: could not save registry branch to /home/caesum/.wine-tMfKVv/system.reg : No such file or directory
wineserver: could not save registry branch to /home/caesum/.wine-tMfKVv/user.reg : No such file or directory

caesum@Caesum:~$ wineprefixcreate
Segmentation fault (core dumped)

```

Is this common ?

---

