---
title: "DualCore becomes SingleCore after upgrade 8.04 to 8.10"
date: 2008-11-13
forum: x86 64-bit Users
---

### Post by Phkillah on 2008-11-13
Greetings, fellow Ubuntians!

My Ubuntu 8.04 x64 marvelously upgraded himself to 8.10 apparently without any problem.
I must say i was surprised by the efficient release-upgrade script since it all works now.... except for my AMD x2....

My previous kernel was 2.6.24-18-generic, and now i have 2.6.27-8-generic, and "cat /proc/cpuinfo" only shows core#0......
Worst of all, my vital virtual machines won't boot since they are DualCore enabled...

Here's the current status output:
```
phk ~ $ cat /proc/cpuinfo 
processor	: 0
vendor_id	: AuthenticAMD
cpu family	: 15
model		: 35
model name	: AMD Athlon(tm) 64 X2 Dual Core Processor 4400+
stepping	: 2
cpu MHz		: 2250.612
cache size	: 1024 KB
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
flags		: fpu vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt lm 3dnowext 3dnow rep_good nopl pni lahf_lm cmp_legacy
bogomips	: 4501.22
TLB size	: 1024 4K pages
clflush size	: 64
cache_alignment	: 64
address sizes	: 40 bits physical, 48 bits virtual
power management: ts fid vid ttp

phk ~ $ uname -a
Linux Phk-HQ 2.6.27-8-generic #1 SMP Thu Nov 6 17:38:14 UTC 2008 x86_64 GNU/Linux

```

