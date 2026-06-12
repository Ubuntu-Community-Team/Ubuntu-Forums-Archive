---
title: "Not able to d/l ia-32 libs"
date: 2008-05-08
forum: x86 64-bit Users
---

### Post by Lifeboat on 2008-05-08
I have two computers running 8.04 X64. The first one found and downloaded the ia-32 libs, right away.

The second one keeps telling me (in the terminal window):
adak@adak-dualQuad:~$ sudo apt-get install ia-32libs
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ia-32libs

Naturally, I run a program which requires the ia-32libs, on both computers. What can I do to get this critical library?

[SOLVED] Thanks tamoneya, what a goofy error.

---

### Post by tamoneya on 2008-05-08
you spelled it wrong.  No big problem```
sudo apt-get install ia32-libs
```

---

### Post by Bluesky09 on 2009-03-14
I am trying to download the drivers for my Dell all-in-one printer A940 using LexmarxZ55 drivers.  I keep getting this message? sunset@sunset-desktop:~$ sudo apt-get install ia32-libs
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ia32-libs
sunset@sunset-desktop:~$ 

saying that ia-32-libs cannot be find?  I have only been using Linus now for about 3 weeks.  Can anyone Help!:(

---

### Post by Yellow Pasque on 2009-03-14
Bluesky09: are you sure you're running the x86_64 version of Ubuntu? What does this return?
```
uname -m
```

---

