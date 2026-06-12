---
title: "Memory Hogging"
date: 2006-11-18
forum: x86 64-bit Users (Pre April '08)
---

### Post by jjandrj6679 on 2006-11-18
Hi all. 
I have a problem with my ram not letting go of its resorces. When I fire linux up it sits around the 150Mb on idle but after only about 15 minutes of use, say one page of firefox, Nautalus was used to transfere data from one drive to another and to the trash,my ram idles at 40% about 380MB. The system info says that its using 38% in progs & 61% in cashe if that means anything.
It used to happen in Drapper but take about 2 hours, now with a fresh install of Edgy its about 15 mins. If I want to play on line I have to reboot first so its has as much as it need to run properly.

In Xp I used a program that automaticly clears/flushed the ram at regular intevals or when I needed to. Do I need something like that or does it need investigating further, coz there realy is a problem.

Yours
Josh

---

### Post by FluffyElmo on 2006-11-18
Have you tried running your online game or are you just assuming it won't work? Chances are it'll work fine.

Linux uses memory differently than XP does so it's hard to make a direct comparison. XP tends to use swap extensively even with RAM free while Linux generally grabs all available memory but gives it back when necessary.

Compared to Dapper you shouldn't be seeing much of a difference, unless you've gone from 32bit Dapper to 64bit Edgy? 64bit generally uses more RAM than 32bit but in exchange for better performance.

---

### Post by jjandrj6679 on 2006-11-19
Hi there
I have run the game Nexuiz 2.1 both on initial startup and after an hour or so. When the memory hits 380 it starts to get jerky sometimes, especialy under fast moving conditions, but from start up I can play for hours.

When you say "Linux generally grabs all available memory but gives it back when necessary." At what point, coz I left my pc running all nite on idle & it didn't give any back. So how does it work, as the longer I use my pc the more it cosumes and never gives back. 
In the system monitor, I added all the processes listed, (Not just mine) and it was 138 short of what the system was actually using.
Josh

---

### Post by RAOF on 2006-11-19
Linux gives memory back when something asks for more memory.  The "61% cache" number you report means that 61% of your memory is being used as disc-cache (and other forms of cache, too), speeding up harddrive access (among other things).  If any program asks for memory, some of this disc cache is just given to the program.   Basically, Edgy should be on 100% memory useage, 100% of the time.  Empty RAM is wasted RAM!

The problem with Nexuiz is interesting, and shouldn't be happening.  Can you give any more details about that?  It may well be unrelated to memory.

---

### Post by jjandrj6679 on 2006-11-20
Hi there
Humm Ive spent far too long with Windoze.
So what you are saying is, within linux its best to have the Ram maxed out to 100% all the time, any required ram would be given to the program I opened at the time. so if I opened a prog that would use 25% it would release 25% & continue using 75% as cache...Yes?

Ok so why does my pc start up with 20% Progs & 20% Cache and not 50/50 or 100%?
Also why do I startup using 153mb and end up after an hour with 380+mb?
Also when I close a prog it doesn't hold onto all of the ram, just a couple of megs at a time, but over time they add up to a lot.?
Just to test I fired up glxgears whilst opening firefox in two screens its now using 237mb and 100% CPU Usage & none of the Swap. If I close glxgears Im using 220mb & 3% CPU. If I shut everything down I get 168mb (minus Sys Mon 7.8mb) =160mb, thats 7mb differance in 5mins. Every time I start up & shut down Firefox it holds onto a few ram.
It all seems to be a bit strange, but I still have a windoze mentality I suppose

As to Nexuiz, I'll be happly playing away ON LINE, then it freezes (just like its does at the end of the game) then it unfreezes and I find myself slammed against a wall, then blown up, or even worse I've fallen of the map. Ths happens quite a lot when I havn't restarted the pc before playing. The more ram used the worse it seems to be.

Yours
Josh

---

### Post by FluffyElmo on 2006-11-20
Try using *top* instead of system monitor. From a terminal window just type *top*, then you can hit *M* to sort by memory usage (it sorts by CPU by default). You can also hit *s* and then enter a value in seconds (I use '1')to increase the sampling rate. I think system monitor is only showing a couple of numbers. Top will give you more detail.

There is most likely something happening with the game, but if you're not running Firefox while playing then I don't think that's it. When you experience a freeze run top right away (or leave it running while you play on a reduced sample rate) to see if any processes are using CPU or RAM.

It's of course possible you have a memory leak, some Firefox extensions have been known to be bad for this. Check this link [http://plugindoc.mozdev.org/faqs/memusage.html]("http://plugindoc.mozdev.org/faqs/memusage.html")for some details on Firefox memory usage.

In the "Things That Are Not Memory Leaks" section they describe what you're seeing though:
> 
Firefox Memory Usage Doesn't Always Go Down

This is generally not an issue, and does not represent a memory leak. Why? When Firefox is finished with memory, it releases it to its heap. However, operating system reports this memory as being in use, even though Firefox is not using it for anything. A common symptom of this is the amount of memory used by Firefox going up, but not coming down - instead staying constant. 

---

### Post by jjandrj6679 on 2006-11-20
Hi
Humm here is a copy of my TOP to see what you make of it.
```
josh@josh-desktop:~$ top

top - 20:11:00 up 21 min,  2 users,  load average: 0.06, 0.05, 0.06
Tasks: 105 total,   2 running, 103 sleeping,   0 stopped,   0 zombie
Cpu0  :  5.7%us,  0.9%sy,  0.0%ni, 92.9%id,  0.1%wa,  0.1%hi,  0.4%si,  0.0%st
Mem:   1025872k total,   515056k used,   510816k free,    65112k buffers
Swap:   514040k total,        0k used,   514040k free,   204372k cached

 PID USER       PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 5619 josh      15   0  139m  18m  10m R  6.6  1.9   0:05.18 gnome-terminal     
 4246 root      15   0 70604  23m 8132 R  2.3  2.4   0:19.18 Xorg               
 4782 josh      15   0 65348  10m 7196 S  0.7  1.1   0:02.12 metacity           
    1 root      16   0  2732  596  476 S  0.0  0.1   0:00.69 init               
    2 root      RT   0     0    0    0 S  0.0  0.0   0:00.00 migration/0        
    3 root      34  19     0    0    0 S  0.0  0.0   0:00.00 ksoftirqd/0        
    4 root      RT   0     0    0    0 S  0.0  0.0   0:00.00 watchdog/0         
    5 root      10  -5     0    0    0 S  0.0  0.0   0:00.01 events/0           
    6 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 khelper            
    7 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 kthread            
   10 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 kblockd/0          
   11 root      20  -5     0    0    0 S  0.0  0.0   0:00.00 kacpid             
   12 root      20  -5     0    0    0 S  0.0  0.0   0:00.00 kacpi_notify       
  100 root      10  -5     0    0    0 S  0.0  0.0   0:00.02 kseriod            
  137 root      20   0     0    0    0 S  0.0  0.0   0:00.00 pdflush            
  138 root      15   0     0    0    0 S  0.0  0.0   0:00.01 pdflush            
  139 root      25   0     0    0    0 S  0.0  0.0   0:00.00 kswapd0            
  140 root      20  -5     0    0    0 S  0.0  0.0   0:00.00 aio/0              
 1617 root      13  -5     0    0    0 S  0.0  0.0   0:00.00 ata/0              
 1619 root      17  -5     0    0    0 S  0.0  0.0   0:00.00 scsi_eh_0          
 1620 root      17  -5     0    0    0 S  0.0  0.0   0:00.00 scsi_eh_1          
 1839 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 khubd              
 1938 root      10  -5     0    0    0 S  0.0  0.0   0:00.03 kjournald          
 2014 root      15   0  2696  584  488 S  0.0  0.1   0:00.00 logd               
 2156 root      13  -4 11268 1440  376 S  0.0  0.1   0:00.22 udevd              
 2972 root      13  -5     0    0    0 S  0.0  0.0   0:00.00 shpchpd            
 3047 root      13  -5     0    0    0 S  0.0  0.0   0:00.00 kpsmoused          
 3177 root      20  -5     0    0    0 S  0.0  0.0   0:00.00 kgameportd         
 3464 root      16   0  7632 1008  508 S  0.0  0.1   0:00.00 mount.ntfs-3g      
 3467 root      16   0  7628 1000  508 S  0.0  0.1   0:00.00 mount.ntfs-3g      
 3470 root      15   0  7632 1008  508 S  0.0  0.1   0:00.00 mount.ntfs-3g      
 3604 dhcp      14  -2  8900  756  236 S  0.0  0.1   0:00.00 dhclient3          
 3652 daemon    15   0  4860  404  284 S  0.0  0.0   0:00.00 portmap            
 3823 root      16   0  2688  548  460 S  0.0  0.1   0:00.00 getty              
 3824 root      16   0  2692  552  460 S  0.0  0.1   0:00.00 getty              
 3825 root      16   0  2692  552  460 S  0.0  0.1   0:00.00 getty              
 3833 root      16   0  2692  552  460 S  0.0  0.1   0:00.00 getty              
 3836 root      16   0  2688  548  460 S  0.0  0.1   0:00.00 getty              
 3839 root      16   0  2692  552  460 S  0.0  0.1   0:00.00 getty   
``` 103 processes??? that seems a lot just to idle a pc. Linux is a completely differant animal to Xp. I am fairly fluent in Xp & have learnt to understand what process does what & whether there is a need fo it. So much so that I had created an Xp quick install disk that would get any pc up'n'runnin is 1/2hour with an istall size of 350 MB's. I even got it running quite quickly on a Pentium 166hz pc.. yes 166???

But as to what all these mean and whether I need them running is another matter.
I cant seem to get to the bottom of the list as I cant see all 105 processes running and its damn hard to copy/paste the info.. any advice?

I looked at the link, but to me unless I missed the point, revealed nout. I tryed to install the Leak Monitor Extension but its a windoze prog not linux??
It may discribe the problem but it doesn't explain how to solve it..does it?
JJ

---

### Post by RAOF on 2006-11-20
> **jjandrj6679 said:**
> ...
So what you are saying is, within linux its best to have the Ram maxed out to 100% all the time, any required ram would be given to the program I opened at the time. so if I opened a prog that would use 25% it would release 25% & continue using 75% as cache...Yes?

Ok so why does my pc start up with 20% Progs & 20% Cache and not 50/50 or 100%?...

1) Yes.
2) Because there's nothing (or very little) to cache yet.  It won't read random stuff into memory just to fill it :).

---

### Post by jjandrj6679 on 2006-11-21
Ok so as I use my pc the cache/ram fills up to 100% and then it regulates how much memory each prog gets?

seems a bit weird, wouldn't it be better to let the prog obtain the required amount of free ram then dump it back on closing? Instead of fighting for a bit of memory that is alredy being used. Or have I got it completely wrong?

---

