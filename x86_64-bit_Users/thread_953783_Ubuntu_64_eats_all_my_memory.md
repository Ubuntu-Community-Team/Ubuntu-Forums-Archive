---
title: "Ubuntu 64 eats all my memory"
date: 2008-10-20
forum: x86 64-bit Users
---

### Post by josir on 2008-10-20
Hi folks, 
this is the first time I am installing a 64bits Ubuntu and I would like to ask for help about a memory problem.

Dell Vostro 200 / Pentium(R) Dual  CPU  E2160  @ 1.80GHz
Linux josir-desktop 2.6.24-21-generic #1 SMP Mon Aug 25 16:57:51 UTC 2008 x86_64 GNU/Linux

Installation runs smoothly and all drivers were recognized. But I notice that this machine became very slow when I opened several programs. After some digging, I discover that the swap was being used and usual programs are consuming a lot of memory. Top example:

Mem:   1018480k total,   925380k used,    93100k free,    10728k buffers
Swap:  1951888k total,    44952k used,  1906936k free,   394260k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM   COMMAND            
 5408 root      20   0  483m  80m 8472 S    5  8.1   Xorg               
 8680 josir     20   0  483m  91m  26m S    1  9.2   firefox            
 5662 josir     20   0  144m 6280 3552 S    0  0.6   pulseaudio         
 5789 josir     20   0  216m  24m 8568 S    0  2.5   compiz.real        
 8658 josir     20   0  265m  26m  12m S    0  2.7   gnome-terminal 

Notice that Xorg is consuming 483m!! 
Is this normal for a 64bits machine ?

Thanks in advance,
Josir

---

### Post by philinux on 2008-10-20
Try using

free -m

---

### Post by josir on 2008-10-20
Thanks for replying philinux but the memory stays at the same stage with the free -m command.
Josir

---

### Post by cariboo on 2008-10-20
From your post:

> PID USER PR NI VIRT RES SHR S %CPU %MEM COMMAND
5408 root 20 0 483m 80m 8472 S 5 8.1 Xorg
8680 josir 20 0 483m 91m 26m S 1 9.2 firefox 

IF you look closely you see that Xorg is using 483Mb of virtual memory. I quoted from man top concerning virtual memory

> VIRT  --  Virtual Image (kb)
          The  total  amount  of virtual memory used by the task.  It includes
          all code, data and  shared  libraries  plus  pages  that  have  been
          swapped out.

If you look at your listing Xorg is using 8.1% of your ram or about 80Mb

Jim

---

### Post by josir on 2008-10-20
Thanks for replying cariboo907 but a XOrg on a regular machine uses at most 100Mb (Virtual) - I have several machines here with Compiz and tons of screenlets and it took 150Mb at maximum.

This machine has compiz but with no visual effect. 

Notice that Firefox waste another 400Mb. And the gnome-terminal another 400Mb !!!

What I am trying to say is: this problem is system-wide and not a specific application problem.

---

### Post by wangmaster on 2008-10-20
you have 1gb ram.  44MB is swapped.  That's not too bad.  Look more closely at your memory utilization, I believe philinux was trying to make a point with free that you missed.

> Mem: 1018480k total, 925380k used, 93100k free, 10728k buffers
Swap: 1951888k total, 44952k used, 1906936k free, 394260k cached

1018480-394260=624220.  That's actually how much memory you have free.  I tend not to subtract buffers (but free does) because not all buffers are dynamic and thus you can't shrink buffer memory necessarily to get more physical memory.  However, given that you are not using all your memory.  Linux/Unix OSes use memory for cache.  "free memory is wasted memory"

Now the virtual size of your X and firefox processes are a bit large, but virtual size is not how much memory your app is using, and can vary depending your X server configuration, X screen size, modules loaded, etc etc.

There's nothing wrong with processes taking a HUGE VIRT size.  There is a problem if you have processes with lots of VIRT memory, and lots of RES memory AND you're swap thrashing.

Given that you're only swapping 40some K, your performance problem is not likely a result of swap thrashing.  That's not that much memory in swap.  However if swap is an issue, you'll want to tune swappiness since you do have enough free memory to fit all your process images in RAM.  google for swappiness to understand how to tune swappiness and what criteria to use.

---

### Post by josir on 2008-10-20
People, I worked with more than 10 ubuntu machines daily and I am used to the memory use. The scenario I post was the startup. When I load Eclipse, VirtualBox, etc. the machine got really slow. The Windows zealots have already started to joke on me :(((

My point is: in a 386 Ubuntu machine, I got 300Mb after a fresh boot and machine flies. With 64bits, I got 900Mb with THE SAME applications loaded.

What I want to know: Did I install something wrong or this is a tipical 64bits memory schema ?

Thanks for your support.
Josir.

---

### Post by wangmaster on 2008-10-20
> **josir said:**
> People, I worked with more than 10 ubuntu machines daily and I am used to the memory use. The scenario I post was the startup. When I load Eclipse, VirtualBox, etc. the machine got really slow. The Windows zealots have already started to joke on me :(((

My point is: in a 386 Ubuntu machine, I got 300Mb after a fresh boot and machine flies. With 64bits, I got 900Mb with THE SAME applications loaded.

What I want to know: Did I install something wrong or this is a tipical 64bits memory schema ?

Thanks for your support.
Josir.

64-bit memory structures do indeed suffer from additional overhead. Whether the bitness contributes to exactly what you're seeing I'm not sure.  For example, here's my Xorg and firefox-bin:
 6071 root      20   0  899m  50m  10m S   32  1.3   1:26.90 Xorg     
 7829 dopey     20   0  190m  89m  20m S    6  2.3   0:36.82 firefox-bin

So pretty high as well.  Here's the X on my 64-bit gentoo box:
 7907 root      20   0  766m  51m  13m S    0  1.3  16:28.63 X

64-bit windows likes to use more memory than 32-bit windows as well :)

---

### Post by patrickballeux on 2008-10-20
To have a more accurate view (or nearer to the Windows view), use the System Monitor (in System - Administration).  It will show you process with the amount of real memory used.

"top" is good, but can be confusing...  And yes, 64bits softwares use more memory because of the 64bits architecture.  It can use more memory, but it should run faster (this more visible in CPU intensive application live transcoding a video for example...)

Just to give you an example:  I have a Java application that when run in my 32bits/512meg-Ram takes around 60 megs of memory and 50 megs of that memory is for caching purpose.

In my 64bits/2gigs computer, the same software will use 100-120megs of real memory in a 250-300 megs of cache...

It all depends on how much memory you have and the architecture so you cannot compare memory usage between a 32bits and 64bits system.  

I think that Vista is doing the same, it uses some memory as cache to make the system run (cough!) faster and smoother...

---

### Post by josir on 2008-10-21
Thank you folks. That's the information that I am looking for. 

In fact, I should read the second column memory. It shows more similar values comparing to 32bits systems.

And I agree with you, in small tests that I did, certain memory intensive processes run faster.

Summary: If you are going to use a 64bit SO, use at least 2Gb RAM, which is cheap even on third-world countries like mine :)

PS: I've already answered to the Windows zealots. Here is my answer: I have the freedom to install this 64bits OS, now go to your manager and persuate him to buy a 64bits Windows....

---

