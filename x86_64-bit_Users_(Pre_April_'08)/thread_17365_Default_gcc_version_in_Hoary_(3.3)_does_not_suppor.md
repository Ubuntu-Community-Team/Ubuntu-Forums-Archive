---
title: "Default gcc version in Hoary (3.3) does not support &quot;-march=k8&quot;"
date: 2005-02-28
forum: x86 64-bit Users (Pre April '08)
---

### Post by rwillmer on 2005-02-28
I am confused, enlightenment sought...

I'm in the process of compiling mythtv from source on my AMD64 box running Hoary.

It failed at the first hurdle when I got an error "-march=k8" not supported. More precisely, it fails with

[font=Lucida Console][color=Navy]cc1: error: bad value (k8) for -march= switch[/color][/font][color=Gray]
[/color] 
So I checked the man page, and did some googling, and sure enough, k8 isn't supported until gcc 3.4.

Not a problem for the task in hand, I've installed gcc 3.4 and compilation proceeds OK.

BUT, I'm confused. If the default compiler in hoary doesn't support this option, how is anything else I'm compiling or have installed being compiled for 64-bit usage?

Any suggestions, answers, etc, welcome...

---

### Post by AndersAA on 2005-02-28
try x86_64 or x86-64, it's something like that ;)

---

### Post by tube013 on 2005-02-28
I just went through this same thing.  It compiles fine with gcc-3.4  what I did was go into /usr/bin and change all the simlinks (gcc, g++, etc.) to point to the  *.3.4

just go to /usr/bin, and run ls -ln | grep 3.3 and those are the ones to change.  also make sure you install gcc-3.4.

I think there is another way to do this using debian alternatives, but I'm at a loss as to how.

I'm currently recompiling mythtv in the background right now.

---

### Post by cybrjackle on 2005-03-01
```

-march=athlon64

```

Try that on gcc 3.3

---

