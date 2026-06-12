---
title: "How check my prossecor"
date: 2006-05-10
forum: x86 64-bit Users (Pre April '08)
---

### Post by dimitrisglobal on 2006-05-10
I am a amd user but i do not know the exact type of my prossecor.
Could you please help find it?

Thanks in advance,
Dimitris-Greece

---

### Post by kabus on 2006-05-10
```
cat /proc/cpuinfo
```

---

### Post by bluevoodoo1 on 2006-05-10
or

sudo lshw

---

### Post by dimitrisglobal on 2006-05-10
*-cpu
          description: CPU
          product: AMD Athlon(tm) Processor
          vendor: Advanced Micro Devices [AMD]
          physical id: 4
          bus info: cpu@0
          version: 6.8.1
          slot: Socket-A
          size: 2GHz
          capacity: 3GHz
          width: 32 bits
          clock: 133MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 mmx fxsr sse syscall mmxext 3dnowext 3dnow
        *-cache:0

These are the details of my processor.
Does it means that the processor is 32bit?
Do I have to install a different version of Ubuntu? How could i get the maximum performance from my computer?

Thanks in advance

Dimitris

---

### Post by skylark on 2006-05-11
Yes, I think your CPU is only 32-bit.

Here is my CPU for comparison:
     *-cpu
          description: CPU
          product: AMD Athlon(tm) 64 Processor 3200+
          vendor: Advanced Micro Devices [AMD]
          physical id: 3
          bus info: cpu@0
          version: AMD Athlon(tm) 64 Processor 3200+
          slot: Socket 939
          size: 2GHz
          capacity: 3GHz
          width: 64 bits
          clock: 200MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext fxsr_opt x86-64 3dnowext 3dnow pni lahf_lm

---

