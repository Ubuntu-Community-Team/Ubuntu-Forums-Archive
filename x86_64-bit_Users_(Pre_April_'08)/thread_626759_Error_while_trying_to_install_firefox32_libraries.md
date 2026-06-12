---
title: "Error while trying to install firefox32 libraries"
date: 2007-11-29
forum: x86 64-bit Users (Pre April '08)
---

### Post by Fixman on 2007-11-29
I used [this]("https://help.ubuntu.com/community/AMD64/FirefoxAndPlugins") page for trying to install 32 bit firefox on my AMD64 Ubuntu. The problem is tat, when I write

```
 sudo aptitude install ia32-libs ia32-libs-gtk linux32 lib32asound2 
```

It tells me

```

Remove the following packages:
ubuntu-minimal
util-linux
util-linux-locales

Score is -99754

Accept this solution? [Y/n/q/?] y
The following ESSENTIAL packages will be REMOVED!
  util-linux 

WARNING: Performing this action will probably cause your system to break!
         Do NOT continue unless you know EXACTLY what you are doing!
To continue, type the phrase "I am aware that this is a very bad idea":

```

In that page, it sayed that util-linux would give problems, but it didn't say anything about ubuntu-minimal. Its a bad idea typing "I am aware this is a bad idea" or it isn't?

---

### Post by Cappy on 2007-11-29
What you want is
```
sudo aptitude install ia32-libs lib32asound2
```
This solves your problem.

ia32-libs-gtk is inside ia32-libs in Gutsy and linux32 is inside util-linux.
If you ever remove util-linux you will break your system, by the way.

---

