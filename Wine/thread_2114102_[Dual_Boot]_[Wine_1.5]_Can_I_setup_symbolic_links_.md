---
title: "[Dual Boot] [Wine 1.5] Can I setup symbolic links for .dll's for wine?!"
date: 2013-02-09
forum: Wine
---

### Post by ksaul on 2013-02-09
just like the topic said, since I am running Ubuntu 12.04 x64 and Windows 7 x64 on the same machine, is it possible to setup a symbolic link between the partitions so WIne1.5 has all the neccessary .dll's to run smoothly?

---

### Post by U202E on 2013-02-13
Wine can't run installed programs from a windows partition, if you manage to force wine to do so (will probably fail) your windows 7 won't boot anymore. :o
only if you have a portable app on your windows partition wine can start it up.
and it's the same things with dll's.
the wine dll's are 'fake': they point to the linux system, so different from the windows ones.

Maybe there is a fork of wine that can use a windows partition. So far I wasn't able to find it.
But it would be a fun project to make such a version wine.

---
you can set up symbolic links to another version of wine but that's not what you want.

---

### Post by dmallion on 2013-02-15
Yes. Wine can use same ddl's and programs as on a widows. But that said,they still have to be compatible with wine.

---

### Post by Mark Phelps on 2013-02-15
> **dmallion said:**
> Yes. Wine can use same ddl's and programs as on a widows. But that said,they still have to be compatible with wine.

I think you misunderstand how Wine works and the OP's question ...

As mentioned, for Windows programs to run in Linux, the DLLs that make Windows system calls have to be REPLACED with DLLs that make Linux system calls.  Thus, SOME Windows DLLs will not work with Wine.

The OP appears to be asking about linking to Windows DLLs in an existing Windows installation -- which the previous poster already answered.

---

