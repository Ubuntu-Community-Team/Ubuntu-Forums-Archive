---
title: "32bit Intel... Can i install Ubuntu 64bit ?"
date: 2007-10-19
forum: x86 64-bit Users (Pre April '08)
---

### Post by vietunion on 2007-10-19
Hi All

First, sorry for my english

I have install Ubuntu 64bit ( 7.10)  on my PC ( AMD 64, 4000+ ) and run very good

I have Laptop Dell Inspiron 9200 ( Centrino 1.6, 32bit), and i don't want download Ubuntu 7.10 ( for 32bit ), so, can i install Ubuntu64bit on intel 32bit ?

Sorry my english :-)

Thanks

---

### Post by 505 on 2007-10-19
Very short answer: no.

---

### Post by FredB on 2007-10-19
> **vietunion said:**
> Hi All

First, sorry for my english

I have install Ubuntu 64bit ( 7.10)  on my PC ( AMD 64, 4000+ ) and run very good

Kinda logical ;)

> I have Laptop Dell Inspiron 9200 ( Centrino 1.6, 32bit), and i don't want download Ubuntu 7.10 ( for 32bit ), so, can i install Ubuntu64bit on intel 32bit ?

Sorry my english :-)Sorry, you'll have to download 32 bits ISO.

If a 64 bits CPU can run both 32 and 64 bits distro, a 32 bits CPU will only run 32 bits distro.

> Thanks

You're welcome

---

### Post by Yellow Pasque on 2007-10-19
Are you sure your Intel processor doesn't support 64-bit? What model is it?

The distribution is named AMD64, but it will work on recent Intel chips too, because Intel copied the 64-bit extensions from AMD.

---

### Post by vietunion on 2007-10-19
Thanks 505, FredB and Temüjin

It seem i have to download Ubuntu 32bit :-)

@Temüjin: My Dell Inspiron is 32bit ( Intel Pentium M 1.6 GHz )

Thanks Again

---

### Post by ashlakim on 2007-10-20
Before that how can i check whether my processor is 32 bit or 64 bit? I only know Im running on Ubuntu 32bit.

---

### Post by FredB on 2007-10-21
> **ashlakim said:**
> Before that how can i check whether my processor is 32 bit or 64 bit? I only know Im running on Ubuntu 32bit.

For intel :

[http://en.wikipedia.org/wiki/List_of_Intel_microprocessors#64-bit_processors:_Intel64_-_NetBurst](http://en.wikipedia.org/wiki/List_of_Intel_microprocessors#64-bit_processors:_Intel64_-_NetBurst)

and for AMD :

[http://en.wikipedia.org/wiki/AMD64](http://en.wikipedia.org/wiki/AMD64)

If you want to have more info - and help us, install lshw (a hardware lister) ; in synaptic, search for lshw (2 packages, with one ending with "gtk"). After you installed it, in a console type :

```
sudo lshw-gtk 
```

You'll get a box with hardware info. Click on computer, and then on every option.

Here is for example my Sempron3100+ (K8 - 64 bits core) :

> 
product: AMD Sempron(tm) Processor 3100+
vendor: Advanced Micro Devices [AMD]
bus info: cpu@0
version: AMD Sempron(tm) Processor 3100+
slot: Socket 754
size: 1800MHz
capacity: 4GHz
width: 64 bits
clock: 200MHz
capabilities:
    mathematical co-processor,
    FPU exceptions reporting,
    wp,
    virtual mode extensions,
    debugging extensions,
    page size extensions,
    time stamp counter,
    model-specific registers,
    4GB+ memory addressing (Physical Address Extension),
    machine check exceptions,
    compare and exchange 8-byte,
    on-chip advanced programmable interrupt controller (APIC),
    fast system calls,
    memory type range registers,
    page global enable,
    machine check architecture,
    conditional move instruction,
    page attribute table,
    36-bit page size extensions,
    clflush,
    multimedia extensions (MMX),
    fast floating point save/restore,
    streaming SIMD extensions (SSE),
    streaming SIMD extensions (SSE2),
    fast system calls,
    no-execute bit (NX),
    multimedia extensions (MMXExt),
    fxsr_opt,
    64bits extensions (x86-64),
    multimedia extensions (3DNow!Ext),
    multimedia extensions (3DNow!),
    up,
    pni,
    lahf_lm,
    CPU Frequency scaling


If you have   "64bits extensions (x86-64)" in the list, you have a 64 bits processor. If not, a 32 bits processor.

Hope I helped ;)

---

