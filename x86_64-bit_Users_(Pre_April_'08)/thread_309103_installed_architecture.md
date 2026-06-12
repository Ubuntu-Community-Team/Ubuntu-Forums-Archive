---
title: "installed architecture?"
date: 2006-11-29
forum: x86 64-bit Users (Pre April '08)
---

### Post by TWFJR on 2006-11-29
How does one know that they have installed a 64 bit architecture?  Not remembering the command, I learned that my system is recognized as "generic." I was expecting, "64 bit."  If I have a 32 bit architecture installed, what went wrong during the installation process that I missed the "64 bit" installation.  I do not remember any installation choice for 64 bit.  I looked for the choice during installation but saw no choice.

---

### Post by pay on 2006-11-29
To know if you are using 64bit or 32bit open up the terminal and type ```
uname -m
```x86 = 32bit, x86_64 = 64bit. To install the 64bit version of Ubuntu you must use the amd64 installation iso. Heres the iso you need. [ftp://mirror.d-jacobs.com/ubuntu/edgy/ubuntu-6.10-desktop-amd64.iso](ftp://mirror.d-jacobs.com/ubuntu/edgy/ubuntu-6.10-desktop-amd64.iso)

---

