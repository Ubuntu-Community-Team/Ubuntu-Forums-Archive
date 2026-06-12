---
title: "Libqt4 missing"
date: 2009-09-08
forum: x86 64-bit Users
---

### Post by kempy1000 on 2009-09-08
Hi

I have been trying to update my mythtv version to the latest unstable svn release.

I am fine with compiling etc just one small problem, when it comes to installing i issue the command:

sudo checkinstall

I get an error saying that libqt4 is missing, i have hunted for this package and cannot find it anywere!

Thanks for any help 

Chris

---

### Post by Yellow Pasque on 2009-09-08
```
sudo apt-get install libqt4-core libqt4-dev libqt4-gui libqt4-sql qt4-dev-tools qt4-qtconfig qt4-doc qt4-designer
```

---

### Post by kempy1000 on 2009-09-08
> **Temüjin said:**
> ```
sudo apt-get install libqt4-core libqt4-dev libqt4-gui libqt4-sql qt4-dev-tools qt4-qtconfig qt4-doc qt4-designer
```

Hi

Thanks

upon issuing this command i get the result:

```

Reading package lists... Done
Building dependency tree
Reading state information... Done
libqt4-core is already the newest version.
libqt4-dev is already the newest version.
libqt4-sql is already the newest version.
libqt4-sql set to manually installed.
qt4-qtconfig is already the newest version.
qt4-qtconfig set to manually installed.
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies.
  mythtv: Depends: libqt4 but it is not installable
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).


```

Thanks
Chris

---

### Post by Yellow Pasque on 2009-09-09
Ok. So try:
```
sudo apt-get install libqt4
```
and see why it's not installable.

---

