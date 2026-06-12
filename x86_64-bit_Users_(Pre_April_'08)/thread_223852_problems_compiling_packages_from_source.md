---
title: "problems compiling packages from source"
date: 2006-07-27
forum: x86 64-bit Users (Pre April '08)
---

### Post by caseyaberhart on 2006-07-27
hi i hate to be a n00b here....

i'm having problems compiling packages.... ./configure doesnt work... or i dont know how to use it.... can anyone direct me to a guide on how to compile packages under ubuntu ppc? and what packages need to be installed in order to compile, and how to install them. thanks all

---

### Post by OpsVentus on 2006-07-27
To compile you need the package "build-essentials".
How to compile depends on the source your compiling, most of the time you start with "./configure", but other times just "scons", "qmake" even.
Compiling is the same under Ubuntu as under any other Linux.

Cheers,
Bart.

---

### Post by caseyaberhart on 2006-07-27
could you go into detail on how to install build-essentials? i tried apt-get build-essentials. it told me it couldnt find the package..... is there a difference between compiling packages on x86 and PPC?

---

### Post by OpsVentus on 2006-07-27
It should be:
#sudo apt-get install build-essential

There could be differences compiling packages. But I don't know exactly what.

Good luck,
Bart.

---

### Post by linear on 2006-07-27
The [CompilingSoftware]("https://help.ubuntu.com/community/CompilingSoftware") entry in the wiki has useful information.
 
The process is more or less the same on all platforms.

---

### Post by caseyaberhart on 2006-07-28
thanks wery much all

---

