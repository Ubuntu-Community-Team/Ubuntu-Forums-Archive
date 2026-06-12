---
title: "Help with folding@home"
date: 2008-06-07
forum: x86 64-bit Users
---

### Post by Princey on 2008-06-07
I installed the folding@home client according to [this lin]("https://help.ubuntu.com/community/FoldingAtHome/fah_install")k from the help pages, however, when I run top, I see four instances running when I have an AMD 64 x2 Processor. Is this normal or am I doing something wrong with the configurations?

---

### Post by David E. Fox on 2008-06-07
> **Princey said:**
> I installed the folding@home client according to [this lin]("https://help.ubuntu.com/community/FoldingAtHome/fah_install")k from the help pages, however, when I run top, I see four instances running when I have an AMD 64 x2 Processor. Is this normal or am I doing something wrong with the configurations?

Perfectly normal. And if you run the client via 'fah6 -smp' it should automatically download the amd64 client and use it rather than the x86 client, and run in threaded mode - so all four instances of the process are actually doing work, since you have 2 cores, and each of those can do HT.

---

### Post by Princey on 2008-06-08
Thanks David, was wondering since when AMD dual cores were quad cores, lol. Thanks for clearing it up.

---

