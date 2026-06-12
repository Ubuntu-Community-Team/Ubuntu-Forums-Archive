---
title: "64 bit seems to use alot more ram then 32bit"
date: 2007-12-22
forum: x86 64-bit Users (Pre April '08)
---

### Post by markp1989 on 2007-12-22
i jus switched to 64bit gusty, and i have noticed that alot of ram seems to be getting used, when using 32bit it never used swap, and now with only a few programs running it is already using swap, is this normal or am i missing somthing, the output from top is bellow 


```
mark@mark-desktop:~$ top

top - 15:57:55 up 18:19,  3 users,  load average: 0.61, 0.70, 0.54
Tasks: 107 total,   2 running, 104 sleeping,   0 stopped,   1 zombie
Cpu(s): 10.0%us,  2.0%sy,  0.0%ni, 86.6%id,  0.0%wa,  0.3%hi,  1.0%si,  0.0%st
Mem:   2063560k total,  2042216k used,    21344k free,    56592k buffers
Swap:   489972k total,    38352k used,   451620k free,  1541160k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 6905 root      15   0  156m  38m  10m S  5.0  1.9  12:57.66 Xorg               
 7145 mark      15   0  499m  64m  20m S  4.7  3.2  19:58.36 deluge             
 7143 mark      15   0  239m  28m  11m R  1.3  1.4   0:01.59 gnome-terminal     
 7112 mark      15   0  253m  43m 9212 S  0.7  2.2   3:32.67 compiz.real        
 7147 mark      15   0 81056 2324 1356 S  0.7  0.1   4:21.85 conky              
 8480 mark      15   0  547m  82m  24m S  0.3  4.1   1:29.56 firefox-bin        
 8554 mark      15   0 18948 1316  972 R  0.3  0.1   0:00.09 top                
    1 root      18   0  5112 1964  572 S  0.0  0.1   0:00.79 init               
    2 root      11  -5     0    0    0 S  0.0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 migration/0        
    4 root      34  19     0    0    0 S  0.0  0.0   0:01.52 ksoftirqd/0        
    5 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 watchdog/0         
    6 root      10  -5     0    0    0 S  0.0  0.0   0:00.08 events/0           
    7 root      10  -5     0    0    0 S  0.0  0.0   0:00.01 khelper            
   25 root      10  -5     0    0    0 S  0.0  0.0   0:00.04 kblockd/0          
   26 root      20  -5     0    0    0 S  0.0  0.0   0:00.00 kacpid             
   27 root      20  -5     0    0    0 S  0.0  0.0   0:00.00 kacpi_notify       


```

---

### Post by gbesso on 2007-12-22
I think it's normal.

---

### Post by markp1989 on 2007-12-22
> **gbesso said:**
> I think it's normal.

ok, i would still like to know what is using up alot of ram, any one know what it is?

---

### Post by jordilin on 2007-12-22
can you run the following in the command line:
```
vmstat -a
```
and paste the results

---

### Post by jordilin on 2007-12-22
In any case, I see from top screenshot, that the cause could be the process called deluge and firefox-bin. Kill them and see what happens.

---

### Post by slavik on 2007-12-22
Mem:   2063560k total,  2042216k used,    21344k free,    56592k buffers
Swap:   489972k total,    38352k used,   451620k free,  1541160k cached

Note the end of the second line: 1.5GB are being used for caching. :)

---

### Post by markp1989 on 2007-12-22
> **jordilin said:**
> can you run the following in the command line:
```
vmstat -a
```
and paste the results

```
 vmstat -a
procs -----------memory---------- ---swap-- -----io---- -system-- ----cpu----
 r  b   swpd   free  inact active   si   so    bi    bo   in   cs us sy id wa
 0  0  38332  16392 1318056 644964    0    5  1129    73  563 1152 14  4 75  6
mark@mark-desktop:~$ 
```

---

### Post by Kilz on 2007-12-22
Using 38meg of swap is not large by any estimate.

What is the memory usage with Firefox (huge memory hog with multiple tabs open) and Bittorrent (deluge should be the name of the amount of ram it wastes) turned off.

---

### Post by markp1989 on 2007-12-22
> **Kilz said:**
> Using 38meg of swap is not large by any estimate.

What is the memory usage with Firefox (huge memory hog with multiple tabs open) and Bittorrent (deluge should be the name of the amount of ram it wastes) turned off.

here is top and vmstat -a right after i killed deluge and firefox-bin 

