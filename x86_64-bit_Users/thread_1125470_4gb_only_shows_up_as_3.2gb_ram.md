---
title: "4gb only shows up as 3.2gb ram"
date: 2009-04-14
forum: x86 64-bit Users
---

### Post by dsx on 2009-04-14
hi

i know many people have/had the same problem.
i read pretty much posts about this problem but i still cant work it out...

i have installed ubuntu 64bit version on my new pc:
mainboard: foxconn G31MX / 2x 2gb RAM
graphics: GeForce GTS 250 (512 mb)

i have only 3.2gb of ram in ubuntu (in bios its showing up as 4096mb)
my bios: Phoenix Award v6.0

i didnt find any bios update available, anyway the memory is shown correctly in bios itself.
there is no "memory remapping" option in bios, i tried other settings, but without success.

also i dont use the onboard graphics (=> no shared memory in use).

here are the hardware / system information:

=== uname outputs ===
```

uname -a: Linux dsbox 2.6.27-11-generic #1 SMP Wed Apr 1 20:53:41 UTC 2009 x86_64 GNU/Linux
uname -m: x86_64

```

=== hwinfo --mem output ===
```

01: None 00.0: 10102 Main Memory                                
  [Created at memory.61]
  Unique ID: rdCR.CxwsZFjVASF
  Hardware Class: memory
  Model: "Main Memory"
  Memory Range: 0x00000000-0xcfe8ffff (rw)
  Memory Size: 3 GB + 256 MB
  Config Status: cfg=new, avail=yes, need=no, active=unknown

```

=== first lines of dmesg ===
```

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.27-11-generic (buildd@yellow) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu11) ) #1 SMP Wed Apr 1 20:53:41 UTC 2009 (Ubuntu 2.6.27-11.31-generic)
[    0.000000] Command line: root=UUID=fd218a2a-440b-46cb-869a-063fd4fcb060 ro quiet splash iommu=65534,noagp,soft
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f400 (usable)
[    0.000000]  BIOS-e820: 000000000009f400 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000cfe90000 (usable)
[    0.000000]  BIOS-e820: 00000000cfe90000 - 00000000cfee3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000cfee3000 - 00000000cfef0000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000cfef0000 - 00000000cff00000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000] DMI 2.5 present.
[    0.000000] Phoenix BIOS detected: BIOS may corrupt low RAM, working it around.
[    0.000000] last_pfn = 0xcfe90 max_arch_pfn = 0x3ffffffff
[    0.000000] init_memory_mapping
[    0.000000]  0000000000 - 00cfe00000 page 2M
[    0.000000]  00cfe00000 - 00cfe90000 page 4k
[    0.000000] kernel direct mapping tables up to cfe90000 @ 10000-16000
[    0.000000] last_map_addr: cfe90000 end: cfe90000
[    0.000000] RAMDISK: 377ab000 - 37fefee2
[    0.000000] ACPI: RSDP 000F8040, 0024 (r2 IntelR)
[    0.000000] ACPI: XSDT CFEE3080, 004C (r1 IntelR AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: FACP CFEE8080, 00F4 (r3 IntelR AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: DSDT CFEE3200, 4E6C (r1 INTELR AWRDACPI     1000 MSFT  3000000)
[    0.000000] ACPI: FACS CFE90000, 0040
[    0.000000] ACPI: HPET CFEE8280, 0038 (r1 IntelR AWRDACPI 42302E31 AWRD       98)
[    0.000000] ACPI: MCFG CFEE82C0, 003C (r1 IntelR AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: APIC CFEE8180, 0084 (r1 IntelR AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: SSDT CFEE8960, 07EF (r1  PmRef    CpuPm     3000 INTL 20041203)
[    0.000000] No NUMA configuration found

```


as u can see at dmesg output i already tried the kernel boot-option "iommu"

same result for:
- iommu=aperture
- iommu=65534,noagp,soft
- or without this option

perhaps anybody knows what to change in this phoenix bios?
i dont find any other expedient option in that bios.


please help me to work this out

thanks in advance
ds

---

### Post by Maheriano on 2009-04-14
Is your graphics card shared memory or dedicated? If it's shared then Windows will report that much less RAM because it allocates it to the video card.

---

