---
title: "apt-find not installed"
date: 2007-05-06
forum: x86 64-bit Users (Pre April '08)
---

### Post by colin59 on 2007-05-06
in other versions of linux i've used the apt-find command extensively and it's help me to update my apps. Is there any way that i can either enable or install this app? how can go about doing this?

---

### Post by Cappy on 2007-05-06
synaptic or **System->Administration->Synaptic Package Manager** is the most common program in Ubuntu. 
There's also dselect, aptitude, gnome-apt, and wajig.

---

### Post by firecat53 on 2007-05-07
From the command line:

apt-cache search xxxx
or
aptitude search xxxx

aptitude search ~dxxxxxx  will also search the package descriptions

Scott

---

### Post by colin59 on 2007-05-07
much thanks!

---

