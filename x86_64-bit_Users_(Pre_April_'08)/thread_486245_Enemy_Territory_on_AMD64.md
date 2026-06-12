---
title: "Enemy Territory on AMD64"
date: 2007-06-27
forum: x86 64-bit Users (Pre April '08)
---

### Post by djprozac on 2007-06-27
Hey guys,

Anyone managed to get Enemy Territory to work on Feisty Fawn 64bit?
I tried installing ia32-libs as the instructions at Zerowing.idsoftware.com state, but when I try to run the installer with

```
sudo linux32 sh et-linux-2.55.x86.run
```

I still get an error message saying

```
The setup program seems to have failed on x86/glibc-2.0
```

What am I doing wrong?

Thanks!

---

### Post by djprozac on 2007-06-28
*bump*

Anyone?

---

### Post by avik on 2007-06-28
I got it to work, but it was a long time ago.  Let's see if anything I say helps.

I know you have to install ia32-libs (sudo apt-get install ia32libs), and you should be able to run the installer via linux32:

```
sudo linux32 sh et-linux-2.60.x86.run
```

---

### Post by djprozac on 2007-06-28
Thats exactly what I tried (well I have version 2.55 of ET instead of 2.60 -could that be the cause?)

But when I try that it says

```
The setup program seems to have failed on x86/glibc-2.0
```
Thanks!

---

### Post by avik on 2007-06-29
2.60 was the only one that worked.  2.55 gave me the same error, if I remember correctly.

[http://linux.softpedia.com/get/GAMES-ENTERTAINMENT/FPS/Wolfenstein-Enemy-Territory-3948.shtml]("http://linux.softpedia.com/get/GAMES-ENTERTAINMENT/FPS/Wolfenstein-Enemy-Territory-3948.shtml")

Try running 2.60.

---

### Post by djprozac on 2007-06-29
Alright, I will. Thanks!

---

### Post by donkyhotay on 2007-09-16
I had the exact same problem with 64-bit feisty and downloading versin 2.60 worked. I couldn't find it on the 'official' site but it can be downloaded here:
[http://www.mrbass.org/enemyterritory/](http://www.mrbass.org/enemyterritory/)

---

### Post by FishFace on 2007-09-26
I have just tried to download and play version 2.60 using linux32, but to no avail:

```
...loading libGL.so.1: Segmentation fault (core dumped)
```

Any other ideas?

---

### Post by innocenceisdeath on 2007-09-27
Just download this.

[http://www.ausgamers.com/files/details/html/18074](http://www.ausgamers.com/files/details/html/18074)

Move to the directory you downloaded it to and run this in terminal:

```
sudo chmod a+x et-linux-2.60.x86.run
sudo et-linux-2.60.x86.run
```

Sorry if that code isn't right =/ I'm new to Linux but I did something along those lines and now have it running in Feisty Fawn 64bit

---

