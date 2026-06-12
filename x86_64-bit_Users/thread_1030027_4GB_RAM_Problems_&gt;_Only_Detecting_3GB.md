---
title: "4GB RAM Problems &gt; Only Detecting 3GB"
date: 2009-01-04
forum: x86 64-bit Users
---

### Post by hundredwatt on 2009-01-04
I am running 64bit Intrepid. I upgraded my system from 2x1GB of RAM to 2x2GB. I am using a Toshiba A200 with an Intel Core 2 T7200 processor. I had to flash the BIOS to get it to recognize the ram. The BIOS now shows 4096MB of memory available. However, Ubuntu only recognizes 2.9GB of memory. Here's the system output:

```
~$ free -m 
             total       used       free     shared    buffers     cached
Mem:          3015       1027       1987          0         27        342


~$ cat /proc/mtrr 
reg00: base=0x00000000 (   0MB), size=2048MB: write-back, count=1
reg01: base=0x80000000 (2048MB), size=1024MB: write-back, count=1
reg02: base=0xbff00000 (3071MB), size=   1MB: uncachable, count=1
       3015       1027       1987          0         27        342


~$ dmesg | head -20
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.27-9-generic (buildd@yellow) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu11) ) #1 SMP Thu Nov 20 22:15:32 UTC 2008 (Ubuntu 2.6.27-9.19-generic)
[    0.000000] Command line: root=UUID=ac7f825a-3651-476a-9871-82735d0f5b56 ro quiet splash 
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
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


```

I also ran the Memtest86+ v2.0.1. It detected 2 slots of 2048MB of memory, but only listed capacity as 3070MB. When I looked at the mapping. It showed one slot as mapped across something like 00000000-fffff000 and the other as only mapped across 00000000-7ffff000. 

I am not sure what else to try with this. I looked across the forums and people with a similar problem were either not running 64bit or had an ATI graphics card (I have a dedicated NVIDIA w/128MB). Also, my BIOS does not have any kind of mapping options as some of the threads suggested to look for.

---

### Post by felker2 on 2009-01-04
Interesting.

My thoughts:
what happens if you swap the memory modules in the banks?
what happens with alone memory module #2 in bank #1 (and bank #2 empty)? And with memory module #1 in bank #2 (and bank #1 empty)
isn't the BIOS limiting the memory to 3GB? A lot of computers are sold with 3GB and 32-bit Windows, to avoid 4GB / 64bit questons from customers.

Edit: I checked on [nl.computers.toshiba-europe.com]("http://nl.computers.toshiba-europe.com/innovation/jsp/SUPPORTSECTION/discontinuedProductPage.do?service=NL&DISC_MODEL=0&ACTION=PRINT_WITH_BACK&com.broadvision.session.new=Yes&PRODUCT_ID=148087"), and the Satellite A200-236 and the Satellite A200-1WF can handle 4GB of RAM. Can you check for your model?

---

### Post by graysky on 2009-01-04
There might be an option in your bios to 'remap' the memory for 64-bit operating systems.  My older Asus P5B had one (memory remap is what they called it I think) and enabling it was the only way to get to the extra memory.

EDIT: here is a screenshot of that old BIOS.  Note the top option which is what I'm talking about (it's disabled in the pic but you get the idea).

[img]http://img113.imageshack.us/img113/9047/bios3wl0.jpg[/img]

---

### Post by felker2 on 2009-01-04
@graysky: the OP should certainly check that, but he is seeing 3.0 GB. The memory-hole-remapping/hoisting problem will typically show 3.2 GB.

But as said: the OP should certainly check the remapping / hoisting is his bios.

---

### Post by felker2 on 2009-01-04
@hundredwatt:

Can you post the complete dmesg?

Have you checked your BIOS for anything limiting to 3.0 GB? Check the (onboard?) VGA settings too.

Have you tried resetting your BIOS to factory defaults to see if that helps?

How much memory do you get when you boot the 64-bit ubuntu live-CD?

---

### Post by hundredwatt on 2009-01-04
> **felker2 said:**
> @hundredwatt:

Can you post the complete dmesg?

[http://pastie.org/352290](http://pastie.org/352290)

> **felker2 said:**
> Have you checked your BIOS for anything limiting to 3.0 GB? Check the (onboard?) VGA settings too.

I did not see any remap option or anything like that and the BIOS does show 4096MB of memory. My Toshiba model A200-PSAFCU is supposed to handle 64bit and 4GB of memory.

> **felker2 said:**
> Have you tried resetting your BIOS to factory defaults to see if that helps?

How much memory do you get when you boot the 64-bit ubuntu live-CD?

I had to updgrade the Phoenix BIOS in order to get the laptop to see the full 4GB. I am going to try the LiveCD as well as swapping slots right now.

Thank you very much.

EDIT: I am currently on the LiveCD and it is also only showing 2.9GB. I swapped the two memory sticks around and it didn't make any difference. I also tried all 4 combinations of Memory Stick 1/2 in Slot A/B and in all cases both Ubuntu and the BIOS showed 2GB of memory.

---

### Post by PokerFacePenguin on 2009-01-05
I just noticed the exact same problem a bit earlier tonight.  I wondered if it was bad hardware (only a year old or so) or if it was a bug.  I was running 8.04 64-bit and showing 3.9G RAM.  After upgrading to 8.10, I now show 2.9G RAM just like yourself.  I will be checking out the hardware side of things by doing some swapping, but something strikes me as odd about this since everything is fairly new.  

Keep us posted on what you find out.  
PFP

---

### Post by felker2 on 2009-01-05
> **PokerFacePenguin said:**
> 
I was running 8.04 64-bit and showing 3.9G RAM.  After upgrading to 8.10, I now show 2.9G RAM just like yourself.



Wow, that's very strange. Can you post both dmesg-outputs here?

@OP: can you live-boot 8.04 64-bit and see what happens?

---

### Post by PokerFacePenguin on 2009-01-05
> **felker2 said:**
> Wow, that's very strange. Can you post both dmesg-outputs here?

@OP: can you live-boot 8.04 64-bit and see what happens?

Well, I guess I spoke too soon.  I got down to the dirty of swapping the ram modules in and out of different sockets.  I took all the ram out but one G at a time (there are four sticks) in two banks of two.  Using the first slot only, I tried all the RAM.  They all showed 1G in the first slot.  Then I added one to the second slot.  2G shows up in bios.  Added another to the second bank in the correct slot....3G showed up.  Added a fourth, still 3G.  I then swapped the RAM modules in the 3rd and 4th slots...showed 3G.  It appears all my RAM is good but I might have a bad slot in the final position on the motherboard because with all of the modules in I can still only show 3G in BIOSs and therefore it shows 3G in Ubuntu.  Seems it was all coincidental because the failure was noticed at the same time I did the upgrade.  What a bummer.  That liquid cooling on the motherboard is such a pain, I might be limping along with 3G for a while til a more appropriate upgrade time.   :-(  Where is that crying emoticon when I need it.

---

### Post by hundredwatt on 2009-01-06
> **felker2 said:**
> Wow, that's very strange. Can you post both dmesg-outputs here?

@OP: can you live-boot 8.04 64-bit and see what happens?

Same thing. 3070MB, 2.9GB

I am going to try getting in touch with Toshiba tech support to see if it might be a hardware issue.

---

### Post by PokerFacePenguin on 2009-01-06
I have to wonder if making shared memory changes per the HOWTO's for cinelerra at places like [http://g-raffa.eu/Cinelerra/HOWTO/installation.html]("http://g-raffa.eu/Cinelerra/HOWTO/installation.html") under the section "How to approach the Cinelerra error message you get at start up" had something to do with my supposed hardware failure.  I am going to post my output per felker's request anyway.

> ~$ free -m
             total       used       free     shared    buffers     cached
Mem:          2951       1155       1795          0         31        350
-/+ buffers/cache:        774       2177
Swap:         8134          0       8134


-----------------------------
~$ cat /proc/mtrr
reg00: base=0x100000000 (4096MB), size= 256MB: write-back, count=1
reg01: base=0x00000000 (   0MB), size=2048MB: write-back, count=1
reg02: base=0x80000000 (2048MB), size= 512MB: write-back, count=1
reg03: base=0xa0000000 (2560MB), size= 256MB: write-back, count=1
reg04: base=0xaff00000 (2815MB), size=   1MB: uncachable, count=1
-----------------------------
 
~$ dmesg | head -20
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.27-9-generic (buildd@yellow) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu11) ) #1 SMP Thu Nov 20 22:15:32 UTC 2008 (Ubuntu 2.6.27-9.19-generic)
[    0.000000] Command line: root=UUID=9bd3f68f-feb5-404d-a036-7e0778548634 ro quiet splash 
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009b800 (usable)
[    0.000000]  BIOS-e820: 000000000009b800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000afef0000 (usable)
[    0.000000]  BIOS-e820: 00000000afef0000 - 00000000afef3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000afef3000 - 00000000aff00000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000d0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 0000000110000000 (usable)
[    0.000000] last_pfn = 0x110000 max_arch_pfn = 0x3ffffffff
[    0.000000] last_pfn = 0xafef0 max_arch_pfn = 0x3ffffffff
-------------------------------

