---
title: "help with installing"
date: 2006-07-16
forum: x86 64-bit Users (Pre April '08)
---

### Post by ChrisJ on 2006-07-16
I'm trying to install a file "ati-driver-installer-8.26.18-x86_64.run" but am way to new to ubuntu to know how to install this myself.

how do i install this file please?

it is for my HIS ATIx1800GTO 256MB graphiccard.

feel free to email me at [email]tigger76@verizon.net[/email] for help

again...thank you for your help and assistance.

-Chrisj

---

### Post by Kilz on 2006-07-16
There is a [good hotwo that explains everything]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI#head-26e8b0d4be861a6b7c545dc21c45232f909d8ca2") and gives you what to type in. The only thing it is missing for 64bit is this command.
```
sudo apt-get install build-essential linux-headers-`uname -r`
```
Enter it in a terminal before starting the howto. Part of the howto will automaticly build kernels modules for you, it will need the things that command installs.

---

