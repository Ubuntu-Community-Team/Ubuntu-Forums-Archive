---
title: "More than 8 cores"
date: 2008-10-31
forum: x86 64-bit Users
---

### Post by srlietzx on 2008-10-31
I need a way to enable the kernel to see more than 8 cores. Ive never in my life complied a kernel and am a complete and total linux newb. Is there any easy way of doing this?

---

### Post by insane_alien on 2008-10-31
not really as its the kernel that interfaces with the hardware.

although i do think ubuntu should be compiled with support for more than 8 cores now that we are well and truely in the multicore era.

64 cores would be a good value i think.

---

### Post by xzero1 on 2008-10-31
There may be a way to configure at linux at bootime using a kernel parameter.
See [http://kernelnewbies.org/Linux_2_6_27#head-30ac00cf04bdd369c6fde636d99f8781f5b7f273](http://kernelnewbies.org/Linux_2_6_27#head-30ac00cf04bdd369c6fde636d99f8781f5b7f273)

Under Architecture specific (IA64), kernel 2.6.27 allows up to 4096 cpus.

---

### Post by srlietzx on 2008-10-31
Anyone know if 8.10 will come with more than 8 core support?

---

### Post by soxs on 2008-10-31
I am not sure about it, but I thought AMD64 kernerl gets compiled for max of 64 cpus atm (or was it 16??). But the number of cores it spports should be beyond 8..

---

### Post by srlietzx on 2008-10-31
I checked it, its only configured for 8 out of the gate...

---

### Post by soxs on 2008-10-31
> **srlietzx said:**
> I checked it, its only configured for 8 out of the gate...

Source plx, I just want to see it as I was sure I read about it about 8 weeks ago...

EDIT: 
Maybe you can try the server kernel, this may be the one I thought to have support for more than 8 cores..

---

### Post by jespdj on 2008-11-01
> **xzero1 said:**
> There may be a way to configure at linux at bootime using a kernel parameter.
See [http://kernelnewbies.org/Linux_2_6_27#head-30ac00cf04bdd369c6fde636d99f8781f5b7f273](http://kernelnewbies.org/Linux_2_6_27#head-30ac00cf04bdd369c6fde636d99f8781f5b7f273)

Under Architecture specific (IA64), kernel 2.6.27 allows up to 4096 cpus.
But that is ofcourse only relevant if you have an IA64 CPU, which you most likely do not. The IA64 architecture is only implemented on Intel's [Itanium](http://en.wikipedia.org/wiki/Itanium) processors, which are used in big and expensive servers, and which are not available for desktop PCs.

Note that IA64 is something completely different from [x86-64](http://en.wikipedia.org/wiki/X86-64), which are the 64-bit extensions of the x86 architecture.

*edit*

However, on that same page, under the **x86** architecture, it also says:
> Allow up to 4096 cpus: NR_CPUS to 4096 and MAX_NUMNODES to 512

---

