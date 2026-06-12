---
title: "Using &quot;cpuid&quot; to determine 32-bit or 64-bit"
date: 2009-05-25
forum: x86 64-bit Users
---

### Post by podollb on 2009-05-25
Maybe I'm an idiot, but I can't figure out if my CPU is 32-bit or 64-bit. The output of the "**cpuid**" command was:

 ```
eax in    eax      ebx      ecx      edx
00000000 0000000a 756e6547 6c65746e 49656e69
00000001 000006fb 00020800 0000e3fd bfebfbff
00000002 05b0b101 005657f0 00000000 2cb43049
00000003 00000000 00000000 00000000 00000000
00000004 04000121 01c0003f 0000003f 00000001
00000005 00000040 00000040 00000003 00000220
00000006 00000001 00000002 00000001 00000000
00000007 00000000 00000000 00000000 00000000
00000008 00000400 00000000 00000000 00000000
00000009 00000000 00000000 00000000 00000000
0000000a 07280202 00000000 00000000 00000503
80000000 80000008 00000000 00000000 00000000
80000001 00000000 00000000 00000001 20100000
80000002 65746e49 2952286c 726f4320 4d542865
80000003 44203229 43206f75 20205550 45202020
80000004 30353736 20402020 36362e32 007a4847
80000005 00000000 00000000 00000000 00000000
80000006 00000000 00000000 10008040 00000000
80000007 00000000 00000000 00000000 00000000
80000008 00003024 00000000 00000000 00000000

Vendor ID: "GenuineIntel"; CPUID level 10

Intel-specific functions:
Version 000006fb:
Type 0 - Original OEM
Family 6 - Pentium Pro
Model 15 - 
Extended model 0
Stepping 11
Reserved 0

Extended brand string: "Intel(R) Core(TM)2 Duo CPU     E6750  @ 2.66GHz"
CLFLUSH instruction cache line size: 8
Hyper threading siblings: 2

Feature flags bfebfbff:
FPU    Floating Point Unit
VME    Virtual 8086 Mode Enhancements
DE     Debugging Extensions
PSE    Page Size Extensions
TSC    Time Stamp Counter
MSR    Model Specific Registers
PAE    Physical Address Extension
MCE    Machine Check Exception
CX8    COMPXCHG8B Instruction
APIC   On-chip Advanced Programmable Interrupt Controller present and enabled
SEP    Fast System Call
MTRR   Memory Type Range Registers
PGE    PTE Global Flag
MCA    Machine Check Architecture
CMOV   Conditional Move and Compare Instructions
FGPAT  Page Attribute Table
PSE-36 36-bit Page Size Extension
CLFSH  CFLUSH instruction
DS     Debug store
ACPI   Thermal Monitor and Clock Ctrl
MMX    MMX instruction set
FXSR   Fast FP/MMX Streaming SIMD Extensions save/restore
SSE    Streaming SIMD Extensions instruction set
SSE2   SSE2 extensions
SS     Self Snoop
HT     Hyper Threading
TM     Thermal monitor
31     reserved

TLB and cache info:
b1: unknown TLB/cache descriptor
b0: unknown TLB/cache descriptor
05: unknown TLB/cache descriptor
f0: unknown TLB/cache descriptor
57: unknown TLB/cache descriptor
56: unknown TLB/cache descriptor
49: unknown TLB/cache descriptor
30: unknown TLB/cache descriptor
b4: unknown TLB/cache descriptor
2c: unknown TLB/cache descriptor
Processor serial: 0000-06FB-0000-0000-0000-0000
```

---

### Post by 73ckn797 on 2009-05-25
Try in terminal:
```
sudo lshw
```

The first section will tell you.

---

### Post by podollb on 2009-05-25
Since it says "width: 64 bits" under the "cpu" section I guess it's a 64-bit processor right? Although, I do see "width: 32 bits" on the 7th or 8th line near the top which is confusing.

```
blitzen                   
    description: Desktop Computer
    product: SG31
    vendor: Shuttle Inc
    version: V10
    serial: 0
    width: 32 bits
    capabilities: smbios-2.5 dmi-2.5 smp-1.4 smp
    configuration: boot=normal chassis=desktop cpus=2 uuid=01020907-0301-0103-0807-060504030201
  *-core
       description: Motherboard
       product: FG31
       vendor: Shuttle Inc
       physical id: 0
       version: V10
       serial: 0
     *-firmware
          description: BIOS
          vendor: Phoenix Technologies, LTD
          physical id: 0
          version: 6.00 PG (08/23/2007)
          size: 128KiB
          capacity: 960KiB
          capabilities: isa pci pnp apm upgrade shadowing cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification
     *-cpu:0
          description: CPU
          product: Intel(R) Core(TM)2 Duo CPU     E6750  @ 2.66GHz
          vendor: Intel Corp.
          physical id: 5
          bus info: cpu@0
          version: 6.15.11
          serial: 0000-06FB-0000-0000-0000-0000
          slot: Socket 775
          size: 1600MHz
          capacity: 4GHz
          width: 64 bits
          clock: 266MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx x86-64 constant_tsc arch_perfmon pebs bts pni dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm lahf_lm tpr_shadow vnmi flexpriority cpufreq
          configuration: id=0
        *-cache:0
**...**

```

---

### Post by 73ckn797 on 2009-05-25
What does "cpu:1" show? It (cpu:0) appears to be 64bit. Have you booted from a 64bit installation disk? It will probably tell you that is will not work if the system is 32 bit.

---

### Post by podollb on 2009-05-25
Here's the cpu-1 section:

```
*-cpu:1
          physical id: 1
          bus info: cpu@1
          version: 6.15.11
          serial: 0000-06FB-0000-0000-0000-0000
          size: 1600MHz
          capacity: 1600MHz
          capabilities: vmx ht cpufreq
          configuration: id=0
        *-logicalcpu:0
             description: Logical CPU
             physical id: 0.1
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 0.2
             capabilities: logical

```

---

### Post by Cappy on 2009-05-26
"Intel(R) Core(TM)2 Duo" = 64-bit

---

### Post by jespdj on 2009-05-26
You have an Intel Core 2 Duo E6750, which does have the 64-bit extensions.

Lookup your processor on [Intel's processorfinder](http://processorfinder.intel.com/): [E6750](http://processorfinder.intel.com/details.aspx?sSpec=SLA9V). Note that it says "Intel® EM64T", which means that it does have the 64-bit extensions.

---

