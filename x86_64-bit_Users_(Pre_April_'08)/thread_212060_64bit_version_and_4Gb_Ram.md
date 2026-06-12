---
title: "64bit version and 4Gb Ram"
date: 2006-07-09
forum: x86 64-bit Users (Pre April '08)
---

### Post by iddo lev on 2006-07-09
Hey guys,

i'm new here.
i'm running an 

AMD Athlon64 3500 w 4Gb RAM

but the system monitor only shows 3.2 Gb RAM.

how do i know if i installed the 64-bit version?
how can i make use of all 4Gb RAM i have?

thanks,
iddo

---

### Post by Teroedni on 2006-07-09
In a terminal write uname -a


post the output here

---

### Post by iddo lev on 2006-07-09
uname -a  
-----------
Linux potato 2.6.15-23-amd64-generic #1 SMP PREEMPT Tue May 23 13:45:47 UTC 2006  x86_64 GNU/Linux

---

### Post by Teroedni on 2006-07-09
Yes you have 64 bit:)


so what does ```
cat /proc/meminfo
```
gives?

---

### Post by iddo lev on 2006-07-09
great. thanks.

so why doesn't it discover all 4Gb of RAM? 
the system monitor insists that i have only 3.2 Gb?

---

### Post by Teroedni on 2006-07-09
Does the command             
cat /proc/meminfo        
 shows the same?

And what motherboard are you using
Some motherboards have problem accessing over 3.5 gb

---

### Post by iddo lev on 2006-07-09
yeap.
it was the motherboard.
it works now.

thanks
iddo

---

