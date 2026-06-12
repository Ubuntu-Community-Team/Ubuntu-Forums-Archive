---
title: "E: Couldn't find package linux-amd64-k8-smp"
date: 2006-03-27
forum: x86 64-bit Users (Pre April '08)
---

### Post by jtp51 on 2006-03-27
$ sudo apt-get install linux-amd64-k8-smp
Password:
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package linux-amd64-k8-smp

This is frustrating, I have checked to make sure that my universe is selected in my repository list.

How can I get the package linux-amd64-k8-smp?

Thanks,

---

### Post by o_fortuna on 2006-03-27
[QUOTE=jtp51]$ sudo apt-get install linux-amd64-k8-smp
Password:
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package linux-amd64-k8-smp

This is frustrating, I have checked to make sure that my universe is selected in my repository list.

How can I get the package linux-amd64-k8-smp?

Thanks,[/QUOTE]
I don't have a clue why apt won't install it. However, you can find the package here: [http://packages.ubuntu.com/breezy/base/linux-amd64-k8-smp]("http://packages.ubuntu.com/breezy/base/linux-amd64-k8-smp")
Download the package to the desktop, open a terminal (Applications-->Accessories-->Terminal) and put this in:
```
cd Desktop
sudo dpkg -i <package>
```
where <package> is the exact name of the package. Hope that works for you.

---

