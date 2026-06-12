---
title: "Can't boot up after install"
date: 2009-06-11
forum: x86 64-bit Users
---

### Post by jeffmcd on 2009-06-11
Hello, guys.
I used to have Fedora and Vista installed on dual boot mode in my HP Pavilion dv4 laptop (AMD Turion X2 64 / Ati Radeon / Broadcom wireless), everything working perfectly. Then I decided to switch to Ubuntu Studio, to try its applications and the RT feature.
I've downloaded the AMD 64 alternate DVD and installed over the ext3 partition, everything seemed to be ok, but when I try to load it from GRUB it doesn't boot up. I've tried to reinstall it several times, and just get the same error. Here is a part of the code that appears before it freezes (I had to write down on a paper because I didn't know how to copy it or access it from a log, if there is any). Some random numbers I'm just representing by "..."

[COLOR=Blue]Call Trace:

[...] tick_handle_periodic+0x21/0x90
[...] hpet_interrupt_handler+0x../...
[...] handle_IRQ_event+...
[...] thread_edge_irq+...
[...] do_irqd+...
[...] ? do_irdq
[...] kthread
[...] child_rip
[...] ? kthread
[...] ? child_rip

Code: 2e 0f 1f[/COLOR][COLOR=Blue] ... ... ... ... ...[/COLOR][COLOR=Blue] ... ... ... ... ...[/COLOR][COLOR=Blue] ... ... ... ... ...[/COLOR]
[COLOR=Blue] ... ... ... ... ...[/COLOR][COLOR=Blue] ... ... ... ... ... [/COLOR][COLOR=Blue]... ... ... ... 1f 40

RIP [<ffffffff80278722>] tick_periodic+0x22/0x80
 RSP <ffff88013ec8fe00>
CR2: 0000000000000000
---[ end trace 4eaa2a86a8e2da22 ]---[/COLOR]

