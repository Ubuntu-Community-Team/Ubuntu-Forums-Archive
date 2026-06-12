---
title: "Is everything fixed on [Ubuntu 64-bit PC (AMD64)]  kernel-smp?"
date: 2006-03-02
forum: x86 64-bit Users (Pre April '08)
---

### Post by Hoffmann on 2006-03-02
Hi All:

I a previous posting I hear:

"One more bit of advice. If you have a dual-core AMD64 processor, do NOT use the SMP version of the kernel. It crashes like crazy. If you know what you're doing, compile your own SMP version of the kernel from the latest sources. It doesn't support everything Ubuntu/Kubuntu uses, but it works fine for my needs and it doesn't crash".

Since I will install Ubuntu 64-bit PC (AMD64) on Intel Pentiun D (EM64T) machine soon, could anyone, please, let me know it that problem is already fixed? I mean, can I run the SMP version of the kernel with no problem on my machine?

Thanks!
Hoffmann

---

### Post by stimpie on 2006-03-03
I am running the Ubuntu smp kernel and it is working fine.

One  issue I encountered was clock drift. This however was easily solved by adding the boot option "notsc" 

Another problem was that my system crashes when  I plug in my kvm switch with usb-hub. this however is happening on my old single core 32bit machine also.

---

### Post by Hoffmann on 2006-03-03
Hi stimpie,

Many thanks for reply. As soon as my Ubuntu CD arrives, I will install it, so.
Could you, tell me more about the boot option "notsc"? What does that mean? 

Best,
Hoffmann

---

### Post by claudio99 on 2006-04-11
Crashes likes hell here, dapper worse that breezy (breezy after a few hours, dapper will install but won't boot).

C.

---

### Post by Hoffmann on 2006-04-11
[QUOTE=claudio99]Crashes likes hell here, dapper worse that breezy (breezy after a few hours, dapper will install but won't boot).

C.[/QUOTE]

Hi Claudio99,

Since the beginning of my Ubuntu-64 bits, I have realized that it was a mistake. I got several problems. So, I installed Ubuntu-32, and all is working fine. My machine is a Intel core dual (EM64T), and I am using the smp kernel. So, I have both the CPUs running, and this is all I need.

I WON'T INSTALL THE 64-BIT 'STUFF' BACK!

Hoffmann

---

### Post by mariuss on 2006-04-11
I am running Ubuntu 64 SMP on a dual core AMD 64, and it never crashes. I had problems with the video driver, at some point it would start grabling the scree, but after installing the nvidia drivers it was fine.

Is it possible that the Intel 64 is not supported properly?

---

### Post by Hoffmann on 2006-04-11
[QUOTE=mariuss]I am running Ubuntu 64 SMP on a dual core AMD 64, and it never crashes. I had problems with the video driver, at some point it would start grabling the scree, but after installing the nvidia drivers it was fine.

Is it possible that the Intel 64 is not supported properly?[/QUOTE]

My Ubuntu-64 never crashes too. However, I think that the necessity of doing chroot some times, in order to 'build' an 32-bit enviromnet for running some applications doesn't deserve an effort. Instead, I did prefer a true 32-Ubuntu. Just after a 'better' 64 linux or windows be ready, I would think in installing it. A lot of things need to be done yet.
Hoffmann

---

### Post by 12345p on 2006-04-11
Heh. I always thought the crashing was caused by running vmare server (free version) and windows XP. But then, I've been avoiding installing the "latest" kernel because I would have to reinstall vmware. Maybe I should do it to see if my random crashing goes away. Thanks for the heads up!

---

### Post by Cashel on 2006-04-11
It works for me fine... 

$ uname -a
Linux wargod 2.6.15-20-amd64-k8 #1 SMP PREEMPT Tue Apr 4 18:03:46 UTC 2006 x86_64 GNU/Linux

This is from the repositories, you'll note the change from the breezy image (theres no -smp in the package name). I think its probably best to compile your own kernel, at least you'll know where your sources are but then I compile a lot of stuff because its fun for me :)

In any event, using the regular debian kernel howtos will make your kernel package manager friendly if your worried about it.. 

Cashel

---

### Post by mariuss on 2006-04-11
[QUOTE=Hoffmann]My Ubuntu-64 never crashes too ... A lot of things need to be done yet.
Hoffmann[/QUOTE]

Well, you are not running on AMD64, and Ubuntu-64 as far as I know is explicitely for AMD, not Intel. Am I worng?

Even the name of this forum says "AMD 64 Users"!

Marius

---

