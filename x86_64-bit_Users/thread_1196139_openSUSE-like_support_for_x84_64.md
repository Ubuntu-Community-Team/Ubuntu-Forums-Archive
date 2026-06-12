---
title: "openSUSE-like support for x84_64 ?"
date: 2009-06-24
forum: x86 64-bit Users
---

### Post by Shinka.S on 2009-06-24
I have openSUSE 11.1 on my laptop and Ubuntu 9.04 on my desktop. Both are 64bits versions.

I must say that, while I prefer Ubuntu to openSUSE, the support for 64bits seems horrible for Ubuntu. I don't exactly know how it works, but from what I understand when I installed openSUSE from the dvd, it also installed 32bits librairies to make programs such a Skype works with no problem. I just tried to install Skype on Ubuntu 64 and I got stange messages (I had to uninstall severals librairies and I want to take a look at it before making mistakes). 

I am **not** asking for help to install Skype, several people have done it and I'm sure I can do it, but I wonder if there's a way to get the same level of support for 32bits lib with Ubuntu 64 ?

I don't understand why Ubuntu isn't making more effort to improve the support for the 64bits version, most modern computer have AMD64 processors. Yet even the download page of Ubuntu doesn't encourage people to get the 64bits version.

---

### Post by Therion on 2009-06-24
Have you installed **ia32-libs**?

```
sudo apt-get install ia32-libs
```

---

### Post by Arup on 2009-06-24
Installing skype via medibuntu repos automatically draws in the 32bit libs, no need for separate install.

---

### Post by Shinka.S on 2009-06-24
> **Therion said:**
> Have you installed **ia32-libs**?

```
sudo apt-get install ia32-libs
```

Yep. But when I try to install the file from skype.com it says "Wrong architecture". Which is my point; openSUSE hasn't this problem and I wonder why Ubuntu doesn't support more 64bits computers.

> **Arup said:**
> Installing skype via medibuntu repos automatically draws in the 32bit libs, no need for separate install.

I already have this repo and I just checked in Software Sources, it works and it's updated. Yet I get no result with "Skype" from add/remove, and I only have skyketool frmo synaptics.

And as I said, this is not about skype, it's not the only program I have troubles with, is there a way to get all the 32bits equivalent of the libraries as in openSUSE ?

---

### Post by Yellow Pasque on 2009-06-24
[http://ubuntuforums.org/showthread.php?t=474790](http://ubuntuforums.org/showthread.php?t=474790)

---

### Post by Sef on 2009-06-26
Read [**getlibs: Automatically solves dependencies for 32-bit programs on 64-bit.**]("http://ubuntuforums.org/showthread.php?t=474790&highlight=64+bit")

---

### Post by jespdj on 2009-06-27
> **Shinka.S said:**
> I already have this repo and I just checked in Software Sources, it works and it's updated. Yet I get no result with "Skype" from add/remove, and I only have skyketool frmo synaptics.
Then you should check if you added the Medibuntu repository properly, because that should just work. See [http://www.medibuntu.org/](http://www.medibuntu.org/)

---

