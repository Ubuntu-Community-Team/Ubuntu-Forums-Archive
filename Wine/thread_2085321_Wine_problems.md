---
title: "Wine problems"
date: 2012-11-17
forum: Wine
---

### Post by Tiltonblue on 2012-11-17
Hi all I have just loaded Ubunto and am really enjoying in, I am having problems installing wine, I keep getting the following error messages, can any one help me so i can start loading some of my windows software.

Package Dependancies Cannot be resolved.

This error could be caused by required additional software packages which are missing or not installable. Furthermore there could be a conflict between software packages which are not allowed to be installed at the same time.

Many thanks Mike

---

### Post by Gone fishing on 2012-11-17
How are you installing Wine?

I would guess not through the software centre but downloading a file, just try installing wine using the repositories and the software centre.

---

### Post by howefield on 2012-11-17
Thread moved to the "*Wine*" forum.

---

### Post by Tiltonblue on 2012-11-17
I have been doing it through the ubuntu software centre

---

### Post by Gone fishing on 2012-11-17
How odd never had a dependancy problems with software centre.

Try

```
sudo apt-get update
```
then
```
sudo apt-get install wine
```

In a terminal and post any errors and this should explain what the dependancy problems are possibly first check that you have enabled all the sources in the software centre.

---

### Post by Dlambert on 2012-11-18
To solve your WINE problems, check into rehab.

But, you could go the simpler route and install PlayOnLinux. PlayOnLinux is a GUI for WINE that makes installations of many programs a breeze, and even has installers for major applications that do all the work for you!

[http://www.playonlinux.com](http://www.playonlinux.com)

---