And the screen keeps frozen after this last line :( I don't know what to do, do you guys have any idea, has this problem already occured to you? Thank you.

---

### Post by balloooza on 2009-06-11
can you boot into grub, then chose (recovery mode)
> Some random numbers
random numbers = the time from boot-up the event happened (1.14156 = 1.14156 seconds after start)

---

### Post by balloooza on 2009-06-11
Also jeffmcd, Ubuntu studio dose not work well with 64 bit, the rt kernel is horrible, and the applications crash, I know because I just bought an amd processor, and was excited to try the 64 bit, and it had bad results,  do you have the ability to download a 32 bit cd, possible causes of this failure may include a bad download of the .iso, or a bad burn, the 32 bit one has much more success, and if fedora is your favorite system, there is a project for fedora that includes RT kernel and audio apps, it is called Planet CCRMA (car-ma)
[http://ccrma.stanford.edu/planetccrma/software/installplaneteight.html](http://ccrma.stanford.edu/planetccrma/software/installplaneteight.html)
Fedora 8 is the only one that realy works, so you have to find a place to get the fedora 8 disk, 11 will also work, once PLANET CCRMA finishes it.

---

### Post by jeffmcd on 2009-06-12
Thank you for the answer, balloooza!

Unfortunately, the recovery mode also doesn't work, it gives the same screen.

are you saying that rt kernel is not stable? that's really bad to hear :( if that's the case, I'll give up and keep with normal kernel

anyway, do you think installing the normal ubuntu, and then the rt kernel might work?

I don't have a favorite distribution, I was just excited about the RT for audio applications. I'm thinking about trying 64 Studio, and Planet CCRMA. Thank you for that tip ;)

---

### Post by lnappa on 2009-07-31
Hi,

I have the same problem with a HP Pavilion dv6-1105 laptop (AMD Athlon X2 64, ATI Radeon). I have tried both Studio 9.04 64 and 32 bit installs, and both hang on what I believe is a kernel panic showing a stack trace ending with tick_periodic. 32-bit Call trace here;

[     0.796908] Call Trace:
[     0.796908]  [<c015d1b9>] ? tick_handle_periodic+0x19/0x80
[     0.796908]  [<c0130850>] ? finish_task_switch+0x50/0x120
[     0.796908]  [<c01213f1>] ? hpet_interrupt_handler+0x11/0x30
[     0.796908]  [<c018255c>] ? handle_IRQ_event+0x5c/0x120
[     0.796908]  [<c0182f93>] ? thread_edge_irq+0x63/0xd0
[     0.796908]  [<c01831e2>] ? do_irqd+0xc2/0x160
[     0.796908]  [<c0183120>] ? do_irqd+0x0/0x160
[     0.796908]  [<c015164c>] ? kthread+0x3c/0x70
 [     0.796908]  [<c0151610>] ? kthread+0x0/0x70
 [     0.796908]  [<c0105547>] ? kernel_thread_helper+0x7/0x10
[     0.796908] Code: e8 f5 fc ff ff 85 c0 75 d9 83 c4 08 5b 5e 5f 5d c3 89 f6 8d bc 27 00 00 00 00 39 05 68 16 79 c0 55 89 e5 74 1d 64 a1 08 20 81 c0 <8b> 40 30 83 e0 03 83 f8 03 0f 94 c0 0f b6 c0 e8 4b 92 fe ff 5d
[     0.796908] EIP [<c015d141>] tick_periodic+0x11/0x70 SS:ESP 0068:f67b7f28
[     0.796908] ---[ end trace 4eaa2a86a82da22 ]---

  	 	 	 	 	 	  I have got the 64-bit version up and working on a Asrock ION 330 NetTop (Intel Atom 330 Dual-Core CPU and NVIDIA ION graphics processor) comming up with four (4)! CPUs. Studio sound works really well on this computer and I now wanted to introduce it to my daughter why I need the HP laptop working.


What can I do?

---

### Post by luvr on 2009-07-31
> **jeffmcd said:**
> anyway, do you think installing the normal ubuntu, and then the rt kernel might work?

No, it won't work. The RT kernel just won't boot on my AMD Athlon 64 X2 either.

I have already tried the 32-bit, as well as the 64-bit edition of UbuntuStudio 9.04, and they both run into the *Call Trace* that you took the time to manually reproduce.

Not sure if it could help any, but here's the output from the **cpuid** command on my system:

```
 eax in    eax      ebx      ecx      edx
00000000 00000001 68747541 444d4163 69746e65
00000001 00040f33 00020800 00002001 178bfbff
80000000 80000018 68747541 444d4163 69746e65
80000001 00040f33 000009a3 0000001f ebd3fbff
80000002 20444d41 6c687441 74286e6f 3620296d
80000003 32582034 61754420 6f43206c 50206572
80000004 65636f72 726f7373 30303620 00002b30
80000005 ff08ff08 ff20ff20 40020140 40020140
80000006 00000000 42004200 04008140 00000000
80000007 00000000 00000000 00000000 0000003f
80000008 00003028 00000000 00000001 00000000
80000009 00000000 00000000 00000000 00000000
8000000a 00000001 00000040 00000000 00000000
8000000b 00000000 00000000 00000000 00000000
8000000c 00000000 00000000 00000000 00000000
8000000d 00000000 00000000 00000000 00000000
8000000e 00000000 00000000 00000000 00000000
8000000f 00000000 00000000 00000000 00000000
80000010 00000000 00000000 00000000 00000000
80000011 00000000 00000000 00000000 00000000
80000012 00000000 00000000 00000000 00000000
80000013 00000000 00000000 00000000 00000000
80000014 00000000 00000000 00000000 00000000
80000015 00000000 00000000 00000000 00000000
80000016 00000000 00000000 00000000 00000000
80000017 00000000 00000000 00000000 00000000
80000018 00000000 00000000 00000000 00000000

Vendor ID: "AuthenticAMD"; CPUID level 1

AMD-specific functions
Version 00040f33:
Family: 15 Model: 3 []

Standard feature flags 178bfbff:
Floating Point Unit
Virtual Mode Extensions
Debugging Extensions
Page Size Extensions
Time Stamp Counter (with RDTSC and CR4 disable bit)
Model Specific Registers with RDMSR & WRMSR
PAE - Page Address Extensions
Machine Check Exception
COMPXCHG8B Instruction
APIC
SYSCALL/SYSRET or SYSENTER/SYSEXIT instructions
MTRR - Memory Type Range Registers
Global paging extension
Machine Check Architecture
Conditional Move Instruction
PAT - Page Attribute Table
PSE-36 - Page Size Extensions
19 - reserved
MMX instructions
FXSAVE/FXRSTOR
25 - reserved
26 - reserved
28 - reserved
Generation: 15 Model: 3
Extended feature flags ebd3fbff:
Floating Point Unit
Virtual Mode Extensions
Debugging Extensions
Page Size Extensions
Time Stamp Counter (with RDTSC and CR4 disable bit)
Model Specific Registers with RDMSR & WRMSR
PAE - Page Address Extensions
Machine Check Exception
COMPXCHG8B Instruction
APIC
SYSCALL/SYSRET or SYSENTER/SYSEXIT instructions
MTRR - Memory Type Range Registers
Global paging extension
Machine Check Architecture
Conditional Move Instruction
PAT - Page Attribute Table
PSE-36 - Page Size Extensions
20 - reserved
AMD MMX Instruction Extensions
MMX instructions
FXSAVE/FXRSTOR
25 - reserved
27 - reserved
29 - reserved
3DNow! Instruction Extensions
3DNow instructions

Processor name string: AMD Athlon(tm) 64 X2 Dual Core Processor 6000+
L1 Cache Information:
2/4-MB Pages:
   Data TLB: associativity 255-way #entries 8
   Instruction TLB: associativity 255-way #entries 8
4-KB Pages:
   Data TLB: associativity 255-way #entries 32
   Instruction TLB: associativity 255-way #entries 32
L1 Data cache:
   size 64 KB associativity 2-way lines per tag 1 line size 64
L1 Instruction cache:
   size 64 KB associativity 2-way lines per tag 1 line size 64

L2 Cache Information:
2/4-MB Pages:
   Data TLB: associativity L2 off #entries 0
   Instruction TLB: associativity L2 off #entries 0
4-KB Pages:
   Data TLB: associativity 2-way #entries 0
   Instruction TLB: associativity 2-way #entries 0
   size 4 KB associativity L2 off lines per tag 129 line size 64

Advanced Power Management Feature Flags
Has temperature sensing diode
Supports Frequency ID control
Supports Voltage ID control
Maximum linear address: 48; maximum phys address 40
```

At first glance, this problem has not yet been reported as a bug in Launchpad--even though there are quite a few other bugs about the RT kernel on AMD64.

---

### Post by luvr on 2009-08-01
I created a bug report on this problem in Launchpad: [Bug #407660 in linux-rt (Ubuntu): “Real-Time Kernel won't boot on my AMD Athlon 64 X2 Dual Core - Displays Call Trace”]("https://bugs.launchpad.net/ubuntu/+source/linux-rt/+bug/407660")

---

### Post by ram130 on 2009-08-02
I have wasted one extra cd trying figure out why this is happening. I never had the problem with 8.04 so this is strange. I too have AMD Athlon X2 and have tried both 32bit and 64bit installs. Wasted a whole day on this, burning extra cds and installing over and over. Has any solution been found yet?

---

### Post by Csharp on 2009-08-18
Same 

AMD X2 7750 CPU   crash on 32 or 64 install. 

You can press C for command line at grub prompt then add this.

acpi=no   pnpbios=no

Or do the whole thing.

root (hd*,*)
kernel  /boot/vmlinuz-2.6.29----rt root=/dev/sda*  acpi=no pnpbios=no
initrd  /boot/initrd-2.6.29*****rt 

boot

That should get you up.   I found it sucked though as the system won't shutdown properly etc.  

Added Suse 2.6.29rt kernel  to opensuse 11.1 and boots fine.   Still no jackd yet though.

---

### Post by ram130 on 2009-08-19
Doesnt work...gonna try sum other tings..anyone else got tru?

---

### Post by ram130 on 2009-08-26
has it work for anyone else?:confused:

---

