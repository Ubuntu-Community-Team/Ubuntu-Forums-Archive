---
title: "System Temperature Differences between 32 and 64 bit versions"
date: 2007-09-12
forum: x86 64-bit Users (Pre April '08)
---

### Post by atomicdad on 2007-09-12
I have the 64bit version installed on my laptop (Dell Inspiron 1520 T730,) and the install went pretty smooth. 

I've been running a finite element model generation code on my machine and it gets really hot really fast under full load, ( ~80 C, monitored with the Ksensor package installed). It is a proprietary code that we developed so I have access to either 32 bit or 64 bit versions, would running 32 bit Ubuntu be cooler on my laptop as opposed to the 64 bit version.

I'm hoping somebody might have some input to any operating temp differences before I just try the 32 bit install and test it out.

---

### Post by russo.mic on 2007-09-12
I've noticed that the 64 bit versions have been cooler on 2 laptops compared to the 32 bit versions

---

### Post by Jouke74 on 2007-09-13
Theoretically you are using more uh "bits" under 64 bit, thus it should become warmer. On the other hand 32 bit probably is being put by the processor as a 64 bit as well. Calculations 64 bit will be more efficient? I don't think it will make a huge difference in practise. With the program you're simply kicking the processor's ***. So make sure your cooling is working ok, because 80 degrees is actually quite high.

It would be an interesting test. However, I don think you are able to factor out all other variables 
(e.g. room temperature).

---

