---
title: "High Memory Usage"
date: 2009-03-12
forum: x86 64-bit Users
---

### Post by lynwode on 2009-03-12
Hi,
I have been trying to install Oracle 11g on Hardy Heron, AMD64 3600, 2GB Ram. However when the install gets to the linking stage the machine sits there churning away for hours (I left it 2 days and still going). I killed the box and have restarted and all looks ok in the logs. I, by chance, did a top and found that I am using 90+% of the 2GB of memory. All that is running is Gnome, Firefox and a couple of terminal windows. This combined is probably no more than 200MB. This seems very strange and I guessing that is why the Oracle install is taking for ever. 

So here is my question, can anyone help me diagnose what may be causing this memory to be chewed up. below is the output of top.

Cheers,
Tim.

top - 20:53:02 up 10:02,  6 users,  load average: 0.49, 0.57, 0.65
Tasks: 180 total,   2 running, 177 sleeping,   1 stopped,   0 zombie
Cpu(s): 14.1%us,  0.5%sy,  0.0%ni, 85.5%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   2062844k total,  2034176k used,    28668k free,    33552k buffers
Swap:  4194296k total,      276k used,  4194020k free,  1033296k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                                                                                             
14570 lynwode   20   0 71648  21m 7848 S   26  1.1  25:08.18 npviewer.bin                                                                                                        
15333 root      20   0  406m  44m  12m R    3  2.2   3:54.43 Xorg                                                                                                                
15916 oracle    20   0  523m  85m  26m S    1  4.3   0:27.83 firefox                                                                                                             
15670 oracle    20   0  277m  57m  33m S    1  2.9   0:14.31 compiz.real                                                                                                         
15903 oracle    20   0 18992 1320  932 R    1  0.1   0:02.54 top                                                                                                                 
 7041 root      20   0  415m  82m  13m S    1  4.1  27:16.36 Xorg                                                                                                                
15749 oracle    20   0  253m  23m  11m S    1  1.2   0:01.83 gnome-terminal                                                                                                      
 7395 lynwode   20   0  290m  24m  13m S    0  1.2   0:06.11 gnome-panel                                                                                                         
 7463 lynwode   20   0  269m  48m  25m S    0  2.4   9:07.07 compiz.real                                                                                                         
15245 lynwode   20   0  262m  25m  11m S    0  1.3   0:01.02 gnome-terminal                                                                                                      
15512 oracle    20   0  251m  11m 8816 S    0  0.6   0:00.60 gnome-settings-                                                                                                     
15611 oracle    20   0  131m 3092 1808 S    0  0.1   0:01.29 gnome-screensav                                                                                                     
    1 root      20   0  4020  876  592 S    0  0.0   0:01.19 init

---

### Post by Yellow Pasque on 2009-03-12
Can you post the output of:
```
free -m
```

---

### Post by lynwode on 2009-03-12
total       used       free     shared    buffers     cached
Mem:          2014       1995         19          0         34        990
-/+ buffers/cache:        970       1044
Swap:         4095          0       4095

---

### Post by Yellow Pasque on 2009-03-12
Over half you RAM is free (look at the buffers line to see your free RAM). I don't see an issue there.
It sounds more like a problem with the Oracle install.

---

### Post by lynwode on 2009-03-12
Ok I now really confused. The output from free -m shows that there is a total of 2014 and used 1995. In my book thats 19 free. 
What does the buffers mean?

---

### Post by boof1988 on 2009-03-12
> **lynwode said:**
> Ok I now really confused. The output from free -m shows that there is a total of 2014 and used 1995. In my book thats 19 free. 
What does the buffers mean?

Hopefully someone else can explain about the buffers.

I just wanted to recommend using *htop* for finding out where your memory is being used.  It will show (using color coding) how much memory is being used for each (used, buffers & cache).  That way there there is no question about what is using any memory.  I don't use *top* anymore because the display is not as easy for me to read as *htop*'s display.

Here's a [link to htop's website](http://htop.sourceforge.net/).

---

### Post by in5urg3n7 on 2009-03-12
Lynwode,

Can you grep if there is any oracle background process that is running? How far did the Oracle install go before you canceled it?

---

### Post by insane_alien on 2009-03-12
the buffers and cache bit shows you waht is used by applications, the rest of it is filled by cache and buffers.

cache is when the OS copies certain files to RAM to improve response times, it can be deleted at anytime with no ill effects. the cache will expand to use all aavailable RAM in order to speed up your computer, it has no(negligble at worst) performance hit but plenty of performance benefits. it is normal for this to occupy most of your RAM.

buffers are files waiting to be fed into the processor or written to disk, these cannot be deleted at anytime and must have the actions carried out then deleted.

RAM used for cache is essentially free ram, applications have priority over it and it speeds up your system.

unused RAM is wasted RAM.

---

### Post by lynwode on 2009-03-12
in5urg3n7,
Oracle install did not complete as I killed it after 2 days of trying to link. There are no Oracle processes running.

---

### Post by lynwode on 2009-03-12
Ok sounds like my theory of memory being chewed up was a load of horse manure. 

Anyone have any ideas of why the Oracle linking should run for ever locking up the machine?  Anyone please help this is killing me and has been for months:(

---

### Post by lynwode on 2009-03-14
Ok, Me dumbo.

I have solved the issue with the Oracle install.... 
As per another post I had created a new script for gcc-4.2 that added the switch to compile 32bit. Unfortunately in my hast I had managed to point the script back to itself instead of the actual gcc-4.2. So it was looping and looping and thus ran for ever. Once fixed all worked straight out the box.

Thanks.
Tim.

---

