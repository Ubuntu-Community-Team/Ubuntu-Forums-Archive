---
title: "A core missing!"
date: 2009-04-29
forum: x86 64-bit Users
---

### Post by Mman_ on 2009-04-29
Hi.

I upgraded my system from Ibex to Jaunty a couple of days ago and wondered why is new distribution so horribly slow.

Today I found the reason. Ubuntu is missing one of my CPU cores! =O

I have an AMD 64 x2 6400 cpu, and on Ibex both cores were there. Now Jaunty sees it as a one core cpu.

I have no idea how to start bringing my core back, so any help is very much appreciated.

Thanks in advance!

Here's my "cat /proc/cpuinfo"
```

mman@b52:~$ cat /proc/cpuinfo 
processor	: 0
vendor_id	: AuthenticAMD
cpu family	: 15
model		: 43
model name	: AMD Athlon(tm) 64 X2 Dual Core Processor 4600+
stepping	: 1
cpu MHz		: 2412.191
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
flags		: fpu vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt lm 3dnowext 3dnow rep_good pni lahf_lm cmp_legacy
bogomips	: 4824.38
TLB size	: 1024 4K pages
clflush size	: 64
cache_alignment	: 64
address sizes	: 40 bits physical, 48 bits virtual
power management: ts fid vid ttp

```

---

### Post by sanderj on 2009-04-29
Have you looked at dmesg, especially for lines like "bringing up" and/or "cpu"?

BTW: I think your CPU is 4600+, not 6400.

---

### Post by sanderj on 2009-04-29
This can be handy too:

```
ubuntu@ubuntu:~$ dmesg | grep -i cpu
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] KERNEL supported cpus:
[    0.000000]   Transmeta TransmetaCPU
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] PERCPU: Allocating 45056 bytes of per cpu data
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 2, nr_node_ids 1
[    0.000000] Initializing CPU#0
[    0.004000] SLUB: Genslabs=12, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.004000] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.004000] Initializing cgroup subsys cpuacct
[    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004000] CPU: L2 cache: 2048K
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 0
[    0.441435] CPU0: Genuine Intel(R) CPU           T2300  @ 1.66GHz stepping 08
[    0.004000] Initializing CPU#1
[    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004000] CPU: L2 cache: 2048K
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 1
[    0.528482] CPU1: Genuine Intel(R) CPU           T2300  @ 1.66GHz stepping 08
[    0.528505] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.532047] Brought up 2 CPUs
[    0.532112] CPU0 attaching sched-domain:
[    0.532126] CPU1 attaching sched-domain:
[    0.580014] Switched to high resolution mode on CPU 0
[    0.580551] Switched to high resolution mode on CPU 1
[    1.406456] cpufreq: No nForce2 chipset.
[    1.430385] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[    1.430413] processor ACPI_CPU:00: registered as cooling_device0
[    1.431848] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
[    1.431871] processor ACPI_CPU:01: registered as cooling_device1
[    2.688702] cpuidle: using governor ladder
[    2.688846] cpuidle: using governor menu
ubuntu@ubuntu:~$ 
```

---

### Post by epsilon359 on 2009-05-03
This is not the output I should be getting on a Core 2 Duo E6600...

```
sean@xxxx:~$ dmesg | grep -i cpu
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] KERNEL supported cpus:
[    0.000000]   Transmeta TransmetaCPU
[    0.000000] ACPI: SSDT 7FEE7F80, 015C (r1  PmRef  Cpu0Ist     3000 INTL 20060912)
[    0.000000] ACPI: SSDT 7FEE8410, 02F1 (r1  PmRef    CpuPm     3000 INTL 20040311)
[    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
[    0.000000] PERCPU: Allocating 45056 bytes of per cpu data
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 1, nr_node_ids 1
[    0.000000] Initializing CPU#0
[    0.004000] SLUB: Genslabs=12, HWalign=64, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
[    0.004000] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.004000] Initializing cgroup subsys cpuacct
[    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004000] CPU: L2 cache: 4096K
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 0
[    0.335607] weird, boot CPU (#0) not listedby the BIOS.
[    0.336001] Brought up 1 CPUs
[    0.336001] CPU0 attaching NULL sched-domain.
[    0.398512] checking if image is initramfs...<7>Switched to high resolution mode on CPU 0
[    0.893847] cpufreq: No nForce2 chipset.
[    0.904608] processor ACPI_CPU:00: registered as cooling_device1
[    4.428433] cpuidle: using governor ladder
[    4.428435] cpuidle: using governor menu

```

EDIT: especially when
```
sean@xxxx:~$ cat /proc/cpuinfo
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 15
model name	: Intel(R) Core(TM)2 CPU          6600  @ 2.40GHz
stepping	: 6
cpu MHz		: 1600.000
cache size	: 4096 KB
physical id	: 0
siblings	: 1
core id		: 0
cpu cores	: 1
apicid		: 0
initial apicid	: 0
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc up arch_perfmon pebs bts pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm lahf_lm tpr_shadow
bogomips	: 4791.90
clflush size	: 64
power management:

```

---

### Post by Yellow Pasque on 2009-05-03
It looks like an incorrectly configured kernel (Transmeta CPU's ???). If it makes you feel any better, you're not the only one suffering: [https://bugs.launchpad.net/ubuntu/+bug/371210](https://bugs.launchpad.net/ubuntu/+bug/371210)

---

### Post by sanderj on 2009-05-04
I think these are the most interesting dmesg lines:

```

[    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs

[    0.000000] NR_CPUS: 64, nr_cpu_ids: 1, nr_node_ids 1

[    0.336001] Brought up 1 CPUs
```

You're not running a virtual machine, right?


If not, Googling I found [http://ubuntuforums.org/showthread.php?t=1144905](http://ubuntuforums.org/showthread.php?t=1144905) saying 


> 

 Re: Only 1 CPU core on Dualcore
I seem to have fixed this. This is what I did:

I changed my boot entry from
Code:

image=/boot/vmlinuz-2.6.28-11-generic
        label="Linux 2.6.28-11"
        append=" acpi=off noapic pci=nomsi pnpbios=off ro quiet splash"
        initrd=/boot/initrd.img-2.6.28-11-generic
        read-only

To
Code:

image=/boot/vmlinuz-2.6.28-11-generic
	label="Linux 2.6.28-11"
        append=" pci=nomsi pnpbios=off ro quiet splash"
        initrd=/boot/initrd.img-2.6.28-11-generic
        read-only

I don't really understand why it works, as I had to add "acpi=off" after the Jaunty upgrade to even make Ubuntu start properly. But right now my gnome-system-monitor shows two cpu's again!


So, (s)he changed the kernel-append-boot-options for ACPI and APIC. Can you check if that works for you?

And here's another option to check: See 

[http://ubuntuforums.org/archive/index.php/t-1062918.html](http://ubuntuforums.org/archive/index.php/t-1062918.html)

> It's fixed. System monitor now shows all four cores. The problem was that apic wasn't disabled in the kernel line, but it was in the BIOS setup. I'd already checked the BIOS to make sure all cores were enabled, but I guess I didn't notice the apic option.

So check the BIOS too for APIC to be disabled.

---

