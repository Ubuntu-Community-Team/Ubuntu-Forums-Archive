---
title: "help: no acceptable cc found in $PATH"
date: 2006-09-15
forum: x86 64-bit Users (Pre April '08)
---

### Post by carteris21 on 2006-09-15
Hi,
i'm trying to install gcc compiler and got a message : error no acceptable cc found in $PATH; may some help?

---

### Post by TLE on 2006-09-15
> **carteris21 said:**
> Hi,
i'm trying to install gcc compiler and got a message : error no acceptable cc found in $PATH; may some help?

Install how?

---

### Post by carteris21 on 2006-09-15
from source, then i configure.

---

### Post by TLE on 2006-09-15
> **carteris21 said:**
> from source, then i configure.

Why would you want to install it from source, I'm pretty sure that would be in the reposotories, search in the repos by typing:
```
sudo apt-cache search gcc
```
then find the package name you want to use and install it with something like
```
sudo apt-get install gcc
```

---

### Post by Punk-Piranha on 2006-09-15
You can't install ggc from source unless some version of gcc is already installed, as if you don't you have no compiler to compile it with o.o
Do `sudo apt-get install build-essential` from the terminal, it's a metapackage than will install gcc and other stuff you need to compile source code.

---

