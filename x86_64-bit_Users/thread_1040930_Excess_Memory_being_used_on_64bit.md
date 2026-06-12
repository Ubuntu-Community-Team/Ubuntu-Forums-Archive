---
title: "Excess Memory being used on 64bit?"
date: 2009-01-16
forum: x86 64-bit Users
---

### Post by ihavenoname on 2009-01-16
I just recently switched to kubuntu x64. On this system by ram is getting to 1gb out 2gb usage very quickly. 
When I was using i386 I would hardly ever get above 500mb usage. That was in cases of severely heavy loads. I just got to 1.2gb of ram usage using openoffice, firefox(w/java plugin), dolphin and okular.  
Right now I have 1 tab of firefox open, and ksysguard(system monitor) and I am using 885mb of ram. It also doesn't just seem to be that linux is stretching itself to use as much ram as it can beacuse it has actually swapped about 5.1mb.  I am not really noticing slow down but what gives?

---

### Post by mgranet on 2009-01-16
Exact same issue here.

---

### Post by ihavenoname on 2009-01-16
> **mgranet said:**
> Exact same issue here.

do you have this problem with other distros or just (k/x)ubuntu?
This is really the first time I use x64, normally I just test it and go back but most blocker x64 issues are gone (all the ones I can think of actually, barring this one of course).

edit: also it seems that Xorg is increasing in ram quite fast.

---

### Post by Arup on 2009-01-16
x64 OS in general is made to use memory far more efficiently, simplistically speaking its because there are more bits to access memory, one of the reasons it can handle 4GB+ memory easily. OTOH, check with the TOP command which apps are consuming memory to an excess.

---

### Post by pansz on 2009-01-16
You should check which process is using more memory.

On my system, 64-bit uses less memory than 32-bit.

But generally, 64-bit program consumes 20-50% more memory in code-segment, so that level of increase is normal.

---

### Post by Kilz on 2009-01-16
One other thing to keep in mind is that unused memory in Linux is wasted memory.

---

### Post by stefangr1 on 2009-01-16
Can you post the output of the command "free"? Normally Ubuntu uses as much memory as is possible, either for system/user applications or for caching, so it is quite normal that a lot of RAM is used.

---

### Post by ihavenoname on 2009-01-16
Yes, I would understand if it was a mild increase in memory usage, but it just seems to me like Xorg keeps adding to the amount of ram it's using. It goes from 14mb to 145mb based on the apps I'm using. I'm not even using a compositor.

Here is the output of Free after 20minutes of using the computer (surfing the internet)

```
$
 free
             total       used       free     shared    buffers     cached
Mem:       2047952     951208    1096744          0      16964     300472
-/+ buffers/cache:     633772    1414180
Swap:      1959920          0    1959920

                    
```here is the output of top

```


  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
 5680 ag        20   0  805m 248m  41m S   23 12.4   3:59.02 firefox
 5096 root      20   0  474m  63m 5640 S   10  3.2   0:44.50 Xorg
 5551 ag        20   0  522m  45m  23m S    5  2.3   0:06.83 plasma
 5547 ag        20   0  179m  19m  13m S    1  1.0   0:01.70 kwin
 6661 ag        20   0  247m  26m  15m R    1  1.3   0:01.58 konsole
 1376 root      15  -5     0    0    0 S    1  0.0   0:00.32 ata/0
 4776 messageb  20   0 21780 1480  748 S    1  0.1   0:01.62 dbus-daemon
 5050 root      20   0 62900 2956 2288 S    1  0.1   0:00.98 NetworkManager
 5606 ag        20   0  156m  15m  10m S    1  0.8   0:10.04 knetworkmanager
 5683 ag        20   0 43224 3088 2268 S    1  0.2   0:00.06 gconfd-2
    1 root      20   0  4100  912  620 S    0  0.0   0:02.02 init
    2 root      15  -5     0    0    0 S    0  0.0   0:00.00 kthreadd
    3 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/0
    4 root      15  -5     0    0    0 S    0  0.0   0:00.04 ksoftirqd/0
    5 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/0
    6 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/1
    7 root      15  -5     0    0    0 S    0  0.0   0:00.02 ksoftirq

```

my user in this case is "ag".

Also, I understand that my computer actually using my ram is a good thing. But after enough time passes it goes beyond that and starts swapping. I think maybe I should test this in another distro and see what comes up.

---

### Post by Arup on 2009-01-16
Seven hours of running, surfing, programming, encoding, chatting etc.

top - 22:36:16 up  6:31,  2 users,  load average: 0.04, 0.10, 0.13
Tasks: 147 total,   1 running, 146 sleeping,   0 stopped,   0 zombie
Cpu(s):  1.0%us,  0.3%sy,  0.0%ni, 98.7%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   4043512k total,  2022968k used,  2020544k free,    73252k buffers
Swap: 11839864k total,        0k used, 11839864k free,   856984k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 5636 root      20   0  652m 229m  11m S    2  5.8  27:14.50 Xorg               
 6092 arup      20   0  272m  11m 8296 S    1  0.3   2:31.81 gkrellm            
