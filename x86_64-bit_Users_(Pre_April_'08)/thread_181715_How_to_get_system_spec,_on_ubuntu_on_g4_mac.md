---
title: "How to get system spec, on ubuntu on g4 mac"
date: 2006-05-24
forum: x86 64-bit Users (Pre April '08)
---

### Post by moriatti on 2006-05-24
Im curious as to what cpu my machine has, and i am new to ubuntu, so excuse me if i sound a lil stoopid! :-?  lol

Ive just got a g4 powermac, and i have no idea of the cpu speed! 

It doesnt say on the case, so there must be a way! (like in windows: start/control panel/system)

Thanks all!

Moriatti

---

### Post by rado_london on 2006-05-24
Fire up a terminal (Application-Accessories-Terminal) and enter the following:
```
cat /proc/cpuinfo
```

This will give you the model of your CPU

---

### Post by moriatti on 2006-05-24
thanks! i will try that now! ;)

---

### Post by rado_london on 2006-05-24
Post if it went Ok because I have tested it on x86 machine not on mac.:)

---

