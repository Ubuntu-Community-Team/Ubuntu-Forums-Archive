---
title: "where do steam games get innstalled in ubunt?????"
date: 2011-12-25
forum: Wine
---

### Post by piezoelectron on 2011-12-25
hey everyone, 

i have ubuntu 11.10 on my laptop. i just installed steam through wine only(without any support from playonlinux and the likes). what i wanted to ask is, where do the games get installed, i.e. do they get installed on the ubuntu partition or the windows C drive?
also, where does steam get installed on ubuntu, or does it get installed on windows as well?

---

### Post by Perfect Storm on 2011-12-25
Moved to wine forum.

---

### Post by DoktorSeven on 2011-12-25
Wine creates its own "C drive" by default in your home directory under a hidden directory called .wine called drive_c -- by default, Steam would be in [your home directory]/.wine/drive_c/Program\ Files/Steam

I always make it easier on myself by creating a symbolic link to drive_c in my home directory by opening a terminal and typing:

```
ln -s ~/.wine/drive_c ~/wine
```

This way, you can more easily get to your Wine C "drive".

---

