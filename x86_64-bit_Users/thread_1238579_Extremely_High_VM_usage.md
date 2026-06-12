---
title: "Extremely High VM usage"
date: 2009-08-12
forum: x86 64-bit Users
---

### Post by ufuser1 on 2009-08-12
I'm not completely sure if this is normal, but being a windows user this somewhat looks strange.. I've
already resized my swap partition half it's size(2.75gb) and I have 2 Gigs of ram.

---

### Post by emshains on 2009-08-12
And what does happen when you check the VM usage on the resources tab?

---

### Post by ufuser1 on 2009-08-12
Swap, as far as research goes, isn't it supposed to be proportional to VS?, this contradicts itself and it's confusing me.

---

### Post by emshains on 2009-08-12
Well, swap IS  virtual memory, to be more specific, swap is a partition which acts like RAM, but is slower (better than page files on windows). I suspect that something is very wrong with your setup, but the gnome system monitor is known to not work properly, it can even cause fatal crashes, AND I DON'T UNDERSTAND WHY IS IT STILL SHIPPED WITH UBUNTU.
Try opening a terminal and running the command "top". It's a bit hard at the start, but once you get used to it, it's the perfect tool for checking the systems' resources.

---

### Post by ufuser1 on 2009-08-12
What could be wrong?, this is the third time i format my partition, and this one was just recently.

---

### Post by Bronto on 2009-08-12
The second screenshot shows that there isn't a swap partition in your system!

---

### Post by ufuser1 on 2009-08-12
You're right, i just noticed that Swap On/Off entry, but i think i have another problem, changes wont save on restart. 
I'm just wondering why I'm having these saving problems all of sudden.

---

### Post by ufuser1 on 2009-08-12
> **ufuser1 said:**
> You're right, i just noticed that Swap On/Off entry, but i think i have another problem, changes wont save on restart. 
I'm just wondering why I'm having these saving problems all of sudden.
nevermind about that, got it working thanks to this thread [http://ubuntuforums.org/showthread.php?t=1052769]("http://ubuntuforums.org/showthread.php?t=1052769:lol::lol:") :D:D
however, my system is still eating my VM usage.

---

### Post by ufuser1 on 2009-08-12
this is my top report in top with my new system monitor software.
```
top - 16:57:31 up 10 min,  2 users,  load average: 0.21, 0.29, 0.16
Tasks: 121 total,   2 running, 119 sleeping,   0 stopped,   0 zombie
Cpu(s):  1.5%us,  0.0%sy,  0.0%ni, 95.2%id,  3.3%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   2032840k total,   586620k used,  1446220k free,    30660k buffers
Swap:  2883656k total,        0k used,  2883656k free,   244200k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 3169 orlando   20   0  515m  80m  25m S    2  4.0   0:39.43 firefox            
 2469 root      20   0  263m  30m 8800 S    1  1.5   0:38.37 Xorg               
    1 root      20   0  4104  924  632 S    0  0.0   0:02.34 init               
    2 root      15  -5     0    0    0 S    0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/0        
    4 root      15  -5     0    0    0 S    0  0.0   0:00.00 ksoftirqd/0        
    5 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/0         
    6 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/1        
    7 root      15  -5     0    0    0 S    0  0.0   0:00.00 ksoftirqd/1        
    8 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/1         
    9 root      15  -5     0    0    0 S    0  0.0   0:00.01 events/0           
   10 root      15  -5     0    0    0 S    0  0.0   0:00.01 events/1           
   11 root      15  -5     0    0    0 S    0  0.0   0:00.00 khelper            
   12 root      RT  -5     0    0    0 S    0  0.0   0:00.00 kstop/0            
   13 root      RT  -5     0    0    0 S    0  0.0   0:00.00 kstop/1            
   14 root      15  -5     0    0    0 S    0  0.0   0:00.00 kintegrityd/0      
   15 root      15  -5     0    0    0 S    0  0.0   0:00.00 kintegrityd/1      
```

---

### Post by ufuser1 on 2009-08-16
bump
can someone  please tell me this is normal, because my system is running pretty well ;).

---

### Post by insane_alien on 2009-08-17
i'm pretty sure vm usage just indicates the amount that it is allowed to expand into. it doesn't mean it actually occupies that much at any time.

i've got vm sizes all over the shot and always have. just ignore it and use free -m for memory usage.

---

### Post by ufuser1 on 2009-08-22
> **insane_alien said:**
> i'm pretty sure vm usage just indicates the amount that it is allowed to expand into. it doesn't mean it actually occupies that much at any time.

i've got vm sizes all over the shot and always have. just ignore it and use free -m for memory usage.

I sure hope so. :D

---

### Post by r m h on 2009-08-30
Search is your Friend (SIYF), do it.

See also:  [http://linux-mm.org/ActualMemoryFootprint](http://linux-mm.org/ActualMemoryFootprint)

---

