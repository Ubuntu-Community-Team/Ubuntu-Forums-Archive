---
title: "to 64bit or not to 64bit"
date: 2006-02-09
forum: x86 64-bit Users (Pre April '08)
---

### Post by gary79 on 2006-02-09
I've searched around on this forum but have not been able to turn up an answer.

My girlfriend has a new ASUS A4B00K notebook and it is just not clear if it is a sempron 64bit or 32bit.

lshw returns
```
*-cpu
          description: CPU
          product: Mobile AMD Sempron(tm) Processor 3000+
          vendor: Advanced Micro Devices [AMD]
          physical id: 4
          bus info: cpu@0
          version: 15.12.0
          serial: To Be Filled By O.E.M.
          slot: Socket-754
          size: 1800MHz
          capacity: 1800MHz
          width: 32 bits
          clock: 200MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext fxsr_opt 3dnowext 3dnow lahf_lm

```


and /proc/cpuinfo returns

```
processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 28
model name      : Mobile AMD Sempron(tm) Processor 3000+
stepping        : 0
cpu MHz         : 797.982
cache size      : 128 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext fxsr_opt 3dnowext 3dnow lahf_lm
bogomips        : 1580.14

```

checking aganist this handy cpu id [tool]("http://www.amdcompare.com/us-en/desktop/Default.aspx") it is still not clear if it is 64+

So, I thought the best way would just be to see if the notebook ran on the 64bit kernel.

What I'm hoping for is if someone confirm whether this is 64bit and how I go about installing the amd64 kernel as it does not appear in my current apt-cache search.

Cheers,

Gary.

---

### Post by newuser111 on 2006-02-09
use 32bit ubuntu, its easier to setup and install anyway

---

### Post by najames on 2006-02-09
If I were you, I'd install Ubuntu Breezy 32bit.  Then I'd add Arnieboy's Automatix.  Everything works fantastic on an AMD64 desktop.  I hope it works as well on a lappy too.  I have been using for a month or so now w/o any problems.

This is exactly the setup I'd be real happy with on a 64bit system, if it existed.  You can use the Automatix installer to configure and Syaptic as usual.

EDIT: I am installing this 32bit setup as I type on another AMD64box, for VMware attempt 2.

---

### Post by alfotis on 2006-02-09
I also have an AMD64 processor but I have ubuntu 32bit installed. I tried 64bit but it sucked. I think it's a bit early for fully 64bit OS. If I were you, I would try something more extreme like gentoo or linux from scratch in order to make sure that everything is going to be 64 bit and working

---

### Post by midwinter on 2006-02-09
Eh, 64bit is fine, great even.  I do however think that is a 32bit cpu but i'm not 100% sure.

---

### Post by drake on 2006-02-09
thats a 32 bit cpu dude.

---

### Post by pmc.nano on 2006-02-09
mh..no..i think its a 64bits procesor, bc S754 its of 64 bits ^^...hope it helped..
well..but it says down there width 32bits..im confused =O

---

### Post by Jason_25 on 2006-02-09
That's 32-bit.  If it were 64-bit, It would say 'x86-64' in the capabilities section.

---

### Post by RAOF on 2006-02-09
[QUOTE=pmc.nano]mh..no..i think its a 64bits procesor, bc S754 its of 64 bits ^^...hope it helped..
well..but it says down there width 32bits..im confused =O[/QUOTE]
The earlier socket 754 Semprons had their 64bit code disabled, so it's entirely possible that your chip is 32bit only.

---

### Post by atoponce on 2006-02-09
It is a 32-bit processor.  The data path is 32-bits wide, which makes the processor 32-bits.  Besides, 64-bit, as mentioned above, just doesn't seem to be all that great.  Hopefully, this will change in Dapper.

---

### Post by rplantz on 2006-02-10
Here's what AMD has to say about it:
```

Q:	Will the Mobile AMD Sempron processor work with 64-bit operating systems?
A:	The Mobile AMD Sempron processor is an entry-level processor for everyday
computing needs. Newer technology such as 64-bit operating systems are
targeted for higher performance needs such as CAD, audio and video editing,
large database applications, high-end consumer games and other
high-performance applications. For these uses, we recommend purchasing a PC
based on the AMD Athlon 64 processor or Mobile AMD Athlon 64 processor.
```

I had to dig around on their website, finally locating a tab "Support & Downloads." Then I scrolled down to "AMD Sempron™ FAQs" and clicked on "Mobile AMD Sempron™ Processor FAQs."

After a bit of reading, I clicked on the link that gave me the convoluted "no" above.

Along the way I clicked on "AMD Sempron™ Tech Docs" which gave me a pdf file titled "AMD Sempron™ Product Data Sheet." Since I'm an electrical engineer with a lot of assembly language embedded system experience, I thought this document would answer the question. Nope, at least not that I can tell.

 They must employ politicians to write these things.  :)

