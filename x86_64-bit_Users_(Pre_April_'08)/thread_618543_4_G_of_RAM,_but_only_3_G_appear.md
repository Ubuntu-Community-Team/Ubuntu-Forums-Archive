---
title: "4 G of RAM, but only 3 G appear"
date: 2007-11-20
forum: x86 64-bit Users (Pre April '08)
---

### Post by cow_racer on 2007-11-20
I just installed 4 G of RAM but gutsy only see 3 G of RAM. I'm very sure I'm running AMD64 version. 
```


$uname -a

Linux alis 2.6.22-14-generic #1 SMP Sun Oct 14 21:45:15 GMT 2007 x86_64 GNU/Linux


```

---

### Post by John.Michael.Kane on 2007-11-20
> **cow_racer said:**
> I just installed 4 G of RAM but gutsy only see 3 G of RAM. I'm very sure I'm running AMD64 version. 
```


$uname -a

Linux alis 2.6.22-14-generic #1 SMP Sun Oct 14 21:45:15 GMT 2007 x86_64 GNU/Linux


```

Well your not going to get much help by only listing uname -a. More details from you will garner you a better response to the issue you have, Mainly your complete hardware specs, and the output of the command below.

```
free -t
```

---

### Post by cow_racer on 2007-11-20
```
             total       used       free     shared    buffers     cached
Mem:       3096684     936272    2160412          0      49556     417636
-/+ buffers/cache:     469080    2627604
Swap:      2048248          0    2048248
Total:     5144932     936272    4208660

```

---

### Post by Fire_Chief on 2007-11-20
What motherboard do you have (vendor/version) and what is the BIOS revision are you running? Out of the box, some boards don't play well w/ 64-bit and 4GB of RAM or more.

---

### Post by kuja on 2007-11-20
Another idea. Why not pop in a 64-bit knoppix DVD and see what it detects. I've found it's really good with hardware detetion.

---

### Post by cow_racer on 2007-11-20
I read else where that the chipset 945 on the thinkpad t60 will not support 4 G of RAM.  

[http://forum.thinkpads.com/viewtopic.php?t=41554](http://forum.thinkpads.com/viewtopic.php?t=41554)

Sounds like I had wasted money on the extra memory.

---

