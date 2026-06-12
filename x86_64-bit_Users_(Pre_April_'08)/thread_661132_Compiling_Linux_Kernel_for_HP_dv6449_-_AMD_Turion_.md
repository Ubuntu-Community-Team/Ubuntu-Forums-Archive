---
title: "Compiling Linux Kernel for HP dv6449 - AMD Turion 64 X2"
date: 2008-01-07
forum: x86 64-bit Users (Pre April '08)
---

### Post by rahul_s on 2008-01-07
I have downloaded Linux Kernel 2.6.23.12 for my HP dv6449 laptop. I am trying to configure it to run on my lappie.

The specs are as follows:
AMD Turion 64 X2 processor
2 gigs of RAM
160 gigs of SATA

I am typing make xconfig/menuconfig to configure a kernel... where do I make the required changes to see to it that the correct processor is selected

I have had a previous error: kernel panic - kernel not syncing when some knowledgable people told me that I am not selecting the right kernel

Hoping some help... thanks in advance

Rahul

---

### Post by John.Michael.Kane on 2008-01-07
> **rahul_s said:**
> I have downloaded Linux Kernel 2.6.23.12 for my HP dv6449 laptop. I am trying to configure it to run on my lappie.

The specs are as follows:
AMD Turion 64 X2 processor
2 gigs of RAM
160 gigs of SATA

I am typing make xconfig/menuconfig to configure a kernel... where do I make the required changes to see to it that the correct processor is selected

I have had a previous error: kernel panic - kernel not syncing when some knowledgable people told me that I am not selecting the right kernel

Hoping some help... thanks in advance

Rahul

First why the need for a kernel compile? Looking at the hardware it's very basic, and should not require a kernel compile.

in any case here are three guides that explain howto compile a kernel properly. Take your pick, and read the guide thoroughly.  
[kernel compiling guide 1]("http://ubuntuforums.org/showthread.php?t=311158&highlight=Compiling+Linux+Kernel")
[Kernel compiling guide 2]("http://ubuntuforums.org/showthread.php?t=56835&highlight=Compiling+Linux+Kernel")
[Kernel compiling guide 3]("http://ubuntuforums.org/showthread.php?t=43065&highlight=Compiling+Linux+Kernel")

---

### Post by rahul_s on 2008-01-07
Its a learning project.. not a homework... so I am not asking you guys to help me with my homework... I am supposed to compile a linux kernel... 
I tried doing it before but didnt work well as the end image failed to sync

Thanks for the guides... I will go through these

---

### Post by rahul_s on 2008-01-07
What processor family do I select for an AMD Turion 64 X2 in the menuconfig screen ??

---

### Post by John.Michael.Kane on 2008-01-07
> **rahul_s said:**
> What processor family do I select for an AMD Turion 64 X2 in the menuconfig screen ??

AMD Turion is K8L based. Thus you might be best off using Generic-x86-64 which would allow for the best compatibility. 

You can compile it using AMD-Opteron/Athlon64 as your choice, and it "might" work as well.

---

