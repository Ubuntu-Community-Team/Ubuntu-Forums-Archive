---
title: "Xorg/KDE using a lot of memory (maybe leaking memory)"
date: 2009-05-14
forum: x86 64-bit Users
---

### Post by hashinclude on 2009-05-14
I have Jaunty x86_64 installed on a Thinkpad t61, and I'm concerned about the (imo) excessive memory used by KDE and Xorg. 

Configured with:
[LIST]
[*]KDE 4.2.2 (stock kubuntu install)
[*]QT 4.5.0
[*]xserver-xorg 2.1.12-1
[*]nvidia-glx-173 173.14.16 (I couldn't get dual screen to work with higher glx versions).
[/LIST]

In an intense day, I sometimes have to kill all KDE stuff (logout, login) for the response time to come down to an acceptable level. For today's session I see

```

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                     
12981 root      20   0  403m 194m  19m S    0  9.9  75:53.19 Xorg                         
29601 hash      20   0  540m 117m  32m S    0  6.0   0:14.03 konqueror                    
24041 hash      20   0  724m  88m  28m S    0  4.5   4:16.15 kontact                      
29113 hash      20   0  539m  59m  33m S    0  3.0   0:14.47 kopete                       
23998 hash      20   0  697m  44m  20m S    0  2.3   2:04.71 plasma                       
24039 hash      20   0  757m  42m  11m S    0  2.2   0:10.10 amarok                       
23997 hash      20   0  546m  30m 7800 S    0  1.6   0:05.31 knotify4                     
23993 hash      20   0  329m  27m  11m S    0  1.4  21:17.44 kwin                         
24045 hash      20   0 66428  20m 5312 R    0  1.0   5:03.49 skype                        
23935 hash      20   0  409m  13m 7496 S    0  0.7   0:19.56 kded4                        
 3607 root      20   0  449m  10m 1312 S    0  0.6   2:56.28 webAccess                    
24062 hash      20   0  212m  10m 8312 S    0  0.6   0:03.19 klipper                      
24029 hash      20   0  619m 9.9m 7644 S    0  0.5   0:09.10 krunner  
```

(kopete was actually eating ~80 MB worth, I logged out, exit kopete, and started it up again, and now it's ~60 MB)

Anyone experienced something similar? How about 32-bit folks on a similar setup?

I was using 7.10 32-bit (KDE 3.5.x) before upgrading to 9.04, and I could work with no trouble for 2-3 weeks without logging out, then only because I needed to take the laptop home.

---

### Post by Yellow Pasque on 2009-05-14
How much RAM do you have?
Do you have a working swap area/file?
When your system starts slowing down, what does free show?
```
free -m
```

---

### Post by swobz007 on 2009-05-18
Hi

I have the same problem, through I thought I noticed you run on nvidia hardward and I thought it was linked to UXA and the intel drivers (see [https://bugs.launchpad.net/compiz/+bug/328232](https://bugs.launchpad.net/compiz/+bug/328232)). Actually whether composite screen/effets are on or off it's pretty much the same.

I was using jaunty 32b and I switch to 64b in the hope of getting ride of that problem :) But actually it still occurs. No clue what's going on.

Right now with nothing running, my computer shows :
Mem Use : 910/3790mb
Swap: 900/956mb

As request, the output of "free -m" is:
```

             total       used       free     shared    buffers     cached
Mem:          3790       3626        164          0         45       2666
-/+ buffers/cache:        914       2876
Swap:          956        899         57

```

Here is the Xorg  process
```

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
 3144 root      20   0 3302m 264m 106m S    2  7.0  31:45.76 Xorg

```
My conf :
- ibm T400
- ii  xserver-xorg-core                          2:1.6.0-0ubuntu14 
- Kde neon nightly builds
- Intel Driver almost nightly build

---

### Post by krazyd on 2009-05-18
I think there are two different issues here. One with [nvidia's drivers]("http://www.kdedevelopers.org/node/3959") and one with intel's as linked in that bug.

---

