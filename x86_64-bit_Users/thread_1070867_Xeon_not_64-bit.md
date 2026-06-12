---
title: "Xeon not 64-bit?"
date: 2009-02-15
forum: x86 64-bit Users
---

### Post by flaggh on 2009-02-15
I'm trying to install ubuntu using the ubuntu-8.04-desktop-amd64.iso image.  When I try to load the LiveCD it tells me that my processor is i1586 and incompatible but its a dual Xeon motherboard and I'm fairly sure its 64-bit.  Any idea what's going on?

Here's the output of cat /proc/cpuinfo:

```
ubuntu@ubuntu:~$ cat /proc/cpuinfo
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 15
model		: 2
model name	: Intel(R) Xeon(TM) CPU 3.06GHz
stepping	: 9
cpu MHz		: 3066.986
cache size	: 512 KB
physical id	: 0
siblings	: 2
core id		: 0
cpu cores	: 1
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 2
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe pebs bts sync_rdtsc cid xtpr
bogomips	: 6138.78
clflush size	: 64

processor	: 1
vendor_id	: GenuineIntel
cpu family	: 15
model		: 2
model name	: Intel(R) Xeon(TM) CPU 3.06GHz
stepping	: 9
cpu MHz		: 3066.986
cache size	: 512 KB
physical id	: 0
siblings	: 2
core id		: 0
cpu cores	: 1
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 2
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe pebs bts sync_rdtsc cid xtpr
bogomips	: 6133.97
clflush size	: 64

processor	: 2
vendor_id	: GenuineIntel
cpu family	: 15
model		: 2
model name	: Intel(R) Xeon(TM) CPU 3.06GHz
stepping	: 9
cpu MHz		: 3066.986
cache size	: 512 KB
physical id	: 3
siblings	: 2
core id		: 0
cpu cores	: 1
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 2
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe pebs bts sync_rdtsc cid xtpr
bogomips	: 6134.07
clflush size	: 64

processor	: 3
vendor_id	: GenuineIntel
cpu family	: 15
model		: 2
model name	: Intel(R) Xeon(TM) CPU 3.06GHz
stepping	: 9
cpu MHz		: 3066.986
cache size	: 512 KB
physical id	: 3
siblings	: 2
core id		: 0
cpu cores	: 1
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 2
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe pebs bts sync_rdtsc cid xtpr
bogomips	: 6134.07
clflush size	: 64

```

---

### Post by paulisdead on 2009-02-15
That gets real tricky to tell, since Intel's been using the xeon name for so many chips.  It looks like you have a system with 2 physical CPU sockets?  Am I right in thinking it's a dual proc system?  To me it looks like you've got 2 physical CPUs, with hyperthreading, making it appear as if you had 4 CPUs.  If that's true, you most likely don't have 64bit enabled chips.  I'm pretty sure all the 64bit xeons have had sse3 support, as well, which you seem to be lacking.  I'm not 100% on this, but I think all the 64bit xeons were dual core as well, if not all of them at least the majority.  So I'm fairly sure it's not 64bit capable.

---

### Post by flaggh on 2009-02-15
Thanks for the reply.

It is a dual processor system.  I guess I'll just have to install 32-bit on it.  Do you know what it means by i1586 cpu?

---

### Post by Yellow Pasque on 2009-02-15
It looks like you have two Prescott-based Xeons with hyperthreading. It would be helpful if you could find the model number of the CPU.

[http://www.intel.com/support/processors/xeon/sb/CS-012580.htm](http://www.intel.com/support/processors/xeon/sb/CS-012580.htm)

---

### Post by sanderj on 2009-02-15
You CPU's flags info does not contain "lm" (Long Mode), and is thus not 64-bit. It's 32-bit. Install the i386/32-bit version of Ubuntu.


flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe pebs bts sync_rdtsc cid xtpr

---

### Post by jerrrys on 2009-02-15
Xeon 3.06 	3066 MHz 	512 KiB 	533 MT/s 	23x 	1.525 V 	85 W 	Socket 604 	March 10 2003 	RK80532KE083512

and yes its 32bit w/hyperthreading

you running an x235 like me??

---

### Post by flaggh on 2009-02-15
Thanks for all the help.  32-bit is running great.

---