~$ dmesg
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.27-9-generic (buildd@yellow) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu11) ) #1 SMP Thu Nov 20 22:15:32 UTC 2008 (Ubuntu 2.6.27-9.19-generic)
[    0.000000] Command line: root=UUID=9bd3f68f-feb5-404d-a036-7e0778548634 ro quiet splash 
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009b800 (usable)
[    0.000000]  BIOS-e820: 000000000009b800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000afef0000 (usable)
[    0.000000]  BIOS-e820: 00000000afef0000 - 00000000afef3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000afef3000 - 00000000aff00000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000d0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 0000000110000000 (usable)
[    0.000000] last_pfn = 0x110000 max_arch_pfn = 0x3ffffffff
[    0.000000] last_pfn = 0xafef0 max_arch_pfn = 0x3ffffffff
[    0.000000] init_memory_mapping
[    0.000000]  0000000000 - 00afe00000 page 2M
[    0.000000]  00afe00000 - 00afef0000 page 4k
[    0.000000] kernel direct mapping tables up to afef0000 @ 8000-d000
[    0.000000] last_map_addr: afef0000 end: afef0000
[    0.000000] init_memory_mapping
[    0.000000]  0100000000 - 0110000000 page 2M
[    0.000000] kernel direct mapping tables up to 110000000 @ b000-11000
[    0.000000] last_map_addr: 110000000 end: 110000000
[    0.000000] RAMDISK: 377ac000 - 37fef5e7
[    0.000000] DMI 2.4 present.
[    0.000000] ACPI: RSDP 000F7F20, 0014 (r0 XFX68L)
[    0.000000] ACPI: RSDT AFEF3040, 0038 (r1 XFX68L NVDAACPI 42302E31 NVDA        0)
[    0.000000] ACPI: FACP AFEF30C0, 0074 (r1 XFX68L NVDAACPI 42302E31 NVDA        0)
[    0.000000] ACPI: DSDT AFEF3180, 5271 (r1 XFX68L NVDAACPI     1000 MSFT  3000000)
[    0.000000] ACPI: FACS AFEF0000, 0040
[    0.000000] ACPI: HPET AFEF8540, 0038 (r1 XFX68L NVDAACPI 42302E31 NVDA       98)
[    0.000000] ACPI: WDRT AFEF85C0, 0047 (r1 XFX68L NVDAACPI 42302E31 NVDA        0)
[    0.000000] ACPI: MCFG AFEF8680, 003C (r1 XFX68L NVDAACPI 42302E31 NVDA        0)
[    0.000000] ACPI: APIC AFEF8440, 0098 (r1 XFX68L NVDAACPI 42302E31 NVDA        0)
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-0000000110000000
[    0.000000] Bootmem setup node 0 0000000000000000-0000000110000000
[    0.000000]   NODE_DATA [0000000000001000 - 0000000000005fff]
[    0.000000]   bootmap [000000000000c000 -  000000000002dfff] pages 22
[    0.000000] (7 early reservations) ==> bootmem [0000000000 - 0110000000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000006000 - 0000008000]       TRAMPOLINE ==> [0000006000 - 0000008000]
[    0.000000]   #2 [0000200000 - 00008b8f9c]    TEXT DATA BSS ==> [0000200000 - 00008b8f9c]
[    0.000000]   #3 [00377ac000 - 0037fef5e7]          RAMDISK ==> [00377ac000 - 0037fef5e7]
[    0.000000]   #4 [000009b800 - 0000100000]    BIOS reserved ==> [000009b800 - 0000100000]
[    0.000000]   #5 [0000008000 - 000000b000]          PGTABLE ==> [0000008000 - 000000b000]
[    0.000000]   #6 [000000b000 - 000000c000]          PGTABLE ==> [000000b000 - 000000c000]
[    0.000000] found SMP MP-table at [ffff8800000f3f50] 000f3f50
[    0.000000]  [ffffe20000000000-ffffe200043fffff] PMD -> [ffff880028200000-ffff88002b1fffff] on node 0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   0x00100000 -> 0x00110000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x0000009b
[    0.000000]     0: 0x00000100 -> 0x000afef0
[    0.000000]     0: 0x00100000 -> 0x00110000
[    0.000000] On node 0 totalpages: 786059
[    0.000000]   DMA zone: 2102 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 700208 pages, LIFO batch:31
[    0.000000]   Normal zone: 64512 pages, LIFO batch:15
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x02] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x03] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 4, version 0, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 14 global_irq 14 high edge)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 15 global_irq 15 high edge)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] ACPI: IRQ14 used by override.
[    0.000000] ACPI: IRQ15 used by override.
[    0.000000] Setting APIC routing to flat
[    0.000000] ACPI: HPET id: 0x10de8201 base: 0xfeff0000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 4 CPUs, 0 hotplug CPUs
[    0.000000] PM: Registered nosave memory: 000000000009b000 - 000000000009c000
[    0.000000] PM: Registered nosave memory: 000000000009c000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
[    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
[    0.000000] PM: Registered nosave memory: 00000000afef0000 - 00000000afef3000
[    0.000000] PM: Registered nosave memory: 00000000afef3000 - 00000000aff00000
[    0.000000] PM: Registered nosave memory: 00000000aff00000 - 00000000d0000000
[    0.000000] PM: Registered nosave memory: 00000000d0000000 - 00000000f0000000
[    0.000000] PM: Registered nosave memory: 00000000f0000000 - 00000000fec00000
[    0.000000] PM: Registered nosave memory: 00000000fec00000 - 0000000100000000
[    0.000000] Allocating PCI resources starting at b0000000 (gap: aff00000:20100000)
[    0.000000] PERCPU: Allocating 64928 bytes of per cpu data
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 4, nr_node_ids 1
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 766822
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: root=UUID=9bd3f68f-feb5-404d-a036-7e0778548634 ro quiet splash 
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
[    0.000000] TSC: PIT calibration confirmed by PMTIMER.
[    0.000000] TSC: using PIT calibration value
[    0.000000] Detected 2399.966 MHz processor.
[    0.004000] spurious 8259A interrupt: IRQ7.
[    0.004000] Console: colour VGA+ 80x25
[    0.004000] console [tty0] enabled
[    0.004000] Checking aperture...
[    0.004000] No AGP bridge found
[    0.004000] Calgary: detecting Calgary via BIOS EBDA area
[    0.004000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.004000] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    0.004000] Placing software IO TLB between 0x20000000 - 0x24000000
[    0.004000] Memory: 3013296k/4456448k available (3112k kernel code, 130940k reserved, 1575k data, 536k init)
[    0.004000] CPA: page pool initialized 1 of 1 pages preallocated
[    0.004000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.004000] hpet clockevent registered
[    0.004000] Calibrating delay loop (skipped), value calculated using timer frequency.. 4799.93 BogoMIPS (lpj=9599864)
[    0.004000] Security Framework initialized
[    0.004000] SELinux:  Disabled at boot.
[    0.004000] AppArmor: AppArmor initialized
[    0.004000] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.004000] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.004180] Mount-cache hash table entries: 256
[    0.004368] Initializing cgroup subsys ns
[    0.004374] Initializing cgroup subsys cpuacct
[    0.004376] Initializing cgroup subsys memory
[    0.004391] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004393] CPU: L2 cache: 4096K
[    0.004395] CPU 0/0 -> Node 0
[    0.004397] CPU: Physical Processor ID: 0
[    0.004398] CPU: Processor Core ID: 0
[    0.004404] CPU0: Thermal monitoring enabled (TM1)
[    0.004406] using mwait in idle threads.
[    0.006278] ACPI: Core revision 20080609
[    0.007252] ACPI: Checking initramfs for custom DSDT
[    0.324523] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.365526] CPU0: Intel(R) Core(TM)2 Quad CPU    Q6600  @ 2.40GHz stepping 0b
[    0.365530] Using local APIC timer interrupts.
[    0.368024] APIC timer calibration result 16666481
[    0.368025] Detected 16.666 MHz APIC timer.
[    0.368135] Booting processor 1/2 ip 6000
[    0.004000] Initializing CPU#1
[    0.004000] Calibrating delay using timer specific routine.. 4800.00 BogoMIPS (lpj=9600012)
[    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004000] CPU: L2 cache: 4096K
[    0.004000] CPU 1/2 -> Node 0
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 2
[    0.004000] CPU1: Thermal monitoring enabled (TM1)
[    0.456512] CPU1: Intel(R) Core(TM)2 Quad CPU    Q6600  @ 2.40GHz stepping 0b
[    0.456533] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.460108] Booting processor 2/1 ip 6000
[    0.004000] Initializing CPU#2
[    0.004000] Calibrating delay using timer specific routine.. 4799.95 BogoMIPS (lpj=9599905)
[    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004000] CPU: L2 cache: 4096K
[    0.004000] CPU 2/1 -> Node 0
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 1
[    0.004000] CPU2: Thermal monitoring enabled (TM1)
[    0.548506] CPU2: Intel(R) Core(TM)2 Quad CPU    Q6600  @ 2.40GHz stepping 0b
[    0.548527] checking TSC synchronization [CPU#0 -> CPU#2]: passed.
[    0.552151] Booting processor 3/3 ip 6000
[    0.004000] Initializing CPU#3
[    0.004000] Calibrating delay using timer specific routine.. 4799.99 BogoMIPS (lpj=9599999)
[    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004000] CPU: L2 cache: 4096K
[    0.004000] CPU 3/3 -> Node 0
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 3
[    0.004000] CPU3: Thermal monitoring enabled (TM1)
[    0.640536] CPU3: Intel(R) Core(TM)2 Quad CPU    Q6600  @ 2.40GHz stepping 0b
[    0.640556] checking TSC synchronization [CPU#0 -> CPU#3]: passed.
[    0.644049] Brought up 4 CPUs
[    0.644053] Total of 4 processors activated (19199.89 BogoMIPS).
[    0.644123] CPU0 attaching sched-domain:
[    0.644125]  domain 0: span 0,2 level MC
[    0.644127]   groups: 0 2
[    0.644130]   domain 1: span 0-3 level CPU
[    0.644131]    groups: 0,2 1,3
[    0.644134]    domain 2: span 0-3 level NODE
[    0.644136]     groups: 0-3
[    0.644139] CPU1 attaching sched-domain:
[    0.644141]  domain 0: span 1,3 level MC
[    0.644142]   groups: 1 3
[    0.644144]   domain 1: span 0-3 level CPU
[    0.644146]    groups: 1,3 0,2
[    0.644149]    domain 2: span 0-3 level NODE
[    0.644150]     groups: 0-3
[    0.644153] CPU2 attaching sched-domain:
[    0.644154]  domain 0: span 0,2 level MC
[    0.644156]   groups: 2 0
[    0.644158]   domain 1: span 0-3 level CPU
[    0.644160]    groups: 0,2 1,3
[    0.644162]    domain 2: span 0-3 level NODE
[    0.644164]     groups: 0-3
[    0.644166] CPU3 attaching sched-domain:
[    0.644167]  domain 0: span 1,3 level MC
[    0.644169]   groups: 3 1
[    0.644171]   domain 1: span 0-3 level CPU
[    0.644173]    groups: 1,3 0,2
[    0.644175]    domain 2: span 0-3 level NODE
[    0.644177]     groups: 0-3
[    0.644309] net_namespace: 1552 bytes
[    0.644309] Booting paravirtualized kernel on bare hardware
[    0.644309] Time: 11:42:08  Date: 01/05/09
[    0.644309] NET: Registered protocol family 16
[    0.644309] ACPI: bus type pci registered
[    0.644309] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.644309] PCI: MCFG area at e0000000 reserved in E820
[    0.652836] PCI: Using MMCONFIG at e0000000 - efffffff
[    0.652838] PCI: Using configuration type 1 for base access
[    0.652885] ACPI: EC: Look up EC in DSDT
[    0.662418] ACPI: Interpreter enabled
[    0.662420] ACPI: (supports S0 S1 S3 S4 S5)
[    0.662440] ACPI: Using IOAPIC for interrupt routing
[    0.672181] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.672917] PCI: 0000:00:0a.0 reg 10 io port: [fc00, fc7f]
[    0.672965] PCI: 0000:00:0a.1 reg 10 io port: [f800, f83f]
[    0.672980] PCI: 0000:00:0a.1 reg 20 io port: [f400, f43f]
[    0.672985] PCI: 0000:00:0a.1 reg 24 io port: [f000, f03f]
[    0.673004] pci 0000:00:0a.1: PME# supported from D3hot D3cold
[    0.673009] pci 0000:00:0a.1: PME# disabled
[    0.673036] PCI: 0000:00:0b.0 reg 10 32bit mmio: [cffff000, cfffffff]
[    0.673063] pci 0000:00:0b.0: supports D1
[    0.673064] pci 0000:00:0b.0: supports D2
[    0.673066] pci 0000:00:0b.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.673069] pci 0000:00:0b.0: PME# disabled
[    0.673091] PCI: 0000:00:0b.1 reg 10 32bit mmio: [cfffe000, cfffe0ff]
[    0.673119] pci 0000:00:0b.1: supports D1
[    0.673120] pci 0000:00:0b.1: supports D2
[    0.673121] pci 0000:00:0b.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.673124] pci 0000:00:0b.1: PME# disabled
[    0.673158] PCI: 0000:00:0d.0 reg 20 io port: [ec00, ec0f]
[    0.673195] PCI: 0000:00:0e.0 reg 10 io port: [9f0, 9f7]
[    0.673199] PCI: 0000:00:0e.0 reg 14 io port: [bf0, bf3]
[    0.673203] PCI: 0000:00:0e.0 reg 18 io port: [970, 977]
[    0.673207] PCI: 0000:00:0e.0 reg 1c io port: [b70, b73]
[    0.673212] PCI: 0000:00:0e.0 reg 20 io port: [d800, d80f]
[    0.673216] PCI: 0000:00:0e.0 reg 24 32bit mmio: [cfffd000, cfffdfff]
[    0.673253] PCI: 0000:00:0e.1 reg 10 io port: [9e0, 9e7]
[    0.673257] PCI: 0000:00:0e.1 reg 14 io port: [be0, be3]
[    0.673261] PCI: 0000:00:0e.1 reg 18 io port: [960, 967]
[    0.673265] PCI: 0000:00:0e.1 reg 1c io port: [b60, b63]
[    0.673270] PCI: 0000:00:0e.1 reg 20 io port: [c400, c40f]
[    0.673274] PCI: 0000:00:0e.1 reg 24 32bit mmio: [cfffc000, cfffcfff]
[    0.673311] PCI: 0000:00:0e.2 reg 10 io port: [c000, c007]
[    0.673315] PCI: 0000:00:0e.2 reg 14 io port: [bc00, bc03]
[    0.673319] PCI: 0000:00:0e.2 reg 18 io port: [b800, b807]
[    0.673323] PCI: 0000:00:0e.2 reg 1c io port: [b400, b403]
[    0.673328] PCI: 0000:00:0e.2 reg 20 io port: [b000, b00f]
[    0.673332] PCI: 0000:00:0e.2 reg 24 32bit mmio: [cfffb000, cfffbfff]
[    0.673406] PCI: 0000:00:0f.1 reg 10 32bit mmio: [cfff4000, cfff7fff]
[    0.673436] pci 0000:00:0f.1: PME# supported from D3hot D3cold
[    0.673439] pci 0000:00:0f.1: PME# disabled
[    0.673479] PCI: 0000:00:12.0 reg 10 32bit mmio: [cfffa000, cfffafff]
[    0.673484] PCI: 0000:00:12.0 reg 14 io port: [ac00, ac07]
[    0.673488] PCI: 0000:00:12.0 reg 18 32bit mmio: [cfff9000, cfff90ff]
[    0.673492] PCI: 0000:00:12.0 reg 1c 32bit mmio: [cfff8000, cfff800f]
[    0.673515] pci 0000:00:12.0: supports D1
[    0.673516] pci 0000:00:12.0: supports D2
[    0.673518] pci 0000:00:12.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.673522] pci 0000:00:12.0: PME# disabled
[    0.673565] pci 0000:00:18.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.673568] pci 0000:00:18.0: PME# disabled
[    0.673608] PCI: 0000:01:07.0 reg 10 32bit mmio: [cfeff000, cfeff7ff]
[    0.673614] PCI: 0000:01:07.0 reg 14 32bit mmio: [cfef8000, cfefbfff]
[    0.673645] pci 0000:01:07.0: supports D1
[    0.673646] pci 0000:01:07.0: supports D2
[    0.673648] pci 0000:01:07.0: PME# supported from D0 D1 D2 D3hot
[    0.673651] pci 0000:01:07.0: PME# disabled
[    0.673677] pci 0000:00:0f.0: transparent bridge
[    0.673681] PCI: bridge 0000:00:0f.0 32bit mmio: [cfe00000, cfefffff]
[    0.673711] PCI: 0000:02:00.0 reg 10 32bit mmio: [cc000000, ccffffff]
[    0.673716] PCI: 0000:02:00.0 reg 14 32bit mmio: [b0000000, bfffffff]
[    0.673729] PCI: 0000:02:00.0 reg 1c 64bit mmio: [ca000000, cbffffff]
[    0.673734] PCI: 0000:02:00.0 reg 24 io port: [9c00, 9c7f]
[    0.673739] PCI: 0000:02:00.0 reg 30 32bit mmio: [0, 1ffff]
[    0.673788] PCI: bridge 0000:00:18.0 io port: [9000, 9fff]
[    0.673791] PCI: bridge 0000:00:18.0 32bit mmio: [ca000000, cdffffff]
[    0.673795] PCI: bridge 0000:00:18.0 64bit mmio pref: [b0000000, bfffffff]
[    0.673808] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.674377] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[    0.745273] ACPI: PCI Interrupt Link [LNK1] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.745273] ACPI: PCI Interrupt Link [LNK2] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.745273] ACPI: PCI Interrupt Link [LNK3] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.745273] ACPI: PCI Interrupt Link [LNK4] (IRQs 5 7 9 10 *11 14 15)
[    0.745273] ACPI: PCI Interrupt Link [LXV5] (IRQs 5 7 9 *10 11 14 15)
[    0.745273] ACPI: PCI Interrupt Link [LXV6] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.745273] ACPI: PCI Interrupt Link [LXV7] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.745380] ACPI: PCI Interrupt Link [LXV8] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.745549] ACPI: PCI Interrupt Link [LUBA] (IRQs 5 7 9 10 *11 14 15)
[    0.745719] ACPI: PCI Interrupt Link [LMC1] (IRQs *5 7 9 10 11 14 15)
[    0.745892] ACPI: PCI Interrupt Link [LMAC] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.746062] ACPI: PCI Interrupt Link [LAZA] (IRQs 5 7 9 10 *11 14 15)
[    0.746230] ACPI: PCI Interrupt Link [LSMB] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.746399] ACPI: PCI Interrupt Link [LUB2] (IRQs 5 7 9 *10 11 14 15)
[    0.748121] ACPI: PCI Interrupt Link [LIDE] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.748291] ACPI: PCI Interrupt Link [LSA0] (IRQs 5 7 9 10 *11 14 15)
[    0.748460] ACPI: PCI Interrupt Link [LSA1] (IRQs 5 7 9 10 *11 14 15)
[    0.748634] ACPI: PCI Interrupt Link [LSA2] (IRQs 5 7 9 *10 11 14 15)
[    0.748844] ACPI: PCI Interrupt Link [APC1] (IRQs 16) *0, disabled.
[    0.749046] ACPI: PCI Interrupt Link [APC2] (IRQs 17) *0, disabled.
[    0.749253] ACPI: PCI Interrupt Link [APC3] (IRQs 18) *0, disabled.
[    0.749454] ACPI: PCI Interrupt Link [APC4] (IRQs 19) *0
[    0.749665] ACPI: PCI Interrupt Link [AXV5] (IRQs 16) *0
[    0.749865] ACPI: PCI Interrupt Link [AXV6] (IRQs 16) *0, disabled.
[    0.750066] ACPI: PCI Interrupt Link [AXV7] (IRQs 16) *0, disabled.
[    0.750269] ACPI: PCI Interrupt Link [AXV8] (IRQs 16) *0, disabled.
[    0.750471] ACPI: PCI Interrupt Link [AUBA] (IRQs 20 21 22 23) *0
[    0.750675] ACPI: PCI Interrupt Link [AMA1] (IRQs 20 21 22 23) *0
[    0.750878] ACPI: PCI Interrupt Link [AMAC] (IRQs 20 21 22 23) *0, disabled.
[    0.751082] ACPI: PCI Interrupt Link [AAZA] (IRQs 20 21 22 23) *0
[    0.751290] ACPI: PCI Interrupt Link [AACI] (IRQs 20 21 22 23) *0, disabled.
[    0.751493] ACPI: PCI Interrupt Link [AMCI] (IRQs 20 21 22 23) *0, disabled.
[    0.751695] ACPI: PCI Interrupt Link [ASMB] (IRQs 20 21 22 23) *0, disabled.
[    0.751897] ACPI: PCI Interrupt Link [AUS2] (IRQs 20 21 22 23) *0
[    0.752110] ACPI: PCI Interrupt Link [AIDE] (IRQs 20 21 22 23) *0, disabled.
[    0.752313] ACPI: PCI Interrupt Link [ASA0] (IRQs 20 21 22 23) *0
[    0.752515] ACPI: PCI Interrupt Link [ASA1] (IRQs 20 21 22 23) *0
[    0.752717] ACPI: PCI Interrupt Link [ASA2] (IRQs 20 21 22 23) *0
[    0.752784] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.752784] pnp: PnP ACPI init
[    0.752784] ACPI: bus type pnp registered
[    0.756894] pnp: PnP ACPI: found 12 devices
[    0.756894] ACPI: ACPI bus type pnp unregistered
[    0.756894] PCI: Using ACPI for IRQ routing
[    0.776045] NET: Registered protocol family 8
[    0.776047] NET: Registered protocol family 20
[    0.776066] NetLabel: Initializing
[    0.776066] NetLabel:  domain hash size = 128
[    0.776066] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.776066] NetLabel:  unlabeled traffic allowed by default
[    0.776090] PCI-GART: No AMD northbridge found.
[    0.776097] hpet0: at MMIO 0xfeff0000, IRQs 2, 8, 31
[    0.776102] hpet0: 3 32-bit timers, 25000000 Hz
[    0.779230] tracer: 1286 pages allocated for 65536 entries of 80 bytes
[    0.779232]    actual entries 65586
[    0.779316] AppArmor: AppArmor Filesystem Enabled
[    0.779342] ACPI: RTC can wake from S4
[    0.780039] Switched to high resolution mode on CPU 0
[    0.780563] Switched to high resolution mode on CPU 2
[    0.781248] Switched to high resolution mode on CPU 3
[    0.781513] Switched to high resolution mode on CPU 1
[    0.792043] system 00:00: ioport range 0x1000-0x107f has been reserved
[    0.792047] system 00:00: ioport range 0x1080-0x10ff has been reserved
[    0.792049] system 00:00: ioport range 0x1400-0x147f has been reserved
[    0.792052] system 00:00: ioport range 0x1480-0x14ff has been reserved
[    0.792055] system 00:00: ioport range 0x1800-0x187f has been reserved
[    0.792058] system 00:00: ioport range 0x1880-0x18ff has been reserved
[    0.792066] system 00:02: ioport range 0x4d0-0x4d1 has been reserved
[    0.792068] system 00:02: ioport range 0x295-0x314 has been reserved
[    0.792071] system 00:02: ioport range 0x880-0x88f has been reserved
[    0.792094] system 00:0a: iomem range 0xe0000000-0xefffffff could not be reserved
[    0.792101] system 00:0b: iomem range 0xd0000-0xd3fff has been reserved
[    0.792104] system 00:0b: iomem range 0xd5800-0xd7fff has been reserved
[    0.792107] system 00:0b: iomem range 0xf0000-0xfbfff could not be reserved
[    0.792110] system 00:0b: iomem range 0xfc000-0xfffff could not be reserved
[    0.792113] system 00:0b: iomem range 0xafef0000-0xafefffff could not be reserved
[    0.792116] system 00:0b: iomem range 0xffff0000-0xffffffff could not be reserved
[    0.792119] system 00:0b: iomem range 0x0-0x9ffff could not be reserved
[    0.792122] system 00:0b: iomem range 0x100000-0xafeeffff could not be reserved
[    0.792125] system 00:0b: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.792128] system 00:0b: iomem range 0xd0000000-0xdfffffff could not be reserved
[    0.792131] system 00:0b: iomem range 0xfee00000-0xfee00fff could not be reserved
[    0.792134] system 00:0b: iomem range 0xfeff0000-0xfeff0000 could not be reserved
[    0.797655] pci 0000:00:0f.0: PCI bridge, secondary bus 0000:01
[    0.797657] pci 0000:00:0f.0:   IO window: disabled
[    0.797660] pci 0000:00:0f.0:   MEM window: 0xcfe00000-0xcfefffff
[    0.797663] pci 0000:00:0f.0:   PREFETCH window: disabled
[    0.797668] pci 0000:00:18.0: PCI bridge, secondary bus 0000:02
[    0.797671] pci 0000:00:18.0:   IO window: 0x9000-0x9fff
[    0.797674] pci 0000:00:18.0:   MEM window: 0xca000000-0xcdffffff
[    0.797677] pci 0000:00:18.0:   PREFETCH window: 0x000000b0000000-0x000000bfffffff
[    0.797685] pci 0000:00:0f.0: setting latency timer to 64
[    0.797691] pci 0000:00:18.0: setting latency timer to 64
[    0.797693] bus: 00 index 0 io port: [0, ffff]
[    0.797695] bus: 00 index 1 mmio: [0, ffffffffffffffff]
[    0.797696] bus: 01 index 0 mmio: [0, 0]
[    0.797698] bus: 01 index 1 mmio: [cfe00000, cfefffff]
[    0.797699] bus: 01 index 2 mmio: [0, 0]
[    0.797700] bus: 01 index 3 io port: [0, ffff]
[    0.797702] bus: 01 index 4 mmio: [0, ffffffffffffffff]
[    0.797703] bus: 02 index 0 io port: [9000, 9fff]
[    0.797705] bus: 02 index 1 mmio: [ca000000, cdffffff]
[    0.797706] bus: 02 index 2 mmio: [b0000000, bfffffff]
[    0.797707] bus: 02 index 3 mmio: [0, 0]
[    0.797715] NET: Registered protocol family 2
[    0.840204] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.841410] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    0.845755] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.846384] TCP: Hash tables configured (established 524288 bind 65536)
[    0.846386] TCP reno registered
[    0.856159] NET: Registered protocol family 1
[    0.856276] checking if image is initramfs... it is
[    1.499249] Freeing initrd memory: 8461k freed
[    1.505269] audit: initializing netlink socket (disabled)
[    1.505286] type=2000 audit(1231155727.504:1): initialized
[    1.510402] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    1.513903] VFS: Disk quotas dquot_6.5.1
[    1.514026] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    1.514158] msgmni has been set to 5901
[    1.514299] io scheduler noop registered
[    1.514301] io scheduler anticipatory registered
[    1.514303] io scheduler deadline registered
[    1.514465] io scheduler cfq registered (default)
[    1.529581] pci 0000:00:0e.0: Disabling HT MSI mapping<6>pci 0000:00:0e.1: Disabling HT MSI mapping<6>pci 0000:00:0e.2: Disabling HT MSI mapping<6>pci 0000:00:0f.0: Disabling HT MSI mapping<6>pci 0000:00:0f.1: Disabling HT MSI mapping<6>pci 0000:00:12.0: Disabling HT MSI mapping<6>pci 0000:00:18.0: Disabling HT MSI mapping<7>pci 0000:02:00.0: Boot video device
[    1.529864] pcieport-driver 0000:00:18.0: setting latency timer to 64
[    1.529912] pcieport-driver 0000:00:18.0: found MSI capability
[    1.529949] pci_express 0000:00:18.0:pcie00: allocate port service
[    1.530007] pci_express 0000:00:18.0:pcie03: allocate port service
[    1.570749] hpet_resources: 0xfeff0000 is busy
[    1.570854] Linux agpgart interface v0.103
[    1.570859] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    1.571022] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.571832] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.574252] brd: module loaded
[    1.574334] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    1.574576] PNP: No PS/2 controller found. Probing ports directly.
[    1.577424] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.577432] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.596186] mice: PS/2 mouse device common for all mice
[    1.596411] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
[    1.596440] rtc0: alarms up to one year, y3k, hpet irqs
[    1.596511] cpuidle: using governor ladder
[    1.596513] cpuidle: using governor menu
[    1.596847] TCP cubic registered
[    1.597277] registered taskstats version 1
[    1.597417]   Magic number: 9:193:731
[    1.597624] rtc_cmos 00:05: setting system clock to 2009-01-05 11:42:09 UTC (1231155729)
[    1.597631] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.597633] EDD information not available.
[    1.597666] Freeing unused kernel memory: 536k freed
[    1.597884] Write protecting the kernel read-only data: 4348k
[    1.710139] fuse init (API version 7.9)
[    1.754600] processor ACPI0007:00: registered as cooling_device0
[    1.754605] ACPI: Processor [CPU0] (supports 8 throttling states)
[    1.754698] processor ACPI0007:01: registered as cooling_device1
[    1.754776] processor ACPI0007:02: registered as cooling_device2
[    1.754843] processor ACPI0007:03: registered as cooling_device3
[    1.957345] No dock devices found.
[    1.976687] SCSI subsystem initialized
[    1.987577] libata version 3.00 loaded.
[    1.994837] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.61.
[    1.995198] ACPI: PCI Interrupt Link [AMA1] enabled at IRQ 23
[    1.995205] forcedeth 0000:00:12.0: PCI INT A -> Link[AMA1] -> GSI 23 (level, low) -> IRQ 23
[    1.995211] forcedeth 0000:00:12.0: setting latency timer to 64
[    1.995232] nv_probe: set workaround bit for reversed mac addr
[    2.007195] usbcore: registered new interface driver usbfs
[    2.007219] usbcore: registered new interface driver hub
[    2.007262] usbcore: registered new device driver usb
[    2.011078] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[    2.512453] forcedeth 0000:00:12.0: ifname eth0, PHY OUI 0x5043 @ 2, addr 00:04:4b:03:2e:3c
[    2.512456] forcedeth 0000:00:12.0: highdma csum vlan pwrctl mgmt timirq gbit lnktim msi desc-v3
[    2.513719] ACPI: PCI Interrupt Link [AUBA] enabled at IRQ 22
[    2.513727] ohci_hcd 0000:00:0b.0: PCI INT A -> Link[AUBA] -> GSI 22 (level, low) -> IRQ 22
[    2.513738] ohci_hcd 0000:00:0b.0: setting latency timer to 64
[    2.513740] ohci_hcd 0000:00:0b.0: OHCI Host Controller
[    2.513775] ohci_hcd 0000:00:0b.0: new USB bus registered, assigned bus number 1
[    2.513799] ohci_hcd 0000:00:0b.0: irq 22, io mem 0xcffff000
[    2.570272] usb usb1: configuration #1 chosen from 1 choice
[    2.570299] hub 1-0:1.0: USB hub found
[    2.570321] hub 1-0:1.0: 10 ports detected
[    2.776543] ACPI: PCI Interrupt Link [AUS2] enabled at IRQ 21
[    2.776548] ehci_hcd 0000:00:0b.1: PCI INT B -> Link[AUS2] -> GSI 21 (level, low) -> IRQ 21
[    2.776555] ehci_hcd 0000:00:0b.1: setting latency timer to 64
[    2.776558] ehci_hcd 0000:00:0b.1: EHCI Host Controller
[    2.776577] ehci_hcd 0000:00:0b.1: new USB bus registered, assigned bus number 2
[    2.776598] ehci_hcd 0000:00:0b.1: debug port 1
[    2.776602] ehci_hcd 0000:00:0b.1: cache line size of 32 is not supported
[    2.776614] ehci_hcd 0000:00:0b.1: irq 21, io mem 0xcfffe000
[    2.940066] usb 1-5: new low speed USB device using ohci_hcd and address 2
[    2.952026] ehci_hcd 0000:00:0b.1: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    2.952116] usb usb2: configuration #1 chosen from 1 choice
[    2.952146] hub 2-0:1.0: USB hub found
[    2.952154] hub 2-0:1.0: 10 ports detected
[    3.012046] hub 1-0:1.0: unable to enumerate USB device on port 5
[    3.160176] pata_acpi 0000:00:0d.0: setting latency timer to 64
[    3.161221] ACPI: PCI Interrupt Link [ASA0] enabled at IRQ 20
[    3.161226] pata_acpi 0000:00:0e.0: PCI INT A -> Link[ASA0] -> GSI 20 (level, low) -> IRQ 20
[    3.161240] pata_acpi 0000:00:0e.0: setting latency timer to 64
[    3.161247] pata_acpi 0000:00:0e.0: PCI INT A disabled
[    3.161724] ACPI: PCI Interrupt Link [ASA1] enabled at IRQ 23
[    3.161726] pata_acpi 0000:00:0e.1: PCI INT B -> Link[ASA1] -> GSI 23 (level, low) -> IRQ 23
[    3.161740] pata_acpi 0000:00:0e.1: setting latency timer to 64
[    3.161747] pata_acpi 0000:00:0e.1: PCI INT B disabled
[    3.162212] ACPI: PCI Interrupt Link [ASA2] enabled at IRQ 22
[    3.162214] pata_acpi 0000:00:0e.2: PCI INT C -> Link[ASA2] -> GSI 22 (level, low) -> IRQ 22
[    3.162228] pata_acpi 0000:00:0e.2: setting latency timer to 64
[    3.162235] pata_acpi 0000:00:0e.2: PCI INT C disabled
[    3.162793] ACPI: PCI Interrupt Link [APC4] enabled at IRQ 19
[    3.162801] ohci1394 0000:01:07.0: PCI INT A -> Link[APC4] -> GSI 19 (level, low) -> IRQ 19
[    3.162806] ohci1394 0000:01:07.0: setting latency timer to 64
[    3.213214] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[19]  MMIO=[cfeff000-cfeff7ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    3.214763] sata_nv 0000:00:0e.0: version 3.5
[    3.214772] sata_nv 0000:00:0e.0: PCI INT A -> Link[ASA0] -> GSI 20 (level, low) -> IRQ 20
[    3.214774] sata_nv 0000:00:0e.0: Using SWNCQ mode
[    3.214990] sata_nv 0000:00:0e.0: setting latency timer to 64
[    3.215192] scsi0 : sata_nv
[    3.215276] scsi1 : sata_nv
[    3.215425] ata1: SATA max UDMA/133 cmd 0x9f0 ctl 0xbf0 bmdma 0xd800 irq 20
[    3.215428] ata2: SATA max UDMA/133 cmd 0x970 ctl 0xb70 bmdma 0xd808 irq 20
[    3.688049] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    3.743865] ata1.00: ATA-7: ST3500630AS, 3.AAK, max UDMA/133
[    3.743869] ata1.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    3.784026] usb 2-7: new high speed USB device using ehci_hcd and address 4
[    3.810479] ata1.00: configured for UDMA/133
[    4.046439] usb 2-7: configuration #1 chosen from 1 choice
[    4.156022] usb 2-9: new high speed USB device using ehci_hcd and address 5
[    4.285548] ata2: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    4.295127] usb 2-9: configuration #1 chosen from 1 choice
[    4.337980] ata2.00: ATA-7: ST3500630AS, 3.AAK, max UDMA/133
[    4.337984] ata2.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    4.404598] ata2.00: configured for UDMA/133
[    4.404719] scsi 0:0:0:0: Direct-Access     ATA      ST3500630AS      3.AA PQ: 0 ANSI: 5
[    4.404853] scsi 1:0:0:0: Direct-Access     ATA      ST3500630AS      3.AA PQ: 0 ANSI: 5
[    4.404922] sata_nv 0000:00:0e.1: PCI INT B -> Link[ASA1] -> GSI 23 (level, low) -> IRQ 23
[    4.404925] sata_nv 0000:00:0e.1: Using SWNCQ mode
[    4.404962] sata_nv 0000:00:0e.1: setting latency timer to 64
[    4.405074] scsi2 : sata_nv
[    4.405139] scsi3 : sata_nv
[    4.405305] ata3: SATA max UDMA/133 cmd 0x9e0 ctl 0xbe0 bmdma 0xc400 irq 23
[    4.405307] ata4: SATA max UDMA/133 cmd 0x960 ctl 0xb60 bmdma 0xc408 irq 23
[    4.484199] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0d6020ed00044b03]
[    4.596018] usb 1-5: new low speed USB device using ohci_hcd and address 3
[    4.880170] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    4.885175] usb 1-5: configuration #1 chosen from 1 choice
[    4.888536] ata3.00: ATA-8: ST3500320AS, SD15, max UDMA/133
[    4.888538] ata3.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    4.905547] ata3.00: configured for UDMA/133
[    5.192039] usb 1-6: new low speed USB device using ohci_hcd and address 4
[    5.380108] ata4: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    5.388520] ata4.00: ATA-8: ST3500320AS, SD15, max UDMA/133
[    5.388523] ata4.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    5.404548] ata4.00: configured for UDMA/133
[    5.404656] scsi 2:0:0:0: Direct-Access     ATA      ST3500320AS      SD15 PQ: 0 ANSI: 5
[    5.404782] scsi 3:0:0:0: Direct-Access     ATA      ST3500320AS      SD15 PQ: 0 ANSI: 5
[    5.404849] sata_nv 0000:00:0e.2: PCI INT C -> Link[ASA2] -> GSI 22 (level, low) -> IRQ 22
[    5.404852] sata_nv 0000:00:0e.2: Using SWNCQ mode
[    5.404885] sata_nv 0000:00:0e.2: setting latency timer to 64
[    5.404985] scsi4 : sata_nv
[    5.405056] scsi5 : sata_nv
[    5.405171] usb 1-6: configuration #1 chosen from 1 choice
[    5.405228] ata5: SATA max UDMA/133 cmd 0xc000 ctl 0xbc00 bmdma 0xb000 irq 22
[    5.405231] ata6: SATA max UDMA/133 cmd 0xb800 ctl 0xb400 bmdma 0xb008 irq 22
[    5.408613] usbcore: registered new interface driver hiddev
[    5.408613] usbcore: registered new interface driver libusual
[    5.413178] Initializing USB Mass Storage driver...
[    5.413617] scsi6 : SCSI emulation for USB Mass Storage devices
[    5.413708] usb-storage: device found at 5
[    5.413710] usb-storage: waiting for device to settle before scanning
[    5.418551] scsi 0:0:0:0: Attached scsi generic sg0 type 0
[    5.418579] scsi 1:0:0:0: Attached scsi generic sg1 type 0
[    5.418608] scsi 2:0:0:0: Attached scsi generic sg2 type 0
[    5.418636] scsi 3:0:0:0: Attached scsi generic sg3 type 0
[    5.739477] ata5: SATA link down (SStatus 0 SControl 300)
[    6.066478] ata6: SATA link down (SStatus 0 SControl 300)
[    6.066560] pata_amd 0000:00:0d.0: version 0.3.10
[    6.066595] pata_amd 0000:00:0d.0: setting latency timer to 64
[    6.067115] scsi7 : pata_amd
[    6.069215] scsi8 : pata_amd
[    6.070859] ata7: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xec00 irq 14
[    6.070861] ata8: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xec08 irq 15
[    6.424286] ata7.01: ATAPI: LITE-ON DVDRW LH-20A1P, KL0N, max UDMA/66
[    6.424295] ata7: nv_mode_filter: 0x1f39f&0x1f01f->0x1f01f, BIOS=0x1f000 (0xc50000) ACPI=0x1f01f (600:30:0x1c)
[    6.424297] ata7.01: limited to UDMA/33 due to 40-wire cable
[    6.456218] ata7.01: configured for UDMA/33
[    6.456243] ata8: port disabled. ignoring.
[    6.457271] scsi 7:0:1:0: CD-ROM            LITE-ON  DVDRW LH-20A1P   KL0N PQ: 0 ANSI: 5
[    6.457414] scsi 7:0:1:0: Attached scsi generic sg4 type 5
[    6.473094] Driver 'sd' needs updating - please use bus_type methods
[    6.473202] sd 0:0:0:0: [sda] 976773168 512-byte hardware sectors (500108 MB)
[    6.473217] sd 0:0:0:0: [sda] Write Protect is off
[    6.473219] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    6.473242] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    6.473316] sd 0:0:0:0: [sda] 976773168 512-byte hardware sectors (500108 MB)
[    6.473329] sd 0:0:0:0: [sda] Write Protect is off
[    6.473331] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    6.473353] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    6.473357]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[    6.490407]  sda1 sda2 < sda5 > sda4
[    6.514253] sd 0:0:0:0: [sda] Attached SCSI disk
[    6.514342] sd 1:0:0:0: [sdb] 976773168 512-byte hardware sectors (500108 MB)
[    6.514357] sd 1:0:0:0: [sdb] Write Protect is off
[    6.514359] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    6.514384] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    6.514432] sd 1:0:0:0: [sdb] 976773168 512-byte hardware sectors (500108 MB)
[    6.514446] sd 1:0:0:0: [sdb] Write Protect is off
[    6.514448] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    6.514471] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    6.514474]  sdb: sdb1
[    6.534915] sd 1:0:0:0: [sdb] Attached SCSI disk
[    6.534985] sd 2:0:0:0: [sdc] 976773168 512-byte hardware sectors (500108 MB)
[    6.535000] sd 2:0:0:0: [sdc] Write Protect is off
[    6.535001] sd 2:0:0:0: [sdc] Mode Sense: 00 3a 00 00
[    6.535026] sd 2:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    6.535072] sd 2:0:0:0: [sdc] 976773168 512-byte hardware sectors (500108 MB)
[    6.535086] sd 2:0:0:0: [sdc] Write Protect is off
[    6.535088] sd 2:0:0:0: [sdc] Mode Sense: 00 3a 00 00
[    6.535117] sd 2:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    6.535119]  sdc: sdc1
[    6.539969] sd 2:0:0:0: [sdc] Attached SCSI disk
[    6.540062] sd 3:0:0:0: [sdd] 976773168 512-byte hardware sectors (500108 MB)
[    6.540076] sd 3:0:0:0: [sdd] Write Protect is off
[    6.540078] sd 3:0:0:0: [sdd] Mode Sense: 00 3a 00 00
[    6.540103] sd 3:0:0:0: [sdd] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    6.540152] sd 3:0:0:0: [sdd] 976773168 512-byte hardware sectors (500108 MB)
[    6.540166] sd 3:0:0:0: [sdd] Write Protect is off
[    6.540168] sd 3:0:0:0: [sdd] Mode Sense: 00 3a 00 00
[    6.540192] sd 3:0:0:0: [sdd] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    6.540195]  sdd: sdd1
[    6.547781] sd 3:0:0:0: [sdd] Attached SCSI disk
[    6.558399] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    6.558403] Uniform CD-ROM driver Revision: 3.20
[    6.558496] sr 7:0:1:0: Attached scsi CD-ROM sr0
[    6.569264] hiddev96hidraw0: USB HID v1.10 Device [American Power Conversion Back-UPS XS 1300 LCD FW:836.H5 .D USB FW:H5 ] on usb-0000:00:0b.0-5
[    6.574445] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:0b.0/usb1/1-6/1-6:1.0/input/input1
[    6.600162] input,hidraw1: USB HID v1.10 Keyboard [Logitech USB Receiver] on usb-0000:00:0b.0-6
[    6.609124] Fixing up Logitech keyboard report descriptor
[    6.609924] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:0b.0/usb1/1-6/1-6:1.1/input/input2
[    6.664216] input,hiddev97,hidraw2: USB HID v1.10 Mouse [Logitech USB Receiver] on usb-0000:00:0b.0-6
[    6.664257] usbcore: registered new interface driver usb-storage
[    6.664258] usbcore: registered new interface driver usbhid
[    6.664260] usbhid: v2.6:USB HID core driver
[    6.664262] USB Mass Storage support registered.
[    6.778652] PM: Starting manual resume from disk
[    6.778655] PM: Resume from partition 8:5
[    6.778656] PM: Checking hibernation image.
[    6.778792] PM: Resume from disk failed.
[    6.820544] kjournald starting.  Commit interval 5 seconds
[    6.820550] EXT3-fs: mounted filesystem with ordered data mode.
[   10.412303] usb-storage: device scan complete
[   10.414014] scsi 6:0:0:0: Direct-Access     Generic  USB SD Reader    1.00 PQ: 0 ANSI: 0
[   10.414510] scsi 6:0:0:1: Direct-Access     Generic  USB CF Reader    1.01 PQ: 0 ANSI: 0
[   10.415010] scsi 6:0:0:2: Direct-Access     Generic  USB SM Reader    1.02 PQ: 0 ANSI: 0
[   10.415511] scsi 6:0:0:3: Direct-Access     Generic  USB MS Reader    1.03 PQ: 0 ANSI: 0
[   10.416716] sd 6:0:0:0: [sde] Attached SCSI removable disk
[   10.416826] sd 6:0:0:0: Attached scsi generic sg5 type 0
[   10.417563] sd 6:0:0:1: [sdf] Attached SCSI removable disk
[   10.417617] sd 6:0:0:1: Attached scsi generic sg6 type 0
[   10.418436] sd 6:0:0:2: [sdg] Attached SCSI removable disk
[   10.418491] sd 6:0:0:2: Attached scsi generic sg7 type 0
[   10.419312] sd 6:0:0:3: [sdh] Attached SCSI removable disk
[   10.419365] sd 6:0:0:3: Attached scsi generic sg8 type 0
[   11.853112] ip_tables: (C) 2000-2006 Netfilter Core Team
[   11.885107] nf_conntrack version 0.5.0 (16384 buckets, 65536 max)
[   11.885216] CONFIG_NF_CT_ACCT is deprecated and will be removed soon. Plase use
[   11.885219] nf_conntrack.acct=1 kernel paramater, acct=1 nf_conntrack module option or
[   11.885221] sysctl net.netfilter.nf_conntrack_acct=1 to enable it.
[   11.996305] udevd version 124 started
[   12.195415] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[   12.212033] ACPI: Power Button (FF) [PWRF]
[   12.212108] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input4
[   12.244019] ACPI: Power Button (CM) [PWRB]
[   12.690581] ck804xrom ck804xrom_init_one(): Unable to register resource 0x00000000ff000000-0x00000000ffffffff - kernel bug?
[   12.729675] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   12.773504] i2c-adapter i2c-0: nForce2 SMBus adapter at 0xf400
[   12.773539] i2c-adapter i2c-1: nForce2 SMBus adapter at 0xf000
[   12.808682] input: PC Speaker as /devices/platform/pcspkr/input/input5
[   12.859858] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   12.906635] Found: SST 49LF040B
[   12.906638] ck804xrom @fff80000: Found 1 x8 devices at 0x0 in 8-bit bank
[   12.935173] Linux video capture interface: v2.00
[   13.226152] nvidia: module license 'NVIDIA' taints kernel.
[   13.482185] ACPI: PCI Interrupt Link [AXV5] enabled at IRQ 16
[   13.482194] nvidia 0000:02:00.0: PCI INT A -> Link[AXV5] -> GSI 16 (level, low) -> IRQ 16
[   13.482200] nvidia 0000:02:00.0: setting latency timer to 64
[   13.482488] using fwh lock/unlock method
[   13.482491] number of JEDEC chips: 1
[   13.482492] cfi_cmdset_0002: Disabling erase-suspend-program due to code brokenness.
[   13.482693] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  177.80  Wed Oct  1 14:43:46 PDT 2008
[   13.497601] uvcvideo: Found UVC 1.00 device <unnamed> (046d:0990)
[   13.513563] input: UVC Camera (046d:0990) as /devices/pci0000:00/0000:00:0b.1/usb2/2-7/2-7:1.0/input/input6
[   13.541199] usbcore: registered new interface driver uvcvideo
[   13.541202] USB Video Class driver (v0.1.0)
[   14.119142] ACPI: PCI Interrupt Link [AAZA] enabled at IRQ 21
[   14.119147] HDA Intel 0000:00:0f.1: PCI INT B -> Link[AAZA] -> GSI 21 (level, low) -> IRQ 21
[   14.119162] HDA Intel 0000:00:0f.1: setting latency timer to 64
[   14.122844] usbcore: registered new interface driver snd-usb-audio
[   14.150796] hda_codec: Unknown model for ALC882, trying auto-probe from BIOS...
[   14.743313] lp: driver loaded but no devices found
[   14.889109] Adding 8329660k swap on /dev/sda5.  Priority:-1 extents:1 across:8329660k
[   15.430970] EXT3 FS on sda1, internal journal
[   16.207767] kjournald starting.  Commit interval 5 seconds
[   16.208091] EXT3 FS on sda4, internal journal
[   16.208098] EXT3-fs: mounted filesystem with ordered data mode.
[   16.244035] kjournald starting.  Commit interval 5 seconds
[   16.244052] EXT3-fs warning: maximal mount count reached, running e2fsck is recommended
[   16.244353] EXT3 FS on sdb1, internal journal
[   16.244358] EXT3-fs: mounted filesystem with ordered data mode.
[   16.354262] kjournald starting.  Commit interval 5 seconds
[   16.354271] EXT3-fs warning: maximal mount count reached, running e2fsck is recommended
[   16.354790] EXT3 FS on sdc1, internal journal
[   16.354795] EXT3-fs: mounted filesystem with ordered data mode.
[   16.379347] kjournald starting.  Commit interval 5 seconds
[   16.379844] EXT3 FS on sdd1, internal journal
[   16.379848] EXT3-fs: mounted filesystem with ordered data mode.
[   16.633192] type=1505 audit(1231155744.021:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=4974
[   16.744371] type=1505 audit(1231155744.133:3): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=4979
[   16.744555] type=1505 audit(1231155744.133:4): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=4979
[   17.320255] ACPI: WMI: Mapper loaded
[   18.178527] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
[   19.740154] ppdev: user-space parallel port driver
[   24.724621] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[   24.724627] vboxdrv: Successfully done.
[   24.724628] vboxdrv: Found 4 processor cores.
[   24.725531] VBoxDrv: dbg - g_abExecMemory=ffffffffa0c38fc0
[   24.725587] vboxdrv: fAsync=0 offMin=0x44a offMax=0x1e2a
[   24.726782] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[   24.726786] vboxdrv: Successfully loaded version 2.1.0 (interface 0x000a0008).
[   26.048861] Bluetooth: Core ver 2.13
[   26.049311] NET: Registered protocol family 31
[   26.049315] Bluetooth: HCI device and connection manager initialized
[   26.049323] Bluetooth: HCI socket layer initialized
[   26.056520] Bluetooth: L2CAP ver 2.11
[   26.056525] Bluetooth: L2CAP socket layer initialized
[   26.061045] Bluetooth: RFCOMM socket layer initialized
[   26.061074] Bluetooth: RFCOMM TTY layer initialized
[   26.061075] Bluetooth: RFCOMM ver 1.10
[   26.070993] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   26.070998] Bluetooth: BNEP filters: protocol multicast
[   26.095389] Bridge firewalling registered
[   26.095819] pan0: Dropping NETIF_F_UFO since no NETIF_F_HW_CSUM feature.
[   26.100776] Bluetooth: SCO (Voice Link) ver 0.6
[   26.100781] Bluetooth: SCO socket layer initialized
[   30.278077] NET: Registered protocol family 17
[   33.747062] NET: Registered protocol family 10
[   33.748076] lo: Disabled Privacy Extensions
[   43.888038] eth0: no IPv6 routers present


