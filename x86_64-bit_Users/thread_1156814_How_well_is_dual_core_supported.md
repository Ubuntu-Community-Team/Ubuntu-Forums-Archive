---
title: "How well is dual core supported?"
date: 2009-05-12
forum: x86 64-bit Users
---

### Post by slughappy1 on 2009-05-12
I was just curious how well a 64-bit dual core is supported? Specifically Intel Core 2 Duo. I have the 64-bit Ubuntu installed, but I want to know if it is using my dual cores properly.

---

### Post by Bucky Ball on 2009-05-12
AMD64 version is for any kind of 64bit processor (just like the i386 version is for AMD 32 bit processors). Ubuntu does not come in specific AMD or Intel versions for different processors. It's either 32 or 64 bit.

 I am running a Turion 64x2 dual core in my laptop (over a year) and brilliant. If it wasn't using the dual cores properly Canonical probably wouldn't go to the effort of developing and supporting it. But I am not a programmer who can give technical details and data of how the OS treats your two processors. :)

Try looking in the system monitor and you will find both are purring along nicely. If not, you have a problem unique to your machine.

---

### Post by drave on 2009-05-12
> **slughappy1 said:**
> I was just curious how well a 64-bit dual core is supported? Specifically Intel Core 2 Duo. I have the 64-bit Ubuntu installed, but I want to know if it is using my dual cores properly.

checkout htop. shows activity on all cores

---

### Post by djuke04 on 2009-05-12
I have a quad-core intel, and it seems to me like Ubuntu uses all of the cores without any issues.  System Monitor shows that across time each of the CPU's (identified as separate processors) gets used in varying percentages up to 100%.

---

### Post by kauboy on 2009-05-12
Actually, whether its a 32bit or a 64bit OS, they'll use all the available cores, as long as the OS is able to 'see' them all. But using a 64bit OS and 64bit softwares on a 64bit processor (no matter how many cores it has) has its own advantages. Like faster processing (because of better usage of available resources within the processor) and ability to handle tremendous amounts of RAM with ease. Simply put, an n-bit processor can address upto 2^n memory locations, assuming that memory is organized as bytes, for a 32-bit processor, you can address 2^32 Bytes = 4 GB. Whereas a 64-bit processor can theoretically access upto 2^64 Bytes = 16 EB!! But they usually can't handle that much in practice. Anything around (or more than) 4GB RAM, you must use a 64bit OS.

- Kaushik.

---

### Post by MMoudry on 2009-05-12
Actually this is a linux question and not Ubuntu question. From what I know about the Linux Kernel is scales very nicely up till 16 cores. Beyond that there are specific patches to the kernel scheduler for optimizing the performance on many-cored systems running thousands of processes. So in response to the original question, yes, ubuntu uses your two cores at maximum efficency, even in 64 bit.

---

### Post by automaton26 on 2009-05-12
I'm running Kubuntu AMD64 on a Core i7 920 (Quad core with Hyperthreading - muhahaha).

So I can see in the *System Monitor* application that all **8** cores are being used, and very nice it is too.

:P

---

### Post by 3Miro on 2009-05-12
Linux runs on 90% of the top 500 supercomputers in the world. There is a reason for that, mainly it can handle the power better than any other OS (some Unixes compete,but they are not as flexible and optimizable).

Believe me Linux is using both cores to maximum efficiency.

---

### Post by RoboNuggie on 2009-05-12
> **slughappy1 said:**
> I was just curious how well a 64-bit dual core is supported? Specifically Intel Core 2 Duo. I have the 64-bit Ubuntu installed, but I want to know if it is using my dual cores properly.

I think you can be rest assured that if you are using 64-bit on a dual core2, then both your cores will be utilized just fine. 

Saying that, I once overclocked my CPU too far, did a silly thing with the vcore and only one core was working..... lowered the O/C a bit, and they both showed again.....

Ubuntu 64-bit is just sweet with 4 gigs of Ram on a Intel E5200.... 8)

---

### Post by philinux on 2009-05-12
In a terminal use 

```
top
```

Then press key number 1. Both or more cores will show.

---

### Post by slughappy1 on 2009-05-13
Thanks everyone. I was reading stuff that was saying I had to use a specific kernel to get it to work properly.

---

