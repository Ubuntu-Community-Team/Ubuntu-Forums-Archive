---
title: "wine and plants vs. zombies"
date: 2012-10-01
forum: Wine
---

### Post by chroniclesofdave on 2012-10-01
hey, im new to ubuntu and i love it so far, but im having an issue. i want to port my plants vs. zombies game to ubuntu but wine wont open it. i keep relieving this error message:


Exception: Access Violation (code 0xc0000005) at address 7DDCB39B in thread 32
Module: wined3d.dll
Logical Address: 0001:000CA39B

0033F368 7DDCB39B wined3d_swapchain_get_desc+5B [(Unknown File Name)(0)+0x00000000]
Params: 00000000 0033F4A0 0033F4DC 00000000

0033F508 7DE39AE7 0001:00008AE7 ddraw.dll
Params: 0033F54C 00000000 00000007 7BCC2568

0033F568 7DE3A112 0001:00009112 ddraw.dll
Params: 00139890 0033F6C8 0033F598 00000000

0033F6C8 00561473 0001:00160473 popcapgame1.exe
Params: 00000000 00000000 00000000 00000001


EAX:FFFFFFFF EBX:7DE1AFF4 ECX:00139890 EDX:00000003 ESI:0033F4A0 EDI:00000000
EIP:7DDCB39B ESP:0033F330  EBP:0033F368
CS:0023 SS:002B DS:002B ES:002B FS:0063 GS:006B
Flags:00010286

Windows Ver: NT 5.1 Service Pack 3 Build 2600
DDraw Ver: 5.3.1.904
DSound Ver: 5.3.1.904

Product: PlantsVsZombies
Version: 1.0.0.1051
Time Loaded: 00:00:00
Fullscreen: Yes
Primary ThreadId: 32
Times Played: 0
Build Num: 0
Build Date: 



and this one as well:



couldn't load main module (32)
Unhandled exception: page fault on read access to 0x0000001c in 32-bit code (0x7ddcb39b).
Register dump:
 CS:0023 SS:002b DS:002b ES:002b FS:0063 GS:006b
 EIP:7ddcb39b ESP:0033f330 EBP:0033f368 EFLAGS:00010286(  R- --  I S - -P- )
 EAX:ffffffff EBX:7de1aff4 ECX:00139890 EDX:00000003
 ESI:0033f4a0 EDI:00000000
Stack dump:
0x0033f330:  00000003 7de1e874 7de07081 7de06d87
0x0033f340:  00000000 0033f4a0 00000000 00000073
0x0033f350:  00000000 00000000 00000320 7de84ff4
0x0033f360:  0033f6c8 80070057 0033f508 7de39aec
0x0033f370:  00000000 0033f4a0 0033f4dc 00000000
0x0033f380:  0033f3e0 f75c6ff4 0033f400 f749867e
000c: sel=0067 base=00000000 limit=00000000 16-bit --x
Backtrace:
=>0 0x7ddcb39b wined3d_swapchain_get_desc+0x5b() in wined3d (0x0033f368)
  1 0x7de39aec in ddraw (+0x9aeb) (0x0033f508)
  2 0x7de3a117 in ddraw (+0xa116) (0x0033f568)
  3 0x00561478 (0x0033f6c8)
0x7ddcb39b wined3d_swapchain_get_desc+0x5b in wined3d: movl    0x1c(%edi),%eax
Modules:
Module    Address            Debug info    Name (87 modules)
ELF    7b800000-7ba15000    Deferred        kernel32<elf>
  \-PE    7b810000-7ba15000    \               kernel32
ELF    7bc00000-7bcc3000    Deferred        ntdll<elf>
  \-PE    7bc10000-7bcc3000    \               ntdll
ELF    7bf00000-7bf04000    Deferred        <wine-loader>
ELF    7da40000-7dacd000    Deferred        msvcrt<elf>
  \-PE    7da50000-7dacd000    \               msvcrt
ELF    7dc40000-7dc78000    Deferred        usp10<elf>
  \-PE    7dc50000-7dc78000    \               usp10
ELF    7dc8c000-7dc90000    Deferred        libnvidia-tls.so.295.40
ELF    7dca9000-7dcec000    Deferred        dsound<elf>
  \-PE    7dcb0000-7dcec000    \               dsound