---

### Post by williamson389 on 2009-01-06
Speaking from experience, i upgraded my shitty Acer laptop to 4 gb of ram. I had the same problem of not all of it being recognized.  I ended up having to upgrade to 64 bit.  it sucked, but was worth it in the end.

---

### Post by PokerFacePenguin on 2009-01-07
> **williamson389 said:**
> Speaking from experience, i upgraded my shitty Acer laptop to 4 gb of ram. I had the same problem of not all of it being recognized.  I ended up having to upgrade to 64 bit.  it sucked, but was worth it in the end.

Not the same problem.  I HAD 4GB showing up under 64 bit Hardy.  Now I recently discovered under Intrepid that I have 3GB.  I think it is hardware malfunction on my issue.

---

### Post by blackgr on 2009-01-10
> **PokerFacePenguin said:**
> Not the same problem.  I HAD 4GB showing up under 64 bit Hardy.  Now I recently discovered under Intrepid that I have 3GB.  I think it is hardware malfunction on my issue.

Try installing the server kernel from the repositories.

---

### Post by matsonfamily on 2009-01-12
I am getting the same thing.  3G and on 8.10 64bit, generic kernel.  I have 4G.  Swapping RAM (only 2 slots in my desktop mobo!) doesn't help.  Parted Magic (Slackware based, I think) shows 4G, but Ubuntu 8.10 shows 3G.  I have added mem=4G on the kernel line (of /boot/grub/menu.lst) to "force" it to recognize 4G, but no luck.  As a side note, I have installed 8.10 64bit on my Toshiba laptop (L305D series) and it recognizes 4G with the same kernel, and no mem=4G line passed to the kernel via grub.  I am really at a loss of how to troubleshoot this.  I assume the BIOS/mobo is ok, since a linux based distro can use all 4G, just not Ubuntu 8.10 64bit.  I assume there's no prob with Ubuntu 8.10 64bit as well, since my laptop does it with no extra configuration...

