---
title: "package lists"
date: 2008-02-29
forum: x86 64-bit Users (Pre April '08)
---

### Post by professor-g on 2008-02-29
apolgoies - super simple question - i have forgotten stuff in past few months

recently upgraded from 7.04 (complete reinstall - ah  fresh!)
now - ubuntu 7.10 desktop
this problem not encountered in 7.04 installs

when doing the following it cant find package lists:

sudo apt-get update
reading package lists
done

they are probably commented out in the file ... 
Where is the file that defines packagae lists ?

Thx,


G.

---

### Post by jan quark on 2008-02-29
run this terminal

```
gksudo gedit /etc/apt/sources.list
```

---

### Post by professor-g on 2008-02-29
thx !

I just vi'd the file and uncommented everything I needed to  ... basically forget location of the file

---