```
mark@mark-desktop:~$ top
top - 23:41:49 up  2:29,  3 users,  load average: 0.59, 0.44, 0.45
Tasks: 101 total,   2 running,  98 sleeping,   0 stopped,   1 zombie
Cpu(s):  5.3%us,  1.3%sy,  0.0%ni, 92.7%id,  0.0%wa,  0.0%hi,  0.7%si,  0.0%st
Mem:   2063560k total,  1962452k used,   101108k free,    23508k buffers
Swap:   489972k total,    38332k used,   451640k free,  1629112k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 6130 root      15   0  154m  65m 9096 S  3.3  3.2   5:37.76 Xorg               
 7646 mark      15   0  268m  30m  13m R  2.0  1.5   0:01.27 gnome-terminal     
 6538 mark      15   0  245m  35m 9104 S  1.3  1.8   1:46.68 compiz.real        
 6636 mark      15   0 81056 2324 1356 S  0.3  0.1   0:44.87 conky              
    1 root      18   0  5112 1968  572 S  0.0  0.1   0:00.77 init               
    2 root      11  -5     0    0    0 S  0.0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 migration/0        
    4 root      34  19     0    0    0 S  0.0  0.0   0:00.15 ksoftirqd/0        
    5 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 watchdog/0         
    6 root      10  -5     0    0    0 S  0.0  0.0   0:00.06 events/0           
    7 root      10  -5     0    0    0 S  0.0  0.0   0:00.01 khelper            
   25 root      10  -5     0    0    0 S  0.0  0.0   0:00.05 kblockd/0          
   26 root      20  -5     0    0    0 S  0.0  0.0   0:00.00 kacpid             
   27 root      20  -5     0    0    0 S  0.0  0.0   0:00.00 kacpi_notify       
  112 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 kseriod            
  138 root      15   0     0    0    0 S  0.0  0.0   0:00.04 pdflush            
  139 root      15   0     0    0    0 S  0.0  0.0   0:00.00 pdflush     



mark@mark-desktop:~$ vmstat -a
procs -----------memory---------- ---swap-- -----io---- -system-- ----cpu----
 r  b   swpd   free  inact active   si   so    bi    bo   in   cs us sy id wa
 0  0  38332  97220 1249316 633476    0    4   916    67  551 1072 13  4 78  5
```

---

### Post by thenewrhapsody on 2007-12-22
It looks as if your system is using all of your memory because it is! Linux is meant to manage your memory is a way where it uses as much memory as it can for cache. If you look closely you can see that you are using over 1.6 gigs as cache which speeds up your system because RAM is much much faster to access than your disk, just think of it as memory not used is memory wasted. Linux is nothing if not efficient when it comes to managing memory.

---

### Post by toupeiro on 2007-12-23
Another way to look at how your memory is used without the granularity of processes (just to get a better top level look at what the OS is doing with it) is to type: free -m



> free -m
             total       used       free     shared    buffers     cached
Mem:          2015       1561        453          0        200        729
-/+ buffers/cache:        631       1383
Swap:         2000          0       2000


---

### Post by markp1989 on 2007-12-23
> **toupeiro said:**
> Another way to look at how your memory is used without the granularity of processes (just to get a better top level look at what the OS is doing with it) is to type: free -m

```
mark@mark-desktop:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          2015       1999         15          0          3       1631
-/+ buffers/cache:        364       1650
Swap:          478         37        441

```

---

### Post by Ux64 on 2007-12-27
Or some times 64 bit is using more memory. Here is screenshot from system monitor. 

Using Firefox 64bit 2.0.0.11 & Gutsy Gibbon 64 bit 7.10 

[[IMG]http://picozilla.com/files/147293t64bit.jpeg[/IMG]](http://picozilla.com/en/147293/64bit.png.html)

That's right, Firefox is using 4.2 gigabytes! 

I wondered where I lost all system mememory before I noticed that. And system started to get really slow after all of 4 gb ram was used.

I'm happy to run 64 bit system. I guess there would have been a problem with 32 bit system. ;)

---

### Post by marx2k on 2007-12-27
> **Ux64 said:**
> Or some times 64 bit is using more memory. Here is screenshot from system monitor. 

Using Firefox 64bit 2.0.0.11 & Gutsy Gibbon 64 bit 7.10 

[[IMG]http://picozilla.com/files/147293t64bit.jpeg[/IMG]](http://picozilla.com/en/147293/64bit.png.html)

That's right, Firefox is using 4.2 gigabytes! 

I wondered where I lost all system mememory before I noticed that. And system started to get really slow after all of 4 gb ram was used.

I'm happy to run 64 bit system. I guess there would have been a problem with 32 bit system. ;)

Why i the world is FF using that much memory?!?!?

---

### Post by Kilz on 2007-12-27
> **marx2k said:**
> Why i the world is FF using that much memory?!?!?

Firefox is a known memory hog. The more tabs you have open and extensions loaded, the more it uses. This is the case in 64 and 32 bit.

---

### Post by rsambuca on 2007-12-27
4.2 GIGABYTES???  There is definitely something wrong with either FF or your install.

---