<confused>

---

### Post by Victormd on 2009-01-13
> **PokerFacePenguin said:**
> Well, I guess I spoke too soon.  I got down to the dirty of swapping the ram modules in and out of different sockets.  I took all the ram out but one G at a time (there are four sticks) in two banks of two.  Using the first slot only, I tried all the RAM.  They all showed 1G in the first slot.  Then I added one to the second slot.  2G shows up in bios.  Added another to the second bank in the correct slot....3G showed up.  Added a fourth, still 3G.  I then swapped the RAM modules in the 3rd and 4th slots...showed 3G.  It appears all my RAM is good but I might have a bad slot in the final position on the motherboard because with all of the modules in I can still only show 3G in BIOSs and therefore it shows 3G in Ubuntu.  Seems it was all coincidental because the failure was noticed at the same time I did the upgrade.  What a bummer.  That liquid cooling on the motherboard is such a pain, I might be limping along with 3G for a while til a more appropriate upgrade time.   :-(  Where is that crying emoticon when I need it.
Don't be too quick to blame it on your hardware. You say that you have a problem on your mem slot 4. What happens if you plug your sticks in slots 1, 2 and 4; 1, 3, and 4; and 2,3 and 4? This will tell you if it's a hardware problem or configuration issue...

---

### Post by joebuntu_2 on 2009-03-13
I have the same issue, Acer Aspire 5680 laptop. 4096mb shows in bios, only 2.9g showing in intrepid. Running 64bit.

Some people say the bios needs to be set to remap the memory (not an option on my crappy BIOS). Others say you need to add the iomem=noaperture line on the grub menu. Tried this but no joy. I ran Vista 64 once before and that showed all 4gb which leads me to think it's not a bios setting.

If anyone experiences the same issue and gets a fix, please post it back here. Keen to get this running at full capacity!
Thanks

---

### Post by petri on 2009-03-13
I've been wondering this also.

I have a Asus P5Q-E and it shows only 2,9GB although I have 8GB. I have already reinstalled Ubuntu but still 2,9GB RAM.

I have tested all the memory modules one by one and they all show 2GB so the modules should be ok.

I'm starting to suspect there is something wrong in Intrepid 64-bits.



EDIT: Well enagling memory mapping in BIOS as advised in [http://ubuntuforums.org/showpost.php?p=6490982&postcount=3](http://ubuntuforums.org/showpost.php?p=6490982&postcount=3) did the trick for me. Should have tried it before posting 	:redface:

---

### Post by 3Miro on 2009-03-13
> **hundredwatt said:**
> I am running 64bit Intrepid. I upgraded my system from 2x1GB of RAM to 2x2GB. I am using a Toshiba A200 with an Intel Core 2 T7200 processor. I had to flash the BIOS to get it to recognize the ram. The BIOS now shows 4096MB of memory available. However, Ubuntu only recognizes 2.9GB of memory. Here's the system output:

```
~$ free -m 
             total       used       free     shared    buffers     cached
Mem:          3015       1027       1987          0         27        342


~$ cat /proc/mtrr 
reg00: base=0x00000000 (   0MB), size=2048MB: write-back, count=1
reg01: base=0x80000000 (2048MB), size=1024MB: write-back, count=1
reg02: base=0xbff00000 (3071MB), size=   1MB: uncachable, count=1
       3015       1027       1987          0         27        342


~$ dmesg | head -20
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.27-9-generic (buildd@yellow) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu11) ) #1 SMP Thu Nov 20 22:15:32 UTC 2008 (Ubuntu 2.6.27-9.19-generic)
[    0.000000] Command line: root=UUID=ac7f825a-3651-476a-9871-82735d0f5b56 ro quiet splash 
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
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


```

I also ran the Memtest86+ v2.0.1. It detected 2 slots of 2048MB of memory, but only listed capacity as 3070MB. When I looked at the mapping. It showed one slot as mapped across something like 00000000-fffff000 and the other as only mapped across 00000000-7ffff000. 

I am not sure what else to try with this. I looked across the forums and people with a similar problem were either not running 64bit or had an ATI graphics card (I have a dedicated NVIDIA w/128MB). Also, my BIOS does not have any kind of mapping options as some of the threads suggested to look for.

OK I am not a great expert (understatement), but here is something peculiar:

7ffff000 for memory address is actually 7f-ff-f0-00, 2 hex digits for a byte, which gives us total of 4-bytes, times 8-bits per byte = 32-bits!

I think you guys just have the wrong version of Ubuntu installed.

In general I have 2 systems with 4GB of ram (kubuntu and ubuntu) and they both show 3.9 I think it might be related to BIOS taking 64MB or whatever, in either case I don't care enough about it to go after it in details.

---

### Post by joebuntu_2 on 2009-03-13
> **3Miro said:**
> OK I am not a great expert (understatement), but here is something peculiar:

7ffff000 for memory address is actually 7f-ff-f0-00, 2 hex digits for a byte, which gives us total of 4-bytes, times 8-bits per byte = 32-bits!

I think you guys just have the wrong version of Ubuntu installed.

In general I have 2 systems with 4GB of ram (kubuntu and ubuntu) and they both show 3.9 I think it might be related to BIOS taking 64MB or whatever, in either case I don't care enough about it to go after it in details.


Mine is def 64 bit, checked the version number and get told everytime I try and install 32 bit software.

Anyway, I tried the latest 64 bit OpenSUSE live cd but that also showed 2.9GB. Maybe it's the motherboard after all. Running on 32 bit now - shows me having 3.0 gig instead of 2.9 on 64 bit. Sweet - extra 100mb, WOOP WOOP!

---

### Post by ahbart on 2009-03-16
I have the same problem on my Ubuntu 86_64 system. I have 4Gb in 4 separated modules of 1Gb. As far as I know I could see all 4Gb with hardy (when I installed the 4Gb). 
This is whatt free -m tell's me:
```

             total       used       free     shared    buffers     cached
Mem:          3393        865       2528          0          4        341
-/+ buffers/cache:        519       2873

```
So a total of 3393Kb. I think/assume this is 3,2Gb.

I have no remap option in the bios, and the motherboard manual tell me that:
"Supports up to 4GB memory size."
I will try some live cd's.

---

### Post by ahbart on 2009-03-16
Damn! I just found this in my manual. Haven't seen that before:
```
Due to the South Bridge resource deployment, the system density
will only be detected up to 3+GB (not full 4GB) when each DIMM is
installed with an 1GB memory module.
```
and:
```

Install at least one DIMM module on the slots. Each DIMM slot supports
up to a maximum size of 1GB. Users can install either single- or double-sided 
modules to meet their own needs. Please note that each DIM M can
work respectively for single-channel DDR, while both channels 
(in different color) populated with same amount of memory size 
will work as dual-channel DDR.
```
Sounds like this motheboard support 4Gb of memory, but it does actually not, because I can not use modules bigger then 1Gb in each slot.
Am I right?
It's a MSI ms7204 mainboard.

---

### Post by albandy on 2009-03-16
cat /boot/config-2.6.24-23-generic | grep HIGH

This will show your kernel memory configuration

CONFIG_HIGHMEM=y
CONFIG_HIGHPTE=y
CONFIG_HIGH_RES_TIMERS=y
# CONFIG_NOHIGHMEM is not set
CONFIG_HIGHMEM4G=y
# CONFIG_HIGHMEM64G is not set

Ensure CONFIG_HIGHMEM is set to y and CONFIG_HIGHMEM4G is set to y
also you can try with the server kernel what is configured to support 64GB by default

if HIGHMEM and HIGIMEM4G are enabled it's a BIOS problem

---

### Post by ahbart on 2009-03-16
Okay. Thanks for your quick answer.
```
 cat /boot/config-2.6.27-9-generic | grep HIGH
CONFIG_HIGH_RES_TIMERS=y

```
It looks like some lines are missing?
Can I add these somewhere or is this a kernel compile issue?

---

### Post by albandy on 2009-03-16
from my ubuntu 8.10 32bit machine I get this answer:
cat config-2.6.27-11-generic | grep HIGH
# CONFIG_DEBUG_HIGHMEM is not set
CONFIG_HIGHMEM=y
CONFIG_HIGHPTE=y
CONFIG_HIGH_RES_TIMERS=y
# CONFIG_NOHIGHMEM is not set
CONFIG_HIGHMEM4G=y
# CONFIG_HIGHMEM64G is not set

Ensure you're using the last kernel version.

---

### Post by ahbart on 2009-03-16
I use: uname -r
```
2.6.27-9-generic
```
on: uname -m
```
x86_64
```
and: cat /etc/lsb-release
```
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=8.10
DISTRIB_CODENAME=intrepid
DISTRIB_DESCRIPTION="Ubuntu 8.10"
```

The latest kernel 2.6.27-11 disabled my wireless.
But: cat /boot/config-2.6.27-11-generic | grep HIGH
Gives the same output:
```
CONFIG_HIGH_RES_TIMERS=y
```

---

### Post by euxneks on 2009-03-19
Was browsing this forum, saw this issue, remembered I had encountered it before on my fiancee's machine, thought I would pipe up and offer support, then I realized looking at my machine that it was only reporting 2.9G from my 4G as well! D'Oh!

Anyway, went into BIOS, did the memory remap thing ala:

[http://ubuntuforums.org/showpost.php?p=6490982&postcount=3](http://ubuntuforums.org/showpost.php?p=6490982&postcount=3)

(set to enabled) and it works now. I have an ASUS P5B.

---

### Post by ahbart on 2009-03-19
Damn. My computer doesn't allow remapping. MSI told me (it's a MSI OEM motherboard) that the South bridge reserves a big amount of memory for hardware addressing! Almost 800Mb!!!
Ridiculous. There is noting I can do about that. 

That this motherboard would accept 4Gb memory is almost misleading if you can only use 3,2Gb of the 4!

---

### Post by albandy on 2009-03-19
> **ahbart said:**
> Damn. My computer doesn't allow remapping. MSI told me (it's a MSI OEM motherboard) that the South bridge reserves a big amount of memory for hardware addressing! Almost 800Mb!!!
Ridiculous. There is noting I can do about that. 

That this motherboard would accept 4Gb memory is almost misleading if you can only use 3,2Gb of the 4!

Have you updated your BIOS?

---

### Post by ahbart on 2009-03-19
yes. That did not help at all. No remapping in this BIOS. MSI told me it is a chip limitation.

---

### Post by Scubdup on 2009-03-19
> **felker2 said:**
> @graysky: the OP should certainly check that, but he is seeing 3.0 GB. The memory-hole-remapping/hoisting problem will typically show 3.2 GB.Thanks for this. Slightly OT but this has resolved a problem I was having. Tried the Live CD for 64-bit, just to see if my old 5 gb RAM P4 could handle it, which it could, but was showing only 3.2Gb of the RAM. I'm certain therefore that I have this remapping/Hoisting issue, and thankts to your post I know where to look for a solution.

---

### Post by RoboNuggie on 2009-03-19
I was having the same issue with only 3.2 gb being detected.

I disabled all non essential and unused USB, serial and parallel ports on my desktop (I have an additional USB 2.0 card so don't need the motherboard ones) and tried again.... and now I have 3.9 gb detected... which I think will do me fine for now.

---

### Post by Slim Odds on 2009-03-19
> **Scubdup said:**
> Tried the Live CD for 64-bit, just to see if my old 5 gb RAM P4 could handle it, which it could, but was showing only 3.2Gb of the RAM.

Not sure how it "handled it" since the P4 is not a 64 bit CPU.

---

### Post by Yellow Pasque on 2009-03-19
> **Slim Odds said:**
> Not sure how it "handled it" since the P4 is not a 64 bit CPU.
Some P4's had EM64T

---

### Post by Slim Odds on 2009-03-19
> **Temüjin said:**
> Some P4's had EM64T

Thanks, I did not know that.....

---

### Post by can8dnSix on 2009-03-20
You'll get that decimal (7.8) etc because of the conversion between binary and decimal. For example, check out your hard drive; you know you have a 320GB drive but it only shows up as 298.1GB (instead of 320GB). 

1GB=2^30 or 1024^3 (binary)  1,073,741,824 x 298.1 = 320GB (decimal)
1GB=10^9 or 1000^3 (decimal) 1,000,000,000 x 320.0 = 320GB (decimal)

Nonetheless, I believe you can have it show the binary number instead of the decimal number which is the one we see most of the time. Anyway, the actual amount of RAM one has is "greater" if one does the binary value of the number as opposed to the decimal value of the number. Anyway, just my $0.02.

L

---

### Post by MGlosenger on 2009-03-20
I had the same issue with my AsRock 939 Dual SATA 2 mobo and Ubuntu 8.10..  if I turn on the 'memory hole' in BIOS, though, I can access all 4 GB.  Otherwise I get 3.  Go figure.

I don't think the 'memory hole' option was created for this issue, but the Dual SATA 2's BIOS is rather dicey in general, but hey, whateva works!

---

### Post by Slim Odds on 2009-03-20
> **MGlosenger said:**
> I had the same issue with my AsRock 939 Dual SATA 2 mobo and Ubuntu 8.10..  if I turn on the 'memory hole' in BIOS, though, I can access all 4 GB.  Otherwise I get 3.  Go figure.

I don't think the 'memory hole' option was created for this issue, but the Dual SATA 2's BIOS is rather dicey in general, but hey, whateva works!

That's **exactly** what the "memory hole" was created to do.

Some devices (probably most) are not 64 bit and they have memory that needs to be addressed. That memory must reside **below** the 4G limit (since they are not able to use a higher address). Therefore, the memory hole takes some of the RAM that **would be below 4G** and moves it UP. So you still get all of your RAM and some room to put the devices.

---

### Post by ameno on 2009-03-24
just as a note for intel dg45id users: remapping is not enabled in manual memory configuration mode (bios version used: 0091). use auto if you have more than 3GB.

---

### Post by jo4hnc on 2009-03-24
Hi Guys,

There's a bug report posted for this issue.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/271070](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/271070)

Don't know if it will help but its worth a look.

I've also seen it posted that it may have been resolved in the next distro.

John

---

### Post by warpasylum on 2009-04-01
Hey guys,
     Got the 3.2G RAM problem on my Acer Aspire 5050.  Acer doesn't have a bios to support memory hole on the site, but I'm gonna see if there's one as far as Phoenix is concerned. I'll post back if I find anything.

---

### Post by warpasylum on 2009-04-02
Nope, no love from Acer or Phoenix.  BIOS only sees 3838MB out of 4GB of RAM. No memory remap option, even after updating BIOS.

---

### Post by ahbart on 2009-04-02
> **warpasylum said:**
> Nope, no love from Acer or Phoenix.  BIOS only sees 3838MB out of 4GB of RAM. No memory remap option, even after updating BIOS.

3,8Gb is a lot better than the 3,2 limit. 3838Mb*1024=3,930 (Or 3838*1040=3,992)

---

### Post by ptg on 2009-06-01
&#292;i all

I experiencing the same problem... I recently upgraded my 2gb toshiba to 4gb and Ubuntu (64bit) only detects 2.9gb. I already tried to swap the memory cards without any effect and my bios is updated to the last version. The specifications of the notebook are clear regarding to the support of 4gb ram. The bios is extremely simple and doesn't have options to remap. 
Any solution? 
Thanks!

---

### Post by golden.larch@gmail.com on 2009-06-09
Guys, if you are running a 32bit OS, the chances you are not going to get all 4G memory space.

On a 32bit system, the entire system address space is 2^32 = 4G. System devices (hd, modem, v card, etc.) need some space for traffic. The rest is used up by RAM, which will always be less than 4G.

Upgrade to a 64bit OS is the only solution.

---

### Post by Slim Odds on 2009-06-09
> **golden.larch@gmail.com said:**
> Upgrade to a 64bit OS is the only solution.

The last post mentioned that he is using 64 bit.

For some of the rest of you. The problem is your motherboard. Ubuntu 64 has no problem accessing all available RAM.

If you're getting a lot less then the total you have installed, you need a new motherboard. That's the bottom line.

Here's what I get on my 8G machine....
```
$ free -m
             total       used       free     shared    buffers     cached
Mem:          7991       7855        135          0        268       6042
-/+ buffers/cache:       1543       6447
Swap:         9718          5       9713

```

---

### Post by Youresorock on 2009-06-10
I just ran the same command [free -m] as the previous post and got this:

```
free -m
             total       used       free     shared    buffers     cached
Mem:          7757       7562        195          0         64       5760
-/+ buffers/cache:       1737       6019
Swap:         9703         42       9661
```

Where do you think my missing 435 megs are?  I have 8GB on a 64bit machine, I should get the full 1024 x 8 = 8192 megs, shouldn't I?

---

### Post by Yellow Pasque on 2009-06-10
> Where do you think my missing 435 megs are?
Look at dmesg and find out.

---

### Post by hachaboob on 2009-06-11
Some of your system RAM could be reserved for integrated video.

---

### Post by ptg on 2009-06-12
Hi

Unfortunately I have to agree with Slim Odds... the problem is somewhere in the motherboard! With [free -m] I have obtained this message:

             total       used       free     shared    buffers     cached
Mem:          2982       2684        298          0         71       1980

which is clear about the available RAM. with Dmesg I have this information:

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
[    0.000000] RAMDISK: 3785b000 - 37feff24

with some words like 'corrupt' that I don't like very much... :) And, finally, with lshw I have this:

      *-memory
          description: System Memory
          physical id: 13
          slot: System board or motherboard
          size: 4GiB
        *-bank:0
             description: SODIMM Synchronous
             physical id: 0
             slot: M1
             size: 2GiB
             width: 32 bits
        *-bank:1
             description: SODIMM Synchronous 667 MHz (1.5 ns)
             physical id: 1
             slot: M2
             size: 2GiB
             width: 32 bits
             clock: 667MHz (1.5ns)

that reveals two occupied ram slots with 2Gb each!!! Isn't it stange?

---

### Post by trivialpackets on 2009-06-12
grep MemTotal /proc/meminfo

I like that command when looking into memory issues as well.

---

### Post by iceback on 2009-07-03
Just got a new HP Elitebook 8530w (T9400 cpu,nvida quadro gpu,camera).  I loaded Ubuntu 9.04 desktop 32-bit and I'm seeing (a variation?), on this 4-gets-you-3 problem.

$ uname -a
Linux kuldo 2.6.28-13-generic #45-Ubuntu SMP Tue Jun 30 19:49:51 UTC 2009 i686 GNU/Linux

I'm most confused by the fact that lshw (and mtrr too?) sees all the RAM and /proc/meminfo doesn't come close. Both it and SystemMonitor show just over 3GB, where as lshw recognises the hardware reality.
[INDENT]
$ cat /proc/meminfo | grep MemTotal
MemTotal:        3061312 kB

$ lshw
     *-memory
          description: System Memory
          physical id: 4
          slot: System board or motherboard
          size: 4GiB
$ cat /proc/mtrr
reg00: base=0x0ffe00000 ( 4094MB), size=    2MB, count=1: write-protect
reg01: base=0x000000000 (    0MB), size= 2048MB, count=1: write-back
reg02: base=0x080000000 ( 2048MB), size= 1024MB, count=1: write-back
reg03: base=0x100000000 ( 4096MB), size= 1024MB, count=1: write-back
reg04: base=0x0b9d70000 ( 2973MB), size=   64KB, count=1: uncachable

[/INDENT]

The BIOS access doesn't appear to have any memory remap capability.

High memory kernel options seem to be in order
[INDENT]grep HIGH /boot/config-2.6.28-13-generic 
# CONFIG_DEBUG_HIGHMEM is not set
CONFIG_HIGHMEM=y
CONFIG_HIGHPTE=y
CONFIG_HIGH_RES_TIMERS=y
# CONFIG_NOHIGHMEM is not set
CONFIG_HIGHMEM4G=y
# CONFIG_HIGHMEM64G is not set
[/INDENT]

If any other HP8530 owner has more information, I'm all ears.

---

### Post by giancast on 2009-07-03
Hello I found this and maybe if you redo your numbers it may come closer to what you have. Ubuntu does not count in gygabytes, it counts in gibibytes (GiB). If you look at your System Monitor it does not say 3GB it says 3GiB (at least that is what my system monitor displays).
You may ask what is a Gibibyte well
one GibiByte 	 1 GiB = 2^30 B = 1 073 741 824 B.
I am not saying that there is no problem but the above may explain to some.

I have 4GB of memory but my system monitor says that I have 3.3GiB. If I take 3.3GiB * 1 073 741 824 = 3543348019 B what happened to my 456.6Mb? I think that some of it goes to my video card (I use integrated) but 456Mb?

I have a 1Tb hard drive and it is missing 24Gb, the system monitor shows 907.4GiB.
907.4 * 1 073 741 824 = 974 313 331 097 B 
So something is not right.

---

### Post by iceback on 2009-07-04
> **giancast said:**
> Hello I found this and maybe if you redo your numbers it may come closer to what you have. Ubuntu does not count in gygabytes, it counts in gibibytes (GiB). If you look at your System Monitor it does not say 3GB it says 3GiB (at least that is what my system monitor displays).
You may ask what is a Gibibyte well
one GibiByte 	 1 GiB = 2^30 B = 1 073 741 824 B.
I am not saying that there is no problem but the above may explain to some.

I have 4GB of memory but my system monitor says that I have 3.3GiB. If I take 3.3GiB * 1 073 741 824 = 3543348019 B what happened to my 456.6Mb? I think that some of it goes to my video card (I use integrated) but 456Mb?

I have a 1Tb hard drive and it is missing 24Gb, the system monitor shows 907.4GiB.
907.4 * 1 073 741 824 = 974 313 331 097 B 
So something is not right.

Note that lshw is showing "4GiB".  So there is a difference of opinion between meminfo and lshw.  Is this an ubuntu bug?

---

