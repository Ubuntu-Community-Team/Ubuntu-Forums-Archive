---
title: "dual 2 core, just one core working"
date: 2008-12-14
forum: x86 64-bit Users
---

### Post by ras-zealot on 2008-12-14
i have an intel core 2 duo E8400, when i check the system monitor i see only one cpu working, how can i enable the both. im using 64bit intrepid ibex

---

### Post by soxs on 2008-12-14
> **ras-zealot said:**
> i have an intel core 2 duo E8400, when i check the system monitor i see only one cpu working, how can i enable the both. im using 64bit intrepid ibex

Append the the output from cat /proc/cpu

---

### Post by graysky on 2008-12-14
What tasks are you doing?  If it's just web, mail, etc. I wouldn't expect to see anything different.  

Download [Handbrake](http://handbrake.fr/?article=download) and try some x264 encoding, or [compile a new kernel](http://technowizah.com/2005/12/debian-how-to-custom-kernel-compile.html) with the following command before the build step:

```
# export CONCURRENCY_LEVEL=3
```

Intel has oversold the whole "do more with 2 cores" slogan.  I have a quad core that sits idle 98 % of the time.  It's only a speed up for things like compiling, video encoding, some games.  Most apps are still single-threaded.

Now you can do multiple apps at once with a dual/quad chip, but most people don't find a need for this, and depending on what you're doing, it's I/O limited anyway.

---

### Post by roelpeeters on 2008-12-14
> **soxs said:**
> Append the the output from cat /proc/cpu
I think you mean cat /proc/cpuinfo. Anyway that would be the first place to look, to see if both cores are recognized. 
Second would be to check the BIOS settings to make sure a core has not been switched off. 
Third could be that the powersavings switches off one core to save energy. (I don't have personal experience for this)
Hope this helps.

---

### Post by ras-zealot on 2008-12-14
> **roelpeeters said:**
> I think you mean cat /proc/cpuinfo. Anyway that would be the first place to look, to see if both cores are recognized. 
Second would be to check the BIOS settings to make sure a core has not been switched off. 
Third could be that the powersavings switches off one core to save energy. (I don't have personal experience for this)
Hope this helps.

its not disabled in the BIOS, here's what is display for the cpuinfo
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 23
model name	: Intel(R) Core(TM)2 Duo CPU     E8400  @ 3.00GHz
stepping	: 6
cpu MHz		: 1998.000
cache size	: 6144 KB
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss tm pbe syscall nx lm constant_tsc up arch_perfmon pebs bts rep_good nopl pni monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr sse4_1 lahf_lm
bogomips	: 5999.86
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:


thats all

---

### Post by roelpeeters on 2008-12-15
> **ras-zealot said:**
> its not disabled in the BIOS, here's what is display for the cpuinfo
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 23
model name	: Intel(R) Core(TM)2 Duo CPU     E8400  @ 3.00GHz
stepping	: 6
cpu MHz		: 1998.000
cache size	: 6144 KB
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss tm pbe syscall nx lm constant_tsc up arch_perfmon pebs bts rep_good nopl pni monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr sse4_1 lahf_lm
bogomips	: 5999.86
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:


thats all
This does not seem like all the data I would expect. Are you running Ubuntu in a virtual machine by any chance?

---

### Post by Billxyzzy on 2008-12-15
Good day I would like to add a bit of info on this problem.
I am running two systems,  dual boot (Win xp and Ibex 8.10 64Bit.)
This would be considered a virtual environment for Ibex as I 
understand it.
My two system have the following motherboards
1.Elitegroup AMD690GM-M2 the older board
2.Elitegroup C51GM-M  a newer board.
The first system only shows one CPU core when I 
Cat /proc/Cpuinfo,  the second shows two cpu cores.
Thus I feel that the problem is hardware/bios related.

I will include the full output below.
I want to add one additional item to this as
there is a CPU speed difference between the two systems.
This might also be a problem but I will let others comment.

> bill@ubuntu:~$ cat /proc/cpuinfo
processor	: 0
                 ____
vendor_id	: AuthenticAMD
cpu family	: 15
model		: 75
model name	: AMD Athlon(tm) 64 X2 Dual Core Processor 4200+
stepping	: 2
cpu MHz		: 0.000
___________________________
cache size	: 512 KB
physical id	: 0
siblings	: 1
core id		: 0
cpu cores	: 1
apicid		: 0
initial apicid	: 0
fpu		: yes
fpu_exception	: yes
cpuid level	: 1
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp lm 3dnowext 3dnow rep_good nopl pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy
bogomips	: 2072.57
_________________________
TLB size	: 1024 4K pages
clflush size	: 64
cache_alignment	: 64
address sizes	: 40 bits physical, 48 bits virtual
power management: ts fid vid ttp tm stc

bill@ubuntu:~$ 

> bill@ubuntu:~$ cat /proc/cpuinfo
processor	: 0
                ____
vendor_id	: AuthenticAMD
cpu family	: 15
model		: 75
model name	: AMD Athlon(tm) 64 X2 Dual Core Processor 4200+
stepping	: 2
cpu MHz		: 1000.000
__________________________
cache size	: 512 KB
physical id	: 0
siblings	: 2
core id		: 0
cpu cores	: 2
apicid		: 0
initial apicid	: 0
fpu		: yes
fpu_exception	: yes
cpuid level	: 1
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp lm 3dnowext 3dnow rep_good nopl pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy
bogomips	: 2009.22
                 _________
TLB size	: 1024 4K pages
clflush size	: 64
cache_alignment	: 64
address sizes	: 40 bits physical, 48 bits virtual
power management: ts fid vid ttp tm stc

processor	: 1
                ____
vendor_id	: AuthenticAMD
cpu family	: 15
model		: 75
model name	: AMD Athlon(tm) 64 X2 Dual Core Processor 4200+
stepping	: 2
cpu MHz		: 1000.000
__________________________
cache size	: 512 KB
physical id	: 0
siblings	: 2
core id		: 1
cpu cores	: 2
apicid		: 1
initial apicid	: 1
fpu		: yes
fpu_exception	: yes
cpuid level	: 1
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp lm 3dnowext 3dnow rep_good nopl pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy
bogomips	: 2009.22
                  ________
TLB size	: 1024 4K pages
clflush size	: 64
cache_alignment	: 64
address sizes	: 40 bits physical, 48 bits virtual
power management: ts fid vid ttp tm stc

bill@ubuntu:~$ 


As you can see the two systems output different results
which I have underlined.

Ok any comments?

---

### Post by ras-zealot on 2008-12-15
not in a virtual machine

---

### Post by roelpeeters on 2008-12-16
OK, in both cases I am seeing things that don't sound right to me. Unless you are running mobile CPUs, the speed of the processor should be the 'full speed' (unless it is underclocked). In the case of Billxyzzy the cpu speed is 0.000, in the case of ras-zealot I see a lower speed (1998) than I would expect. Can you show the output of 'dmesg' also?

---

### Post by Billxyzzy on 2008-12-16
Before I get the dmsg outputs I will make one comment.
The first board (the oldest)  only has the bios option
for the CPU  virtualization enabled or disabled.
If disabled the system will not even boot.  No other features even
offered.

The second board has several options for CPU control in the bios
and I will experiment with them before I post again.

I think that the first board is a no go and I have to live with it.
I have upgraded the bios on the board but it did not help.

thanks

---

### Post by eyelessfade on 2008-12-16
I have the same cpu as you and:
```

$ cat /proc/cpuinfo                                                     
processor       : 0                                                                           
vendor_id       : GenuineIntel                                                                
cpu family      : 6                                                                           
model           : 23                                                                          
model name      : Intel(R) Core(TM)2 Duo CPU     E8400  @ 3.00GHz                             
stepping        : 6                                                                           
cpu MHz         : 2040.000                                                                    
cache size      : 6144 KB                                                                     
physical id     : 0                                                                           
siblings        : 2                                                                           
core id         : 0                                                                           
cpu cores       : 2                                                                           
apicid          : 0                                                                           
initial apicid  : 0                                                                           
fpu             : yes                                                                         
fpu_exception   : yes                                                                         
cpuid level     : 10                                                                          
wp              : yes                                                                         
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good nopl pni monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr sse4_1 lahf_lm                
bogomips        : 6119.99                                                                     
clflush size    : 64                                                                          
cache_alignment : 64                                                                          
address sizes   : 36 bits physical, 48 bits virtual                                           
power management:                                                                             

processor       : 1
vendor_id       : GenuineIntel
cpu family      : 6           
model           : 23          
model name      : Intel(R) Core(TM)2 Duo CPU     E8400  @ 3.00GHz
stepping        : 6                                              
cpu MHz         : 2040.000
cache size      : 6144 KB
physical id     : 0
siblings        : 2
core id         : 1
cpu cores       : 2
apicid          : 1
initial apicid  : 1
fpu             : yes
fpu_exception   : yes
cpuid level     : 10
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good nopl pni monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr sse4_1 lahf_lm
bogomips        : 6119.98
clflush size    : 64
cache_alignment : 64
address sizes   : 36 bits physical, 48 bits virtual
power management:

```

Guess its your board or bios...

---

### Post by fjgaude on 2008-12-16
I have the same E8400 Intel and it acts just fine when it is not overclocked. But as soon as the slightest overclocking is applied the speed control is lost and it runs at its highest frequency. So be it, until this bug is fixed by the development staff.

---

### Post by ras-zealot on 2008-12-16
the /var/log/dmesg display:
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.27-9-generic (buildd@yellow) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu11) ) #1 SMP Thu Nov 20 22:15:32 UTC 2008 (Ubuntu 2.6.27-9.19-generic)
[    0.000000] Command line: root=UUID=67d65750-8423-490f-a349-313c02a73302 ro quiet splash 
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000cf2ab000 (usable)
[    0.000000]  BIOS-e820: 00000000cf2ab000 - 00000000cf2ee000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000cf2ee000 - 00000000cf3c6000 (reserved)
[    0.000000]  BIOS-e820: 00000000cf3c6000 - 00000000cf3d6000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000cf3d6000 - 00000000cf452000 (reserved)
[    0.000000]  BIOS-e820: 00000000cf452000 - 00000000cf458000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000cf458000 - 00000000cf459000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000cf459000 - 00000000cf45b000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000cf45b000 - 00000000cf45d000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000cf45d000 - 00000000cf45e000 (reserved)
[    0.000000]  BIOS-e820: 00000000cf45e000 - 00000000cf462000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000cf462000 - 00000000cf471000 (reserved)
[    0.000000]  BIOS-e820: 00000000cf471000 - 00000000cf600000 (usable)
[    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed20000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffa00000 - 00000000ffc00000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffe00000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 0000000130000000 (usable)
[    0.000000] last_pfn = 0x130000 max_arch_pfn = 0x3ffffffff
[    0.000000] last_pfn = 0xcf600 max_arch_pfn = 0x3ffffffff
[    0.000000] init_memory_mapping
[    0.000000]  0000000000 - 00cf600000 page 2M
[    0.000000] kernel direct mapping tables up to cf600000 @ 8000-d000
[    0.000000] last_map_addr: cf600000 end: cf600000
[    0.000000] init_memory_mapping
[    0.000000]  0100000000 - 0130000000 page 2M
[    0.000000] kernel direct mapping tables up to 130000000 @ b000-11000
[    0.000000] last_map_addr: 130000000 end: 130000000
[    0.000000] RAMDISK: 377ac000 - 37fefb9b
[    0.000000] DMI 2.4 present.
[    0.000000] ACPI: RSDP 000F03F0, 0024 (r2  INTEL)
[    0.000000] ACPI: XSDT CF459F10, 0044 (r1  INTEL   DG31PR  6222004 MSFT    10013)
[    0.000000] ACPI: FACP CF457D90, 00F4 (r4  INTEL   DG31PR  6222004 MSFT    10013)
[    0.000000] ACPI: DSDT CF452010, 4BDC (r1  INTEL   DG31PR        0 INTL 20051117)
[    0.000000] ACPI: FACS CF458F40, 0040
[    0.000000] ACPI: APIC CF457F10, 006C (r2  INTEL   DG31PR  6222004 MSFT    10013)
[    0.000000] ACPI: HPET CF460D10, 0038 (r1  INTEL ICH7HPET  6222004 AMI.        1)
[    0.000000] ACPI: MCFG CF460C10, 003C (r1 INTEL  DG31PR    6222004 MSFT       97)
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-0000000130000000
[    0.000000] Bootmem setup node 0 0000000000000000-0000000130000000
[    0.000000]   NODE_DATA [0000000000001000 - 0000000000005fff]
[    0.000000]   bootmap [000000000000c000 -  0000000000031fff] pages 26
[    0.000000] (7 early reservations) ==> bootmem [0000000000 - 0130000000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000006000 - 0000008000]       TRAMPOLINE ==> [0000006000 - 0000008000]
[    0.000000]   #2 [0000200000 - 00008b8f9c]    TEXT DATA BSS ==> [0000200000 - 00008b8f9c]
[    0.000000]   #3 [00377ac000 - 0037fefb9b]          RAMDISK ==> [00377ac000 - 0037fefb9b]
[    0.000000]   #4 [000009fc00 - 0000100000]    BIOS reserved ==> [000009fc00 - 0000100000]
[    0.000000]   #5 [0000008000 - 000000b000]          PGTABLE ==> [0000008000 - 000000b000]
[    0.000000]   #6 [000000b000 - 000000c000]          PGTABLE ==> [000000b000 - 000000c000]
[    0.000000] found SMP MP-table at [ffff8800000fc5e0] 000fc5e0
[    0.000000]  [ffffe20000000000-ffffe20004bfffff] PMD -> [ffff880028200000-ffff88002c1fffff] on node 0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   0x00100000 -> 0x00130000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[4] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x000cf2ab
[    0.000000]     0: 0x000cf471 -> 0x000cf600
[    0.000000]     0: 0x00100000 -> 0x00130000
[    0.000000] On node 0 totalpages: 1045465
[    0.000000]   DMA zone: 2110 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 828538 pages, LIFO batch:31
[    0.000000]   Normal zone: 193536 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x02] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x03] disabled)
[    0.000000] ACPI: IOAPIC (id[0x00] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 0, version 0, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Setting APIC routing to flat
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 4 CPUs, 3 hotplug CPUs
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] PM: Registered nosave memory: 00000000cf2ab000 - 00000000cf2ee000
[    0.000000] PM: Registered nosave memory: 00000000cf2ee000 - 00000000cf3c6000
[    0.000000] PM: Registered nosave memory: 00000000cf3c6000 - 00000000cf3d6000
[    0.000000] PM: Registered nosave memory: 00000000cf3d6000 - 00000000cf452000
[    0.000000] PM: Registered nosave memory: 00000000cf452000 - 00000000cf458000
[    0.000000] PM: Registered nosave memory: 00000000cf458000 - 00000000cf459000
[    0.000000] PM: Registered nosave memory: 00000000cf459000 - 00000000cf45b000
[    0.000000] PM: Registered nosave memory: 00000000cf45b000 - 00000000cf45d000
[    0.000000] PM: Registered nosave memory: 00000000cf45d000 - 00000000cf45e000
[    0.000000] PM: Registered nosave memory: 00000000cf45e000 - 00000000cf462000
[    0.000000] PM: Registered nosave memory: 00000000cf462000 - 00000000cf471000
[    0.000000] PM: Registered nosave memory: 00000000cf600000 - 00000000fed1c000
[    0.000000] PM: Registered nosave memory: 00000000fed1c000 - 00000000fed20000
[    0.000000] PM: Registered nosave memory: 00000000fed20000 - 00000000ffa00000
[    0.000000] PM: Registered nosave memory: 00000000ffa00000 - 00000000ffc00000
[    0.000000] PM: Registered nosave memory: 00000000ffc00000 - 00000000ffe00000
[    0.000000] PM: Registered nosave memory: 00000000ffe00000 - 0000000100000000
[    0.000000] Allocating PCI resources starting at d0000000 (gap: cf600000:2f71c000)
[    0.000000] PERCPU: Allocating 64928 bytes of per cpu data
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 4, nr_node_ids 1
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 1024184
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: root=UUID=67d65750-8423-490f-a349-313c02a73302 ro quiet splash 
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
[    0.000000] Extended CMOS year: 2000
[    0.000000] TSC: PIT calibration confirmed by PMTIMER.
[    0.000000] TSC: using PIT calibration value
[    0.000000] Detected 2999.932 MHz processor.
[    0.004000] Console: colour VGA+ 80x25
[    0.004000] console [tty0] enabled
[    0.004000] Checking aperture...
[    0.004000] No AGP bridge found
[    0.004000] Calgary: detecting Calgary via BIOS EBDA area
[    0.004000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.004000] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    0.004000] Placing software IO TLB between 0x20000000 - 0x24000000
[    0.004000] Memory: 4034512k/4980736k available (3112k kernel code, 147348k reserved, 1575k data, 536k init)
[    0.004000] CPA: page pool initialized 1 of 1 pages preallocated
[    0.004000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.004000] hpet clockevent registered
[    0.004000] Calibrating delay loop (skipped), value calculated using timer frequency.. 5999.86 BogoMIPS (lpj=11999728)
[    0.004000] Security Framework initialized
[    0.004000] SELinux:  Disabled at boot.
[    0.004000] AppArmor: AppArmor initialized
[    0.004000] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.004000] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.004000] Mount-cache hash table entries: 256
[    0.004000] Initializing cgroup subsys ns
[    0.004000] Initializing cgroup subsys cpuacct
[    0.004000] Initializing cgroup subsys memory
[    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004000] CPU: L2 cache: 6144K
[    0.004000] CPU 0/0 -> Node 0
[    0.004000] CPU0: Thermal monitoring enabled (TM2)
[    0.004000] using mwait in idle threads.
[    0.004000] SMP alternatives: switching to UP code
[    0.007386] ACPI: Core revision 20080609
[    0.008844] ACPI: Checking initramfs for custom DSDT
[    0.264016] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.303780] CPU0: Intel(R) Core(TM)2 Duo CPU     E8400  @ 3.00GHz stepping 06
[    0.303782] Using local APIC timer interrupts.
[    0.304019] APIC timer calibration result 20832919
[    0.304020] Detected 20.832 MHz APIC timer.
[    0.304062] Brought up 1 CPUs
[    0.304064] Total of 1 processors activated (5999.86 BogoMIPS).
[    0.304098] CPU0 attaching sched-domain:
[    0.304100]  domain 0: span 0 level NODE
[    0.304101]   groups: 0
[    0.304241] net_namespace: 1552 bytes
[    0.304245] Booting paravirtualized kernel on bare hardware
[    0.304344] Time: 13:31:34  Date: 12/16/08
[    0.304364] NET: Registered protocol family 16
[    0.304547] ACPI: bus type pci registered
[    0.304612] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 64
[    0.304614] PCI: Not using MMCONFIG.
[    0.304615] PCI: Using configuration type 1 for base access
[    0.305476] ACPI: EC: Look up EC in DSDT
[    0.310080] ACPI: Interpreter enabled
[    0.310082] ACPI: (supports S0 S1 S3 S4 S5)
[    0.310092] ACPI: Using IOAPIC for interrupt routing
[    0.310131] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 64
[    0.312178] PCI: MCFG area at e0000000 reserved in ACPI motherboard resources
[    0.312179] PCI: updated MCFG configuration 0: base e0000000 segment 0 buses 0 - 31
[    0.313019] PCI: Using MMCONFIG at e0000000 - e1ffffff
[    0.313373] ACPI: BIOS _OSI(Linux) query ignored
[    0.313374] ACPI: DMI System Vendor:         
[    0.313375] ACPI: DMI Product Name:         
[    0.313376] ACPI: DMI Product Version:         
[    0.313377] ACPI: DMI Board Name: DG31PR
[    0.313377] ACPI: DMI BIOS Vendor: Intel Corp.
[    0.313378] ACPI: DMI BIOS Date: 10/24/2008
[    0.313379] ACPI: Please send DMI info above to [email]linux-acpi@vger.kernel.org[/email]
[    0.313380] ACPI: If "acpi_osi=Linux" works better, please notify [email]linux-acpi@vger.kernel.org[/email]
[    0.317986] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.318059] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    0.318062] pci 0000:00:01.0: PME# disabled
[    0.318072] PCI: 0000:00:02.0 reg 10 32bit mmio: [ff900000, ff97ffff]
[    0.318075] PCI: 0000:00:02.0 reg 14 io port: [f140, f147]
[    0.318077] PCI: 0000:00:02.0 reg 18 32bit mmio: [d0000000, dfffffff]
[    0.318080] PCI: 0000:00:02.0 reg 1c 32bit mmio: [ff700000, ff7fffff]
[    0.318127] PCI: 0000:00:1b.0 reg 10 64bit mmio: [ff980000, ff983fff]
[    0.318152] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.318155] pci 0000:00:1b.0: PME# disabled
[    0.318187] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.318190] pci 0000:00:1c.0: PME# disabled
[    0.318222] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.318224] pci 0000:00:1c.1: PME# disabled
[    0.318252] PCI: 0000:00:1d.0 reg 20 io port: [f080, f09f]
[    0.318285] PCI: 0000:00:1d.1 reg 20 io port: [f060, f07f]
[    0.318318] PCI: 0000:00:1d.2 reg 20 io port: [f040, f05f]
[    0.318351] PCI: 0000:00:1d.3 reg 20 io port: [f020, f03f]
[    0.318388] PCI: 0000:00:1d.7 reg 10 32bit mmio: [ff984000, ff9843ff]
[    0.318421] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.318424] pci 0000:00:1d.7: PME# disabled
[    0.318507] pci 0000:00:1f.0: quirk: region 0400-047f claimed by ICH6 ACPI/GPIO/TCO
[    0.318509] pci 0000:00:1f.0: quirk: region 0500-053f claimed by ICH6 GPIO
[    0.318527] PCI: 0000:00:1f.1 reg 10 io port: [f130, f137]
[    0.318531] PCI: 0000:00:1f.1 reg 14 io port: [f120, f123]
[    0.318535] PCI: 0000:00:1f.1 reg 18 io port: [f110, f117]
[    0.318540] PCI: 0000:00:1f.1 reg 1c io port: [f100, f103]
[    0.318544] PCI: 0000:00:1f.1 reg 20 io port: [f0f0, f0ff]
[    0.318570] PCI: 0000:00:1f.2 reg 10 io port: [f0e0, f0e7]
[    0.318574] PCI: 0000:00:1f.2 reg 14 io port: [f0d0, f0d3]
[    0.318578] PCI: 0000:00:1f.2 reg 18 io port: [f0c0, f0c7]
[    0.318581] PCI: 0000:00:1f.2 reg 1c io port: [f0b0, f0b3]
[    0.318585] PCI: 0000:00:1f.2 reg 20 io port: [f0a0, f0af]
[    0.318599] pci 0000:00:1f.2: PME# supported from D3hot
[    0.318601] pci 0000:00:1f.2: PME# disabled
[    0.318632] PCI: 0000:00:1f.3 reg 20 io port: [f000, f01f]
[    0.318749] PCI: 0000:03:00.0 reg 10 io port: [e000, e0ff]
[    0.318767] PCI: 0000:03:00.0 reg 18 64bit mmio: [ff820000, ff820fff]
[    0.318785] PCI: 0000:03:00.0 reg 30 32bit mmio: [ff800000, ff81ffff]
[    0.318802] pci 0000:03:00.0: supports D1
[    0.318803] pci 0000:03:00.0: supports D2
[    0.318804] pci 0000:03:00.0: PME# supported from D1 D2 D3hot D3cold
[    0.318808] pci 0000:03:00.0: PME# disabled
[    0.318831] PCI: bridge 0000:00:1c.1 io port: [e000, efff]
[    0.318833] PCI: bridge 0000:00:1c.1 32bit mmio: [ff800000, ff8fffff]
[    0.318872] pci 0000:00:1e.0: transparent bridge
[    0.318892] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.319034] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P2._PRT]
[    0.319135] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX0._PRT]
[    0.319206] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX1._PRT]
[    0.321521] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[    0.321610] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[    0.321696] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 *7 10 11 12 14 15)
[    0.321783] ACPI: PCI Interrupt Link [LNKD] (IRQs *3 4 5 6 10 11 12 14 15)
[    0.321870] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11 12 14 15) *0
[    0.321957] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11 12 14 15) *0
[    0.322044] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 11 12 14 15) *0
[    0.322130] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[    0.322251] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.322272] pnp: PnP ACPI init
[    0.322276] ACPI: bus type pnp registered
[    0.324214] pnp: PnP ACPI: found 12 devices
[    0.324216] ACPI: ACPI bus type pnp unregistered
[    0.324407] PCI: Using ACPI for IRQ routing
[    0.332059] NET: Registered protocol family 8
[    0.332061] NET: Registered protocol family 20
[    0.332091] NetLabel: Initializing
[    0.332093] NetLabel:  domain hash size = 128
[    0.332094] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.332105] NetLabel:  unlabeled traffic allowed by default
[    0.332114] PCI-GART: No AMD northbridge found.
[    0.332118] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.332121] hpet0: 3 64-bit timers, 14318180 Hz
[    0.334334] tracer: 1286 pages allocated for 65536 entries of 80 bytes
[    0.334335]    actual entries 65586
[    0.334384] AppArmor: AppArmor Filesystem Enabled
[    0.334399] ACPI: RTC can wake from S4
[    0.344036] system 00:01: iomem range 0xfed14000-0xfed19fff has been reserved
[    0.344039] system 00:01: iomem range 0xe0000000-0xe3ffffff has been reserved
[    0.344046] system 00:02: ioport range 0x400-0x47f has been reserved
[    0.344048] system 00:02: ioport range 0x1180-0x119f has been reserved
[    0.344050] system 00:02: ioport range 0x500-0x53f has been reserved
[    0.344055] system 00:02: iomem range 0xfec00000-0xfecfffff has been reserved
[    0.344057] system 00:02: iomem range 0xfee00000-0xfee0ffff has been reserved
[    0.344059] system 00:02: iomem range 0xfed1c000-0xfed1ffff could not be reserved
[    0.344062] system 00:02: iomem range 0xffb00000-0xffcfffff could not be reserved
[    0.344064] system 00:02: iomem range 0xfc800000-0xfc800fff has been reserved
[    0.344066] system 00:02: iomem range 0xfed20000-0xfed7ffff has been reserved
[    0.344068] system 00:02: iomem range 0xffe00000-0xffffffff could not be reserved
[    0.344073] system 00:03: ioport range 0x290-0x29f has been reserved
[    0.344080] system 00:09: ioport range 0x4d0-0x4d1 has been reserved
[    0.348887] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.348889] pci 0000:00:01.0:   IO window: disabled
[    0.348891] pci 0000:00:01.0:   MEM window: disabled
[    0.348892] pci 0000:00:01.0:   PREFETCH window: disabled
[    0.348895] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:02
[    0.348896] pci 0000:00:1c.0:   IO window: disabled
[    0.348899] pci 0000:00:1c.0:   MEM window: disabled
[    0.348901] pci 0000:00:1c.0:   PREFETCH window: disabled
[    0.348905] pci 0000:00:1c.1: PCI bridge, secondary bus 0000:03
[    0.348907] pci 0000:00:1c.1:   IO window: 0xe000-0xefff
[    0.348910] pci 0000:00:1c.1:   MEM window: 0xff800000-0xff8fffff
[    0.348912] pci 0000:00:1c.1:   PREFETCH window: disabled
[    0.348916] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:04
[    0.348917] pci 0000:00:1e.0:   IO window: disabled
[    0.348920] pci 0000:00:1e.0:   MEM window: disabled
[    0.348922] pci 0000:00:1e.0:   PREFETCH window: disabled
[    0.348930] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.348933] pci 0000:00:01.0: setting latency timer to 64
[    0.348937] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.348939] pci 0000:00:1c.0: setting latency timer to 64
[    0.348944] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.348946] pci 0000:00:1c.1: setting latency timer to 64
[    0.348950] pci 0000:00:1e.0: setting latency timer to 64
[    0.348953] bus: 00 index 0 io port: [0, ffff]
[    0.348954] bus: 00 index 1 mmio: [0, ffffffffffffffff]
[    0.348955] bus: 01 index 0 mmio: [0, 0]
[    0.348956] bus: 01 index 1 mmio: [0, 0]
[    0.348957] bus: 01 index 2 mmio: [0, 0]
[    0.348958] bus: 01 index 3 mmio: [0, 0]
[    0.348959] bus: 02 index 0 mmio: [0, 0]
[    0.348960] bus: 02 index 1 mmio: [0, 0]
[    0.348961] bus: 02 index 2 mmio: [0, 0]
[    0.348961] bus: 02 index 3 mmio: [0, 0]
[    0.348962] bus: 03 index 0 io port: [e000, efff]
[    0.348963] bus: 03 index 1 mmio: [ff800000, ff8fffff]
[    0.348964] bus: 03 index 2 mmio: [0, 0]
[    0.348965] bus: 03 index 3 mmio: [0, 0]
[    0.348966] bus: 04 index 0 mmio: [0, 0]
[    0.348967] bus: 04 index 1 mmio: [0, 0]
[    0.348968] bus: 04 index 2 mmio: [0, 0]
[    0.348969] bus: 04 index 3 io port: [0, ffff]
[    0.348970] bus: 04 index 4 mmio: [0, ffffffffffffffff]
[    0.348975] NET: Registered protocol family 2
[    0.388143] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.388809] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    0.391601] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.392065] TCP: Hash tables configured (established 524288 bind 65536)
[    0.392068] TCP reno registered
[    0.404123] NET: Registered protocol family 1
[    0.404215] checking if image is initramfs...<7>Switched to high resolution mode on CPU 0
[    0.653732]  it is
[    0.916007] Freeing initrd memory: 8462k freed
[    0.918343] audit: initializing netlink socket (disabled)
[    0.918357] type=2000 audit(1229434294.916:1): initialized
[    0.922486] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.923990] VFS: Disk quotas dquot_6.5.1
[    0.924050] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.924128] msgmni has been set to 7896
[    0.924207] io scheduler noop registered
[    0.924208] io scheduler anticipatory registered
[    0.924210] io scheduler deadline registered
[    0.924284] io scheduler cfq registered (default)
[    0.924295] pci 0000:00:02.0: Boot video device
[    8.924006] pci 0000:00:1d.7: EHCI: BIOS handoff failed (BIOS bug?) 01010001
[    8.924177] pcieport-driver 0000:00:01.0: setting latency timer to 64
[    8.924195] pcieport-driver 0000:00:01.0: found MSI capability
[    8.924214] pci_express 0000:00:01.0:pcie00: allocate port service
[    8.924237] pci_express 0000:00:01.0:pcie03: allocate port service
[    8.924283] pcieport-driver 0000:00:1c.0: setting latency timer to 64
[    8.924305] pcieport-driver 0000:00:1c.0: found MSI capability
[    8.924327] pci_express 0000:00:1c.0:pcie00: allocate port service
[    8.924350] pci_express 0000:00:1c.0:pcie02: allocate port service
[    8.924373] pci_express 0000:00:1c.0:pcie03: allocate port service
[    8.924429] pcieport-driver 0000:00:1c.1: setting latency timer to 64
[    8.924451] pcieport-driver 0000:00:1c.1: found MSI capability
[    8.924473] pci_express 0000:00:1c.1:pcie00: allocate port service
[    8.924494] pci_express 0000:00:1c.1:pcie02: allocate port service
[    8.924516] pci_express 0000:00:1c.1:pcie03: allocate port service
[    8.943983] hpet_resources: 0xfed00000 is busy
[    8.944048] Linux agpgart interface v0.103
[    8.944075] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    8.944186] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    8.944555] 00:05: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    8.945634] brd: module loaded
[    8.945680] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    8.945743] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[    8.945744] PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
[    8.946161] serio: i8042 KBD port at 0x60,0x64 irq 1
[    8.952096] mice: PS/2 mouse device common for all mice
[    8.952178] rtc_cmos 00:07: rtc core: registered rtc_cmos as rtc0
[    8.952197] rtc0: alarms up to one year, y3k, hpet irqs
[    8.952220] cpuidle: using governor ladder
[    8.952221] cpuidle: using governor menu
[    8.952440] TCP cubic registered
[    8.952558] registered taskstats version 1
[    8.952635]   Magic number: 4:96:534
[    8.952637] bdi 1:12: hash matches
[    8.952701] rtc_cmos 00:07: setting system clock to 2008-12-16 13:31:43 UTC (1229434303)
[    8.952702] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    8.952703] EDD information not available.
[    8.952740] Freeing unused kernel memory: 536k freed
[    8.952871] Write protecting the kernel read-only data: 4348k
[    8.976692] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[    9.103847] fuse init (API version 7.9)
[    9.214625] ACPI: SSDT CF45CC10, 02CC (r1    AMI      IST        1 MSFT  3000001)
[    9.214864] processor ACPI0007:00: registered as cooling_device0
[    9.482185] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    9.482199] r8169 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    9.482212] r8169 0000:03:00.0: setting latency timer to 64
[    9.482427] eth0: RTL8168b/8111b at 0xffffc2000062e000, 00:1c:c0:67:89:e5, XID 38500000 IRQ 2300
[    9.506030] usbcore: registered new interface driver usbfs
[    9.506042] usbcore: registered new interface driver hub
[    9.506062] usbcore: registered new device driver usb
[    9.506993] USB Universal Host Controller Interface driver v3.0
[    9.507023] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    9.507028] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    9.507030] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    9.507051] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[    9.507078] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000f080
[    9.507164] usb usb1: configuration #1 chosen from 1 choice
[    9.507178] hub 1-0:1.0: USB hub found
[    9.507182] hub 1-0:1.0: 2 ports detected
[    9.531153] No dock devices found.
[    9.542787] SCSI subsystem initialized
[    9.567234] libata version 3.00 loaded.
[    9.712211] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    9.712218] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    9.712220] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    9.712234] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[    9.712261] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000f060
[    9.712315] usb usb2: configuration #1 chosen from 1 choice
[    9.712331] hub 2-0:1.0: USB hub found
[    9.712335] hub 2-0:1.0: 2 ports detected
[    9.824044] usb 1-1: new full speed USB device using uhci_hcd and address 2
[    9.920122] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    9.920128] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    9.920130] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    9.920143] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[    9.920168] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000f040
[    9.920220] usb usb3: configuration #1 chosen from 1 choice
[    9.920235] hub 3-0:1.0: USB hub found
[    9.920239] hub 3-0:1.0: 2 ports detected
[   10.022165] usb 1-1: configuration #1 chosen from 1 choice
[   10.024123] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 16 (level, low) -> IRQ 16
[   10.024127] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[   10.024129] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[   10.024142] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[   10.024164] uhci_hcd 0000:00:1d.3: irq 16, io base 0x0000f020
[   10.024212] usb usb4: configuration #1 chosen from 1 choice
[   10.024225] hub 4-0:1.0: USB hub found
[   10.024230] hub 4-0:1.0: 2 ports detected
[   10.128152] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[   10.128162] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[   10.128165] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   10.128177] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[   10.132068] ehci_hcd 0000:00:1d.7: debug port 1
[   10.132072] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[   10.132075] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xff984000
[   10.136814] usb 1-2: new full speed USB device using uhci_hcd and address 3
[   10.148008] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   10.148056] usb usb5: configuration #1 chosen from 1 choice
[   10.148071] hub 5-0:1.0: USB hub found
[   10.148075] hub 5-0:1.0: 8 ports detected
[   10.204035] hub 1-0:1.0: unable to enumerate USB device on port 2
[   10.332035] usbcore: registered new interface driver hiddev
[   10.332401] usb 1-1: USB disconnect, address 2
[   10.358496] ata_piix 0000:00:1f.1: version 2.12
[   10.358504] ata_piix 0000:00:1f.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   10.358526] ata_piix 0000:00:1f.1: setting latency timer to 64
[   10.359184] scsi0 : ata_piix
[   10.359240] scsi1 : ata_piix
[   10.360322] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xf0f0 irq 14
[   10.360324] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xf0f8 irq 15