Terrible... :( Anyone has an idea on how to fix this? Please shed some light...


Thank you.

Cheers

---

### Post by punkybouy on 2008-11-13
I have had a couple of upgrades in the past not install the SMP kernel.  A quick check of Package Manger doesn't show anything obvious.  Are you sure you are not booting from an older kernel?  Sorry I can't be more helpful.

---

### Post by Phkillah on 2008-11-14
> **punkybouy said:**
> I have had a couple of upgrades in the past not install the SMP kernel.  A quick check of Package Manger doesn't show anything obvious.  Are you sure you are not booting from an older kernel?  Sorry I can't be more helpful.

Yes, uname -a shows me this
```
phk ~ $ uname -a
Linux Phk-HQ 2.6.27-8-generic #1 SMP Thu Nov 6 17:38:14 UTC 2008 x86_64 GNU/Linux

```

Why.. ? :(

Anyone PLLLEEEAAASSSEE!!! I'll give you some :popcorn:

---

### Post by Teddy_P on 2008-11-14
Heres my output so you can compare. This is my first Dual Core with 64bit.
And I just got it two days ago. Sorry I can't help much more.

Teddy_P
```
processor	: 0
vendor_id	: AuthenticAMD
cpu family	: 15
model		: 107
model name	: AMD Athlon(tm) 64 X2 Dual Core Processor 5000+
stepping	: 2
cpu MHz		: 1000.000
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
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp lm 3dnowext 3dnow rep_good nopl pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy 3dnowprefetch
bogomips	: 2004.25
TLB size	: 1024 4K pages
clflush size	: 64
cache_alignment	: 64
address sizes	: 40 bits physical, 48 bits virtual
power management: ts fid vid ttp tm stc 100mhzsteps

processor	: 1
vendor_id	: AuthenticAMD
cpu family	: 15
model		: 107
model name	: AMD Athlon(tm) 64 X2 Dual Core Processor 5000+
stepping	: 2
cpu MHz		: 1000.000
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
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp lm 3dnowext 3dnow rep_good nopl pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy 3dnowprefetch
bogomips	: 2004.25
TLB size	: 1024 4K pages
clflush size	: 64
cache_alignment	: 64
address sizes	: 40 bits physical, 48 bits virtual
power management: ts fid vid ttp tm stc 100mhzsteps
```

---

### Post by Yellow Pasque on 2008-11-14
Well, make sure you have the latest BIOS for your motherboard and that there's no disabled option for Dual Core in the BIOS. If the BIOS offers an option of what ACPI version to support, try ACPI 3.0.
If that doesn't work...
```
gksudo gedit /boot/grub/menu.lst
```
Add additional_cpus=1 to your kernel boot line, e.g:
```
title Ubuntu 8.10, kernel 2.6.27-7-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=7a119114-4fd7-4ee0-922f-a7d03a5b4b3e ro **additional_cpus=1**
initrd		/boot/initrd.img-2.6.27-7-generic
```
Save, quit, reboot. If that works, take up the cause with your mobo manufacturer to support non-Windows OS's properly.
[http://www.mjmwired.net/kernel/Documentation/x86_64/cpu-hotplug-spec](http://www.mjmwired.net/kernel/Documentation/x86_64/cpu-hotplug-spec)

---

### Post by radtek on 2008-11-14
I got this:

```
radtek@tosh:~$ cat /proc/cpuinfo 
[COLOR="DarkRed"]processor	: 0[/COLOR]
vendor_id	: AuthenticAMD
cpu family	: 15
model		: 104
model name	: AMD Athlon(tm) 64 X2 Dual-Core Processor TK-55
[COLOR="DarkRed"]stepping	: 1[/COLOR]
cpu MHz		: 800.000
cache size	: 256 KB
physical id	: 0
siblings	: 2
core id		: 0
[COLOR="DarkRed"]cpu cores	: 2[/COLOR]
apicid		: 0
initial apicid	: 0
fpu		: yes
fpu_exception	: yes
cpuid level	: 1
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp lm 3dnowext 3dnow rep_good nopl pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy 3dnowprefetch
bogomips	: 1596.17
TLB size	: 1024 4K pages
clflush size	: 64
cache_alignment	: 64
address sizes	: 40 bits physical, 48 bits virtual
power management: ts fid vid ttp tm stc 100mhzsteps

```

Works for me...

I'm wondering what the "stepping" means... Is it dynamic powersaving?

---

### Post by Yellow Pasque on 2008-11-14
"Stepping" refers to physical changes in the die during the manufacturing process. For example, AMD 65nm Brisbane cores were changed in the middle of their sales life (AMD had advanced their 65nm manufacturing process so that CPU's would use less power).

---

### Post by Kilz on 2008-11-14
> **Phkillah said:**
> Yes, uname -a shows me this
```
phk ~ $ uname -a
Linux Phk-HQ 2.6.27-8-generic #1 SMP Thu Nov 6 17:38:14 UTC 2008 x86_64 GNU/Linux

```

Why.. ? :(

Anyone PLLLEEEAAASSSEE!!! I'll give you some :popcorn:

Have you filled out a bug report?

---

### Post by Yellow Pasque on 2008-11-14
> **Kilz said:**
> Have you filled out a bug report?
Before filing a bug report, try the kernel parameter as I suggested in my previous post. Your Launchpad report will get more developer attention if you demonstrate a solid understanding of the problem and show that you've attempted to fix it yourself before caving in and bothering the developers.

EDIT: There's a similar report here: [https://bugs.launchpad.net/ubuntu/+bug/281329](https://bugs.launchpad.net/ubuntu/+bug/281329)

In this case, the CPU hotplugging in the kernel doesn't play nice with the specific motherboard. The motherboard/BIOS's ACPI table implementation is suspect and this should be taken up with the motherboard manufacturer assuming you have the latest BIOS revision. Sure, the motherborad manufacturer will likely respond with "we don't support Linux", in which case you threaten legal action because the manufacturer probably advertises ACPI x.0 standard support, but doesn't implement it properly :P

> General Stuff about CPU Hotplug
--------------------------------

Command Line Switches
---------------------
maxcpus=n    Restrict boot time cpus to n. Say if you have 4 cpus, using
             maxcpus=2 will only boot 2. You can choose to bring the
             other cpus later online, read FAQ's for more info.

additional_cpus=n (*)	Use this to limit hotpluggable cpus. This option sets
  			cpu_possible_map = cpu_present_map + additional_cpus

(*) Option valid only for following architectures
- x86_64, ia64

ia64 and x86_64 use the number of disabled local apics in ACPI tables MADT
to determine the number of potentially hot-pluggable cpus. The implementation
should only rely on this to count the # of cpus, but *MUST* not rely on the
apicid values in those tables for disabled apics. In the event BIOS doesn't
mark such hot-pluggable cpus as disabled entries, one could use this
parameter "additional_cpus=x" to represent those cpus in the cpu_possible_map.

possible_cpus=n		[s390 only] use this to set hotpluggable cpus.
			This option sets possible_cpus bits in
			cpu_possible_map. Thus keeping the numbers of bits set
			constant even if the machine gets rebooted.


---

### Post by Phkillah on 2008-11-15
YES, i have an old old old BIOS.. Sorry i f'got that...
I have a 2005 "Oscar Wu's" tweaked BIOS so that i can run my GeilOneW DDRs at 500mhz 1.5-2-2-5 timings.. they drink 3.5v each.. Really really fast RAMs :D

This BIOS prolly has the apic and acpi bugz.. I've tested my ubuntu with all the possible bios acpi/apic configurations, but the only way i can boot my machine is with
**apic=off**
at the grub **kernel** line..

So about the DualCore issue, i fixed it also adding
**apic=off noapic acpi=off noacpi**
to the grub kernel line..

Here it goes:
```
phk ~ $ cat /boot/grub/menu.lst
default		0
timeout		3

title		Ubuntu Linux 2.6.27-8 AMD64
root		(hd0,5)
kernel		/vmlinuz-2.6.27-8-generic root=/dev/mapper/nvidia_feejacjb8 ro quiet splash acpi=off noacpi apic=off noapic
initrd		/initrd.img-2.6.27-8-generic

```

Thanks to all of you about helping me...
No i will not report bug since this is an old BIOS which has lots of newer versions available (although none support 3.6v for DDRs)

Here's the promise:
:popcorn::popcorn::popcorn::popcorn::popcorn:

Cheers!
Phk

---

