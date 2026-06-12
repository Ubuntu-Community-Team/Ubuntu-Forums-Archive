---
title: "Jaunty 9.04 - high CPU usage"
date: 2009-07-27
forum: x86 64-bit Users
---

### Post by hotbit on 2009-07-27
Hi All,

I have dual core proc. and just noticed Jaunty is eating my CPU. 
The graph in System Monitor / Resources shows over 60% on each CPU core in almost "naked" system.

Top shows:
Cpu(s): 44.4%us, 20.0%sy,  0.0%ni, 35.6%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st

PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
18730 mar    20   0  830m 198m  33m S   32 20.1   1:35.52 firefox            
31182 root      20   0  495m  50m  13m R   16  5.1   4:38.24 Xorg               
32479 mar    20   0  225m  23m  15m S   10  2.4   1:26.69 gnome-system-mo    
31273 mar    20   0 21888 1420  592 S    6  0.1   0:58.95 dbus-daemon        
24772 root      20   0 19112 1236  900 R    2  0.1   0:00.01 top                
24778 mar    20   0  208m 7020 5388 R    2  0.7   0:00.01 vino-server        
31281 mar    20   0 47080 6984 2344 S    2  0.7   0:50.66 gconfd-2           
31316 mar    20   0  248m  35m 7604 S    2  3.6   0:34.62 compiz.real        
31335 mar    20   0  211m  18m 9032 S    2  1.9   0:18.64 python             
    1 root      20   0  4104  620  540 S    0  0.1   0:00.71 init               
    2 root      15  -5     0    0    0 S    0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S    0  0.0   0:00.21 migration/0        
    4 root      15  -5     0    0    0 S    0  0.0   0:00.74 ksoftirqd/0        
    5 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/0         
    6 root      RT  -5     0    0    0 S    0  0.0   0:00.37 migration/1        
    7 root      15  -5     0    0    0 S    0  0.0   0:00.24 ksoftirqd/1        
    8 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/1        

In ubuntu 8.04 usually in similar circumstances CPU usage was like 20% on 1 core and 5 % on another. Just I feel it works slower.
With firefox, pidgin and skype on it takes over 90% on both cores. I have no idea what is wrong.

Any suggestions please?

---

### Post by hotbit on 2009-07-27
Thanks to
[http://ubuntuforums.org/showthread.php?t=1178055](http://ubuntuforums.org/showthread.php?t=1178055)

problem solved.

---

