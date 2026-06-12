---
title: "overclocking on foxconn m61pmx"
date: 2008-06-06
forum: x86 64-bit Users
---

### Post by rjfoo on 2008-06-06
i just bought a foxconn m61pmx am2/am2+ motherboard and 1150 sempron . how would i go about overclocking because i am running just kubuntu and to overclock it seems i have to use the foxone utility included with the board. the bios wont even allow me to access the cpu clock.  are there any alternatives or am i stuck at stock?

---

### Post by paulisdead on 2008-06-06
If you have to ask you probably shouldn't be doing it.

But anyways, you probably have some options to increase the front side bus or system bus.  The multiplier on the CPU is locked, so in order to increas the speed of the cpu, you have to increase the front side bus.  This can introduce other problems, since the front side bus has other busses tied to it.  At least these days you should only have to worry about the speed of the RAM going up when you raise the front side bus.

A problem when you start overclocking, is that things will get unstable.  To stabilize it, you add more voltage.  The problem there is increasing the clock speeds and adding voltage adds heat.  So overclocking is juggling the various speeds, voltages, and heat.

I do advocate overclocking on desktop machines, but you really need to rigorously test the overclock before relying on it.  Anything mission critical or requiring solid uptime shouldn't be overclocked.

If you really don't know how to do any of this, you seriously need to do some more research on it.  There are a lot of other forums and sites that are way better suited to overclocking than here.  Anandtech, HardOCP, and Futuremark are all good places to check out, and read their forums before you try to overclock anything.

---

### Post by rjfoo on 2008-06-06
thanks for the reply, i know how to overclock though. that wasnt the problem. the problem is that i cant change anything in the bios. i think the foxone overclocking utility its packaged with is supposed to be used to oc it but since im not using windows and its not working in wine so i was looking for an alternative.

---

### Post by paulisdead on 2008-06-07
> **rjfoo said:**
> thanks for the reply, i know how to overclock though. that wasnt the problem. the problem is that i cant change anything in the bios. i think the foxone overclocking utility its packaged with is supposed to be used to oc it but since im not using windows and its not working in wine so i was looking for an alternative.

You running the latest bios?  Sometimes they don't include overclocking options in the original BIOS.

---

### Post by rjfoo on 2008-06-10
is there another program like powertweak or something to overclock without using the bios? i tried powertweak but i couldnt get it going.

---

### Post by fjgaude on 2008-06-10
Many motherboards have you use the <ctrl>-F1 combo to get to see the features of the BIOS that can be changed. Know about anything about your board.

Another thing, that sempron chip may be locked by AMD, not to be oc'ed.

---