15972 arup      20   0  816m 157m  30m S    1  4.0   1:04.30 firefox            
17941 arup      20   0 19100 1348  992 R    1  0.0   0:00.10 top                
 5995 arup      20   0  137m  14m 8640 S    0  0.4   2:11.29 metacity           
 6254 arup      20   0  549m 211m  26m S    0  5.4   8:03.31 opera              
    1 root      20   0  4100  916  620 S    0  0.0   0:01.12 init               
    2 root      15  -5     0    0    0 S    0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/0        
    4 root      15  -5     0    0    0 S    0  0.0   0:00.02 ksoftirqd/0        
    5 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/0         
    6 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/1        
    7 root      15  -5     0    0    0 S    0  0.0   0:00.00 ksoftirqd/1        
    8 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/1         
    9 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/2        
   10 root      15  -5     0    0    0 S    0  0.0   0:00.02 ksoftirqd/2        
   11 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/2

---

### Post by stefangr1 on 2009-01-16
Well, it does seem that quite a lot of RAM is used. I also have 2GB, and I have 1848768 free including cache. Even though my swap space is used sometimes, while some others is not. 

             total       used       free     shared    buffers     cached
Mem:       2075624    1150276     925348          0      25352     898068
-/+ buffers/cache:     226856    1848768
Swap:      1020088      74760     945328

It seems though, that your RAM usage excluding cache etc. is indeed at the higher end. It is very difficult to say, however, what that is caused by.

---

### Post by mgranet on 2009-01-16
```
me@Kubuntu:~$ uptime
 22:47:10 up  3:05,  1 user,  load average: 0.02, 0.08, 0.04
```
```
me@Kubuntu:~$ free -m                                     
             total       used       free     shared    buffers     cached
Mem:          2009       1272        736          0         57        582
-/+ buffers/cache:        632       1376                                 
Swap:        10997          0      10997
```                                 

```
me@Kubuntu:~$ top -d 1
                                                                                                                                                         
top - 22:47:43 up  3:06,  1 user,  load average: 0.01, 0.07, 0.04
Tasks: 124 total,   2 running, 120 sleeping,   0 stopped,   2 zombie
Cpu(s):  1.0%us,  1.4%sy,  0.0%ni, 97.1%id,  0.0%wa,  0.5%hi,  0.0%si,  0.0%st
Mem:   2057284k total,  1303036k used,   754248k free,    58804k buffers
Swap: 11261556k total,        0k used, 11261556k free,   596916k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
 5894 me        20   0  292m  51m  29m S    2  2.6   2:00.16 kwin
 7093 me        20   0 19100 1332  996 R    2  0.1   0:00.02 top
 5585 root      20   0  224m  71m  11m S    1  3.6   3:05.64 Xorg
 5900 me        20   0  472m  50m  22m S    1  2.5   1:59.73 plasma
    1 root      20   0  4100  908  616 S    0  0.0   0:01.04 init
    2 root      15  -5     0    0    0 S    0  0.0   0:00.00 kthreadd
    3 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/0
    4 root      15  -5     0    0    0 S    0  0.0   0:00.02 ksoftirqd/0
    5 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/0
    6 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/1
    7 root      15  -5     0    0    0 S    0  0.0   0:00.22 ksoftirqd/1
    8 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/1
    9 root      15  -5     0    0    0 S    0  0.0   0:00.06 events/0
   10 root      15  -5     0    0    0 S    0  0.0   0:00.06 events/1
   11 root      15  -5     0    0    0 S    0  0.0   0:00.00 khelper
   49 root      15  -5     0    0    0 S    0  0.0   0:00.00 kintegrityd/0
   50 root      15  -5     0    0    0 S    0  0.0   0:00.00 kintegrityd/1
   52 root      15  -5     0    0    0 S    0  0.0   0:00.00 kblockd/0
   53 root      15  -5     0    0    0 S    0  0.0   0:00.08 kblockd/1
   55 root      15  -5     0    0    0 S    0  0.0   0:00.00 kacpid
   56 root      15  -5     0    0    0 S    0  0.0   0:00.00 kacpi_notify
  166 root      15  -5     0    0    0 S    0  0.0   0:00.00 cqueue
  170 root      15  -5     0    0    0 S    0  0.0   0:00.00 kseriod
  220 root      20   0     0    0    0 S    0  0.0   0:00.00 pdflush
  221 root      20   0     0    0    0 S    0  0.0   0:00.12 pdflush
```

What's with the zombies? How do I find out what process that is? System manger shows nothing.

---

### Post by Arup on 2009-01-16
Zombies are residual processess which are still around even after the program has been closed.0 Zombies means its very good, nothing to worry about.

---

### Post by mgranet on 2009-01-16
> **Arup said:**
> Zombies are residual processess which are still around even after the program has been closed.0 Zombies means its very good, nothing to worry about.

Um, is "0 Zombies" a typo?

---

### Post by movieman on 2009-01-17
> **mgranet said:**
> Um, is "0 Zombies" a typo?

Zombies should have released all their resources and just be waiting for their parent to 'shoot them in the head', so aren't likely to be a problem. The only memory they're likely to be using is a few kernel structures.

---

### Post by mgranet on 2009-01-17
> **movieman said:**
> Zombies should have released all their resources and just be waiting for their parent to 'shoot them in the head', so aren't likely to be a problem. The only memory they're likely to be using is a few kernel structures.

Thanks.

---