---

### Post by hasek on 2006-02-10
here is an example of a real 64 bit processor

satan
    description: Desktop Computer
    product: POWERMATE F VL350
    vendor: NEC Computers International
    version: ND991899802
    serial: 204731870004
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3
    configuration: boot=normal chassis=desktop uuid=7CCBADCE-4646-DA11-8000-4E45435F4349
  *-core
       description: Motherboard
       product: MS-7168
       vendor: NEC COMPUTERS INTERNATIONAL
       physical id: 0
       version: 1.0
       slot: To Be Filled By O.E.M.
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: 080012 (08/11/2005)
          size: 64KB
          capacity: 448KB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscree
n int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification netboot
     *-cpu
          description: CPU
          product: AMD Athlon(tm) 64 Processor 3000+
          vendor: Advanced Micro Devices [AMD]
          physical id: 4
          bus info: cpu@0
          version: AMD Athlon(tm) 64 Processor 3000+
          serial: To Be Filled By O.E.M.
          slot: CPU 1
          size: 1800MHz
          capacity: 1800MHz
          width: 64 bits
          clock: 200MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext f
xsr_opt x86-64 3dnowext 3dnow pni lahf_lm
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1-Cache
             size: 64KB
             capacity: 64KB
             capabilities: pipeline-burst internal varies data
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2-Cache
             size: 512KB
             capacity: 512KB
             capabilities: pipeline-burst internal varies unified
        *-cache:2 DISABLED
             description: L3 cache
             physical id: 7
             slot: L3-Cache
             capabilities: internal

---

### Post by rempuii7 on 2008-07-10
If your Sempron 3000+ is Palermo E6-SSE3
Socket 754   Stepping- EG
or Socket AM2 Sempron you can be sure it is both 64-bits and SSE3 capable.

If the socket is 462 it is not 
If it is a Socket 754 it depends on the stepping (part number): 
Steppings: CG (Part No.: *AX) or D0 (Part No.: *BA) have neither SSE3 nor AMD64 
Stepping: E3 (Part No.: *BO) has SSE3

So not all Semptron are the same the 64 bits are usually found in the mobile CPU-you can check your system configuration with the help of 'Everest Ultimate'it is very good.
The width: 32 bits is not important if it is 64 bits and you install 64 bits OS it will adjust.

---

### Post by ByteJuggler on 2008-07-10
Some of the Sempron 3000+'s had 64 bit ability, others didnt.  See [here.]("http://products.amd.com/en-us/DesktopCPUSideBySide.aspx?id=162&id=163&id=164&id=165&id=166")

I'm tempted to conclude (edit: I'm 100% sure, see [here.]("http://gentoo-wiki.com/Cpuinfo")) this chip does ***not*** have 64-bit support, as I think it should list the "lm" flag on the capabilities line if it has 64-bit, which this cpu does not list. Sorry. [Here's ]("http://www.gelato.unsw.edu.au/lxr/source/include/asm-i386/cpufeature.h")a reference to the different flags as defined in the kernel.  See the entry for "X86_FEATURE_LM", which is 64-bit support.

---