ELF    7dcec000-7de20000    Dwarf           wined3d<elf>
  \-PE    7dd00000-7de20000    \               wined3d
ELF    7de20000-7de88000    Dwarf           ddraw<elf>
  \-PE    7de30000-7de88000    \               ddraw
ELF    7dea0000-7ded4000    Deferred        uxtheme<elf>
  \-PE    7deb0000-7ded4000    \               uxtheme
ELF    7ded4000-7deda000    Deferred        libxfixes.so.3
ELF    7deda000-7dee5000    Deferred        libxcursor.so.1
ELF    7df61000-7df8b000    Deferred        libexpat.so.1
ELF    7df8b000-7dfbf000    Deferred        libfontconfig.so.1
ELF    7dfbf000-7dfcf000    Deferred        libxi.so.6
ELF    7dfcf000-7dfd3000    Deferred        libxcomposite.so.1
ELF    7dfd3000-7dfdc000    Deferred        libxrandr.so.2
ELF    7dfdc000-7dfe6000    Deferred        libxrender.so.1
ELF    7dfe6000-7dfec000    Deferred        libxxf86vm.so.1
ELF    7dfec000-7e00e000    Deferred        imm32<elf>
  \-PE    7dff0000-7e00e000    \               imm32
ELF    7e00e000-7e015000    Deferred        libxdmcp.so.6
ELF    7e015000-7e036000    Deferred        libxcb.so.1
ELF    7e036000-7e0c9000    Deferred        winex11<elf>
  \-PE    7e040000-7e0c9000    \               winex11
ELF    7e127000-7e12b000    Deferred        libxinerama.so.1
ELF    7e12b000-7e12f000    Deferred        libxau.so.6
ELF    7e12f000-7e135000    Deferred        libuuid.so.1
ELF    7e135000-7e14f000    Deferred        libice.so.6
ELF    7e14f000-7e283000    Deferred        libx11.so.6
ELF    7e283000-7e295000    Deferred        libxext.so.6
ELF    7e295000-7e29e000    Deferred        libsm.so.6
ELF    7e29e000-7e338000    Deferred        libfreetype.so.6
ELF    7e338000-7e42a000    Deferred        oleaut32<elf>
  \-PE    7e350000-7e42a000    \               oleaut32
ELF    7e42a000-7e44c000    Deferred        iphlpapi<elf>
  \-PE    7e430000-7e44c000    \               iphlpapi
ELF    7e44c000-7e47e000    Deferred        ws2_32<elf>
  \-PE    7e450000-7e47e000    \               ws2_32
ELF    7e47e000-7e499000    Deferred        wsock32<elf>
  \-PE    7e480000-7e499000    \               wsock32
ELF    7e499000-7e4c1000    Deferred        msacm32<elf>
  \-PE    7e4a0000-7e4c1000    \               msacm32
ELF    7e4c1000-7e536000    Deferred        rpcrt4<elf>
  \-PE    7e4d0000-7e536000    \               rpcrt4
ELF    7e536000-7e63e000    Deferred        ole32<elf>
  \-PE    7e550000-7e63e000    \               ole32
ELF    7e63e000-7e6eb000    Deferred        winmm<elf>
  \-PE    7e650000-7e6eb000    \               winmm
ELF    7e6eb000-7e7e3000    Deferred        comctl32<elf>
  \-PE    7e6f0000-7e7e3000    \               comctl32
ELF    7e7e3000-7e9f4000    Deferred        shell32<elf>
  \-PE    7e7f0000-7e9f4000    \               shell32
ELF    7e9f4000-7ea5e000    Deferred        shlwapi<elf>
  \-PE    7ea00000-7ea5e000    \               shlwapi
ELF    7ea5e000-7ea84000    Deferred        mpr<elf>
  \-PE    7ea60000-7ea84000    \               mpr
ELF    7ea84000-7ea9a000    Deferred        libz.so.1
ELF    7eab3000-7eb22000    Deferred        wininet<elf>
  \-PE    7eac0000-7eb22000    \               wininet
ELF    7eb22000-7eb82000    Deferred        advapi32<elf>
  \-PE    7eb30000-7eb82000    \               advapi32
