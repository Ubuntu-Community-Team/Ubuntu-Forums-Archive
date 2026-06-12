---
title: "how to uninstall those package ?"
date: 2007-11-23
forum: x86 64-bit Users (Pre April '08)
---

### Post by xieu90 on 2007-11-23
hi everyone I don't know where I should have put this question, but my computer is running x64 for sure
so after I install a program with synaptic (normally with other package)
now I want to uninstall that program (also other packages with were also installed when I installed that program)
so how I can do that ?
I can uninstall that program, but those packages with it, they were too much I didn't have time to write down their name (I wouldn't like to do it and wouldn't do it)
so how can I uninstall those packages ?
thanks in advance

---

### Post by Stephen Howard on 2007-11-23
Use synaptic to uninstall - it will automatically delete the other packages.

---

### Post by xieu90 on 2007-11-24
how did you do that ? even I choose completely removal it would uninstall only that one package

---

### Post by drs305 on 2007-11-24
deborphan finds "orphaned" packages on your system. It determines which packages have no other packages depending on their installation, and shows you a list of these packages. It is most useful when finding libraries, but it can be used on packages in all sections.

You can install deborphan through synaptic.

---

### Post by rsambuca on 2007-11-25
sudo apt-get autoremove

---

### Post by erfahren on 2007-11-25
just in case you didn't know, you can view your history in Synaptic through File > History

---

