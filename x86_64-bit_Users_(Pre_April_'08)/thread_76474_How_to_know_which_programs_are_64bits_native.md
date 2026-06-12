---
title: "How to know which programs are 64bits native?"
date: 2005-10-15
forum: x86 64-bit Users (Pre April '08)
---

### Post by JuanC on 2005-10-15
Hi to all ,

I installed Kubuntu 5.10 for Amd 64-bit.

During the install i saw that a 32bits kde lib was created.

Using apt-get i install serveral applications , but i didn't know if they are 64 bits native or 32 bits.


How to know which programs are 64bits native?

---

### Post by Anes Lihovac on 2005-10-16
Hi

You could do 'file filename', e.g. 'file /usr/bin/kwin' gives: 

/usr/bin/kwin: ELF 64-bit LSB executable, AMD x86-64, version 1 (SYSV), for GNU/Linux 2.6.0, dynamically linked (uses shared libs), stripped

which shows you that the KDE app kwin is a 64Bit linux binary. The are a bunch off 32bit compatiblity libs installed cause some apps like OpenOffice are not builded for 64bit, cause iiirc they cannot be builded native for 64bit so the 32bit version is used. But most of the apps in 64Bit Ubuntu are realy 64bit compiled apps. OpenOffice is the only one which I know at the moment is 32bit.

Regards
Anes

---

### Post by JuanC on 2005-10-17
Thanks , I try it.

---

