---
title: "Kernel for AMD64 is now Generic"
date: 2006-10-11
forum: x86 64-bit Users (Pre April '08)
---

### Post by mrfelker on 2006-10-11
I wondering if anybody knows why the AMD64 kernel has been deprecated and replaced with kernel 2.6.17-10-generic?  I am running Kubuntu if that makes any difference.  Have I lost any functionality?

Marty Felker:confused:

---

### Post by aeon on 2006-10-11
Noticed the same thing on my edgy install when i updated, don't know about the effect loss, if any, but the system feels a bit sluggish afer the update..
 
Still, i guess that's what you get for running a bunch of alpha and beta software :rolleyes: 

Tried running off my 2.6.16-vanilla, but that bl0rked up my x-server (xorg7.1/aiglx), so unless i compile a new kernel, i guess i'm stuck in genericland..

Well, the latest stable build is 2.6.18 so i guess there'll be an updated vanilla x86_64 kernel in a week or so..

My 0.02c

---

### Post by incubus on 2006-10-11
If I remember correctly, I think it's a general plan of developers to reduce their workload. Instead of supporting many kernel versions, they want to have just a generic one for each platform. I may be wrong.

incubus

---

### Post by earthfall on 2006-10-11
Incubus may be right. Someone mentioned that the performance gain by branching kernel version is almost neglectable compared to the application optimization.

---

### Post by John.Michael.Kane on 2006-10-11
incubus is spot on. endusers will have only one kernel option.

---

### Post by kleeman on 2006-10-12
There was a long discussion on this issue on the developers list with benchmarks done to see whether running a generic kernel caused a performance hit. mdz (Matt Zimmerman) concluded that the performance change was negligible. My impression was however that the benchmarking was not comprehensive however I have noticed little change on my edgy install....

---

### Post by incubus on 2006-10-12
This is just worth 2 cents, but I think most people who would really notice and be bothered by the difference are able to compile their own kernel in the first place. : )

That said, I'm using the generic kernel and I can't tell the difference. I guess I've been too busy lately.

incubus

---

### Post by prince_niceguy on 2006-10-13
yup... those who are so particular about their kernel will know how to compile the same... I did to mine. I compiled the latest version .18 for K8 :D

---

