---
title: "Lib64ncurses5"
date: 2008-10-24
forum: x86 64-bit Users
---

### Post by Zerocool3001 on 2008-10-24
I'm running a program (Neuron) that requires the 64-bit version of the ncurses library. I've found a [listing for it]("http://packages.ubuntu.com/hardy/lib64ncurses5") on the repository website, but a search of aptitude and synaptic reveals nothing. Is there some reason this isn't listed in the universe repository?


P.S. I have the restricted repository enabled.

---

### Post by Yellow Pasque on 2008-10-25
If you're running Ubuntu64, the 64-bit ncurses library package is simply called libncurses5. "lib64ncurses" is only for 32-bit users who are building software for 64-bit targets.

If you're building Neuron from source, install the development package:
```
sudo apt-get install libncurses5-dev
```

---

### Post by Zerocool3001 on 2008-10-25
I thought that might be the case. Actually I'm not building Neuron from source, just using an "alienated" rpm. I've also tried creating a sym link to libncurses from lib64ncurses, but that doesn't seem to help.

---

