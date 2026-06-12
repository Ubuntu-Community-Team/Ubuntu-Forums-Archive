---
title: "Seeing both cores in System Monitor"
date: 2006-06-29
forum: x86 64-bit Users (Pre April '08)
---

### Post by hemes on 2006-06-29
Hey,

I have an AMD 3800+ X2 with the i386 kernal and, in the system monitor I only get one reading.  It is not difficult to get it up to 100% but in windows I have to try very hard to get to 100% and have two separate readings (one for each core).  I have a feeling that linux is not using the processor to its full potential or doesn't even know its got two cores??

Anyone know the full story?

Thanks,
Brett

---

### Post by Casey on 2006-06-29
The 386 kernel doesn't support multiple cores.  

You can install linux-686 through synaptic and then reboot to get multiple-core support.

---

### Post by hemes on 2006-07-05
what is the difference between the 686 and k7?  and smp?   

I did some searching and it seems I should install the k7-smp kernal... is this not correct?

Thanks,
Brett

---

### Post by hajk on 2006-07-05
Well, you're asking this question in the 64-bit subforum, so if you want to make full use of your 64-bit AMD dual-core processor, then you should install the amd64-k8 kernel (which is configured for SMP).

You have already noticed that Macromedia's Flash is not available in 64-bit (yet), but there are already a few early free flash players around -- like the SWF project. Just search for the string "SWF" in Synaptic (Description and name), and you'll see lots of 64-bit flash libraries and a mozilla plugin. These don't have the full functionality of Macromedia Flash yet, but at least they allow me to do my banking affairs on-line on the bank's web pages using flash. 

If you need full Flash functionality, then you might consider installing the amd64-k7 kernel -- it's 32-bit and also configured for SMP. You won't notice much difference in speed in practice, unless you're heavily into graphics work.

---