ELF    7eb82000-7ec3f000    Deferred        gdi32<elf>
  \-PE    7eb90000-7ec3f000    \               gdi32
ELF    7ec3f000-7ed7f000    Deferred        user32<elf>
  \-PE    7ec50000-7ed7f000    \               user32
ELF    7ed7f000-7ed8c000    Deferred        libnss_files.so.2
ELF    7ed8c000-7ed98000    Deferred        libnss_nis.so.2
ELF    7ed98000-7edb2000    Deferred        libnsl.so.1
ELF    7edb2000-7edbb000    Deferred        libnss_compat.so.2
ELF    7efbb000-7efe7000    Deferred        libm.so.6
ELF    7efe7000-7f000000    Deferred        version<elf>
  \-PE    7eff0000-7f000000    \               version
ELF    f7421000-f7426000    Deferred        libdl.so.2
ELF    f7426000-f75cb000    Deferred        libc.so.6
ELF    f75cc000-f75e7000    Deferred        libpthread.so.0
ELF    f7600000-f7742000    Dwarf           libwine.so.1
ELF    f7744000-f7766000    Deferred        ld-linux.so.2
ELF    f7766000-f7767000    Deferred        [vdso].so
Threads:
process  tid      prio (all id:s are in hex)
0000000e services.exe
    0000001f    0
    0000001e    0
    00000015    0
    00000010    0
    0000000f    0
00000012 winedevice.exe
    0000001c    0
    00000018    0
    00000014    0
    00000013    0
0000001a plugplay.exe
    00000020    0
    0000001d    0
    0000001b    0
0000002d PlantsVsZombies.exe
    00000033    0
    0000002e   -1
0000002f explorer.exe
    00000030    0
00000031 (D) Z:\media\OSDisk\Users\Dave\Desktop\games\[[www.tnttorrent.info]](www.tnttorrent.info]) Plants vs Zombies Game Of The Year Edition [ENG] [miguel] [Ekipa TnT]\Plants vs Zombies Game Of The Year Edition\popcapgame1.exe
    00000032    0 <==
System information:
    Wine build: wine-1.4
    Platform: i386 (WOW64)
    Host system: Linux
    Host version: 3.2.0-32-generic



any and all help would be great

---

### Post by doorknob60 on 2012-10-01
I can confirm that that game should be able to work, since it works for me. What graphics card do you have, and what drivers are you using?

---

### Post by oldos2er on 2012-10-03
Moved to Wine.

---

### Post by chroniclesofdave on 2012-10-06
the only info i could come up with for my nvidia geforce card was this using hwinfo in my terminal:
    Driver Status: nouveau is not active
    Driver Activation Cmd: "modprobe nouveau"
  Driver Info #2:
    Driver Status: nvidia_current is not active
    Driver Activation Cmd: "modprobe nvidia_current"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #14 (PCI bridge)

---

### Post by thatguruguy on 2012-10-06
> **chroniclesofdave said:**
> the only info i could come up with for my nvidia geforce card was this using hwinfo in my terminal:
    Driver Status: nouveau is not active
    Driver Activation Cmd: "modprobe nouveau"
  Driver Info #2:
    Driver Status: nvidia_current is not active
    Driver Activation Cmd: "modprobe nvidia_current"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #14 (PCI bridge)

The first step is figuring out what graphics card do you have. You may want to type the following into a terminal:

```
lspci | grep VGA
```and post the result here. Also, is your computer a laptop or a desktop?

EDIT: Go ahead and type the following in a terminal as well, and post the results here:
```
cat /proc/cpuinfo
```

---

### Post by chroniclesofdave on 2012-10-07
it is a laptop. a dell xps l502x to be exact. in regards to the lspci, this is what i got

00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 05)
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b5)
00:1c.1 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 2 (rev b5)
00:1c.3 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 4 (rev b5)
00:1c.4 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 5 (rev b5)
00:1c.5 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 6 (rev b5)
00:1d.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation HM67 Express Chipset Family LPC Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 05)
01:00.0 VGA compatible controller: NVIDIA Corporation GF108 [GeForce GT 540M] (rev a1)
03:00.0 Network controller: Intel Corporation Centrino Wireless-N 1030 (rev 34)
04:00.0 USB controller: NEC Corporation uPD720200 USB 3.0 Host Controller (rev 04)
06:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)

