---
title: "Open Hand clutter"
date: 2007-08-26
forum: x86 64-bit Users (Pre April '08)
---

### Post by Basics102 on 2007-08-26
Well im very new to Ubuntu but found this on the web ----> [here]("http://www.clutter-project.org/"). Well I definitely want this, but I dont know how to compile it. I have Ubuntu installed on AMD64, ati X600. [http://video.google.com/videoplay?docid=5623221548018224547](http://video.google.com/videoplay?docid=5623221548018224547)

I tried the svn thing and then ./autogen.sh, make, sudo make install but that doesnt work.

Hope someone can help me... thanks

---

### Post by Kilz on 2007-08-26
> **Basics102 said:**
> Well im very new to Ubuntu but found this on the web ----> [here]("http://www.clutter-project.org/"). Well I definitely want this, but I dont know how to compile it. I have Ubuntu installed on AMD64, ati X600. [http://video.google.com/videoplay?docid=5623221548018224547](http://video.google.com/videoplay?docid=5623221548018224547)

I tried the svn thing and then ./autogen.sh, make, sudo make install but that doesnt work.

Hope someone can help me... thanks

[It looks like they have a repository]("http://debian.o-hand.com/") you can add. perhaps that will have the packages already built for you.

---

### Post by Basics102 on 2007-08-27
It doesnt work, perhaps because im using amd64.

---

### Post by Basics102 on 2007-08-27
Got it to work with compiling with sourceball and using ./configure, also there are dependencies needed to be installed like gstreamer-dev and pytgk-dev.

---

