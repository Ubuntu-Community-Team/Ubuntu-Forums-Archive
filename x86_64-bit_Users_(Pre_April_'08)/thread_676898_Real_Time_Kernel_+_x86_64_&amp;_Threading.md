---
title: "Real Time Kernel + x86_64 &amp; Threading"
date: 2008-01-24
forum: x86 64-bit Users (Pre April '08)
---

### Post by wawarren on 2008-01-24
I've just recently installed Ubuntu Studio with the Real Time Kernel, and I've got some questions. 

My "threaded" applications are not using the full potential of my machine as they have in Fiesty for so long now. By that, I mean I'm only seeing 2 of my 4 cores at work, but 4 "graphs" are present. To clarify, I'm doing 3D rendering, so I have x2 cores @ 0% and x2 cores @ 100% during processing.  dmesg suggests that CPU 0 through 3 are all loading . ie. (0 1 2 3 = x4 cpu) 

At first I thought perhaps the CPU usage window was inaccurate, but I rendered out a lot of images from the command line in Verbose mode using different variations of cores.  1, 2, 3, 4.  Anything over "2" shows zero improvment as far as speed goes, and this is just as the little graphs in my performance monitor (w/e it's called) displays. 

Naturally I should go back to generic kernel and be done with it right..   I will do that, but I'm curious if this could in "any" way be related to something else?

From my Googling.  

I've heard of somebody installing "Im-sensors" in order to get threading in their apps.  

and this quote in particular I find very interesting, but I've no clue how dated this is. 


> 1. this new kernel only works for 'one core' processors. For AMD dual core processors, only one core will be seen by the system. It still works (no xruns), but defeats the object for heavy audio projects...stay tune: as mentionned in other posts, Ubuntu Edgy might help a bit + the ubuntu.toine.net team is working on a new version of kernel which should support smp.

2. the last version of kernel in Ubuntu-musique is the kernel 2.6.17.6-rt7. Ubuntu-musique might install by default the previous version 2.6.15.26-rt21 (which is working fine for me). So if it is the case and that you want to have the last kernel available of Ubuntu-musique, go back to synaptic and check that the last kernel is installed. If not, mark it for installation, and apply.

 I have got to be using the most recent RT kernel, but maybe I missed a patch? 

Please let me know if you're familiar with this.   

Thanks

---

### Post by wawarren on 2008-01-24
Solved. 

Going back to the generic Kernel fixed this problem.  The RT Kernel which says it's SMP doesn't support threaded applications with my hardware, which I find strange.

dmesg | grep CPU shows them, so they're all there, but only 2 cores - or - 1 CPU is working under heavy loads in "threaded" apps like 3D rendering engines. (ie. Mental Ray)

You would think there's Audio professionals out there with x2 dual core Opterons that would've left me a trail on google or something, but nada.

---

### Post by dcstar on 2008-01-26
> **wawarren said:**
> Solved. 

Going back to the generic Kernel fixed this problem.  The RT Kernel which says it's SMP doesn't support threaded applications with my hardware, which I find strange.

dmesg | grep CPU shows them, so they're all there, but only 2 cores - or - 1 CPU is working under heavy loads in "threaded" apps like 3D rendering engines. (ie. Mental Ray)

You would think there's Audio professionals out there with x2 dual core Opterons that would've left me a trail on google or something, but nada.

I used to use the old "Low Latency" kernels and then started to use the "-rt" ones when the other stopped being built - what a disaster!, now I stick to the generic kernel for my base system (and the 100Hz "-system" kernels for my VMware Ubuntu VMs).

I don't know who gets a benefit from the -rt kernels, but it ain't me...........:(

---

