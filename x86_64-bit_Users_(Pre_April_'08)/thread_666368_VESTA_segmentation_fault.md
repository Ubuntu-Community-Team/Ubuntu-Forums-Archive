---
title: "VESTA segmentation fault"
date: 2008-01-13
forum: x86 64-bit Users (Pre April '08)
---

### Post by kevintibbetts on 2008-01-13
I have been messing around with Linux for a little while, but am still somewhat of a beginner.  I am running ubuntu 7.10 on AMD64.
I need to have a crystal structure viewer,  VESTA and VICS-II (essentially an older version of VESTA) are the best options.  They have 64 bit versions that are known to work on 
    *  Fedora 4, 5, 6, 7, 8
    * Mandriva 2006, 2007.1
    * openSUSE 10.0
    * Redhat Enterprise Linux 4 
but not Ubuntu.  This is not a package that is installed.  It is a tarred directory that runs upon extraction (I don't know the proper terms for this).  I tried running on my ubuntu, but got a segmentation fault.
I thought about installing the i386 version of ubuntu, but I would rather try to figure out how to get the 64 bit version working on ubuntu.
Can anyone tell me if there is a way to figure out why it won't work?
Thanks,
Kevin

---

### Post by Kilz on 2008-01-13
> **kevintibbetts said:**
> I have been messing around with Linux for a little while, but am still somewhat of a beginner.  I am running ubuntu 7.10 on AMD64.
I need to have a crystal structure viewer,  VESTA and VICS-II (essentially an older version of VESTA) are the best options.  They have 64 bit versions that are known to work on 
    *  Fedora 4, 5, 6, 7, 8
    * Mandriva 2006, 2007.1
    * openSUSE 10.0
    * Redhat Enterprise Linux 4 
but not Ubuntu.  This is not a package that is installed.  It is a tarred directory that runs upon extraction (I don't know the proper terms for this).  I tried running on my ubuntu, but got a segmentation fault.
I thought about installing the i386 version of ubuntu, but I would rather try to figure out how to get the 64 bit version working on ubuntu.
Can anyone tell me if there is a way to figure out why it won't work?
Thanks,
Kevin

Please copy the error you receive from the terminal to a post here. I tride VICS-II and did not get a segmentation error, but a different error.

---

### Post by kevintibbetts on 2008-01-13
when I run VICS-II I just get

Segmentation fault (core dumped)

Is there away for me to get more verbose output?
Thanks,
Kevin

---

### Post by Kilz on 2008-01-13
> **kevintibbetts said:**
> when I run VICS-II I just get

Segmentation fault (core dumped)

Is there away for me to get more verbose output?
Thanks,
Kevin

Not that I know, All I did was open a terminal, navigate to the directory, and start the application in the terminal. For that I got a missing library error, but it isnt a library from any version of Ubuntu. It must have been compiled off of a different distribution.

---

### Post by kevintibbetts on 2008-01-13
By the way, VESTA is the more recent software it is at
[http://www.geocities.jp/kmo_mma/crystal/en/vesta.html](http://www.geocities.jp/kmo_mma/crystal/en/vesta.html)

---

### Post by Kilz on 2008-01-14
> **kevintibbetts said:**
> By the way, VESTA is the more recent software it is at
[http://www.geocities.jp/kmo_mma/crystal/en/vesta.html](http://www.geocities.jp/kmo_mma/crystal/en/vesta.html)

That application starts., see screenshot.

What video drivers do you have installed?

---

### Post by kevintibbetts on 2008-01-14
Excellent!! Thanks.
I installed the restricted NVIDIA driver and it works fine now.
Thanks again.

---

### Post by kevintibbetts on 2008-01-14
By the way, VICS-II also works for me with the new video driver,
You're a genius!

---

