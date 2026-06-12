---
title: "Install of Wine quit while installing from software center while running u14.04 from"
date: 2014-10-21
forum: Wine
---

### Post by nu2u904 on 2014-10-21
Install of Wine quit while installing from software center from live disk running u14.04.1. Locked up software center,I could not redo or install any other software.  Initially I had attempted to do this on the same computer [acer-one-aspire500] from a working installed u14.04.1 system. Wine was installing and the install arrows were moving and stopping. I assumed this was normal and proceded to install 32 other program. No programs were installed all showed waiting to install even though their icons were displayed on the launcher. I shutdown and attempted to restart the computer. All I got was a blank screen.  Hence my switch to the live dvd. How did installing Wine cause grub2 to be corrupted? How can I find and run boot-repair from the live disk?

---

### Post by Alireza_Zamani on 2014-11-01
in a short sentence what is your problem ?
.........................................................
if ubuntu software center crashed, you can kill that, and run it again :
```
$ pidof software-center
$ kill [pid]
$ software-center
```

---

### Post by Bucky Ball on 2014-11-01
> **Alireza_Zamani said:**
> in a short sentence what is your problem ?
.........................................................
if ubuntu software center crashed, you can kill that, and run it again :
```
$ pidof software-center
$ kill [pid]
$ software-center
```

^^^
This.

I will assume for the moment it is a Wine issue until you let us know one way or the other. And unsure why you posted this in ***New to Ubuntu***. That will decrease your chances of help with this. Please post in the appropriate forum section. Thanks. ;) 

*Thread moved to **Wine**.*

---