### Post by jespdj on 2009-04-14
If your BIOS does not have a "memory remapping" option or something similar, then it is possible that your motherboard has a chipset that does not support memory remapping.

Look in the specifications of your motherboard to find out what chipset it has exactly, and then search the web to find out if it does or does not support memory remapping.

---

### Post by dsx on 2009-04-14
hi

this is my mobo-spec:
[http://www.foxconnchannel.com/support/downloads_detail.aspx?ID=en-us0001880](http://www.foxconnchannel.com/support/downloads_detail.aspx?ID=en-us0001880)

hope the link is working.
there are all bios settings inside, but i don't know what setting is effecting the "memory remapping"

---

### Post by dsx on 2009-04-14
> **Maheriano said:**
> Is your graphics card shared memory or dedicated? If it's shared then Windows will report that much less RAM because it allocates it to the video card.

i dont use the onboard graphics, i have a dedicated GeForce GTS 250 with 512 mb ram.

---

### Post by Slim Odds on 2009-04-14
> **dsx said:**
> i dont use the onboard graphics, i have a dedicated GeForce GTS 250 with 512 mb ram.

So, is the motherboard automatically disabling the onboard video?

Maybe you need to check your BIOS settings.

---

### Post by dsx on 2009-04-14
> **Slim Odds said:**
> So, is the motherboard automatically disabling the onboard video?

Maybe you need to check your BIOS settings.

looks like, when i choose PCI-E, the memory setting will be grey'ed out.
anyway it would be only 128mb

---

### Post by LowSky on 2009-04-14
there was a BIOS update pretty recently for the 2.0 verison MB
[http://www.foxconnchannel.com/support/downloads.aspx?ProductModel=G31MX-K%202.0&TypeID=en-us0000003](http://www.foxconnchannel.com/support/downloads.aspx?ProductModel=G31MX-K%202.0&TypeID=en-us0000003)

---

### Post by dsx on 2009-04-14
> **LowSky said:**
> there was a BIOS update pretty recently for the 2.0 verison MB
[http://www.foxconnchannel.com/support/downloads.aspx?ProductModel=G31MX-K%202.0&TypeID=en-us0000003](http://www.foxconnchannel.com/support/downloads.aspx?ProductModel=G31MX-K%202.0&TypeID=en-us0000003)

hi

i just checked my mainboard.
its really looks like the one u said above (G31MX-K 2.0).
i thought, i have the first verion...

but where did u find a bios update for this mainboard?
your link doesn't work and if i search for that mainboard on the foxconn site, i only get the manual...


regards
ds

---

### Post by 3Miro on 2009-04-14
Other Linux distros (such as Fedora) also have LiveCDs. You can try loading one of them to see if it will show 4GB. If they do, then it is Ubuntu issue, if not, it might be a BIOS one.

---

### Post by dsx on 2009-04-19
i tried now with fedora 11-beta x86_64 => same result.

looks like a bios problem (or chipset)..

thx 2 all for your help

regards
ds

---

### Post by abcborges on 2009-05-25
Any luck? I have the board and the same problem.

---

### Post by LarryMi on 2009-05-25
I have a Asus-P5Q-EM motherboard.

In the bios I lowered the "DVMT Memory" from 256 to 128.  Unfortunately you can't disable this setting.  The information states this setting is for WinXP usage (perhaps necessary if your using Wine, but I'm not).

I have 4gb installed, and the system monitor shows up as 3.8 GiB.  I went through the Asus manual and checked each and every option which pretains to memory usage and 64 bit OS's.

The only setting which remains greater then 0 or enabled regarding memory is the "DVMT Memory" setting as I mentioned above.

Just a note, I installed using the minimal CD and using ext4.

Something else I don't understand, is my HDD.  The size is 640 GB, but the system monitor says the total is 596.8 GiB, Free 585.0 GiB, and 552.2 available.

---

### Post by cmost on 2009-05-25
I essentially have the same problem on my system but I'm not letting it bother me.  My 4GB of RAM is reported as 3.8 GB.  When I used a 32Bit Linux distribution, I was able to utilize my full 4 GB of RAM by recompiling the kernel with 64GB memory support enabled.  I'm sure the same would work on 64Bit Linux as well, however, in theory it shouldn't be necessary as 64Bit allows for a much higher memory range to begin with.  Nevertheless, it's worth a shot if you're willing to roll your own kernel, which is a great learning experience and highly recommended.  Here's some resources if you want to give it a shot.

How to Compile a Kernel the Ubuntu way
[http://www.howtoforge.com/kernel_compilation_ubuntu](http://www.howtoforge.com/kernel_compilation_ubuntu)

How To Compile A Kernel - Debian Etch
[http://www.howtoforge.com/kernel_compilation_debian_etch](http://www.howtoforge.com/kernel_compilation_debian_etch)

---

### Post by jazzcatgab on 2009-05-25
Well, my math might be a little shaky, but running the 64 bit version, my 4 gigs of RAM comes out 3.9, which makes sense as in actuality, 4 gigs is really 3,939,483,648 bits.

Am I wrong on that?

---

### Post by LarryMi on 2009-05-25
How do you come up with 3,939,483,64?  If each module is 2,048 MB and if you have 2, then should that not be 4,096,000?  I'm probably overlooking something.

---

### Post by abcborges on 2009-05-25
Hey guys! I have the same board and problem. I have contacted the technical support and thats what I got:

"Dear Andre,

Thank you for contacting Foxconn technical service.
This is the chipset limitation, for the motherboard can only support up to 4GB memory and the chipset does not support memory remapping function, as is why the system could only show less than 4GB.
Best regards,

Foxconn Technical Support"

---

### Post by jazzcatgab on 2009-05-26
> **LarryMi said:**
> How do you come up with 3,939,483,64?  If each module is 2,048 MB and if you have 2, then should that not be 4,096,000?  I'm probably overlooking something.

Larry, I should know when math is involved to run away. I did find a nifty little calculator for it at:
[http://www.draac.com/byte-converter.html](http://www.draac.com/byte-converter.html)

and it says 4 gigs is actually 4,194,304 kilobytes, so you are much closer than I am.

Personally, however, I'm going to think the missing 200K is overhead somewhere in the process, but it would be interesting to know where.

---

### Post by ptg on 2009-06-08
Hi

I also have the same problem with my notebook... the output of dmesg is:

[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000dc000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000bfe70000 (usable)
[    0.000000]  BIOS-e820: 00000000bfe70000 - 00000000bff00000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000bff00000 - 00000000c0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed00000 - 00000000fed00400 (reserved)
[    0.000000]  BIOS-e820: 00000000fed14000 - 00000000fed1a000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed90000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff000000 - 0000000100000000 (reserved)
[    0.000000] DMI present.
[    0.000000] Phoenix BIOS detected: BIOS may corrupt low RAM, working it around.
[    0.000000] last_pfn = 0xbfe70 max_arch_pfn = 0x3ffffffff
[    0.000000] Scanning 0 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 000000000009f800 (usable)
[    0.000000]  modified: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000dc000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 00000000bfe70000 (usable)
[    0.000000]  modified: 00000000bfe70000 - 00000000bff00000 (ACPI NVS)
[    0.000000]  modified: 00000000bff00000 - 00000000c0000000 (reserved)
[    0.000000]  modified: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  modified: 00000000fed00000 - 00000000fed00400 (reserved)
[    0.000000]  modified: 00000000fed14000 - 00000000fed1a000 (reserved)
[    0.000000]  modified: 00000000fed1c000 - 00000000fed90000 (reserved)
[    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  modified: 00000000ff000000 - 0000000100000000 (reserved)
[    0.000000] init_memory_mapping: 0000000000000000-00000000bfe70000
[    0.000000]  0000000000 - 00bfe00000 page 2M
[    0.000000]  00bfe00000 - 00bfe70000 page 4k
[    0.000000] kernel direct mapping tables up to bfe70000 @ 10000-15000
[    0.000000] last_map_addr: bfe70000 end: bfe70000


and there are lots of thing there that doesn't seem right to me... The BIOS is already in the latest version available and doesn't have the remap function (but shows 4096 mb of available ram) and the mother board is refered as CAPELL VALLEY(NAPA) CRB by Intel. Did anyone solve this type of problem? Can it be a limitation/defect of the hardware?

Thanks!

---

### Post by gordintoronto on 2009-06-08
The link worked fine for me.  Not that it's material; the problem is your BIOS.

[QUOTE=dsx;7071662]hi

but where did u find a bios update for this mainboard?
your link doesn't work ...

---

