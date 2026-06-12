---
title: "How can I tell if my Ubuntu install is 64-bit?"
date: 2007-05-22
forum: x86 64-bit Users (Pre April '08)
---

### Post by timdoc1 on 2007-05-22
uname -a doesn't cut it (as was recommended in previous post in another category).  HOw do I know?  I get the same result to that command on my 32-bit machine.

Thanks,
Tim

---

### Post by pbw on 2007-05-22
Just take a quick peek in /var/cache/apt/archives/  and see if you've been installing x86 or x86-64 bit debs *shrug*

---

### Post by Cappy on 2007-05-22
If
```
sudo apt-get install ia32-libs
```
returns "installed" or allows you to install it then you have a 64-bit OS. I don't know another way =p

---

### Post by incubus on 2007-05-22
How about this:

```

$ arch

```
...should return "x86_64".

incubus

---

