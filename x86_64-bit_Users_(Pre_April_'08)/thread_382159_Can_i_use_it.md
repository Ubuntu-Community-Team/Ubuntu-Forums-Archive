---
title: "Can i use it ?"
date: 2007-03-11
forum: x86 64-bit Users (Pre April '08)
---

### Post by tjotser on 2007-03-11
I recently bought a Pentium 4 531+ 3Ghz 1MB l2  Hyperthreading , and it's running great on Ubuntu Feisty, Then i read somewhere that it might be possible to go 64Bit. Hoping to hear a yes,, here is my cpuinfo  :

> 

processor       : 0
vendor_id       : GenuineIntel
cpu family      : 15
model           : 4
model name      : Intel(R) Pentium(R) 4 CPU 3.00GHz
stepping        : 9
cpu MHz         : 3000.003
cache size      : 1024 KB
physical id     : 0
siblings        : 2
core id         : 0
cpu cores       : 1
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 3
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe$
bogomips        : 6007.82
clflush size    : 64

processor       : 1
vendor_id       : GenuineIntel
cpu family      : 15
model           : 4
model name      : Intel(R) Pentium(R) 4 CPU 3.00GHz
stepping        : 9
cpu MHz         : 3000.003
cache size      : 1024 KB
physical id     : 0
siblings        : 2
core id         : 0
cpu cores       : 1
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 3
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe$
bogomips        : 5999.79
clflush size    : 64




So, please tell me if i can run a 64 bit ubuntu and if so, should i use Feisty-herd-5 or Edgy or Dapper ? Thank you

---

### Post by John.Michael.Kane on 2007-03-11
According to the specifications of the processor it supports EM64T which means you should be able to run ubuntu 64bit,however. with out knowing the rest of your hardware configuration it will be hard to tell you if you will any other issues.

---

### Post by tjotser on 2007-03-11
I needed someones confirmation on this so thanks, The motherboard i a have is Asus p5dvxxx and the box says it is 64 bit supported. I will try it but... should i get - FeistyHerd5 / Edgy / DapperLTS  ??

---

### Post by John.Michael.Kane on 2007-03-11
You should be fine with edgy.


I would only suggest Feisty if your comfortable with the terminal in case things break as it is still under dev work.

---

### Post by tjotser on 2007-03-11
Thanks for the advice !! I am on feisty herd 5 now so i wouldn't mind the extra challenge of trying it first, but i'll get both anyway..  now to download the iso's and get some sleep..

Thanks and bye !! :KS

---