and the cat /proc/cpuinfo

processor    : 0
vendor_id    : GenuineIntel
cpu family    : 6
model        : 42
model name    : Intel(R) Core(TM) i7-2620M CPU @ 2.70GHz
stepping    : 7
microcode    : 0x15
cpu MHz        : 800.000
cache size    : 4096 KB
physical id    : 0
siblings    : 4
core id        : 0
cpu cores    : 2
apicid        : 0
initial apicid    : 0
fpu        : yes
fpu_exception    : yes
cpuid level    : 13
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp lm constant_tsc arch_perfmon pebs bts nopl xtopology nonstop_tsc aperfmperf pni pclmulqdq dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic popcnt tsc_deadline_timer aes xsave avx lahf_lm ida arat epb xsaveopt pln pts dtherm tpr_shadow vnmi flexpriority ept vpid
bogomips    : 5387.38
clflush size    : 64
cache_alignment    : 64
address sizes    : 36 bits physical, 48 bits virtual
power management:

processor    : 1
vendor_id    : GenuineIntel
cpu family    : 6
model        : 42
model name    : Intel(R) Core(TM) i7-2620M CPU @ 2.70GHz
stepping    : 7
microcode    : 0x15
cpu MHz        : 800.000
cache size    : 4096 KB
physical id    : 0
siblings    : 4
core id        : 0
cpu cores    : 2
apicid        : 1
initial apicid    : 1
fpu        : yes
fpu_exception    : yes
cpuid level    : 13
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp lm constant_tsc arch_perfmon pebs bts nopl xtopology nonstop_tsc aperfmperf pni pclmulqdq dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic popcnt tsc_deadline_timer aes xsave avx lahf_lm ida arat epb xsaveopt pln pts dtherm tpr_shadow vnmi flexpriority ept vpid
bogomips    : 5387.71
clflush size    : 64
cache_alignment    : 64
address sizes    : 36 bits physical, 48 bits virtual
power management:

processor    : 2
vendor_id    : GenuineIntel
cpu family    : 6
model        : 42
model name    : Intel(R) Core(TM) i7-2620M CPU @ 2.70GHz
stepping    : 7
microcode    : 0x15
cpu MHz        : 800.000
cache size    : 4096 KB
physical id    : 0
siblings    : 4
core id        : 1
cpu cores    : 2
apicid        : 2
initial apicid    : 2
fpu        : yes
fpu_exception    : yes
cpuid level    : 13
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp lm constant_tsc arch_perfmon pebs bts nopl xtopology nonstop_tsc aperfmperf pni pclmulqdq dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic popcnt tsc_deadline_timer aes xsave avx lahf_lm ida arat epb xsaveopt pln pts dtherm tpr_shadow vnmi flexpriority ept vpid
bogomips    : 5387.73
clflush size    : 64
cache_alignment    : 64
address sizes    : 36 bits physical, 48 bits virtual
power management:

processor    : 3
vendor_id    : GenuineIntel
cpu family    : 6
model        : 42
model name    : Intel(R) Core(TM) i7-2620M CPU @ 2.70GHz
stepping    : 7
microcode    : 0x15
cpu MHz        : 800.000
cache size    : 4096 KB
physical id    : 0
siblings    : 4
core id        : 1
cpu cores    : 2
apicid        : 3
initial apicid    : 3
fpu        : yes
fpu_exception    : yes
cpuid level    : 13
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp lm constant_tsc arch_perfmon pebs bts nopl xtopology nonstop_tsc aperfmperf pni pclmulqdq dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic popcnt tsc_deadline_timer aes xsave avx lahf_lm ida arat epb xsaveopt pln pts dtherm tpr_shadow vnmi flexpriority ept vpid
bogomips    : 5387.73
clflush size    : 64
cache_alignment    : 64
address sizes    : 36 bits physical, 48 bits virtual
power management:

---

### Post by chroniclesofdave on 2012-10-07
and by the way, i must thank all of you. your quick responses instill in me a great feeling of team spirit in the name of open source. i used ubuntu and gentoo a long time ago, and then fell back into windows, subsequently forgetting most all of my computer knowledge. thank you all for your speedy responses and detailed assistance.

---

