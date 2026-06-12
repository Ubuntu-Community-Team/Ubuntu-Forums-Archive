---
title: "Starcraft 2: Slow on Ubuntu 12.04"
date: 2012-04-30
forum: Wine
---

### Post by Neo40 on 2012-04-30
I decided to install 12.04 32bit last week-end and I found when I play Starcraft 2, I only get around 14 fps in medium resolution.

I was on Archlinux before and I was able to get easily 32 fps when playing with the same resolution. 

Anyone has the same problem or it is just me?

Thanks

CPU: AMD Phenom(tm) II X4 925 Processor × 4 
Memory: 4GB
Video card: GeFORCE GTS 250

---

### Post by pensadorlouco on 2012-06-17
I have a similar problem.  Most of the games I had were working fine under 11.10, but since I've made the upgrade to 12.04 the started to slow. Games such as Ryzom or even Teeworlds (who were running without problems on 11.10) now are too slow to play (Ryzom) ou keep skiping frames (Teeworlds).

I still haven't found a solution for that either. If anyone here knows what might it be, I'd appreciate to know.

---

### Post by ergo-proxy on 2012-06-18
> **Neo40 said:**
> I decided to install 12.04 32bit last week-end and I found when I play Starcraft 2, I only get around 14 fps in medium resolution.
 
I was on Archlinux before and I was able to get easily 32 fps when playing with the same resolution. 
 
Anyone has the same problem or it is just me?
 
Thanks
 
CPU: AMD Phenom(tm) II X4 925 Processor × 4 
Memory: 4GB
Video card: GeFORCE GTS 250
 
You might be having a problem with recognizing all cpu cores, try "switching" the main starcraft2.exe process to use only a single core (0). In diablo3 it makes miracles.

---

### Post by Neo40 on 2012-06-18
> **ergo-proxy said:**
> You might be having a problem with recognizing all cpu cores, try "switching" the main starcraft2.exe process to use only a single core (0). In diablo3 it makes miracles.

How can I do that?!

---

### Post by ergo-proxy on 2012-06-19
Check what it's the name of a main starcraft process, if it's for example Startcraft II.exe then do sometime like:
 
taskset -cp 0 `pidof Starcraft\ II.exe`

---

### Post by Dlambert on 2012-06-19
You should also try Unity2D. Maybe it's the eye candy of unity slowing you down.

---

### Post by Redshirt4 on 2012-06-20
You could try turning down your graphics settings. Wine, being an Emulator and such, will run the program slower than it's supposed to.

---

### Post by ergo-proxy on 2012-06-20
> **Redshirt4 said:**
> You could try turning down your graphics settings. Wine, being an Emulator and such, will run the program slower than it's supposed to.


***W**INE **I**s **N**ot an **E**mulator :]*

---

