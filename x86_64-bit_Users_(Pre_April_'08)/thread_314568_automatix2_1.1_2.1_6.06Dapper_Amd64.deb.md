---
title: "automatix2_1.1_2.1_6.06Dapper_Amd64.deb"
date: 2006-12-07
forum: x86 64-bit Users (Pre April '08)
---

### Post by Bhawns on 2006-12-07
I am running Dapper 64bit and I don`t see this alacarte menu editor all I have is the application menu editor. Where for me will I find this gdebi program?

---

### Post by devnu11 on 2006-12-07
Try system -> preferences -> Menu Layout  I don't have dapper but it is on Edgy as I described.

---

### Post by Kilz on 2006-12-07
> **Bhawns said:**
> I am running Dapper 64bit and I don`t see this alacarte menu editor all I have is the application menu editor. Where for me will I find this gdebi program?

Double click on the .deb file and gdebi will start automatically.

---

### Post by Bhawns on 2006-12-07
Sorry guys no menu layout in that area you mentioned. Is it that some Repo. or package needs to be installed to see it anywhere?

---

### Post by Kilz on 2006-12-07
> **Bhawns said:**
> Sorry guys no menu layout in that area you mentioned. Is it that some Repo. or package needs to be installed to see it anywhere?

gdebi isn't a program that you start by clicking on a menu item. But rather it starts when you double click on a .deb file to enable installing of that deb file in a graphical way. When you type gdebi into the terminal you get

```
ubuntu:~$ gdebi
/usr/lib/python2.4/site-packages/apt/__init__.py:17: FutureWarning: apt API not stable yet
  warnings.warn("apt API not stable yet", FutureWarning)
Usage: /usr/bin/gdebi [package.deb]

To use the graphical user interface, right-click
on a '.deb' software package in the file browser
and select: Open with 'GDebi Package Installer'.
```

---

### Post by Bhawns on 2006-12-08
All that is said I would be humbled, the thing is I have a .deb package and when I click it (could not open achive type not supported) that`s it no package installer. Next step! the other qusetion is as earlier is some parts of the package missing that makes this installer function?

---