[   10.636309] ata1.00: ATAPI: LITE-ON LTR-48246S, SS06, max UDMA/33
[   10.636317] ata1.01: ATAPI: JLMS XJ-HD166S, DS0F, max UDMA/33
[   10.652237] ata1.00: configured for UDMA/33
[   10.652688] ata1.01: configured for UDMA/33
[   10.652708] ata2: port disabled. ignoring.
[   10.658540] scsi 0:0:0:0: CD-ROM            LITE-ON  LTR-48246S       SS06 PQ: 0 ANSI: 5
[   10.659521] scsi 0:0:1:0: CD-ROM            JLMS     XJ-HD166S        DS0F PQ: 0 ANSI: 5
[   10.659563] ata_piix 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[   10.659566] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
[   10.659583] ata_piix 0000:00:1f.2: setting latency timer to 64
[   10.660416] scsi2 : ata_piix
[   10.660993] scsi3 : ata_piix
[   10.661017] ata3: SATA max UDMA/133 cmd 0xf0e0 ctl 0xf0d0 bmdma 0xf0a0 irq 19
[   10.661019] ata4: SATA max UDMA/133 cmd 0xf0c0 ctl 0xf0b0 bmdma 0xf0a8 irq 19
[   10.796041] usbcore: registered new interface driver usbhid
[   10.796044] usbhid: v2.6:USB HID core driver
[   10.824533] ata3.00: ATA-8: ST3500320AS, SD15, max UDMA/133
[   10.824535] ata3.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[   10.840550] ata3.00: configured for UDMA/133
[   11.036010] usb 1-1: new full speed USB device using uhci_hcd and address 4
[   11.037360] ata4.00: ATA-7: ST3120813AS, 3.AAD, max UDMA/133
[   11.037362] ata4.00: 234441648 sectors, multi 16: LBA48 NCQ (depth 0/32)
[   11.103996] ata4.00: configured for UDMA/133
[   11.104062] scsi 2:0:0:0: Direct-Access     ATA      ST3500320AS      SD15 PQ: 0 ANSI: 5
[   11.104942] scsi 3:0:0:0: Direct-Access     ATA      ST3120813AS      3.AA PQ: 0 ANSI: 5
[   11.112643] scsi 0:0:0:0: Attached scsi generic sg0 type 5
[   11.112666] scsi 0:0:1:0: Attached scsi generic sg1 type 5
[   11.112685] scsi 2:0:0:0: Attached scsi generic sg2 type 0
[   11.112703] scsi 3:0:0:0: Attached scsi generic sg3 type 0
[   11.128811] Driver 'sr' needs updating - please use bus_type methods
[   11.132232] Driver 'sd' needs updating - please use bus_type methods
[   11.176161] sr0: scsi3-mmc drive: 255x/48x writer cd/rw xa/form2 cdda tray
[   11.176164] Uniform CD-ROM driver Revision: 3.20
[   11.176232] sr 0:0:0:0: Attached scsi CD-ROM sr0
[   11.178339] sr1: scsi3-mmc drive: 48x/48x cd/rw xa/form2 cdda tray
[   11.178397] sr 0:0:1:0: Attached scsi CD-ROM sr1
[   11.178457] sd 2:0:0:0: [sda] 976773168 512-byte hardware sectors (500108 MB)
[   11.178467] sd 2:0:0:0: [sda] Write Protect is off
[   11.178469] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   11.178486] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   11.178520] sd 2:0:0:0: [sda] 976773168 512-byte hardware sectors (500108 MB)
[   11.178530] sd 2:0:0:0: [sda] Write Protect is off
[   11.178531] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   11.178548] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   11.178550]  sda: sda1 sda2 < sda5 > sda3 sda4
[   11.196997] sd 2:0:0:0: [sda] Attached SCSI disk
[   11.197039] sd 3:0:0:0: [sdb] 234441648 512-byte hardware sectors (120034 MB)
[   11.197049] sd 3:0:0:0: [sdb] Write Protect is off
[   11.197051] sd 3:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[   11.197067] sd 3:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   11.197098] sd 3:0:0:0: [sdb] 234441648 512-byte hardware sectors (120034 MB)
[   11.197107] sd 3:0:0:0: [sdb] Write Protect is off
[   11.197109] sd 3:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[   11.197125] sd 3:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   11.197127]  sdb: sdb1
[   11.210349] sd 3:0:0:0: [sdb] Attached SCSI disk
[   11.245731] usb 1-1: configuration #1 chosen from 1 choice
[   11.266851] input: Razer Razer Copperhead Laser Mouse as /devices/pci0000:00/0000:00:1d.0/usb1/1-1/1-1:1.0/input/input2
[   11.276183] input,hidraw0: USB HID v1.00 Mouse [Razer Razer Copperhead Laser Mouse] on usb-0000:00:1d.0-1
[   11.287234] input: Razer Razer Copperhead Laser Mouse as /devices/pci0000:00/0000:00:1d.0/usb1/1-1/1-1:1.1/input/input3
[   11.292071] input,hidraw1: USB HID v0.01 Keyboard [Razer Razer Copperhead Laser Mouse] on usb-0000:00:1d.0-1
[   11.532012] usb 1-2: new full speed USB device using uhci_hcd and address 5
[   11.572816] PM: Starting manual resume from disk
[   11.572818] PM: Resume from partition 8:5
[   11.572818] PM: Checking hibernation image.
[   11.573157] PM: Resume from disk failed.
[   11.601230] kjournald starting.  Commit interval 5 seconds
[   11.601237] EXT3-fs: mounted filesystem with ordered data mode.
[   11.683209] usb 1-2: configuration #1 chosen from 1 choice
[   11.690160] input: C-Media USB Headphone Set   as /devices/pci0000:00/0000:00:1d.0/usb1/1-2/1-2:1.3/input/input4
[   11.700037] input,hidraw2: USB HID v1.00 Device [C-Media USB Headphone Set  ] on usb-0000:00:1d.0-2
[   11.940014] usb 2-2: new full speed USB device using uhci_hcd and address 2
[   12.133388] usb 2-2: configuration #1 chosen from 1 choice
[   15.761622] udevd version 124 started
[   15.954039] agpgart-intel 0000:00:00.0: Intel G33 Chipset
[   15.954716] agpgart-intel 0000:00:00.0: detected 7164K stolen memory
[   16.003526] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xd0000000
[   16.003604] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   16.025589] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   16.151370] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input5
[   16.160009] ACPI: Power Button (FF) [PWRF]
[   16.160071] input: Sleep Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input6
[   16.176012] ACPI: Sleep Button (CM) [SLPB]
[   16.176054] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input7
[   16.192012] ACPI: Power Button (CM) [PWRB]
[   16.568453] ACPI Exception (video-1630): AE_NOT_FOUND, Evaluating _DOD [20080609]
[   16.568499] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:17/input/input8
[   16.580015] ACPI: Video Device [GFX0] (multi-head: no  rom: yes  post: no)
[   16.936863] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   16.936878] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   16.969916] hda_codec: Unknown model for ALC883, trying auto-probe from BIOS...
[   17.003687] Linux video capture interface: v2.00
[   17.036080] gspca: main v2.2.0 registered
[   17.052454] usbcore: registered new interface driver snd-usb-audio
[   17.052670] gspca: probing 041e:4036
[   17.181536] intel_rng: Firmware space is locked read-only. If you can't or
[   17.181537] intel_rng: don't want to disable this in firmware setup, and if
[   17.181538] intel_rng: you are certain that your system has a functional
[   17.181538] intel_rng: RNG, try using the 'no_fwh_detect' option.
[   17.220564] iTCO_vendor_support: vendor-support=0
[   17.223309] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.03 (30-Apr-2008)
[   17.223370] iTCO_wdt: Found a ICH7 or ICH7R TCO device (Version=2, TCOBASE=0x0460)
[   17.223443] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   17.484761] input: PC Speaker as /devices/platform/pcspkr/input/input9
[   18.671307] zc3xx: probe 2wr ov vga 0x0000
[   18.715307] zc3xx: probe sensor -> 11
[   18.715308] zc3xx: Find Sensor HV7131R(c)
[   18.721565] gspca: probe ok
[   18.721581] usbcore: registered new interface driver zc3xx
[   18.722421] zc3xx: registered
[   19.718741] lp: driver loaded but no devices found
[   19.846241] Adding 8000328k swap on /dev/sda5.  Priority:-1 extents:1 across:8000328k
[   20.372266] EXT3 FS on sda4, internal journal
[   21.193593] type=1505 audit(1229455915.561:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=4086
[   21.274024] type=1505 audit(1229455915.641:3): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=4091
[   21.274136] type=1505 audit(1229455915.641:4): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=4091
[   21.373144] ip_tables: (C) 2000-2006 Netfilter Core Team

---

### Post by ras-zealot on 2008-12-16
btw i also have windows xp 64 bits and i can see the both cores there at my pc preferences

---

### Post by soxs on 2008-12-17
In post #11 you defnitly HAVE 2 CPU cores DETECTED! So if one core is at 100%, and the other  below 10%, don't care. Not all programs are made for multicore systems.

---

### Post by roelpeeters on 2008-12-17
@ras-zealot: In your dmesg output I see that only one CPU is activated... to me that means that either something is wrong with the hardware, or the kernel is not able to detect the two cores (essentially meaning a bug in the kernel). However, the cpuinfo from eyelessfade (who has the same CPU) shows the detection of two cores. My final guess it would be a hardware issue.

---

### Post by ras-zealot on 2008-12-17
damn seems we reach the EOF without any way to enable or do something :(

---

### Post by graysky on 2008-12-17
> **ras-zealot said:**
> damn seems we reach the EOF without any way to enable or do something :(

Not totally true.. you have several options to test whether the problem lies in your hardware or your kernel.  

1) Install Debian/Lenny and see if both cores work properly (this can be done on a spare HDD so you don't lose your Ubuntu install).

If reinstalling isn't appealing or if you don't have a spare HDD:

2) [Compile](http://technowizah.com/2005/12/debian-how-to-custom-kernel-compile.html) a new kernel starting from the debian .config and see if it is able to detect both your cores.  I have been burnt by the [Ubuntu-amd64 kernel on Intrepid](http://ubuntuforums.org/showthread.php?t=1000132) - it simply wasn't able to preform CPU frequency adjustment on my Xeon X3360.  If you read that thread I referenced, when I compiled by own kernel based on the Debian/Lenny .config file and rebooted with it, everything just worked.

**Let me know if you want help with either option I outlined.**  I do think you want to do one of the two to verify if it's your hardware or not.

EDIT: for reference, here is the Debian/Lenny .config for 2.6.26-1-amd64:

```
#
# Automatically generated make config: don't edit
# Linux kernel version: 2.6.26
# Wed Nov 26 17:37:24 2008
#
CONFIG_64BIT=y
# CONFIG_X86_32 is not set
CONFIG_X86_64=y
CONFIG_X86=y
CONFIG_ARCH_DEFCONFIG="arch/x86/configs/x86_64_defconfig"
# CONFIG_GENERIC_LOCKBREAK is not set
CONFIG_GENERIC_TIME=y
CONFIG_GENERIC_CMOS_UPDATE=y
CONFIG_CLOCKSOURCE_WATCHDOG=y
CONFIG_GENERIC_CLOCKEVENTS=y
CONFIG_GENERIC_CLOCKEVENTS_BROADCAST=y
CONFIG_LOCKDEP_SUPPORT=y
CONFIG_STACKTRACE_SUPPORT=y
CONFIG_HAVE_LATENCYTOP_SUPPORT=y
CONFIG_FAST_CMPXCHG_LOCAL=y
CONFIG_MMU=y
CONFIG_ZONE_DMA=y
CONFIG_GENERIC_ISA_DMA=y
CONFIG_GENERIC_IOMAP=y
CONFIG_GENERIC_BUG=y
CONFIG_GENERIC_HWEIGHT=y
# CONFIG_GENERIC_GPIO is not set
CONFIG_ARCH_MAY_HAVE_PC_FDC=y
CONFIG_RWSEM_GENERIC_SPINLOCK=y
# CONFIG_RWSEM_XCHGADD_ALGORITHM is not set
# CONFIG_ARCH_HAS_ILOG2_U32 is not set
# CONFIG_ARCH_HAS_ILOG2_U64 is not set
CONFIG_ARCH_HAS_CPU_IDLE_WAIT=y
CONFIG_GENERIC_CALIBRATE_DELAY=y
CONFIG_GENERIC_TIME_VSYSCALL=y
CONFIG_ARCH_HAS_CPU_RELAX=y
CONFIG_ARCH_HAS_CACHE_LINE_SIZE=y
CONFIG_HAVE_SETUP_PER_CPU_AREA=y
CONFIG_HAVE_CPUMASK_OF_CPU_MAP=y
CONFIG_ARCH_HIBERNATION_POSSIBLE=y
CONFIG_ARCH_SUSPEND_POSSIBLE=y
CONFIG_ZONE_DMA32=y
CONFIG_ARCH_POPULATES_NODE_MAP=y
CONFIG_AUDIT_ARCH=y
CONFIG_ARCH_SUPPORTS_AOUT=y
CONFIG_ARCH_SUPPORTS_OPTIMIZED_INLINING=y
CONFIG_GENERIC_HARDIRQS=y
CONFIG_GENERIC_IRQ_PROBE=y
CONFIG_GENERIC_PENDING_IRQ=y
CONFIG_X86_SMP=y
CONFIG_X86_64_SMP=y
CONFIG_X86_HT=y
CONFIG_X86_BIOS_REBOOT=y
CONFIG_X86_TRAMPOLINE=y
# CONFIG_KTIME_SCALAR is not set
CONFIG_DEFCONFIG_LIST="/lib/modules/$UNAME_RELEASE/.config"

#
# General setup
#
CONFIG_EXPERIMENTAL=y
CONFIG_LOCK_KERNEL=y
CONFIG_INIT_ENV_ARG_LIMIT=32
CONFIG_LOCALVERSION=""
# CONFIG_LOCALVERSION_AUTO is not set
CONFIG_SWAP=y
CONFIG_SYSVIPC=y
CONFIG_SYSVIPC_SYSCTL=y
CONFIG_POSIX_MQUEUE=y
CONFIG_BSD_PROCESS_ACCT=y
CONFIG_BSD_PROCESS_ACCT_V3=y
CONFIG_TASKSTATS=y
CONFIG_TASK_DELAY_ACCT=y
CONFIG_TASK_XACCT=y
CONFIG_TASK_IO_ACCOUNTING=y
CONFIG_AUDIT=y
CONFIG_AUDITSYSCALL=y
CONFIG_AUDIT_TREE=y
# CONFIG_IKCONFIG is not set
CONFIG_LOG_BUF_SHIFT=17
CONFIG_CGROUPS=y
# CONFIG_CGROUP_DEBUG is not set
CONFIG_CGROUP_NS=y
CONFIG_CGROUP_DEVICE=y
CONFIG_CPUSETS=y
CONFIG_HAVE_UNSTABLE_SCHED_CLOCK=y
CONFIG_GROUP_SCHED=y
CONFIG_FAIR_GROUP_SCHED=y
# CONFIG_RT_GROUP_SCHED is not set
# CONFIG_USER_SCHED is not set
CONFIG_CGROUP_SCHED=y
CONFIG_CGROUP_CPUACCT=y
# CONFIG_RESOURCE_COUNTERS is not set
CONFIG_SYSFS_DEPRECATED=y
CONFIG_SYSFS_DEPRECATED_V2=y
CONFIG_PROC_PID_CPUSET=y
CONFIG_RELAY=y
CONFIG_NAMESPACES=y
CONFIG_UTS_NS=y
CONFIG_IPC_NS=y
CONFIG_USER_NS=y
CONFIG_PID_NS=y
CONFIG_BLK_DEV_INITRD=y
CONFIG_INITRAMFS_SOURCE=""
CONFIG_CC_OPTIMIZE_FOR_SIZE=y
CONFIG_SYSCTL=y
# CONFIG_EMBEDDED is not set
CONFIG_UID16=y
CONFIG_SYSCTL_SYSCALL=y
CONFIG_SYSCTL_SYSCALL_CHECK=y
CONFIG_KALLSYMS=y
# CONFIG_KALLSYMS_ALL is not set
# CONFIG_KALLSYMS_EXTRA_PASS is not set
CONFIG_HOTPLUG=y
CONFIG_PRINTK=y
CONFIG_BUG=y
CONFIG_ELF_CORE=y
CONFIG_PCSPKR_PLATFORM=y
# CONFIG_COMPAT_BRK is not set
CONFIG_BASE_FULL=y
CONFIG_FUTEX=y
CONFIG_ANON_INODES=y
CONFIG_EPOLL=y
CONFIG_SIGNALFD=y
CONFIG_TIMERFD=y
CONFIG_EVENTFD=y
CONFIG_SHMEM=y
CONFIG_VM_EVENT_COUNTERS=y
CONFIG_SLAB=y
# CONFIG_SLUB is not set
# CONFIG_SLOB is not set
CONFIG_PROFILING=y
# CONFIG_MARKERS is not set
CONFIG_OPROFILE=m
CONFIG_HAVE_OPROFILE=y
# CONFIG_KPROBES is not set
CONFIG_HAVE_KPROBES=y
CONFIG_HAVE_KRETPROBES=y
# CONFIG_HAVE_DMA_ATTRS is not set
CONFIG_PROC_PAGE_MONITOR=y
CONFIG_SLABINFO=y
CONFIG_RT_MUTEXES=y
# CONFIG_TINY_SHMEM is not set
CONFIG_BASE_SMALL=0
CONFIG_MODULES=y
CONFIG_MODULE_FORCE_LOAD=y
CONFIG_MODULE_UNLOAD=y
CONFIG_MODULE_FORCE_UNLOAD=y
CONFIG_MODVERSIONS=y
# CONFIG_MODULE_SRCVERSION_ALL is not set
CONFIG_KMOD=y
CONFIG_STOP_MACHINE=y
CONFIG_BLOCK=y
CONFIG_BLK_DEV_IO_TRACE=y
CONFIG_BLK_DEV_BSG=y
CONFIG_BLOCK_COMPAT=y

#
# IO Schedulers
#
CONFIG_IOSCHED_NOOP=y
CONFIG_IOSCHED_AS=y
CONFIG_IOSCHED_DEADLINE=y
CONFIG_IOSCHED_CFQ=y
# CONFIG_DEFAULT_AS is not set
# CONFIG_DEFAULT_DEADLINE is not set
CONFIG_DEFAULT_CFQ=y
# CONFIG_DEFAULT_NOOP is not set
CONFIG_DEFAULT_IOSCHED="cfq"
CONFIG_PREEMPT_NOTIFIERS=y
CONFIG_CLASSIC_RCU=y

#
# Processor type and features
#
CONFIG_TICK_ONESHOT=y
CONFIG_NO_HZ=y
CONFIG_HIGH_RES_TIMERS=y
CONFIG_GENERIC_CLOCKEVENTS_BUILD=y
CONFIG_SMP=y
CONFIG_X86_PC=y
# CONFIG_X86_ELAN is not set
# CONFIG_X86_VOYAGER is not set
# CONFIG_X86_NUMAQ is not set
# CONFIG_X86_SUMMIT is not set
# CONFIG_X86_BIGSMP is not set
# CONFIG_X86_VISWS is not set
# CONFIG_X86_GENERICARCH is not set
# CONFIG_X86_ES7000 is not set
# CONFIG_X86_RDC321X is not set
# CONFIG_X86_VSMP is not set
CONFIG_PARAVIRT_GUEST=y
CONFIG_KVM_CLOCK=y
CONFIG_KVM_GUEST=y
CONFIG_PARAVIRT=y
CONFIG_PARAVIRT_CLOCK=y
CONFIG_MEMTEST_BOOTPARAM=y
CONFIG_MEMTEST_BOOTPARAM_VALUE=0
# CONFIG_M386 is not set
# CONFIG_M486 is not set
# CONFIG_M586 is not set
# CONFIG_M586TSC is not set
# CONFIG_M586MMX is not set
# CONFIG_M686 is not set
# CONFIG_MPENTIUMII is not set
# CONFIG_MPENTIUMIII is not set
# CONFIG_MPENTIUMM is not set
# CONFIG_MPENTIUM4 is not set
# CONFIG_MK6 is not set
# CONFIG_MK7 is not set
# CONFIG_MK8 is not set
# CONFIG_MCRUSOE is not set
# CONFIG_MEFFICEON is not set
# CONFIG_MWINCHIPC6 is not set
# CONFIG_MWINCHIP2 is not set
# CONFIG_MWINCHIP3D is not set
# CONFIG_MGEODEGX1 is not set
# CONFIG_MGEODE_LX is not set
# CONFIG_MCYRIXIII is not set
# CONFIG_MVIAC3_2 is not set
# CONFIG_MVIAC7 is not set
# CONFIG_MPSC is not set
# CONFIG_MCORE2 is not set
CONFIG_GENERIC_CPU=y
CONFIG_X86_CPU=y
CONFIG_X86_L1_CACHE_BYTES=128
CONFIG_X86_INTERNODE_CACHE_BYTES=128
CONFIG_X86_CMPXCHG=y
CONFIG_X86_L1_CACHE_SHIFT=7
CONFIG_X86_GOOD_APIC=y
CONFIG_X86_TSC=y
CONFIG_X86_CMOV=y
CONFIG_X86_MINIMUM_CPU_FAMILY=64
CONFIG_X86_DEBUGCTLMSR=y
CONFIG_HPET_TIMER=y
CONFIG_HPET_EMULATE_RTC=y
CONFIG_DMI=y
CONFIG_GART_IOMMU=y
CONFIG_CALGARY_IOMMU=y
CONFIG_CALGARY_IOMMU_ENABLED_BY_DEFAULT=y
CONFIG_SWIOTLB=y
CONFIG_IOMMU_HELPER=y
CONFIG_NR_CPUS=32
CONFIG_SCHED_SMT=y
CONFIG_SCHED_MC=y
CONFIG_PREEMPT_NONE=y
# CONFIG_PREEMPT_VOLUNTARY is not set
# CONFIG_PREEMPT is not set
CONFIG_X86_LOCAL_APIC=y
CONFIG_X86_IO_APIC=y
CONFIG_X86_MCE=y
CONFIG_X86_MCE_INTEL=y
CONFIG_X86_MCE_AMD=y
CONFIG_I8K=m
CONFIG_MICROCODE=m
CONFIG_MICROCODE_OLD_INTERFACE=y
CONFIG_X86_MSR=m
CONFIG_X86_CPUID=m
CONFIG_NUMA=y
CONFIG_K8_NUMA=y
CONFIG_X86_64_ACPI_NUMA=y
CONFIG_NODES_SPAN_OTHER_NODES=y
# CONFIG_NUMA_EMU is not set
CONFIG_NODES_SHIFT=6
CONFIG_ARCH_SPARSEMEM_DEFAULT=y
CONFIG_ARCH_SPARSEMEM_ENABLE=y
CONFIG_ARCH_SELECT_MEMORY_MODEL=y
CONFIG_SELECT_MEMORY_MODEL=y
# CONFIG_FLATMEM_MANUAL is not set
# CONFIG_DISCONTIGMEM_MANUAL is not set
CONFIG_SPARSEMEM_MANUAL=y
CONFIG_SPARSEMEM=y
CONFIG_NEED_MULTIPLE_NODES=y
CONFIG_HAVE_MEMORY_PRESENT=y
# CONFIG_SPARSEMEM_STATIC is not set
CONFIG_SPARSEMEM_EXTREME=y
CONFIG_SPARSEMEM_VMEMMAP_ENABLE=y
CONFIG_SPARSEMEM_VMEMMAP=y

#
# Memory hotplug is currently incompatible with Software Suspend
#
CONFIG_PAGEFLAGS_EXTENDED=y
CONFIG_SPLIT_PTLOCK_CPUS=4
CONFIG_MIGRATION=y
CONFIG_RESOURCES_64BIT=y
CONFIG_ZONE_DMA_FLAG=1
CONFIG_BOUNCE=y
CONFIG_VIRT_TO_BUS=y
CONFIG_MTRR=y
# CONFIG_X86_PAT is not set
CONFIG_EFI=y
CONFIG_SECCOMP=y
# CONFIG_HZ_100 is not set
CONFIG_HZ_250=y
# CONFIG_HZ_300 is not set
# CONFIG_HZ_1000 is not set
CONFIG_HZ=250
CONFIG_SCHED_HRTICK=y
CONFIG_KEXEC=y
# CONFIG_CRASH_DUMP is not set
CONFIG_PHYSICAL_START=0x200000
# CONFIG_RELOCATABLE is not set
CONFIG_PHYSICAL_ALIGN=0x200000
CONFIG_HOTPLUG_CPU=y
# CONFIG_COMPAT_VDSO is not set
CONFIG_ARCH_ENABLE_MEMORY_HOTPLUG=y
CONFIG_HAVE_ARCH_EARLY_PFN_TO_NID=y

#
# Power management options
#
CONFIG_ARCH_HIBERNATION_HEADER=y
CONFIG_PM=y
# CONFIG_PM_DEBUG is not set
CONFIG_PM_SLEEP_SMP=y
CONFIG_PM_SLEEP=y
CONFIG_SUSPEND=y
CONFIG_SUSPEND_FREEZER=y
CONFIG_HIBERNATION=y
CONFIG_PM_STD_PARTITION=""
CONFIG_ACPI=y
CONFIG_ACPI_SLEEP=y
CONFIG_ACPI_PROCFS=y
CONFIG_ACPI_PROCFS_POWER=y
CONFIG_ACPI_SYSFS_POWER=y
CONFIG_ACPI_PROC_EVENT=y
CONFIG_ACPI_AC=m
CONFIG_ACPI_BATTERY=m
CONFIG_ACPI_BUTTON=m
CONFIG_ACPI_VIDEO=m
CONFIG_ACPI_FAN=m
CONFIG_ACPI_DOCK=m
CONFIG_ACPI_BAY=m
CONFIG_ACPI_PROCESSOR=m
CONFIG_ACPI_HOTPLUG_CPU=y
CONFIG_ACPI_THERMAL=m
CONFIG_ACPI_NUMA=y
CONFIG_ACPI_WMI=m
CONFIG_ACPI_ASUS=m
CONFIG_ACPI_TOSHIBA=m
# CONFIG_ACPI_CUSTOM_DSDT is not set
CONFIG_ACPI_BLACKLIST_YEAR=0
# CONFIG_ACPI_DEBUG is not set
CONFIG_ACPI_EC=y
CONFIG_ACPI_POWER=y
CONFIG_ACPI_SYSTEM=y
CONFIG_X86_PM_TIMER=y
CONFIG_ACPI_CONTAINER=m
CONFIG_ACPI_SBS=m

#
# CPU Frequency scaling
#
CONFIG_CPU_FREQ=y
CONFIG_CPU_FREQ_TABLE=m
# CONFIG_CPU_FREQ_DEBUG is not set
CONFIG_CPU_FREQ_STAT=m
# CONFIG_CPU_FREQ_STAT_DETAILS is not set
CONFIG_CPU_FREQ_DEFAULT_GOV_PERFORMANCE=y
# CONFIG_CPU_FREQ_DEFAULT_GOV_POWERSAVE is not set
# CONFIG_CPU_FREQ_DEFAULT_GOV_USERSPACE is not set
# CONFIG_CPU_FREQ_DEFAULT_GOV_ONDEMAND is not set
# CONFIG_CPU_FREQ_DEFAULT_GOV_CONSERVATIVE is not set
CONFIG_CPU_FREQ_GOV_PERFORMANCE=y
CONFIG_CPU_FREQ_GOV_POWERSAVE=m
CONFIG_CPU_FREQ_GOV_USERSPACE=m
CONFIG_CPU_FREQ_GOV_ONDEMAND=m
CONFIG_CPU_FREQ_GOV_CONSERVATIVE=m

#
# CPUFreq processor drivers
#
CONFIG_X86_ACPI_CPUFREQ=m
CONFIG_X86_POWERNOW_K8=m
CONFIG_X86_POWERNOW_K8_ACPI=y
CONFIG_X86_SPEEDSTEP_CENTRINO=m
# CONFIG_X86_P4_CLOCKMOD is not set

#
# shared options
#
# CONFIG_X86_ACPI_CPUFREQ_PROC_INTF is not set
# CONFIG_X86_SPEEDSTEP_LIB is not set
CONFIG_CPU_IDLE=y
CONFIG_CPU_IDLE_GOV_LADDER=y
CONFIG_CPU_IDLE_GOV_MENU=y

#
# Bus options (PCI etc.)
#
CONFIG_PCI=y
CONFIG_PCI_DIRECT=y
CONFIG_PCI_MMCONFIG=y
CONFIG_PCI_DOMAINS=y
# CONFIG_DMAR is not set
CONFIG_PCIEPORTBUS=y
CONFIG_HOTPLUG_PCI_PCIE=m
CONFIG_PCIEAER=y
# CONFIG_PCIEASPM is not set
CONFIG_ARCH_SUPPORTS_MSI=y
CONFIG_PCI_MSI=y
CONFIG_PCI_LEGACY=y
# CONFIG_PCI_DEBUG is not set
CONFIG_HT_IRQ=y
CONFIG_ISA_DMA_API=y
CONFIG_K8_NB=y
CONFIG_PCCARD=m
# CONFIG_PCMCIA_DEBUG is not set
CONFIG_PCMCIA=m
CONFIG_PCMCIA_LOAD_CIS=y
CONFIG_PCMCIA_IOCTL=y
CONFIG_CARDBUS=y

#
# PC-card bridges
#
CONFIG_YENTA=m
CONFIG_YENTA_O2=y
CONFIG_YENTA_RICOH=y
CONFIG_YENTA_TI=y
CONFIG_YENTA_ENE_TUNE=y
CONFIG_YENTA_TOSHIBA=y
CONFIG_PD6729=m
CONFIG_I82092=m
CONFIG_PCCARD_NONSTATIC=m
CONFIG_HOTPLUG_PCI=m
CONFIG_HOTPLUG_PCI_FAKE=m
CONFIG_HOTPLUG_PCI_ACPI=m
CONFIG_HOTPLUG_PCI_ACPI_IBM=m
CONFIG_HOTPLUG_PCI_CPCI=y
CONFIG_HOTPLUG_PCI_CPCI_ZT5550=m
CONFIG_HOTPLUG_PCI_CPCI_GENERIC=m
CONFIG_HOTPLUG_PCI_SHPC=m

#
# Executable file formats / Emulations
#
CONFIG_BINFMT_ELF=y
CONFIG_COMPAT_BINFMT_ELF=y
CONFIG_BINFMT_MISC=m
CONFIG_IA32_EMULATION=y
CONFIG_IA32_AOUT=y
CONFIG_COMPAT=y
CONFIG_COMPAT_FOR_U64_ALIGNMENT=y
CONFIG_SYSVIPC_COMPAT=y

#
# Networking
#
CONFIG_NET=y

#
# Networking options
#
CONFIG_PACKET=y
CONFIG_PACKET_MMAP=y
CONFIG_UNIX=y
CONFIG_XFRM=y
CONFIG_XFRM_USER=m
# CONFIG_XFRM_SUB_POLICY is not set
# CONFIG_XFRM_MIGRATE is not set
# CONFIG_XFRM_STATISTICS is not set
CONFIG_NET_KEY=m
# CONFIG_NET_KEY_MIGRATE is not set
CONFIG_INET=y
CONFIG_IP_MULTICAST=y
CONFIG_IP_ADVANCED_ROUTER=y
CONFIG_ASK_IP_FIB_HASH=y
# CONFIG_IP_FIB_TRIE is not set
CONFIG_IP_FIB_HASH=y
CONFIG_IP_MULTIPLE_TABLES=y
CONFIG_IP_ROUTE_MULTIPATH=y
CONFIG_IP_ROUTE_VERBOSE=y
# CONFIG_IP_PNP is not set
CONFIG_NET_IPIP=m
CONFIG_NET_IPGRE=m
CONFIG_NET_IPGRE_BROADCAST=y
CONFIG_IP_MROUTE=y
CONFIG_IP_PIMSM_V1=y
CONFIG_IP_PIMSM_V2=y
# CONFIG_ARPD is not set
CONFIG_SYN_COOKIES=y
CONFIG_INET_AH=m
CONFIG_INET_ESP=m
CONFIG_INET_IPCOMP=m
CONFIG_INET_XFRM_TUNNEL=m
CONFIG_INET_TUNNEL=m
CONFIG_INET_XFRM_MODE_TRANSPORT=m
CONFIG_INET_XFRM_MODE_TUNNEL=m
CONFIG_INET_XFRM_MODE_BEET=m
CONFIG_INET_LRO=m
CONFIG_INET_DIAG=m
CONFIG_INET_TCP_DIAG=m
CONFIG_TCP_CONG_ADVANCED=y
CONFIG_TCP_CONG_BIC=m
CONFIG_TCP_CONG_CUBIC=y
CONFIG_TCP_CONG_WESTWOOD=m
CONFIG_TCP_CONG_HTCP=m
CONFIG_TCP_CONG_HSTCP=m
CONFIG_TCP_CONG_HYBLA=m
CONFIG_TCP_CONG_VEGAS=m
CONFIG_TCP_CONG_SCALABLE=m
CONFIG_TCP_CONG_LP=m
CONFIG_TCP_CONG_VENO=m
CONFIG_TCP_CONG_YEAH=m
CONFIG_TCP_CONG_ILLINOIS=m
# CONFIG_DEFAULT_BIC is not set
CONFIG_DEFAULT_CUBIC=y
# CONFIG_DEFAULT_HTCP is not set
# CONFIG_DEFAULT_VEGAS is not set
# CONFIG_DEFAULT_WESTWOOD is not set
# CONFIG_DEFAULT_RENO is not set
CONFIG_DEFAULT_TCP_CONG="cubic"
CONFIG_TCP_MD5SIG=y
CONFIG_IP_VS=m
# CONFIG_IP_VS_DEBUG is not set
CONFIG_IP_VS_TAB_BITS=12

#
# IPVS transport protocol load balancing support
#
CONFIG_IP_VS_PROTO_TCP=y
CONFIG_IP_VS_PROTO_UDP=y
CONFIG_IP_VS_PROTO_ESP=y
CONFIG_IP_VS_PROTO_AH=y

#
# IPVS scheduler
#
CONFIG_IP_VS_RR=m
CONFIG_IP_VS_WRR=m
CONFIG_IP_VS_LC=m
CONFIG_IP_VS_WLC=m
CONFIG_IP_VS_LBLC=m
CONFIG_IP_VS_LBLCR=m
CONFIG_IP_VS_DH=m
CONFIG_IP_VS_SH=m
CONFIG_IP_VS_SED=m
CONFIG_IP_VS_NQ=m

#
# IPVS application helper
#
CONFIG_IP_VS_FTP=m
CONFIG_IPV6=m
CONFIG_IPV6_PRIVACY=y
CONFIG_IPV6_ROUTER_PREF=y
CONFIG_IPV6_ROUTE_INFO=y
CONFIG_IPV6_OPTIMISTIC_DAD=y
CONFIG_INET6_AH=m
CONFIG_INET6_ESP=m
CONFIG_INET6_IPCOMP=m
CONFIG_IPV6_MIP6=m
CONFIG_INET6_XFRM_TUNNEL=m
CONFIG_INET6_TUNNEL=m
CONFIG_INET6_XFRM_MODE_TRANSPORT=m
CONFIG_INET6_XFRM_MODE_TUNNEL=m
CONFIG_INET6_XFRM_MODE_BEET=m
CONFIG_INET6_XFRM_MODE_ROUTEOPTIMIZATION=m
CONFIG_IPV6_SIT=m
CONFIG_IPV6_NDISC_NODETYPE=y
CONFIG_IPV6_TUNNEL=m
CONFIG_IPV6_MULTIPLE_TABLES=y
CONFIG_IPV6_SUBTREES=y
CONFIG_IPV6_MROUTE=y
CONFIG_IPV6_PIMSM_V2=y
# CONFIG_NETLABEL is not set
CONFIG_NETWORK_SECMARK=y
CONFIG_NETFILTER=y
# CONFIG_NETFILTER_DEBUG is not set
CONFIG_NETFILTER_ADVANCED=y
CONFIG_BRIDGE_NETFILTER=y

#
# Core Netfilter Configuration
#
CONFIG_NETFILTER_NETLINK=m
CONFIG_NETFILTER_NETLINK_QUEUE=m
CONFIG_NETFILTER_NETLINK_LOG=m
CONFIG_NF_CONNTRACK=m
CONFIG_NF_CT_ACCT=y
CONFIG_NF_CONNTRACK_MARK=y
CONFIG_NF_CONNTRACK_SECMARK=y
CONFIG_NF_CONNTRACK_EVENTS=y
CONFIG_NF_CT_PROTO_DCCP=m
CONFIG_NF_CT_PROTO_GRE=m
CONFIG_NF_CT_PROTO_SCTP=m
CONFIG_NF_CT_PROTO_UDPLITE=m
CONFIG_NF_CONNTRACK_AMANDA=m
CONFIG_NF_CONNTRACK_FTP=m
CONFIG_NF_CONNTRACK_H323=m
CONFIG_NF_CONNTRACK_IRC=m
CONFIG_NF_CONNTRACK_NETBIOS_NS=m
CONFIG_NF_CONNTRACK_PPTP=m
CONFIG_NF_CONNTRACK_SANE=m
CONFIG_NF_CONNTRACK_SIP=m
CONFIG_NF_CONNTRACK_TFTP=m
CONFIG_NF_CT_NETLINK=m
CONFIG_NETFILTER_XTABLES=m
CONFIG_NETFILTER_XT_TARGET_CLASSIFY=m
CONFIG_NETFILTER_XT_TARGET_CONNMARK=m
CONFIG_NETFILTER_XT_TARGET_DSCP=m
CONFIG_NETFILTER_XT_TARGET_MARK=m
CONFIG_NETFILTER_XT_TARGET_NFQUEUE=m
CONFIG_NETFILTER_XT_TARGET_NFLOG=m
CONFIG_NETFILTER_XT_TARGET_NOTRACK=m
CONFIG_NETFILTER_XT_TARGET_RATEEST=m
CONFIG_NETFILTER_XT_TARGET_TRACE=m
CONFIG_NETFILTER_XT_TARGET_SECMARK=m
CONFIG_NETFILTER_XT_TARGET_CONNSECMARK=m
CONFIG_NETFILTER_XT_TARGET_TCPMSS=m
CONFIG_NETFILTER_XT_TARGET_TCPOPTSTRIP=m
CONFIG_NETFILTER_XT_MATCH_COMMENT=m
CONFIG_NETFILTER_XT_MATCH_CONNBYTES=m
CONFIG_NETFILTER_XT_MATCH_CONNLIMIT=m
CONFIG_NETFILTER_XT_MATCH_CONNMARK=m
CONFIG_NETFILTER_XT_MATCH_CONNTRACK=m
CONFIG_NETFILTER_XT_MATCH_DCCP=m
CONFIG_NETFILTER_XT_MATCH_DSCP=m
CONFIG_NETFILTER_XT_MATCH_ESP=m
CONFIG_NETFILTER_XT_MATCH_HELPER=m
CONFIG_NETFILTER_XT_MATCH_IPRANGE=m
CONFIG_NETFILTER_XT_MATCH_LENGTH=m
CONFIG_NETFILTER_XT_MATCH_LIMIT=m
CONFIG_NETFILTER_XT_MATCH_MAC=m
CONFIG_NETFILTER_XT_MATCH_MARK=m
CONFIG_NETFILTER_XT_MATCH_OWNER=m
CONFIG_NETFILTER_XT_MATCH_POLICY=m
CONFIG_NETFILTER_XT_MATCH_MULTIPORT=m
CONFIG_NETFILTER_XT_MATCH_PHYSDEV=m
CONFIG_NETFILTER_XT_MATCH_PKTTYPE=m
CONFIG_NETFILTER_XT_MATCH_QUOTA=m
CONFIG_NETFILTER_XT_MATCH_RATEEST=m
CONFIG_NETFILTER_XT_MATCH_REALM=m
CONFIG_NETFILTER_XT_MATCH_SCTP=m
CONFIG_NETFILTER_XT_MATCH_STATE=m
CONFIG_NETFILTER_XT_MATCH_STATISTIC=m
CONFIG_NETFILTER_XT_MATCH_STRING=m
CONFIG_NETFILTER_XT_MATCH_TCPMSS=m
CONFIG_NETFILTER_XT_MATCH_TIME=m
CONFIG_NETFILTER_XT_MATCH_U32=m
CONFIG_NETFILTER_XT_MATCH_HASHLIMIT=m

#
# IP: Netfilter Configuration
#
CONFIG_NF_CONNTRACK_IPV4=m
CONFIG_NF_CONNTRACK_PROC_COMPAT=y
CONFIG_IP_NF_QUEUE=m
CONFIG_IP_NF_IPTABLES=m
CONFIG_IP_NF_MATCH_RECENT=m
CONFIG_IP_NF_MATCH_ECN=m
CONFIG_IP_NF_MATCH_AH=m
CONFIG_IP_NF_MATCH_TTL=m
CONFIG_IP_NF_MATCH_ADDRTYPE=m
CONFIG_IP_NF_FILTER=m
CONFIG_IP_NF_TARGET_REJECT=m
CONFIG_IP_NF_TARGET_LOG=m
CONFIG_IP_NF_TARGET_ULOG=m
CONFIG_NF_NAT=m
CONFIG_NF_NAT_NEEDED=y
CONFIG_IP_NF_TARGET_MASQUERADE=m
CONFIG_IP_NF_TARGET_REDIRECT=m
CONFIG_IP_NF_TARGET_NETMAP=m
CONFIG_NF_NAT_SNMP_BASIC=m
CONFIG_NF_NAT_PROTO_DCCP=m
CONFIG_NF_NAT_PROTO_GRE=m
CONFIG_NF_NAT_PROTO_UDPLITE=m
CONFIG_NF_NAT_PROTO_SCTP=m
CONFIG_NF_NAT_FTP=m
CONFIG_NF_NAT_IRC=m
CONFIG_NF_NAT_TFTP=m
CONFIG_NF_NAT_AMANDA=m
CONFIG_NF_NAT_PPTP=m
CONFIG_NF_NAT_H323=m
CONFIG_NF_NAT_SIP=m
CONFIG_IP_NF_MANGLE=m
CONFIG_IP_NF_TARGET_ECN=m
CONFIG_IP_NF_TARGET_TTL=m
CONFIG_IP_NF_TARGET_CLUSTERIP=m
CONFIG_IP_NF_RAW=m
CONFIG_IP_NF_ARPTABLES=m
CONFIG_IP_NF_ARPFILTER=m
CONFIG_IP_NF_ARP_MANGLE=m

#
# IPv6: Netfilter Configuration
#
CONFIG_NF_CONNTRACK_IPV6=m
CONFIG_IP6_NF_QUEUE=m
CONFIG_IP6_NF_IPTABLES=m
CONFIG_IP6_NF_MATCH_RT=m
CONFIG_IP6_NF_MATCH_OPTS=m
CONFIG_IP6_NF_MATCH_FRAG=m
CONFIG_IP6_NF_MATCH_HL=m
CONFIG_IP6_NF_MATCH_IPV6HEADER=m
CONFIG_IP6_NF_MATCH_AH=m
CONFIG_IP6_NF_MATCH_MH=m
CONFIG_IP6_NF_MATCH_EUI64=m
CONFIG_IP6_NF_FILTER=m
CONFIG_IP6_NF_TARGET_LOG=m
CONFIG_IP6_NF_TARGET_REJECT=m
CONFIG_IP6_NF_MANGLE=m
CONFIG_IP6_NF_TARGET_HL=m
CONFIG_IP6_NF_RAW=m

#
# DECnet: Netfilter Configuration
#
CONFIG_DECNET_NF_GRABULATOR=m

#
# Bridge: Netfilter Configuration
#
CONFIG_BRIDGE_NF_EBTABLES=m
CONFIG_BRIDGE_EBT_BROUTE=m
CONFIG_BRIDGE_EBT_T_FILTER=m
CONFIG_BRIDGE_EBT_T_NAT=m
CONFIG_BRIDGE_EBT_802_3=m
CONFIG_BRIDGE_EBT_AMONG=m
CONFIG_BRIDGE_EBT_ARP=m
CONFIG_BRIDGE_EBT_IP=m
CONFIG_BRIDGE_EBT_LIMIT=m
CONFIG_BRIDGE_EBT_MARK=m
CONFIG_BRIDGE_EBT_PKTTYPE=m
CONFIG_BRIDGE_EBT_STP=m
CONFIG_BRIDGE_EBT_VLAN=m
CONFIG_BRIDGE_EBT_ARPREPLY=m
CONFIG_BRIDGE_EBT_DNAT=m
CONFIG_BRIDGE_EBT_MARK_T=m
CONFIG_BRIDGE_EBT_REDIRECT=m
CONFIG_BRIDGE_EBT_SNAT=m
CONFIG_BRIDGE_EBT_LOG=m
CONFIG_BRIDGE_EBT_ULOG=m
CONFIG_BRIDGE_EBT_NFLOG=m
CONFIG_IP_DCCP=m
CONFIG_INET_DCCP_DIAG=m
CONFIG_IP_DCCP_ACKVEC=y

#
# DCCP CCIDs Configuration (EXPERIMENTAL)
#
CONFIG_IP_DCCP_CCID2=m
# CONFIG_IP_DCCP_CCID2_DEBUG is not set
CONFIG_IP_DCCP_CCID3=m
# CONFIG_IP_DCCP_CCID3_DEBUG is not set
CONFIG_IP_DCCP_CCID3_RTO=100
CONFIG_IP_DCCP_TFRC_LIB=m

#
# DCCP Kernel Hacking
#
# CONFIG_IP_DCCP_DEBUG is not set
CONFIG_IP_SCTP=m
# CONFIG_SCTP_DBG_MSG is not set
# CONFIG_SCTP_DBG_OBJCNT is not set
# CONFIG_SCTP_HMAC_NONE is not set
# CONFIG_SCTP_HMAC_SHA1 is not set
CONFIG_SCTP_HMAC_MD5=y
CONFIG_TIPC=m
CONFIG_TIPC_ADVANCED=y
CONFIG_TIPC_ZONES=3
CONFIG_TIPC_CLUSTERS=1
CONFIG_TIPC_NODES=255
CONFIG_TIPC_SLAVE_NODES=0
CONFIG_TIPC_PORTS=8191
CONFIG_TIPC_LOG=0
# CONFIG_TIPC_DEBUG is not set
CONFIG_ATM=m
CONFIG_ATM_CLIP=m
# CONFIG_ATM_CLIP_NO_ICMP is not set
CONFIG_ATM_LANE=m
CONFIG_ATM_MPOA=m
CONFIG_ATM_BR2684=m
# CONFIG_ATM_BR2684_IPFILTER is not set
CONFIG_BRIDGE=m
CONFIG_VLAN_8021Q=m
CONFIG_DECNET=m
# CONFIG_DECNET_ROUTER is not set
CONFIG_LLC=y
CONFIG_LLC2=m
CONFIG_IPX=m
# CONFIG_IPX_INTERN is not set
CONFIG_ATALK=m
CONFIG_DEV_APPLETALK=m
CONFIG_IPDDP=m
CONFIG_IPDDP_ENCAP=y
CONFIG_IPDDP_DECAP=y
CONFIG_X25=m
CONFIG_LAPB=m
CONFIG_ECONET=m
CONFIG_ECONET_AUNUDP=y
CONFIG_ECONET_NATIVE=y
CONFIG_WAN_ROUTER=m
CONFIG_NET_SCHED=y

#
# Queueing/Scheduling
#
CONFIG_NET_SCH_CBQ=m
CONFIG_NET_SCH_HTB=m
CONFIG_NET_SCH_HFSC=m
CONFIG_NET_SCH_ATM=m
CONFIG_NET_SCH_PRIO=m
CONFIG_NET_SCH_RED=m
CONFIG_NET_SCH_SFQ=m
CONFIG_NET_SCH_TEQL=m
CONFIG_NET_SCH_TBF=m
CONFIG_NET_SCH_GRED=m
CONFIG_NET_SCH_DSMARK=m
CONFIG_NET_SCH_NETEM=m
CONFIG_NET_SCH_INGRESS=m

#
# Classification
#
CONFIG_NET_CLS=y
CONFIG_NET_CLS_BASIC=m
CONFIG_NET_CLS_TCINDEX=m
CONFIG_NET_CLS_ROUTE4=m
CONFIG_NET_CLS_ROUTE=y
CONFIG_NET_CLS_FW=m
CONFIG_NET_CLS_U32=m
CONFIG_CLS_U32_PERF=y
CONFIG_CLS_U32_MARK=y
CONFIG_NET_CLS_RSVP=m
CONFIG_NET_CLS_RSVP6=m
CONFIG_NET_CLS_FLOW=m
CONFIG_NET_EMATCH=y
CONFIG_NET_EMATCH_STACK=32
CONFIG_NET_EMATCH_CMP=m
CONFIG_NET_EMATCH_NBYTE=m
CONFIG_NET_EMATCH_U32=m
CONFIG_NET_EMATCH_META=m
CONFIG_NET_EMATCH_TEXT=m
CONFIG_NET_CLS_ACT=y
CONFIG_NET_ACT_POLICE=m
CONFIG_NET_ACT_GACT=m
CONFIG_GACT_PROB=y
CONFIG_NET_ACT_MIRRED=m
CONFIG_NET_ACT_IPT=m
CONFIG_NET_ACT_NAT=m
CONFIG_NET_ACT_PEDIT=m
CONFIG_NET_ACT_SIMP=m
CONFIG_NET_CLS_IND=y
CONFIG_NET_SCH_FIFO=y

#
# Network testing
#
CONFIG_NET_PKTGEN=m
CONFIG_HAMRADIO=y

#
# Packet Radio protocols
#
CONFIG_AX25=m
# CONFIG_AX25_DAMA_SLAVE is not set
CONFIG_NETROM=m
CONFIG_ROSE=m

#
# AX.25 network device drivers
#
CONFIG_MKISS=m
CONFIG_6PACK=m
CONFIG_BPQETHER=m
CONFIG_BAYCOM_SER_FDX=m
CONFIG_BAYCOM_SER_HDX=m
CONFIG_BAYCOM_PAR=m
CONFIG_CAN=m
CONFIG_CAN_RAW=m
CONFIG_CAN_BCM=m

#
# CAN Device Drivers
#
CONFIG_CAN_VCAN=m
# CONFIG_CAN_DEBUG_DEVICES is not set
CONFIG_IRDA=m

#
# IrDA protocols
#
CONFIG_IRLAN=m
CONFIG_IRNET=m
CONFIG_IRCOMM=m
# CONFIG_IRDA_ULTRA is not set

#
# IrDA options
#
CONFIG_IRDA_CACHE_LAST_LSAP=y
CONFIG_IRDA_FAST_RR=y
# CONFIG_IRDA_DEBUG is not set

#
# Infrared-port device drivers
#

#
# SIR device drivers
#
CONFIG_IRTTY_SIR=m

#
# Dongle support
#
CONFIG_DONGLE=y
CONFIG_ESI_DONGLE=m
CONFIG_ACTISYS_DONGLE=m
CONFIG_TEKRAM_DONGLE=m
CONFIG_TOIM3232_DONGLE=m
CONFIG_LITELINK_DONGLE=m
CONFIG_MA600_DONGLE=m
CONFIG_GIRBIL_DONGLE=m
CONFIG_MCP2120_DONGLE=m
CONFIG_OLD_BELKIN_DONGLE=m
CONFIG_ACT200L_DONGLE=m
CONFIG_KINGSUN_DONGLE=m
CONFIG_KSDAZZLE_DONGLE=m
CONFIG_KS959_DONGLE=m

#
# FIR device drivers
#
CONFIG_USB_IRDA=m
CONFIG_SIGMATEL_FIR=m
CONFIG_NSC_FIR=m
CONFIG_WINBOND_FIR=m
CONFIG_SMC_IRCC_FIR=m
CONFIG_ALI_FIR=m
CONFIG_VLSI_FIR=m
CONFIG_VIA_FIR=m
CONFIG_MCS_FIR=m
CONFIG_BT=m
CONFIG_BT_L2CAP=m
CONFIG_BT_SCO=m
CONFIG_BT_RFCOMM=m
CONFIG_BT_RFCOMM_TTY=y
CONFIG_BT_BNEP=m
CONFIG_BT_BNEP_MC_FILTER=y
CONFIG_BT_BNEP_PROTO_FILTER=y
CONFIG_BT_CMTP=m
CONFIG_BT_HIDP=m

#
# Bluetooth device drivers
#
CONFIG_BT_HCIUSB=m
CONFIG_BT_HCIUSB_SCO=y
CONFIG_BT_HCIBTSDIO=m
CONFIG_BT_HCIUART=m
CONFIG_BT_HCIUART_H4=y
CONFIG_BT_HCIUART_BCSP=y
CONFIG_BT_HCIUART_LL=y
CONFIG_BT_HCIBCM203X=m
CONFIG_BT_HCIBPA10X=m
CONFIG_BT_HCIBFUSB=m
CONFIG_BT_HCIDTL1=m
CONFIG_BT_HCIBT3C=m
CONFIG_BT_HCIBLUECARD=m
CONFIG_BT_HCIBTUART=m
CONFIG_BT_HCIVHCI=m
CONFIG_AF_RXRPC=m
# CONFIG_AF_RXRPC_DEBUG is not set
CONFIG_RXKAD=m
CONFIG_FIB_RULES=y

#
# Wireless
#
CONFIG_CFG80211=m
CONFIG_NL80211=y
CONFIG_WIRELESS_EXT=y
CONFIG_MAC80211=m

#
# Rate control algorithm selection
#
CONFIG_MAC80211_RC_DEFAULT_PID=y
# CONFIG_MAC80211_RC_DEFAULT_NONE is not set

#
# Selecting 'y' for an algorithm will
#

#
# build the algorithm into mac80211.
#
CONFIG_MAC80211_RC_DEFAULT="pid"
CONFIG_MAC80211_RC_PID=y
CONFIG_MAC80211_MESH=y
CONFIG_MAC80211_LEDS=y
# CONFIG_MAC80211_DEBUGFS is not set
# CONFIG_MAC80211_DEBUG_PACKET_ALIGNMENT is not set
# CONFIG_MAC80211_DEBUG is not set
CONFIG_IEEE80211=m
# CONFIG_IEEE80211_DEBUG is not set
CONFIG_IEEE80211_CRYPT_WEP=m
CONFIG_IEEE80211_CRYPT_CCMP=m
CONFIG_IEEE80211_CRYPT_TKIP=m
CONFIG_RFKILL=m
CONFIG_RFKILL_INPUT=m
CONFIG_RFKILL_LEDS=y
CONFIG_NET_9P=m
CONFIG_NET_9P_VIRTIO=m
# CONFIG_NET_9P_DEBUG is not set

#
# Device Drivers
#

#
# Generic Driver Options
#
CONFIG_UEVENT_HELPER_PATH="/sbin/hotplug"
CONFIG_STANDALONE=y
CONFIG_PREVENT_FIRMWARE_BUILD=y
CONFIG_FW_LOADER=m
# CONFIG_DEBUG_DRIVER is not set
# CONFIG_DEBUG_DEVRES is not set
# CONFIG_SYS_HYPERVISOR is not set
CONFIG_CONNECTOR=m
CONFIG_MTD=m
# CONFIG_MTD_DEBUG is not set
CONFIG_MTD_CONCAT=m
CONFIG_MTD_PARTITIONS=y
CONFIG_MTD_REDBOOT_PARTS=m
CONFIG_MTD_REDBOOT_DIRECTORY_BLOCK=-1
# CONFIG_MTD_REDBOOT_PARTS_UNALLOCATED is not set
# CONFIG_MTD_REDBOOT_PARTS_READONLY is not set
CONFIG_MTD_AR7_PARTS=m

#
# User Modules And Translation Layers
#
CONFIG_MTD_CHAR=m
CONFIG_MTD_BLKDEVS=m
CONFIG_MTD_BLOCK=m
CONFIG_MTD_BLOCK_RO=m
CONFIG_FTL=m
CONFIG_NFTL=m
CONFIG_NFTL_RW=y
CONFIG_INFTL=m
CONFIG_RFD_FTL=m
CONFIG_SSFDC=m
CONFIG_MTD_OOPS=m

#
# RAM/ROM/Flash chip drivers
#
CONFIG_MTD_CFI=m
CONFIG_MTD_JEDECPROBE=m
CONFIG_MTD_GEN_PROBE=m
# CONFIG_MTD_CFI_ADV_OPTIONS is not set
CONFIG_MTD_MAP_BANK_WIDTH_1=y
CONFIG_MTD_MAP_BANK_WIDTH_2=y
CONFIG_MTD_MAP_BANK_WIDTH_4=y
# CONFIG_MTD_MAP_BANK_WIDTH_8 is not set
# CONFIG_MTD_MAP_BANK_WIDTH_16 is not set
# CONFIG_MTD_MAP_BANK_WIDTH_32 is not set
CONFIG_MTD_CFI_I1=y
CONFIG_MTD_CFI_I2=y
# CONFIG_MTD_CFI_I4 is not set
# CONFIG_MTD_CFI_I8 is not set
CONFIG_MTD_CFI_INTELEXT=m
CONFIG_MTD_CFI_AMDSTD=m
CONFIG_MTD_CFI_STAA=m
CONFIG_MTD_CFI_UTIL=m
CONFIG_MTD_RAM=m
CONFIG_MTD_ROM=m
CONFIG_MTD_ABSENT=m

#
# Mapping drivers for chip access
#
CONFIG_MTD_COMPLEX_MAPPINGS=y
CONFIG_MTD_PHYSMAP=m
CONFIG_MTD_PHYSMAP_START=0x8000000
CONFIG_MTD_PHYSMAP_LEN=0x4000000
CONFIG_MTD_PHYSMAP_BANKWIDTH=2
CONFIG_MTD_SC520CDP=m
CONFIG_MTD_NETSC520=m
CONFIG_MTD_TS5500=m
CONFIG_MTD_SBC_GXX=m
# CONFIG_MTD_AMD76XROM is not set
# CONFIG_MTD_ICHXROM is not set
# CONFIG_MTD_ESB2ROM is not set
# CONFIG_MTD_CK804XROM is not set
# CONFIG_MTD_SCB2_FLASH is not set
CONFIG_MTD_NETtel=m
CONFIG_MTD_DILNETPC=m
CONFIG_MTD_DILNETPC_BOOTSIZE=0x80000
# CONFIG_MTD_L440GX is not set
CONFIG_MTD_PCI=m
CONFIG_MTD_INTEL_VR_NOR=m
CONFIG_MTD_PLATRAM=m

#
# Self-contained MTD device drivers
#
CONFIG_MTD_PMC551=m
# CONFIG_MTD_PMC551_BUGFIX is not set
# CONFIG_MTD_PMC551_DEBUG is not set
CONFIG_MTD_DATAFLASH=m
CONFIG_MTD_M25P80=m
CONFIG_M25PXX_USE_FAST_READ=y
CONFIG_MTD_SLRAM=m
CONFIG_MTD_PHRAM=m
CONFIG_MTD_MTDRAM=m
CONFIG_MTDRAM_TOTAL_SIZE=4096
CONFIG_MTDRAM_ERASE_SIZE=128
CONFIG_MTD_BLOCK2MTD=m

#
# Disk-On-Chip Device Drivers
#
CONFIG_MTD_DOC2000=m
CONFIG_MTD_DOC2001=m
CONFIG_MTD_DOC2001PLUS=m
CONFIG_MTD_DOCPROBE=m
CONFIG_MTD_DOCECC=m
# CONFIG_MTD_DOCPROBE_ADVANCED is not set
CONFIG_MTD_DOCPROBE_ADDRESS=0
CONFIG_MTD_NAND=m
# CONFIG_MTD_NAND_VERIFY_WRITE is not set
# CONFIG_MTD_NAND_ECC_SMC is not set
# CONFIG_MTD_NAND_MUSEUM_IDS is not set
CONFIG_MTD_NAND_IDS=m
CONFIG_MTD_NAND_DISKONCHIP=m
# CONFIG_MTD_NAND_DISKONCHIP_PROBE_ADVANCED is not set
CONFIG_MTD_NAND_DISKONCHIP_PROBE_ADDRESS=0
# CONFIG_MTD_NAND_DISKONCHIP_BBTWRITE is not set
CONFIG_MTD_NAND_CAFE=m
# CONFIG_MTD_NAND_NANDSIM is not set
CONFIG_MTD_NAND_PLATFORM=m
CONFIG_MTD_ALAUDA=m
CONFIG_MTD_ONENAND=m
CONFIG_MTD_ONENAND_VERIFY_WRITE=y
# CONFIG_MTD_ONENAND_OTP is not set
CONFIG_MTD_ONENAND_2X_PROGRAM=y
CONFIG_MTD_ONENAND_SIM=m

#
# UBI - Unsorted block images
#
CONFIG_MTD_UBI=m
CONFIG_MTD_UBI_WL_THRESHOLD=4096
CONFIG_MTD_UBI_BEB_RESERVE=1
# CONFIG_MTD_UBI_GLUEBI is not set

#
# UBI debugging options
#
# CONFIG_MTD_UBI_DEBUG is not set
CONFIG_PARPORT=m
CONFIG_PARPORT_PC=m
CONFIG_PARPORT_SERIAL=m
# CONFIG_PARPORT_PC_FIFO is not set
# CONFIG_PARPORT_PC_SUPERIO is not set
CONFIG_PARPORT_PC_PCMCIA=m
# CONFIG_PARPORT_GSC is not set
CONFIG_PARPORT_AX88796=m
CONFIG_PARPORT_1284=y
CONFIG_PARPORT_NOT_PC=y
CONFIG_PNP=y
CONFIG_PNP_DEBUG=y

#
# Protocols
#
CONFIG_PNPACPI=y
CONFIG_BLK_DEV=y
CONFIG_BLK_DEV_FD=m
CONFIG_PARIDE=m

#
# Parallel IDE high-level drivers
#
CONFIG_PARIDE_PD=m
CONFIG_PARIDE_PCD=m
CONFIG_PARIDE_PF=m
CONFIG_PARIDE_PT=m
CONFIG_PARIDE_PG=m

#
# Parallel IDE protocol modules
#
CONFIG_PARIDE_ATEN=m
CONFIG_PARIDE_BPCK=m
CONFIG_PARIDE_COMM=m
CONFIG_PARIDE_DSTR=m
CONFIG_PARIDE_FIT2=m
CONFIG_PARIDE_FIT3=m
CONFIG_PARIDE_EPAT=m
# CONFIG_PARIDE_EPATC8 is not set
CONFIG_PARIDE_EPIA=m
CONFIG_PARIDE_FRIQ=m
CONFIG_PARIDE_FRPW=m
CONFIG_PARIDE_KBIC=m
CONFIG_PARIDE_KTTI=m
CONFIG_PARIDE_ON20=m
CONFIG_PARIDE_ON26=m
CONFIG_BLK_CPQ_DA=m
CONFIG_BLK_CPQ_CISS_DA=m
CONFIG_CISS_SCSI_TAPE=y
CONFIG_BLK_DEV_DAC960=m
CONFIG_BLK_DEV_UMEM=m
# CONFIG_BLK_DEV_COW_COMMON is not set
CONFIG_BLK_DEV_LOOP=m
CONFIG_BLK_DEV_CRYPTOLOOP=m
CONFIG_BLK_DEV_NBD=m
CONFIG_BLK_DEV_SX8=m
# CONFIG_BLK_DEV_UB is not set
CONFIG_BLK_DEV_RAM=y
CONFIG_BLK_DEV_RAM_COUNT=16
CONFIG_BLK_DEV_RAM_SIZE=65536
# CONFIG_BLK_DEV_XIP is not set
CONFIG_CDROM_PKTCDVD=m
CONFIG_CDROM_PKTCDVD_BUFFERS=8
# CONFIG_CDROM_PKTCDVD_WCACHE is not set
CONFIG_ATA_OVER_ETH=m
CONFIG_VIRTIO_BLK=m
CONFIG_MISC_DEVICES=y
CONFIG_IBM_ASM=m
CONFIG_PHANTOM=m
CONFIG_EEPROM_93CX6=m
CONFIG_SGI_IOC4=m
CONFIG_TIFM_CORE=m
CONFIG_TIFM_7XX1=m
CONFIG_ACER_WMI=m
CONFIG_ASUS_LAPTOP=m
CONFIG_FUJITSU_LAPTOP=m
CONFIG_MSI_LAPTOP=m
CONFIG_SONY_LAPTOP=m
CONFIG_SONYPI_COMPAT=y
CONFIG_THINKPAD_ACPI=m
# CONFIG_THINKPAD_ACPI_DEBUG is not set
CONFIG_THINKPAD_ACPI_BAY=y
CONFIG_THINKPAD_ACPI_VIDEO=y
CONFIG_THINKPAD_ACPI_HOTKEY_POLL=y
# CONFIG_INTEL_MENLOW is not set
CONFIG_EEEPC_LAPTOP=m
CONFIG_ENCLOSURE_SERVICES=m
CONFIG_HP_ILO=m
CONFIG_HAVE_IDE=y
CONFIG_IDE=m
CONFIG_BLK_DEV_IDE=m

#
# Please see Documentation/ide/ide.txt for help/info on IDE drives
#
# CONFIG_BLK_DEV_IDE_SATA is not set
CONFIG_BLK_DEV_IDEDISK=m
# CONFIG_IDEDISK_MULTI_MODE is not set
CONFIG_BLK_DEV_IDECS=m
CONFIG_BLK_DEV_DELKIN=m
CONFIG_BLK_DEV_IDECD=m
CONFIG_BLK_DEV_IDECD_VERBOSE_ERRORS=y
CONFIG_BLK_DEV_IDETAPE=m
CONFIG_BLK_DEV_IDEFLOPPY=m
# CONFIG_BLK_DEV_IDESCSI is not set
CONFIG_BLK_DEV_IDEACPI=y
# CONFIG_IDE_TASK_IOCTL is not set
CONFIG_IDE_PROC_FS=y

#
# IDE chipset support/bugfixes
#
CONFIG_IDE_GENERIC=m
# CONFIG_BLK_DEV_PLATFORM is not set
CONFIG_BLK_DEV_CMD640=m
# CONFIG_BLK_DEV_CMD640_ENHANCED is not set
CONFIG_BLK_DEV_IDEPNP=m
CONFIG_BLK_DEV_IDEDMA_SFF=y

#
# PCI IDE chipsets support
#
CONFIG_BLK_DEV_IDEPCI=y
# CONFIG_BLK_DEV_OFFBOARD is not set
CONFIG_BLK_DEV_GENERIC=m
CONFIG_BLK_DEV_OPTI621=m
CONFIG_BLK_DEV_RZ1000=m
CONFIG_BLK_DEV_IDEDMA_PCI=y
CONFIG_BLK_DEV_AEC62XX=m
CONFIG_BLK_DEV_ALI15X3=m
CONFIG_BLK_DEV_AMD74XX=m
CONFIG_BLK_DEV_ATIIXP=m
CONFIG_BLK_DEV_CMD64X=m
CONFIG_BLK_DEV_TRIFLEX=m
CONFIG_BLK_DEV_CY82C693=m
CONFIG_BLK_DEV_CS5520=m
CONFIG_BLK_DEV_CS5530=m
CONFIG_BLK_DEV_HPT34X=m
# CONFIG_HPT34X_AUTODMA is not set
CONFIG_BLK_DEV_HPT366=m
CONFIG_BLK_DEV_JMICRON=m
CONFIG_BLK_DEV_SC1200=m
CONFIG_BLK_DEV_PIIX=m
CONFIG_BLK_DEV_IT8213=m
CONFIG_BLK_DEV_IT821X=m
CONFIG_BLK_DEV_NS87415=m
CONFIG_BLK_DEV_PDC202XX_OLD=m
CONFIG_BLK_DEV_PDC202XX_NEW=m
CONFIG_BLK_DEV_SVWKS=m
CONFIG_BLK_DEV_SIIMAGE=m
CONFIG_BLK_DEV_SIS5513=m
CONFIG_BLK_DEV_SLC90E66=m
CONFIG_BLK_DEV_TRM290=m
CONFIG_BLK_DEV_VIA82CXXX=m
CONFIG_BLK_DEV_TC86C001=m
CONFIG_BLK_DEV_IDEDMA=y
# CONFIG_BLK_DEV_HD_ONLY is not set
# CONFIG_BLK_DEV_HD is not set

#
# SCSI device support
#
CONFIG_RAID_ATTRS=m
CONFIG_SCSI=m
CONFIG_SCSI_DMA=y
CONFIG_SCSI_TGT=m
CONFIG_SCSI_NETLINK=y
CONFIG_SCSI_PROC_FS=y

#
# SCSI support type (disk, tape, CD-ROM)
#
CONFIG_BLK_DEV_SD=m
CONFIG_CHR_DEV_ST=m
CONFIG_CHR_DEV_OSST=m
CONFIG_BLK_DEV_SR=m
CONFIG_BLK_DEV_SR_VENDOR=y
CONFIG_CHR_DEV_SG=m
CONFIG_CHR_DEV_SCH=m
CONFIG_SCSI_ENCLOSURE=m

#
# Some SCSI devices (e.g. CD jukebox) support multiple LUNs
#
CONFIG_SCSI_MULTI_LUN=y
CONFIG_SCSI_CONSTANTS=y
CONFIG_SCSI_LOGGING=y
CONFIG_SCSI_SCAN_ASYNC=y
CONFIG_SCSI_WAIT_SCAN=m

#
# SCSI Transports
#
CONFIG_SCSI_SPI_ATTRS=m
CONFIG_SCSI_FC_ATTRS=m
CONFIG_SCSI_FC_TGT_ATTRS=y
CONFIG_SCSI_ISCSI_ATTRS=m
CONFIG_SCSI_SAS_ATTRS=m
CONFIG_SCSI_SAS_LIBSAS=m
CONFIG_SCSI_SAS_ATA=y
CONFIG_SCSI_SAS_HOST_SMP=y
# CONFIG_SCSI_SAS_LIBSAS_DEBUG is not set
CONFIG_SCSI_SRP_ATTRS=m
CONFIG_SCSI_SRP_TGT_ATTRS=y
CONFIG_SCSI_LOWLEVEL=y
CONFIG_ISCSI_TCP=m
CONFIG_BLK_DEV_3W_XXXX_RAID=m
CONFIG_SCSI_3W_9XXX=m
CONFIG_SCSI_ACARD=m
CONFIG_SCSI_AACRAID=m
CONFIG_SCSI_AIC7XXX=m
CONFIG_AIC7XXX_CMDS_PER_DEVICE=8
CONFIG_AIC7XXX_RESET_DELAY_MS=15000
CONFIG_AIC7XXX_DEBUG_ENABLE=y
CONFIG_AIC7XXX_DEBUG_MASK=0
CONFIG_AIC7XXX_REG_PRETTY_PRINT=y
CONFIG_SCSI_AIC7XXX_OLD=m
CONFIG_SCSI_AIC79XX=m
CONFIG_AIC79XX_CMDS_PER_DEVICE=32
CONFIG_AIC79XX_RESET_DELAY_MS=15000
CONFIG_AIC79XX_DEBUG_ENABLE=y
CONFIG_AIC79XX_DEBUG_MASK=0
CONFIG_AIC79XX_REG_PRETTY_PRINT=y
CONFIG_SCSI_AIC94XX=m
# CONFIG_AIC94XX_DEBUG is not set
CONFIG_SCSI_DPT_I2O=m
CONFIG_SCSI_ADVANSYS=m
CONFIG_SCSI_ARCMSR=m
# CONFIG_SCSI_ARCMSR_AER is not set
CONFIG_MEGARAID_NEWGEN=y
CONFIG_MEGARAID_MM=m
CONFIG_MEGARAID_MAILBOX=m
CONFIG_MEGARAID_LEGACY=m
CONFIG_MEGARAID_SAS=m
CONFIG_SCSI_HPTIOP=m
CONFIG_SCSI_BUSLOGIC=m
CONFIG_SCSI_DMX3191D=m
CONFIG_SCSI_EATA=m
CONFIG_SCSI_EATA_TAGGED_QUEUE=y
CONFIG_SCSI_EATA_LINKED_COMMANDS=y
CONFIG_SCSI_EATA_MAX_TAGS=16
CONFIG_SCSI_FUTURE_DOMAIN=m
CONFIG_SCSI_GDTH=m
CONFIG_SCSI_IPS=m
CONFIG_SCSI_INITIO=m
CONFIG_SCSI_INIA100=m
CONFIG_SCSI_PPA=m
CONFIG_SCSI_IMM=m
# CONFIG_SCSI_IZIP_EPP16 is not set
# CONFIG_SCSI_IZIP_SLOW_CTR is not set
CONFIG_SCSI_MVSAS=m
CONFIG_SCSI_STEX=m
CONFIG_SCSI_SYM53C8XX_2=m
CONFIG_SCSI_SYM53C8XX_DMA_ADDRESSING_MODE=1
CONFIG_SCSI_SYM53C8XX_DEFAULT_TAGS=16
CONFIG_SCSI_SYM53C8XX_MAX_TAGS=64
CONFIG_SCSI_SYM53C8XX_MMIO=y
CONFIG_SCSI_IPR=m
# CONFIG_SCSI_IPR_TRACE is not set
# CONFIG_SCSI_IPR_DUMP is not set
CONFIG_SCSI_QLOGIC_1280=m
CONFIG_SCSI_QLA_FC=m
CONFIG_SCSI_QLA_ISCSI=m
CONFIG_SCSI_LPFC=m
CONFIG_SCSI_DC395x=m
CONFIG_SCSI_DC390T=m
CONFIG_SCSI_DEBUG=m
CONFIG_SCSI_SRP=m
CONFIG_SCSI_LOWLEVEL_PCMCIA=y
CONFIG_PCMCIA_FDOMAIN=m
CONFIG_PCMCIA_QLOGIC=m
CONFIG_PCMCIA_SYM53C500=m
CONFIG_ATA=m
# CONFIG_ATA_NONSTANDARD is not set
CONFIG_ATA_ACPI=y
CONFIG_SATA_PMP=y
CONFIG_SATA_AHCI=m
CONFIG_SATA_SIL24=m
CONFIG_ATA_SFF=y
CONFIG_SATA_SVW=m
CONFIG_ATA_PIIX=m
CONFIG_SATA_MV=m
CONFIG_SATA_NV=m
CONFIG_PDC_ADMA=m
CONFIG_SATA_QSTOR=m
CONFIG_SATA_PROMISE=m
CONFIG_SATA_SX4=m
CONFIG_SATA_SIL=m
CONFIG_SATA_SIS=m
CONFIG_SATA_ULI=m
CONFIG_SATA_VIA=m
CONFIG_SATA_VITESSE=m
CONFIG_SATA_INIC162X=m
# CONFIG_PATA_ACPI is not set
# CONFIG_PATA_ALI is not set
# CONFIG_PATA_AMD is not set
CONFIG_PATA_ARTOP=m
# CONFIG_PATA_ATIIXP is not set
# CONFIG_PATA_CMD640_PCI is not set
# CONFIG_PATA_CMD64X is not set
# CONFIG_PATA_CS5520 is not set
# CONFIG_PATA_CS5530 is not set
# CONFIG_PATA_CYPRESS is not set
# CONFIG_PATA_EFAR is not set
CONFIG_ATA_GENERIC=m
# CONFIG_PATA_HPT366 is not set
# CONFIG_PATA_HPT37X is not set
# CONFIG_PATA_HPT3X2N is not set
# CONFIG_PATA_HPT3X3 is not set
# CONFIG_PATA_IT821X is not set
# CONFIG_PATA_IT8213 is not set
# CONFIG_PATA_JMICRON is not set
# CONFIG_PATA_TRIFLEX is not set
CONFIG_PATA_MARVELL=m
# CONFIG_PATA_MPIIX is not set
# CONFIG_PATA_OLDPIIX is not set
# CONFIG_PATA_NETCELL is not set
# CONFIG_PATA_NINJA32 is not set
# CONFIG_PATA_NS87410 is not set
# CONFIG_PATA_NS87415 is not set
# CONFIG_PATA_OPTI is not set
# CONFIG_PATA_OPTIDMA is not set
# CONFIG_PATA_PCMCIA is not set
# CONFIG_PATA_PDC_OLD is not set
# CONFIG_PATA_RADISYS is not set
# CONFIG_PATA_RZ1000 is not set
# CONFIG_PATA_SC1200 is not set
# CONFIG_PATA_SERVERWORKS is not set
# CONFIG_PATA_PDC2027X is not set
# CONFIG_PATA_SIL680 is not set
CONFIG_PATA_SIS_STUB=m
# CONFIG_PATA_SIS is not set
# CONFIG_PATA_VIA is not set
# CONFIG_PATA_WINBOND is not set
CONFIG_PATA_SCH=m
CONFIG_MD=y
CONFIG_BLK_DEV_MD=m
CONFIG_MD_LINEAR=m
CONFIG_MD_RAID0=m
CONFIG_MD_RAID1=m
CONFIG_MD_RAID10=m
CONFIG_MD_RAID456=m
CONFIG_MD_RAID5_RESHAPE=y
CONFIG_MD_MULTIPATH=m
CONFIG_MD_FAULTY=m
CONFIG_BLK_DEV_DM=m
# CONFIG_DM_DEBUG is not set
CONFIG_DM_CRYPT=m
CONFIG_DM_SNAPSHOT=m
CONFIG_DM_MIRROR=m
CONFIG_DM_ZERO=m
CONFIG_DM_MULTIPATH=m
CONFIG_DM_MULTIPATH_EMC=m
CONFIG_DM_MULTIPATH_RDAC=m
CONFIG_DM_MULTIPATH_HP=m
CONFIG_DM_DELAY=m
CONFIG_DM_UEVENT=y
CONFIG_FUSION=y
CONFIG_FUSION_SPI=m
CONFIG_FUSION_FC=m
CONFIG_FUSION_SAS=m
CONFIG_FUSION_MAX_SGE=40
CONFIG_FUSION_CTL=m
CONFIG_FUSION_LAN=m
# CONFIG_FUSION_LOGGING is not set

#
# IEEE 1394 (FireWire) support
#

#
# Enable only one of the two stacks, unless you know what you are doing
#
# CONFIG_FIREWIRE is not set
CONFIG_IEEE1394=m
CONFIG_IEEE1394_OHCI1394=m
CONFIG_IEEE1394_PCILYNX=m
CONFIG_IEEE1394_SBP2=m
# CONFIG_IEEE1394_SBP2_PHYS_DMA is not set
CONFIG_IEEE1394_ETH1394_ROM_ENTRY=y
CONFIG_IEEE1394_ETH1394=m
CONFIG_IEEE1394_RAWIO=m
CONFIG_IEEE1394_VIDEO1394=m
CONFIG_IEEE1394_DV1394=m
# CONFIG_IEEE1394_VERBOSEDEBUG is not set
CONFIG_I2O=m
CONFIG_I2O_LCT_NOTIFY_ON_CHANGES=y
CONFIG_I2O_EXT_ADAPTEC=y
CONFIG_I2O_EXT_ADAPTEC_DMA64=y
CONFIG_I2O_CONFIG=m
CONFIG_I2O_CONFIG_OLD_IOCTL=y
CONFIG_I2O_BUS=m
CONFIG_I2O_BLOCK=m
CONFIG_I2O_SCSI=m
CONFIG_I2O_PROC=m
CONFIG_MACINTOSH_DRIVERS=y
CONFIG_MAC_EMUMOUSEBTN=y
CONFIG_NETDEVICES=y
CONFIG_NETDEVICES_MULTIQUEUE=y
CONFIG_IFB=m
CONFIG_DUMMY=m
CONFIG_BONDING=m
# CONFIG_MACVLAN is not set
CONFIG_EQUALIZER=m
CONFIG_TUN=m
CONFIG_VETH=m
CONFIG_NET_SB1000=m
CONFIG_ARCNET=m
CONFIG_ARCNET_1201=m
CONFIG_ARCNET_1051=m
CONFIG_ARCNET_RAW=m
CONFIG_ARCNET_CAP=m
CONFIG_ARCNET_COM90xx=m
CONFIG_ARCNET_COM90xxIO=m
CONFIG_ARCNET_RIM_I=m
CONFIG_ARCNET_COM20020=m
CONFIG_ARCNET_COM20020_PCI=m
CONFIG_PHYLIB=m

#
# MII PHY device drivers
#
CONFIG_MARVELL_PHY=m
CONFIG_DAVICOM_PHY=m
CONFIG_QSEMI_PHY=m
CONFIG_LXT_PHY=m
CONFIG_CICADA_PHY=m
CONFIG_VITESSE_PHY=m
CONFIG_SMSC_PHY=m
CONFIG_BROADCOM_PHY=m
CONFIG_ICPLUS_PHY=m
CONFIG_REALTEK_PHY=m
CONFIG_MDIO_BITBANG=m
CONFIG_NET_ETHERNET=y
CONFIG_MII=m
CONFIG_HAPPYMEAL=m
CONFIG_SUNGEM=m
CONFIG_CASSINI=m
CONFIG_NET_VENDOR_3COM=y
CONFIG_VORTEX=m
CONFIG_TYPHOON=m
CONFIG_ENC28J60=m
# CONFIG_ENC28J60_WRITEVERIFY is not set
CONFIG_NET_TULIP=y
CONFIG_DE2104X=m
CONFIG_TULIP=m
# CONFIG_TULIP_MWI is not set
# CONFIG_TULIP_MMIO is not set
CONFIG_TULIP_NAPI=y
CONFIG_TULIP_NAPI_HW_MITIGATION=y
CONFIG_DE4X5=m
CONFIG_WINBOND_840=m
CONFIG_DM9102=m
CONFIG_ULI526X=m
CONFIG_PCMCIA_XIRCOM=m
CONFIG_HP100=m
# CONFIG_IBM_NEW_EMAC_ZMII is not set
# CONFIG_IBM_NEW_EMAC_RGMII is not set
# CONFIG_IBM_NEW_EMAC_TAH is not set
# CONFIG_IBM_NEW_EMAC_EMAC4 is not set
CONFIG_NET_PCI=y
CONFIG_PCNET32=m
CONFIG_AMD8111_ETH=m
CONFIG_AMD8111E_NAPI=y
CONFIG_ADAPTEC_STARFIRE=m
CONFIG_ADAPTEC_STARFIRE_NAPI=y
CONFIG_B44=m
CONFIG_B44_PCI_AUTOSELECT=y
CONFIG_B44_PCICORE_AUTOSELECT=y
CONFIG_B44_PCI=y
CONFIG_FORCEDETH=m
# CONFIG_FORCEDETH_NAPI is not set
CONFIG_EEPRO100=m
CONFIG_E100=m
CONFIG_FEALNX=m
CONFIG_NATSEMI=m
CONFIG_NE2K_PCI=m
CONFIG_8139CP=m
CONFIG_8139TOO=m
# CONFIG_8139TOO_PIO is not set
CONFIG_8139TOO_TUNE_TWISTER=y
CONFIG_8139TOO_8129=y
# CONFIG_8139_OLD_RX_RESET is not set
CONFIG_R6040=m
CONFIG_SIS900=m
CONFIG_EPIC100=m
CONFIG_SUNDANCE=m
# CONFIG_SUNDANCE_MMIO is not set
CONFIG_VIA_RHINE=m
# CONFIG_VIA_RHINE_MMIO is not set
CONFIG_VIA_RHINE_NAPI=y
CONFIG_SC92031=m
# CONFIG_NET_POCKET is not set
CONFIG_NETDEV_1000=y
CONFIG_ACENIC=m
# CONFIG_ACENIC_OMIT_TIGON_I is not set
CONFIG_DL2K=m
CONFIG_E1000=m
CONFIG_E1000_NAPI=y
# CONFIG_E1000_DISABLE_PACKET_SPLIT is not set
CONFIG_E1000E=m
CONFIG_E1000E_ENABLED=y
CONFIG_IP1000=m
CONFIG_IGB=m
CONFIG_NS83820=m
CONFIG_HAMACHI=m
CONFIG_YELLOWFIN=m
CONFIG_R8169=m
CONFIG_R8169_NAPI=y
CONFIG_R8169_VLAN=y
CONFIG_SIS190=m
CONFIG_SKGE=m
# CONFIG_SKGE_DEBUG is not set
CONFIG_SKY2=m
# CONFIG_SKY2_DEBUG is not set
CONFIG_VIA_VELOCITY=m
CONFIG_TIGON3=m
CONFIG_BNX2=m
CONFIG_QLA3XXX=m
CONFIG_ATL1=m
CONFIG_ATL1E=m
CONFIG_NETDEV_10000=y
CONFIG_CHELSIO_T1=m
CONFIG_CHELSIO_T1_1G=y
CONFIG_CHELSIO_T1_NAPI=y
CONFIG_CHELSIO_T3=m
CONFIG_IXGBE=m
CONFIG_IXGB=m
CONFIG_IXGB_NAPI=y
CONFIG_S2IO=m
CONFIG_S2IO_NAPI=y
CONFIG_MYRI10GE=m
CONFIG_NETXEN_NIC=m
CONFIG_NIU=m
CONFIG_MLX4_CORE=m
CONFIG_MLX4_DEBUG=y
CONFIG_TEHUTI=m
CONFIG_SFC=m
CONFIG_TR=y
CONFIG_IBMOL=m
CONFIG_TMS380TR=m
CONFIG_TMSPCI=m
CONFIG_ABYSS=m

#
# Wireless LAN
#
CONFIG_WLAN_PRE80211=y
CONFIG_STRIP=m
CONFIG_PCMCIA_WAVELAN=m
CONFIG_PCMCIA_NETWAVE=m
CONFIG_WLAN_80211=y
CONFIG_PCMCIA_RAYCS=m
# CONFIG_IPW2100 is not set
CONFIG_IPW2200=m
CONFIG_IPW2200_MONITOR=y
CONFIG_IPW2200_RADIOTAP=y
CONFIG_IPW2200_PROMISCUOUS=y
CONFIG_IPW2200_QOS=y
# CONFIG_IPW2200_DEBUG is not set
CONFIG_LIBERTAS=m
CONFIG_LIBERTAS_USB=m
CONFIG_LIBERTAS_CS=m
CONFIG_LIBERTAS_SDIO=m
# CONFIG_LIBERTAS_DEBUG is not set
CONFIG_AIRO=m
CONFIG_HERMES=m
CONFIG_PLX_HERMES=m
CONFIG_TMD_HERMES=m
CONFIG_NORTEL_HERMES=m
CONFIG_PCI_HERMES=m
CONFIG_PCMCIA_HERMES=m
CONFIG_PCMCIA_SPECTRUM=m
CONFIG_ATMEL=m
CONFIG_PCI_ATMEL=m
CONFIG_PCMCIA_ATMEL=m
CONFIG_USB_ATMEL=m
CONFIG_AIRO_CS=m
CONFIG_PCMCIA_WL3501=m
# CONFIG_PRISM54 is not set
CONFIG_USB_ZD1201=m
CONFIG_USB_NET_RNDIS_WLAN=m
CONFIG_RTL8180=m
CONFIG_RTL8187=m
CONFIG_ADM8211=m
CONFIG_P54_COMMON=m
CONFIG_P54_USB=m
CONFIG_P54_PCI=m
CONFIG_ATH5K=m
# CONFIG_ATH5K_DEBUG is not set
CONFIG_IWLWIFI=m
CONFIG_IWLCORE=m
CONFIG_IWLWIFI_LEDS=y
CONFIG_IWLWIFI_RFKILL=y
CONFIG_IWL4965=m
CONFIG_IWL4965_HT=y
CONFIG_IWL4965_LEDS=y
CONFIG_IWL4965_SPECTRUM_MEASUREMENT=y
CONFIG_IWL4965_SENSITIVITY=y
# CONFIG_IWLWIFI_DEBUG is not set
CONFIG_IWL3945=m
CONFIG_IWL3945_SPECTRUM_MEASUREMENT=y
CONFIG_IWL3945_LEDS=y
# CONFIG_IWL3945_DEBUG is not set
CONFIG_HOSTAP=m
CONFIG_HOSTAP_FIRMWARE=y
# CONFIG_HOSTAP_FIRMWARE_NVRAM is not set
CONFIG_HOSTAP_PLX=m
CONFIG_HOSTAP_PCI=m
CONFIG_HOSTAP_CS=m
CONFIG_B43=m
CONFIG_B43_PCI_AUTOSELECT=y
CONFIG_B43_PCICORE_AUTOSELECT=y
CONFIG_B43_PCMCIA=y
CONFIG_B43_PIO=y
CONFIG_B43_LEDS=y
CONFIG_B43_RFKILL=y
# CONFIG_B43_DEBUG is not set
CONFIG_B43LEGACY=m
CONFIG_B43LEGACY_PCI_AUTOSELECT=y
CONFIG_B43LEGACY_PCICORE_AUTOSELECT=y
CONFIG_B43LEGACY_LEDS=y
CONFIG_B43LEGACY_RFKILL=y
CONFIG_B43LEGACY_DEBUG=y
CONFIG_B43LEGACY_DMA=y
CONFIG_B43LEGACY_PIO=y
CONFIG_B43LEGACY_DMA_AND_PIO_MODE=y
# CONFIG_B43LEGACY_DMA_MODE is not set
# CONFIG_B43LEGACY_PIO_MODE is not set
CONFIG_ZD1211RW=m
# CONFIG_ZD1211RW_DEBUG is not set
CONFIG_RT2X00=m
CONFIG_RT2X00_LIB=m
CONFIG_RT2X00_LIB_PCI=m
CONFIG_RT2X00_LIB_USB=m
CONFIG_RT2X00_LIB_FIRMWARE=y
CONFIG_RT2X00_LIB_RFKILL=y
CONFIG_RT2X00_LIB_LEDS=y
CONFIG_RT2400PCI=m
CONFIG_RT2400PCI_RFKILL=y
CONFIG_RT2400PCI_LEDS=y
CONFIG_RT2500PCI=m
CONFIG_RT2500PCI_RFKILL=y
CONFIG_RT2500PCI_LEDS=y
CONFIG_RT61PCI=m
CONFIG_RT61PCI_RFKILL=y
CONFIG_RT61PCI_LEDS=y
CONFIG_RT2500USB=m
CONFIG_RT2500USB_LEDS=y
CONFIG_RT73USB=m
CONFIG_RT73USB_LEDS=y
# CONFIG_RT2X00_DEBUG is not set

#
# USB Network Adapters
#
CONFIG_USB_CATC=m
CONFIG_USB_KAWETH=m
CONFIG_USB_PEGASUS=m
CONFIG_USB_RTL8150=m
CONFIG_USB_USBNET=m
CONFIG_USB_NET_AX8817X=m
CONFIG_USB_NET_CDCETHER=m
CONFIG_USB_NET_DM9601=m
CONFIG_USB_NET_GL620A=m
CONFIG_USB_NET_NET1080=m
CONFIG_USB_NET_PLUSB=m
CONFIG_USB_NET_MCS7830=m
CONFIG_USB_NET_RNDIS_HOST=m
CONFIG_USB_NET_CDC_SUBSET=m
CONFIG_USB_ALI_M5632=y
CONFIG_USB_AN2720=y
CONFIG_USB_BELKIN=y
CONFIG_USB_ARMLINUX=y
CONFIG_USB_EPSON2888=y
CONFIG_USB_KC2190=y
CONFIG_USB_NET_ZAURUS=m
CONFIG_NET_PCMCIA=y
CONFIG_PCMCIA_3C589=m
CONFIG_PCMCIA_3C574=m
CONFIG_PCMCIA_FMVJ18X=m
CONFIG_PCMCIA_PCNET=m
CONFIG_PCMCIA_NMCLAN=m
CONFIG_PCMCIA_SMC91C92=m
CONFIG_PCMCIA_XIRC2PS=m
CONFIG_PCMCIA_AXNET=m
CONFIG_ARCNET_COM20020_CS=m
CONFIG_WAN=y
CONFIG_LANMEDIA=m
CONFIG_HDLC=m
CONFIG_HDLC_RAW=m
CONFIG_HDLC_RAW_ETH=m
CONFIG_HDLC_CISCO=m
CONFIG_HDLC_FR=m
CONFIG_HDLC_PPP=m
CONFIG_HDLC_X25=m
CONFIG_PCI200SYN=m
CONFIG_WANXL=m
CONFIG_PC300=m
CONFIG_PC300_MLPPP=y

#
# Cyclades-PC300 MLPPP support is disabled.
#

#
# Refer to the file README.mlppp, provided by PC300 package.
#
# CONFIG_PC300TOO is not set
CONFIG_FARSYNC=m
CONFIG_DSCC4=m
CONFIG_DSCC4_PCISYNC=y
CONFIG_DSCC4_PCI_RST=y
CONFIG_DLCI=m
CONFIG_DLCI_MAX=8
CONFIG_WAN_ROUTER_DRIVERS=m
CONFIG_CYCLADES_SYNC=m
CONFIG_CYCLOMX_X25=y
CONFIG_LAPBETHER=m
CONFIG_X25_ASY=m
CONFIG_SBNI=m
# CONFIG_SBNI_MULTILINE is not set
CONFIG_ATM_DRIVERS=y
CONFIG_ATM_DUMMY=m
CONFIG_ATM_TCP=m
CONFIG_ATM_LANAI=m
CONFIG_ATM_ENI=m
# CONFIG_ATM_ENI_DEBUG is not set
# CONFIG_ATM_ENI_TUNE_BURST is not set
CONFIG_ATM_FIRESTREAM=m
CONFIG_ATM_ZATM=m
# CONFIG_ATM_ZATM_DEBUG is not set
CONFIG_ATM_IDT77252=m
# CONFIG_ATM_IDT77252_DEBUG is not set
# CONFIG_ATM_IDT77252_RCV_ALL is not set
CONFIG_ATM_IDT77252_USE_SUNI=y
CONFIG_ATM_HORIZON=m
# CONFIG_ATM_HORIZON_DEBUG is not set
CONFIG_ATM_FORE200E_MAYBE=m
CONFIG_ATM_HE=m
CONFIG_ATM_HE_USE_SUNI=y
CONFIG_FDDI=y
CONFIG_DEFXX=m
# CONFIG_DEFXX_MMIO is not set
CONFIG_SKFP=m
CONFIG_HIPPI=y
CONFIG_ROADRUNNER=m
# CONFIG_ROADRUNNER_LARGE_RINGS is not set
CONFIG_PLIP=m
CONFIG_PPP=m
CONFIG_PPP_MULTILINK=y
CONFIG_PPP_FILTER=y
CONFIG_PPP_ASYNC=m
CONFIG_PPP_SYNC_TTY=m
CONFIG_PPP_DEFLATE=m
CONFIG_PPP_BSDCOMP=m
CONFIG_PPP_MPPE=m
CONFIG_PPPOE=m
CONFIG_PPPOATM=m
CONFIG_PPPOL2TP=m
CONFIG_SLIP=m
CONFIG_SLIP_COMPRESSED=y
CONFIG_SLHC=m
CONFIG_SLIP_SMART=y
CONFIG_SLIP_MODE_SLIP6=y
CONFIG_NET_FC=y
CONFIG_NETCONSOLE=m
CONFIG_NETCONSOLE_DYNAMIC=y
CONFIG_NETPOLL=y
# CONFIG_NETPOLL_TRAP is not set
CONFIG_NET_POLL_CONTROLLER=y
CONFIG_VIRTIO_NET=m
CONFIG_ISDN=m
CONFIG_ISDN_I4L=m
CONFIG_ISDN_PPP=y
CONFIG_ISDN_PPP_VJ=y
CONFIG_ISDN_MPP=y
CONFIG_IPPP_FILTER=y
CONFIG_ISDN_PPP_BSDCOMP=m
CONFIG_ISDN_AUDIO=y
CONFIG_ISDN_TTY_FAX=y
CONFIG_ISDN_X25=y

#
# ISDN feature submodules
#
CONFIG_ISDN_DIVERSION=m

#
# ISDN4Linux hardware drivers
#

#
# Passive cards
#
CONFIG_ISDN_DRV_HISAX=m

#
# D-channel protocol features
#
CONFIG_HISAX_EURO=y
CONFIG_DE_AOC=y
# CONFIG_HISAX_NO_SENDCOMPLETE is not set
# CONFIG_HISAX_NO_LLC is not set
# CONFIG_HISAX_NO_KEYPAD is not set
CONFIG_HISAX_1TR6=y
CONFIG_HISAX_NI1=y
CONFIG_HISAX_MAX_CARDS=8

#
# HiSax supported cards
#
CONFIG_HISAX_16_3=y
CONFIG_HISAX_TELESPCI=y
CONFIG_HISAX_S0BOX=y
CONFIG_HISAX_FRITZPCI=y
CONFIG_HISAX_AVM_A1_PCMCIA=y
CONFIG_HISAX_ELSA=y
CONFIG_HISAX_DIEHLDIVA=y
CONFIG_HISAX_SEDLBAUER=y
CONFIG_HISAX_NETJET=y
CONFIG_HISAX_NETJET_U=y
CONFIG_HISAX_NICCY=y
CONFIG_HISAX_BKM_A4T=y
CONFIG_HISAX_SCT_QUADRO=y
CONFIG_HISAX_GAZEL=y
CONFIG_HISAX_HFC_PCI=y
CONFIG_HISAX_W6692=y
CONFIG_HISAX_HFC_SX=y
CONFIG_HISAX_ENTERNOW_PCI=y
# CONFIG_HISAX_DEBUG is not set

#
# HiSax PCMCIA card service modules
#
CONFIG_HISAX_SEDLBAUER_CS=m
CONFIG_HISAX_ELSA_CS=m
CONFIG_HISAX_AVM_A1_CS=m
CONFIG_HISAX_TELES_CS=m

#
# HiSax sub driver modules
#
CONFIG_HISAX_ST5481=m
CONFIG_HISAX_HFCUSB=m
CONFIG_HISAX_HFC4S8S=m
CONFIG_HISAX_FRITZ_PCIPNP=m
CONFIG_HISAX_HDLC=y

#
# Active cards
#
CONFIG_HYSDN=m
CONFIG_HYSDN_CAPI=y
CONFIG_ISDN_DRV_GIGASET=m
CONFIG_GIGASET_BASE=m
CONFIG_GIGASET_M105=m
CONFIG_GIGASET_M101=m
# CONFIG_GIGASET_DEBUG is not set
# CONFIG_GIGASET_UNDOCREQ is not set
CONFIG_ISDN_CAPI=m
CONFIG_ISDN_DRV_AVMB1_VERBOSE_REASON=y
CONFIG_CAPI_TRACE=y
CONFIG_ISDN_CAPI_MIDDLEWARE=y
CONFIG_ISDN_CAPI_CAPI20=m
CONFIG_ISDN_CAPI_CAPIFS_BOOL=y
CONFIG_ISDN_CAPI_CAPIFS=m
CONFIG_ISDN_CAPI_CAPIDRV=m

#
# CAPI hardware drivers
#
CONFIG_CAPI_AVM=y
CONFIG_ISDN_DRV_AVMB1_B1PCI=m
CONFIG_ISDN_DRV_AVMB1_B1PCIV4=y
CONFIG_ISDN_DRV_AVMB1_B1PCMCIA=m
CONFIG_ISDN_DRV_AVMB1_AVM_CS=m
CONFIG_ISDN_DRV_AVMB1_T1PCI=m
CONFIG_ISDN_DRV_AVMB1_C4=m
CONFIG_CAPI_EICON=y
CONFIG_ISDN_DIVAS=m
CONFIG_ISDN_DIVAS_BRIPCI=y
CONFIG_ISDN_DIVAS_PRIPCI=y
CONFIG_ISDN_DIVAS_DIVACAPI=m
CONFIG_ISDN_DIVAS_USERIDI=m
CONFIG_ISDN_DIVAS_MAINT=m
CONFIG_PHONE=m
CONFIG_PHONE_IXJ=m
CONFIG_PHONE_IXJ_PCMCIA=m

#
# Input device support
#
CONFIG_INPUT=y
CONFIG_INPUT_FF_MEMLESS=m
CONFIG_INPUT_POLLDEV=m

#
# Userland interfaces
#
CONFIG_INPUT_MOUSEDEV=y
CONFIG_INPUT_MOUSEDEV_PSAUX=y
CONFIG_INPUT_MOUSEDEV_SCREEN_X=1024
CONFIG_INPUT_MOUSEDEV_SCREEN_Y=768
CONFIG_INPUT_JOYDEV=m
CONFIG_INPUT_EVDEV=m
# CONFIG_INPUT_EVBUG is not set

#
# Input Device Drivers
#
CONFIG_INPUT_KEYBOARD=y
CONFIG_KEYBOARD_ATKBD=y
CONFIG_KEYBOARD_SUNKBD=m
CONFIG_KEYBOARD_LKKBD=m
CONFIG_KEYBOARD_XTKBD=m
CONFIG_KEYBOARD_NEWTON=m
CONFIG_KEYBOARD_STOWAWAY=m
CONFIG_INPUT_MOUSE=y
CONFIG_MOUSE_PS2=m
CONFIG_MOUSE_PS2_ALPS=y
CONFIG_MOUSE_PS2_LOGIPS2PP=y
CONFIG_MOUSE_PS2_SYNAPTICS=y
CONFIG_MOUSE_PS2_LIFEBOOK=y
CONFIG_MOUSE_PS2_TRACKPOINT=y
# CONFIG_MOUSE_PS2_TOUCHKIT is not set
CONFIG_MOUSE_SERIAL=m
CONFIG_MOUSE_APPLETOUCH=m
CONFIG_MOUSE_VSXXXAA=m
CONFIG_INPUT_JOYSTICK=y
CONFIG_JOYSTICK_ANALOG=m
CONFIG_JOYSTICK_A3D=m
CONFIG_JOYSTICK_ADI=m
CONFIG_JOYSTICK_COBRA=m
CONFIG_JOYSTICK_GF2K=m
CONFIG_JOYSTICK_GRIP=m
CONFIG_JOYSTICK_GRIP_MP=m
CONFIG_JOYSTICK_GUILLEMOT=m
CONFIG_JOYSTICK_INTERACT=m
CONFIG_JOYSTICK_SIDEWINDER=m
CONFIG_JOYSTICK_TMDC=m
CONFIG_JOYSTICK_IFORCE=m
CONFIG_JOYSTICK_IFORCE_USB=y
CONFIG_JOYSTICK_IFORCE_232=y
CONFIG_JOYSTICK_WARRIOR=m
CONFIG_JOYSTICK_MAGELLAN=m
CONFIG_JOYSTICK_SPACEORB=m
CONFIG_JOYSTICK_SPACEBALL=m
CONFIG_JOYSTICK_STINGER=m
CONFIG_JOYSTICK_TWIDJOY=m
CONFIG_JOYSTICK_ZHENHUA=m
CONFIG_JOYSTICK_DB9=m
CONFIG_JOYSTICK_GAMECON=m
CONFIG_JOYSTICK_TURBOGRAFX=m
CONFIG_JOYSTICK_JOYDUMP=m
CONFIG_JOYSTICK_XPAD=m
CONFIG_JOYSTICK_XPAD_FF=y
CONFIG_JOYSTICK_XPAD_LEDS=y
CONFIG_INPUT_TABLET=y
CONFIG_TABLET_USB_ACECAD=m
CONFIG_TABLET_USB_AIPTEK=m
CONFIG_TABLET_USB_GTCO=m
CONFIG_TABLET_USB_KBTAB=m
CONFIG_TABLET_USB_WACOM=m
CONFIG_INPUT_TOUCHSCREEN=y
CONFIG_TOUCHSCREEN_ADS7846=m
CONFIG_TOUCHSCREEN_FUJITSU=m
CONFIG_TOUCHSCREEN_GUNZE=m
CONFIG_TOUCHSCREEN_ELO=m
CONFIG_TOUCHSCREEN_MTOUCH=m
CONFIG_TOUCHSCREEN_MK712=m
CONFIG_TOUCHSCREEN_PENMOUNT=m
CONFIG_TOUCHSCREEN_TOUCHRIGHT=m
CONFIG_TOUCHSCREEN_TOUCHWIN=m
CONFIG_TOUCHSCREEN_UCB1400=m
CONFIG_TOUCHSCREEN_WM97XX=m
CONFIG_TOUCHSCREEN_WM9705=y
CONFIG_TOUCHSCREEN_WM9712=y
CONFIG_TOUCHSCREEN_WM9713=y
CONFIG_TOUCHSCREEN_USB_COMPOSITE=m
CONFIG_TOUCHSCREEN_USB_EGALAX=y
CONFIG_TOUCHSCREEN_USB_PANJIT=y
CONFIG_TOUCHSCREEN_USB_3M=y
CONFIG_TOUCHSCREEN_USB_ITM=y
CONFIG_TOUCHSCREEN_USB_ETURBO=y
CONFIG_TOUCHSCREEN_USB_GUNZE=y
CONFIG_TOUCHSCREEN_USB_DMC_TSC10=y
CONFIG_TOUCHSCREEN_USB_IRTOUCH=y
CONFIG_TOUCHSCREEN_USB_IDEALTEK=y
CONFIG_TOUCHSCREEN_USB_GENERAL_TOUCH=y
CONFIG_TOUCHSCREEN_USB_GOTOP=y
CONFIG_INPUT_MISC=y
CONFIG_INPUT_PCSPKR=m
CONFIG_INPUT_APANEL=m
CONFIG_INPUT_ATLAS_BTNS=m
CONFIG_INPUT_ATI_REMOTE=m
CONFIG_INPUT_ATI_REMOTE2=m
CONFIG_INPUT_KEYSPAN_REMOTE=m
CONFIG_INPUT_POWERMATE=m
CONFIG_INPUT_YEALINK=m
CONFIG_INPUT_UINPUT=m

#
# Hardware I/O ports
#
CONFIG_SERIO=y
CONFIG_SERIO_I8042=y
CONFIG_SERIO_SERPORT=m
CONFIG_SERIO_CT82C710=m
CONFIG_SERIO_PARKBD=m
CONFIG_SERIO_PCIPS2=m
CONFIG_SERIO_LIBPS2=y
CONFIG_SERIO_RAW=m
CONFIG_GAMEPORT=m
CONFIG_GAMEPORT_NS558=m
CONFIG_GAMEPORT_L4=m
CONFIG_GAMEPORT_EMU10K1=m
CONFIG_GAMEPORT_FM801=m

#
# Character devices
#
CONFIG_VT=y
CONFIG_VT_CONSOLE=y
CONFIG_HW_CONSOLE=y
# CONFIG_VT_HW_CONSOLE_BINDING is not set
CONFIG_DEVKMEM=y
CONFIG_SERIAL_NONSTANDARD=y
CONFIG_COMPUTONE=m
CONFIG_ROCKETPORT=m
CONFIG_CYCLADES=m
# CONFIG_CYZ_INTR is not set
CONFIG_DIGIEPCA=m
CONFIG_MOXA_INTELLIO=m
CONFIG_MOXA_SMARTIO=m
CONFIG_ISI=m
CONFIG_SYNCLINK=m
CONFIG_SYNCLINKMP=m
CONFIG_SYNCLINK_GT=m
CONFIG_N_HDLC=m
CONFIG_RISCOM8=m
CONFIG_SPECIALIX=m
# CONFIG_SPECIALIX_RTSCTS is not set
CONFIG_SX=m
CONFIG_RIO=m
CONFIG_RIO_OLDPCI=y
CONFIG_STALDRV=y
CONFIG_NOZOMI=m

#
# Serial drivers
#
CONFIG_SERIAL_8250=y
CONFIG_SERIAL_8250_CONSOLE=y
CONFIG_FIX_EARLYCON_MEM=y
CONFIG_SERIAL_8250_PCI=y
CONFIG_SERIAL_8250_PNP=y
CONFIG_SERIAL_8250_CS=m
CONFIG_SERIAL_8250_NR_UARTS=32
CONFIG_SERIAL_8250_RUNTIME_UARTS=4
CONFIG_SERIAL_8250_EXTENDED=y
CONFIG_SERIAL_8250_MANY_PORTS=y
CONFIG_SERIAL_8250_SHARE_IRQ=y
# CONFIG_SERIAL_8250_DETECT_IRQ is not set
CONFIG_SERIAL_8250_RSA=y

#
# Non-8250 serial port support
#
CONFIG_SERIAL_CORE=y
CONFIG_SERIAL_CORE_CONSOLE=y
CONFIG_SERIAL_JSM=m
CONFIG_UNIX98_PTYS=y
# CONFIG_LEGACY_PTYS is not set
CONFIG_PRINTER=m
# CONFIG_LP_CONSOLE is not set
CONFIG_PPDEV=m
CONFIG_IPMI_HANDLER=m
# CONFIG_IPMI_PANIC_EVENT is not set
CONFIG_IPMI_DEVICE_INTERFACE=m
CONFIG_IPMI_SI=m
CONFIG_IPMI_WATCHDOG=m
CONFIG_IPMI_POWEROFF=m
CONFIG_HW_RANDOM=m
CONFIG_HW_RANDOM_INTEL=m
CONFIG_HW_RANDOM_AMD=m
CONFIG_HW_RANDOM_VIRTIO=m
CONFIG_NVRAM=m
CONFIG_R3964=m
CONFIG_APPLICOM=m

#
# PCMCIA character devices
#
CONFIG_SYNCLINK_CS=m
CONFIG_CARDMAN_4000=m
CONFIG_CARDMAN_4040=m
CONFIG_IPWIRELESS=m
CONFIG_MWAVE=m
CONFIG_PC8736x_GPIO=m
CONFIG_NSC_GPIO=m
CONFIG_RAW_DRIVER=m
CONFIG_MAX_RAW_DEVS=256
CONFIG_HPET=y
CONFIG_HPET_MMAP=y
CONFIG_HANGCHECK_TIMER=m
CONFIG_TCG_TPM=m
CONFIG_TCG_TIS=m
CONFIG_TCG_NSC=m
CONFIG_TCG_ATMEL=m
CONFIG_TCG_INFINEON=m
CONFIG_TELCLOCK=m
CONFIG_DEVPORT=y
CONFIG_I2C=m
CONFIG_I2C_BOARDINFO=y
CONFIG_I2C_CHARDEV=m
CONFIG_I2C_HELPER_AUTO=y
CONFIG_I2C_ALGOBIT=m
CONFIG_I2C_ALGOPCA=m

#
# I2C Hardware Bus support
#
CONFIG_I2C_ALI1535=m
CONFIG_I2C_ALI1563=m
CONFIG_I2C_ALI15X3=m
CONFIG_I2C_AMD756=m
CONFIG_I2C_AMD756_S4882=m
CONFIG_I2C_AMD8111=m
CONFIG_I2C_I801=m
CONFIG_I2C_I810=m
CONFIG_I2C_PIIX4=m
CONFIG_I2C_NFORCE2=m
CONFIG_I2C_OCORES=m
CONFIG_I2C_PARPORT=m
CONFIG_I2C_PARPORT_LIGHT=m
CONFIG_I2C_PROSAVAGE=m
CONFIG_I2C_SAVAGE4=m
CONFIG_I2C_SIMTEC=m
CONFIG_I2C_SIS5595=m
CONFIG_I2C_SIS630=m
CONFIG_I2C_SIS96X=m
CONFIG_I2C_TAOS_EVM=m
CONFIG_I2C_STUB=m
CONFIG_I2C_TINY_USB=m
CONFIG_I2C_VIA=m
CONFIG_I2C_VIAPRO=m
CONFIG_I2C_VOODOO3=m
CONFIG_I2C_PCA_PLATFORM=m

#
# Miscellaneous I2C Chip support
#
CONFIG_DS1682=m
CONFIG_SENSORS_EEPROM=m
CONFIG_SENSORS_PCF8574=m
CONFIG_PCF8575=m
CONFIG_SENSORS_PCF8591=m
CONFIG_SENSORS_MAX6875=m
CONFIG_SENSORS_TSL2550=m
# CONFIG_I2C_DEBUG_CORE is not set
# CONFIG_I2C_DEBUG_ALGO is not set
# CONFIG_I2C_DEBUG_BUS is not set
# CONFIG_I2C_DEBUG_CHIP is not set
CONFIG_SPI=y
# CONFIG_SPI_DEBUG is not set
CONFIG_SPI_MASTER=y

#
# SPI Master Controller Drivers
#
CONFIG_SPI_BITBANG=m
CONFIG_SPI_BUTTERFLY=m
CONFIG_SPI_LM70_LLP=m

#
# SPI Protocol Masters
#
CONFIG_SPI_AT25=m
# CONFIG_SPI_SPIDEV is not set
CONFIG_SPI_TLE62X0=m
CONFIG_W1=m
CONFIG_W1_CON=y

#
# 1-wire Bus Masters
#
CONFIG_W1_MASTER_MATROX=m
CONFIG_W1_MASTER_DS2490=m
CONFIG_W1_MASTER_DS2482=m

#
# 1-wire Slaves
#
CONFIG_W1_SLAVE_THERM=m
CONFIG_W1_SLAVE_SMEM=m
CONFIG_W1_SLAVE_DS2433=m
# CONFIG_W1_SLAVE_DS2433_CRC is not set
CONFIG_W1_SLAVE_DS2760=m
CONFIG_POWER_SUPPLY=y

# CONFIG_POWER_SUPPLY_DEBUG is not set
CONFIG_PDA_POWER=m
CONFIG_BATTERY_DS2760=m
CONFIG_HWMON=y
CONFIG_HWMON_VID=m
CONFIG_SENSORS_ABITUGURU=m
CONFIG_SENSORS_ABITUGURU3=m
CONFIG_SENSORS_AD7418=m
CONFIG_SENSORS_ADM1021=m
CONFIG_SENSORS_ADM1025=m
CONFIG_SENSORS_ADM1026=m
CONFIG_SENSORS_ADM1029=m
CONFIG_SENSORS_ADM1031=m
CONFIG_SENSORS_ADM9240=m
CONFIG_SENSORS_ADT7470=m
CONFIG_SENSORS_ADT7473=m
CONFIG_SENSORS_K8TEMP=m
CONFIG_SENSORS_ASB100=m
CONFIG_SENSORS_ATXP1=m
CONFIG_SENSORS_DS1621=m
CONFIG_SENSORS_I5K_AMB=m
CONFIG_SENSORS_F71805F=m
CONFIG_SENSORS_F71882FG=m
CONFIG_SENSORS_F75375S=m
CONFIG_SENSORS_FSCHER=m
CONFIG_SENSORS_FSCPOS=m
CONFIG_SENSORS_FSCHMD=m
CONFIG_SENSORS_GL518SM=m
CONFIG_SENSORS_GL520SM=m
CONFIG_SENSORS_CORETEMP=m
CONFIG_SENSORS_IBMAEM=m
CONFIG_SENSORS_IBMPEX=m
CONFIG_SENSORS_IT87=m
CONFIG_SENSORS_LM63=m
CONFIG_SENSORS_LM70=m
CONFIG_SENSORS_LM75=m
CONFIG_SENSORS_LM77=m
CONFIG_SENSORS_LM78=m
CONFIG_SENSORS_LM80=m
CONFIG_SENSORS_LM83=m
CONFIG_SENSORS_LM85=m
CONFIG_SENSORS_LM87=m
CONFIG_SENSORS_LM90=m
CONFIG_SENSORS_LM92=m
CONFIG_SENSORS_LM93=m
CONFIG_SENSORS_MAX1619=m
CONFIG_SENSORS_MAX6650=m
CONFIG_SENSORS_PC87360=m
CONFIG_SENSORS_PC87427=m
CONFIG_SENSORS_SIS5595=m
CONFIG_SENSORS_DME1737=m
CONFIG_SENSORS_SMSC47M1=m
CONFIG_SENSORS_SMSC47M192=m
CONFIG_SENSORS_SMSC47B397=m
CONFIG_SENSORS_ADS7828=m
CONFIG_SENSORS_THMC50=m
CONFIG_SENSORS_VIA686A=m
CONFIG_SENSORS_VT1211=m
CONFIG_SENSORS_VT8231=m
CONFIG_SENSORS_W83781D=m
CONFIG_SENSORS_W83791D=m
CONFIG_SENSORS_W83792D=m
CONFIG_SENSORS_W83793=m
CONFIG_SENSORS_W83L785TS=m
CONFIG_SENSORS_W83L786NG=m
CONFIG_SENSORS_W83627HF=m
CONFIG_SENSORS_W83627EHF=m
CONFIG_SENSORS_HDAPS=m
CONFIG_SENSORS_APPLESMC=m
# CONFIG_HWMON_DEBUG_CHIP is not set
CONFIG_THERMAL=m
CONFIG_THERMAL_HWMON=y
CONFIG_WATCHDOG=y
# CONFIG_WATCHDOG_NOWAYOUT is not set

#
# Watchdog Device Drivers
#
CONFIG_SOFT_WATCHDOG=m
CONFIG_ACQUIRE_WDT=m
CONFIG_ADVANTECH_WDT=m
CONFIG_ALIM1535_WDT=m
CONFIG_ALIM7101_WDT=m
CONFIG_SC520_WDT=m
CONFIG_EUROTECH_WDT=m
CONFIG_IB700_WDT=m
CONFIG_IBMASR=m
CONFIG_WAFER_WDT=m
CONFIG_I6300ESB_WDT=m
CONFIG_ITCO_WDT=m
# CONFIG_ITCO_VENDOR_SUPPORT is not set
CONFIG_IT8712F_WDT=m
CONFIG_HP_WATCHDOG=m
CONFIG_SC1200_WDT=m
CONFIG_PC87413_WDT=m
CONFIG_60XX_WDT=m
CONFIG_SBC8360_WDT=m
CONFIG_CPU5_WDT=m
CONFIG_SMSC37B787_WDT=m
CONFIG_W83627HF_WDT=m
CONFIG_W83697HF_WDT=m
CONFIG_W83877F_WDT=m
CONFIG_W83977F_WDT=m
CONFIG_MACHZ_WDT=m
CONFIG_SBC_EPX_C3_WATCHDOG=m

#
# PCI-based Watchdog Cards
#
CONFIG_PCIPCWATCHDOG=m
CONFIG_WDTPCI=m
CONFIG_WDT_501_PCI=y

#
# USB-based Watchdog Cards
#
CONFIG_USBPCWATCHDOG=m

#
# Sonics Silicon Backplane
#
CONFIG_SSB_POSSIBLE=y
CONFIG_SSB=m
CONFIG_SSB_SPROM=y
CONFIG_SSB_BLOCKIO=y
CONFIG_SSB_PCIHOST_POSSIBLE=y
CONFIG_SSB_PCIHOST=y
CONFIG_SSB_B43_PCI_BRIDGE=y
CONFIG_SSB_PCMCIAHOST_POSSIBLE=y
CONFIG_SSB_PCMCIAHOST=y
# CONFIG_SSB_DEBUG is not set
CONFIG_SSB_DRIVER_PCICORE_POSSIBLE=y
CONFIG_SSB_DRIVER_PCICORE=y

#
# Multifunction device drivers
#
CONFIG_MFD_SM501=m
CONFIG_HTC_PASIC3=m

#
# Multimedia devices
#

#
# Multimedia core support
#
CONFIG_VIDEO_DEV=m
CONFIG_VIDEO_V4L2_COMMON=m
CONFIG_VIDEO_ALLOW_V4L1=y
CONFIG_VIDEO_V4L1_COMPAT=y
CONFIG_DVB_CORE=m
CONFIG_VIDEO_MEDIA=m

#
# Multimedia drivers
#
CONFIG_VIDEO_SAA7146=m
CONFIG_VIDEO_SAA7146_VV=m
CONFIG_MEDIA_ATTACH=y
CONFIG_MEDIA_TUNER=m
# CONFIG_MEDIA_TUNER_CUSTOMIZE is not set
CONFIG_MEDIA_TUNER_SIMPLE=m
CONFIG_MEDIA_TUNER_TDA8290=m
CONFIG_MEDIA_TUNER_TDA827X=m
CONFIG_MEDIA_TUNER_TDA18271=m
CONFIG_MEDIA_TUNER_TDA9887=m
CONFIG_MEDIA_TUNER_TEA5761=m
CONFIG_MEDIA_TUNER_TEA5767=m
CONFIG_MEDIA_TUNER_MT20XX=m
CONFIG_MEDIA_TUNER_MT2060=m
CONFIG_MEDIA_TUNER_MT2266=m
CONFIG_MEDIA_TUNER_MT2131=m
CONFIG_MEDIA_TUNER_QT1010=m
CONFIG_MEDIA_TUNER_XC2028=m
CONFIG_MEDIA_TUNER_XC5000=m
CONFIG_MEDIA_TUNER_MXL5005S=m
CONFIG_VIDEO_V4L2=m
CONFIG_VIDEO_V4L1=m
CONFIG_VIDEOBUF_GEN=m
CONFIG_VIDEOBUF_DMA_SG=m
CONFIG_VIDEOBUF_VMALLOC=m
CONFIG_VIDEOBUF_DVB=m
CONFIG_VIDEO_BTCX=m
CONFIG_VIDEO_IR_I2C=m
CONFIG_VIDEO_IR=m
CONFIG_VIDEO_TVEEPROM=m
CONFIG_VIDEO_TUNER=m
CONFIG_VIDEO_CAPTURE_DRIVERS=y
# CONFIG_VIDEO_ADV_DEBUG is not set
CONFIG_VIDEO_HELPER_CHIPS_AUTO=y
CONFIG_VIDEO_TVAUDIO=m
CONFIG_VIDEO_TDA7432=m
CONFIG_VIDEO_TDA9840=m
CONFIG_VIDEO_TDA9875=m
CONFIG_VIDEO_TEA6415C=m
CONFIG_VIDEO_TEA6420=m
CONFIG_VIDEO_MSP3400=m
CONFIG_VIDEO_CS5345=m
CONFIG_VIDEO_CS53L32A=m
CONFIG_VIDEO_M52790=m
CONFIG_VIDEO_WM8775=m
CONFIG_VIDEO_WM8739=m
CONFIG_VIDEO_VP27SMPX=m
CONFIG_VIDEO_BT819=m
CONFIG_VIDEO_BT856=m
CONFIG_VIDEO_KS0127=m
CONFIG_VIDEO_OV7670=m
CONFIG_VIDEO_SAA7110=m
CONFIG_VIDEO_SAA7111=m
CONFIG_VIDEO_SAA7114=m
CONFIG_VIDEO_SAA711X=m
CONFIG_VIDEO_SAA717X=m
CONFIG_VIDEO_TVP5150=m
CONFIG_VIDEO_VPX3220=m
CONFIG_VIDEO_CX25840=m
CONFIG_VIDEO_CX2341X=m
CONFIG_VIDEO_SAA7127=m
CONFIG_VIDEO_SAA7185=m
CONFIG_VIDEO_ADV7170=m
CONFIG_VIDEO_ADV7175=m
CONFIG_VIDEO_UPD64031A=m
CONFIG_VIDEO_UPD64083=m
CONFIG_VIDEO_VIVI=m
CONFIG_VIDEO_BT848=m
CONFIG_VIDEO_BT848_DVB=y
CONFIG_VIDEO_SAA6588=m
CONFIG_VIDEO_BWQCAM=m
CONFIG_VIDEO_CQCAM=m
CONFIG_VIDEO_W9966=m
CONFIG_VIDEO_CPIA=m
CONFIG_VIDEO_CPIA_PP=m
CONFIG_VIDEO_CPIA_USB=m
CONFIG_VIDEO_CPIA2=m
CONFIG_VIDEO_SAA5246A=m
CONFIG_VIDEO_SAA5249=m
CONFIG_TUNER_3036=m
CONFIG_VIDEO_STRADIS=m
CONFIG_VIDEO_ZORAN_ZR36060=m
CONFIG_VIDEO_ZORAN=m
CONFIG_VIDEO_ZORAN_BUZ=m
CONFIG_VIDEO_ZORAN_DC10=m
CONFIG_VIDEO_ZORAN_DC30=m
CONFIG_VIDEO_ZORAN_LML33=m
CONFIG_VIDEO_ZORAN_LML33R10=m
CONFIG_VIDEO_ZORAN_AVS6EYES=m
CONFIG_VIDEO_MEYE=m
CONFIG_VIDEO_SAA7134=m
CONFIG_VIDEO_SAA7134_ALSA=m
CONFIG_VIDEO_SAA7134_DVB=m
CONFIG_VIDEO_MXB=m
CONFIG_VIDEO_DPC=m
CONFIG_VIDEO_HEXIUM_ORION=m
CONFIG_VIDEO_HEXIUM_GEMINI=m
CONFIG_VIDEO_CX88=m
CONFIG_VIDEO_CX88_ALSA=m
CONFIG_VIDEO_CX88_BLACKBIRD=m
CONFIG_VIDEO_CX88_DVB=m
CONFIG_VIDEO_CX88_VP3054=m
CONFIG_VIDEO_CX23885=m
CONFIG_VIDEO_AU0828=m
CONFIG_VIDEO_IVTV=m
CONFIG_VIDEO_FB_IVTV=m
CONFIG_VIDEO_CX18=m
CONFIG_VIDEO_CAFE_CCIC=m
CONFIG_V4L_USB_DRIVERS=y
CONFIG_USB_VIDEO_CLASS=m
CONFIG_USB_VIDEO_CLASS_INPUT_EVDEV=y
CONFIG_VIDEO_PVRUSB2=m
CONFIG_VIDEO_PVRUSB2_SYSFS=y
CONFIG_VIDEO_PVRUSB2_DVB=y
# CONFIG_VIDEO_PVRUSB2_DEBUGIFC is not set
CONFIG_VIDEO_EM28XX=m
CONFIG_VIDEO_EM28XX_ALSA=m
CONFIG_VIDEO_EM28XX_DVB=m
CONFIG_VIDEO_USBVISION=m
CONFIG_VIDEO_USBVIDEO=m
CONFIG_USB_VICAM=m
CONFIG_USB_IBMCAM=m
CONFIG_USB_KONICAWC=m
CONFIG_USB_QUICKCAM_MESSENGER=m
CONFIG_USB_ET61X251=m
CONFIG_VIDEO_OVCAMCHIP=m
CONFIG_USB_W9968CF=m
CONFIG_USB_OV511=m
CONFIG_USB_SE401=m
CONFIG_USB_SN9C102=m
CONFIG_USB_STV680=m
CONFIG_USB_ZC0301=m
CONFIG_USB_PWC=m
# CONFIG_USB_PWC_DEBUG is not set
CONFIG_USB_ZR364XX=m
CONFIG_USB_STKWEBCAM=m
CONFIG_SOC_CAMERA=m
CONFIG_SOC_CAMERA_MT9M001=m
CONFIG_SOC_CAMERA_MT9V022=m
CONFIG_RADIO_ADAPTERS=y
CONFIG_RADIO_GEMTEK_PCI=m
CONFIG_RADIO_MAXIRADIO=m
CONFIG_RADIO_MAESTRO=m
CONFIG_USB_DSBR=m
CONFIG_USB_SI470X=m
CONFIG_DVB_CAPTURE_DRIVERS=y

#
# Supported SAA7146 based PCI Adapters
#
CONFIG_TTPCI_EEPROM=m
CONFIG_DVB_AV7110=m
CONFIG_DVB_AV7110_OSD=y
CONFIG_DVB_BUDGET_CORE=m
CONFIG_DVB_BUDGET=m
CONFIG_DVB_BUDGET_CI=m
CONFIG_DVB_BUDGET_AV=m
CONFIG_DVB_BUDGET_PATCH=m

#
# Supported USB Adapters
#
CONFIG_DVB_USB=m
# CONFIG_DVB_USB_DEBUG is not set
CONFIG_DVB_USB_A800=m
CONFIG_DVB_USB_DIBUSB_MB=m
CONFIG_DVB_USB_DIBUSB_MB_FAULTY=y
CONFIG_DVB_USB_DIBUSB_MC=m
CONFIG_DVB_USB_DIB0700=m
CONFIG_DVB_USB_UMT_010=m
CONFIG_DVB_USB_CXUSB=m
CONFIG_DVB_USB_M920X=m
CONFIG_DVB_USB_GL861=m
CONFIG_DVB_USB_AU6610=m
CONFIG_DVB_USB_DIGITV=m
CONFIG_DVB_USB_VP7045=m
CONFIG_DVB_USB_VP702X=m
CONFIG_DVB_USB_GP8PSK=m
CONFIG_DVB_USB_NOVA_T_USB2=m
CONFIG_DVB_USB_TTUSB2=m
CONFIG_DVB_USB_DTT200U=m
CONFIG_DVB_USB_OPERA1=m
CONFIG_DVB_USB_AF9005=m
CONFIG_DVB_USB_AF9005_REMOTE=m
CONFIG_DVB_TTUSB_DEC=m
CONFIG_DVB_CINERGYT2=m
# CONFIG_DVB_CINERGYT2_TUNING is not set

#
# Supported FlexCopII (B2C2) Adapters
#
CONFIG_DVB_B2C2_FLEXCOP=m
CONFIG_DVB_B2C2_FLEXCOP_PCI=m
CONFIG_DVB_B2C2_FLEXCOP_USB=m
# CONFIG_DVB_B2C2_FLEXCOP_DEBUG is not set

#
# Supported BT878 Adapters
#
CONFIG_DVB_BT8XX=m

#
# Supported Pluto2 Adapters
#
CONFIG_DVB_PLUTO2=m

#
# Supported DVB Frontends
#

#
# Customise DVB Frontends
#
# CONFIG_DVB_FE_CUSTOMISE is not set

#
# DVB-S (satellite) frontends
#
CONFIG_DVB_CX24110=m
CONFIG_DVB_CX24123=m
CONFIG_DVB_MT312=m
CONFIG_DVB_S5H1420=m
CONFIG_DVB_STV0299=m
CONFIG_DVB_TDA8083=m
CONFIG_DVB_TDA10086=m
CONFIG_DVB_VES1X93=m
CONFIG_DVB_TUNER_ITD1000=m
CONFIG_DVB_TDA826X=m
CONFIG_DVB_TUA6100=m

#
# DVB-T (terrestrial) frontends
#
CONFIG_DVB_SP8870=m
CONFIG_DVB_SP887X=m
CONFIG_DVB_CX22700=m
CONFIG_DVB_CX22702=m
CONFIG_DVB_L64781=m
CONFIG_DVB_TDA1004X=m
CONFIG_DVB_NXT6000=m
CONFIG_DVB_MT352=m
CONFIG_DVB_ZL10353=m
CONFIG_DVB_DIB3000MB=m
CONFIG_DVB_DIB3000MC=m
CONFIG_DVB_DIB7000M=m
CONFIG_DVB_DIB7000P=m
CONFIG_DVB_TDA10048=m

#
# DVB-C (cable) frontends
#
CONFIG_DVB_VES1820=m
CONFIG_DVB_TDA10021=m
CONFIG_DVB_TDA10023=m
CONFIG_DVB_STV0297=m

#
# ATSC (North American/Korean Terrestrial/Cable DTV) frontends
#
CONFIG_DVB_NXT200X=m
CONFIG_DVB_OR51211=m
CONFIG_DVB_OR51132=m
CONFIG_DVB_BCM3510=m
CONFIG_DVB_LGDT330X=m
CONFIG_DVB_S5H1409=m
CONFIG_DVB_AU8522=m
CONFIG_DVB_S5H1411=m

#
# Digital terrestrial only tuners/PLL
#
CONFIG_DVB_PLL=m
CONFIG_DVB_TUNER_DIB0070=m

#
# SEC control devices for DVB-S
#
CONFIG_DVB_LNBP21=m
CONFIG_DVB_ISL6405=m
CONFIG_DVB_ISL6421=m
CONFIG_DAB=y
CONFIG_USB_DABUSB=m

#
# Graphics support
#
CONFIG_AGP=y
CONFIG_AGP_AMD64=y
CONFIG_AGP_INTEL=m
CONFIG_AGP_SIS=m
CONFIG_AGP_VIA=m
CONFIG_DRM=m
CONFIG_DRM_TDFX=m
CONFIG_DRM_R128=m
CONFIG_DRM_RADEON=m
CONFIG_DRM_I810=m
CONFIG_DRM_I830=m
CONFIG_DRM_I915=m
CONFIG_DRM_MGA=m
CONFIG_DRM_SIS=m
CONFIG_DRM_VIA=m
CONFIG_DRM_SAVAGE=m
CONFIG_VGASTATE=m
CONFIG_VIDEO_OUTPUT_CONTROL=m
CONFIG_FB=y
CONFIG_FIRMWARE_EDID=y
CONFIG_FB_DDC=m
CONFIG_FB_CFB_FILLRECT=y
CONFIG_FB_CFB_COPYAREA=y
CONFIG_FB_CFB_IMAGEBLIT=y
# CONFIG_FB_CFB_REV_PIXELS_IN_BYTE is not set
CONFIG_FB_SYS_FILLRECT=m
CONFIG_FB_SYS_COPYAREA=m
CONFIG_FB_SYS_IMAGEBLIT=m
# CONFIG_FB_FOREIGN_ENDIAN is not set
CONFIG_FB_SYS_FOPS=m
CONFIG_FB_DEFERRED_IO=y
CONFIG_FB_HECUBA=m
CONFIG_FB_SVGALIB=m
# CONFIG_FB_MACMODES is not set
CONFIG_FB_BACKLIGHT=y
CONFIG_FB_MODE_HELPERS=y
CONFIG_FB_TILEBLITTING=y

#
# Frame buffer hardware drivers
#
CONFIG_FB_CIRRUS=m
CONFIG_FB_PM2=m
CONFIG_FB_PM2_FIFO_DISCONNECT=y
CONFIG_FB_CYBER2000=m
CONFIG_FB_ARC=m
# CONFIG_FB_ASILIANT is not set
# CONFIG_FB_IMSTT is not set
CONFIG_FB_VGA16=m
CONFIG_FB_UVESA=m
CONFIG_FB_VESA=y
CONFIG_FB_EFI=y
# CONFIG_FB_IMAC is not set
CONFIG_FB_N411=m
CONFIG_FB_HGA=m
# CONFIG_FB_HGA_ACCEL is not set
CONFIG_FB_S1D13XXX=m
CONFIG_FB_NVIDIA=m
# CONFIG_FB_NVIDIA_I2C is not set
# CONFIG_FB_NVIDIA_DEBUG is not set
CONFIG_FB_NVIDIA_BACKLIGHT=y
# CONFIG_FB_RIVA is not set
CONFIG_FB_LE80578=m
CONFIG_FB_CARILLO_RANCH=m
CONFIG_FB_INTEL=m
# CONFIG_FB_INTEL_DEBUG is not set
CONFIG_FB_INTEL_I2C=y
CONFIG_FB_MATROX=m
CONFIG_FB_MATROX_MILLENIUM=y
CONFIG_FB_MATROX_MYSTIQUE=y
CONFIG_FB_MATROX_G=y
CONFIG_FB_MATROX_I2C=m
CONFIG_FB_MATROX_MAVEN=m
CONFIG_FB_MATROX_MULTIHEAD=y
CONFIG_FB_RADEON=m
CONFIG_FB_RADEON_I2C=y
CONFIG_FB_RADEON_BACKLIGHT=y
# CONFIG_FB_RADEON_DEBUG is not set
CONFIG_FB_ATY128=m
CONFIG_FB_ATY128_BACKLIGHT=y
CONFIG_FB_ATY=m
CONFIG_FB_ATY_CT=y
# CONFIG_FB_ATY_GENERIC_LCD is not set
CONFIG_FB_ATY_GX=y
CONFIG_FB_ATY_BACKLIGHT=y
CONFIG_FB_S3=m
CONFIG_FB_SAVAGE=m
# CONFIG_FB_SAVAGE_I2C is not set
# CONFIG_FB_SAVAGE_ACCEL is not set
CONFIG_FB_SIS=m
CONFIG_FB_SIS_300=y
CONFIG_FB_SIS_315=y
CONFIG_FB_NEOMAGIC=m
CONFIG_FB_KYRO=m
CONFIG_FB_3DFX=m
# CONFIG_FB_3DFX_ACCEL is not set
CONFIG_FB_VOODOO1=m
CONFIG_FB_VT8623=m
CONFIG_FB_TRIDENT=m
# CONFIG_FB_TRIDENT_ACCEL is not set
CONFIG_FB_ARK=m
CONFIG_FB_PM3=m
# CONFIG_FB_GEODE is not set
CONFIG_FB_SM501=m
CONFIG_FB_VIRTUAL=m
CONFIG_BACKLIGHT_LCD_SUPPORT=y
# CONFIG_LCD_CLASS_DEVICE is not set
CONFIG_BACKLIGHT_CLASS_DEVICE=y
# CONFIG_BACKLIGHT_CORGI is not set
CONFIG_BACKLIGHT_PROGEAR=m

#
# Display device support
#
CONFIG_DISPLAY_SUPPORT=m

#
# Display hardware drivers
#

#
# Console display driver support
#
CONFIG_VGA_CONSOLE=y
# CONFIG_VGACON_SOFT_SCROLLBACK is not set
CONFIG_VIDEO_SELECT=y
CONFIG_DUMMY_CONSOLE=y
CONFIG_FRAMEBUFFER_CONSOLE=y
# CONFIG_FRAMEBUFFER_CONSOLE_DETECT_PRIMARY is not set
CONFIG_FRAMEBUFFER_CONSOLE_ROTATION=y
# CONFIG_FONTS is not set
CONFIG_FONT_8x8=y
CONFIG_FONT_8x16=y
# CONFIG_LOGO is not set

#
# Sound
#
CONFIG_SOUND=m

#
# Advanced Linux Sound Architecture
#
CONFIG_SND=m
CONFIG_SND_TIMER=m
CONFIG_SND_PCM=m
CONFIG_SND_HWDEP=m
CONFIG_SND_RAWMIDI=m
CONFIG_SND_SEQUENCER=m
CONFIG_SND_SEQ_DUMMY=m
CONFIG_SND_OSSEMUL=y
CONFIG_SND_MIXER_OSS=m
CONFIG_SND_PCM_OSS=m
CONFIG_SND_PCM_OSS_PLUGINS=y
CONFIG_SND_SEQUENCER_OSS=y
# CONFIG_SND_DYNAMIC_MINORS is not set
CONFIG_SND_SUPPORT_OLD_API=y
CONFIG_SND_VERBOSE_PROCFS=y
# CONFIG_SND_VERBOSE_PRINTK is not set
# CONFIG_SND_DEBUG is not set
CONFIG_SND_VMASTER=y

#
# Generic devices
#
CONFIG_SND_PCSP=m
CONFIG_SND_MPU401_UART=m
CONFIG_SND_OPL3_LIB=m
CONFIG_SND_VX_LIB=m
CONFIG_SND_AC97_CODEC=m
CONFIG_SND_DUMMY=m
CONFIG_SND_VIRMIDI=m
CONFIG_SND_MTPAV=m
CONFIG_SND_MTS64=m
CONFIG_SND_SERIAL_U16550=m
CONFIG_SND_MPU401=m
CONFIG_SND_PORTMAN2X4=m
CONFIG_SND_SB_COMMON=m
CONFIG_SND_SB16_DSP=m

#
# PCI devices
#
CONFIG_SND_AD1889=m
CONFIG_SND_ALS300=m
CONFIG_SND_ALS4000=m
CONFIG_SND_ALI5451=m
CONFIG_SND_ATIIXP=m
CONFIG_SND_ATIIXP_MODEM=m
CONFIG_SND_AU8810=m
CONFIG_SND_AU8820=m
CONFIG_SND_AU8830=m
# CONFIG_SND_AW2 is not set
CONFIG_SND_AZT3328=m
CONFIG_SND_BT87X=m
# CONFIG_SND_BT87X_OVERCLOCK is not set
CONFIG_SND_CA0106=m
CONFIG_SND_CMIPCI=m
CONFIG_SND_OXYGEN_LIB=m
CONFIG_SND_OXYGEN=m
CONFIG_SND_CS4281=m
CONFIG_SND_CS5530=m
CONFIG_SND_DARLA20=m
CONFIG_SND_GINA20=m
CONFIG_SND_LAYLA20=m
CONFIG_SND_DARLA24=m
CONFIG_SND_GINA24=m
CONFIG_SND_LAYLA24=m
CONFIG_SND_MONA=m
CONFIG_SND_MIA=m
CONFIG_SND_ECHO3G=m
CONFIG_SND_INDIGO=m
CONFIG_SND_INDIGOIO=m
CONFIG_SND_INDIGODJ=m
CONFIG_SND_EMU10K1=m
CONFIG_SND_EMU10K1X=m
CONFIG_SND_ENS1370=m
CONFIG_SND_ENS1371=m
CONFIG_SND_ES1938=m
CONFIG_SND_ES1968=m
CONFIG_SND_FM801=m
CONFIG_SND_FM801_TEA575X_BOOL=y
CONFIG_SND_FM801_TEA575X=m
CONFIG_SND_HDA_INTEL=m
# CONFIG_SND_HDA_HWDEP is not set
CONFIG_SND_HDA_CODEC_REALTEK=y
CONFIG_SND_HDA_CODEC_ANALOG=y
CONFIG_SND_HDA_CODEC_SIGMATEL=y
CONFIG_SND_HDA_CODEC_VIA=y
CONFIG_SND_HDA_CODEC_ATIHDMI=y
CONFIG_SND_HDA_CODEC_CONEXANT=y
CONFIG_SND_HDA_CODEC_CMEDIA=y
CONFIG_SND_HDA_CODEC_SI3054=y
CONFIG_SND_HDA_GENERIC=y
CONFIG_SND_HDA_POWER_SAVE=y
CONFIG_SND_HDA_POWER_SAVE_DEFAULT=0
CONFIG_SND_HDSP=m
CONFIG_SND_HDSPM=m
CONFIG_SND_HIFIER=m
CONFIG_SND_ICE1712=m
CONFIG_SND_ICE1724=m
CONFIG_SND_INTEL8X0=m
CONFIG_SND_INTEL8X0M=m
CONFIG_SND_KORG1212=m
CONFIG_SND_MAESTRO3=m
CONFIG_SND_MIXART=m
CONFIG_SND_NM256=m
CONFIG_SND_PCXHR=m
CONFIG_SND_RIPTIDE=m
CONFIG_SND_RME32=m
CONFIG_SND_RME96=m
CONFIG_SND_RME9652=m
CONFIG_SND_SONICVIBES=m
CONFIG_SND_TRIDENT=m
CONFIG_SND_VIA82XX=m
CONFIG_SND_VIA82XX_MODEM=m
CONFIG_SND_VIRTUOSO=m
CONFIG_SND_VX222=m
CONFIG_SND_YMFPCI=m
CONFIG_SND_AC97_POWER_SAVE=y
CONFIG_SND_AC97_POWER_SAVE_DEFAULT=0

#
# SPI devices
#

#
# USB devices
#
CONFIG_SND_USB_AUDIO=m
CONFIG_SND_USB_USX2Y=m
CONFIG_SND_USB_CAIAQ=m
CONFIG_SND_USB_CAIAQ_INPUT=y

#
# PCMCIA devices
#
CONFIG_SND_VXPOCKET=m
CONFIG_SND_PDAUDIOCF=m

#
# System on Chip audio support
#
# CONFIG_SND_SOC is not set

#
# ALSA SoC audio for Freescale SOCs
#

#
# SoC Audio for the Texas Instruments OMAP
#

#
# Open Sound System
#
CONFIG_SOUND_PRIME=m
CONFIG_SOUND_TRIDENT=m
CONFIG_SOUND_OSS=m
# CONFIG_SOUND_TRACEINIT is not set
# CONFIG_SOUND_DMAP is not set
CONFIG_SOUND_SSCAPE=m
CONFIG_SOUND_VMIDI=m
CONFIG_SOUND_TRIX=m
CONFIG_SOUND_MSS=m
CONFIG_SOUND_MPU401=m
CONFIG_SOUND_PAS=m
CONFIG_SOUND_PSS=m
CONFIG_PSS_MIXER=y
CONFIG_SOUND_SB=m
CONFIG_SOUND_YM3812=m
CONFIG_SOUND_UART6850=m
CONFIG_SOUND_AEDSP16=m
CONFIG_SC6600=y
CONFIG_SC6600_JOY=y
CONFIG_SC6600_CDROM=4
CONFIG_SC6600_CDROMBASE=0x0
# CONFIG_AEDSP16_MSS is not set
# CONFIG_AEDSP16_SBPRO is not set
CONFIG_SOUND_KAHLUA=m
CONFIG_AC97_BUS=m
CONFIG_HID_SUPPORT=y
CONFIG_HID=m
# CONFIG_HID_DEBUG is not set
CONFIG_HIDRAW=y

#
# USB Input Devices
#
CONFIG_USB_HID=m
CONFIG_USB_HIDINPUT_POWERBOOK=y
CONFIG_HID_FF=y
CONFIG_HID_PID=y
CONFIG_LOGITECH_FF=y
CONFIG_LOGIRUMBLEPAD2_FF=y
CONFIG_PANTHERLORD_FF=y
CONFIG_THRUSTMASTER_FF=y
CONFIG_ZEROPLUS_FF=y
CONFIG_USB_HIDDEV=y

#
# USB HID Boot Protocol drivers
#
CONFIG_USB_KBD=m
CONFIG_USB_MOUSE=m
CONFIG_USB_SUPPORT=y
CONFIG_USB_ARCH_HAS_HCD=y
CONFIG_USB_ARCH_HAS_OHCI=y
CONFIG_USB_ARCH_HAS_EHCI=y
CONFIG_USB=y
# CONFIG_USB_DEBUG is not set
CONFIG_USB_ANNOUNCE_NEW_DEVICES=y

#
# Miscellaneous USB options
#
CONFIG_USB_DEVICEFS=y
CONFIG_USB_DEVICE_CLASS=y
# CONFIG_USB_DYNAMIC_MINORS is not set
CONFIG_USB_SUSPEND=y
# CONFIG_USB_OTG is not set

#
# USB Host Controller Drivers
#
CONFIG_USB_C67X00_HCD=m
CONFIG_USB_EHCI_HCD=m
CONFIG_USB_EHCI_ROOT_HUB_TT=y
CONFIG_USB_EHCI_TT_NEWSCHED=y
CONFIG_USB_ISP116X_HCD=m
# CONFIG_USB_ISP1760_HCD is not set
CONFIG_USB_OHCI_HCD=m
# CONFIG_USB_OHCI_HCD_SSB is not set
# CONFIG_USB_OHCI_BIG_ENDIAN_DESC is not set
# CONFIG_USB_OHCI_BIG_ENDIAN_MMIO is not set
CONFIG_USB_OHCI_LITTLE_ENDIAN=y
CONFIG_USB_UHCI_HCD=m
CONFIG_USB_U132_HCD=m
CONFIG_USB_SL811_HCD=m
CONFIG_USB_SL811_CS=m
CONFIG_USB_R8A66597_HCD=m

#
# USB Device Class drivers
#
CONFIG_USB_ACM=m
CONFIG_USB_PRINTER=m
CONFIG_USB_WDM=m

#
# NOTE: USB_STORAGE enables SCSI, and 'SCSI disk support'
#

#
# may also be needed; see USB_STORAGE Help for more information
#
CONFIG_USB_STORAGE=m
# CONFIG_USB_STORAGE_DEBUG is not set
CONFIG_USB_STORAGE_DATAFAB=y
CONFIG_USB_STORAGE_FREECOM=y
CONFIG_USB_STORAGE_ISD200=y
CONFIG_USB_STORAGE_DPCM=y
CONFIG_USB_STORAGE_USBAT=y
CONFIG_USB_STORAGE_SDDR09=y
CONFIG_USB_STORAGE_SDDR55=y
CONFIG_USB_STORAGE_JUMPSHOT=y
CONFIG_USB_STORAGE_ALAUDA=y
CONFIG_USB_STORAGE_ONETOUCH=y
CONFIG_USB_STORAGE_KARMA=y
CONFIG_USB_STORAGE_CYPRESS_ATACB=y
# CONFIG_USB_LIBUSUAL is not set

#
# USB Imaging devices
#
CONFIG_USB_MDC800=m
CONFIG_USB_MICROTEK=m
CONFIG_USB_MON=y

#
# USB port drivers
#
CONFIG_USB_USS720=m
CONFIG_USB_SERIAL=m
CONFIG_USB_EZUSB=y
CONFIG_USB_SERIAL_GENERIC=y
CONFIG_USB_SERIAL_AIRCABLE=m
CONFIG_USB_SERIAL_AIRPRIME=m
CONFIG_USB_SERIAL_ARK3116=m
CONFIG_USB_SERIAL_BELKIN=m
CONFIG_USB_SERIAL_CH341=m
# CONFIG_USB_SERIAL_WHITEHEAT is not set
CONFIG_USB_SERIAL_DIGI_ACCELEPORT=m
CONFIG_USB_SERIAL_CP2101=m
CONFIG_USB_SERIAL_CYPRESS_M8=m
CONFIG_USB_SERIAL_EMPEG=m
CONFIG_USB_SERIAL_FTDI_SIO=m
CONFIG_USB_SERIAL_FUNSOFT=m
CONFIG_USB_SERIAL_VISOR=m
CONFIG_USB_SERIAL_IPAQ=m
CONFIG_USB_SERIAL_IR=m
CONFIG_USB_SERIAL_EDGEPORT=m
CONFIG_USB_SERIAL_EDGEPORT_TI=m
CONFIG_USB_SERIAL_GARMIN=m
CONFIG_USB_SERIAL_IPW=m
CONFIG_USB_SERIAL_IUU=m
CONFIG_USB_SERIAL_KEYSPAN_PDA=m
CONFIG_USB_SERIAL_KEYSPAN=m
CONFIG_USB_SERIAL_KLSI=m
CONFIG_USB_SERIAL_KOBIL_SCT=m
CONFIG_USB_SERIAL_MCT_U232=m
CONFIG_USB_SERIAL_MOS7720=m
CONFIG_USB_SERIAL_MOS7840=m
CONFIG_USB_SERIAL_MOTOROLA=m
CONFIG_USB_SERIAL_NAVMAN=m
CONFIG_USB_SERIAL_PL2303=m
CONFIG_USB_SERIAL_OTI6858=m
CONFIG_USB_SERIAL_SPCP8X5=m
CONFIG_USB_SERIAL_HP4X=m
CONFIG_USB_SERIAL_SAFE=m
# CONFIG_USB_SERIAL_SAFE_PADDED is not set
CONFIG_USB_SERIAL_SIERRAWIRELESS=m
# CONFIG_USB_SERIAL_TI is not set
CONFIG_USB_SERIAL_CYBERJACK=m
CONFIG_USB_SERIAL_XIRCOM=m
CONFIG_USB_SERIAL_OPTION=m
CONFIG_USB_SERIAL_OMNINET=m
CONFIG_USB_SERIAL_DEBUG=m

#
# USB Miscellaneous drivers
#
CONFIG_USB_ADUTUX=m
CONFIG_USB_AUERSWALD=m
CONFIG_USB_RIO500=m
CONFIG_USB_LEGOTOWER=m
CONFIG_USB_LCD=m
CONFIG_USB_BERRY_CHARGE=m
CONFIG_USB_LED=m
CONFIG_USB_CYPRESS_CY7C63=m
CONFIG_USB_CYTHERM=m
CONFIG_USB_PHIDGET=m
CONFIG_USB_PHIDGETKIT=m
CONFIG_USB_PHIDGETMOTORCONTROL=m
CONFIG_USB_PHIDGETSERVO=m
CONFIG_USB_IDMOUSE=m
CONFIG_USB_FTDI_ELAN=m
CONFIG_USB_APPLEDISPLAY=m
CONFIG_USB_SISUSBVGA=m
CONFIG_USB_SISUSBVGA_CON=y
CONFIG_USB_LD=m
CONFIG_USB_TRANCEVIBRATOR=m
CONFIG_USB_IOWARRIOR=m
CONFIG_USB_TEST=m
CONFIG_USB_ISIGHTFW=m
CONFIG_USB_ATM=m
CONFIG_USB_SPEEDTOUCH=m
CONFIG_USB_CXACRU=m
CONFIG_USB_UEAGLEATM=m
CONFIG_USB_XUSBATM=m
# CONFIG_USB_GADGET is not set
CONFIG_MMC=m
# CONFIG_MMC_DEBUG is not set
# CONFIG_MMC_UNSAFE_RESUME is not set

#
# MMC/SD Card Drivers
#
CONFIG_MMC_BLOCK=m
CONFIG_MMC_BLOCK_BOUNCE=y
CONFIG_SDIO_UART=m
# CONFIG_MMC_TEST is not set

#
# MMC/SD Host Controller Drivers
#
CONFIG_MMC_SDHCI=m
CONFIG_MMC_RICOH_MMC=m
CONFIG_MMC_WBSD=m
CONFIG_MMC_TIFM_SD=m
CONFIG_MMC_SPI=m
CONFIG_MEMSTICK=m
# CONFIG_MEMSTICK_DEBUG is not set

#
# MemoryStick drivers
#
# CONFIG_MEMSTICK_UNSAFE_RESUME is not set
CONFIG_MSPRO_BLOCK=m

#
# MemoryStick Host Controller Drivers
#
CONFIG_MEMSTICK_TIFM_MS=m
CONFIG_MEMSTICK_JMICRON_38X=m
CONFIG_NEW_LEDS=y
CONFIG_LEDS_CLASS=m

#
# LED drivers
#
CONFIG_LEDS_CLEVO_MAIL=m

#
# LED Triggers
#
CONFIG_LEDS_TRIGGERS=y
CONFIG_LEDS_TRIGGER_TIMER=m
CONFIG_LEDS_TRIGGER_IDE_DISK=y
CONFIG_LEDS_TRIGGER_HEARTBEAT=m
CONFIG_LEDS_TRIGGER_DEFAULT_ON=m
CONFIG_ACCESSIBILITY=y
CONFIG_A11Y_BRAILLE_CONSOLE=y
CONFIG_INFINIBAND=m
CONFIG_INFINIBAND_USER_MAD=m
CONFIG_INFINIBAND_USER_ACCESS=m
CONFIG_INFINIBAND_USER_MEM=y
CONFIG_INFINIBAND_ADDR_TRANS=y
CONFIG_INFINIBAND_MTHCA=m
CONFIG_INFINIBAND_MTHCA_DEBUG=y
CONFIG_INFINIBAND_IPATH=m
CONFIG_INFINIBAND_AMSO1100=m
# CONFIG_INFINIBAND_AMSO1100_DEBUG is not set
CONFIG_INFINIBAND_CXGB3=m
# CONFIG_INFINIBAND_CXGB3_DEBUG is not set
CONFIG_MLX4_INFINIBAND=m
CONFIG_INFINIBAND_NES=m
# CONFIG_INFINIBAND_NES_DEBUG is not set
CONFIG_INFINIBAND_IPOIB=m
# CONFIG_INFINIBAND_IPOIB_CM is not set
CONFIG_INFINIBAND_IPOIB_DEBUG=y
# CONFIG_INFINIBAND_IPOIB_DEBUG_DATA is not set
CONFIG_INFINIBAND_SRP=m
CONFIG_INFINIBAND_ISER=m
CONFIG_EDAC=y

#
# Reporting subsystems
#
# CONFIG_EDAC_DEBUG is not set
CONFIG_EDAC_MM_EDAC=m
CONFIG_EDAC_E752X=m
CONFIG_EDAC_I82975X=m
CONFIG_EDAC_I3000=m
CONFIG_EDAC_I5000=m
CONFIG_RTC_LIB=y
CONFIG_RTC_CLASS=y
CONFIG_RTC_HCTOSYS=y
CONFIG_RTC_HCTOSYS_DEVICE="rtc0"
# CONFIG_RTC_DEBUG is not set

#
# RTC interfaces
#
CONFIG_RTC_INTF_SYSFS=y
CONFIG_RTC_INTF_PROC=y
CONFIG_RTC_INTF_DEV=y
# CONFIG_RTC_INTF_DEV_UIE_EMUL is not set
# CONFIG_RTC_DRV_TEST is not set

#
# I2C RTC drivers
#
CONFIG_RTC_DRV_DS1307=m
CONFIG_RTC_DRV_DS1374=m
CONFIG_RTC_DRV_DS1672=m
CONFIG_RTC_DRV_MAX6900=m
CONFIG_RTC_DRV_RS5C372=m
CONFIG_RTC_DRV_ISL1208=m
CONFIG_RTC_DRV_X1205=m
CONFIG_RTC_DRV_PCF8563=m
CONFIG_RTC_DRV_PCF8583=m
CONFIG_RTC_DRV_M41T80=m
# CONFIG_RTC_DRV_M41T80_WDT is not set
CONFIG_RTC_DRV_S35390A=m
CONFIG_RTC_DRV_FM3130=m

#
# SPI RTC drivers
#
CONFIG_RTC_DRV_MAX6902=m
CONFIG_RTC_DRV_R9701=m
CONFIG_RTC_DRV_RS5C348=m

#
# Platform RTC drivers
#
CONFIG_RTC_DRV_CMOS=y
CONFIG_RTC_DRV_DS1511=m
CONFIG_RTC_DRV_DS1553=m
CONFIG_RTC_DRV_DS1742=m
CONFIG_RTC_DRV_STK17TA8=m
CONFIG_RTC_DRV_M48T86=m
CONFIG_RTC_DRV_M48T59=m
CONFIG_RTC_DRV_V3020=m

#
# on-CPU RTC drivers
#
CONFIG_DMADEVICES=y

#
# DMA Devices
#
CONFIG_INTEL_IOATDMA=m
CONFIG_DMA_ENGINE=y

#
# DMA Clients
#
CONFIG_NET_DMA=y
CONFIG_DCA=m
# CONFIG_AUXDISPLAY is not set
CONFIG_UIO=m
CONFIG_UIO_CIF=m
CONFIG_UIO_SMX=m

#
# Firmware Drivers
#
CONFIG_EDD=m
# CONFIG_EDD_OFF is not set
CONFIG_EFI_VARS=m
CONFIG_DELL_RBU=m
CONFIG_DCDBAS=m
CONFIG_DMIID=y
CONFIG_ISCSI_IBFT_FIND=y
CONFIG_ISCSI_IBFT=y

#
# File systems
#
CONFIG_EXT2_FS=m
CONFIG_EXT2_FS_XATTR=y
CONFIG_EXT2_FS_POSIX_ACL=y
CONFIG_EXT2_FS_SECURITY=y
# CONFIG_EXT2_FS_XIP is not set
CONFIG_EXT3_FS=m
CONFIG_EXT3_FS_XATTR=y
CONFIG_EXT3_FS_POSIX_ACL=y
CONFIG_EXT3_FS_SECURITY=y
CONFIG_EXT4DEV_FS=m
CONFIG_EXT4DEV_FS_XATTR=y
CONFIG_EXT4DEV_FS_POSIX_ACL=y
CONFIG_EXT4DEV_FS_SECURITY=y
CONFIG_JBD=m
# CONFIG_JBD_DEBUG is not set
CONFIG_JBD2=m
# CONFIG_JBD2_DEBUG is not set
CONFIG_FS_MBCACHE=m
CONFIG_REISERFS_FS=m
# CONFIG_REISERFS_CHECK is not set
# CONFIG_REISERFS_PROC_INFO is not set
CONFIG_REISERFS_FS_XATTR=y
CONFIG_REISERFS_FS_POSIX_ACL=y
CONFIG_REISERFS_FS_SECURITY=y
CONFIG_JFS_FS=m
CONFIG_JFS_POSIX_ACL=y
CONFIG_JFS_SECURITY=y
# CONFIG_JFS_DEBUG is not set
# CONFIG_JFS_STATISTICS is not set
CONFIG_FS_POSIX_ACL=y
CONFIG_XFS_FS=m
CONFIG_XFS_QUOTA=y
CONFIG_XFS_POSIX_ACL=y
CONFIG_XFS_RT=y
# CONFIG_XFS_DEBUG is not set
CONFIG_GFS2_FS=m
CONFIG_GFS2_FS_LOCKING_NOLOCK=m
CONFIG_GFS2_FS_LOCKING_DLM=m
CONFIG_OCFS2_FS=m
CONFIG_OCFS2_FS_O2CB=m
CONFIG_OCFS2_FS_USERSPACE_CLUSTER=m
CONFIG_OCFS2_DEBUG_MASKLOG=y
# CONFIG_OCFS2_DEBUG_FS is not set
CONFIG_DNOTIFY=y
CONFIG_INOTIFY=y
CONFIG_INOTIFY_USER=y
CONFIG_QUOTA=y
CONFIG_QUOTA_NETLINK_INTERFACE=y
CONFIG_PRINT_QUOTA_WARNING=y
CONFIG_QFMT_V1=m
CONFIG_QFMT_V2=m
CONFIG_QUOTACTL=y
CONFIG_AUTOFS_FS=m
CONFIG_AUTOFS4_FS=m
CONFIG_FUSE_FS=m
CONFIG_GENERIC_ACL=y

#
# CD-ROM/DVD Filesystems
#
CONFIG_ISO9660_FS=m
CONFIG_JOLIET=y
CONFIG_ZISOFS=y
CONFIG_UDF_FS=m
CONFIG_UDF_NLS=y

#
# DOS/FAT/NT Filesystems
#
CONFIG_FAT_FS=m
CONFIG_MSDOS_FS=m
CONFIG_VFAT_FS=m
CONFIG_FAT_DEFAULT_CODEPAGE=437
CONFIG_FAT_DEFAULT_IOCHARSET="utf8"
CONFIG_NTFS_FS=m
# CONFIG_NTFS_DEBUG is not set
CONFIG_NTFS_RW=y

#
# Pseudo filesystems
#
CONFIG_PROC_FS=y
CONFIG_PROC_KCORE=y
CONFIG_PROC_SYSCTL=y
CONFIG_SYSFS=y
CONFIG_TMPFS=y
CONFIG_TMPFS_POSIX_ACL=y
CONFIG_HUGETLBFS=y
CONFIG_HUGETLB_PAGE=y
CONFIG_CONFIGFS_FS=m

#
# Miscellaneous filesystems
#
CONFIG_ADFS_FS=m
# CONFIG_ADFS_FS_RW is not set
CONFIG_AFFS_FS=m
CONFIG_ECRYPT_FS=m
CONFIG_HFS_FS=m
CONFIG_HFSPLUS_FS=m
CONFIG_BEFS_FS=m
# CONFIG_BEFS_DEBUG is not set
CONFIG_BFS_FS=m
CONFIG_EFS_FS=m
CONFIG_JFFS2_FS=m
CONFIG_JFFS2_FS_DEBUG=0
CONFIG_JFFS2_FS_WRITEBUFFER=y
# CONFIG_JFFS2_FS_WBUF_VERIFY is not set
CONFIG_JFFS2_SUMMARY=y
CONFIG_JFFS2_FS_XATTR=y
CONFIG_JFFS2_FS_POSIX_ACL=y
CONFIG_JFFS2_FS_SECURITY=y
CONFIG_JFFS2_COMPRESSION_OPTIONS=y
CONFIG_JFFS2_ZLIB=y
CONFIG_JFFS2_LZO=y
CONFIG_JFFS2_RTIME=y
# CONFIG_JFFS2_RUBIN is not set
# CONFIG_JFFS2_CMODE_NONE is not set
CONFIG_JFFS2_CMODE_PRIORITY=y
# CONFIG_JFFS2_CMODE_SIZE is not set
# CONFIG_JFFS2_CMODE_FAVOURLZO is not set
CONFIG_CRAMFS=m
CONFIG_VXFS_FS=m
CONFIG_MINIX_FS=m
CONFIG_HPFS_FS=m
CONFIG_QNX4FS_FS=m
CONFIG_ROMFS_FS=m
CONFIG_SYSV_FS=m
CONFIG_UFS_FS=m
# CONFIG_UFS_FS_WRITE is not set
# CONFIG_UFS_DEBUG is not set
CONFIG_NETWORK_FILESYSTEMS=y
CONFIG_NFS_FS=m
CONFIG_NFS_V3=y
CONFIG_NFS_V3_ACL=y
CONFIG_NFS_V4=y
CONFIG_NFSD=m
CONFIG_NFSD_V2_ACL=y
CONFIG_NFSD_V3=y
CONFIG_NFSD_V3_ACL=y
CONFIG_NFSD_V4=y
CONFIG_LOCKD=m
CONFIG_LOCKD_V4=y
CONFIG_EXPORTFS=m
CONFIG_NFS_ACL_SUPPORT=m
CONFIG_NFS_COMMON=y
CONFIG_SUNRPC=m
CONFIG_SUNRPC_GSS=m
CONFIG_SUNRPC_XPRT_RDMA=m
CONFIG_SUNRPC_BIND34=y
CONFIG_RPCSEC_GSS_KRB5=m
CONFIG_RPCSEC_GSS_SPKM3=m
# CONFIG_SMB_FS is not set
CONFIG_CIFS=m
# CONFIG_CIFS_STATS is not set
CONFIG_CIFS_WEAK_PW_HASH=y
CONFIG_CIFS_XATTR=y
CONFIG_CIFS_POSIX=y
# CONFIG_CIFS_DEBUG2 is not set
CONFIG_CIFS_EXPERIMENTAL=y
CONFIG_CIFS_UPCALL=y
CONFIG_CIFS_DFS_UPCALL=y
CONFIG_NCP_FS=m
# CONFIG_NCPFS_PACKET_SIGNING is not set
# CONFIG_NCPFS_IOCTL_LOCKING is not set
# CONFIG_NCPFS_STRONG is not set
CONFIG_NCPFS_NFS_NS=y
CONFIG_NCPFS_OS2_NS=y
# CONFIG_NCPFS_SMALLDOS is not set
CONFIG_NCPFS_NLS=y
CONFIG_NCPFS_EXTRAS=y
CONFIG_CODA_FS=m
# CONFIG_CODA_FS_OLD_API is not set
CONFIG_AFS_FS=m
# CONFIG_AFS_DEBUG is not set
CONFIG_9P_FS=m

#
# Partition Types
#
CONFIG_PARTITION_ADVANCED=y
CONFIG_ACORN_PARTITION=y
# CONFIG_ACORN_PARTITION_CUMANA is not set
# CONFIG_ACORN_PARTITION_EESOX is not set
CONFIG_ACORN_PARTITION_ICS=y
# CONFIG_ACORN_PARTITION_ADFS is not set
# CONFIG_ACORN_PARTITION_POWERTEC is not set
CONFIG_ACORN_PARTITION_RISCIX=y
CONFIG_OSF_PARTITION=y
CONFIG_AMIGA_PARTITION=y
CONFIG_ATARI_PARTITION=y
CONFIG_MAC_PARTITION=y
CONFIG_MSDOS_PARTITION=y
CONFIG_BSD_DISKLABEL=y
CONFIG_MINIX_SUBPARTITION=y
CONFIG_SOLARIS_X86_PARTITION=y
CONFIG_UNIXWARE_DISKLABEL=y
CONFIG_LDM_PARTITION=y
# CONFIG_LDM_DEBUG is not set
CONFIG_SGI_PARTITION=y
CONFIG_ULTRIX_PARTITION=y
CONFIG_SUN_PARTITION=y
CONFIG_KARMA_PARTITION=y
CONFIG_EFI_PARTITION=y
# CONFIG_SYSV68_PARTITION is not set
CONFIG_NLS=m
CONFIG_NLS_DEFAULT="utf8"
CONFIG_NLS_CODEPAGE_437=m
CONFIG_NLS_CODEPAGE_737=m
CONFIG_NLS_CODEPAGE_775=m
CONFIG_NLS_CODEPAGE_850=m
CONFIG_NLS_CODEPAGE_852=m
CONFIG_NLS_CODEPAGE_855=m
CONFIG_NLS_CODEPAGE_857=m
CONFIG_NLS_CODEPAGE_860=m
CONFIG_NLS_CODEPAGE_861=m
CONFIG_NLS_CODEPAGE_862=m
CONFIG_NLS_CODEPAGE_863=m
CONFIG_NLS_CODEPAGE_864=m
CONFIG_NLS_CODEPAGE_865=m
CONFIG_NLS_CODEPAGE_866=m
CONFIG_NLS_CODEPAGE_869=m
CONFIG_NLS_CODEPAGE_936=m
CONFIG_NLS_CODEPAGE_950=m
CONFIG_NLS_CODEPAGE_932=m
CONFIG_NLS_CODEPAGE_949=m
CONFIG_NLS_CODEPAGE_874=m
CONFIG_NLS_ISO8859_8=m
CONFIG_NLS_CODEPAGE_1250=m
CONFIG_NLS_CODEPAGE_1251=m
CONFIG_NLS_ASCII=m
CONFIG_NLS_ISO8859_1=m
CONFIG_NLS_ISO8859_2=m
CONFIG_NLS_ISO8859_3=m
CONFIG_NLS_ISO8859_4=m
CONFIG_NLS_ISO8859_5=m
CONFIG_NLS_ISO8859_6=m
CONFIG_NLS_ISO8859_7=m
CONFIG_NLS_ISO8859_9=m
CONFIG_NLS_ISO8859_13=m
CONFIG_NLS_ISO8859_14=m
CONFIG_NLS_ISO8859_15=m
CONFIG_NLS_KOI8_R=m
CONFIG_NLS_KOI8_U=m
CONFIG_NLS_UTF8=m
CONFIG_DLM=m
CONFIG_DLM_DEBUG=y

#
# Kernel hacking
#
CONFIG_TRACE_IRQFLAGS_SUPPORT=y
CONFIG_PRINTK_TIME=y
CONFIG_ENABLE_WARN_DEPRECATED=y
CONFIG_ENABLE_MUST_CHECK=y
CONFIG_FRAME_WARN=2048
CONFIG_MAGIC_SYSRQ=y
CONFIG_UNUSED_SYMBOLS=y
CONFIG_DEBUG_FS=y
# CONFIG_HEADERS_CHECK is not set
CONFIG_DEBUG_KERNEL=y
# CONFIG_DEBUG_SHIRQ is not set
CONFIG_DETECT_SOFTLOCKUP=y
CONFIG_SCHED_DEBUG=y
# CONFIG_SCHEDSTATS is not set
CONFIG_TIMER_STATS=y
# CONFIG_DEBUG_OBJECTS is not set
# CONFIG_DEBUG_SLAB is not set
# CONFIG_DEBUG_RT_MUTEXES is not set
# CONFIG_RT_MUTEX_TESTER is not set
# CONFIG_DEBUG_SPINLOCK is not set
# CONFIG_DEBUG_MUTEXES is not set
# CONFIG_DEBUG_LOCK_ALLOC is not set
# CONFIG_PROVE_LOCKING is not set
# CONFIG_LOCK_STAT is not set
# CONFIG_DEBUG_SPINLOCK_SLEEP is not set
# CONFIG_DEBUG_LOCKING_API_SELFTESTS is not set
# CONFIG_DEBUG_KOBJECT is not set
CONFIG_DEBUG_BUGVERBOSE=y
# CONFIG_DEBUG_INFO is not set
# CONFIG_DEBUG_VM is not set
# CONFIG_DEBUG_WRITECOUNT is not set
# CONFIG_DEBUG_LIST is not set
# CONFIG_DEBUG_SG is not set
# CONFIG_FRAME_POINTER is not set
# CONFIG_BOOT_PRINTK_DELAY is not set
# CONFIG_RCU_TORTURE_TEST is not set
# CONFIG_BACKTRACE_SELF_TEST is not set
# CONFIG_FAULT_INJECTION is not set
# CONFIG_LATENCYTOP is not set
# CONFIG_PROVIDE_OHCI1394_DMA_INIT is not set
# CONFIG_SAMPLES is not set
CONFIG_HAVE_ARCH_KGDB=y
# CONFIG_KGDB is not set
# CONFIG_NONPROMISC_DEVMEM is not set
CONFIG_EARLY_PRINTK=y
# CONFIG_DEBUG_STACKOVERFLOW is not set
# CONFIG_DEBUG_STACK_USAGE is not set
# CONFIG_DEBUG_PAGEALLOC is not set
# CONFIG_DEBUG_PER_CPU_MAPS is not set
# CONFIG_X86_PTDUMP is not set
# CONFIG_DEBUG_RODATA is not set
# CONFIG_DIRECT_GBPAGES is not set
# CONFIG_DEBUG_NX_TEST is not set
CONFIG_X86_MPPARSE=y
# CONFIG_IOMMU_DEBUG is not set
CONFIG_IO_DELAY_TYPE_0X80=0
CONFIG_IO_DELAY_TYPE_0XED=1
CONFIG_IO_DELAY_TYPE_UDELAY=2
CONFIG_IO_DELAY_TYPE_NONE=3
CONFIG_IO_DELAY_0X80=y
# CONFIG_IO_DELAY_0XED is not set
# CONFIG_IO_DELAY_UDELAY is not set
# CONFIG_IO_DELAY_NONE is not set
CONFIG_DEFAULT_IO_DELAY_TYPE=0
# CONFIG_DEBUG_BOOT_PARAMS is not set
# CONFIG_CPA_DEBUG is not set

#
# Security options
#
CONFIG_KEYS=y
# CONFIG_KEYS_DEBUG_PROC_KEYS is not set
CONFIG_SECURITY=y
CONFIG_SECURITY_NETWORK=y
CONFIG_SECURITY_NETWORK_XFRM=y
CONFIG_SECURITY_CAPABILITIES=y
CONFIG_SECURITY_FILE_CAPABILITIES=y
# CONFIG_SECURITY_ROOTPLUG is not set
CONFIG_SECURITY_DEFAULT_MMAP_MIN_ADDR=0
CONFIG_SECURITY_SELINUX=y
CONFIG_SECURITY_SELINUX_BOOTPARAM=y
CONFIG_SECURITY_SELINUX_BOOTPARAM_VALUE=0
CONFIG_SECURITY_SELINUX_DISABLE=y
CONFIG_SECURITY_SELINUX_DEVELOP=y
CONFIG_SECURITY_SELINUX_AVC_STATS=y
CONFIG_SECURITY_SELINUX_CHECKREQPROT_VALUE=1
# CONFIG_SECURITY_SELINUX_ENABLE_SECMARK_DEFAULT is not set
# CONFIG_SECURITY_SELINUX_POLICYDB_VERSION_MAX is not set
CONFIG_XOR_BLOCKS=m
CONFIG_ASYNC_CORE=m
CONFIG_ASYNC_MEMCPY=m
CONFIG_ASYNC_XOR=m
CONFIG_CRYPTO=y

#
# Crypto core or helper
#
CONFIG_CRYPTO_ALGAPI=y
CONFIG_CRYPTO_AEAD=m
CONFIG_CRYPTO_BLKCIPHER=m
CONFIG_CRYPTO_HASH=y
CONFIG_CRYPTO_MANAGER=y
CONFIG_CRYPTO_GF128MUL=m
CONFIG_CRYPTO_NULL=m
# CONFIG_CRYPTO_CRYPTD is not set
CONFIG_CRYPTO_AUTHENC=m
CONFIG_CRYPTO_TEST=m

#
# Authenticated Encryption with Associated Data
#
CONFIG_CRYPTO_CCM=m
CONFIG_CRYPTO_GCM=m
CONFIG_CRYPTO_SEQIV=m

#
# Block modes
#
CONFIG_CRYPTO_CBC=m
CONFIG_CRYPTO_CTR=m
CONFIG_CRYPTO_CTS=m
CONFIG_CRYPTO_ECB=m
CONFIG_CRYPTO_LRW=m
CONFIG_CRYPTO_PCBC=m
CONFIG_CRYPTO_XTS=m

#
# Hash modes
#
CONFIG_CRYPTO_HMAC=y
CONFIG_CRYPTO_XCBC=m

#
# Digest
#
CONFIG_CRYPTO_CRC32C=m
CONFIG_CRYPTO_MD4=m
CONFIG_CRYPTO_MD5=y
CONFIG_CRYPTO_MICHAEL_MIC=m
CONFIG_CRYPTO_SHA1=m
CONFIG_CRYPTO_SHA256=m
CONFIG_CRYPTO_SHA512=m
CONFIG_CRYPTO_TGR192=m
CONFIG_CRYPTO_WP512=m

#
# Ciphers
#
CONFIG_CRYPTO_AES=m
CONFIG_CRYPTO_AES_X86_64=m
CONFIG_CRYPTO_ANUBIS=m
CONFIG_CRYPTO_ARC4=m
CONFIG_CRYPTO_BLOWFISH=m
CONFIG_CRYPTO_CAMELLIA=m
CONFIG_CRYPTO_CAST5=m
CONFIG_CRYPTO_CAST6=m
CONFIG_CRYPTO_DES=m
CONFIG_CRYPTO_FCRYPT=m
CONFIG_CRYPTO_KHAZAD=m
CONFIG_CRYPTO_SALSA20=m
CONFIG_CRYPTO_SALSA20_X86_64=m
CONFIG_CRYPTO_SEED=m
CONFIG_CRYPTO_SERPENT=m
CONFIG_CRYPTO_TEA=m
CONFIG_CRYPTO_TWOFISH=m
CONFIG_CRYPTO_TWOFISH_COMMON=m
CONFIG_CRYPTO_TWOFISH_X86_64=m

#
# Compression
#
CONFIG_CRYPTO_DEFLATE=m
CONFIG_CRYPTO_LZO=m
CONFIG_CRYPTO_HW=y
CONFIG_CRYPTO_DEV_HIFN_795X=m
CONFIG_CRYPTO_DEV_HIFN_795X_RNG=y
CONFIG_HAVE_KVM=y
CONFIG_VIRTUALIZATION=y
CONFIG_KVM=m
CONFIG_KVM_INTEL=m
CONFIG_KVM_AMD=m
CONFIG_VIRTIO=m
CONFIG_VIRTIO_RING=m
CONFIG_VIRTIO_PCI=m
CONFIG_VIRTIO_BALLOON=m

#
# Library routines
#
CONFIG_BITREVERSE=y
CONFIG_GENERIC_FIND_FIRST_BIT=y
CONFIG_GENERIC_FIND_NEXT_BIT=y
CONFIG_CRC_CCITT=m
CONFIG_CRC16=m
CONFIG_CRC_ITU_T=m
CONFIG_CRC32=y
CONFIG_CRC7=m
CONFIG_LIBCRC32C=m
CONFIG_ZLIB_INFLATE=m
CONFIG_ZLIB_DEFLATE=m
CONFIG_LZO_COMPRESS=m
CONFIG_LZO_DECOMPRESS=m
CONFIG_GENERIC_ALLOCATOR=y
CONFIG_REED_SOLOMON=m
CONFIG_REED_SOLOMON_DEC16=y
CONFIG_TEXTSEARCH=y
CONFIG_TEXTSEARCH_KMP=m
CONFIG_TEXTSEARCH_BM=m
CONFIG_TEXTSEARCH_FSM=m
CONFIG_PLIST=y
CONFIG_HAS_IOMEM=y
CONFIG_HAS_IOPORT=y
CONFIG_HAS_DMA=y
CONFIG_CHECK_SIGNATURE=y
```

---

### Post by theotherphil on 2008-12-18
> **roelpeeters said:**
> OK, in both cases I am seeing things that don't sound right to me. Unless you are running mobile CPUs, the speed of the processor should be the 'full speed' (unless it is underclocked). In the case of Billxyzzy the cpu speed is 0.000, in the case of ras-zealot I see a lower speed (1998) than I would expect. Can you show the output of 'dmesg' also?


Most desktop systems now support Speedstep/ Cool n Quiet which will drop the multiplier on the CPU to allow it to run at a slower speed for power savings. As you can see below, my E8500's default speed is 3.16GHz (9.5 multiplier) but they are actually running at 2Ghz (6 multiplier) at idle. They speed back up under load:

```
phil@polaris:~$ cat /proc/cpuinfo
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 23
model name	: Intel(R) Core(TM)2 Duo CPU     E8500  @ 3.16GHz
stepping	: 6
cpu MHz		: 1998.000
cache size	: 6144 KB
physical id	: 0
siblings	: 2
core id		: 0
cpu cores	: 2
apicid		: 0
initial apicid	: 0
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good nopl pni monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr sse4_1 lahf_lm
bogomips	: 6339.47
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:

processor	: 1
vendor_id	: GenuineIntel
cpu family	: 6
model		: 23
model name	: Intel(R) Core(TM)2 Duo CPU     E8500  @ 3.16GHz
stepping	: 6
cpu MHz		: 1998.000
cache size	: 6144 KB
physical id	: 0
siblings	: 2
core id		: 1
cpu cores	: 2
apicid		: 1
initial apicid	: 1
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good nopl pni monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr sse4_1 lahf_lm
bogomips	: 6339.51
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:

```

---

### Post by stchman on 2008-12-18
> **ras-zealot said:**
> i have an intel core 2 duo E8400, when i check the system monitor i see only one cpu working, how can i enable the both. im using 64bit intrepid ibex

The -generic kernel in Intrepid has SMP support OOB.  Trust me all of your cores are being used.

---

### Post by ras-zealot on 2008-12-19
OMG nvm someone changed my bios options -.-" now im feeling stupid for not checking that again and ill see who the fk was playing with my bios...

---

### Post by zongpog on 2009-01-21
Hi,

I have a similar problem. My Ubuntu Fiesty recognised only one core. System Monitor reports only one core.  How could you enable the second one?

# cat /proc/cpuinfo
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 14
model name	: Genuine Intel(R) CPU           T2600  @ 2.16GHz
stepping	: 8
cpu MHz		: 1000.000
cache size	: 2048 KB
physical id	: 0
siblings	: 1
core id		: 0
cpu cores	: 1
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx constant_tsc up arch_perfmon bts pni monitor vmx est tm2 xtpr
bogomips	: 4338.83
clflush size	: 64

# uname -a
Linux fred 2.6.24-23-generic #1 SMP Thu Nov 27 18:44:42 UTC 2008 i686 GNU/Linux

---

### Post by rcorbish on 2009-01-23
I'm in a similar situation but dmesg shows ...

[    0.272027] SMP disabled
[    0.272065] Brought up 1 CPUs
[    0.272067] Total of 1 processors activated (5999.91 BogoMIPS).

BIOS looks good

generic kernel and cpuinfo reports only a single CPU

uname -v
#1 SMP Thu Nov 20 22:15:32 UTC 2008

---

### Post by rcorbish on 2009-01-23
Actually BIOS wasn't good ACPI was disabled. Turned it on - I'm in business with 2 Cores (at 1% each but that's not the point!)

---

### Post by zongpog on 2009-01-24
I checked the BIOS and there are no settings for ACPI.  Its a Sony Vaio SZ and has a custom Phoenix BIOS that has had many of the options removed at Sony's behest.

I booted into Windows XP and it shows two cores and uses those quite happily.  Ubuntu just does not know the other core is there.

---

### Post by dcstar on 2009-01-25
> **ras-zealot said:**
> OMG nvm someone changed my bios options -.-" now im feeling stupid for not checking that again and ill see who the fk was playing with my bios...

And now you will use a BIOS admin password, won't you..... ;-)

---

