---
title: "CPU usage more than 100%"
date: 2008-07-29
forum: x86 64-bit Users
---

### Post by aranzuglia on 2008-07-29
Hi, we have a web application that receives about 10 users per second.

**uname -a**
```
Linux host 2.6.24-16-server #1 SMP Thu Apr 10 13:15:38 UTC 2008 x86_64 GNU/Linux
```

**top**
```
top - 15:58:17 up 6 days, 11:51,  3 users,  load average: 2.04, 2.08, 2.08
Tasks:  91 total,   1 running,  90 sleeping,   0 stopped,   0 zombie
Cpu(s): 47.5%us,  0.1%sy,  0.0%ni, 52.2%id,  0.2%wa,  0.0%hi,  0.0%si, 0.0%st
Mem:   4049544k total,  2980876k used,  1068668k free,   208556k buffers
Swap:  8008392k total,      104k used,  8008288k free,   826664k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
21697 administ  20   0 3711m 1.4g  15m S  200 37.0 227:19.56 java                                                                 
 5599 mysql     20   0  898m 166m 6104 S    2  4.2  45:54.99 mysqld
``` 


Why is the java process telling 200% CPU usage?

Thanks

---

### Post by tamoneya on 2008-07-29
that is because you have a dual core machine.

---

### Post by aranzuglia on 2008-07-29
With dmesg I can see 4 CPUs: CPU0 ... CPU3, are there really 4 processor?

I can't understand what 200% means? It also says CPU(s) 47.5%us. What is the relationship between them?

Thanks again

---

### Post by tamoneya on 2008-07-29
im not sure what the 47.5% means but 200% means you have two cores at 100% or 4 cores at 50%.

---

