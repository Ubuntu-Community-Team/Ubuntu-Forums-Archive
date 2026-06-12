---
title: "Error In Installing Wine"
date: 2013-03-09
forum: Wine
---

### Post by jithinjohnygeorge on 2013-03-09
I had downloaded the Wine, extracted and then started installing by command ./configure. 
After applying the command, it ends in the error message 


> configure: error: X development files not found. Wine will be built
without X support, which probably isn't what you want. You will need
to install development packages of Xlib/Xfree86 at the very least.
Use the --without-x option if you really want this.



i have installed 64 bit version of os. 


Please help me. Thanks in advance.

---

### Post by Mr. Shannon on 2013-03-09
Why not install wine from the repositories?
```
sudo apt-get install wine
```

If you really need to install from source (I don't recommend this for a beginner) then try installing the X11 development libraries first:
```
sudo apt-get install libx11-dev
```

---

### Post by jithinjohnygeorge on 2013-03-10
> [INDENT]If you really need to install from source (I don't recommend this for a beginner) then try installing the X11 development libraries first:
Code:

sudo apt-get install libx11-dev
[/INDENT]






when i have given this code, it shows an error message

> E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).




---

### Post by Shadowstripe on 2013-03-10
tbh I wouldn't even try building it from source if your running 64bit ubuntu seems overcomplicated and only compiles with a workaround

if you feel like giving it a go the instructions are available here

[http://wiki.winehq.org/WineOn64bit](http://wiki.winehq.org/WineOn64bit)

---

