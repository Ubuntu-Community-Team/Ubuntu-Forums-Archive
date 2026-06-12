---
title: "athlon64 x2 dual-core not showing up as 2 processors"
date: 2006-08-24
forum: x86 64-bit Users (Pre April '08)
---

### Post by danny_mandel on 2006-08-24
Hi all, I installed Ubuntu for the first time last night and I am very impressed! Things have gone incredibly smoothly and it is a wonderful introduction to the Debian way of doing things (I've been using RedHat/Fedora for the past 5 yrs).

Anyhow, I'm having problems getting my dual-core processor recognized by the kernel. From other posts, I did find the name of the smp kernel and it is installed. 'uname -a' outputs the following:

[I][FONT="Courier New"]
Linux dmandel-desktop 2.6.15-26-amd64-k8 #1 SMP PREEMPT Thu Aug 3 03:11:38 UTC 2006 x86_64 GNU/Linux[/FONT][/I]

But 'cat /proc/cpuinfo' outputs this:


[FONT="Courier New"][I]processor : 0
vendor_id : AuthenticAMD
cpu family : 15
model : 43
model name : AMD Athlon(tm) 64 X2 Dual Core Processor 4200+
stepping : 1
cpu MHz : 2204.621
cache size : 512 KB
physical id : 0
siblings : 1
core id : 0
cpu cores : 1
fpu : yes
fpu_exception : yes
cpuid level : 1
wp : yes
flags : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt lm 3dnowext 3dnow pni lahf_lm cmp_legacy
bogomips : 4416.11
TLB size : 1024 4K pages
clflush size : 64
cache_alignment : 64
address sizes : 40 bits physical, 48 bits virtual
power management: ts fid vid ttp[/I][/FONT]


I'm willing to dig deeper and try other avenues, but I'm not sure where to begin looking. Any suggestions would be greatly appreciated.

Sincerely,
Danny Mandel

---

### Post by Blaineoliver on 2006-08-24
you need the correct kernal to see your two physical cores, look through this forum, as their was a helpful topic on the right kernals for the right processor.:cool:

---

### Post by Ausus on 2006-08-24
Hi danny_mandel,

I'm able to see dual-cores with default generic kernel loaded.
My mobo is a ASUS A8N32-Sli Deluxe.

Rgards

---

### Post by mrfreddy on 2006-08-24
I've got the same CPU in an MSI K9NGM2-FI with ubuntu-server 6.06.1. Here's more info than you possibly wanted :D 
uname -a gives:
```
Linux banana@rama.com 2.6.15-26-amd64-server #1 SMP Thu Aug 3 03:32:26 UTC 2006 x86_64 GNU/Linux
```

cat /proc/cpuinfo gives:
```
processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 75
model name      : AMD Athlon(tm) 64 X2 Dual Core Processor 3800+
stepping        : 2
cpu MHz         : 2009.166
cache size      : 512 KB
physical id     : 0
siblings        : 2
core id         : 0
cpu cores       : 2
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov 
pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt lm 3dnowext 3d
now pni cx16 lahf_lm cmp_legacy
bogomips        : 4024.27
TLB size        : 1024 4K pages
clflush size    : 64
cache_alignment : 64
address sizes   : 40 bits physical, 48 bits virtual
power management: ts fid vid ttp tm stc

processor       : 1
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 75
model name      : AMD Athlon(tm) 64 X2 Dual Core Processor 3800+
stepping        : 2
cpu MHz         : 2009.166
cache size      : 512 KB
physical id     : 0
siblings        : 2
core id         : 1
cpu cores       : 2
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov 
pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt lm 3dnowext 3d
now pni cx16 lahf_lm cmp_legacy
bogomips        : 4018.57
TLB size        : 1024 4K pages
clflush size    : 64
cache_alignment : 64
address sizes   : 40 bits physical, 48 bits virtual
power management: ts fid vid ttp tm stc

```
And dpkg -l | grep kernel gives:
```
dpkg -l | grep kernel
ii  iptables                             1.3.3-2ubuntu4               Linux kernel 2.4+ iptables administration to
ii  linux-amd64-server                   2.6.15.24                    Complete Linux kernel on Server Equipment.
ii  linux-headers-2.6.15-26              2.6.15-26.46                 Header files related to Linux kernel version
ii  linux-headers-2.6.15-26-amd64-server 2.6.15-26.46                 Linux kernel headers 2.6.15 on Server Equipm
ii  linux-image-2.6.15-26-amd64-server   2.6.15-26.46                 Linux kernel image for version 2.6.15 on Ser
ii  linux-image-amd64-server             2.6.15.24                    Linux kernel image on Server Equipment.
ii  module-init-tools                    3.2.2-1ubuntu7               tools for managing Linux kernel modules
ii  udev                                 079-0ubuntu34                rule-based device node and kernel event mana
```

---

### Post by danny_mandel on 2006-08-24
Ok, total weirdness.  I rebooted and now it claims to recognize both cores.  This happened after I installed the server kernel, which didn't seem to fix anything.  Curiously, the mhz of each individual core has been cut in half.  Maybe that's normal, though.  Here's what /proc/cpuinfo says now:

[FONT="Courier New"][I]
processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 43
model name      : AMD Athlon(tm) 64 X2 Dual Core Processor 4200+
stepping        : 1
cpu MHz         : 1002.117
cache size      : 512 KB
physical id     : 0
siblings        : 2
core id         : 0
cpu cores       : 2
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt lm 3dnowext 3d now pni lahf_lm cmp_legacy
bogomips        : 2007.43
TLB size        : 1024 4K pages
clflush size    : 64
cache_alignment : 64
address sizes   : 40 bits physical, 48 bits virtual
power management: ts fid vid ttp

processor       : 1
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 43
model name      : AMD Athlon(tm) 64 X2 Dual Core Processor 4200+
stepping        : 1
cpu MHz         : 1002.117
cache size      : 512 KB
physical id     : 0
siblings        : 2
core id         : 1
cpu cores       : 2
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt lm 3dnowext 3d now pni lahf_lm cmp_legacy
bogomips        : 2007.43
TLB size        : 1024 4K pages
clflush size    : 64
cache_alignment : 64
address sizes   : 40 bits physical, 48 bits virtual
power management: ts fid vid ttp

dmandel@dmandel-desktop:~$ uname -a
Linux dmandel-desktop 2.6.15-26-amd64-k8 #1 SMP PREEMPT Thu Aug 3 03:11:38 UTC 2 006 x86_64 GNU/Linux
[/I][/FONT]

Maybe there's something funky going on with my hardware.  Anyhow, thanks for your help and suggestions!

Danny

---

### Post by kuja on 2006-08-24
No, that's certainly not normal! 
Mine sees the full 2808Mhz on both cores, no cutting in half business. 
Are you getting the halved speed out of it as well? 
I do believe the correct kernel, unless you're running on odd server hardware, is probably the amd64-k8 kernel, though the amd64-generic would probably work as well.
I'm not really sure what's going on for you.

---

### Post by kozimodo on 2006-08-24
> **danny_mandel said:**
> Curiously, the mhz of each individual core has been cut in half.  

That's your CPU frequency scaling at work.  Put the frequency scaling applet on your panel and you'll see that when you start demanding more from the processor, your clock speed will go up.

---

### Post by danny_mandel on 2006-08-24
> **kozimodo said:**
> That's your CPU frequency scaling at work.  Put the frequency scaling applet on your panel and you'll see that when you start demanding more from the processor, your clock speed will go up.

Ahhhhh.  Ok.  That was definitely it!  I didn't even know this existed.  Interestingly enough this fixed another problem I was having where my monitor would flicker when the CPUs switched performances mode.  Yay!  No more warts in my system!

Thanks so much!

---

### Post by Ausus on 2006-08-26
Hi danny_mandel,

When I checked my system at present, it also shows half the frequencies what they should be running.
Should be at 2000Mhz know only 1000Mhz.
This could be Cool and Quite technology from AMD.
Mine is enabled in bios.
I have seen it when I run XP64.

Regards
:-({|=

---

### Post by wr1 on 2006-11-30
Dear Ubuntu people, 

Following this thread, it seems to me that the same problem seems to exist for 2.6.17.10

dpkg -l | grep kernel
cat /proc/cpuinfo 
uname -a

gives:

> ii  iptables                                   1.3.5.0debian1-1ubuntu2              Linux kernel 2.4+ iptables administration to
ii  libdrm2                                    2.0.2+git20060809-0ubuntu1           Userspace interface to kernel DRM services -
ii  linux-generic                              2.6.17.10                            Complete Generic Linux kernel
ii  linux-headers-2.6.17-10                    2.6.17-10.33                         Header files related to Linux kernel version
ii  linux-headers-2.6.17-10-generic            2.6.17-10.33                         Linux kernel headers for version 2.6.17 on x
ii  linux-headers-generic                      2.6.17.10                            Generic Linux kernel headers
ii  linux-image-2.6.17-10-generic              2.6.17-10.33                         Linux kernel image for version 2.6.17 on x86
ii  linux-image-2.6.17-10-server               2.6.17-10.33                         Linux kernel image for version 2.6.17 on x86
ii  linux-image-generic                        2.6.17.10                            Generic Linux kernel image
ii  linux-image-server                         2.6.17.10                            Linux kernel image on Server Equipment.
ii  linux-restricted-modules-generic           2.6.17.10                            Restricted Linux modules for generic kernels
ii  linux-server                               2.6.17.10                            Complete Linux kernel on Server Equipment.
ii  module-init-tools                          3.2.2-3ubuntu3                       tools for managing Linux kernel modules
ii  nvidia-kernel-common                       20051028+1ubuntu7                    NVIDIA binary kernel module common files
ii  udev                                       093-0ubuntu18                        rule-based device node and kernel event mana
> processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 75
model name      : AMD Athlon(tm) 64 X2 Dual Core Processor 4200+
stepping        : 2
cpu MHz         : 1000.000
cache size      : 512 KB
physical id     : 0
siblings        : 1
core id         : 0
cpu cores       : 1
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt lm 3dnowext 3dnow pni cx16 lahf_lm cmp_legacy svm cr8legacy ts fid vid ttp tm stc
bogomips        : 2006.57

> Linux wm1 2.6.17-10-server #2 SMP Fri Oct 13 18:47:26 UTC 2006 i686 GNU/Linux

So all is well except recognizing the second core. This happens regardless of whether I use the server or the generic kernel. 

Greetings
W

---

### Post by nijltjetweety on 2006-11-30
> **Blaineoliver said:**
> you need the correct kernal to see your two physical cores, look through this forum, as their was a helpful topic on the right kernals for the right processor.:cool:

I have an athlon x2 3800+ with an ASUS M2NPV-VM motherboard.
2 weeks ago i downloaded the latest ubuntu release but the installation faild.what ubuntu release have you?

---

### Post by wr1 on 2006-11-30
I am using the 6.10 release, the 64 bit CD failed on me too but the i386 CD worked. Reinstalling the kernel using the repo does not improve the situation though, I must be missing a setting somewhere. 

Cheers
W

---

