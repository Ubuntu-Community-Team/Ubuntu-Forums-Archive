---
title: "Error: Wrong architechture ' Amd64'"
date: 2008-10-17
forum: x86 64-bit Users
---

### Post by kurtdriver on 2008-10-17
I received the above error message after attempting to install a number of .debs through gnome. They were all AMD64 from packages.ubuntu.org. This is on a AMD Phenom X4 chip which I understand is designed to enable simultaneous 32- and 64-bit computing. So, I'm confused as heck, I have a 64 bit chip, why wouldn't they install? Any help would be much appreciated. Thanks, Kurt

---

### Post by dje on 2008-10-17
you may have a 64 bit processor but do you have a 64 bit os? you must have a 64 bit processor **and** a 64 bit os to use 64 bit programs ;)

dje

---

### Post by Yellow Pasque on 2008-10-17
```
uname -a
```

---

### Post by jespdj on 2008-10-18
You have most likely the 32-bit version of Ubuntu installed. Try this command:
```
uname -m
```
If it says **i686**, then you have 32-bit Ubuntu installed.
If it says **x86_64**, then you have 64-bit Ubuntu installed.

To be able to use amd64 packages, you must be using Ubuntu 64-bit. If you have 32-bit Ubuntu, use the equivalent 32-bit (i386) packages.

---

### Post by kurtdriver on 2008-10-18
That's it, Thanks a lot, Kurt

---

