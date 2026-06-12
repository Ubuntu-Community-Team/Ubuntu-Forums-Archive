---
title: "Ubuntu 64bit &amp; AMD 6 core Opteron"
date: 2009-11-12
forum: x86 64-bit Users
---

### Post by Barbaros.Oezdemir on 2009-11-12
[SIZE=4][SIZE=3]Does Ubuntu Support AMD's six-core "Istanbul" Opteron processors?
 
Thanks for any feedback. [/SIZE][/SIZE]

---

### Post by Kilz on 2009-11-12
> **Barbaros.Oezdemir said:**
> [SIZE=4][SIZE=3]Does Ubuntu Support AMD's six-core "Istanbul" Opteron processors?
 
Thanks for any feedback. [/SIZE][/SIZE]

It should as smp detects to my phenom with the generic kernel. Boot into a live cd to make sure. Open a terminal and enter this command to tell how many corers it sees.
```
cat /proc/cpuinfo
```

---

### Post by insane_alien on 2009-11-12
there is no reason why it shouldn't. it's an AMD64 processor with AMD64 instruction sets and the kernel can handle FAR FAR more processors/cores than 6

---

