---
title: "Permissions under wine"
date: 2008-06-12
forum: Wine
---

### Post by andriy.kostyuk on 2008-06-12
I tried to install a language course for win 95,98,NT under wine.

I accessed the installation CD via wine (wine->browse drive c:->CD icon).
Then pressed "Open autorun prompt", confirmed by pressing "run".eBut at this pint, I got the message "Error starting autoran program: permission denied".
Indeed, when I checked the permissions of "autorun.exe" under wine (left-click on it in the wine window), I found that I have only the permission to read this file and I cannot change it because the owner is root.

But if I checked the permissions of the same file in the linux terminal (ls -l), I found that I (and everybody else) do have the permission to execute this file.

How to solve this problem? How can one make the same permissions under wine as they are under linux?

Thanks in advance.

---

### Post by Sleaka J on 2008-06-12
It's a CD, they are always read-only.

But to install your program, you should go to a terminal and type the following:

```
wine /media/cdrom/setup.exe
```

Where "/media/cdrom" is the location of your CD-ROM drive and "setup.exe" is the executable file to install it.

I didn't think CD autorun ran under Wine at all.

---

### Post by cogadh on 2008-06-12
Some autorun *executables* will run, but Wine does not have autorun functionality at all. It is usually best to just skip the whole autorun step and go straight to manually running the setup.exe anyway.

---

