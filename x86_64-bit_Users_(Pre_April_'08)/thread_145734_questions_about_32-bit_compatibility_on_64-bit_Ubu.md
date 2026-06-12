---
title: "questions about 32-bit compatibility on 64-bit Ubuntu"
date: 2006-03-16
forum: x86 64-bit Users (Pre April '08)
---

### Post by blaine00 on 2006-03-16
This seems like one of those questions that has probably be answered over a hundred times but I honestly have not been able to find information about it.

I am wanting to build a computer with a 64-bit chip... either a Sempron 64 or Athlon 64. If I decide to use 64-bit Ubuntu, does that mean I won't be able to run programs compiled for 32-bit chips? Also, will all my device drivers have to be 64-bit?

---

### Post by MighMoS on 2006-03-16
If you buy a 64-bit system, then you can run 32 bit code as well.  But your device drivers will have to be 64 bit if you use a 64 bit kernel (it is possible to use a 32 bit kernel)

---

### Post by casper_2095 on 2006-03-17
1) So whilst the default ubuntu is a 32 bit kernel, this AMD 64 forum is all about the 64 bit kernel?  

2) I don't recall having to dig around endlessly for shiny new 64 bit drivers for everything in my box.  It all just workedTM.  Does someone really have to rebuild every driver for every kernel?  Surely there is some abstraction there.  Is this tribute to some guys who like to sit around geeking up new drivers for everything, or was it actually a bit of a no-brainer?

---

### Post by blaine00 on 2006-03-17
Great! I hear of a lot of people having issues with 64-bit Ubuntu and I am hoping most of this stuff will be fixed by the time Dapper comes out.

I am not too worried about needing 64-bit drivers because I really haven't had to get any drivers outside of the default installation and repos... and I would imagine everything in the repos would be compiled correctly by default.

I do however have a few 32-bit programs I got outside the repos and it is nice to know I will able to run them under a 64-bit OS.

---

### Post by MighMoS on 2006-03-17
I actually don't know too much about driver development, but I do know that drivers would at least have to be re-*compiled*.  As for re-written, I guess it depends on the driver.

---

