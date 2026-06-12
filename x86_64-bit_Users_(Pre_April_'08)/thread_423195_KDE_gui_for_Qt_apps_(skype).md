---
title: "KDE gui for Qt apps (skype)"
date: 2007-04-25
forum: x86 64-bit Users (Pre April '08)
---

### Post by Cervantez on 2007-04-25
Skype (i think) is a qt app. When installed on gnome, it looks ugly.

In 32-bit ubuntu, you can just download the KDE libraries (kde-libs4 i think) that come with all KDE apps (like kopete) when you download them from synaptic.

Installing that in 64-bit doesn't work though. Does anyone know how to give skype a proper gui in gnome with 64-bit OS?

Thanks.

---

### Post by Kilz on 2007-04-25
> **Cervantez said:**
> Skype (i think) is a qt app. When installed on gnome, it looks ugly.

In 32-bit ubuntu, you can just download the KDE libraries (kde-libs4 i think) that come with all KDE apps (like kopete) when you download them from synaptic.

Installing that in 64-bit doesn't work though. Does anyone know how to give skype a proper gui in gnome with 64-bit OS?

Thanks.

Yes, to a degree. You see the problem is that skype is a 32bit application. The kde libraries that you can download through apt/synaptic are 64bit. You can however install a 32bit version. But its a lot of manual installing. You will also have to know the names of the packages. 
There are a few already packaged the package name is ia32-libs-kde. If that doesnt make everythiong look better. You will have to go to the [Ubuntu package site]("http://packages.ubuntu.com/") download all the libraries and their dependancies. Extract the contents

```
sudo dpkg -x packagename
```

Then copy the contents of the /usr/lib in the package contents to /usr/lib32 on your computer.

---

