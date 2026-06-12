---
title: "Yet another FailedBoot &quot;[   11.292011] ata1 SRST: failed (errno=-16)&quot;  / uuid problem"
date: 2009-06-19
forum: x86 64-bit Users
---

### Post by C0NSTANTIN on 2009-06-19
[   11.292011] ata1 SRST: failed (errno=-16)
[   21.300010] ata1 SRST: failed (errno=-16)
.....
Alert! /dev/disk/by-uuid/<my ST3320620AD's signature ID> not found
Dropping onto a shell


Afterwards my whole HDD is gone under radar from all-linux live CD's

is it an ext4 vs x64 conflict?
is it a compiz/emerald/gDesklets package conflict?

It's the 2nd time i have to run Windows Install CD to format the HDD ....

[[IMG]http://img504.imageshack.us/img504/7731/dsc02135w.th.jpg[/IMG]]("http://img504.imageshack.us/i/dsc02135w.jpg/")

---

### Post by C0NSTANTIN on 2009-06-19
i've organized my thoughts and i think i will eraze the HDD all together and start anew.
once re-installed ... after all the updates i am planning to reboot several times to see if i can upsat linux again ..

i am planning to install fewer libraries for compiz emerald and gdesklets.
i will forget all together about cairo-dock.

and the most important thing i learned while googleing from live CD this session ... is to make a backup of the fstab in case xubuntu is just poized to crash ....

---

### Post by C0NSTANTIN on 2009-06-20
I've booted Windows XP Install CD,
Erased all partitions
Created one big NTFS out of all the HDD
Formated [rough mode]
... went to sleep

Linux still can't see HDD, windows does ...

Here is another photo with more details on the matter ...
[[IMG]http://img301.imageshack.us/img301/4607/dsc00243p.th.jpg[/IMG]](http://img301.imageshack.us/i/dsc00243p.jpg/)

---

### Post by C0NSTANTIN on 2009-06-20
Managed to get someone attention [finally ...] on my other thred ...
[http://ubuntuforums.org/showthread.php?t=1190046](http://ubuntuforums.org/showthread.php?t=1190046)

I was sugested to use the "How To" thred:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

NOT ONE TERMINAL INPUT SESSION I HAVE USED FROM THIS FORUM HAVE WORKED UNTIL THE END FOR ME ...

In this case, i was suggested to use the [Grub Boot Loader]("http://en.wikipedia.org/wiki/GNU_GRUB")

The post was edited, with a list of commandes for the case where "find /boot/grub/stage1 did not worked
I thought i was saved ... [yet..]("http://ubuntuforums.org/showthread.php?p=7488359&posted=1#post7488359")


The Photo i uploaded earlyer prints:

> Boot from (hd0,0) ext4 e957c068-1ffe-4b75-abee-5c6d247bf228
[   11.296011] ata1: SRST failed (errno=-16)
[   21.304010] ata1: SRST failed (errno=-16)
[   56.344010] ata1: SRST failed (errno=-16)
[   61.368010] ata1: SRST failed (errno=-16)
Loading, please wait...
Gave up waiting for root device. Common problems:
 - Boot args (cat /proc/cmdline)
   - Check rootdelay= (did the system wait long enough?)
   - Check root= (did the system wait for the right device?)
 - Missing modules (cat /proc/modules; Is /dev)
ALERT! /dev/disk/by-uuid/e957c068-1ffe-4b75-abee-5c6d247bf228 does not exist. Dr
opping to a shell!

BusyBox v1.10.2 (Ubuntu 1:1.10.2-2ubuntu7) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs) _

Now [any] Linux can't see my HDD even though i have Windows XP / ntfs on it ....  what gives?

---

### Post by C0NSTANTIN on 2009-06-20
I've jus remembered that i had this problems before, some years back when i tried to install Symphony OS... 

I've also noticed that the only thing that made the HDD reusable for Linux doring my experiments was [**Linux Reader**](http://www.downloadsquad.com/2007/12/17/linux-reader-read-linux-files-using-windows) ...

---

### Post by C0NSTANTIN on 2009-06-20
To save you some time ... 

TestDisk doesn't see lost drives ...

[[IMG]http://img37.imageshack.us/img37/82/screenshotwrz.th.png[/IMG]]("http://img37.imageshack.us/i/screenshotwrz.png/")


I don't understand ... i should have had a clean install ... i am not begging the OS to recover lost partitions ... only to see a one partitioned HDD, formatet roughly and windoes xp installed ...
It worked before the format ... what is changed now?!!?!?!? 5 years Linux enigma for me ...

It seames like all i cand do is surf the net with a linux live CD and post some posts that no one can answer ..

---

### Post by C0NSTANTIN on 2009-06-20
no one ??

---

### Post by C0NSTANTIN on 2009-06-20
I am thinking of collecting posts that have similar issues and that warn't answered ...

[http://ubuntuforums.org/showpost.php?p=819512&postcount=1](http://ubuntuforums.org/showpost.php?p=819512&postcount=1)

---

### Post by Endolith on 2009-06-20
This looks like a pretty unusual problem, which is why people don't know how to answer it.  I'm pretty sure this has nothing to do with Compiz or packages.  It's a hardware incompatibility or something.

What is your hardware?  What version of Ubuntu are you using?  Have you tried other Ubuntu versions?  The LiveCD works?  Which LiveCD?

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/220706](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/220706)

---

### Post by C0NSTANTIN on 2009-06-20
> **Endolith said:**
> This looks like a pretty unusual problem, which is why people don't know how to answer it.  I'm pretty sure this has nothing to do with Compiz or packages.  It's a hardware incompatibility or something.

What is your hardware?  What version of Ubuntu are you using?  Have you tried other Ubuntu versions?  The LiveCD works?  Which LiveCD?

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/220706](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/220706)

my hardware is the one in my signature ... 
Intel's [Pentium D945]("http://processorfinder.intel.com/details.aspx?sSpec=SL9QQ")
BFG's [NVIDIA nForce 680i LT SLI]("http://www.nvidia.com/page/nforce_600i_tech_specs.html")
Gainward's [GeForce 9800 GT]("http://www.nvidia.com/object/product_geforce_9800gt_us.html")
2xA-data's [1GB of RAM]("http://www.adata.com.tw/en/product_show.php?ProductNo=AD2800U")
Seagate's [320GB HDD](http://www.pcgarage.ro/hard-disk-uri/seagate/320-gb-barracuda-sata-ii-720010-7200rpm-16mb/)

My version of Ubuntu is Xubuntu 9.04
Live CD's i tried: Symphony OS, Knopix and Xubuntu 9.04, non of witch recognize my HDD.

I fail to understand why is it so... because i've managed to instal Xubuntu on my HDD 2 times ... and have it working for about 2~3 reboots ...

---

### Post by Endolith on 2009-06-20
> **C0NSTANTIN said:**
> 
Live CD's i tried: Symphony OS, Knopix and Xubuntu 9.04, non of witch recognize my HDD.

Have you tried normal Ubuntu?  [System Rescue CD]("http://www.sysresccd.org/Main_Page")?  That's what i usually use to do drive repartitioning, etc.

---

### Post by C0NSTANTIN on 2009-06-20
I will try them now ... and thank you so much for noticing me .... you have no ideea how much it means for my troubled environment .. the pc and the mind ...

---

### Post by C0NSTANTIN on 2009-06-20
Atlast ... some trail of success ...
Tried MHDD 4.6 witch found my HDD :X

I could get it to make the HDD visible for Live CD but at least i have some tools i can handle :X
[although 'makebad' and 'randombad' scared the .. swap out of me :)) ]

I'm going in to test some more commands :p

edit: i've tried almost all functions from all aplications from that cd ...
i just remembered that i made linux see my cd using wubi from windows ...

edit2: OMG!!! that didn't worked either :((((((((
IT'S BEEN 10 DAYS AND I STILL CAN'T RUN LINUX ON THIS MACHINE :(((
linux reader was another tool i used under windows just before my later linus install... i'll try to recover the last partition table that worked, then fresh install...
I'll do some google to see if i can get grub do find /boot/grub/stage1 as instructed in 
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by linux_0 on 2009-06-21
Does the ubuntu live CD work ok on your system?  Have you tried running memtest?  Good luck :)  linux_0

---

### Post by linux_0 on 2009-06-21
What does

```

sudo su -

fdisk -l

```

show?

Good luck :smile:  linux_0

---

### Post by C0NSTANTIN on 2009-06-21
> **linux_0 said:**
> What does

```

sudo su -

fdisk -l

```show?

Good luck :smile:  linux_0


10x ... i've tried them and this is what i got ...

```
To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ sudo su -
root@ubuntu:~# fdisk -l
root@ubuntu:~# fdisk -l
root@ubuntu:~# 



```



> **linux_0 said:**
> Does the ubuntu live CD work ok on your system?  Have you tried running memtest?  Good luck :)  linux_0

I am now using the live CD to acces ubuntuforums.org ....

---

### Post by linux_0 on 2009-06-21
Please PM me the output of

```

sudo su -

lspci

dmesg


```

:) linux_0

---

### Post by C0NSTANTIN on 2009-06-21
They didn't fit into a message .. 
here are the outputs ...

```
**ubuntu@ubuntu:~$ sudo su -**
**root@ubuntu:~# lspci**
00:00.0 Host bridge: nVidia Corporation C55 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.3 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.4 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.5 RAM memory: nVidia Corporation C55 Memory Controller (rev a2)
00:00.6 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.7 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.0 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.1 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.3 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.4 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.5 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.6 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:02.0 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:02.1 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:02.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:03.0 PCI bridge: nVidia Corporation C55 PCI Express bridge (rev a1)
00:09.0 RAM memory: nVidia Corporation MCP55 Memory Controller (rev a1)
00:0a.0 ISA bridge: nVidia Corporation MCP55 LPC Bridge (rev a2)
00:0a.1 SMBus: nVidia Corporation MCP55 SMBus (rev a2)
00:0b.0 USB Controller: nVidia Corporation MCP55 USB Controller (rev a1)
00:0b.1 USB Controller: nVidia Corporation MCP55 USB Controller (rev a2)
00:0d.0 IDE interface: nVidia Corporation MCP55 IDE (rev a1)
00:0e.0 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a2)
00:0e.1 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a2)
00:0e.2 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a2)
00:0f.0 PCI bridge: nVidia Corporation MCP55 PCI bridge (rev a2)
00:0f.1 Audio device: nVidia Corporation MCP55 High Definition Audio (rev a2)
00:11.0 Bridge: nVidia Corporation MCP55 Ethernet (rev a2)
00:12.0 Bridge: nVidia Corporation MCP55 Ethernet (rev a2)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 9800 GT (rev a2)
02:07.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
**root@ubuntu:~# dmesg**
[    0.000000] BIOS EBDA/lowmem at: 0009f000/0009f000
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.28-11-generic (buildd@crested) (gcc version 4.3.3 (Ubuntu 4.3.3-5ubuntu4) ) #42-Ubuntu SMP Fri Apr 17 01:58:03 UTC 2009 (Ubuntu 2.6.28-11.42-generic)
[    0.000000] Command line: BOOT_IMAGE=/casper/vmlinuz file=/cdrom/preseed/xubuntu.seed boot=casper initrd=/casper/initrd.gz quiet splash --
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
[    0.000000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007fef0000 (usable)
[    0.000000]  BIOS-e820: 000000007fef0000 - 000000007fef3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007fef3000 - 000000007ff00000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000d0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000] DMI 2.4 present.
[    0.000000] Phoenix BIOS detected: BIOS may corrupt low RAM, working it around.
[    0.000000] last_pfn = 0x7fef0 max_arch_pfn = 0x3ffffffff
[    0.000000] Scanning 0 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 000000000009f000 (usable)
[    0.000000]  modified: 000000000009f000 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 000000007fef0000 (usable)
[    0.000000]  modified: 000000007fef0000 - 000000007fef3000 (ACPI NVS)
[    0.000000]  modified: 000000007fef3000 - 000000007ff00000 (ACPI data)
[    0.000000]  modified: 00000000d0000000 - 00000000f0000000 (reserved)
[    0.000000]  modified: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000] init_memory_mapping: 0000000000000000-000000007fef0000
[    0.000000]  0000000000 - 007fe00000 page 2M
[    0.000000]  007fe00000 - 007fef0000 page 4k
[    0.000000] kernel direct mapping tables up to 7fef0000 @ 10000-14000
[    0.000000] last_map_addr: 7fef0000 end: 7fef0000
[    0.000000] RAMDISK: 7f6e9000 - 7febf44d
[    0.000000] ACPI: RSDP 000F7F30, 0014 (r0 Nvidia)
[    0.000000] ACPI: RSDT 7FEF3040, 0038 (r1 Nvidia NVDAACPI 42302E31 NVDA        0)
[    0.000000] ACPI: FACP 7FEF30C0, 0074 (r1 Nvidia NVDAACPI 42302E31 NVDA        0)
[    0.000000] ACPI: DSDT 7FEF3180, 5349 (r1 NVIDIA NVDAACPI     1000 MSFT  3000000)
[    0.000000] ACPI: FACS 7FEF0000, 0040
[    0.000000] ACPI: HPET 7FEF8640, 003C (r1 Nvidia NVDAACPI 42302E31 NVDA        0)
[    0.000000] ACPI: WDRT 7FEF86C0, 0047 (r1 Nvidia NVDAACPI 42302E31 NVDA        0)
[    0.000000] ACPI: MCFG 7FEF8780, 003C (r1 Nvidia NVDAACPI 42302E31 NVDA        0)
[    0.000000] ACPI: APIC 7FEF8540, 0098 (r1 Nvidia NVDAACPI 42302E31 NVDA        0)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] (6 early reservations) ==> bootmem [0000000000 - 007fef0000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000006000 - 0000008000]       TRAMPOLINE ==> [0000006000 - 0000008000]
[    0.000000]   #2 [0000200000 - 0000b854b0]    TEXT DATA BSS ==> [0000200000 - 0000b854b0]
[    0.000000]   #3 [007f6e9000 - 007febf44d]          RAMDISK ==> [007f6e9000 - 007febf44d]
[    0.000000]   #4 [000009f000 - 0000100000]    BIOS reserved ==> [000009f000 - 0000100000]
[    0.000000]   #5 [0000010000 - 0000012000]          PGTABLE ==> [0000010000 - 0000012000]
[    0.000000] found SMP MP-table at [ffff8800000f3f60] 000f3f60
[    0.000000]  [ffffe20000000000-ffffe20001bfffff] PMD -> [ffff880001200000-ffff880002dfffff] on node 0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   0x00100000 -> 0x00100000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0007fef0
[    0.000000] On node 0 totalpages: 523903
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 2541 pages reserved
[    0.000000]   DMA zone: 1386 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 7109 pages used for memmap
[    0.000000]   DMA32 zone: 512811 pages, LIFO batch:31
[    0.000000]   Normal zone: 0 pages used for memmap
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x03] disabled)
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
[    0.000000] ACPI: HPET timers must be located in memory.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
[    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 80000000 (gap: 7ff00000:50100000)
[    0.000000] PERCPU: Allocating 69632 bytes of per cpu data
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 4, nr_node_ids 1
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 514197
[    0.000000] Kernel command line: BOOT_IMAGE=/casper/vmlinuz file=/cdrom/preseed/xubuntu.seed boot=casper initrd=/casper/initrd.gz quiet splash --
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 3399.691 MHz processor.
[    0.004000] spurious 8259A interrupt: IRQ7.
[    0.004000] Console: colour VGA+ 80x25
[    0.004000] console [tty0] enabled
[    0.004000] Dentry cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.004000] Inode-cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.004000] allocated 20971520 bytes of page_cgroup
[    0.004000] please try cgroup_disable=memory option if you don't want
[    0.004000] Scanning for low memory corruption every 60 seconds
[    0.004000] Checking aperture...
[    0.004000] No AGP bridge found
[    0.004000] Calgary: detecting Calgary via BIOS EBDA area
[    0.004000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.004000] Memory: 2024460k/2096064k available (4760k kernel code, 452k absent, 70416k reserved, 2540k data, 536k init)
[    0.004000] SLUB: Genslabs=12, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.004010] Calibrating delay loop (skipped), value calculated using timer frequency.. 6799.38 BogoMIPS (lpj=13598764)
[    0.004033] Security Framework initialized
[    0.004039] SELinux:  Disabled at boot.
[    0.004056] AppArmor: AppArmor initialized
[    0.004066] Mount-cache hash table entries: 256
[    0.004221] Initializing cgroup subsys ns
[    0.004225] Initializing cgroup subsys cpuacct
[    0.004228] Initializing cgroup subsys memory
[    0.004233] Initializing cgroup subsys freezer
[    0.004251] CPU: Trace cache: 12K uops, L1 D cache: 16K
[    0.004253] CPU: L2 cache: 2048K
[    0.004256] CPU: Physical Processor ID: 0
[    0.004258] CPU: Processor Core ID: 0
[    0.004261] using mwait in idle threads.
[    0.006611] ACPI: Core revision 20080926
[    0.008683] ACPI: Checking initramfs for custom DSDT
[    0.304051] Setting APIC routing to flat
[    0.304551] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.344341] CPU0: Intel(R) Pentium(R) D CPU 3.40GHz stepping 04
[    0.348001] Booting processor 1 APIC 0x1 ip 0x6000
[    0.004000] Initializing CPU#1
[    0.004000] Calibrating delay using timer specific routine.. 6800.36 BogoMIPS (lpj=13600727)
[    0.004000] CPU: Trace cache: 12K uops, L1 D cache: 16K
[    0.004000] CPU: L2 cache: 2048K
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 1
[    0.432428] CPU1: Intel(R) Pentium(R) D CPU 3.40GHz stepping 04
[    0.432457] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.436029] Brought up 2 CPUs
[    0.436032] Total of 2 processors activated (13599.74 BogoMIPS).
[    0.436107] CPU0 attaching sched-domain:
[    0.436110]  domain 0: span 0-1 level CPU
[    0.436113]   groups: 0 1
[    0.436119] CPU1 attaching sched-domain:
[    0.436120]  domain 0: span 0-1 level CPU
[    0.436123]   groups: 1 0
[    0.436180] net_namespace: 1400 bytes
[    0.436180] Booting paravirtualized kernel on bare hardware
[    0.436282] Time: 11:32:02  Date: 06/21/09
[    0.436282] regulator: core version 0.5
[    0.436282] NET: Registered protocol family 16
[    0.436282] ACPI: bus type pci registered
[    0.436282] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.436282] PCI: MCFG area at e0000000 reserved in E820
[    0.449687] PCI: Using MMCONFIG at e0000000 - efffffff
[    0.449690] PCI: Using configuration type 1 for base access
[    0.450488] ACPI: EC: Look up EC in DSDT
[    0.461946] ACPI: Interpreter enabled
[    0.461950] ACPI: (supports S0 S1 S3 S4 S5)
[    0.461980] ACPI: Using IOAPIC for interrupt routing
[    0.472626] ACPI: No dock devices found.
[    0.472643] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.473540] pci 0000:00:03.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.473544] pci 0000:00:03.0: PME# disabled
[    0.473717] pci 0000:00:0a.0: reg 10 io port: [0xfc00-0xfc7f]
[    0.473741] HPET not enabled in BIOS. You might try hpet=force boot option
[    0.473775] pci 0000:00:0a.1: reg 10 io port: [0xf800-0xf83f]
[    0.473792] pci 0000:00:0a.1: reg 20 io port: [0xf400-0xf43f]
[    0.473798] pci 0000:00:0a.1: reg 24 io port: [0xf000-0xf03f]
[    0.473813] pci 0000:00:0a.1: PME# supported from D3hot D3cold
[    0.473819] pci 0000:00:0a.1: PME# disabled
[    0.473855] pci 0000:00:0b.0: reg 10 32bit mmio: [0xcffff000-0xcfffffff]
[    0.473883] pci 0000:00:0b.0: supports D1 D2
[    0.473885] pci 0000:00:0b.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.473889] pci 0000:00:0b.0: PME# disabled
[    0.473920] pci 0000:00:0b.1: reg 10 32bit mmio: [0xcfffe000-0xcfffe0ff]
[    0.473949] pci 0000:00:0b.1: supports D1 D2
[    0.473951] pci 0000:00:0b.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.473954] pci 0000:00:0b.1: PME# disabled
[    0.474000] pci 0000:00:0d.0: reg 20 io port: [0xec00-0xec0f]
[    0.474046] pci 0000:00:0e.0: reg 10 io port: [0x9f0-0x9f7]
[    0.474051] pci 0000:00:0e.0: reg 14 io port: [0xbf0-0xbf3]
[    0.474056] pci 0000:00:0e.0: reg 18 io port: [0x970-0x977]
[    0.474061] pci 0000:00:0e.0: reg 1c io port: [0xb70-0xb73]
[    0.474067] pci 0000:00:0e.0: reg 20 io port: [0xd800-0xd80f]
[    0.474072] pci 0000:00:0e.0: reg 24 32bit mmio: [0xcfffd000-0xcfffdfff]
[    0.474118] pci 0000:00:0e.1: reg 10 io port: [0x9e0-0x9e7]
[    0.474123] pci 0000:00:0e.1: reg 14 io port: [0xbe0-0xbe3]
[    0.474128] pci 0000:00:0e.1: reg 18 io port: [0x960-0x967]
[    0.474133] pci 0000:00:0e.1: reg 1c io port: [0xb60-0xb63]
[    0.474138] pci 0000:00:0e.1: reg 20 io port: [0xc400-0xc40f]
[    0.474144] pci 0000:00:0e.1: reg 24 32bit mmio: [0xcfffc000-0xcfffcfff]
[    0.474190] pci 0000:00:0e.2: reg 10 io port: [0xc000-0xc007]
[    0.474195] pci 0000:00:0e.2: reg 14 io port: [0xbc00-0xbc03]
[    0.474200] pci 0000:00:0e.2: reg 18 io port: [0xb800-0xb807]
[    0.474205] pci 0000:00:0e.2: reg 1c io port: [0xb400-0xb403]
[    0.474211] pci 0000:00:0e.2: reg 20 io port: [0xb000-0xb00f]
[    0.474216] pci 0000:00:0e.2: reg 24 32bit mmio: [0xcfffb000-0xcfffbfff]
[    0.474307] pci 0000:00:0f.1: reg 10 32bit mmio: [0xcfff0000-0xcfff3fff]
[    0.474335] pci 0000:00:0f.1: PME# supported from D3hot D3cold
[    0.474339] pci 0000:00:0f.1: PME# disabled
[    0.474394] pci 0000:00:11.0: reg 10 32bit mmio: [0xcfffa000-0xcfffafff]
[    0.474399] pci 0000:00:11.0: reg 14 io port: [0xac00-0xac07]
[    0.474405] pci 0000:00:11.0: reg 18 32bit mmio: [0xcfff9000-0xcfff90ff]
[    0.474410] pci 0000:00:11.0: reg 1c 32bit mmio: [0xcfff8000-0xcfff800f]
[    0.474428] pci 0000:00:11.0: supports D1 D2
[    0.474430] pci 0000:00:11.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.474435] pci 0000:00:11.0: PME# disabled
[    0.474484] pci 0000:00:12.0: reg 10 32bit mmio: [0xcfff7000-0xcfff7fff]
[    0.474489] pci 0000:00:12.0: reg 14 io port: [0xa800-0xa807]
[    0.474494] pci 0000:00:12.0: reg 18 32bit mmio: [0xcfff6000-0xcfff60ff]
[    0.474499] pci 0000:00:12.0: reg 1c 32bit mmio: [0xcfff5000-0xcfff500f]
[    0.474518] pci 0000:00:12.0: supports D1 D2
[    0.474519] pci 0000:00:12.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.474524] pci 0000:00:12.0: PME# disabled
[    0.474580] pci 0000:01:00.0: reg 10 32bit mmio: [0xcc000000-0xccffffff]
[    0.474589] pci 0000:01:00.0: reg 14 64bit mmio: [0xb0000000-0xbfffffff]
[    0.474599] pci 0000:01:00.0: reg 1c 64bit mmio: [0xca000000-0xcbffffff]
[    0.474605] pci 0000:01:00.0: reg 24 io port: [0x9c00-0x9c7f]
[    0.474610] pci 0000:01:00.0: reg 30 32bit mmio: [0x000000-0x01ffff]
[    0.474667] pci 0000:00:03.0: bridge io port: [0x9000-0x9fff]
[    0.474670] pci 0000:00:03.0: bridge 32bit mmio: [0xca000000-0xcdffffff]
[    0.474675] pci 0000:00:03.0: bridge 64bit mmio pref: [0xb0000000-0xbfffffff]
[    0.474718] pci 0000:02:07.0: reg 10 32bit mmio: [0xcfdff000-0xcfdff7ff]
[    0.474724] pci 0000:02:07.0: reg 14 32bit mmio: [0xcfdf8000-0xcfdfbfff]
[    0.474756] pci 0000:02:07.0: supports D1 D2
[    0.474758] pci 0000:02:07.0: PME# supported from D0 D1 D2 D3hot
[    0.474762] pci 0000:02:07.0: PME# disabled
[    0.474796] pci 0000:00:0f.0: transparent bridge
[    0.474800] pci 0000:00:0f.0: bridge io port: [0x8000-0x8fff]
[    0.474803] pci 0000:00:0f.0: bridge 32bit mmio: [0xcfd00000-0xcfdfffff]
[    0.474807] pci 0000:00:0f.0: bridge 32bit mmio pref: [0xcfe00000-0xcfefffff]
[    0.474816] bus 00 -> node 0
[    0.474825] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.475530] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[    0.475642] ACPI Warning (nspredef-0858): \_SB_.PCI0.HUB0._PRT: Return Package type mismatch at index 2 - found [NULL Object Descriptor], expected Integer/Reference [20080926]
[    0.563423] ACPI: PCI Interrupt Link [LNK1] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.563638] ACPI: PCI Interrupt Link [LNK2] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.563850] ACPI: PCI Interrupt Link [LNK3] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.564069] ACPI: PCI Interrupt Link [LNK4] (IRQs 5 7 9 *10 11 14 15)
[    0.564281] ACPI: PCI Interrupt Link [LXV5] (IRQs 5 7 9 *10 11 14 15)
[    0.564493] ACPI: PCI Interrupt Link [LXV6] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.564704] ACPI: PCI Interrupt Link [LXV7] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.564915] ACPI: PCI Interrupt Link [LXV8] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.565124] ACPI: PCI Interrupt Link [LUBA] (IRQs 5 7 9 *10 11 14 15)
[    0.565333] ACPI: PCI Interrupt Link [LMC1] (IRQs *5 7 9 10 11 14 15)
[    0.565541] ACPI: PCI Interrupt Link [LMAC] (IRQs *5 7 9 10 11 14 15)
[    0.565756] ACPI: PCI Interrupt Link [LAZA] (IRQs 5 7 9 10 *11 14 15)
[    0.565965] ACPI: PCI Interrupt Link [LSMB] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.566175] ACPI: PCI Interrupt Link [LUB2] (IRQs 5 7 9 10 *11 14 15)
[    0.566385] ACPI: PCI Interrupt Link [LIDE] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.566594] ACPI: PCI Interrupt Link [LSA0] (IRQs 5 7 9 10 *11 14 15)
[    0.566801] ACPI: PCI Interrupt Link [LSA1] (IRQs 5 7 9 10 *11 14 15)
[    0.567014] ACPI: PCI Interrupt Link [LSA2] (IRQs 5 7 9 *10 11 14 15)
[    0.567288] ACPI: PCI Interrupt Link [APC1] (IRQs 16) *0, disabled.
[    0.567546] ACPI: PCI Interrupt Link [APC2] (IRQs 17) *0, disabled.
[    0.567804] ACPI: PCI Interrupt Link [APC3] (IRQs 18) *0, disabled.
[    0.568065] ACPI: PCI Interrupt Link [APC4] (IRQs 19) *0
[    0.568320] ACPI: PCI Interrupt Link [AXV5] (IRQs 16) *0
[    0.568575] ACPI: PCI Interrupt Link [AXV6] (IRQs 16) *0, disabled.
[    0.568829] ACPI: PCI Interrupt Link [AXV7] (IRQs 16) *0, disabled.
[    0.569084] ACPI: PCI Interrupt Link [AXV8] (IRQs 16) *0, disabled.
[    0.569341] ACPI: PCI Interrupt Link [AUBA] (IRQs 20 21 22 23) *0
[    0.569600] ACPI: PCI Interrupt Link [AMA1] (IRQs 20 21 22 23) *0
[    0.569856] ACPI: PCI Interrupt Link [AMAC] (IRQs 20 21 22 23) *0
[    0.570111] ACPI: PCI Interrupt Link [AAZA] (IRQs 20 21 22 23) *0
[    0.570365] ACPI: PCI Interrupt Link [AACI] (IRQs 20 21 22 23) *0, disabled.
[    0.570620] ACPI: PCI Interrupt Link [AMCI] (IRQs 20 21 22 23) *0, disabled.
[    0.570874] ACPI: PCI Interrupt Link [ASMB] (IRQs 20 21 22 23) *0, disabled.
[    0.571129] ACPI: PCI Interrupt Link [AUS2] (IRQs 20 21 22 23) *0
[    0.571385] ACPI: PCI Interrupt Link [AIDE] (IRQs 20 21 22 23) *0, disabled.
[    0.571640] ACPI: PCI Interrupt Link [ASA0] (IRQs 20 21 22 23) *0
[    0.571903] ACPI: PCI Interrupt Link [ASA1] (IRQs 20 21 22 23) *0
[    0.572165] ACPI: PCI Interrupt Link [ASA2] (IRQs 20 21 22 23) *0
[    0.572343] ACPI: WMI: Mapper loaded
[    0.572402] SCSI subsystem initialized
[    0.572402] libata version 3.00 loaded.
[    0.572402] usbcore: registered new interface driver usbfs
[    0.572402] usbcore: registered new interface driver hub
[    0.572402] usbcore: registered new device driver usb
[    0.572402] PCI: Using ACPI for IRQ routing
[    0.584015] Bluetooth: Core ver 2.13
[    0.584035] NET: Registered protocol family 31
[    0.584035] Bluetooth: HCI device and connection manager initialized
[    0.584035] Bluetooth: HCI socket layer initialized
[    0.584035] NET: Registered protocol family 8
[    0.584035] NET: Registered protocol family 20
[    0.584039] NetLabel: Initializing
[    0.584041] NetLabel:  domain hash size = 128
[    0.584043] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.584069] NetLabel:  unlabeled traffic allowed by default
[    0.584176] AppArmor: AppArmor Filesystem Enabled
[    0.596016] pnp: PnP ACPI init
[    0.596031] ACPI: bus type pnp registered
[    0.600967] pnp: PnP ACPI: found 14 devices
[    0.600970] ACPI: ACPI bus type pnp unregistered
[    0.600979] system 00:00: ioport range 0x1000-0x107f has been reserved
[    0.600983] system 00:00: ioport range 0x1080-0x10ff has been reserved
[    0.600985] system 00:00: ioport range 0x1400-0x147f has been reserved
[    0.600987] system 00:00: ioport range 0x1480-0x14ff has been reserved
[    0.600990] system 00:00: ioport range 0x1800-0x187f has been reserved
[    0.600992] system 00:00: ioport range 0x1880-0x18ff has been reserved
[    0.601000] system 00:02: ioport range 0x4d0-0x4d1 has been reserved
[    0.601002] system 00:02: ioport range 0x295-0x314 has been reserved
[    0.601005] system 00:02: ioport range 0x880-0x88f has been reserved
[    0.601014] system 00:0c: iomem range 0xe0000000-0xefffffff has been reserved
[    0.601020] system 00:0d: iomem range 0xd0000-0xd3fff has been reserved
[    0.601022] system 00:0d: iomem range 0xd5800-0xd7fff has been reserved
[    0.601025] system 00:0d: iomem range 0xf0000-0xfbfff could not be reserved
[    0.601027] system 00:0d: iomem range 0xfc000-0xfffff could not be reserved
[    0.601030] system 00:0d: iomem range 0x7fef0000-0x7fefffff could not be reserved
[    0.601033] system 00:0d: iomem range 0xffff0000-0xffffffff has been reserved
[    0.601035] system 00:0d: iomem range 0x0-0x9ffff could not be reserved
[    0.601038] system 00:0d: iomem range 0x100000-0x7feeffff could not be reserved
[    0.601040] system 00:0d: iomem range 0xfec00000-0xfec00fff has been reserved
[    0.601043] system 00:0d: iomem range 0xd0000000-0xdfffffff has been reserved
[    0.601046] system 00:0d: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.601048] system 00:0d: iomem range 0xfeff0000-0xfeff0000 has been reserved
[    0.605761] pci 0000:00:03.0: PCI bridge, secondary bus 0000:01
[    0.605765] pci 0000:00:03.0:   IO window: 0x9000-0x9fff
[    0.605769] pci 0000:00:03.0:   MEM window: 0xca000000-0xcdffffff
[    0.605773] pci 0000:00:03.0:   PREFETCH window: 0x000000b0000000-0x000000bfffffff
[    0.605778] pci 0000:00:0f.0: PCI bridge, secondary bus 0000:02
[    0.605781] pci 0000:00:0f.0:   IO window: 0x8000-0x8fff
[    0.605785] pci 0000:00:0f.0:   MEM window: 0xcfd00000-0xcfdfffff
[    0.605788] pci 0000:00:0f.0:   PREFETCH window: 0x000000cfe00000-0x000000cfefffff
[    0.605800] pci 0000:00:03.0: setting latency timer to 64
[    0.605806] pci 0000:00:0f.0: setting latency timer to 64
[    0.605810] bus: 00 index 0 io port: [0x00-0xffff]
[    0.605812] bus: 00 index 1 mmio: [0x000000-0xffffffffffffffff]
[    0.605815] bus: 01 index 0 io port: [0x9000-0x9fff]
[    0.605817] bus: 01 index 1 mmio: [0xca000000-0xcdffffff]
[    0.605819] bus: 01 index 2 mmio: [0xb0000000-0xbfffffff]
[    0.605821] bus: 01 index 3 mmio: [0x0-0x0]
[    0.605823] bus: 02 index 0 io port: [0x8000-0x8fff]
[    0.605825] bus: 02 index 1 mmio: [0xcfd00000-0xcfdfffff]
[    0.605826] bus: 02 index 2 mmio: [0xcfe00000-0xcfefffff]
[    0.605828] bus: 02 index 3 io port: [0x00-0xffff]
[    0.605830] bus: 02 index 4 mmio: [0x000000-0xffffffffffffffff]
[    0.605841] NET: Registered protocol family 2
[    0.640094] IP route cache hash table entries: 65536 (order: 7, 524288 bytes)
[    0.640471] TCP established hash table entries: 262144 (order: 10, 4194304 bytes)
[    0.642122] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.642576] TCP: Hash tables configured (established 262144 bind 65536)
[    0.642579] TCP reno registered
[    0.652153] NET: Registered protocol family 1
[    0.652290] checking if image is initramfs... it is
[    1.104468] Switched to high resolution mode on CPU 1
[    1.108085] Switched to high resolution mode on CPU 0
[    1.252051] Freeing initrd memory: 8025k freed
[    1.256235] audit: initializing netlink socket (disabled)
[    1.256252] type=2000 audit(1245583922.252:1): initialized
[    1.262613] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    1.263942] VFS: Disk quotas dquot_6.5.1
[    1.264024] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    1.264707] fuse init (API version 7.10)
[    1.264828] msgmni has been set to 3971
[    1.265070] alg: No test for stdrng (krng)
[    1.265088] io scheduler noop registered
[    1.265091] io scheduler anticipatory registered
[    1.265094] io scheduler deadline registered
[    1.265156] io scheduler cfq registered (default)
[    1.265343] pci 0000:00:03.0: Disabling HT MSI mapping<6>pci 0000:00:0e.0: Disabling HT MSI mapping<6>pci 0000:00:0e.1: Disabling HT MSI mapping<6>pci 0000:00:0e.2: Disabling HT MSI mapping<6>pci 0000:00:0f.0: Disabling HT MSI mapping<6>pci 0000:00:0f.1: Disabling HT MSI mapping<6>pci 0000:00:11.0: Disabling HT MSI mapping<6>pci 0000:00:12.0: Disabling HT MSI mapping<7>pci 0000:01:00.0: Boot video device
[    1.287014] pcieport-driver 0000:00:03.0: setting latency timer to 64
[    1.287055] pcieport-driver 0000:00:03.0: found MSI capability
[    1.287080] pcieport-driver 0000:00:03.0: irq 2303 for MSI/MSI-X
[    1.287090] pci_express 0000:00:03.0:pcie00: allocate port service
[    1.287106] pci_express 0000:00:03.0:pcie03: allocate port service
[    1.287169] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.287180] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.287336] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    1.287339] ACPI: Power Button (FF) [PWRF]
[    1.287384] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    1.287386] ACPI: Power Button (CM) [PWRB]
[    1.287912] processor ACPI_CPU:00: registered as cooling_device0
[    1.287918] ACPI: Processor [CPU0] (supports 8 throttling states)
[    1.287980] processor ACPI_CPU:01: registered as cooling_device1
[    1.320236] hpet_acpi_add: no address or irqs in _CRS
[    1.320257] Linux agpgart interface v0.103
[    1.320266] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    1.320370] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.320701] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.321504] brd: module loaded
[    1.321848] loop: module loaded
[    1.321917] Fixed MDIO Bus: probed
[    1.321923] PPP generic driver version 2.4.2
[    1.321981] input: Macintosh mouse button emulation as /devices/virtual/input/input2
[    1.322011] Driver 'sd' needs updating - please use bus_type methods
[    1.322023] Driver 'sr' needs updating - please use bus_type methods
[    1.322251] sata_nv 0000:00:0e.0: version 3.5
[    1.322663] ACPI: PCI Interrupt Link [ASA0] enabled at IRQ 23
[    1.322672] sata_nv 0000:00:0e.0: PCI INT A -> Link[ASA0] -> GSI 23 (level, low) -> IRQ 23
[    1.322675] sata_nv 0000:00:0e.0: Using SWNCQ mode
[    1.322884] sata_nv 0000:00:0e.0: setting latency timer to 64
[    1.323035] scsi0 : sata_nv
[    1.323155] scsi1 : sata_nv
[    1.323370] ata1: SATA max UDMA/133 cmd 0x9f0 ctl 0xbf0 bmdma 0xd800 irq 23
[    1.323374] ata2: SATA max UDMA/133 cmd 0x970 ctl 0xb70 bmdma 0xd808 irq 23
[    2.054520] ata1: SATA link down (SStatus 0 SControl 300)
[    7.972015] ata2: link is slow to respond, please be patient (ready=-19)
[COLOR=Red][   12.060015] ata2: SRST failed (errno=-16)[/COLOR]
[   12.060092] ata2: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[   12.060099] ata2: link online but device misclassified, retrying
[   17.980014] ata2: link is slow to respond, please be patient (ready=-19)
[COLOR=Red][   22.068014] ata2: SRST failed (errno=-16)[/COLOR]
[   22.068088] ata2: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[   22.068094] ata2: link online but device misclassified, retrying
[   27.988014] ata2: link is slow to respond, please be patient (ready=-19)
[[COLOR=Red]   57.108511] ata2: SRST failed (errno=-16)[/COLOR]
[   57.108585] ata2: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[   57.108591] ata2: link online but device misclassified, retrying
[   57.108594] ata2: limiting SATA link speed to 1.5 Gbps
[COLOR=Red][   62.132012] ata2: SRST failed (errno=-16)[/COLOR]
[   62.132086] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[   62.132092] ata2: link online but device misclassified, device detection might fail
[   62.132516] ACPI: PCI Interrupt Link [ASA1] enabled at IRQ 22
[   62.132522] sata_nv 0000:00:0e.1: PCI INT B -> Link[ASA1] -> GSI 22 (level, low) -> IRQ 22
[   62.132525] sata_nv 0000:00:0e.1: Using SWNCQ mode
[   62.132726] sata_nv 0000:00:0e.1: setting latency timer to 64
[   62.132853] scsi2 : sata_nv
[   62.132944] scsi3 : sata_nv
[   62.133127] ata3: SATA max UDMA/133 cmd 0x9e0 ctl 0xbe0 bmdma 0xc400 irq 22
[   62.133130] ata4: SATA max UDMA/133 cmd 0x960 ctl 0xb60 bmdma 0xc408 irq 22
[   62.866520] ata3: SATA link down (SStatus 0 SControl 300)
[   63.598508] ata4: SATA link down (SStatus 0 SControl 300)
[   63.598933] ACPI: PCI Interrupt Link [ASA2] enabled at IRQ 21
[   63.598938] sata_nv 0000:00:0e.2: PCI INT C -> Link[ASA2] -> GSI 21 (level, low) -> IRQ 21
[   63.598940] sata_nv 0000:00:0e.2: Using SWNCQ mode
[   63.599144] sata_nv 0000:00:0e.2: setting latency timer to 64
[   63.599251] scsi4 : sata_nv
[   63.599309] scsi5 : sata_nv
[   63.599482] ata5: SATA max UDMA/133 cmd 0xc000 ctl 0xbc00 bmdma 0xb000 irq 21
[   63.599485] ata6: SATA max UDMA/133 cmd 0xb800 ctl 0xb400 bmdma 0xb008 irq 21
[   64.330510] ata5: SATA link down (SStatus 0 SControl 300)
[   65.062506] ata6: SATA link down (SStatus 0 SControl 300)
[   65.062613] pata_amd 0000:00:0d.0: version 0.3.10
[   65.062647] pata_amd 0000:00:0d.0: setting latency timer to 64
[   65.062726] scsi6 : pata_amd
[   65.062811] scsi7 : pata_amd
[   65.063611] ata7: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xec00 irq 14
[   65.063614] ata8: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xec08 irq 15
[   65.240297] ata7.00: ATAPI: TEAC DV-W516GDM, M4S2, max UDMA/66
[   65.240315] ata7: nv_mode_filter: 0x1f39f&0x1f01f->0x1f01f, BIOS=0x1f000 (0xc5000000) ACPI=0x1f01f (30:600:0x13)
[   65.240317] ata7.00: limited to UDMA/33 due to 40-wire cable
[   65.272241] ata7.00: configured for UDMA/33
[   65.272731] ata8: port disabled. ignoring.
[   65.272774] isa bounce pool size: 16 pages
[   65.273593] scsi 6:0:0:0: CD-ROM            TEAC     DV-W516GDM       M4S2 PQ: 0 ANSI: 5
[   65.277190] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[   65.277195] Uniform CD-ROM driver Revision: 3.20
[   65.277306] sr 6:0:0:0: Attached scsi CD-ROM sr0
[   65.277351] sr 6:0:0:0: Attached scsi generic sg0 type 5
[   65.277881] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[   65.278303] ACPI: PCI Interrupt Link [AUS2] enabled at IRQ 20
[   65.278308] ehci_hcd 0000:00:0b.1: PCI INT B -> Link[AUS2] -> GSI 20 (level, low) -> IRQ 20
[   65.278320] ehci_hcd 0000:00:0b.1: setting latency timer to 64
[   65.278324] ehci_hcd 0000:00:0b.1: EHCI Host Controller
[   65.278392] ehci_hcd 0000:00:0b.1: new USB bus registered, assigned bus number 1
[   65.278422] ehci_hcd 0000:00:0b.1: debug port 1
[   65.278427] ehci_hcd 0000:00:0b.1: cache line size of 128 is not supported
[   65.278442] ehci_hcd 0000:00:0b.1: irq 20, io mem 0xcfffe000
[   65.288021] ehci_hcd 0000:00:0b.1: USB 2.0 started, EHCI 1.00
[   65.288108] usb usb1: configuration #1 chosen from 1 choice
[   65.288136] hub 1-0:1.0: USB hub found
[   65.288144] hub 1-0:1.0: 10 ports detected
[   65.288257] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[   65.288672] ACPI: PCI Interrupt Link [AUBA] enabled at IRQ 23
[   65.288676] ohci_hcd 0000:00:0b.0: PCI INT A -> Link[AUBA] -> GSI 23 (level, low) -> IRQ 23
[   65.288686] ohci_hcd 0000:00:0b.0: setting latency timer to 64
[   65.288689] ohci_hcd 0000:00:0b.0: OHCI Host Controller
[   65.288738] ohci_hcd 0000:00:0b.0: new USB bus registered, assigned bus number 2
[   65.288751] ohci_hcd 0000:00:0b.0: irq 23, io mem 0xcffff000
[   65.346062] usb usb2: configuration #1 chosen from 1 choice
[   65.346088] hub 2-0:1.0: USB hub found
[   65.346098] hub 2-0:1.0: 10 ports detected
[   65.346198] uhci_hcd: USB Universal Host Controller Interface driver
[   65.346255] usbcore: registered new interface driver libusual
[   65.346290] usbcore: registered new interface driver usbserial
[   65.346301] USB Serial support registered for generic
[   65.346315] usbcore: registered new interface driver usbserial_generic
[   65.346317] usbserial: USB Serial Driver core
[   65.346366] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   65.349048] serio: i8042 KBD port at 0x60,0x64 irq 1
[   65.349054] serio: i8042 AUX port at 0x60,0x64 irq 12
[   65.360055] mice: PS/2 mouse device common for all mice
[   65.396087] rtc_cmos 00:05: RTC can wake from S4
[   65.396123] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
[   65.396151] rtc0: alarms up to one year, y3k, 114 bytes nvram
[   65.396214] device-mapper: uevent: version 1.0.3
[   65.396330] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: dm-devel@redhat.com
[   65.396454] device-mapper: multipath: version 1.0.5 loaded
[   65.396458] device-mapper: multipath round-robin: version 1.0.0 loaded
[   65.396614] cpuidle: using governor ladder
[   65.396617] cpuidle: using governor menu
[   65.397038] TCP cubic registered
[   65.397121] NET: Registered protocol family 10
[   65.397524] lo: Disabled Privacy Extensions
[   65.397818] NET: Registered protocol family 17
[   65.397844] Bluetooth: L2CAP ver 2.11
[   65.397846] Bluetooth: L2CAP socket layer initialized
[   65.397849] Bluetooth: SCO (Voice Link) ver 0.6
[   65.397851] Bluetooth: SCO socket layer initialized
[   65.397896] Bluetooth: RFCOMM socket layer initialized
[   65.397902] Bluetooth: RFCOMM TTY layer initialized
[   65.397904] Bluetooth: RFCOMM ver 1.10
[   65.398060] registered taskstats version 1
[   65.398212]   Magic number: 13:221:530
[   65.398299] rtc_cmos 00:05: setting system clock to 2009-06-21 11:33:07 UTC (1245583987)
[   65.398302] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   65.398304] EDD information not available.
[   65.398339] Freeing unused kernel memory: 536k freed
[   65.398575] Write protecting the kernel read-only data: 6708k
[   65.429343] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[   65.624460] FDC 0 is a post-1991 82077
[   65.690680] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.61.
[   65.691142] ACPI: PCI Interrupt Link [AMAC] enabled at IRQ 22
[   65.691147] forcedeth 0000:00:11.0: PCI INT A -> Link[AMAC] -> GSI 22 (level, low) -> IRQ 22
[   65.691152] forcedeth 0000:00:11.0: setting latency timer to 64
[   65.691195] nv_probe: set workaround bit for reversed mac addr
[   65.750701] ACPI: PCI Interrupt Link [APC4] enabled at IRQ 19
[   65.750711] ohci1394 0000:02:07.0: PCI INT A -> Link[APC4] -> GSI 19 (level, low) -> IRQ 19
[   65.750716] ohci1394 0000:02:07.0: setting latency timer to 64
[   65.800464] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[19]  MMIO=[cfdff000-cfdff7ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[   66.148020] usb 2-1: new full speed USB device using ohci_hcd and address 2
[   66.209348] forcedeth 0000:00:11.0: ifname eth0, PHY OUI 0x5043 @ 1, addr 00:04:4b:05:18:da
[   66.209352] forcedeth 0000:00:11.0: highdma csum vlan pwrctl mgmt timirq gbit lnktim msi desc-v3
[   66.209822] ACPI: PCI Interrupt Link [AMA1] enabled at IRQ 21
[   66.209827] forcedeth 0000:00:12.0: PCI INT A -> Link[AMA1] -> GSI 21 (level, low) -> IRQ 21
[   66.209832] forcedeth 0000:00:12.0: setting latency timer to 64
[   66.209888] nv_probe: set workaround bit for reversed mac addr
[   66.360220] usb 2-1: configuration #1 chosen from 1 choice
[   66.664022] usb 2-3: new full speed USB device using ohci_hcd and address 3
[   66.728875] forcedeth 0000:00:12.0: ifname eth1, PHY OUI 0x5043 @ 2, addr 00:04:4b:05:18:db
[   66.728879] forcedeth 0000:00:12.0: highdma csum vlan pwrctl mgmt timirq gbit lnktim msi desc-v3
[   66.900244] usb 2-3: configuration #1 chosen from 1 choice
[   67.092139] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[1aa205bc00044b06]
[   67.204021] usb 2-4: new full speed USB device using ohci_hcd and address 4
[   67.417275] usb 2-4: configuration #1 chosen from 1 choice
[   67.424542] usbcore: registered new interface driver hiddev
[   67.443310] input: WALTOP International Corp. Slim Tablet as /devices/pci0000:00/0000:00:0b.0/usb2/2-4/2-4:1.0/input/input4
[   67.476075] generic-usb 0003:172F:0034.0001: input,hidraw0: USB HID v1.10 Mouse [WALTOP International Corp. Slim Tablet] on usb-0000:00:0b.0-4/input0
[   67.476091] usbcore: registered new interface driver usbhid
[   67.476094] usbhid: v2.6:USB HID core driver
[   69.134450] ISO 9660 Extensions: Microsoft Joliet Level 3
[   69.171172] ISO 9660 Extensions: RRIP_1991A
[   69.412873] aufs 20080922
[   69.608366] squashfs: version 3.3 (2007/10/31) Phillip Lougher
[  113.080198] udev: starting version 141
[  113.360643] i2c-adapter i2c-0: nForce2 SMBus adapter at 0xf400
[  113.360665] i2c-adapter i2c-1: nForce2 SMBus adapter at 0xf000
[  113.434199] ck804xrom ck804xrom_init_one(): Unable to register resource 0x00000000ff000000-0x00000000ffffffff - kernel bug?
[  113.434211] resource map sanity check conflict: 0xff000000 0xffffffff 0xffff0000 0xffffffff pnp 00:0d
[  113.434220] ------------[ cut here ]------------
[  113.434223] WARNING: at /build/buildd/linux-2.6.28/arch/x86/mm/ioremap.c:226 __ioremap_caller+0x349/0x390()
[  113.434225] Modules linked in: ck804xrom(+) mtd chipreg i2c_nforce2 map_funcs squashfs aufs exportfs nls_cp437 isofs usbhid ohci1394 ieee1394 forcedeth floppy fbcon tileblit font bitblit softcursor
[  113.434243] Pid: 2411, comm: modprobe Not tainted 2.6.28-11-generic #42-Ubuntu
[  113.434245] Call Trace:
[  113.434252]  [<ffffffff802509bf>] warn_on_slowpath+0x5f/0x90
[  113.434257]  [<ffffffff8022f669>] ? default_spin_lock_flags+0x9/0x10
[  113.434260]  [<ffffffff8022f669>] ? default_spin_lock_flags+0x9/0x10
[  113.434263]  [<ffffffff80236c29>] __ioremap_caller+0x349/0x390
[  113.434268]  [<ffffffffa01032db>] ? ck804xrom_init_one+0x1ab/0x5ca [ck804xrom]
[  113.434272]  [<ffffffff80236d82>] ioremap_nocache+0x12/0x20
[  113.434277]  [<ffffffffa01032db>] ck804xrom_init_one+0x1ab/0x5ca [ck804xrom]
[  113.434281]  [<ffffffffa00a3041>] init_ck804xrom+0x41/0x59 [ck804xrom]
[  113.434286]  [<ffffffffa00a3000>] ? init_ck804xrom+0x0/0x59 [ck804xrom]
[  113.434290]  [<ffffffff8020a03b>] do_one_initcall+0x3b/0x170
[  113.434294]  [<ffffffff802424b2>] ? enqueue_entity+0x122/0x2b0
[  113.434297]  [<ffffffff802486cd>] ? enqueue_task_fair+0x3d/0x80
[  113.434301]  [<ffffffff8023e2a9>] ? wakeup_preempt_entity+0x59/0x60
[  113.434304]  [<ffffffff80249330>] ? check_preempt_wakeup+0x210/0x230
[  113.434307]  [<ffffffff8024a3cc>] ? try_to_wake_up+0x12c/0x2e0
[  113.434312]  [<ffffffff8027ef9d>] sys_init_module+0xad/0x1e0
[  113.434316]  [<ffffffff8021253a>] system_call_fastpath+0x16/0x1b
[  113.434318] ---[ end trace b48cdac6d1aff966 ]---
[  113.615913] input: PC Speaker as /devices/platform/pcspkr/input/input5
[  113.829920] Found: SST 49LF040B
[  113.829925] ck804xrom @fff80000: Found 1 x8 devices at 0x0 in 8-bit bank
[  113.972106] usblp0: Disabling reads from problematic bidirectional printer
[  113.978996] usblp0: USB Unidirectional printer dev 3 if 0 alt 1 proto 2 vid 0x03F0 pid 0x0204
[  113.979020] usbcore: registered new interface driver usblp
[  114.009951] using fwh lock/unlock method
[  114.009955] number of JEDEC chips: 1
[  114.009957] cfi_cmdset_0002: Disabling erase-suspend-program due to code brokenness.
[  114.094322] synaptics was reset on resume, see synaptics_resume_reset if you have trouble on resume
[  114.229209] Linux video capture interface: v2.00
[  114.765652] gspca: main v2.3.0 registered
[  114.820761] gspca: probing 0ac8:303b
[  115.080824] input: ImPS/2 Generic Wheel Mouse as /devices/platform/i8042/serio1/input/input6
[  115.227934] zc3xx: probe sensor -> 0a
[  115.227938] zc3xx: Find Sensor PB0330. Chip revision 0
[  115.243013] gspca: probe ok
[  115.243039] usbcore: registered new interface driver zc3xx
[  115.243065] zc3xx: registered
[  115.355006] ACPI: PCI Interrupt Link [AAZA] enabled at IRQ 20
[  115.355012] HDA Intel 0000:00:0f.1: PCI INT B -> Link[AAZA] -> GSI 20 (level, low) -> IRQ 20
[  115.355094] HDA Intel 0000:00:0f.1: setting latency timer to 64
[  115.744016] hda_codec: Unknown model for ALC883, trying auto-probe from BIOS...
[  125.867718] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[  125.867722] Bluetooth: BNEP filters: protocol multicast
[  126.010208] Bridge firewalling registered
[  134.333766] lp: driver loaded but no devices found
[  134.409462] ppdev: user-space parallel port driver
[  135.439991] usbcore: registered new interface driver wacom
[  135.439995] wacom: v1.49:USB Wacom Graphire and Wacom Intuos tablet driver
[  135.899308] forcedeth 0000:00:12.0: irq 2302 for MSI/MSI-X
[  135.899533] eth1: no link during initialization.
[  135.900031] ADDRCONF(NETDEV_UP): eth1: link is not ready
[  135.901358] forcedeth 0000:00:11.0: irq 2301 for MSI/MSI-X
[  146.388007] eth0: no IPv6 routers present
**root@ubuntu:~# **

```

I've marked with red the errors that show up when Live CD is trying to load the HDD when booting.
I marked with bold the inputs.

---

### Post by linux_0 on 2009-06-21
Looks like the kernel is unable to detect your SATA drives.

Is your BIOS detecting all the drives?

Have you swapped your SATA cables?

Are you using AHCI?

Good luck :) linux_0

---

### Post by C0NSTANTIN on 2009-06-21
BIOS detects my HDD ... i have swapped the SATA cables between the first two SATA slots... i have 4 more slots that i didn't tried .. 

Boy .. you sure know a lot of linux .. 

i've found in wikipedia about AHCI
"

[LIST]
[*]The AHCI controller does not work on AMD/ATI RS400-200, and RS480 [HBA]("http://en.wikipedia.org/wiki/Host_bus_adapter"); and Nvidia nForce 560 chipset[*[citation needed]("http://en.wikipedia.org/wiki/Wikipedia:Citation_needed")*] when [MSI]("http://en.wikipedia.org/wiki/Message_Signaled_Interrupts") is enabled due to a hardware error. For AHCI to work, users must provide the "pci=nomsi" kernel boot parameter. With MSI disabled in this way, the PCIe bus can only act as a faster PCI bus with hotplug capabilities.
[*]The VIA VT8251 South bridge suffers the same fate but it can be circumvented with the "pci=nomsi" option to force detection of the chip. This has been tested to work on 2.6.26, 2.6.24 and 2.6.20 [kernels]("http://en.wikipedia.org/wiki/Kernel_%28computing%29").
[*]Under [RHEL]("http://en.wikipedia.org/wiki/RHEL"), [CentOS]("http://en.wikipedia.org/wiki/CentOS") and similar, if you change your [BIOS]("http://en.wikipedia.org/wiki/BIOS") to AHCI mode and do not have the AHCI drivers in your [initrd]("http://en.wikipedia.org/wiki/Initrd") then you will not be able to boot."
[/LIST]
I'll go look into BIOS to see if i had it enabled ...

---

### Post by C0NSTANTIN on 2009-06-22
is there no one here able to help me!?!?!?!?
it's the 10th day i am operating live CD os ... i could have installed windows xp but this is how bad i want to migrate!!!

pls help me!!!! it will mean the world to me ...
tomorrow it's my first exam ... i need to make linux work ... pls :((

---

### Post by Endolith on 2009-06-22
Why do you want Linux so badly?

---

### Post by C0NSTANTIN on 2009-06-22
To escape the corporate world ... to protect my self from data theft and to escape marketing tactics windows environment imposes on it's users ...

I am planning a revolution in my country and i trust open source software to encrypt my data packages :p
[http://www.prisonplanet.com/](http://www.prisonplanet.com/)
[http://www.theresistancemanifesto.com/](http://www.theresistancemanifesto.com/)

And last but not least ... i like "the cube" ... :)

I DON'T SEE IT RIGHT THAT CORPORATIONS CHARGE FEES FOR THEIR FINANCED PROJECTS, YET OTHER PEOPLE DO THEM JUST FOR THE FUN OF IT ... FEDERAL RESERVE ENSLAVED GOVERNMENTS ACROSS THE WORLD AND I AM DOING MY BIT TO DISRUPT THEM, ENCOURAGING FREE-OPEN SOURCE .. AND IN TIME IF I GET THE KNOWLEDGE .. HELP OTHER PEOPLE MIGRATE AS WELL ...

i planned to open up a tutorial on my you tube page ... 
It's still a project and not publicized with all the tags ... [http://www.youtube.com/watch?v=f93oDWfuL4o&feature=channel_page](http://www.youtube.com/watch?v=f93oDWfuL4o&feature=channel_page)

I'm planning to make a redo of that movie when i'll have the knowledge to install linux and make it work ...

---

### Post by C0NSTANTIN on 2009-06-22
So no one knows the answer to my problem ... :( no one?!?! :((

---

### Post by C0NSTANTIN on 2009-06-24
IT WORKED :D
don't ask how .. i just installed XP again until i had an ideea to love boot xubuntu and found no longer those errors that i've been having ...

in fact ... that's what scares me most ... i don't know why it crushed .. so i don't know if it's safe to pour down my data ...

can someone pls say what could have been wrong  ... so i may avoid the situation in time ...

10x

---

### Post by C0NSTANTIN on 2009-06-24
well ... it's the 3rd time it crashez :))
I sent the machine to hibernate just like the last time it crashed ... so it's obvious xubuntu 64x crushez when you have the system configuration in my signature ...

the fist time i don't recall sending it to hibernate ... 
I got some pictures that i will post next time ..

---

### Post by C0NSTANTIN on 2009-06-30
I have all this exams ... but i really hope someone is finding out about this problem to fix it :(

---

### Post by Endolith on 2009-06-30
Even after you've solved these problems, you're just going to have more and more problems in the future.  I'd recommend dual booting with Windows so your computer is always usable.  Linux just isn't ready for end users yet, despite what the zealots say.

Also I'd recommend running Gnome Ubuntu instead of Xfce Xubuntu, since it's much more popular and better supported.

---

### Post by matyasfalvi on 2009-07-04
Hey!

I have a similar problem:

I am using a:
Fujitsu Siemens Amilo M6450G laptop and I am running Ubuntu 8.04 onit. (dual boot with xp)

First I experienced some problems with my internet the loopback didn't start automaticly this:

```
sudo ifconfig lo 127.0.0.1 netmask 255.0.0.0
``` 

solved the problem temporarily.

Then I had this issue that I couldn't shut down my computer when I pressed the shut down button the panel on the top with the red button disappeard and I couldn't do anything but the computer didn't shut down. This issue some how disappeard for a while. 

Then I constantly had trouble with my updates it always broke down during the installation process. 

Also I had issues with Firefox somehow I couldn't browse eventhough the internet connection was fine cause all the other apps that required internet connection where working fine.

Ant then finally the same thing happend with me as with Constantin I also get this:

```
ALERT! /dev/disk/by-uuid/78FC97CFFC978652 does not exist. Dropping to a shell!

BusyBox v.1.1.3 (Debian 1:1.1.3-5ubuntu12) Built-in shell (ash)
``` bla bla ...


And of course XP is running!


So I'd be also more than greatful if someone could just even point me where to start here also having in mind that my linux and overall computer skills are probably much more inferior than your's. :P

Thank you!

---

### Post by C0NSTANTIN on 2009-07-12
wow ... 750+ views and still no solution .. . cool :))

edit1 70+ more views and no solution

---

### Post by matyasfalvi on 2009-07-29
Hey Constantin!

May be your hard drive has too much stuff on it or the desktop try deleting some files!

Take care!

---

### Post by C0NSTANTIN on 2009-07-31
> **matyasfalvi said:**
> Hey Constantin!

May be your hard drive has too much stuff on it or the desktop try deleting some files!

Take care!


thanx for the thought ... many people read this topic, few ever take the time to try to help ... i appreciate you. but what i did was a clean install :)

wow ... so now it's 1128 views and no solution :) cool ... i am the voice of a thousand people :p enough to start a revolution in one small country lol :)

---

### Post by dearmrdear on 2009-08-04
Bump!
No one? No one? It took me 5 re-boots to get it to work.
Anyone?

---

### Post by C0NSTANTIN on 2009-08-12
Bump! 1414 an no clue thus far ... is anyone even reading this and thinking about a solution to this problem? ...

---

### Post by C0NSTANTIN on 2009-08-12
1415 views and no solution ... is anyone even noticing this thread and thinking about a solution? ....

edit1: srry ... lag ...

---

### Post by victorbstan on 2009-08-13
Had this same problem... banged my head on the wall for a couple of days...

Then pressed the ESC key when grub was looking for some attention at boot, and up popped some options:

kernel 2.6.28-14-generic


and 


kernel 2.6.28-11-generic


the default is the first one... this is the bad one.

when I chose the second one:

kernel 2.6.28-11-generic

All went well and I was back in the game...

Does this help?

---

### Post by victorbstan on 2009-08-14
Actually I take that back.

I put my computer to hibernate last night and woke up this morning to more of the same error messages:

boot from (hd0,0)ext3
SRST failed (errorno=-16)
/dev/disk/by-uuid/... does not exist.

So you may wonder, how is it that I'm posting here, well I figured out the pattern on when and why my computer all of a sudden decided to see my hd... it after I reboot with a windows cd! I used a Windows Vista installation cd to attempt and repair my computer, it throws errors as well... but a reboot after a windows cd boot makes the problems go away, and the computer thinks it's waking up from hibernation...

What's up with this? And how do I make this issue go away?

---

### Post by victorbstan on 2009-08-14
OK, my motherboard is: nForce 780i SLI
There are two places where groups of SATA sockets are. two of them are off the edge of the board. I used to have my problem SATA drive plugged into this one, and the DVD-RW in there as well. that's SATA 01 and 02. I just took the harddrive plug out of there and connected it to another cluster of 4 SATA plugs, and I have been able to successfully boot up from Hibernation... perhaps that was the problem a bad plug? Or some sort of a different in the location of the plugs making an error?

---

### Post by PatrickVogeli on 2009-08-15
Have you tried disabled AHCI and setting sata as IDE like mode?

Also, it could just be some unsupported hardware combination. It's not that uncommon. 

Or a failing hard drive or other hardware fail. Even though windows can see it / install to it, I'd get another HDD to check.

Also, last check, if you could get some IDE hdd and try that one..

---

### Post by matyasfalvi on 2009-08-18
Hi There Everybody!

I got some help on another forum. Basically we figured out that in my case: Grub is still there (and nagging) but the partition with Ubuntu is missing.

Try to boot from Ubuntu live cd then post the result of:

```
 sudo fdisk -l 
```

then:

```
 tune2fs -l /dev/sda1 | grep UUID 
```

and repeat this for all the other partitions.

and also install the smartmontools into the Live-CD and run:

```
smartctl -a /dev/sda
```

post results.

This way we can figure out what the problem is. In my case as I mentioned earlier the partition is missing. Theoretically it is possible to recover a partition with Testdisk. I don't know how though. I'm gonna look into that and once I figured something out I'm gonna post it here.

Good luck!

---

### Post by rob-ward on 2009-09-08
K, this is a really long thread and there has being no answer, one possible problem I have noticed is you are using a seagate drive. Seagate drives sometimes have an issue where they go to sleep, I know when I was programming set top boxes it was a major issue as linux loses track of them(200 bug reports in one week)

Your problems may be different but the solution was to disable sleep mode, to do that you will need to get into a terminal from a live cd and use this command:

```
sudo hdparm -Z /dev/sda
```

Hope that helps

---

### Post by graben3 on 2009-09-14
Got the same problem...

4 days ago one of my 2 1TB drives started to do SRTS failed errno=-16...

Then today, the other one satrted to do this as well... i really need this to work... and as far as I can tell it seems a kernel issue more than anything...

I never changed a thing in my setup / bios...all my drives were detedted well in my bios and everything was working #1 until now... so what is the problem ????
I have 4 sata drives all configured in IDE mode, all of them were seen by my bios. Now 1 of them is not seen anymore.

What can I do ?

---

### Post by C0NSTANTIN on 2009-09-20
I got something like ....

>  disabling Seagate auto powersaving mode
 HDIO_DRIVE_CMD(seagatepwrsave) failed: Invalid exchange
edit1 
I found this thread about that powersave bypassing command ... i find it strange that no one succedded ...
[http://ubuntuforums.org/showthread.php?t=668621](http://ubuntuforums.org/showthread.php?t=668621)

edit2
I filed a bug at fedora project since that distro too shows the same patterns
[https://bugzilla.redhat.com/show_bug.cgi?id=524756](https://bugzilla.redhat.com/show_bug.cgi?id=524756)
if you would like to vote it, i am sure the answer is the same for both  ubuntu and fedora...

---

### Post by C0NSTANTIN on 2009-09-28
**Actions that make xUbuntu go "SRST failed (errno=-16):**
Shutdown Computer for several hours / Suspend / Hibernate



**Repeating the Cycle:**

_HDD Partitionin Configuration used:_
[C:] ntfs - partition used to host Windows XP sp2
[\boot] ext3
[\] ext4 
[swap] swap

_Session 1 - Triggering the event_
-Start up xUbuntu
{recorded lspci and dmesg in "Log 1"}
-Hibernate/Suspend

_Session 1a - xUbuntu is of this point jammed_
-Resume xUbuntu
{after start-up progress bar compleats, a bleeping upper-left corner "_"
underscore is displayed, system jammes}
-Reset
{subsequent session of xUbuntu start-ups now will produce the same results
over again}

_Session 1a - I used Live CD to record what was going on_
-Boot Live CD
{Live Boot Slow >5 min}
{recorded lspci and dmesgin "Log 2"}
-Restart

[U]Session 2 - Installing the needed drivers under Windows to make HDD visible for
Live CD again[/U]
-Start up Windows XP
-Install MB drivers {drivers details listed below}
-Restart

_Session 2a - Reloading Windows for the Drivers changes made to take effect_
-Start up Windows XP
-Restart

_Session 3 - Installing xUbuntu again_
-Boot Live CD
{recorded lspci and dmesg in "Log 3"}
-Install xUbuntu 
-Restart

_Session 3a - Finishing Instalation of xUbuntu onto HDD_
-Start up xUbuntu[new]
-Continue Instalation until finished
{recorded lspci and dmesg in "Log 4"}



**One of this Drivers under Windows XP made HDD recognisable by Fedora 11 live CD**

I.NVIDIA SMBus Driver
II.NVIDIA Ethernet Driver
III.NVIDIA Storage Driver*
IV.NVIDIA and ForceWare Network Access Manager**

[COLOR="Gray"]*The NVIDIA Storage driver consists of 3 components:
1) NVIDIA storage driver optimized for nForce SATA controller that will replace
the driver that came with Windows.
2) A RAID controller driver which is required if SATA RAID is ENABLED in BIOS
3) RAID Manager application software

**The NVIDIA and ForceWare Network Access Manager consists of 3 components:
1)Network Access Manager's Framework
2)NVIDIA control panel
3)Intelligent Application Manager[/COLOR]



**Possible Causes**
An unavaileble Linux equivalent of the NV121906 hotfix

NVIDIA stated: [Some NVIDIA nForce 680i SLI "Designed by NVIDIA" motherboard customers have reported experiencing disconnect or write error issues with SATA disk drives. To address this, NVIDIA has released a BIOS update for the NVIDIA nForce 680i SLI "Designed by NVIDIA" motherboards that eliminates this bug. ](http://www.nvidia.com/object/680i_hotfix.html)

The fix was called "NV121906" and the [url=http://www.nvidia.com/object/windows_vista_hotfixes.html]links provided on the site are now broken, probably because the problems are now adressed in Windows Vista sp1.
[/url]

I found some [ drivers on NVIDIA's site](http://www.nvidia.com/object/linux_nforce_1.25.html), but i am affraid to use it [i'm kind'a noob to linux, and the file extension within the package scares me. I hope it is not a flash update cuz' last time i did a flash update i ended up frying my motherboard]
Is sata_nv.c included in xUbuntu installation already?

I want to thank linux_o for his hint about the hotfix NVIDIA was having for windows...

---

### Post by C0NSTANTIN on 2009-09-28
Terminal
```
[b][paladin@localhost ~]$ su -
Password:                  
[root@localhost ~]# lspci  [/b]
00:00.0 Host bridge: nVidia Corporation C55 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.3 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.4 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.5 RAM memory: nVidia Corporation C55 Memory Controller (rev a2)
00:00.6 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.7 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.0 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.1 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.3 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.4 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.5 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.6 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:02.0 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:02.1 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:02.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:03.0 PCI bridge: nVidia Corporation C55 PCI Express bridge (rev a1)
00:09.0 RAM memory: nVidia Corporation MCP55 Memory Controller (rev a1)
00:0a.0 ISA bridge: nVidia Corporation MCP55 LPC Bridge (rev a2)       
00:0a.1 SMBus: nVidia Corporation MCP55 SMBus (rev a2)                 
00:0b.0 USB Controller: nVidia Corporation MCP55 USB Controller (rev a1)
00:0b.1 USB Controller: nVidia Corporation MCP55 USB Controller (rev a2)
00:0d.0 IDE interface: nVidia Corporation MCP55 IDE (rev a1)            
00:0e.0 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a2)
00:0e.1 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a2)
00:0e.2 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a2)
00:0f.0 PCI bridge: nVidia Corporation MCP55 PCI bridge (rev a2)        
00:0f.1 Audio device: nVidia Corporation MCP55 High Definition Audio (rev a2)
00:11.0 Bridge: nVidia Corporation MCP55 Ethernet (rev a2)                   
00:12.0 Bridge: nVidia Corporation MCP55 Ethernet (rev a2)                   
01:00.0 VGA compatible controller: nVidia Corporation GeForce 9800 GT (rev a2)
02:07.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)                                                               
**[root@localhost ~]# dmesg                                                       **
Initializing cgroup subsys cpuset                                               
Initializing cgroup subsys cpu                                                  
Linux version 2.6.29.4-167.fc11.x86_64 (mockbuild@xenbuilder4.fedora.phx.redhat.com) (gcc version 4.4.0 20090506 (Red Hat 4.4.0-4) (GCC) ) #1 SMP Wed May 27 17:27:08 EDT 2009                                                                  
Command line: ro root=/dev/mapper/vg_bfg2k8-LogVol01 rhgb quiet                 
KERNEL supported cpus:                                                          
  Intel GenuineIntel                                                            
  AMD AuthenticAMD                                                              
  Centaur CentaurHauls                                                          
BIOS-provided physical RAM map:                                                 
 BIOS-e820: 0000000000000000 - 000000000009f000 (usable)                        
 BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)                      
 BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)                      
 BIOS-e820: 0000000000100000 - 000000007fef0000 (usable)                        
 BIOS-e820: 000000007fef0000 - 000000007fef3000 (ACPI NVS)                      
 BIOS-e820: 000000007fef3000 - 000000007ff00000 (ACPI data)                     
 BIOS-e820: 00000000d0000000 - 00000000f0000000 (reserved)                      
 BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)                      
DMI 2.4 present.                                                                
Phoenix BIOS detected: BIOS may corrupt low RAM, working around it.             
last_pfn = 0x7fef0 max_arch_pfn = 0x100000000                                   
x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106                
original variable MTRRs                                                         
reg 0, base: 0GB, range: 2GB, type WB                                           
reg 1, base: 2047MB, range: 1MB, type UC                                        
total RAM coverred: 2047M                                                       
Found optimal setting for mtrr clean up                                         
 gran_size: 64K         chunk_size: 2M  num_reg: 2      lose cover RAM: 0G      
New variable MTRRs                                                              
reg 0, base: 0GB, range: 2GB, type WB                                           
reg 1, base: 2047MB, range: 1MB, type UC                                        
x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106                
init_memory_mapping: 0000000000000000-000000007fef0000                          
 0000000000 - 007fe00000 page 2M                                                
 007fe00000 - 007fef0000 page 4k                                                
kernel direct mapping tables up to 7fef0000 @ 10000-14000                       
last_map_addr: 7fef0000 end: 7fef0000                                           
RAMDISK: 37c67000 - 37feff29                                                    
ACPI: RSDP 000F7F30, 0014 (r0 Nvidia)                                           
ACPI: RSDT 7FEF3040, 0038 (r1 Nvidia NVDAACPI 42302E31 NVDA        0)           
ACPI: FACP 7FEF30C0, 0074 (r1 Nvidia NVDAACPI 42302E31 NVDA        0)           
FADT: X_PM1a_EVT_BLK.bit_width (16) does not match PM1_EVT_LEN (4)              
ACPI: DSDT 7FEF3180, 5349 (r1 NVIDIA NVDAACPI     1000 MSFT  3000000)           
ACPI: FACS 7FEF0000, 0040                                                       
ACPI: HPET 7FEF8640, 003C (r1 Nvidia NVDAACPI 42302E31 NVDA        0)           
ACPI: WDRT 7FEF86C0, 0047 (r1 Nvidia NVDAACPI 42302E31 NVDA        0)           
ACPI: MCFG 7FEF8780, 003C (r1 Nvidia NVDAACPI 42302E31 NVDA        0)           
ACPI: APIC 7FEF8540, 0098 (r1 Nvidia NVDAACPI 42302E31 NVDA        0)           
ACPI: Local APIC address 0xfee00000                                             
No NUMA configuration found                                                     
Faking a node at 0000000000000000-000000007fef0000                              
Bootmem setup node 0 0000000000000000-000000007fef0000                          
  NODE_DATA [0000000000012000 - 0000000000026fff]                               
  bootmap [0000000000027000 -  0000000000036fdf] pages 10                       
(6 early reservations) ==> bootmem [0000000000 - 007fef0000]                    
  #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]   
  #1 [0000006000 - 0000008000]       TRAMPOLINE ==> [0000006000 - 0000008000]   
  #2 [0000200000 - 0000ac700c]    TEXT DATA BSS ==> [0000200000 - 0000ac700c]   
  #3 [0037c67000 - 0037feff29]          RAMDISK ==> [0037c67000 - 0037feff29]   
  #4 [000009f000 - 0000100000]    BIOS reserved ==> [000009f000 - 0000100000]   
  #5 [0000010000 - 0000012000]          PGTABLE ==> [0000010000 - 0000012000]   
found SMP MP-table at [ffff8800000f3f60] 000f3f60                               
 [ffffe20000000000-ffffe20001bfffff] PMD -> [ffff880001200000-ffff880002dfffff] on node 0                                                                       
Zone PFN ranges:                                                                
  DMA      0x00000010 -> 0x00001000                                             
  DMA32    0x00001000 -> 0x00100000                                             
  Normal   0x00100000 -> 0x00100000                                             
Movable zone start PFN for each node                                            
early_node_map[2] active PFN ranges                                             
    0: 0x00000010 -> 0x0000009f                                                 
    0: 0x00000100 -> 0x0007fef0                                                 
On node 0 totalpages: 523903                                                    
  DMA zone: 56 pages used for memmap                                            
  DMA zone: 2351 pages reserved                                                 
  DMA zone: 1576 pages, LIFO batch:0                                            
  DMA32 zone: 7109 pages used for memmap                                        
  DMA32 zone: 512811 pages, LIFO batch:31                                       
ACPI: PM-Timer IO Port: 0x1008                                                  
ACPI: Local APIC address 0xfee00000                                             
ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)                              
ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)                              
ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] disabled)                             
ACPI: LAPIC (acpi_id[0x03] lapic_id[0x03] disabled)                             
ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])                             
ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])                             
ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])                             
ACPI: LAPIC_NMI (acpi_id[0x03] high edge lint[0x1])                             
ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])                         
IOAPIC[0]: apic_id 4, version 0, address 0xfec00000, GSI 0-23                   
ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)                        
ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)                     
ACPI: INT_SRC_OVR (bus 0 bus_irq 14 global_irq 14 high edge)                    
ACPI: INT_SRC_OVR (bus 0 bus_irq 15 global_irq 15 high edge)                    
ACPI: IRQ0 used by override.                                                    
ACPI: IRQ2 used by override.                                                    
ACPI: IRQ9 used by override.                                                    
ACPI: IRQ14 used by override.                                                   
ACPI: IRQ15 used by override.                                                   
Using ACPI (MADT) for SMP configuration information                             
ACPI: HPET timers must be located in memory.                                    
SMP: Allowing 4 CPUs, 2 hotplug CPUs                                            
nr_irqs_gsi: 24                                                                 
PM: Registered nosave memory: 000000000009f000 - 00000000000a0000               
PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000               
PM: Registered nosave memory: 00000000000f0000 - 0000000000100000               
Allocating PCI resources starting at 80000000 (gap: 7ff00000:50100000)          
NR_CPUS:64 nr_cpumask_bits:64 nr_cpu_ids:4 nr_node_ids:1                        
PERCPU: Allocating 57344 bytes of per cpu data                                  
Built 1 zonelists in Node order, mobility grouping on.  Total pages: 514387     
Policy zone: DMA32                                                              
Kernel command line: ro root=/dev/mapper/vg_bfg2k8-LogVol01 rhgb quiet          
Initializing CPU#0                                                              
PID hash table entries: 4096 (order: 12, 32768 bytes)                           
Fast TSC calibration using PIT                                                  
Detected 3400.384 MHz processor.                                                
spurious 8259A interrupt: IRQ7.                                                 
Console: colour VGA+ 80x25                                                      
console [tty0] enabled                                                          
allocated 20971520 bytes of page_cgroup                                         
please try cgroup_disable=memory option if you don't want                       
Checking aperture...                                                            
No AGP bridge found                                                             
Calgary: detecting Calgary via BIOS EBDA area                                   
Calgary: Unable to locate Rio Grande table in EBDA - bailing!                   
Memory: 2033336k/2096064k available (3786k kernel code, 452k absent, 62276k reserved, 2294k data, 1304k init)                                                   
SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1         
Calibrating delay loop (skipped), value calculated using timer frequency.. 6800.76 BogoMIPS (lpj=3400384)                                                       
Security Framework initialized                                                  
SELinux:  Initializing.                                                         
SELinux:  Starting in permissive mode                                           
Dentry cache hash table entries: 262144 (order: 9, 2097152 bytes)               
Inode-cache hash table entries: 131072 (order: 8, 1048576 bytes)                
Mount-cache hash table entries: 256                                             
Initializing cgroup subsys ns                                                   
Initializing cgroup subsys cpuacct                                              
Initializing cgroup subsys memory                                               
Initializing cgroup subsys devices                                              
Initializing cgroup subsys freezer                                              
Initializing cgroup subsys net_cls                                              
CPU: Trace cache: 12K uops, L1 D cache: 16K                                     
CPU: L2 cache: 2048K                                                            
CPU 0/0x0 -> Node 0                                                             
CPU: Physical Processor ID: 0                                                   
CPU: Processor Core ID: 0                                                       
CPU0: Thermal monitoring enabled (TM1)                                          
using mwait in idle threads.                                                    
ACPI: Core revision 20081204                                                    
ftrace: converting mcount calls to 0f 1f 44 00 00                               
ftrace: allocating 18888 entries in 149 pages                                   
Setting APIC routing to flat                                                    
..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1                            
CPU0: Intel(R) Pentium(R) D CPU 3.40GHz stepping 04                             
Booting processor 1 APIC 0x1 ip 0x6000                                          
Initializing CPU#1                                                              
Calibrating delay using timer specific routine.. 6798.54 BogoMIPS (lpj=3399270) 
CPU: Trace cache: 12K uops, L1 D cache: 16K                                     
CPU: L2 cache: 2048K                                                            
CPU 1/0x1 -> Node 0                                                             
CPU: Physical Processor ID: 0                                                   
CPU: Processor Core ID: 1                                                       
CPU1: Thermal monitoring enabled (TM1)                                          
x86 PAT enabled: cpu 1, old 0x7040600070406, new 0x7010600070106                
CPU1: Intel(R) Pentium(R) D CPU 3.40GHz stepping 04                             
checking TSC synchronization [CPU#0 -> CPU#1]: passed.                          
Brought up 2 CPUs                                                               
Total of 2 processors activated (13599.30 BogoMIPS).                            
sizeof(vma)=176 bytes                                                           
sizeof(page)=56 bytes                                                           
sizeof(inode)=560 bytes                                                         
sizeof(dentry)=192 bytes                                                        
sizeof(ext3inode)=760 bytes                                                     
sizeof(buffer_head)=104 bytes                                                   
sizeof(skbuff)=232 bytes                                                        
sizeof(task_struct)=5880 bytes                                                  
CPU0 attaching sched-domain:                                                    
 domain 0: span 0-1 level CPU                                                   
  groups: 0 1                                                                   
CPU1 attaching sched-domain:                                                    
 domain 0: span 0-1 level CPU                                                   
  groups: 1 0                                                                   
net_namespace: 1904 bytes                                                       
Booting paravirtualized kernel on bare hardware                                 
regulator: core version 0.5                                                     
Time: 15:11:23  Date: 09/28/09                                                  
NET: Registered protocol family 16                                              
ACPI: bus type pci registered                                                   
PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255                
PCI: MCFG area at e0000000 reserved in E820                                     
PCI: Using MMCONFIG at e0000000 - efffffff                                      
PCI: Using configuration type 1 for base access                                 
bio: create slab <bio-0> at 0                                                   
ACPI: EC: Look up EC in DSDT                                                    
ACPI: Interpreter enabled                                                       
ACPI: (supports S0 S1 S3 S4 S5)                                                 
ACPI: Using IOAPIC for interrupt routing                                        
ACPI: No dock devices found.                                                    
ACPI: PCI Root Bridge [PCI0] (0000:00)                                          
pci 0000:00:03.0: PME# supported from D0 D1 D2 D3hot D3cold                     
pci 0000:00:03.0: PME# disabled                                                 
pci 0000:00:0a.0: reg 10 io port: [0xfc00-0xfc7f]                               
HPET not enabled in BIOS. You might try hpet=force boot option                  
pci 0000:00:0a.1: reg 10 io port: [0xf800-0xf83f]                               
pci 0000:00:0a.1: reg 20 io port: [0xf400-0xf43f]                               
pci 0000:00:0a.1: reg 24 io port: [0xf000-0xf03f]                               
pci 0000:00:0a.1: PME# supported from D3hot D3cold                              
pci 0000:00:0a.1: PME# disabled                                                 
pci 0000:00:0b.0: reg 10 32bit mmio: [0xcffff000-0xcfffffff]                    
pci 0000:00:0b.0: supports D1 D2                                                
pci 0000:00:0b.0: PME# supported from D0 D1 D2 D3hot D3cold                     
pci 0000:00:0b.0: PME# disabled                                                 
pci 0000:00:0b.1: reg 10 32bit mmio: [0xcfffe000-0xcfffe0ff]                    
pci 0000:00:0b.1: supports D1 D2                                                
pci 0000:00:0b.1: PME# supported from D0 D1 D2 D3hot D3cold                     
pci 0000:00:0b.1: PME# disabled                                                 
pci 0000:00:0d.0: reg 20 io port: [0xec00-0xec0f]                               
pci 0000:00:0e.0: reg 10 io port: [0x9f0-0x9f7]                                 
pci 0000:00:0e.0: reg 14 io port: [0xbf0-0xbf3]                                 
pci 0000:00:0e.0: reg 18 io port: [0x970-0x977]                                 
pci 0000:00:0e.0: reg 1c io port: [0xb70-0xb73]                                 
pci 0000:00:0e.0: reg 20 io port: [0xd800-0xd80f]                               
pci 0000:00:0e.0: reg 24 32bit mmio: [0xcfffd000-0xcfffdfff]                    
pci 0000:00:0e.1: reg 10 io port: [0x9e0-0x9e7]                                 
pci 0000:00:0e.1: reg 14 io port: [0xbe0-0xbe3]                                 
pci 0000:00:0e.1: reg 18 io port: [0x960-0x967]                                 
pci 0000:00:0e.1: reg 1c io port: [0xb60-0xb63]                                 
pci 0000:00:0e.1: reg 20 io port: [0xc400-0xc40f]                               
pci 0000:00:0e.1: reg 24 32bit mmio: [0xcfffc000-0xcfffcfff]                    
pci 0000:00:0e.2: reg 10 io port: [0xc000-0xc007]                               
pci 0000:00:0e.2: reg 14 io port: [0xbc00-0xbc03]                               
pci 0000:00:0e.2: reg 18 io port: [0xb800-0xb807]                               
pci 0000:00:0e.2: reg 1c io port: [0xb400-0xb403]                               
pci 0000:00:0e.2: reg 20 io port: [0xb000-0xb00f]                               
pci 0000:00:0e.2: reg 24 32bit mmio: [0xcfffb000-0xcfffbfff]                    
pci 0000:00:0f.1: reg 10 32bit mmio: [0xcfff0000-0xcfff3fff]                    
pci 0000:00:0f.1: PME# supported from D3hot D3cold                              
pci 0000:00:0f.1: PME# disabled                                                 
pci 0000:00:11.0: reg 10 32bit mmio: [0xcfffa000-0xcfffafff]                    
pci 0000:00:11.0: reg 14 io port: [0xac00-0xac07]                               
pci 0000:00:11.0: reg 18 32bit mmio: [0xcfff9000-0xcfff90ff]                    
pci 0000:00:11.0: reg 1c 32bit mmio: [0xcfff8000-0xcfff800f]                    
pci 0000:00:11.0: supports D1 D2                                                
pci 0000:00:11.0: PME# supported from D0 D1 D2 D3hot D3cold                     
pci 0000:00:11.0: PME# disabled                                                 
pci 0000:00:12.0: reg 10 32bit mmio: [0xcfff7000-0xcfff7fff]                    
pci 0000:00:12.0: reg 14 io port: [0xa800-0xa807]                               
pci 0000:00:12.0: reg 18 32bit mmio: [0xcfff6000-0xcfff60ff]                    
pci 0000:00:12.0: reg 1c 32bit mmio: [0xcfff5000-0xcfff500f]                    
pci 0000:00:12.0: supports D1 D2                                                
pci 0000:00:12.0: PME# supported from D0 D1 D2 D3hot D3cold                     
pci 0000:00:12.0: PME# disabled                                                 
pci 0000:01:00.0: reg 10 32bit mmio: [0xcc000000-0xccffffff]                    
pci 0000:01:00.0: reg 14 64bit mmio: [0xb0000000-0xbfffffff]                    
pci 0000:01:00.0: reg 1c 64bit mmio: [0xca000000-0xcbffffff]                    
pci 0000:01:00.0: reg 24 io port: [0x9c00-0x9c7f]                               
pci 0000:01:00.0: reg 30 32bit mmio: [0x000000-0x01ffff]                        
pci 0000:00:03.0: bridge io port: [0x9000-0x9fff]                               
pci 0000:00:03.0: bridge 32bit mmio: [0xca000000-0xcdffffff]                    
pci 0000:00:03.0: bridge 64bit mmio pref: [0xb0000000-0xbfffffff]               
pci 0000:02:07.0: reg 10 32bit mmio: [0xcfdff000-0xcfdff7ff]                    
pci 0000:02:07.0: reg 14 32bit mmio: [0xcfdf8000-0xcfdfbfff]                    
pci 0000:02:07.0: supports D1 D2                                                
pci 0000:02:07.0: PME# supported from D0 D1 D2 D3hot                            
pci 0000:02:07.0: PME# disabled                                                 
pci 0000:00:0f.0: transparent bridge                                            
pci 0000:00:0f.0: bridge io port: [0x8000-0x8fff]                               
pci 0000:00:0f.0: bridge 32bit mmio: [0xcfd00000-0xcfdfffff]                    
pci 0000:00:0f.0: bridge 32bit mmio pref: [0xcfe00000-0xcfefffff]               
ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]                             
ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]                        
ACPI Warning (nspredef-0940): \_SB_.PCI0.HUB0._PRT: Return Package type mismatch at index 2 - found [NULL Object Descriptor], expected Integer/Reference [20081204]                                                                             
ACPI: PCI Interrupt Link [LNK1] (IRQs 5 7 9 10 11 14 15) *0, disabled.          
ACPI: PCI Interrupt Link [LNK2] (IRQs 5 7 9 10 11 14 15) *0, disabled.          
ACPI: PCI Interrupt Link [LNK3] (IRQs 5 7 9 10 11 14 15) *0, disabled.          
ACPI: PCI Interrupt Link [LNK4] (IRQs 5 7 9 *10 11 14 15)                       
ACPI: PCI Interrupt Link [LXV5] (IRQs 5 7 9 *10 11 14 15)                       
ACPI: PCI Interrupt Link [LXV6] (IRQs 5 7 9 10 11 14 15) *0, disabled.          
ACPI: PCI Interrupt Link [LXV7] (IRQs 5 7 9 10 11 14 15) *0, disabled.          
ACPI: PCI Interrupt Link [LXV8] (IRQs 5 7 9 10 11 14 15) *0, disabled.          
ACPI: PCI Interrupt Link [LUBA] (IRQs 5 7 9 *10 11 14 15)                       
ACPI: PCI Interrupt Link [LMC1] (IRQs *5 7 9 10 11 14 15)                       
ACPI: PCI Interrupt Link [LMAC] (IRQs *5 7 9 10 11 14 15)                       
ACPI: PCI Interrupt Link [LAZA] (IRQs 5 7 9 10 *11 14 15)                       
ACPI: PCI Interrupt Link [LSMB] (IRQs 5 7 9 10 11 14 15) *0, disabled.          
ACPI: PCI Interrupt Link [LUB2] (IRQs 5 7 9 10 *11 14 15)                       
ACPI: PCI Interrupt Link [LIDE] (IRQs 5 7 9 10 11 14 15) *0, disabled.          
ACPI: PCI Interrupt Link [LSA0] (IRQs 5 7 9 10 *11 14 15)                       
ACPI: PCI Interrupt Link [LSA1] (IRQs 5 7 9 10 *11 14 15)                       
ACPI: PCI Interrupt Link [LSA2] (IRQs 5 7 9 *10 11 14 15)                       
ACPI: PCI Interrupt Link [APC1] (IRQs 16) *0, disabled.                         
ACPI: PCI Interrupt Link [APC2] (IRQs 17) *0, disabled.                         
ACPI: PCI Interrupt Link [APC3] (IRQs 18) *0, disabled.                         
ACPI: PCI Interrupt Link [APC4] (IRQs 19) *0                                    
ACPI: PCI Interrupt Link [AXV5] (IRQs 16) *0                                    
ACPI: PCI Interrupt Link [AXV6] (IRQs 16) *0, disabled.                         
ACPI: PCI Interrupt Link [AXV7] (IRQs 16) *0, disabled.                         
ACPI: PCI Interrupt Link [AXV8] (IRQs 16) *0, disabled.                         
ACPI: PCI Interrupt Link [AUBA] (IRQs 20 21 22 23) *0                           
ACPI: PCI Interrupt Link [AMA1] (IRQs 20 21 22 23) *0                           
ACPI: PCI Interrupt Link [AMAC] (IRQs 20 21 22 23) *0                           
ACPI: PCI Interrupt Link [AAZA] (IRQs 20 21 22 23) *0                           
ACPI: PCI Interrupt Link [AACI] (IRQs 20 21 22 23) *0, disabled.                
ACPI: PCI Interrupt Link [AMCI] (IRQs 20 21 22 23) *0, disabled.                
ACPI: PCI Interrupt Link [ASMB] (IRQs 20 21 22 23) *0, disabled.                
ACPI: PCI Interrupt Link [AUS2] (IRQs 20 21 22 23) *0                           
ACPI: PCI Interrupt Link [AIDE] (IRQs 20 21 22 23) *0, disabled.                
ACPI: PCI Interrupt Link [ASA0] (IRQs 20 21 22 23) *0                           
ACPI: PCI Interrupt Link [ASA1] (IRQs 20 21 22 23) *0                           
ACPI: PCI Interrupt Link [ASA2] (IRQs 20 21 22 23) *0                           
SCSI subsystem initialized                                                      
libata version 3.00 loaded.                                                     
usbcore: registered new interface driver usbfs                                  
usbcore: registered new interface driver hub                                    
usbcore: registered new device driver usb                                       
PCI: Using ACPI for IRQ routing                                                 
NetLabel: Initializing                                                          
NetLabel:  domain hash size = 128                                               
NetLabel:  protocols = UNLABELED CIPSOv4                                        
NetLabel:  unlabeled traffic allowed by default                                 
pnp: PnP ACPI init                                                              
ACPI: bus type pnp registered                                                   
pnp: PnP ACPI: found 13 devices                                                 
ACPI: ACPI bus type pnp unregistered                                            
system 00:00: ioport range 0x1000-0x107f has been reserved                      
system 00:00: ioport range 0x1080-0x10ff has been reserved                      
system 00:00: ioport range 0x1400-0x147f has been reserved                      
system 00:00: ioport range 0x1480-0x14ff has been reserved                      
system 00:00: ioport range 0x1800-0x187f has been reserved                      
system 00:00: ioport range 0x1880-0x18ff has been reserved                      
system 00:02: ioport range 0x4d0-0x4d1 has been reserved                        
system 00:02: ioport range 0x295-0x314 has been reserved                        
system 00:02: ioport range 0x880-0x88f has been reserved                        
system 00:0b: iomem range 0xe0000000-0xefffffff has been reserved               
system 00:0c: iomem range 0xd5800-0xd7fff has been reserved                     
system 00:0c: iomem range 0xf0000-0xf7fff could not be reserved                 
system 00:0c: iomem range 0xf8000-0xfbfff could not be reserved                 
system 00:0c: iomem range 0xfc000-0xfffff could not be reserved                 
system 00:0c: iomem range 0x7fef0000-0x7fefffff could not be reserved           
system 00:0c: iomem range 0xffff0000-0xffffffff has been reserved               
system 00:0c: iomem range 0x0-0x9ffff could not be reserved                     
system 00:0c: iomem range 0x100000-0x7feeffff could not be reserved             
system 00:0c: iomem range 0xfec00000-0xfec00fff has been reserved               
system 00:0c: iomem range 0xd0000000-0xdfffffff has been reserved               
system 00:0c: iomem range 0xfee00000-0xfee00fff has been reserved               
system 00:0c: iomem range 0xfeff0000-0xfeff0000 has been reserved               
pci 0000:00:03.0: PCI bridge, secondary bus 0000:01                             
pci 0000:00:03.0:   IO window: 0x9000-0x9fff                                    
pci 0000:00:03.0:   MEM window: 0xca000000-0xcdffffff                           
pci 0000:00:03.0:   PREFETCH window: 0x000000b0000000-0x000000bfffffff          
pci 0000:00:0f.0: PCI bridge, secondary bus 0000:02                             
pci 0000:00:0f.0:   IO window: 0x8000-0x8fff                                    
pci 0000:00:0f.0:   MEM window: 0xcfd00000-0xcfdfffff                           
pci 0000:00:0f.0:   PREFETCH window: 0x000000cfe00000-0x000000cfefffff          
pci 0000:00:03.0: setting latency timer to 64                                   
pci 0000:00:0f.0: setting latency timer to 64                                   
pci_bus 0000:00: resource 0 io:  [0x00-0xffff]                                  
pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffffffffffff]                  
pci_bus 0000:01: resource 0 io:  [0x9000-0x9fff]                                
pci_bus 0000:01: resource 1 mem: [0xca000000-0xcdffffff]                        
pci_bus 0000:01: resource 2 mem: [0xb0000000-0xbfffffff]                        
pci_bus 0000:01: resource 3 mem: [0x0-0x0]                                      
pci_bus 0000:02: resource 0 io:  [0x8000-0x8fff]                                
pci_bus 0000:02: resource 1 mem: [0xcfd00000-0xcfdfffff]                        
pci_bus 0000:02: resource 2 mem: [0xcfe00000-0xcfefffff]                        
pci_bus 0000:02: resource 3 io:  [0x00-0xffff]                                  
pci_bus 0000:02: resource 4 mem: [0x000000-0xffffffffffffffff]                  
NET: Registered protocol family 2                                               
IP route cache hash table entries: 65536 (order: 7, 524288 bytes)               
TCP established hash table entries: 262144 (order: 10, 4194304 bytes)           
TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)                    
TCP: Hash tables configured (established 262144 bind 65536)                     
TCP reno registered                                                             
NET: Registered protocol family 1                                               
checking if image is initramfs... it is                                         
Freeing initrd memory: 3619k freed                                              
audit: initializing netlink socket (disabled)                                   
type=2000 audit(1254150682.584:1): initialized                                  
HugeTLB registered 2 MB page size, pre-allocated 0 pages                        
VFS: Disk quotas dquot_6.5.2                                                    
Dquot-cache hash table entries: 512 (order 0, 4096 bytes)                       
msgmni has been set to 3978                                                     
SELinux:  Registering netfilter hooks                                           
alg: No test for stdrng (krng)                                                  
Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)            
io scheduler noop registered                                                    
io scheduler anticipatory registered                                            
io scheduler deadline registered                                                
io scheduler cfq registered (default)                                           
pci 0000:01:00.0: Boot video device                                             
pcieport-driver 0000:00:03.0: setting latency timer to 64                       
  alloc irq_desc for 24 on cpu 0 node 0                                         
  alloc kstat_irqs on cpu 0 node 0                                              
pcieport-driver 0000:00:03.0: irq 24 for MSI/MSI-X                              
pci_hotplug: PCI Hot Plug PCI Core version: 0.5                                 
pciehp: PCI Express Hot Plug Controller Driver version: 0.4                     
acpiphp: ACPI Hot Plug PCI Controller Driver version: 0.5                       
input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0       
ACPI: Power Button (FF) [PWRF]                                                  
input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1                                                                              
ACPI: Power Button (CM) [PWRB]                                                  
processor ACPI_CPU:00: registered as cooling_device0                            
ACPI: Processor [CPU0] (supports 8 throttling states)                           
processor ACPI_CPU:01: registered as cooling_device1                            
hpet_acpi_add: no address or irqs in _CRS                                       
Non-volatile memory driver v1.3                                                 
Linux agpgart interface v0.103                                                  
Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled                         
Switched to high resolution mode on CPU 1                                       
Switched to high resolution mode on CPU 0                                       
serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A                            
00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A                                 
brd: module loaded                                                              
loop: module loaded                                                             
Fixed MDIO Bus: probed                                                          
input: Macintosh mouse button emulation as /devices/virtual/input/input2        
Driver 'sd' needs updating - please use bus_type methods                        
Driver 'sr' needs updating - please use bus_type methods                        
ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver                      
ACPI: PCI Interrupt Link [AUS2] enabled at IRQ 23                               
  alloc irq_desc for 23 on cpu 0 node 0                                         
  alloc kstat_irqs on cpu 0 node 0                                              
ehci_hcd 0000:00:0b.1: PCI INT B -> Link[AUS2] -> GSI 23 (level, low) -> IRQ 23 
ehci_hcd 0000:00:0b.1: setting latency timer to 64                              
ehci_hcd 0000:00:0b.1: EHCI Host Controller                                     
ehci_hcd 0000:00:0b.1: new USB bus registered, assigned bus number 1            
ehci_hcd 0000:00:0b.1: debug port 1                                             
ehci_hcd 0000:00:0b.1: cache line size of 128 is not supported                  
ehci_hcd 0000:00:0b.1: irq 23, io mem 0xcfffe000                                
ehci_hcd 0000:00:0b.1: USB 2.0 started, EHCI 1.00                               
usb usb1: New USB device found, idVendor=1d6b, idProduct=0002                   
usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1              
usb usb1: Product: EHCI Host Controller                                         
usb usb1: Manufacturer: Linux 2.6.29.4-167.fc11.x86_64 ehci_hcd                 
usb usb1: SerialNumber: 0000:00:0b.1                                            
usb usb1: configuration #1 chosen from 1 choice                                 
hub 1-0:1.0: USB hub found                                                      
hub 1-0:1.0: 10 ports detected                                                  
ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver                          
ACPI: PCI Interrupt Link [AUBA] enabled at IRQ 22                               
  alloc irq_desc for 22 on cpu 0 node 0                                         
  alloc kstat_irqs on cpu 0 node 0                                              
ohci_hcd 0000:00:0b.0: PCI INT A -> Link[AUBA] -> GSI 22 (level, low) -> IRQ 22 
ohci_hcd 0000:00:0b.0: setting latency timer to 64                              
ohci_hcd 0000:00:0b.0: OHCI Host Controller                                     
ohci_hcd 0000:00:0b.0: new USB bus registered, assigned bus number 2            
ohci_hcd 0000:00:0b.0: irq 22, io mem 0xcffff000                                
usb usb2: New USB device found, idVendor=1d6b, idProduct=0001                   
usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1              
usb usb2: Product: OHCI Host Controller                                         
usb usb2: Manufacturer: Linux 2.6.29.4-167.fc11.x86_64 ohci_hcd                 
usb usb2: SerialNumber: 0000:00:0b.0                                            
usb usb2: configuration #1 chosen from 1 choice                                 
hub 2-0:1.0: USB hub found                                                      
hub 2-0:1.0: 10 ports detected                                                  
uhci_hcd: USB Universal Host Controller Interface driver                        
PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1                          
PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp                                                                  
serio: i8042 KBD port at 0x60,0x64 irq 1                                        
mice: PS/2 mouse device common for all mice                                     
rtc_cmos 00:05: RTC can wake from S4                                            
rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0                           
rtc0: alarms up to one year, y3k, 114 bytes nvram                               
device-mapper: uevent: version 1.0.3                                            
device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: dm-devel@redhat.com
cpuidle: using governor ladder                                                  
cpuidle: using governor menu                                                    
usbcore: registered new interface driver hiddev                                 
usbcore: registered new interface driver usbhid                                 
usbhid: v2.6:USB HID core driver                                                
nf_conntrack version 0.5.0 (16384 buckets, 65536 max)                           
CONFIG_NF_CT_ACCT is deprecated and will be removed soon. Please use            
nf_conntrack.acct=1 kernel paramater, acct=1 nf_conntrack module option or      
sysctl net.netfilter.nf_conntrack_acct=1 to enable it.                          
ip_tables: (C) 2000-2006 Netfilter Core Team                                    
TCP cubic registered                                                            
Initializing XFRM netlink socket                                                
NET: Registered protocol family 17                                              
registered taskstats version 1                                                  
  Magic number: 9:330:185                                                       
Initalizing network drop monitor service                                        
Freeing unused kernel memory: 1304k freed                                       
Write protecting the kernel read-only data: 1844k                               
input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3                                                                              
[drm] Initialized drm 1.1.0 20060810                                            
ACPI: PCI Interrupt Link [AXV5] enabled at IRQ 16                               
  alloc irq_desc for 16 on cpu 0 node 0                                         
  alloc kstat_irqs on cpu 0 node 0                                              
pci 0000:01:00.0: PCI INT A -> Link[AXV5] -> GSI 16 (level, low) -> IRQ 16      
pci 0000:01:00.0: setting latency timer to 64                                   
nouveau 0000:01:00.0: Detected an NV50 generation card (0x092a00a2)             
[drm] Initialized nouveau 0.0.12 20060213 for 0000:01:00.0 on minor 0           
usb 1-5: new high speed USB device using ehci_hcd and address 3                 
sata_nv 0000:00:0e.0: version 3.5                                               
ACPI: PCI Interrupt Link [ASA0] enabled at IRQ 21                               
  alloc irq_desc for 21 on cpu 0 node 0                                         
  alloc kstat_irqs on cpu 0 node 0                                              
sata_nv 0000:00:0e.0: PCI INT A -> Link[ASA0] -> GSI 21 (level, low) -> IRQ 21  
sata_nv 0000:00:0e.0: Using SWNCQ mode                                          
sata_nv 0000:00:0e.0: setting latency timer to 64                               
scsi0 : sata_nv                                                                 
scsi1 : sata_nv                                                                 
ata1: SATA max UDMA/133 cmd 0x9f0 ctl 0xbf0 bmdma 0xd800 irq 21                 
ata2: SATA max UDMA/133 cmd 0x970 ctl 0xb70 bmdma 0xd808 irq 21                 
usb 1-5: New USB device found, idVendor=0951, idProduct=1603                    
usb 1-5: New USB device strings: Mfr=1, Product=2, SerialNumber=3               
usb 1-5: Product: DataTraveler 2.0                                              
usb 1-5: Manufacturer: Kingston                                                 
usb 1-5: SerialNumber: 0019E000C6C1A8C062CF002E                                 
usb 1-5: configuration #1 chosen from 1 choice                                  
usb 2-1: new full speed USB device using ohci_hcd and address 2                 
usb 2-1: New USB device found, idVendor=0ac8, idProduct=303b                    
usb 2-1: New USB device strings: Mfr=1, Product=2, SerialNumber=0               
usb 2-1: Product: PC Camera                                                     
usb 2-1: Manufacturer: Vimicro Corp.                                            
usb 2-1: configuration #1 chosen from 1 choice                                  
usb 2-6: new low speed USB device using ohci_hcd and address 3                  
ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)                          
ata1.00: ATA-7: ST3320620AS, 3.AAE, max UDMA/133                                
ata1.00: 625142448 sectors, multi 16: LBA48 NCQ (depth 31/32)                   
ata1.00: configured for UDMA/133                                                
isa bounce pool size: 16 pages                                                  
scsi 0:0:0:0: Direct-Access     ATA      ST3320620AS      3.AA PQ: 0 ANSI: 5    
sd 0:0:0:0: [sda] 625142448 512-byte hardware sectors: (320 GB/298 GiB)         
sd 0:0:0:0: [sda] Write Protect is off                                          
sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00                                       
sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA                                                                         
sd 0:0:0:0: [sda] 625142448 512-byte hardware sectors: (320 GB/298 GiB)         
sd 0:0:0:0: [sda] Write Protect is off                                          
sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00                                       
sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA                                                                         
 sda: sda1 sda2 sda3                                                            
sd 0:0:0:0: [sda] Attached SCSI disk                                            
sd 0:0:0:0: Attached scsi generic sg0 type 0                                    
usb 2-6: New USB device found, idVendor=046d, idProduct=c501                    
usb 2-6: New USB device strings: Mfr=1, Product=2, SerialNumber=0               
usb 2-6: Product: USB Receiver                                                  
usb 2-6: Manufacturer: Logitech                                                 
usb 2-6: configuration #1 chosen from 1 choice                                  
input: Logitech USB Receiver as /devices/pci0000:00/0000:00:0b.0/usb2/2-6/2-6:1.0/input/input4                                                                  
generic-usb 0003:046D:C501.0001: input,hidraw0: USB HID v1.10 Mouse [Logitech USB Receiver] on usb-0000:00:0b.0-6/input0                                        
ata2: SATA link down (SStatus 0 SControl 300)                                   
ACPI: PCI Interrupt Link [ASA1] enabled at IRQ 20                               
  alloc irq_desc for 20 on cpu 0 node 0                                         
  alloc kstat_irqs on cpu 0 node 0                                              
sata_nv 0000:00:0e.1: PCI INT B -> Link[ASA1] -> GSI 20 (level, low) -> IRQ 20  
sata_nv 0000:00:0e.1: Using SWNCQ mode                                          
sata_nv 0000:00:0e.1: setting latency timer to 64                               
scsi2 : sata_nv                                                                 
scsi3 : sata_nv                                                                 
ata3: SATA max UDMA/133 cmd 0x9e0 ctl 0xbe0 bmdma 0xc400 irq 20                 
ata4: SATA max UDMA/133 cmd 0x960 ctl 0xb60 bmdma 0xc408 irq 20                 
ata3: SATA link down (SStatus 0 SControl 300)                                   
ata4: SATA link down (SStatus 0 SControl 300)                                   
ACPI: PCI Interrupt Link [ASA2] enabled at IRQ 23                               
sata_nv 0000:00:0e.2: PCI INT C -> Link[ASA2] -> GSI 23 (level, low) -> IRQ 23  
sata_nv 0000:00:0e.2: Using SWNCQ mode                                          
sata_nv 0000:00:0e.2: setting latency timer to 64                               
scsi4 : sata_nv                                                                 
scsi5 : sata_nv                                                                 
ata5: SATA max UDMA/133 cmd 0xc000 ctl 0xbc00 bmdma 0xb000 irq 23               
ata6: SATA max UDMA/133 cmd 0xb800 ctl 0xb400 bmdma 0xb008 irq 23               
ata5: SATA link down (SStatus 0 SControl 300)                                   
ata6: SATA link down (SStatus 0 SControl 300)                                   
pata_acpi 0000:00:0d.0: setting latency timer to 64                             
EXT4-fs: barriers enabled                                                       
kjournald2 starting: pid 89, dev dm-0:8, commit interval 5 seconds              
EXT4-fs: delayed allocation enabled                                             
EXT4-fs: file extents enabled                                                   
EXT4-fs: mballoc enabled                                                        
EXT4-fs: mounted filesystem dm-0 with ordered data mode                         
type=1404 audit(1254150688.436:2): enforcing=1 old_enforcing=0 auid=4294967295 ses=4294967295                                                                   
SELinux: 8192 avtab hash slots, 123719 rules.                                   
SELinux: 8192 avtab hash slots, 123719 rules.                                   
SELinux:  8 users, 11 roles, 2722 types, 127 bools, 1 sens, 1024 cats           
SELinux:  74 classes, 123719 rules                                              
SELinux:  Completing initialization.                                            
SELinux:  Setting up existing superblocks.                                      
SELinux: initialized (dev dm-0, type ext4), uses xattr                          
SELinux: initialized (dev tmpfs, type tmpfs), uses transition SIDs              
SELinux: initialized (dev usbfs, type usbfs), uses genfs_contexts               
SELinux: initialized (dev selinuxfs, type selinuxfs), uses genfs_contexts       
SELinux: initialized (dev mqueue, type mqueue), uses transition SIDs            
SELinux: initialized (dev hugetlbfs, type hugetlbfs), uses genfs_contexts       
SELinux: initialized (dev devpts, type devpts), uses transition SIDs            
SELinux: initialized (dev inotifyfs, type inotifyfs), uses genfs_contexts       
SELinux: initialized (dev tmpfs, type tmpfs), uses transition SIDs              
SELinux: initialized (dev anon_inodefs, type anon_inodefs), uses genfs_contexts 
SELinux: initialized (dev pipefs, type pipefs), uses task SIDs                  
SELinux: initialized (dev debugfs, type debugfs), uses genfs_contexts           
SELinux: initialized (dev sockfs, type sockfs), uses task SIDs                  
SELinux: initialized (dev proc, type proc), uses genfs_contexts                 
SELinux: initialized (dev bdev, type bdev), uses genfs_contexts                 
SELinux: initialized (dev rootfs, type rootfs), uses genfs_contexts             
SELinux: initialized (dev sysfs, type sysfs), uses genfs_contexts               
type=1403 audit(1254150688.715:3): policy loaded auid=4294967295 ses=4294967295 
udev: starting version 141                                                      
pata_amd 0000:00:0d.0: version 0.4.1                                            
pata_amd 0000:00:0d.0: setting latency timer to 64                              
scsi6 : pata_amd                                                                
scsi7 : pata_amd                                                                
ata7: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xec00 irq 14                 
ata8: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xec08 irq 15                 
Linux video capture interface: v2.00                                            
gspca: main v2.5.0 registered                                                   
gspca: probing 0ac8:303b                                                        
ata7.00: ATAPI: TEAC DV-W516GDM, M4S2, max UDMA/66                              
ata7: nv_mode_filter: 0x1f39f&0x1f01f->0x1f01f, BIOS=0x1f000 (0xc5000000) ACPI=0x1f01f (30:600:0x13)                                                            
ata7.00: limited to UDMA/33 due to 40-wire cable                                
ata7.00: configured for UDMA/33                                                 
scsi 6:0:0:0: CD-ROM            TEAC     DV-W516GDM       M4S2 PQ: 0 ANSI: 5    
sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray           
Uniform CD-ROM driver Revision: 3.20                                            
sr 6:0:0:0: Attached scsi CD-ROM sr0                                            
sr 6:0:0:0: Attached scsi generic sg1 type 5                                    
ata8: port disabled. ignoring.                                                  
i2c-adapter i2c-0: nForce2 SMBus adapter at 0xf400                              
i2c-adapter i2c-1: nForce2 SMBus adapter at 0xf000                              
Initializing USB Mass Storage driver...                                         
scsi8 : SCSI emulation for USB Mass Storage devices                             
usbcore: registered new interface driver usb-storage                            
USB Mass Storage support registered.                                            
usb-storage: device found at 3                                                  
usb-storage: waiting for device to settle before scanning                       
forcedeth: Reverse Engineered nForce ethernet driver. Version 0.62.             
ACPI: PCI Interrupt Link [AMAC] enabled at IRQ 22                               
forcedeth 0000:00:11.0: PCI INT A -> Link[AMAC] -> GSI 22 (level, low) -> IRQ 22
forcedeth 0000:00:11.0: setting latency timer to 64                             
input: PC Speaker as /devices/platform/pcspkr/input/input5                      
nv_probe: set workaround bit for reversed mac addr                              
forcedeth 0000:00:11.0: ifname eth0, PHY OUI 0x5043 @ 1, addr 00:04:4b:05:18:da 
forcedeth 0000:00:11.0: highdma csum vlan pwrctl mgmt timirq gbit lnktim msi desc-v3                                                                            
ACPI: PCI Interrupt Link [APC4] enabled at IRQ 19                               
  alloc irq_desc for 19 on cpu 0 node 0                                         
  alloc kstat_irqs on cpu 0 node 0                                              
firewire_ohci 0000:02:07.0: PCI INT A -> Link[APC4] -> GSI 19 (level, low) -> IRQ 19                                                                            
firewire_ohci 0000:02:07.0: setting latency timer to 64                         
firewire_ohci: Added fw-ohci device 0000:02:07.0, OHCI version 1.10             
ACPI: PCI Interrupt Link [AAZA] enabled at IRQ 21                               
HDA Intel 0000:00:0f.1: PCI INT B -> Link[AAZA] -> GSI 21 (level, low) -> IRQ 21
HDA Intel 0000:00:0f.1: setting latency timer to 64                             
hda_codec: Unknown model for ALC883, trying auto-probe from BIOS...             
ALSA sound/pci/hda/hda_codec.c:3507: autoconfig: line_outs=4 (0x14/0x15/0x16/0x17/0x0)                                                                          
ALSA sound/pci/hda/hda_codec.c:3511:    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)    
ALSA sound/pci/hda/hda_codec.c:3515:    hp_outs=1 (0x1b/0x0/0x0/0x0/0x0)        
ALSA sound/pci/hda/hda_codec.c:3516:    mono: mono_out=0x0                      
ALSA sound/pci/hda/hda_codec.c:3524:    inputs: mic=0x18, fmic=0x19, line=0x1a, fline=0x0, cd=0x0, aux=0x0                                                      
ACPI: PCI Interrupt Link [AMA1] enabled at IRQ 20                               
forcedeth 0000:00:12.0: PCI INT A -> Link[AMA1] -> GSI 20 (level, low) -> IRQ 20
forcedeth 0000:00:12.0: setting latency timer to 64                             
nv_probe: set workaround bit for reversed mac addr                              
firewire_core: created device fw0: GUID 1aa205bc00044b06, S400                  
forcedeth 0000:00:12.0: ifname eth1, PHY OUI 0x5043 @ 2, addr 00:04:4b:05:18:db 
forcedeth 0000:00:12.0: highdma csum vlan pwrctl mgmt timirq gbit lnktim msi desc-v3                                                                            
zc3xx: probe 2wr ov vga 0x0000                                                  
zc3xx: probe 3wr vga 1 0xe001                                                   
zc3xx: probe sensor -> 0013                                                     
zc3xx: Find Sensor MI0360. Chip revision e001                                   
gspca: probe ok                                                                 
usbcore: registered new interface driver zc3xx                                  
zc3xx: registered                                                               
device-mapper: multipath: version 1.0.5 loaded                                  
EXT4 FS on dm-0, internal journal on dm-0:8                                     
kjournald starting.  Commit interval 5 seconds                                  
EXT3 FS on sda2, internal journal                                               
EXT3-fs: mounted filesystem with ordered data mode.                             
SELinux: initialized (dev sda2, type ext3), uses xattr                          
SELinux: initialized (dev tmpfs, type tmpfs), uses transition SIDs              
swap_cgroup: uses 16288 bytes of vmalloc for pointer array space and 8339456 bytes to hold mem_cgroup pointers on swap                                          
swap_cgroup can be disabled by noswapaccount boot option.                       
Adding 4169720k swap on /dev/mapper/vg_bfg2k8-LogVol02.  Priority:-1 extents:1 across:4169720k                                                                  
SELinux: initialized (dev binfmt_misc, type binfmt_misc), uses genfs_contexts   
platform microcode: firmware: requesting intel-ucode/0f-06-04                   
platform microcode: firmware: requesting intel-ucode/0f-06-04                   
Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba       
Microcode Update Driver: v2.00 removed.                                         
p4-clockmod: P4/Xeon(TM) CPU On-Demand Clock Modulation available               
NET: Registered protocol family 10                                              
lo: Disabled Privacy Extensions                                                 
ip6_tables: (C) 2000-2006 Netfilter Core Team                                   
usb-storage: device scan complete                                               
scsi 8:0:0:0: Direct-Access     Kingston DataTraveler 2.0 1.00 PQ: 0 ANSI: 2    
sd 8:0:0:0: [sdb] 15695872 512-byte hardware sectors: (8.03 GB/7.48 GiB)        
sd 8:0:0:0: [sdb] Write Protect is off                                          
sd 8:0:0:0: [sdb] Mode Sense: 23 00 00 00                                       
sd 8:0:0:0: [sdb] Assuming drive cache: write through                           
sd 8:0:0:0: [sdb] 15695872 512-byte hardware sectors: (8.03 GB/7.48 GiB)        
sd 8:0:0:0: [sdb] Write Protect is off                                          
sd 8:0:0:0: [sdb] Mode Sense: 23 00 00 00                                       
sd 8:0:0:0: [sdb] Assuming drive cache: write through                           
 sdb: sdb1                                                                      
sd 8:0:0:0: [sdb] Attached SCSI removable disk                                  
sd 8:0:0:0: Attached scsi generic sg2 type 0                                    
JBD: barrier-based sync failed on dm-0:8 - disabling barriers                   
RPC: Registered udp transport module.                                           
RPC: Registered tcp transport module.                                           
SELinux: initialized (dev rpc_pipefs, type rpc_pipefs), uses genfs_contexts     
nouveau 0000:01:00.0: Allocating FIFO number 1                                  
nouveau 0000:01:00.0: nouveau_fifo_alloc: initialised FIFO 1                    
nouveau 0000:01:00.0: Allocating FIFO number 2                                  
nouveau 0000:01:00.0: nouveau_fifo_alloc: initialised FIFO 2                    
  alloc irq_desc for 25 on cpu 0 node 0                                         
  alloc kstat_irqs on cpu 0 node 0                                              
forcedeth 0000:00:12.0: irq 25 for MSI/MSI-X                                    
eth1: no link during initialization.                                            
ADDRCONF(NETDEV_UP): eth1: link is not ready                                    
  alloc irq_desc for 26 on cpu 0 node 0                                         
  alloc kstat_irqs on cpu 0 node 0                                              
forcedeth 0000:00:11.0: irq 26 for MSI/MSI-X                                    
eth0: no link during initialization.                                            
ADDRCONF(NETDEV_UP): eth0: link is not ready                                    
CPU0 attaching NULL sched-domain.                                               
CPU1 attaching NULL sched-domain.                                               
CPU0 attaching sched-domain:                                                    
 domain 0: span 0-1 level CPU                                                   
  groups: 0 1                                                                   
CPU1 attaching sched-domain:                                                    
 domain 0: span 0-1 level CPU                                                   
  groups: 1 0                                                                   
ALSA sound/pci/hda/hda_intel.c:1101: Too big adjustment 32: adj=128, bytes=128, size=4096, periods=32                                                           
ALSA sound/pci/hda/hda_intel.c:1101: Too big adjustment 32: adj=128, bytes=128, size=4096, periods=32                                                           
ALSA sound/pci/hda/hda_intel.c:1101: Too big adjustment 32: adj=128, bytes=128, size=4096, periods=32                                                           
ALSA sound/pci/hda/hda_intel.c:1101: Too big adjustment 32: adj=128, bytes=128, size=4096, periods=32                                                           
ALSA sound/pci/hda/hda_intel.c:1101: Too big adjustment 32: adj=128, bytes=128, size=4096, periods=32                                                           
ALSA sound/pci/hda/hda_intel.c:1101: Too big adjustment 32: adj=128, bytes=128, size=4096, periods=32                                                           
ALSA sound/pci/hda/hda_intel.c:1101: Too big adjustment 32: adj=256, bytes=128,size=4096, periods=32
ALSA sound/pci/hda/hda_intel.c:1101: Too big adjustment 32: adj=128, bytes=128,size=4096, periods=32
ALSA sound/pci/hda/hda_intel.c:1101: Too big adjustment 32: adj=128, bytes=128,size=4096, periods=32
ALSA sound/pci/hda/hda_intel.c:1101: Too big adjustment 32: adj=384, bytes=384,size=12288, periods=32
ALSA sound/pci/hda/hda_intel.c:1101: Too big adjustment 32: adj=128, bytes=128,size=4096, periods=32
ALSA sound/pci/hda/hda_intel.c:1101: Too big adjustment 32: adj=128, bytes=128,size=4096, periods=32
ALSA sound/pci/hda/hda_intel.c:1101: Too big adjustment 32: adj=384, bytes=384,size=12288, periods=32
ALSA sound/pci/hda/hda_intel.c:1101: Too big adjustment 32: adj=128, bytes=128,size=4096, periods=32
ALSA sound/pci/hda/hda_intel.c:1101: Too big adjustment 32: adj=128, bytes=128,size=4096, periods=32
ALSA sound/pci/hda/hda_intel.c:1101: Too big adjustment 32: adj=384, bytes=384,size=12288, periods=32
ALSA sound/pci/hda/hda_intel.c:1101: Too big adjustment 32: adj=128, bytes=128,size=4096, periods=32
ALSA sound/pci/hda/hda_intel.c:1101: Too big adjustment 32: adj=128, bytes=128,size=4096, periods=32
ALSA sound/pci/hda/hda_intel.c:1101: Too big adjustment 32: adj=512, bytes=128,size=4096, periods=32
ALSA sound/pci/hda/hda_intel.c:1101: Too big adjustment 32: adj=128, bytes=128,size=4096, periods=32
ALSA sound/pci/hda/hda_intel.c:1101: Too big adjustment 32: adj=128, bytes=128,size=4096, periods=32
ALSA sound/pci/hda/hda_intel.c:1101: Too big adjustment 32: adj=128, bytes=128,size=4096, periods=32
ALSA sound/pci/hda/hda_intel.c:1101: Too big adjustment 32: adj=128, bytes=128,size=4096, periods=32
SELinux: initialized (dev sdb1, type vfat), uses genfs_contexts
**[root@localhost ~]#**
```

---

### Post by C0NSTANTIN on 2009-09-28
Terminal
```
 
**[root@localhost ~]# lspci          **
00:00.0 Host bridge: nVidia Corporation C55 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.3 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.4 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.5 RAM memory: nVidia Corporation C55 Memory Controller (rev a2)
00:00.6 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.7 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.0 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.1 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.3 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.4 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.5 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.6 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:02.0 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:02.1 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:02.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:03.0 PCI bridge: nVidia Corporation C55 PCI Express bridge (rev a1)
00:09.0 RAM memory: nVidia Corporation MCP55 Memory Controller (rev a1)
00:0a.0 ISA bridge: nVidia Corporation MCP55 LPC Bridge (rev a2)       
00:0a.1 SMBus: nVidia Corporation MCP55 SMBus (rev a2)                 
00:0b.0 USB Controller: nVidia Corporation MCP55 USB Controller (rev a1)
00:0b.1 USB Controller: nVidia Corporation MCP55 USB Controller (rev a2)
00:0d.0 IDE interface: nVidia Corporation MCP55 IDE (rev a1)            
00:0e.0 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a2)
00:0e.1 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a2)
00:0e.2 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a2)
00:0f.0 PCI bridge: nVidia Corporation MCP55 PCI bridge (rev a2)        
00:0f.1 Audio device: nVidia Corporation MCP55 High Definition Audio (rev a2)
00:11.0 Bridge: nVidia Corporation MCP55 Ethernet (rev a2)                   
00:12.0 Bridge: nVidia Corporation MCP55 Ethernet (rev a2)                   
01:00.0 VGA compatible controller: nVidia Corporation GeForce 9800 GT (rev a2)
02:07.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)                                                               
**[root@localhost ~]# dmesg                                                       **
Initializing cgroup subsys cpuset                                               
Initializing cgroup subsys cpu                                                  
Linux version 2.6.29.4-167.fc11.x86_64 (mockbuild@xenbuilder4.fedora.phx.redhat.com) (gcc version 4.4.0 20090506 (Red Hat 4.4.0-4) (GCC) ) #1 SMP Wed May 27 17:27:08 EDT 2009                                                                  
Command line: initrd=initrd0.img root=CDLABEL=Fedora-11-x86_64-Live-KDE rootfstype=auto ro liveimg quiet  rhgb  BOOT_IMAGE=vmlinuz0                             
KERNEL supported cpus:                                                          
  Intel GenuineIntel                                                            
  AMD AuthenticAMD                                                              
  Centaur CentaurHauls                                                          
BIOS-provided physical RAM map:                                                 
 BIOS-e820: 0000000000000000 - 000000000009f000 (usable)                        
 BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)                      
 BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)                      
 BIOS-e820: 0000000000100000 - 000000007fef0000 (usable)                        
 BIOS-e820: 000000007fef0000 - 000000007fef3000 (ACPI NVS)                      
 BIOS-e820: 000000007fef3000 - 000000007ff00000 (ACPI data)                     
 BIOS-e820: 00000000d0000000 - 00000000f0000000 (reserved)                      
 BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)                      
DMI 2.4 present.                                                                
Phoenix BIOS detected: BIOS may corrupt low RAM, working around it.             
last_pfn = 0x7fef0 max_arch_pfn = 0x100000000                                   
x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106                
original variable MTRRs                                                         
reg 0, base: 0GB, range: 2GB, type WB                                           
reg 1, base: 2047MB, range: 1MB, type UC                                        
total RAM coverred: 2047M                                                       
Found optimal setting for mtrr clean up                                         
 gran_size: 64K         chunk_size: 2M  num_reg: 2      lose cover RAM: 0G      
New variable MTRRs                                                              
reg 0, base: 0GB, range: 2GB, type WB                                           
reg 1, base: 2047MB, range: 1MB, type UC                                        
x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106                
init_memory_mapping: 0000000000000000-000000007fef0000                          
 0000000000 - 007fe00000 page 2M                                                
 007fe00000 - 007fef0000 page 4k                                                
kernel direct mapping tables up to 7fef0000 @ 10000-14000                       
last_map_addr: 7fef0000 end: 7fef0000                                           
RAMDISK: 7f9de000 - 7feced39                                                    
ACPI: RSDP 000F7F30, 0014 (r0 Nvidia)                                           
ACPI: RSDT 7FEF3040, 0038 (r1 Nvidia NVDAACPI 42302E31 NVDA        0)           
ACPI: FACP 7FEF30C0, 0074 (r1 Nvidia NVDAACPI 42302E31 NVDA        0)           
FADT: X_PM1a_EVT_BLK.bit_width (16) does not match PM1_EVT_LEN (4)              
ACPI: DSDT 7FEF3180, 5349 (r1 NVIDIA NVDAACPI     1000 MSFT  3000000)           
ACPI: FACS 7FEF0000, 0040                                                       
ACPI: HPET 7FEF8640, 003C (r1 Nvidia NVDAACPI 42302E31 NVDA        0)           
ACPI: WDRT 7FEF86C0, 0047 (r1 Nvidia NVDAACPI 42302E31 NVDA        0)           
ACPI: MCFG 7FEF8780, 003C (r1 Nvidia NVDAACPI 42302E31 NVDA        0)           
ACPI: APIC 7FEF8540, 0098 (r1 Nvidia NVDAACPI 42302E31 NVDA        0)           
ACPI: Local APIC address 0xfee00000                                             
No NUMA configuration found                                                     
Faking a node at 0000000000000000-000000007fef0000                              
Bootmem setup node 0 0000000000000000-000000007fef0000                          
  NODE_DATA [0000000000012000 - 0000000000026fff]                               
  bootmap [0000000000027000 -  0000000000036fdf] pages 10                       
(6 early reservations) ==> bootmem [0000000000 - 007fef0000]                    
  #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]   
  #1 [0000006000 - 0000008000]       TRAMPOLINE ==> [0000006000 - 0000008000]   
  #2 [0000200000 - 0000ac700c]    TEXT DATA BSS ==> [0000200000 - 0000ac700c]   
  #3 [007f9de000 - 007feced39]          RAMDISK ==> [007f9de000 - 007feced39]   
  #4 [000009f000 - 0000100000]    BIOS reserved ==> [000009f000 - 0000100000]   
  #5 [0000010000 - 0000012000]          PGTABLE ==> [0000010000 - 0000012000]   
found SMP MP-table at [ffff8800000f3f60] 000f3f60                               
 [ffffe20000000000-ffffe20001bfffff] PMD -> [ffff880001200000-ffff880002dfffff] on node 0                                                                       
Zone PFN ranges:                                                                
  DMA      0x00000010 -> 0x00001000                                             
  DMA32    0x00001000 -> 0x00100000                                             
  Normal   0x00100000 -> 0x00100000                                             
Movable zone start PFN for each node                                            
early_node_map[2] active PFN ranges                                             
    0: 0x00000010 -> 0x0000009f                                                 
    0: 0x00000100 -> 0x0007fef0                                                 
On node 0 totalpages: 523903                                                    
  DMA zone: 56 pages used for memmap                                            
  DMA zone: 2351 pages reserved                                                 
  DMA zone: 1576 pages, LIFO batch:0                                            
  DMA32 zone: 7109 pages used for memmap                                        
  DMA32 zone: 512811 pages, LIFO batch:31                                       
ACPI: PM-Timer IO Port: 0x1008                                                  
ACPI: Local APIC address 0xfee00000                                             
ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)                              
ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)                              
ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] disabled)                             
ACPI: LAPIC (acpi_id[0x03] lapic_id[0x03] disabled)                             
ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])                             
ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])                             
ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])                             
ACPI: LAPIC_NMI (acpi_id[0x03] high edge lint[0x1])                             
ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])                         
IOAPIC[0]: apic_id 4, version 0, address 0xfec00000, GSI 0-23                   
ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)                        
ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)                     
ACPI: INT_SRC_OVR (bus 0 bus_irq 14 global_irq 14 high edge)                    
ACPI: INT_SRC_OVR (bus 0 bus_irq 15 global_irq 15 high edge)                    
ACPI: IRQ0 used by override.                                                    
ACPI: IRQ2 used by override.                                                    
ACPI: IRQ9 used by override.                                                    
ACPI: IRQ14 used by override.                                                   
ACPI: IRQ15 used by override.                                                   
Using ACPI (MADT) for SMP configuration information                             
ACPI: HPET timers must be located in memory.                                    
SMP: Allowing 4 CPUs, 2 hotplug CPUs                                            
nr_irqs_gsi: 24                                                                 
PM: Registered nosave memory: 000000000009f000 - 00000000000a0000               
PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000               
PM: Registered nosave memory: 00000000000f0000 - 0000000000100000               
Allocating PCI resources starting at 80000000 (gap: 7ff00000:50100000)          
NR_CPUS:64 nr_cpumask_bits:64 nr_cpu_ids:4 nr_node_ids:1                        
PERCPU: Allocating 57344 bytes of per cpu data                                  
Built 1 zonelists in Node order, mobility grouping on.  Total pages: 514387     
Policy zone: DMA32                                                              
Kernel command line: initrd=initrd0.img root=CDLABEL=Fedora-11-x86_64-Live-KDE rootfstype=auto ro liveimg quiet  rhgb  BOOT_IMAGE=vmlinuz0                      
Initializing CPU#0                                                              
PID hash table entries: 4096 (order: 12, 32768 bytes)                           
Fast TSC calibration using PIT                                                  
Detected 3400.161 MHz processor.                                                
spurious 8259A interrupt: IRQ7.                                                 
Console: colour VGA+ 80x25                                                      
console [tty0] enabled                                                          
allocated 20971520 bytes of page_cgroup                                         
please try cgroup_disable=memory option if you don't want                       
Checking aperture...                                                            
No AGP bridge found                                                             
Calgary: detecting Calgary via BIOS EBDA area                                   
Calgary: Unable to locate Rio Grande table in EBDA - bailing!                   
Memory: 2031896k/2096064k available (3786k kernel code, 452k absent, 63716k reserved, 2294k data, 1304k init)                                                   
SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1         
Calibrating delay loop (skipped), value calculated using timer frequency.. 6800.32 BogoMIPS (lpj=3400161)                                                       
Security Framework initialized                                                  
SELinux:  Initializing.                                                         
SELinux:  Starting in permissive mode                                           
Dentry cache hash table entries: 262144 (order: 9, 2097152 bytes)               
Inode-cache hash table entries: 131072 (order: 8, 1048576 bytes)                
Mount-cache hash table entries: 256                                             
Initializing cgroup subsys ns                                                   
Initializing cgroup subsys cpuacct                                              
Initializing cgroup subsys memory                                               
Initializing cgroup subsys devices                                              
Initializing cgroup subsys freezer                                              
Initializing cgroup subsys net_cls                                              
CPU: Trace cache: 12K uops, L1 D cache: 16K                                     
CPU: L2 cache: 2048K                                                            
CPU 0/0x0 -> Node 0                                                             
CPU: Physical Processor ID: 0                                                   
CPU: Processor Core ID: 0                                                       
CPU0: Thermal monitoring enabled (TM1)                                          
using mwait in idle threads.                                                    
ACPI: Core revision 20081204                                                    
ftrace: converting mcount calls to 0f 1f 44 00 00                               
ftrace: allocating 18888 entries in 149 pages                                   
Setting APIC routing to flat                                                    
..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1                            
CPU0: Intel(R) Pentium(R) D CPU 3.40GHz stepping 04                             
Booting processor 1 APIC 0x1 ip 0x6000                                          
Initializing CPU#1                                                              
Calibrating delay using timer specific routine.. 6799.09 BogoMIPS (lpj=3399546) 
CPU: Trace cache: 12K uops, L1 D cache: 16K                                     
CPU: L2 cache: 2048K                                                            
CPU 1/0x1 -> Node 0                                                             
CPU: Physical Processor ID: 0                                                   
CPU: Processor Core ID: 1                                                       
CPU1: Thermal monitoring enabled (TM1)                                          
x86 PAT enabled: cpu 1, old 0x7040600070406, new 0x7010600070106                
CPU1: Intel(R) Pentium(R) D CPU 3.40GHz stepping 04                             
checking TSC synchronization [CPU#0 -> CPU#1]: passed.                          
Brought up 2 CPUs                                                               
Total of 2 processors activated (13599.41 BogoMIPS).                            
sizeof(vma)=176 bytes                                                           
sizeof(page)=56 bytes                                                           
sizeof(inode)=560 bytes                                                         
sizeof(dentry)=192 bytes                                                        
sizeof(ext3inode)=760 bytes                                                     
sizeof(buffer_head)=104 bytes                                                   
sizeof(skbuff)=232 bytes                                                        
sizeof(task_struct)=5880 bytes                                                  
CPU0 attaching sched-domain:                                                    
 domain 0: span 0-1 level CPU                                                   
  groups: 0 1                                                                   
CPU1 attaching sched-domain:                                                    
 domain 0: span 0-1 level CPU                                                   
  groups: 1 0                                                                   
net_namespace: 1904 bytes                                                       
Booting paravirtualized kernel on bare hardware                                 
regulator: core version 0.5                                                     
Time: 15:17:42  Date: 09/28/09                                                  
NET: Registered protocol family 16                                              
ACPI: bus type pci registered                                                   
PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255                
PCI: MCFG area at e0000000 reserved in E820                                     
PCI: Using MMCONFIG at e0000000 - efffffff                                      
PCI: Using configuration type 1 for base access                                 
bio: create slab <bio-0> at 0                                                   
ACPI: EC: Look up EC in DSDT                                                    
ACPI: Interpreter enabled                                                       
ACPI: (supports S0 S1 S3 S4 S5)                                                 
ACPI: Using IOAPIC for interrupt routing                                        
ACPI: No dock devices found.                                                    
ACPI: PCI Root Bridge [PCI0] (0000:00)                                          
pci 0000:00:03.0: PME# supported from D0 D1 D2 D3hot D3cold                     
pci 0000:00:03.0: PME# disabled                                                 
pci 0000:00:0a.0: reg 10 io port: [0xfc00-0xfc7f]                               
HPET not enabled in BIOS. You might try hpet=force boot option                  
pci 0000:00:0a.1: reg 10 io port: [0xf800-0xf83f]                               
pci 0000:00:0a.1: reg 20 io port: [0xf400-0xf43f]                               
pci 0000:00:0a.1: reg 24 io port: [0xf000-0xf03f]                               
pci 0000:00:0a.1: PME# supported from D3hot D3cold                              
pci 0000:00:0a.1: PME# disabled                                                 
pci 0000:00:0b.0: reg 10 32bit mmio: [0xcffff000-0xcfffffff]                    
pci 0000:00:0b.0: supports D1 D2                                                
pci 0000:00:0b.0: PME# supported from D0 D1 D2 D3hot D3cold                     
pci 0000:00:0b.0: PME# disabled                                                 
pci 0000:00:0b.1: reg 10 32bit mmio: [0xcfffe000-0xcfffe0ff]                    
pci 0000:00:0b.1: supports D1 D2                                                
pci 0000:00:0b.1: PME# supported from D0 D1 D2 D3hot D3cold                     
pci 0000:00:0b.1: PME# disabled                                                 
pci 0000:00:0d.0: reg 20 io port: [0xec00-0xec0f]                               
pci 0000:00:0e.0: reg 10 io port: [0x9f0-0x9f7]                                 
pci 0000:00:0e.0: reg 14 io port: [0xbf0-0xbf3]                                 
pci 0000:00:0e.0: reg 18 io port: [0x970-0x977]                                 
pci 0000:00:0e.0: reg 1c io port: [0xb70-0xb73]                                 
pci 0000:00:0e.0: reg 20 io port: [0xd800-0xd80f]                               
pci 0000:00:0e.0: reg 24 32bit mmio: [0xcfffd000-0xcfffdfff]                    
pci 0000:00:0e.1: reg 10 io port: [0x9e0-0x9e7]                                 
pci 0000:00:0e.1: reg 14 io port: [0xbe0-0xbe3]                                 
pci 0000:00:0e.1: reg 18 io port: [0x960-0x967]                                 
pci 0000:00:0e.1: reg 1c io port: [0xb60-0xb63]                                 
pci 0000:00:0e.1: reg 20 io port: [0xc400-0xc40f]                               
pci 0000:00:0e.1: reg 24 32bit mmio: [0xcfffc000-0xcfffcfff]                    
pci 0000:00:0e.2: reg 10 io port: [0xc000-0xc007]                               
pci 0000:00:0e.2: reg 14 io port: [0xbc00-0xbc03]                               
pci 0000:00:0e.2: reg 18 io port: [0xb800-0xb807]                               
pci 0000:00:0e.2: reg 1c io port: [0xb400-0xb403]                               
pci 0000:00:0e.2: reg 20 io port: [0xb000-0xb00f]                               
pci 0000:00:0e.2: reg 24 32bit mmio: [0xcfffb000-0xcfffbfff]                    
pci 0000:00:0f.1: reg 10 32bit mmio: [0xcfff0000-0xcfff3fff]                    
pci 0000:00:0f.1: PME# supported from D3hot D3cold                              
pci 0000:00:0f.1: PME# disabled                                                 
pci 0000:00:11.0: reg 10 32bit mmio: [0xcfffa000-0xcfffafff]                    
pci 0000:00:11.0: reg 14 io port: [0xac00-0xac07]                               
pci 0000:00:11.0: reg 18 32bit mmio: [0xcfff9000-0xcfff90ff]                    
pci 0000:00:11.0: reg 1c 32bit mmio: [0xcfff8000-0xcfff800f]                    
pci 0000:00:11.0: supports D1 D2                                                
pci 0000:00:11.0: PME# supported from D0 D1 D2 D3hot D3cold                     
pci 0000:00:11.0: PME# disabled                                                 
pci 0000:00:12.0: reg 10 32bit mmio: [0xcfff7000-0xcfff7fff]                    
pci 0000:00:12.0: reg 14 io port: [0xa800-0xa807]                               
pci 0000:00:12.0: reg 18 32bit mmio: [0xcfff6000-0xcfff60ff]                    
pci 0000:00:12.0: reg 1c 32bit mmio: [0xcfff5000-0xcfff500f]                    
pci 0000:00:12.0: supports D1 D2                                                
pci 0000:00:12.0: PME# supported from D0 D1 D2 D3hot D3cold                     
pci 0000:00:12.0: PME# disabled                                                 
pci 0000:01:00.0: reg 10 32bit mmio: [0xcc000000-0xccffffff]                    
pci 0000:01:00.0: reg 14 64bit mmio: [0xb0000000-0xbfffffff]                    
pci 0000:01:00.0: reg 1c 64bit mmio: [0xca000000-0xcbffffff]                    
pci 0000:01:00.0: reg 24 io port: [0x9c00-0x9c7f]                               
pci 0000:01:00.0: reg 30 32bit mmio: [0x000000-0x01ffff]                        
pci 0000:00:03.0: bridge io port: [0x9000-0x9fff]                               
pci 0000:00:03.0: bridge 32bit mmio: [0xca000000-0xcdffffff]                    
pci 0000:00:03.0: bridge 64bit mmio pref: [0xb0000000-0xbfffffff]               
pci 0000:02:07.0: reg 10 32bit mmio: [0xcfdff000-0xcfdff7ff]                    
pci 0000:02:07.0: reg 14 32bit mmio: [0xcfdf8000-0xcfdfbfff]                    
pci 0000:02:07.0: supports D1 D2                                                
pci 0000:02:07.0: PME# supported from D0 D1 D2 D3hot                            
pci 0000:02:07.0: PME# disabled                                                 
pci 0000:00:0f.0: transparent bridge                                            
pci 0000:00:0f.0: bridge io port: [0x8000-0x8fff]                               
pci 0000:00:0f.0: bridge 32bit mmio: [0xcfd00000-0xcfdfffff]                    
pci 0000:00:0f.0: bridge 32bit mmio pref: [0xcfe00000-0xcfefffff]               
ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]                             
ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]                        
ACPI Warning (nspredef-0940): \_SB_.PCI0.HUB0._PRT: Return Package type mismatch at index 2 - found [NULL Object Descriptor], expected Integer/Reference [20081204]                                                                             
ACPI: PCI Interrupt Link [LNK1] (IRQs 5 7 9 10 11 14 15) *0, disabled.          
ACPI: PCI Interrupt Link [LNK2] (IRQs 5 7 9 10 11 14 15) *0, disabled.          
ACPI: PCI Interrupt Link [LNK3] (IRQs 5 7 9 10 11 14 15) *0, disabled.          
ACPI: PCI Interrupt Link [LNK4] (IRQs 5 7 9 *10 11 14 15)                       
ACPI: PCI Interrupt Link [LXV5] (IRQs 5 7 9 *10 11 14 15)                       
ACPI: PCI Interrupt Link [LXV6] (IRQs 5 7 9 10 11 14 15) *0, disabled.          
ACPI: PCI Interrupt Link [LXV7] (IRQs 5 7 9 10 11 14 15) *0, disabled.          
ACPI: PCI Interrupt Link [LXV8] (IRQs 5 7 9 10 11 14 15) *0, disabled.          
ACPI: PCI Interrupt Link [LUBA] (IRQs 5 7 9 *10 11 14 15)                       
ACPI: PCI Interrupt Link [LMC1] (IRQs *5 7 9 10 11 14 15)                       
ACPI: PCI Interrupt Link [LMAC] (IRQs *5 7 9 10 11 14 15)                       
ACPI: PCI Interrupt Link [LAZA] (IRQs 5 7 9 10 *11 14 15)                       
ACPI: PCI Interrupt Link [LSMB] (IRQs 5 7 9 10 11 14 15) *0, disabled.          
ACPI: PCI Interrupt Link [LUB2] (IRQs 5 7 9 10 *11 14 15)                       
ACPI: PCI Interrupt Link [LIDE] (IRQs 5 7 9 10 11 14 15) *0, disabled.          
ACPI: PCI Interrupt Link [LSA0] (IRQs 5 7 9 10 *11 14 15)                       
ACPI: PCI Interrupt Link [LSA1] (IRQs 5 7 9 10 *11 14 15)                       
ACPI: PCI Interrupt Link [LSA2] (IRQs 5 7 9 *10 11 14 15)                       
ACPI: PCI Interrupt Link [APC1] (IRQs 16) *0, disabled.                         
ACPI: PCI Interrupt Link [APC2] (IRQs 17) *0, disabled.                         
ACPI: PCI Interrupt Link [APC3] (IRQs 18) *0, disabled.                         
ACPI: PCI Interrupt Link [APC4] (IRQs 19) *0                                    
ACPI: PCI Interrupt Link [AXV5] (IRQs 16) *0                                    
ACPI: PCI Interrupt Link [AXV6] (IRQs 16) *0, disabled.                         
ACPI: PCI Interrupt Link [AXV7] (IRQs 16) *0, disabled.                         
ACPI: PCI Interrupt Link [AXV8] (IRQs 16) *0, disabled.                         
ACPI: PCI Interrupt Link [AUBA] (IRQs 20 21 22 23) *0                           
ACPI: PCI Interrupt Link [AMA1] (IRQs 20 21 22 23) *0                           
ACPI: PCI Interrupt Link [AMAC] (IRQs 20 21 22 23) *0                           
ACPI: PCI Interrupt Link [AAZA] (IRQs 20 21 22 23) *0                           
ACPI: PCI Interrupt Link [AACI] (IRQs 20 21 22 23) *0, disabled.                
ACPI: PCI Interrupt Link [AMCI] (IRQs 20 21 22 23) *0, disabled.                
ACPI: PCI Interrupt Link [ASMB] (IRQs 20 21 22 23) *0, disabled.                
ACPI: PCI Interrupt Link [AUS2] (IRQs 20 21 22 23) *0                           
ACPI: PCI Interrupt Link [AIDE] (IRQs 20 21 22 23) *0, disabled.                
ACPI: PCI Interrupt Link [ASA0] (IRQs 20 21 22 23) *0                           
ACPI: PCI Interrupt Link [ASA1] (IRQs 20 21 22 23) *0                           
ACPI: PCI Interrupt Link [ASA2] (IRQs 20 21 22 23) *0                           
SCSI subsystem initialized                                                      
libata version 3.00 loaded.                                                     
usbcore: registered new interface driver usbfs                                  
usbcore: registered new interface driver hub                                    
usbcore: registered new device driver usb                                       
PCI: Using ACPI for IRQ routing                                                 
NetLabel: Initializing                                                          
NetLabel:  domain hash size = 128                                               
NetLabel:  protocols = UNLABELED CIPSOv4                                        
NetLabel:  unlabeled traffic allowed by default                                 
pnp: PnP ACPI init                                                              
ACPI: bus type pnp registered                                                   
pnp: PnP ACPI: found 13 devices                                                 
ACPI: ACPI bus type pnp unregistered                                            
system 00:00: ioport range 0x1000-0x107f has been reserved                      
system 00:00: ioport range 0x1080-0x10ff has been reserved                      
system 00:00: ioport range 0x1400-0x147f has been reserved                      
system 00:00: ioport range 0x1480-0x14ff has been reserved                      
system 00:00: ioport range 0x1800-0x187f has been reserved                      
system 00:00: ioport range 0x1880-0x18ff has been reserved                      
system 00:02: ioport range 0x4d0-0x4d1 has been reserved                        
system 00:02: ioport range 0x295-0x314 has been reserved                        
system 00:02: ioport range 0x880-0x88f has been reserved                        
system 00:0b: iomem range 0xe0000000-0xefffffff has been reserved               
system 00:0c: iomem range 0xd0000-0xd3fff has been reserved                     
system 00:0c: iomem range 0xd5800-0xd7fff has been reserved                     
system 00:0c: iomem range 0xf0000-0xfbfff could not be reserved                 
system 00:0c: iomem range 0xfc000-0xfffff could not be reserved                 
system 00:0c: iomem range 0x7fef0000-0x7fefffff could not be reserved           
system 00:0c: iomem range 0xffff0000-0xffffffff has been reserved               
system 00:0c: iomem range 0x0-0x9ffff could not be reserved                     
system 00:0c: iomem range 0x100000-0x7feeffff could not be reserved             
system 00:0c: iomem range 0xfec00000-0xfec00fff has been reserved               
system 00:0c: iomem range 0xd0000000-0xdfffffff has been reserved               
system 00:0c: iomem range 0xfee00000-0xfee00fff has been reserved               
system 00:0c: iomem range 0xfeff0000-0xfeff0000 has been reserved               
pci 0000:00:03.0: PCI bridge, secondary bus 0000:01                             
pci 0000:00:03.0:   IO window: 0x9000-0x9fff                                    
pci 0000:00:03.0:   MEM window: 0xca000000-0xcdffffff                           
pci 0000:00:03.0:   PREFETCH window: 0x000000b0000000-0x000000bfffffff          
pci 0000:00:0f.0: PCI bridge, secondary bus 0000:02                             
pci 0000:00:0f.0:   IO window: 0x8000-0x8fff                                    
pci 0000:00:0f.0:   MEM window: 0xcfd00000-0xcfdfffff                           
pci 0000:00:0f.0:   PREFETCH window: 0x000000cfe00000-0x000000cfefffff          
pci 0000:00:03.0: setting latency timer to 64                                   
pci 0000:00:0f.0: setting latency timer to 64                                   
pci_bus 0000:00: resource 0 io:  [0x00-0xffff]                                  
pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffffffffffff]                  
pci_bus 0000:01: resource 0 io:  [0x9000-0x9fff]                                
pci_bus 0000:01: resource 1 mem: [0xca000000-0xcdffffff]                        
pci_bus 0000:01: resource 2 mem: [0xb0000000-0xbfffffff]                        
pci_bus 0000:01: resource 3 mem: [0x0-0x0]                                      
pci_bus 0000:02: resource 0 io:  [0x8000-0x8fff]                                
pci_bus 0000:02: resource 1 mem: [0xcfd00000-0xcfdfffff]                        
pci_bus 0000:02: resource 2 mem: [0xcfe00000-0xcfefffff]                        
pci_bus 0000:02: resource 3 io:  [0x00-0xffff]                                  
pci_bus 0000:02: resource 4 mem: [0x000000-0xffffffffffffffff]                  
NET: Registered protocol family 2                                               
IP route cache hash table entries: 65536 (order: 7, 524288 bytes)               
TCP established hash table entries: 262144 (order: 10, 4194304 bytes)           
TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)                    
TCP: Hash tables configured (established 262144 bind 65536)                     
TCP reno registered                                                             
NET: Registered protocol family 1                                               
checking if image is initramfs... it is                                         
Freeing initrd memory: 5059k freed                                              
audit: initializing netlink socket (disabled)                                   
type=2000 audit(1254151061.717:1): initialized                                  
HugeTLB registered 2 MB page size, pre-allocated 0 pages                        
VFS: Disk quotas dquot_6.5.2                                                    
Dquot-cache hash table entries: 512 (order 0, 4096 bytes)                       
msgmni has been set to 3978                                                     
SELinux:  Registering netfilter hooks                                           
alg: No test for stdrng (krng)                                                  
Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)            
io scheduler noop registered                                                    
io scheduler anticipatory registered                                            
io scheduler deadline registered                                                
io scheduler cfq registered (default)                                           
pci 0000:01:00.0: Boot video device                                             
pcieport-driver 0000:00:03.0: setting latency timer to 64                       
  alloc irq_desc for 24 on cpu 0 node 0                                         
  alloc kstat_irqs on cpu 0 node 0                                              
pcieport-driver 0000:00:03.0: irq 24 for MSI/MSI-X                              
pci_hotplug: PCI Hot Plug PCI Core version: 0.5                                 
pciehp: PCI Express Hot Plug Controller Driver version: 0.4                     
acpiphp: ACPI Hot Plug PCI Controller Driver version: 0.5                       
input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0       
ACPI: Power Button (FF) [PWRF]                                                  
input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1                                                                              
ACPI: Power Button (CM) [PWRB]                                                  
processor ACPI_CPU:00: registered as cooling_device0                            
ACPI: Processor [CPU0] (supports 8 throttling states)                           
processor ACPI_CPU:01: registered as cooling_device1                            
hpet_acpi_add: no address or irqs in _CRS                                       
Non-volatile memory driver v1.3                                                 
Linux agpgart interface v0.103                                                  
Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled                         
Switched to high resolution mode on CPU 1                                       
Switched to high resolution mode on CPU 0                                       
serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A                            
00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A                                 
brd: module loaded                                                              
loop: module loaded                                                             
Fixed MDIO Bus: probed                                                          
input: Macintosh mouse button emulation as /devices/virtual/input/input2        
Driver 'sd' needs updating - please use bus_type methods                        
Driver 'sr' needs updating - please use bus_type methods                        
ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver                      
ACPI: PCI Interrupt Link [AUS2] enabled at IRQ 23                               
  alloc irq_desc for 23 on cpu 0 node 0                                         
  alloc kstat_irqs on cpu 0 node 0                                              
ehci_hcd 0000:00:0b.1: PCI INT B -> Link[AUS2] -> GSI 23 (level, low) -> IRQ 23 
ehci_hcd 0000:00:0b.1: setting latency timer to 64                              
ehci_hcd 0000:00:0b.1: EHCI Host Controller                                     
ehci_hcd 0000:00:0b.1: new USB bus registered, assigned bus number 1            
ehci_hcd 0000:00:0b.1: debug port 1                                             
ehci_hcd 0000:00:0b.1: cache line size of 128 is not supported                  
ehci_hcd 0000:00:0b.1: irq 23, io mem 0xcfffe000                                
ehci_hcd 0000:00:0b.1: USB 2.0 started, EHCI 1.00                               
usb usb1: New USB device found, idVendor=1d6b, idProduct=0002                   
usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1              
usb usb1: Product: EHCI Host Controller                                         
usb usb1: Manufacturer: Linux 2.6.29.4-167.fc11.x86_64 ehci_hcd                 
usb usb1: SerialNumber: 0000:00:0b.1                                            
usb usb1: configuration #1 chosen from 1 choice                                 
hub 1-0:1.0: USB hub found                                                      
hub 1-0:1.0: 10 ports detected                                                  
ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver                          
ACPI: PCI Interrupt Link [AUBA] enabled at IRQ 22                               
  alloc irq_desc for 22 on cpu 0 node 0                                         
  alloc kstat_irqs on cpu 0 node 0                                              
ohci_hcd 0000:00:0b.0: PCI INT A -> Link[AUBA] -> GSI 22 (level, low) -> IRQ 22 
ohci_hcd 0000:00:0b.0: setting latency timer to 64                              
ohci_hcd 0000:00:0b.0: OHCI Host Controller                                     
ohci_hcd 0000:00:0b.0: new USB bus registered, assigned bus number 2            
ohci_hcd 0000:00:0b.0: irq 22, io mem 0xcffff000                                
usb usb2: New USB device found, idVendor=1d6b, idProduct=0001                   
usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1              
usb usb2: Product: OHCI Host Controller                                         
usb usb2: Manufacturer: Linux 2.6.29.4-167.fc11.x86_64 ohci_hcd                 
usb usb2: SerialNumber: 0000:00:0b.0                                            
usb usb2: configuration #1 chosen from 1 choice                                 
hub 2-0:1.0: USB hub found                                                      
hub 2-0:1.0: 10 ports detected                                                  
uhci_hcd: USB Universal Host Controller Interface driver                        
PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1                          
PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp                                                                  
serio: i8042 KBD port at 0x60,0x64 irq 1                                        
mice: PS/2 mouse device common for all mice                                     
rtc_cmos 00:05: RTC can wake from S4                                            
rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0                           
rtc0: alarms up to one year, y3k, 114 bytes nvram                               
device-mapper: uevent: version 1.0.3                                            
device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: dm-devel@redhat.com
cpuidle: using governor ladder                                                  
cpuidle: using governor menu                                                    
usbcore: registered new interface driver hiddev                                 
usbcore: registered new interface driver usbhid                                 
usbhid: v2.6:USB HID core driver                                                
nf_conntrack version 0.5.0 (16384 buckets, 65536 max)                           
CONFIG_NF_CT_ACCT is deprecated and will be removed soon. Please use            
nf_conntrack.acct=1 kernel paramater, acct=1 nf_conntrack module option or      
sysctl net.netfilter.nf_conntrack_acct=1 to enable it.                          
ip_tables: (C) 2000-2006 Netfilter Core Team                                    
TCP cubic registered                                                            
Initializing XFRM netlink socket                                                
NET: Registered protocol family 17                                              
registered taskstats version 1                                                  
  Magic number: 9:433:286                                                       
Initalizing network drop monitor service                                        
Freeing unused kernel memory: 1304k freed                                       
Write protecting the kernel read-only data: 1844k                               
input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3                                                                              
udev: starting version 141                                                      
[drm] Initialized drm 1.1.0 20060810                                            
sata_nv 0000:00:0e.0: version 3.5                                               
ACPI: PCI Interrupt Link [ASA0] enabled at IRQ 21                               
  alloc irq_desc for 21 on cpu 0 node 0                                         
  alloc kstat_irqs on cpu 0 node 0                                              
sata_nv 0000:00:0e.0: PCI INT A -> Link[ASA0] -> GSI 21 (level, low) -> IRQ 21  
sata_nv 0000:00:0e.0: Using SWNCQ mode                                          
sata_nv 0000:00:0e.0: setting latency timer to 64                               
scsi0 : sata_nv                                                                 
scsi1 : sata_nv                                                                 
ata1: SATA max UDMA/133 cmd 0x9f0 ctl 0xbf0 bmdma 0xd800 irq 21                 
ata2: SATA max UDMA/133 cmd 0x970 ctl 0xb70 bmdma 0xd808 irq 21                 
ACPI: PCI Interrupt Link [AXV5] enabled at IRQ 16                               
  alloc irq_desc for 16 on cpu 0 node 0                                         
  alloc kstat_irqs on cpu 0 node 0                                              
pci 0000:01:00.0: PCI INT A -> Link[AXV5] -> GSI 16 (level, low) -> IRQ 16      
pci 0000:01:00.0: setting latency timer to 64                                   
nouveau 0000:01:00.0: Detected an NV50 generation card (0x092a00a2)             
[drm] Initialized nouveau 0.0.12 20060213 for 0000:01:00.0 on minor 0           
usb 1-5: new high speed USB device using ehci_hcd and address 3                 
usb 1-5: New USB device found, idVendor=0951, idProduct=1603                    
usb 1-5: New USB device strings: Mfr=1, Product=2, SerialNumber=3               
usb 1-5: Product: DataTraveler 2.0                                              
usb 1-5: Manufacturer: Kingston                                                 
usb 1-5: SerialNumber: 0019E000C6C1A8C062CF002E                                 
usb 1-5: configuration #1 chosen from 1 choice                                  
Initializing USB Mass Storage driver...                                         
scsi2 : SCSI emulation for USB Mass Storage devices                             
usb-storage: device found at 3                                                  
usb-storage: waiting for device to settle before scanning                       
usbcore: registered new interface driver usb-storage                            
USB Mass Storage support registered.                                            
usb 2-1: new full speed USB device using ohci_hcd and address 2                 
usb 2-1: New USB device found, idVendor=0ac8, idProduct=303b                    
usb 2-1: New USB device strings: Mfr=1, Product=2, SerialNumber=0               
usb 2-1: Product: PC Camera                                                     
usb 2-1: Manufacturer: Vimicro Corp.                                            
usb 2-1: configuration #1 chosen from 1 choice                                  
usb 2-6: new low speed USB device using ohci_hcd and address 3                  
usb 2-6: New USB device found, idVendor=046d, idProduct=c501                    
usb 2-6: New USB device strings: Mfr=1, Product=2, SerialNumber=0               
usb 2-6: Product: USB Receiver                                                  
usb 2-6: Manufacturer: Logitech                                                 
usb 2-6: configuration #1 chosen from 1 choice                                  
input: Logitech USB Receiver as /devices/pci0000:00/0000:00:0b.0/usb2/2-6/2-6:1.0/input/input4                                                                  
generic-usb 0003:046D:C501.0001: input,hidraw0: USB HID v1.10 Mouse [Logitech USB Receiver] on usb-0000:00:0b.0-6/input0                                        
usb-storage: device scan complete                                               
isa bounce pool size: 16 pages                                                  
scsi 2:0:0:0: Direct-Access     Kingston DataTraveler 2.0 1.00 PQ: 0 ANSI: 2    
sd 2:0:0:0: [sda] 15695872 512-byte hardware sectors: (8.03 GB/7.48 GiB)        
sd 2:0:0:0: [sda] Write Protect is off                                          
sd 2:0:0:0: [sda] Mode Sense: 23 00 00 00                                       
sd 2:0:0:0: [sda] Assuming drive cache: write through                           
sd 2:0:0:0: [sda] 15695872 512-byte hardware sectors: (8.03 GB/7.48 GiB)        
sd 2:0:0:0: [sda] Write Protect is off                                          
sd 2:0:0:0: [sda] Mode Sense: 23 00 00 00                                       
sd 2:0:0:0: [sda] Assuming drive cache: write through                           
 sda: sda1                                                                      
sd 2:0:0:0: [sda] Attached SCSI removable disk                                  
sd 2:0:0:0: Attached scsi generic sg0 type 0                                    
ata1: link is slow to respond, please be patient (ready=-19)                    
ata1: SRST failed (errno=-16)                                                   
ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)                          
ata1: link online but device misclassified, retrying                            
ata1: link is slow to respond, please be patient (ready=-19)                    
ata1: SRST failed (errno=-16)                                                   
ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)                          
ata1: link online but device misclassified, retrying                            
ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)                          
ata1.00: NODEV after polling detection                                          
ata2: SATA link down (SStatus 0 SControl 300)                                   
ACPI: PCI Interrupt Link [APC4] enabled at IRQ 19                               
  alloc irq_desc for 19 on cpu 0 node 0                                         
  alloc kstat_irqs on cpu 0 node 0                                              
firewire_ohci 0000:02:07.0: PCI INT A -> Link[APC4] -> GSI 19 (level, low) -> IRQ 19                                                                            
firewire_ohci 0000:02:07.0: setting latency timer to 64                         
firewire_ohci: Added fw-ohci device 0000:02:07.0, OHCI version 1.10             
pata_amd 0000:00:0d.0: version 0.4.1                                            
pata_amd 0000:00:0d.0: setting latency timer to 64                              
scsi3 : pata_amd                                                                
scsi4 : pata_amd                                                                
ata3: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xec00 irq 14                 
ata4: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xec08 irq 15                 
ata3.00: ATAPI: TEAC DV-W516GDM, M4S2, max UDMA/66                              
ata3: nv_mode_filter: 0x1f39f&0x1f01f->0x1f01f, BIOS=0x1f000 (0xc5000000) ACPI=0x1f01f (30:600:0x13)                                                            
ata3.00: limited to UDMA/33 due to 40-wire cable                                
ata3.00: configured for UDMA/33                                                 
scsi 3:0:0:0: CD-ROM            TEAC     DV-W516GDM       M4S2 PQ: 0 ANSI: 5    
sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray           
Uniform CD-ROM driver Revision: 3.20                                            
sr 3:0:0:0: Attached scsi CD-ROM sr0                                            
sr 3:0:0:0: Attached scsi generic sg1 type 5                                    
ata4: port disabled. ignoring.                                                  
ACPI: PCI Interrupt Link [ASA1] enabled at IRQ 20                               
  alloc irq_desc for 20 on cpu 0 node 0                                         
  alloc kstat_irqs on cpu 0 node 0                                              
sata_nv 0000:00:0e.1: PCI INT B -> Link[ASA1] -> GSI 20 (level, low) -> IRQ 20  
sata_nv 0000:00:0e.1: Using SWNCQ mode                                          
sata_nv 0000:00:0e.1: setting latency timer to 64                               
scsi5 : sata_nv                                                                 
scsi6 : sata_nv                                                                 
ata5: SATA max UDMA/133 cmd 0x9e0 ctl 0xbe0 bmdma 0xc400 irq 20                 
ata6: SATA max UDMA/133 cmd 0x960 ctl 0xb60 bmdma 0xc408 irq 20                 
firewire_core: created device fw0: GUID 1aa205bc00044b06, S400                  
ata5: SATA link down (SStatus 0 SControl 300)                                   
ata6: SATA link down (SStatus 0 SControl 300)                                   
ACPI: PCI Interrupt Link [ASA2] enabled at IRQ 23                               
sata_nv 0000:00:0e.2: PCI INT C -> Link[ASA2] -> GSI 23 (level, low) -> IRQ 23  
sata_nv 0000:00:0e.2: Using SWNCQ mode                                          
sata_nv 0000:00:0e.2: setting latency timer to 64                               
scsi7 : sata_nv                                                                 
scsi8 : sata_nv                                                                 
ata7: SATA max UDMA/133 cmd 0xc000 ctl 0xbc00 bmdma 0xb000 irq 23               
ata8: SATA max UDMA/133 cmd 0xb800 ctl 0xb400 bmdma 0xb008 irq 23               
ata7: SATA link down (SStatus 0 SControl 300)                                   
ata8: SATA link down (SStatus 0 SControl 300)                                   
ISO 9660 Extensions: Microsoft Joliet Level 3                                   
ISO 9660 Extensions: RRIP_1991A                                                 
squashfs: version 4.0 (2009/01/31) Phillip Lougher                              
EXT4-fs: barriers enabled                                                       
kjournald2 starting: pid 751, dev dm-0:8, commit interval 5 seconds             
EXT4 FS on dm-0, internal journal on dm-0:8                                     
EXT4-fs: delayed allocation enabled                                             
EXT4-fs: file extents enabled                                                   
EXT4-fs: mballoc enabled                                                        
EXT4-fs: mounted filesystem dm-0 with ordered data mode                         
JBD: barrier-based sync failed on dm-0:8 - disabling barriers                   
type=1404 audit(1254151100.535:2): enforcing=1 old_enforcing=0 auid=4294967295 ses=4294967295                                                                   
SELinux: 8192 avtab hash slots, 123719 rules.                                   
SELinux: 8192 avtab hash slots, 123719 rules.                                   
SELinux:  8 users, 11 roles, 2722 types, 127 bools, 1 sens, 1024 cats           
SELinux:  74 classes, 123719 rules                                              
SELinux:  Completing initialization.                                            
SELinux:  Setting up existing superblocks.                                      
SELinux: initialized (dev dm-0, type ext4), uses xattr                          
SELinux: inode_doinit_with_dentry:  no dentry for dev=dm-0 ino=35225            
SELinux: inode_doinit_with_dentry:  no dentry for dev=dm-0 ino=26316            
SELinux: inode_doinit_with_dentry:  no dentry for dev=dm-0 ino=26313            
SELinux: inode_doinit_with_dentry:  no dentry for dev=dm-0 ino=253              
SELinux: initialized (dev loop2, type squashfs), not configured for labeling    
SELinux: initialized (dev loop0, type squashfs), not configured for labeling    
SELinux: initialized (dev sr0, type iso9660), uses genfs_contexts               
SELinux: initialized (dev tmpfs, type tmpfs), uses transition SIDs              
SELinux: initialized (dev usbfs, type usbfs), uses genfs_contexts               
SELinux: initialized (dev selinuxfs, type selinuxfs), uses genfs_contexts       
SELinux: initialized (dev mqueue, type mqueue), uses transition SIDs            
SELinux: initialized (dev hugetlbfs, type hugetlbfs), uses genfs_contexts       
SELinux: initialized (dev devpts, type devpts), uses transition SIDs            
SELinux: initialized (dev inotifyfs, type inotifyfs), uses genfs_contexts       
SELinux: initialized (dev tmpfs, type tmpfs), uses transition SIDs              
SELinux: initialized (dev anon_inodefs, type anon_inodefs), uses genfs_contexts 
SELinux: initialized (dev pipefs, type pipefs), uses task SIDs                  
SELinux: initialized (dev debugfs, type debugfs), uses genfs_contexts           
SELinux: initialized (dev sockfs, type sockfs), uses task SIDs                  
SELinux: initialized (dev proc, type proc), uses genfs_contexts                 
SELinux: initialized (dev bdev, type bdev), uses genfs_contexts                 
SELinux: initialized (dev rootfs, type rootfs), uses genfs_contexts             
SELinux: initialized (dev sysfs, type sysfs), uses genfs_contexts               
type=1403 audit(1254151101.174:3): policy loaded auid=4294967295 ses=4294967295 
udev: starting version 141                                                      
forcedeth: Reverse Engineered nForce ethernet driver. Version 0.62.             
ACPI: PCI Interrupt Link [AMAC] enabled at IRQ 22                               
forcedeth 0000:00:11.0: PCI INT A -> Link[AMAC] -> GSI 22 (level, low) -> IRQ 22
forcedeth 0000:00:11.0: setting latency timer to 64                             
nv_probe: set workaround bit for reversed mac addr                              
input: PC Speaker as /devices/platform/pcspkr/input/input5                      
forcedeth 0000:00:11.0: ifname eth0, PHY OUI 0x5043 @ 1, addr 00:04:4b:05:18:da 
forcedeth 0000:00:11.0: highdma csum vlan pwrctl mgmt timirq gbit lnktim msi desc-v3                                                                            
i2c-adapter i2c-0: nForce2 SMBus adapter at 0xf400                              
i2c-adapter i2c-1: nForce2 SMBus adapter at 0xf000                              
ACPI: PCI Interrupt Link [AMA1] enabled at IRQ 21                               
forcedeth 0000:00:12.0: PCI INT A -> Link[AMA1] -> GSI 21 (level, low) -> IRQ 21
forcedeth 0000:00:12.0: setting latency timer to 64                             
nv_probe: set workaround bit for reversed mac addr                              
forcedeth 0000:00:12.0: ifname eth1, PHY OUI 0x5043 @ 2, addr 00:04:4b:05:18:db 
forcedeth 0000:00:12.0: highdma csum vlan pwrctl mgmt timirq gbit lnktim msi desc-v3                                                                            
Linux video capture interface: v2.00                                            
gspca: main v2.5.0 registered                                                   
gspca: probing 0ac8:303b                                                        
ACPI: PCI Interrupt Link [AAZA] enabled at IRQ 20                               
HDA Intel 0000:00:0f.1: PCI INT B -> Link[AAZA] -> GSI 20 (level, low) -> IRQ 20
HDA Intel 0000:00:0f.1: setting latency timer to 64                             
hda_codec: Unknown model for ALC883, trying auto-probe from BIOS...             
ALSA sound/pci/hda/hda_codec.c:3507: autoconfig: line_outs=4 (0x14/0x15/0x16/0x17/0x0)                                                                          
ALSA sound/pci/hda/hda_codec.c:3511:    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)    
ALSA sound/pci/hda/hda_codec.c:3515:    hp_outs=1 (0x1b/0x0/0x0/0x0/0x0)        
ALSA sound/pci/hda/hda_codec.c:3516:    mono: mono_out=0x0                      
ALSA sound/pci/hda/hda_codec.c:3524:    inputs: mic=0x18, fmic=0x19, line=0x1a, fline=0x0, cd=0x0, aux=0x0                                                      
zc3xx: probe 2wr ov vga 0x0000                                                  
zc3xx: probe 3wr vga 1 0xe001                                                   
zc3xx: probe sensor -> 0013                                                     
zc3xx: Find Sensor MI0360. Chip revision e001                                   
gspca: probe ok                                                                 
usbcore: registered new interface driver zc3xx                                  
zc3xx: registered                                                               
device-mapper: multipath: version 1.0.5 loaded                                  
EXT4 FS on dm-0, internal journal on dm-0:8                                     
SELinux: initialized (dev tmpfs, type tmpfs), uses transition SIDs              
SELinux: initialized (dev binfmt_misc, type binfmt_misc), uses genfs_contexts   
SELinux: initialized (dev tmpfs, type tmpfs), uses transition SIDs              
SELinux: initialized (dev tmpfs, type tmpfs), uses transition SIDs              
SELinux: initialized (dev tmpfs, type tmpfs), uses transition SIDs              
JBD: barrier-based sync failed on dm-0:8 - disabling barriers                   
platform microcode: firmware: requesting intel-ucode/0f-06-04                   
platform microcode: firmware: requesting intel-ucode/0f-06-04                   
Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba       
Microcode Update Driver: v2.00 removed.                                         
p4-clockmod: P4/Xeon(TM) CPU On-Demand Clock Modulation available               
NET: Registered protocol family 10                                              
lo: Disabled Privacy Extensions                                                 
ip6_tables: (C) 2000-2006 Netfilter Core Team                                   
RPC: Registered udp transport module.                                           
RPC: Registered tcp transport module.                                           
SELinux: initialized (dev rpc_pipefs, type rpc_pipefs), uses genfs_contexts     
  alloc irq_desc for 25 on cpu 0 node 0                                         
  alloc kstat_irqs on cpu 0 node 0                                              
forcedeth 0000:00:12.0: irq 25 for MSI/MSI-X                                    
eth1: no link during initialization.                                            
ADDRCONF(NETDEV_UP): eth1: link is not ready                                    
  alloc irq_desc for 26 on cpu 0 node 0                                         
  alloc kstat_irqs on cpu 0 node 0                                              
forcedeth 0000:00:11.0: irq 26 for MSI/MSI-X                                    
eth0: no link during initialization.                                            
ADDRCONF(NETDEV_UP): eth0: link is not ready                                    
nouveau 0000:01:00.0: Allocating FIFO number 1                                  
nouveau 0000:01:00.0: nouveau_fifo_alloc: initialised FIFO 1                    
nouveau 0000:01:00.0: Allocating FIFO number 2                                  
nouveau 0000:01:00.0: nouveau_fifo_alloc: initialised FIFO 2                    
audit(1254165568.120:24760): auid=4294967295 ses=4294967295 subj=system_u:system_r:readahead_t:s0 op=remove rule key=(null) list=2 res=1                        
audit(1254165568.120:24761): audit_enabled=0 old=1 auid=4294967295 ses=4294967295 subj=system_u:system_r:readahead_t:s0 res=1                                   
CPU0 attaching NULL sched-domain.                                               
CPU1 attaching NULL sched-domain.                                               
CPU0 attaching sched-domain:                                                    
 domain 0: span 0-1 level CPU                                                   
  groups: 0 1                                                                   
CPU1 attaching sched-domain:                                                    
 domain 0: span 0-1 level CPU                                                   
  groups: 1 0                                                                   
CPU0 attaching NULL sched-domain.                                               
CPU1 attaching NULL sched-domain.                                               
CPU0 attaching sched-domain:                                                    
 domain 0: span 0-1 level CPU                                                   
  groups: 0 1                                                                   
CPU1 attaching sched-domain:                                                    
 domain 0: span 0-1 level CPU                                                   
  groups: 1 0                                                                   
nouveau 0000:01:00.0: PGRAPH_ERROR - nSource: PROTECTION_ERROR DMA_R_PROTECTION, nStatus:                                                                       
nouveau 0000:01:00.0: PGRAPH_ERROR - Ch 2/2 Class 0x8297 Mthd 0x15e0 Data 0x00000000:0x00000000                                                                 
nouveau 0000:01:00.0: magic set 1:                                              
nouveau 0000:01:00.0:   0x00408900: 0x80000045                                  
nouveau 0000:01:00.0:   0x00408904: 0xfd7b1f7d                                  
nouveau 0000:01:00.0:   0x00408908: 0xba8fdf8e                                  
nouveau 0000:01:00.0:   0x0040890c: 0x400099fb                                  
nouveau 0000:01:00.0:   0x00408910: 0xbcbf26f3                                  
nouveau 0000:01:00.0:   0x00408e08: 0x80018e9e                                  
nouveau 0000:01:00.0:   0x00408e0c: 0x00000000                                  
nouveau 0000:01:00.0:   0x00408e10: 0xb7a89bc5                                  
nouveau 0000:01:00.0:   0x00408e14: 0x000000f9                                  
nouveau 0000:01:00.0:   0x00408e18: 0x48940e4c                                  
nouveau 0000:01:00.0:   0x00408e1c: 0xcf6b8e7f                                  
nouveau 0000:01:00.0:   0x00408e20: 0x350b3f0b                                  
nouveau 0000:01:00.0:   0x00408e24: 0x0913011b                                  
nouveau 0000:01:00.0: magic set 2:                                              
nouveau 0000:01:00.0:   0x00409900: 0x80000048                                  
nouveau 0000:01:00.0:   0x00409904: 0xaffbefb1                                  
nouveau 0000:01:00.0:   0x00409908: 0xff6f8d7d                                  
nouveau 0000:01:00.0:   0x0040990c: 0xc0001242                                  
nouveau 0000:01:00.0:   0x00409910: 0xffff1ddd                                  
nouveau 0000:01:00.0:   0x00409e08: 0x8001a70c                                  
nouveau 0000:01:00.0:   0x00409e0c: 0x00000000                                  
nouveau 0000:01:00.0:   0x00409e10: 0x315f6ffb                                  
nouveau 0000:01:00.0:   0x00409e14: 0x000000ff                                  
nouveau 0000:01:00.0:   0x00409e18: 0x1c431113                                  
nouveau 0000:01:00.0:   0x00409e1c: 0xaa1fffdf                                  
nouveau 0000:01:00.0:   0x00409e20: 0x0434185a                                  
nouveau 0000:01:00.0:   0x00409e24: 0x0b22030b                                  
nouveau 0000:01:00.0: PGRAPH_ERROR - nSource: PROTECTION_ERROR DMA_R_PROTECTION, nStatus:                                                                       
nouveau 0000:01:00.0: PGRAPH_ERROR - Ch 2/2 Class 0x8297 Mthd 0x15e0 Data 0x00000000:0x00000000                                                                 
nouveau 0000:01:00.0: magic set 1:                                              
nouveau 0000:01:00.0:   0x00408900: 0x80000000                                  
nouveau 0000:01:00.0:   0x00408904: 0xfd7b1f7d                                  
nouveau 0000:01:00.0:   0x00408908: 0xba8fdf8e                                  
nouveau 0000:01:00.0:   0x0040890c: 0x400099fb                                  
nouveau 0000:01:00.0:   0x00408910: 0xbcbf26f3                                  
nouveau 0000:01:00.0:   0x00408e08: 0x80000000                                  
nouveau 0000:01:00.0:   0x00408e0c: 0x00000000                                  
nouveau 0000:01:00.0:   0x00408e10: 0x00000000                                  
nouveau 0000:01:00.0:   0x00408e14: 0x00000000                                  
nouveau 0000:01:00.0:   0x00408e18: 0x00000000                                  
nouveau 0000:01:00.0:   0x00408e1c: 0x00000000                                  
nouveau 0000:01:00.0:   0x00408e20: 0x00000000                                  
nouveau 0000:01:00.0:   0x00408e24: 0x00000000                                  
nouveau 0000:01:00.0: magic set 2:                                              
nouveau 0000:01:00.0:   0x00409900: 0x80000000                                  
nouveau 0000:01:00.0:   0x00409904: 0xaffbefb1                                  
nouveau 0000:01:00.0:   0x00409908: 0xff6f8d7d                                  
nouveau 0000:01:00.0:   0x0040990c: 0xc0001242                                  
nouveau 0000:01:00.0:   0x00409910: 0xffff1ddd                                  
nouveau 0000:01:00.0:   0x00409e08: 0x80000000                                  
nouveau 0000:01:00.0:   0x00409e0c: 0x00000000                                  
nouveau 0000:01:00.0:   0x00409e10: 0x00000000                                  
nouveau 0000:01:00.0:   0x00409e14: 0x00000000                                  
nouveau 0000:01:00.0:   0x00409e18: 0x00000000                                  
nouveau 0000:01:00.0:   0x00409e1c: 0x00000000                                  
nouveau 0000:01:00.0:   0x00409e20: 0x00000000                                  
nouveau 0000:01:00.0:   0x00409e24: 0x00000000                                  
ALSA sound/pci/hda/hda_intel.c:1101: Too big adjustment 32: adj=128, bytes=128, size=4096, periods=32                                                           
ALSA sound/pci/hda/hda_intel.c:1101: Too big adjustment 32: adj=128, bytes=128, size=4096, periods=32                                                           
ALSA sound/pci/hda/hda_intel.c:1101: Too big adjustment 32: adj=128, bytes=128, size=4096, periods=32                                                           
ALSA sound/pci/hda/hda_intel.c:1101: Too big adjustment 32: adj=128, bytes=128, size=4096, periods=32                                                           
ALSA sound/pci/hda/hda_intel.c:1101: Too big adjustment 32: adj=128, bytes=128, size=4096, periods=32                                                           
ALSA sound/pci/hda/hda_intel.c:1101: Too big adjustment 32: adj=128, bytes=128, size=4096, periods=32
ALSA sound/pci/hda/hda_intel.c:1101: Too big adjustment 32: adj=256, bytes=128,size=4096, periods=32
ALSA sound/pci/hda/hda_intel.c:1101: Too big adjustment 32: adj=128, bytes=128,size=4096, periods=32
ALSA sound/pci/hda/hda_intel.c:1101: Too big adjustment 32: adj=128, bytes=128,size=4096, periods=32
ALSA sound/pci/hda/hda_intel.c:1101: Too big adjustment 32: adj=384, bytes=384,size=12288, periods=32
ALSA sound/pci/hda/hda_intel.c:1101: Too big adjustment 32: adj=128, bytes=128,size=4096, periods=32
ALSA sound/pci/hda/hda_intel.c:1101: Too big adjustment 32: adj=128, bytes=128,size=4096, periods=32
ALSA sound/pci/hda/hda_intel.c:1101: Too big adjustment 32: adj=384, bytes=384,size=12288, periods=32
ALSA sound/pci/hda/hda_intel.c:1101: Too big adjustment 32: adj=128, bytes=128,size=4096, periods=32
ALSA sound/pci/hda/hda_intel.c:1101: Too big adjustment 32: adj=128, bytes=128,size=4096, periods=32
ALSA sound/pci/hda/hda_intel.c:1101: Too big adjustment 32: adj=384, bytes=384,size=12288, periods=32
ALSA sound/pci/hda/hda_intel.c:1101: Too big adjustment 32: adj=128, bytes=128,size=4096, periods=32
ALSA sound/pci/hda/hda_intel.c:1101: Too big adjustment 32: adj=128, bytes=128,size=4096, periods=32
ALSA sound/pci/hda/hda_intel.c:1101: Too big adjustment 32: adj=512, bytes=128,size=4096, periods=32
ALSA sound/pci/hda/hda_intel.c:1101: Too big adjustment 32: adj=128, bytes=128,size=4096, periods=32
ALSA sound/pci/hda/hda_intel.c:1101: Too big adjustment 32: adj=128, bytes=128,size=4096, periods=32
ALSA sound/pci/hda/hda_intel.c:1101: Too big adjustment 32: adj=128, bytes=128,size=4096, periods=32
ALSA sound/pci/hda/hda_intel.c:1101: Too big adjustment 32: adj=128, bytes=128,size=4096, periods=32
**[root@localhost ~]#**
```

---

### Post by C0NSTANTIN on 2009-09-28
Terminal
```
 
**[liveuser@localhost ~]$ lspci**
00:00.0 Host bridge: nVidia Corporation C55 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.3 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.4 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.5 RAM memory: nVidia Corporation C55 Memory Controller (rev a2)
00:00.6 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.7 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.0 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.1 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.3 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.4 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.5 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.6 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:02.0 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:02.1 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:02.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:03.0 PCI bridge: nVidia Corporation C55 PCI Express bridge (rev a1)
00:09.0 RAM memory: nVidia Corporation MCP55 Memory Controller (rev a1)
00:0a.0 ISA bridge: nVidia Corporation MCP55 LPC Bridge (rev a2)       
00:0a.1 SMBus: nVidia Corporation MCP55 SMBus (rev a2)                 
00:0b.0 USB Controller: nVidia Corporation MCP55 USB Controller (rev a1)
00:0b.1 USB Controller: nVidia Corporation MCP55 USB Controller (rev a2)
00:0d.0 IDE interface: nVidia Corporation MCP55 IDE (rev a1)            
00:0e.0 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a2)
00:0e.1 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a2)
00:0e.2 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a2)
00:0f.0 PCI bridge: nVidia Corporation MCP55 PCI bridge (rev a2)        
00:0f.1 Audio device: nVidia Corporation MCP55 High Definition Audio (rev a2)
00:11.0 Bridge: nVidia Corporation MCP55 Ethernet (rev a2)                   
00:12.0 Bridge: nVidia Corporation MCP55 Ethernet (rev a2)                   
01:00.0 VGA compatible controller: nVidia Corporation GeForce 9800 GT (rev a2)
02:07.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)                                                               
**[liveuser@localhost ~]$ dmesg                                                   **
Initializing cgroup subsys cpuset                                               
Initializing cgroup subsys cpu                                                  
Linux version 2.6.29.4-167.fc11.x86_64 (mockbuild@xenbuilder4.fedora.phx.redhat.com) (gcc version 4.4.0 20090506 (Red Hat 4.4.0-4) (GCC) ) #1 SMP Wed May 27 17:27:08 EDT 2009                                                                  
Command line: initrd=initrd0.img root=CDLABEL=Fedora-11-x86_64-Live-KDE rootfstype=auto ro liveimg quiet  rhgb  BOOT_IMAGE=vmlinuz0                             
KERNEL supported cpus:                                                          
  Intel GenuineIntel                                                            
  AMD AuthenticAMD                                                              
  Centaur CentaurHauls                                                          
BIOS-provided physical RAM map:                                                 
 BIOS-e820: 0000000000000000 - 000000000009f000 (usable)                        
 BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)                      
 BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)                      
 BIOS-e820: 0000000000100000 - 000000007fef0000 (usable)                        
 BIOS-e820: 000000007fef0000 - 000000007fef3000 (ACPI NVS)                      
 BIOS-e820: 000000007fef3000 - 000000007ff00000 (ACPI data)                     
 BIOS-e820: 00000000d0000000 - 00000000f0000000 (reserved)                      
 BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)                      
DMI 2.4 present.                                                                
Phoenix BIOS detected: BIOS may corrupt low RAM, working around it.             
last_pfn = 0x7fef0 max_arch_pfn = 0x100000000                                   
x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106                
original variable MTRRs                                                         
reg 0, base: 0GB, range: 2GB, type WB                                           
reg 1, base: 2047MB, range: 1MB, type UC                                        
total RAM coverred: 2047M                                                       
Found optimal setting for mtrr clean up                                         
 gran_size: 64K         chunk_size: 2M  num_reg: 2      lose cover RAM: 0G      
New variable MTRRs                                                              
reg 0, base: 0GB, range: 2GB, type WB                                           
reg 1, base: 2047MB, range: 1MB, type UC                                        
x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106                
init_memory_mapping: 0000000000000000-000000007fef0000                          
 0000000000 - 007fe00000 page 2M                                                
 007fe00000 - 007fef0000 page 4k                                                
kernel direct mapping tables up to 7fef0000 @ 10000-14000                       
last_map_addr: 7fef0000 end: 7fef0000                                           
RAMDISK: 7f9de000 - 7feced39                                                    
ACPI: RSDP 000F7F30, 0014 (r0 Nvidia)                                           
ACPI: RSDT 7FEF3040, 0038 (r1 Nvidia NVDAACPI 42302E31 NVDA        0)           
ACPI: FACP 7FEF30C0, 0074 (r1 Nvidia NVDAACPI 42302E31 NVDA        0)           
FADT: X_PM1a_EVT_BLK.bit_width (16) does not match PM1_EVT_LEN (4)              
ACPI: DSDT 7FEF3180, 5349 (r1 NVIDIA NVDAACPI     1000 MSFT  3000000)           
ACPI: FACS 7FEF0000, 0040                                                       
ACPI: HPET 7FEF8640, 003C (r1 Nvidia NVDAACPI 42302E31 NVDA        0)           
ACPI: WDRT 7FEF86C0, 0047 (r1 Nvidia NVDAACPI 42302E31 NVDA        0)           
ACPI: MCFG 7FEF8780, 003C (r1 Nvidia NVDAACPI 42302E31 NVDA        0)           
ACPI: APIC 7FEF8540, 0098 (r1 Nvidia NVDAACPI 42302E31 NVDA        0)           
ACPI: Local APIC address 0xfee00000                                             
No NUMA configuration found                                                     
Faking a node at 0000000000000000-000000007fef0000                              
Bootmem setup node 0 0000000000000000-000000007fef0000                          
  NODE_DATA [0000000000012000 - 0000000000026fff]                               
  bootmap [0000000000027000 -  0000000000036fdf] pages 10                       
(6 early reservations) ==> bootmem [0000000000 - 007fef0000]                    
  #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]   
  #1 [0000006000 - 0000008000]       TRAMPOLINE ==> [0000006000 - 0000008000]   
  #2 [0000200000 - 0000ac700c]    TEXT DATA BSS ==> [0000200000 - 0000ac700c]   
  #3 [007f9de000 - 007feced39]          RAMDISK ==> [007f9de000 - 007feced39]   
  #4 [000009f000 - 0000100000]    BIOS reserved ==> [000009f000 - 0000100000]   
  #5 [0000010000 - 0000012000]          PGTABLE ==> [0000010000 - 0000012000]   
found SMP MP-table at [ffff8800000f3f60] 000f3f60                               
 [ffffe20000000000-ffffe20001bfffff] PMD -> [ffff880001200000-ffff880002dfffff] on node 0                                                                       
Zone PFN ranges:                                                                
  DMA      0x00000010 -> 0x00001000                                             
  DMA32    0x00001000 -> 0x00100000                                             
  Normal   0x00100000 -> 0x00100000                                             
Movable zone start PFN for each node                                            
early_node_map[2] active PFN ranges                                             
    0: 0x00000010 -> 0x0000009f                                                 
    0: 0x00000100 -> 0x0007fef0                                                 
On node 0 totalpages: 523903                                                    
  DMA zone: 56 pages used for memmap                                            
  DMA zone: 2351 pages reserved                                                 
  DMA zone: 1576 pages, LIFO batch:0                                            
  DMA32 zone: 7109 pages used for memmap                                        
  DMA32 zone: 512811 pages, LIFO batch:31                                       
ACPI: PM-Timer IO Port: 0x1008                                                  
ACPI: Local APIC address 0xfee00000                                             
ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)                              
ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)                              
ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] disabled)                             
ACPI: LAPIC (acpi_id[0x03] lapic_id[0x03] disabled)                             
ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])                             
ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])                             
ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])                             
ACPI: LAPIC_NMI (acpi_id[0x03] high edge lint[0x1])                             
ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])                         
IOAPIC[0]: apic_id 4, version 0, address 0xfec00000, GSI 0-23                   
ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)                        
ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)                     
ACPI: INT_SRC_OVR (bus 0 bus_irq 14 global_irq 14 high edge)                    
ACPI: INT_SRC_OVR (bus 0 bus_irq 15 global_irq 15 high edge)                    
ACPI: IRQ0 used by override.                                                    
ACPI: IRQ2 used by override.                                                    
ACPI: IRQ9 used by override.                                                    
ACPI: IRQ14 used by override.                                                   
ACPI: IRQ15 used by override.                                                   
Using ACPI (MADT) for SMP configuration information                             
ACPI: HPET timers must be located in memory.                                    
SMP: Allowing 4 CPUs, 2 hotplug CPUs                                            
nr_irqs_gsi: 24                                                                 
PM: Registered nosave memory: 000000000009f000 - 00000000000a0000               
PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000               
PM: Registered nosave memory: 00000000000f0000 - 0000000000100000               
Allocating PCI resources starting at 80000000 (gap: 7ff00000:50100000)          
NR_CPUS:64 nr_cpumask_bits:64 nr_cpu_ids:4 nr_node_ids:1                        
PERCPU: Allocating 57344 bytes of per cpu data                                  
Built 1 zonelists in Node order, mobility grouping on.  Total pages: 514387     
Policy zone: DMA32                                                              
Kernel command line: initrd=initrd0.img root=CDLABEL=Fedora-11-x86_64-Live-KDE rootfstype=auto ro liveimg quiet  rhgb  BOOT_IMAGE=vmlinuz0                      
Initializing CPU#0                                                              
PID hash table entries: 4096 (order: 12, 32768 bytes)                           
Fast TSC calibration using PIT                                                  
Detected 3400.359 MHz processor.                                                
spurious 8259A interrupt: IRQ7.                                                 
Console: colour VGA+ 80x25                                                      
console [tty0] enabled                                                          
allocated 20971520 bytes of page_cgroup                                         
please try cgroup_disable=memory option if you don't want                       
Checking aperture...                                                            
No AGP bridge found                                                             
Calgary: detecting Calgary via BIOS EBDA area                                   
Calgary: Unable to locate Rio Grande table in EBDA - bailing!                   
Memory: 2031896k/2096064k available (3786k kernel code, 452k absent, 63716k reserved, 2294k data, 1304k init)                                                   
SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1         
Calibrating delay loop (skipped), value calculated using timer frequency.. 6800.71 BogoMIPS (lpj=3400359)                                                       
Security Framework initialized                                                  
SELinux:  Initializing.                                                         
SELinux:  Starting in permissive mode                                           
Dentry cache hash table entries: 262144 (order: 9, 2097152 bytes)               
Inode-cache hash table entries: 131072 (order: 8, 1048576 bytes)                
Mount-cache hash table entries: 256                                             
Initializing cgroup subsys ns                                                   
Initializing cgroup subsys cpuacct                                              
Initializing cgroup subsys memory                                               
Initializing cgroup subsys devices                                              
Initializing cgroup subsys freezer                                              
Initializing cgroup subsys net_cls                                              
CPU: Trace cache: 12K uops, L1 D cache: 16K                                     
CPU: L2 cache: 2048K                                                            
CPU 0/0x0 -> Node 0                                                             
CPU: Physical Processor ID: 0                                                   
CPU: Processor Core ID: 0                                                       
CPU0: Thermal monitoring enabled (TM1)                                          
using mwait in idle threads.                                                    
ACPI: Core revision 20081204                                                    
ftrace: converting mcount calls to 0f 1f 44 00 00                               
ftrace: allocating 18888 entries in 149 pages                                   
Setting APIC routing to flat                                                    
..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1                            
CPU0: Intel(R) Pentium(R) D CPU 3.40GHz stepping 04                             
Booting processor 1 APIC 0x1 ip 0x6000                                          
Initializing CPU#1                                                              
Calibrating delay using timer specific routine.. 6798.57 BogoMIPS (lpj=3399285) 
CPU: Trace cache: 12K uops, L1 D cache: 16K                                     
CPU: L2 cache: 2048K                                                            
CPU 1/0x1 -> Node 0                                                             
CPU: Physical Processor ID: 0                                                   
CPU: Processor Core ID: 1                                                       
CPU1: Thermal monitoring enabled (TM1)                                          
x86 PAT enabled: cpu 1, old 0x7040600070406, new 0x7010600070106                
CPU1: Intel(R) Pentium(R) D CPU 3.40GHz stepping 04                             
checking TSC synchronization [CPU#0 -> CPU#1]: passed.                          
Brought up 2 CPUs                                                               
Total of 2 processors activated (13599.28 BogoMIPS).                            
sizeof(vma)=176 bytes                                                           
sizeof(page)=56 bytes                                                           
sizeof(inode)=560 bytes                                                         
sizeof(dentry)=192 bytes                                                        
sizeof(ext3inode)=760 bytes                                                     
sizeof(buffer_head)=104 bytes                                                   
sizeof(skbuff)=232 bytes                                                        
sizeof(task_struct)=5880 bytes                                                  
CPU0 attaching sched-domain:                                                    
 domain 0: span 0-1 level CPU                                                   
  groups: 0 1                                                                   
CPU1 attaching sched-domain:                                                    
 domain 0: span 0-1 level CPU                                                   
  groups: 1 0                                                                   
net_namespace: 1904 bytes                                                       
Booting paravirtualized kernel on bare hardware                                 
regulator: core version 0.5                                                     
Time: 15:30:42  Date: 09/28/09                                                  
NET: Registered protocol family 16                                              
ACPI: bus type pci registered                                                   
PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255                
PCI: MCFG area at e0000000 reserved in E820                                     
PCI: Using MMCONFIG at e0000000 - efffffff                                      
PCI: Using configuration type 1 for base access                                 
bio: create slab <bio-0> at 0                                                   
ACPI: EC: Look up EC in DSDT                                                    
ACPI: Interpreter enabled                                                       
ACPI: (supports S0 S1 S3 S4 S5)                                                 
ACPI: Using IOAPIC for interrupt routing                                        
ACPI: No dock devices found.                                                    
ACPI: PCI Root Bridge [PCI0] (0000:00)                                          
pci 0000:00:03.0: PME# supported from D0 D1 D2 D3hot D3cold                     
pci 0000:00:03.0: PME# disabled                                                 
pci 0000:00:0a.0: reg 10 io port: [0xfc00-0xfc7f]                               
HPET not enabled in BIOS. You might try hpet=force boot option                  
pci 0000:00:0a.1: reg 10 io port: [0xf800-0xf83f]                               
pci 0000:00:0a.1: reg 20 io port: [0xf400-0xf43f]                               
pci 0000:00:0a.1: reg 24 io port: [0xf000-0xf03f]                               
pci 0000:00:0a.1: PME# supported from D3hot D3cold                              
pci 0000:00:0a.1: PME# disabled                                                 
pci 0000:00:0b.0: reg 10 32bit mmio: [0xcffff000-0xcfffffff]                    
pci 0000:00:0b.0: supports D1 D2                                                
pci 0000:00:0b.0: PME# supported from D0 D1 D2 D3hot D3cold                     
pci 0000:00:0b.0: PME# disabled                                                 
pci 0000:00:0b.1: reg 10 32bit mmio: [0xcfffe000-0xcfffe0ff]                    
pci 0000:00:0b.1: supports D1 D2                                                
pci 0000:00:0b.1: PME# supported from D0 D1 D2 D3hot D3cold                     
pci 0000:00:0b.1: PME# disabled                                                 
pci 0000:00:0d.0: reg 20 io port: [0xec00-0xec0f]                               
pci 0000:00:0e.0: reg 10 io port: [0x9f0-0x9f7]                                 
pci 0000:00:0e.0: reg 14 io port: [0xbf0-0xbf3]                                 
pci 0000:00:0e.0: reg 18 io port: [0x970-0x977]                                 
pci 0000:00:0e.0: reg 1c io port: [0xb70-0xb73]                                 
pci 0000:00:0e.0: reg 20 io port: [0xd800-0xd80f]                               
pci 0000:00:0e.0: reg 24 32bit mmio: [0xcfffd000-0xcfffdfff]                    
pci 0000:00:0e.1: reg 10 io port: [0x9e0-0x9e7]                                 
pci 0000:00:0e.1: reg 14 io port: [0xbe0-0xbe3]                                 
pci 0000:00:0e.1: reg 18 io port: [0x960-0x967]                                 
pci 0000:00:0e.1: reg 1c io port: [0xb60-0xb63]                                 
pci 0000:00:0e.1: reg 20 io port: [0xc400-0xc40f]                               
pci 0000:00:0e.1: reg 24 32bit mmio: [0xcfffc000-0xcfffcfff]                    
pci 0000:00:0e.2: reg 10 io port: [0xc000-0xc007]                               
pci 0000:00:0e.2: reg 14 io port: [0xbc00-0xbc03]                               
pci 0000:00:0e.2: reg 18 io port: [0xb800-0xb807]                               
pci 0000:00:0e.2: reg 1c io port: [0xb400-0xb403]                               
pci 0000:00:0e.2: reg 20 io port: [0xb000-0xb00f]                               
pci 0000:00:0e.2: reg 24 32bit mmio: [0xcfffb000-0xcfffbfff]                    
pci 0000:00:0f.1: reg 10 32bit mmio: [0xcfff0000-0xcfff3fff]                    
pci 0000:00:0f.1: PME# supported from D3hot D3cold                              
pci 0000:00:0f.1: PME# disabled                                                 
pci 0000:00:11.0: reg 10 32bit mmio: [0xcfffa000-0xcfffafff]                    
pci 0000:00:11.0: reg 14 io port: [0xac00-0xac07]                               
pci 0000:00:11.0: reg 18 32bit mmio: [0xcfff9000-0xcfff90ff]                    
pci 0000:00:11.0: reg 1c 32bit mmio: [0xcfff8000-0xcfff800f]                    
pci 0000:00:11.0: supports D1 D2                                                
pci 0000:00:11.0: PME# supported from D0 D1 D2 D3hot D3cold                     
pci 0000:00:11.0: PME# disabled                                                 
pci 0000:00:12.0: reg 10 32bit mmio: [0xcfff7000-0xcfff7fff]                    
pci 0000:00:12.0: reg 14 io port: [0xa800-0xa807]                               
pci 0000:00:12.0: reg 18 32bit mmio: [0xcfff6000-0xcfff60ff]                    
pci 0000:00:12.0: reg 1c 32bit mmio: [0xcfff5000-0xcfff500f]                    
pci 0000:00:12.0: supports D1 D2                                                
pci 0000:00:12.0: PME# supported from D0 D1 D2 D3hot D3cold                     
pci 0000:00:12.0: PME# disabled                                                 
pci 0000:01:00.0: reg 10 32bit mmio: [0xcc000000-0xccffffff]                    
pci 0000:01:00.0: reg 14 64bit mmio: [0xb0000000-0xbfffffff]                    
pci 0000:01:00.0: reg 1c 64bit mmio: [0xca000000-0xcbffffff]                    
pci 0000:01:00.0: reg 24 io port: [0x9c00-0x9c7f]                               
pci 0000:01:00.0: reg 30 32bit mmio: [0x000000-0x01ffff]                        
pci 0000:00:03.0: bridge io port: [0x9000-0x9fff]                               
pci 0000:00:03.0: bridge 32bit mmio: [0xca000000-0xcdffffff]                    
pci 0000:00:03.0: bridge 64bit mmio pref: [0xb0000000-0xbfffffff]               
pci 0000:02:07.0: reg 10 32bit mmio: [0xcfdff000-0xcfdff7ff]                    
pci 0000:02:07.0: reg 14 32bit mmio: [0xcfdf8000-0xcfdfbfff]                    
pci 0000:02:07.0: supports D1 D2                                                
pci 0000:02:07.0: PME# supported from D0 D1 D2 D3hot                            
pci 0000:02:07.0: PME# disabled                                                 
pci 0000:00:0f.0: transparent bridge                                            
pci 0000:00:0f.0: bridge io port: [0x8000-0x8fff]                               
pci 0000:00:0f.0: bridge 32bit mmio: [0xcfd00000-0xcfdfffff]                    
pci 0000:00:0f.0: bridge 32bit mmio pref: [0xcfe00000-0xcfefffff]               
ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]                             
ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]                        
ACPI Warning (nspredef-0940): \_SB_.PCI0.HUB0._PRT: Return Package type mismatch at index 2 - found [NULL Object Descriptor], expected Integer/Reference [20081204]                                                                             
ACPI: PCI Interrupt Link [LNK1] (IRQs 5 7 9 10 11 14 15) *0, disabled.          
ACPI: PCI Interrupt Link [LNK2] (IRQs 5 7 9 10 11 14 15) *0, disabled.          
ACPI: PCI Interrupt Link [LNK3] (IRQs 5 7 9 10 11 14 15) *0, disabled.          
ACPI: PCI Interrupt Link [LNK4] (IRQs 5 7 9 *10 11 14 15)                       
ACPI: PCI Interrupt Link [LXV5] (IRQs 5 7 9 *10 11 14 15)                       
ACPI: PCI Interrupt Link [LXV6] (IRQs 5 7 9 10 11 14 15) *0, disabled.          
ACPI: PCI Interrupt Link [LXV7] (IRQs 5 7 9 10 11 14 15) *0, disabled.          
ACPI: PCI Interrupt Link [LXV8] (IRQs 5 7 9 10 11 14 15) *0, disabled.          
ACPI: PCI Interrupt Link [LUBA] (IRQs 5 7 9 *10 11 14 15)                       
ACPI: PCI Interrupt Link [LMC1] (IRQs *5 7 9 10 11 14 15)                       
ACPI: PCI Interrupt Link [LMAC] (IRQs *5 7 9 10 11 14 15)                       
ACPI: PCI Interrupt Link [LAZA] (IRQs 5 7 9 10 *11 14 15)                       
ACPI: PCI Interrupt Link [LSMB] (IRQs 5 7 9 10 11 14 15) *0, disabled.          
ACPI: PCI Interrupt Link [LUB2] (IRQs 5 7 9 10 *11 14 15)                       
ACPI: PCI Interrupt Link [LIDE] (IRQs 5 7 9 10 11 14 15) *0, disabled.          
ACPI: PCI Interrupt Link [LSA0] (IRQs 5 7 9 10 *11 14 15)                       
ACPI: PCI Interrupt Link [LSA1] (IRQs 5 7 9 10 *11 14 15)                       
ACPI: PCI Interrupt Link [LSA2] (IRQs 5 7 9 *10 11 14 15)                       
ACPI: PCI Interrupt Link [APC1] (IRQs 16) *0, disabled.                         
ACPI: PCI Interrupt Link [APC2] (IRQs 17) *0, disabled.                         
ACPI: PCI Interrupt Link [APC3] (IRQs 18) *0, disabled.                         
ACPI: PCI Interrupt Link [APC4] (IRQs 19) *0                                    
ACPI: PCI Interrupt Link [AXV5] (IRQs 16) *0                                    
ACPI: PCI Interrupt Link [AXV6] (IRQs 16) *0, disabled.                         
ACPI: PCI Interrupt Link [AXV7] (IRQs 16) *0, disabled.                         
ACPI: PCI Interrupt Link [AXV8] (IRQs 16) *0, disabled.                         
ACPI: PCI Interrupt Link [AUBA] (IRQs 20 21 22 23) *0                           
ACPI: PCI Interrupt Link [AMA1] (IRQs 20 21 22 23) *0                           
ACPI: PCI Interrupt Link [AMAC] (IRQs 20 21 22 23) *0                           
ACPI: PCI Interrupt Link [AAZA] (IRQs 20 21 22 23) *0                           
ACPI: PCI Interrupt Link [AACI] (IRQs 20 21 22 23) *0, disabled.                
ACPI: PCI Interrupt Link [AMCI] (IRQs 20 21 22 23) *0, disabled.                
ACPI: PCI Interrupt Link [ASMB] (IRQs 20 21 22 23) *0, disabled.                
ACPI: PCI Interrupt Link [AUS2] (IRQs 20 21 22 23) *0                           
ACPI: PCI Interrupt Link [AIDE] (IRQs 20 21 22 23) *0, disabled.                
ACPI: PCI Interrupt Link [ASA0] (IRQs 20 21 22 23) *0                           
ACPI: PCI Interrupt Link [ASA1] (IRQs 20 21 22 23) *0                           
ACPI: PCI Interrupt Link [ASA2] (IRQs 20 21 22 23) *0                           
SCSI subsystem initialized                                                      
libata version 3.00 loaded.                                                     
usbcore: registered new interface driver usbfs                                  
usbcore: registered new interface driver hub                                    
usbcore: registered new device driver usb                                       
PCI: Using ACPI for IRQ routing                                                 
NetLabel: Initializing                                                          
NetLabel:  domain hash size = 128                                               
NetLabel:  protocols = UNLABELED CIPSOv4                                        
NetLabel:  unlabeled traffic allowed by default                                 
pnp: PnP ACPI init                                                              
ACPI: bus type pnp registered                                                   
pnp: PnP ACPI: found 13 devices                                                 
ACPI: ACPI bus type pnp unregistered                                            
system 00:00: ioport range 0x1000-0x107f has been reserved                      
system 00:00: ioport range 0x1080-0x10ff has been reserved                      
system 00:00: ioport range 0x1400-0x147f has been reserved                      
system 00:00: ioport range 0x1480-0x14ff has been reserved                      
system 00:00: ioport range 0x1800-0x187f has been reserved                      
system 00:00: ioport range 0x1880-0x18ff has been reserved                      
system 00:02: ioport range 0x4d0-0x4d1 has been reserved                        
system 00:02: ioport range 0x295-0x314 has been reserved                        
system 00:02: ioport range 0x880-0x88f has been reserved                        
system 00:0b: iomem range 0xe0000000-0xefffffff has been reserved               
system 00:0c: iomem range 0xd5800-0xd7fff has been reserved                     
system 00:0c: iomem range 0xf0000-0xf7fff could not be reserved                 
system 00:0c: iomem range 0xf8000-0xfbfff could not be reserved                 
system 00:0c: iomem range 0xfc000-0xfffff could not be reserved                 
system 00:0c: iomem range 0x7fef0000-0x7fefffff could not be reserved           
system 00:0c: iomem range 0xffff0000-0xffffffff has been reserved               
system 00:0c: iomem range 0x0-0x9ffff could not be reserved                     
system 00:0c: iomem range 0x100000-0x7feeffff could not be reserved             
system 00:0c: iomem range 0xfec00000-0xfec00fff has been reserved               
system 00:0c: iomem range 0xd0000000-0xdfffffff has been reserved               
system 00:0c: iomem range 0xfee00000-0xfee00fff has been reserved               
system 00:0c: iomem range 0xfeff0000-0xfeff0000 has been reserved               
pci 0000:00:03.0: PCI bridge, secondary bus 0000:01                             
pci 0000:00:03.0:   IO window: 0x9000-0x9fff                                    
pci 0000:00:03.0:   MEM window: 0xca000000-0xcdffffff                           
pci 0000:00:03.0:   PREFETCH window: 0x000000b0000000-0x000000bfffffff          
pci 0000:00:0f.0: PCI bridge, secondary bus 0000:02                             
pci 0000:00:0f.0:   IO window: 0x8000-0x8fff                                    
pci 0000:00:0f.0:   MEM window: 0xcfd00000-0xcfdfffff                           
pci 0000:00:0f.0:   PREFETCH window: 0x000000cfe00000-0x000000cfefffff          
pci 0000:00:03.0: setting latency timer to 64                                   
pci 0000:00:0f.0: setting latency timer to 64                                   
pci_bus 0000:00: resource 0 io:  [0x00-0xffff]                                  
pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffffffffffff]                  
pci_bus 0000:01: resource 0 io:  [0x9000-0x9fff]                                
pci_bus 0000:01: resource 1 mem: [0xca000000-0xcdffffff]                        
pci_bus 0000:01: resource 2 mem: [0xb0000000-0xbfffffff]                        
pci_bus 0000:01: resource 3 mem: [0x0-0x0]                                      
pci_bus 0000:02: resource 0 io:  [0x8000-0x8fff]                                
pci_bus 0000:02: resource 1 mem: [0xcfd00000-0xcfdfffff]                        
pci_bus 0000:02: resource 2 mem: [0xcfe00000-0xcfefffff]                        
pci_bus 0000:02: resource 3 io:  [0x00-0xffff]                                  
pci_bus 0000:02: resource 4 mem: [0x000000-0xffffffffffffffff]                  
NET: Registered protocol family 2                                               
IP route cache hash table entries: 65536 (order: 7, 524288 bytes)               
TCP established hash table entries: 262144 (order: 10, 4194304 bytes)           
TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)                    
TCP: Hash tables configured (established 262144 bind 65536)                     
TCP reno registered                                                             
NET: Registered protocol family 1                                               
checking if image is initramfs... it is                                         
Freeing initrd memory: 5059k freed                                              
audit: initializing netlink socket (disabled)                                   
type=2000 audit(1254151842.717:1): initialized                                  
HugeTLB registered 2 MB page size, pre-allocated 0 pages                        
VFS: Disk quotas dquot_6.5.2                                                    
Dquot-cache hash table entries: 512 (order 0, 4096 bytes)                       
msgmni has been set to 3978                                                     
SELinux:  Registering netfilter hooks                                           
alg: No test for stdrng (krng)                                                  
Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)            
io scheduler noop registered                                                    
io scheduler anticipatory registered                                            
io scheduler deadline registered                                                
io scheduler cfq registered (default)                                           
pci 0000:01:00.0: Boot video device                                             
pcieport-driver 0000:00:03.0: setting latency timer to 64                       
  alloc irq_desc for 24 on cpu 0 node 0                                         
  alloc kstat_irqs on cpu 0 node 0                                              
pcieport-driver 0000:00:03.0: irq 24 for MSI/MSI-X                              
pci_hotplug: PCI Hot Plug PCI Core version: 0.5                                 
pciehp: PCI Express Hot Plug Controller Driver version: 0.4                     
acpiphp: ACPI Hot Plug PCI Controller Driver version: 0.5                       
input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0       
ACPI: Power Button (FF) [PWRF]                                                  
input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1                                                                              
ACPI: Power Button (CM) [PWRB]                                                  
processor ACPI_CPU:00: registered as cooling_device0                            
ACPI: Processor [CPU0] (supports 8 throttling states)                           
processor ACPI_CPU:01: registered as cooling_device1                            
hpet_acpi_add: no address or irqs in _CRS                                       
Non-volatile memory driver v1.3                                                 
Linux agpgart interface v0.103                                                  
Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled                         
Switched to high resolution mode on CPU 1                                       
Switched to high resolution mode on CPU 0                                       
serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A                            
00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A                                 
brd: module loaded                                                              
loop: module loaded                                                             
Fixed MDIO Bus: probed                                                          
input: Macintosh mouse button emulation as /devices/virtual/input/input2        
Driver 'sd' needs updating - please use bus_type methods                        
Driver 'sr' needs updating - please use bus_type methods                        
ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver                      
ACPI: PCI Interrupt Link [AUS2] enabled at IRQ 23                               
  alloc irq_desc for 23 on cpu 0 node 0                                         
  alloc kstat_irqs on cpu 0 node 0                                              
ehci_hcd 0000:00:0b.1: PCI INT B -> Link[AUS2] -> GSI 23 (level, low) -> IRQ 23 
ehci_hcd 0000:00:0b.1: setting latency timer to 64                              
ehci_hcd 0000:00:0b.1: EHCI Host Controller                                     
ehci_hcd 0000:00:0b.1: new USB bus registered, assigned bus number 1            
ehci_hcd 0000:00:0b.1: debug port 1                                             
ehci_hcd 0000:00:0b.1: cache line size of 128 is not supported                  
ehci_hcd 0000:00:0b.1: irq 23, io mem 0xcfffe000                                
ehci_hcd 0000:00:0b.1: USB 2.0 started, EHCI 1.00                               
usb usb1: New USB device found, idVendor=1d6b, idProduct=0002                   
usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1              
usb usb1: Product: EHCI Host Controller                                         
usb usb1: Manufacturer: Linux 2.6.29.4-167.fc11.x86_64 ehci_hcd                 
usb usb1: SerialNumber: 0000:00:0b.1                                            
usb usb1: configuration #1 chosen from 1 choice                                 
hub 1-0:1.0: USB hub found                                                      
hub 1-0:1.0: 10 ports detected                                                  
ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver                          
ACPI: PCI Interrupt Link [AUBA] enabled at IRQ 22                               
  alloc irq_desc for 22 on cpu 0 node 0                                         
  alloc kstat_irqs on cpu 0 node 0                                              
ohci_hcd 0000:00:0b.0: PCI INT A -> Link[AUBA] -> GSI 22 (level, low) -> IRQ 22 
ohci_hcd 0000:00:0b.0: setting latency timer to 64                              
ohci_hcd 0000:00:0b.0: OHCI Host Controller                                     
ohci_hcd 0000:00:0b.0: new USB bus registered, assigned bus number 2            
ohci_hcd 0000:00:0b.0: irq 22, io mem 0xcffff000                                
usb usb2: New USB device found, idVendor=1d6b, idProduct=0001                   
usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1              
usb usb2: Product: OHCI Host Controller                                         
usb usb2: Manufacturer: Linux 2.6.29.4-167.fc11.x86_64 ohci_hcd                 
usb usb2: SerialNumber: 0000:00:0b.0                                            
usb usb2: configuration #1 chosen from 1 choice                                 
hub 2-0:1.0: USB hub found                                                      
hub 2-0:1.0: 10 ports detected                                                  
uhci_hcd: USB Universal Host Controller Interface driver                        
PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1                          
PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp                                                                  
serio: i8042 KBD port at 0x60,0x64 irq 1                                        
mice: PS/2 mouse device common for all mice                                     
rtc_cmos 00:05: RTC can wake from S4                                            
rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0                           
rtc0: alarms up to one year, y3k, 114 bytes nvram                               
device-mapper: uevent: version 1.0.3                                            
device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: dm-devel@redhat.com
cpuidle: using governor ladder                                                  
cpuidle: using governor menu                                                    
usbcore: registered new interface driver hiddev                                 
usbcore: registered new interface driver usbhid                                 
usbhid: v2.6:USB HID core driver                                                
nf_conntrack version 0.5.0 (16384 buckets, 65536 max)                           
CONFIG_NF_CT_ACCT is deprecated and will be removed soon. Please use            
nf_conntrack.acct=1 kernel paramater, acct=1 nf_conntrack module option or      
sysctl net.netfilter.nf_conntrack_acct=1 to enable it.                          
ip_tables: (C) 2000-2006 Netfilter Core Team                                    
TCP cubic registered                                                            
Initializing XFRM netlink socket                                                
NET: Registered protocol family 17                                              
registered taskstats version 1                                                  
  Magic number: 9:192:539                                                       
usb_endpoint usbdev2.1_ep00: hash matches                                       
Initalizing network drop monitor service                                        
Freeing unused kernel memory: 1304k freed                                       
Write protecting the kernel read-only data: 1844k                               
input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3                                                                              
udev: starting version 141                                                      
[drm] Initialized drm 1.1.0 20060810                                            
ACPI: PCI Interrupt Link [AXV5] enabled at IRQ 16                               
  alloc irq_desc for 16 on cpu 0 node 0                                         
  alloc kstat_irqs on cpu 0 node 0                                              
pci 0000:01:00.0: PCI INT A -> Link[AXV5] -> GSI 16 (level, low) -> IRQ 16      
pci 0000:01:00.0: setting latency timer to 64                                   
nouveau 0000:01:00.0: Detected an NV50 generation card (0x092a00a2)             
[drm] Initialized nouveau 0.0.12 20060213 for 0000:01:00.0 on minor 0           
pata_amd 0000:00:0d.0: version 0.4.1                                            
pata_amd 0000:00:0d.0: setting latency timer to 64                              
scsi0 : pata_amd                                                                
scsi1 : pata_amd                                                                
ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xec00 irq 14                 
ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xec08 irq 15                 
usb 1-5: new high speed USB device using ehci_hcd and address 3                 
ata1.00: ATAPI: TEAC DV-W516GDM, M4S2, max UDMA/66                              
ata1: nv_mode_filter: 0x1f39f&0x1f01f->0x1f01f, BIOS=0x1f000 (0xc5000000) ACPI=0x1f01f (30:600:0x13)                                                            
ata1.00: limited to UDMA/33 due to 40-wire cable                                
ata1.00: configured for UDMA/33                                                 
isa bounce pool size: 16 pages                                                  
scsi 0:0:0:0: CD-ROM            TEAC     DV-W516GDM       M4S2 PQ: 0 ANSI: 5    
sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray           
Uniform CD-ROM driver Revision: 3.20                                            
sr 0:0:0:0: Attached scsi CD-ROM sr0                                            
sr 0:0:0:0: Attached scsi generic sg0 type 5                                    
ata2: port disabled. ignoring.                                                  
ACPI: PCI Interrupt Link [APC4] enabled at IRQ 19                               
  alloc irq_desc for 19 on cpu 0 node 0                                         
  alloc kstat_irqs on cpu 0 node 0                                              
firewire_ohci 0000:02:07.0: PCI INT A -> Link[APC4] -> GSI 19 (level, low) -> IRQ 19                                                                            
firewire_ohci 0000:02:07.0: setting latency timer to 64                         
usb 1-5: New USB device found, idVendor=0951, idProduct=1603                    
usb 1-5: New USB device strings: Mfr=1, Product=2, SerialNumber=3               
usb 1-5: Product: DataTraveler 2.0                                              
usb 1-5: Manufacturer: Kingston                                                 
usb 1-5: SerialNumber: 0019E000C6C1A8C062CF002E                                 
usb 1-5: configuration #1 chosen from 1 choice                                  
Initializing USB Mass Storage driver...                                         
scsi2 : SCSI emulation for USB Mass Storage devices                             
usb-storage: device found at 3                                                  
usb-storage: waiting for device to settle before scanning                       
usbcore: registered new interface driver usb-storage                            
USB Mass Storage support registered.                                            
firewire_ohci: Added fw-ohci device 0000:02:07.0, OHCI version 1.10             
sata_nv 0000:00:0e.0: version 3.5                                               
ACPI: PCI Interrupt Link [ASA0] enabled at IRQ 21                               
  alloc irq_desc for 21 on cpu 0 node 0                                         
  alloc kstat_irqs on cpu 0 node 0                                              
sata_nv 0000:00:0e.0: PCI INT A -> Link[ASA0] -> GSI 21 (level, low) -> IRQ 21  
sata_nv 0000:00:0e.0: Using SWNCQ mode                                          
sata_nv 0000:00:0e.0: setting latency timer to 64                               
scsi3 : sata_nv                                                                 
scsi4 : sata_nv                                                                 
ata3: SATA max UDMA/133 cmd 0x9f0 ctl 0xbf0 bmdma 0xd800 irq 21                 
ata4: SATA max UDMA/133 cmd 0x970 ctl 0xb70 bmdma 0xd808 irq 21                 
usb 2-1: new full speed USB device using ohci_hcd and address 2                 
usb 2-1: New USB device found, idVendor=0ac8, idProduct=303b                    
usb 2-1: New USB device strings: Mfr=1, Product=2, SerialNumber=0               
usb 2-1: Product: PC Camera                                                     
usb 2-1: Manufacturer: Vimicro Corp.                                            
usb 2-1: configuration #1 chosen from 1 choice                                  
firewire_core: created device fw0: GUID 1aa205bc00044b06, S400                  
usb 2-6: new low speed USB device using ohci_hcd and address 3                  
ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)                          
usb 2-6: New USB device found, idVendor=046d, idProduct=c501                    
usb 2-6: New USB device strings: Mfr=1, Product=2, SerialNumber=0               
usb 2-6: Product: USB Receiver                                                  
usb 2-6: Manufacturer: Logitech                                                 
usb 2-6: configuration #1 chosen from 1 choice                                  
input: Logitech USB Receiver as /devices/pci0000:00/0000:00:0b.0/usb2/2-6/2-6:1.0/input/input4                                                                  
ata3.00: ATA-7: ST3320620AS, 3.AAE, max UDMA/133                                
ata3.00: 625142448 sectors, multi 16: LBA48 NCQ (depth 31/32)                   
generic-usb 0003:046D:C501.0001: input,hidraw0: USB HID v1.10 Mouse [Logitech USB Receiver] on usb-0000:00:0b.0-6/input0                                        
ata3.00: configured for UDMA/133                                                
scsi 3:0:0:0: Direct-Access     ATA      ST3320620AS      3.AA PQ: 0 ANSI: 5    
sd 3:0:0:0: [sda] 625142448 512-byte hardware sectors: (320 GB/298 GiB)         
sd 3:0:0:0: [sda] Write Protect is off                                          
sd 3:0:0:0: [sda] Mode Sense: 00 3a 00 00                                       
sd 3:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA                                                                         
sd 3:0:0:0: [sda] 625142448 512-byte hardware sectors: (320 GB/298 GiB)         
sd 3:0:0:0: [sda] Write Protect is off                                          
sd 3:0:0:0: [sda] Mode Sense: 00 3a 00 00                                       
sd 3:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA                                                                         
 sda: sda1 sda2 sda3                                                            
sd 3:0:0:0: [sda] Attached SCSI disk                                            
sd 3:0:0:0: Attached scsi generic sg1 type 0                                    
ata4: SATA link down (SStatus 0 SControl 300)                                   
ACPI: PCI Interrupt Link [ASA1] enabled at IRQ 20                               
  alloc irq_desc for 20 on cpu 0 node 0                                         
  alloc kstat_irqs on cpu 0 node 0                                              
sata_nv 0000:00:0e.1: PCI INT B -> Link[ASA1] -> GSI 20 (level, low) -> IRQ 20  
sata_nv 0000:00:0e.1: Using SWNCQ mode                                          
sata_nv 0000:00:0e.1: setting latency timer to 64                               
scsi5 : sata_nv                                                                 
scsi6 : sata_nv                                                                 
ata5: SATA max UDMA/133 cmd 0x9e0 ctl 0xbe0 bmdma 0xc400 irq 20                 
ata6: SATA max UDMA/133 cmd 0x960 ctl 0xb60 bmdma 0xc408 irq 20                 
ata5: SATA link down (SStatus 0 SControl 300)                                   
ata6: SATA link down (SStatus 0 SControl 300)                                   
ACPI: PCI Interrupt Link [ASA2] enabled at IRQ 23                               
sata_nv 0000:00:0e.2: PCI INT C -> Link[ASA2] -> GSI 23 (level, low) -> IRQ 23  
sata_nv 0000:00:0e.2: Using SWNCQ mode                                          
sata_nv 0000:00:0e.2: setting latency timer to 64                               
scsi7 : sata_nv                                                                 
scsi8 : sata_nv                                                                 
ata7: SATA max UDMA/133 cmd 0xc000 ctl 0xbc00 bmdma 0xb000 irq 23               
ata8: SATA max UDMA/133 cmd 0xb800 ctl 0xb400 bmdma 0xb008 irq 23               
ata7: SATA link down (SStatus 0 SControl 300)                                   
ata8: SATA link down (SStatus 0 SControl 300)                                   
usb-storage: device scan complete                                               
scsi 2:0:0:0: Direct-Access     Kingston DataTraveler 2.0 1.00 PQ: 0 ANSI: 2    
sd 2:0:0:0: [sdb] 15695872 512-byte hardware sectors: (8.03 GB/7.48 GiB)        
sd 2:0:0:0: [sdb] Write Protect is off                                          
sd 2:0:0:0: [sdb] Mode Sense: 23 00 00 00                                       
sd 2:0:0:0: [sdb] Assuming drive cache: write through                           
sd 2:0:0:0: [sdb] 15695872 512-byte hardware sectors: (8.03 GB/7.48 GiB)        
sd 2:0:0:0: [sdb] Write Protect is off                                          
sd 2:0:0:0: [sdb] Mode Sense: 23 00 00 00                                       
sd 2:0:0:0: [sdb] Assuming drive cache: write through                           
 sdb: sdb1                                                                      
sd 2:0:0:0: [sdb] Attached SCSI removable disk                                  
sd 2:0:0:0: Attached scsi generic sg2 type 0                                    
ISO 9660 Extensions: Microsoft Joliet Level 3                                   
ISO 9660 Extensions: RRIP_1991A                                                 
squashfs: version 4.0 (2009/01/31) Phillip Lougher                              
EXT4-fs: barriers enabled                                                       
kjournald2 starting: pid 752, dev dm-0:8, commit interval 5 seconds             
EXT4 FS on dm-0, internal journal on dm-0:8                                     
EXT4-fs: delayed allocation enabled                                             
EXT4-fs: file extents enabled                                                   
EXT4-fs: mballoc enabled                                                        
EXT4-fs: mounted filesystem dm-0 with ordered data mode                         
JBD: barrier-based sync failed on dm-0:8 - disabling barriers                   
type=1404 audit(1254151860.268:2): enforcing=1 old_enforcing=0 auid=4294967295 ses=4294967295                                                                   
SELinux: 8192 avtab hash slots, 123719 rules.                                   
SELinux: 8192 avtab hash slots, 123719 rules.                                   
SELinux:  8 users, 11 roles, 2722 types, 127 bools, 1 sens, 1024 cats           
SELinux:  74 classes, 123719 rules                                              
SELinux:  Completing initialization.                                            
SELinux:  Setting up existing superblocks.                                      
SELinux: initialized (dev dm-0, type ext4), uses xattr                          
SELinux: inode_doinit_with_dentry:  no dentry for dev=dm-0 ino=35225            
SELinux: inode_doinit_with_dentry:  no dentry for dev=dm-0 ino=26316            
SELinux: inode_doinit_with_dentry:  no dentry for dev=dm-0 ino=26313            
SELinux: inode_doinit_with_dentry:  no dentry for dev=dm-0 ino=253              
SELinux: initialized (dev loop2, type squashfs), not configured for labeling    
SELinux: initialized (dev loop0, type squashfs), not configured for labeling    
SELinux: initialized (dev sr0, type iso9660), uses genfs_contexts               
SELinux: initialized (dev tmpfs, type tmpfs), uses transition SIDs              
SELinux: initialized (dev usbfs, type usbfs), uses genfs_contexts               
SELinux: initialized (dev selinuxfs, type selinuxfs), uses genfs_contexts       
SELinux: initialized (dev mqueue, type mqueue), uses transition SIDs            
SELinux: initialized (dev hugetlbfs, type hugetlbfs), uses genfs_contexts       
SELinux: initialized (dev devpts, type devpts), uses transition SIDs            
SELinux: initialized (dev inotifyfs, type inotifyfs), uses genfs_contexts       
SELinux: initialized (dev tmpfs, type tmpfs), uses transition SIDs              
SELinux: initialized (dev anon_inodefs, type anon_inodefs), uses genfs_contexts 
SELinux: initialized (dev pipefs, type pipefs), uses task SIDs                  
SELinux: initialized (dev debugfs, type debugfs), uses genfs_contexts           
SELinux: initialized (dev sockfs, type sockfs), uses task SIDs                  
SELinux: initialized (dev proc, type proc), uses genfs_contexts                 
SELinux: initialized (dev bdev, type bdev), uses genfs_contexts                 
SELinux: initialized (dev rootfs, type rootfs), uses genfs_contexts             
SELinux: initialized (dev sysfs, type sysfs), uses genfs_contexts               
type=1403 audit(1254151860.814:3): policy loaded auid=4294967295 ses=4294967295 
udev: starting version 141                                                      
input: PC Speaker as /devices/platform/pcspkr/input/input5                      
i2c-adapter i2c-0: nForce2 SMBus adapter at 0xf400                              
i2c-adapter i2c-1: nForce2 SMBus adapter at 0xf000                              
forcedeth: Reverse Engineered nForce ethernet driver. Version 0.62.             
ACPI: PCI Interrupt Link [AMAC] enabled at IRQ 22                               
forcedeth 0000:00:11.0: PCI INT A -> Link[AMAC] -> GSI 22 (level, low) -> IRQ 22
forcedeth 0000:00:11.0: setting latency timer to 64                             
nv_probe: set workaround bit for reversed mac addr                              
Linux video capture interface: v2.00                                            
forcedeth 0000:00:11.0: ifname eth0, PHY OUI 0x5043 @ 1, addr 00:04:4b:05:18:da 
forcedeth 0000:00:11.0: highdma csum vlan pwrctl mgmt timirq gbit lnktim msi desc-v3                                                                            
ACPI: PCI Interrupt Link [AMA1] enabled at IRQ 21                               
forcedeth 0000:00:12.0: PCI INT A -> Link[AMA1] -> GSI 21 (level, low) -> IRQ 21
forcedeth 0000:00:12.0: setting latency timer to 64                             
nv_probe: set workaround bit for reversed mac addr                              
gspca: main v2.5.0 registered                                                   
forcedeth 0000:00:12.0: ifname eth1, PHY OUI 0x5043 @ 2, addr 00:04:4b:05:18:db 
forcedeth 0000:00:12.0: highdma csum vlan pwrctl mgmt timirq gbit lnktim msi desc-v3                                                                            
gspca: probing 0ac8:303b                                                        
ACPI: PCI Interrupt Link [AAZA] enabled at IRQ 20                               
HDA Intel 0000:00:0f.1: PCI INT B -> Link[AAZA] -> GSI 20 (level, low) -> IRQ 20
HDA Intel 0000:00:0f.1: setting latency timer to 64                             
hda_codec: Unknown model for ALC883, trying auto-probe from BIOS...             
ALSA sound/pci/hda/hda_codec.c:3507: autoconfig: line_outs=4 (0x14/0x15/0x16/0x17/0x0)                                                                          
ALSA sound/pci/hda/hda_codec.c:3511:    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)    
ALSA sound/pci/hda/hda_codec.c:3515:    hp_outs=1 (0x1b/0x0/0x0/0x0/0x0)        
ALSA sound/pci/hda/hda_codec.c:3516:    mono: mono_out=0x0                      
ALSA sound/pci/hda/hda_codec.c:3524:    inputs: mic=0x18, fmic=0x19, line=0x1a, fline=0x0, cd=0x0, aux=0x0                                                      
zc3xx: probe 2wr ov vga 0x0000                                                  
zc3xx: probe 3wr vga 1 0xe001                                                   
zc3xx: probe sensor -> 0013                                                     
zc3xx: Find Sensor MI0360. Chip revision e001                                   
gspca: probe ok                                                                 
usbcore: registered new interface driver zc3xx                                  
zc3xx: registered                                                               
device-mapper: multipath: version 1.0.5 loaded                                  
EXT4 FS on dm-0, internal journal on dm-0:8                                     
SELinux: initialized (dev tmpfs, type tmpfs), uses transition SIDs              
SELinux: initialized (dev binfmt_misc, type binfmt_misc), uses genfs_contexts   
SELinux: initialized (dev tmpfs, type tmpfs), uses transition SIDs              
SELinux: initialized (dev tmpfs, type tmpfs), uses transition SIDs              
SELinux: initialized (dev tmpfs, type tmpfs), uses transition SIDs              
JBD: barrier-based sync failed on dm-0:8 - disabling barriers                   
platform microcode: firmware: requesting intel-ucode/0f-06-04                   
platform microcode: firmware: requesting intel-ucode/0f-06-04                   
Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba       
Microcode Update Driver: v2.00 removed.                                         
p4-clockmod: P4/Xeon(TM) CPU On-Demand Clock Modulation available               
NET: Registered protocol family 10                                              
lo: Disabled Privacy Extensions                                                 
ip6_tables: (C) 2000-2006 Netfilter Core Team                                   
RPC: Registered udp transport module.                                           
RPC: Registered tcp transport module.                                           
SELinux: initialized (dev rpc_pipefs, type rpc_pipefs), uses genfs_contexts     
  alloc irq_desc for 25 on cpu 0 node 0                                         
  alloc kstat_irqs on cpu 0 node 0                                              
forcedeth 0000:00:12.0: irq 25 for MSI/MSI-X                                    
eth1: no link during initialization.                                            
ADDRCONF(NETDEV_UP): eth1: link is not ready                                    
  alloc irq_desc for 26 on cpu 0 node 0                                         
  alloc kstat_irqs on cpu 0 node 0                                              
forcedeth 0000:00:11.0: irq 26 for MSI/MSI-X                                    
eth0: no link during initialization.                                            
ADDRCONF(NETDEV_UP): eth0: link is not ready                                    
nouveau 0000:01:00.0: Allocating FIFO number 1                                  
nouveau 0000:01:00.0: nouveau_fifo_alloc: initialised FIFO 1                    
nouveau 0000:01:00.0: Allocating FIFO number 2                                  
nouveau 0000:01:00.0: nouveau_fifo_alloc: initialised FIFO 2                    
CPU0 attaching NULL sched-domain.                                               
CPU1 attaching NULL sched-domain.                                               
CPU0 attaching sched-domain:                                                    
 domain 0: span 0-1 level CPU                                                   
  groups: 0 1                                                                   
CPU1 attaching sched-domain:                                                    
 domain 0: span 0-1 level CPU                                                   
  groups: 1 0                                                                   
CPU0 attaching NULL sched-domain.                                               
CPU1 attaching NULL sched-domain.                                               
CPU0 attaching sched-domain:                                                    
 domain 0: span 0-1 level CPU                                                   
  groups: 0 1                                                                   
CPU1 attaching sched-domain:                                                    
 domain 0: span 0-1 level CPU                                                   
  groups: 1 0                                                                   
ALSA sound/pci/hda/hda_intel.c:1101: Too big adjustment 32: adj=128, bytes=128, size=4096, periods=32                                                           
ALSA sound/pci/hda/hda_intel.c:1101: Too big adjustment 32: adj=128, bytes=128, size=4096, periods=32                                                           
ALSA sound/pci/hda/hda_intel.c:1101: Too big adjustment 32: adj=128, bytes=128, size=4096, periods=32                                                           
ALSA sound/pci/hda/hda_intel.c:1101: Too big adjustment 32: adj=128, bytes=128, size=4096, periods=32                                                           
ALSA sound/pci/hda/hda_intel.c:1101: Too big adjustment 32: adj=128, bytes=128, size=4096, periods=32                                                           
ALSA sound/pci/hda/hda_intel.c:1101: Too big adjustment 32: adj=128, bytes=128, size=4096, periods=32
ALSA sound/pci/hda/hda_intel.c:1101: Too big adjustment 32: adj=256, bytes=128,size=4096, periods=32
ALSA sound/pci/hda/hda_intel.c:1101: Too big adjustment 32: adj=128, bytes=128,size=4096, periods=32
ALSA sound/pci/hda/hda_intel.c:1101: Too big adjustment 32: adj=128, bytes=128,size=4096, periods=32
ALSA sound/pci/hda/hda_intel.c:1101: Too big adjustment 32: adj=384, bytes=384,size=12288, periods=32
ALSA sound/pci/hda/hda_intel.c:1101: Too big adjustment 32: adj=128, bytes=128,size=4096, periods=32
ALSA sound/pci/hda/hda_intel.c:1101: Too big adjustment 32: adj=128, bytes=128,size=4096, periods=32
ALSA sound/pci/hda/hda_intel.c:1101: Too big adjustment 32: adj=384, bytes=384,size=12288, periods=32
ALSA sound/pci/hda/hda_intel.c:1101: Too big adjustment 32: adj=128, bytes=128,size=4096, periods=32
ALSA sound/pci/hda/hda_intel.c:1101: Too big adjustment 32: adj=128, bytes=128,size=4096, periods=32
ALSA sound/pci/hda/hda_intel.c:1101: Too big adjustment 32: adj=384, bytes=384,size=12288, periods=32
ALSA sound/pci/hda/hda_intel.c:1101: Too big adjustment 32: adj=128, bytes=128,size=4096, periods=32
ALSA sound/pci/hda/hda_intel.c:1101: Too big adjustment 32: adj=128, bytes=128,size=4096, periods=32
ALSA sound/pci/hda/hda_intel.c:1101: Too big adjustment 32: adj=512, bytes=128,size=4096, periods=32
ALSA sound/pci/hda/hda_intel.c:1101: Too big adjustment 32: adj=128, bytes=128,size=4096, periods=32
ALSA sound/pci/hda/hda_intel.c:1101: Too big adjustment 32: adj=128, bytes=128,size=4096, periods=32
ALSA sound/pci/hda/hda_intel.c:1101: Too big adjustment 32: adj=128, bytes=128,size=4096, periods=32
ALSA sound/pci/hda/hda_intel.c:1101: Too big adjustment 32: adj=128, bytes=128,size=4096, periods=32
**[liveuser@localhost ~]$**
```

---

### Post by C0NSTANTIN on 2009-09-28
Terminal
```
[b][paladin@BFG-2k8 ~]$ su -
Password:                
[root@BFG-2k8 ~]# lspci[/b]
00:00.0 Host bridge: nVidia Corporation C55 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.3 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.4 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.5 RAM memory: nVidia Corporation C55 Memory Controller (rev a2)
00:00.6 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.7 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.0 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.1 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.3 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.4 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.5 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.6 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:02.0 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:02.1 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:02.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:03.0 PCI bridge: nVidia Corporation C55 PCI Express bridge (rev a1)
00:09.0 RAM memory: nVidia Corporation MCP55 Memory Controller (rev a1)
00:0a.0 ISA bridge: nVidia Corporation MCP55 LPC Bridge (rev a2)       
00:0a.1 SMBus: nVidia Corporation MCP55 SMBus (rev a2)                 
00:0b.0 USB Controller: nVidia Corporation MCP55 USB Controller (rev a1)
00:0b.1 USB Controller: nVidia Corporation MCP55 USB Controller (rev a2)
00:0d.0 IDE interface: nVidia Corporation MCP55 IDE (rev a1)            
00:0e.0 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a2)
00:0e.1 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a2)
00:0e.2 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a2)
00:0f.0 PCI bridge: nVidia Corporation MCP55 PCI bridge (rev a2)        
00:0f.1 Audio device: nVidia Corporation MCP55 High Definition Audio (rev a2)
00:11.0 Bridge: nVidia Corporation MCP55 Ethernet (rev a2)                   
00:12.0 Bridge: nVidia Corporation MCP55 Ethernet (rev a2)                   
01:00.0 VGA compatible controller: nVidia Corporation GeForce 9800 GT (rev a2)
02:07.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)                                                               
**[root@BFG-2k8 ~]# dmesg                                                         **
Initializing cgroup subsys cpuset                                               
Initializing cgroup subsys cpu                                                  
Linux version 2.6.29.4-167.fc11.x86_64 (mockbuild@xenbuilder4.fedora.phx.redhat.com) (gcc version 4.4.0 20090506 (Red Hat 4.4.0-4) (GCC) ) #1 SMP Wed May 27 17:27:08 EDT 2009                                                                  
Command line: ro root=/dev/mapper/vg_bfg2k8-LogVol01 rhgb quiet                 
KERNEL supported cpus:                                                          
  Intel GenuineIntel                                                            
  AMD AuthenticAMD                                                              
  Centaur CentaurHauls                                                          
BIOS-provided physical RAM map:                                                 
 BIOS-e820: 0000000000000000 - 000000000009f000 (usable)                        
 BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)                      
 BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)                      
 BIOS-e820: 0000000000100000 - 000000007fef0000 (usable)                        
 BIOS-e820: 000000007fef0000 - 000000007fef3000 (ACPI NVS)                      
 BIOS-e820: 000000007fef3000 - 000000007ff00000 (ACPI data)                     
 BIOS-e820: 00000000d0000000 - 00000000f0000000 (reserved)                      
 BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)                      
DMI 2.4 present.                                                                
Phoenix BIOS detected: BIOS may corrupt low RAM, working around it.             
last_pfn = 0x7fef0 max_arch_pfn = 0x100000000                                   
x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106                
original variable MTRRs                                                         
reg 0, base: 0GB, range: 2GB, type WB                                           
reg 1, base: 2047MB, range: 1MB, type UC                                        
total RAM coverred: 2047M                                                       
Found optimal setting for mtrr clean up                                         
 gran_size: 64K         chunk_size: 2M  num_reg: 2      lose cover RAM: 0G      
New variable MTRRs                                                              
reg 0, base: 0GB, range: 2GB, type WB                                           
reg 1, base: 2047MB, range: 1MB, type UC                                        
x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106                
init_memory_mapping: 0000000000000000-000000007fef0000                          
 0000000000 - 007fe00000 page 2M                                                
 007fe00000 - 007fef0000 page 4k                                                
kernel direct mapping tables up to 7fef0000 @ 10000-14000                       
last_map_addr: 7fef0000 end: 7fef0000                                           
RAMDISK: 37c67000 - 37fefe5f                                                    
ACPI: RSDP 000F7F30, 0014 (r0 Nvidia)                                           
ACPI: RSDT 7FEF3040, 0038 (r1 Nvidia NVDAACPI 42302E31 NVDA        0)           
ACPI: FACP 7FEF30C0, 0074 (r1 Nvidia NVDAACPI 42302E31 NVDA        0)           
FADT: X_PM1a_EVT_BLK.bit_width (16) does not match PM1_EVT_LEN (4)              
ACPI: DSDT 7FEF3180, 5349 (r1 NVIDIA NVDAACPI     1000 MSFT  3000000)           
ACPI: FACS 7FEF0000, 0040                                                       
ACPI: HPET 7FEF8640, 003C (r1 Nvidia NVDAACPI 42302E31 NVDA        0)           
ACPI: WDRT 7FEF86C0, 0047 (r1 Nvidia NVDAACPI 42302E31 NVDA        0)           
ACPI: MCFG 7FEF8780, 003C (r1 Nvidia NVDAACPI 42302E31 NVDA        0)           
ACPI: APIC 7FEF8540, 0098 (r1 Nvidia NVDAACPI 42302E31 NVDA        0)           
ACPI: Local APIC address 0xfee00000                                             
No NUMA configuration found                                                     
Faking a node at 0000000000000000-000000007fef0000                              
Bootmem setup node 0 0000000000000000-000000007fef0000                          
  NODE_DATA [0000000000012000 - 0000000000026fff]                               
  bootmap [0000000000027000 -  0000000000036fdf] pages 10                       
(6 early reservations) ==> bootmem [0000000000 - 007fef0000]                    
  #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]   
  #1 [0000006000 - 0000008000]       TRAMPOLINE ==> [0000006000 - 0000008000]   
  #2 [0000200000 - 0000ac700c]    TEXT DATA BSS ==> [0000200000 - 0000ac700c]   
  #3 [0037c67000 - 0037fefe5f]          RAMDISK ==> [0037c67000 - 0037fefe5f]   
  #4 [000009f000 - 0000100000]    BIOS reserved ==> [000009f000 - 0000100000]   
  #5 [0000010000 - 0000012000]          PGTABLE ==> [0000010000 - 0000012000]   
found SMP MP-table at [ffff8800000f3f60] 000f3f60                               
 [ffffe20000000000-ffffe20001bfffff] PMD -> [ffff880001200000-ffff880002dfffff] on node 0                                                                       
Zone PFN ranges:                                                                
  DMA      0x00000010 -> 0x00001000                                             
  DMA32    0x00001000 -> 0x00100000                                             
  Normal   0x00100000 -> 0x00100000                                             
Movable zone start PFN for each node                                            
early_node_map[2] active PFN ranges                                             
    0: 0x00000010 -> 0x0000009f                                                 
    0: 0x00000100 -> 0x0007fef0                                                 
On node 0 totalpages: 523903                                                    
  DMA zone: 56 pages used for memmap                                            
  DMA zone: 2351 pages reserved                                                 
  DMA zone: 1576 pages, LIFO batch:0                                            
  DMA32 zone: 7109 pages used for memmap                                        
  DMA32 zone: 512811 pages, LIFO batch:31                                       
ACPI: PM-Timer IO Port: 0x1008                                                  
ACPI: Local APIC address 0xfee00000                                             
ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)                              
ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)                              
ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] disabled)                             
ACPI: LAPIC (acpi_id[0x03] lapic_id[0x03] disabled)                             
ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])                             
ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])                             
ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])                             
ACPI: LAPIC_NMI (acpi_id[0x03] high edge lint[0x1])                             
ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])                         
IOAPIC[0]: apic_id 4, version 0, address 0xfec00000, GSI 0-23                   
ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)                        
ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)                     
ACPI: INT_SRC_OVR (bus 0 bus_irq 14 global_irq 14 high edge)                    
ACPI: INT_SRC_OVR (bus 0 bus_irq 15 global_irq 15 high edge)                    
ACPI: IRQ0 used by override.                                                    
ACPI: IRQ2 used by override.                                                    
ACPI: IRQ9 used by override.                                                    
ACPI: IRQ14 used by override.                                                   
ACPI: IRQ15 used by override.                                                   
Using ACPI (MADT) for SMP configuration information                             
ACPI: HPET timers must be located in memory.                                    
SMP: Allowing 4 CPUs, 2 hotplug CPUs                                            
nr_irqs_gsi: 24                                                                 
PM: Registered nosave memory: 000000000009f000 - 00000000000a0000               
PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000               
PM: Registered nosave memory: 00000000000f0000 - 0000000000100000               
Allocating PCI resources starting at 80000000 (gap: 7ff00000:50100000)          
NR_CPUS:64 nr_cpumask_bits:64 nr_cpu_ids:4 nr_node_ids:1                        
PERCPU: Allocating 57344 bytes of per cpu data                                  
Built 1 zonelists in Node order, mobility grouping on.  Total pages: 514387     
Policy zone: DMA32                                                              
Kernel command line: ro root=/dev/mapper/vg_bfg2k8-LogVol01 rhgb quiet          
Initializing CPU#0                                                              
PID hash table entries: 4096 (order: 12, 32768 bytes)                           
Fast TSC calibration using PIT                                                  
Detected 3400.215 MHz processor.                                                
spurious 8259A interrupt: IRQ7.                                                 
Console: colour VGA+ 80x25                                                      
console [tty0] enabled                                                          
allocated 20971520 bytes of page_cgroup                                         
please try cgroup_disable=memory option if you don't want                       
Checking aperture...                                                            
No AGP bridge found                                                             
Calgary: detecting Calgary via BIOS EBDA area                                   
Calgary: Unable to locate Rio Grande table in EBDA - bailing!                   
Memory: 2033336k/2096064k available (3786k kernel code, 452k absent, 62276k reserved, 2294k data, 1304k init)                                                   
SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1         
Calibrating delay loop (skipped), value calculated using timer frequency.. 6800.43 BogoMIPS (lpj=3400215)                                                       
Security Framework initialized                                                  
SELinux:  Initializing.                                                         
SELinux:  Starting in permissive mode                                           
Dentry cache hash table entries: 262144 (order: 9, 2097152 bytes)               
Inode-cache hash table entries: 131072 (order: 8, 1048576 bytes)                
Mount-cache hash table entries: 256                                             
Initializing cgroup subsys ns                                                   
Initializing cgroup subsys cpuacct                                              
Initializing cgroup subsys memory                                               
Initializing cgroup subsys devices                                              
Initializing cgroup subsys freezer                                              
Initializing cgroup subsys net_cls                                              
CPU: Trace cache: 12K uops, L1 D cache: 16K                                     
CPU: L2 cache: 2048K                                                            
CPU 0/0x0 -> Node 0                                                             
CPU: Physical Processor ID: 0                                                   
CPU: Processor Core ID: 0                                                       
CPU0: Thermal monitoring enabled (TM1)                                          
using mwait in idle threads.                                                    
ACPI: Core revision 20081204                                                    
ftrace: converting mcount calls to 0f 1f 44 00 00                               
ftrace: allocating 18888 entries in 149 pages                                   
Setting APIC routing to flat                                                    
..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1                            
CPU0: Intel(R) Pentium(R) D CPU 3.40GHz stepping 04                             
Booting processor 1 APIC 0x1 ip 0x6000                                          
Initializing CPU#1                                                              
Calibrating delay using timer specific routine.. 6798.53 BogoMIPS (lpj=3399267) 
CPU: Trace cache: 12K uops, L1 D cache: 16K                                     
CPU: L2 cache: 2048K                                                            
CPU 1/0x1 -> Node 0                                                             
CPU: Physical Processor ID: 0                                                   
CPU: Processor Core ID: 1                                                       
CPU1: Thermal monitoring enabled (TM1)                                          
x86 PAT enabled: cpu 1, old 0x7040600070406, new 0x7010600070106                
CPU1: Intel(R) Pentium(R) D CPU 3.40GHz stepping 04                             
checking TSC synchronization [CPU#0 -> CPU#1]: passed.                          
Brought up 2 CPUs                                                               
Total of 2 processors activated (13598.96 BogoMIPS).                            
sizeof(vma)=176 bytes                                                           
sizeof(page)=56 bytes                                                           
sizeof(inode)=560 bytes                                                         
sizeof(dentry)=192 bytes                                                        
sizeof(ext3inode)=760 bytes                                                     
sizeof(buffer_head)=104 bytes                                                   
sizeof(skbuff)=232 bytes                                                        
sizeof(task_struct)=5880 bytes                                                  
CPU0 attaching sched-domain:                                                    
 domain 0: span 0-1 level CPU                                                   
  groups: 0 1                                                                   
CPU1 attaching sched-domain:                                                    
 domain 0: span 0-1 level CPU                                                   
  groups: 1 0                                                                   
net_namespace: 1904 bytes                                                       
Booting paravirtualized kernel on bare hardware                                 
regulator: core version 0.5                                                     
Time: 15:43:18  Date: 09/28/09                                                  
NET: Registered protocol family 16                                              
ACPI: bus type pci registered                                                   
PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255                
PCI: MCFG area at e0000000 reserved in E820                                     
PCI: Using MMCONFIG at e0000000 - efffffff                                      
PCI: Using configuration type 1 for base access                                 
bio: create slab <bio-0> at 0                                                   
ACPI: EC: Look up EC in DSDT                                                    
ACPI: Interpreter enabled                                                       
ACPI: (supports S0 S1 S3 S4 S5)                                                 
ACPI: Using IOAPIC for interrupt routing                                        
ACPI: No dock devices found.                                                    
ACPI: PCI Root Bridge [PCI0] (0000:00)                                          
pci 0000:00:03.0: PME# supported from D0 D1 D2 D3hot D3cold                     
pci 0000:00:03.0: PME# disabled                                                 
pci 0000:00:0a.0: reg 10 io port: [0xfc00-0xfc7f]                               
HPET not enabled in BIOS. You might try hpet=force boot option                  
pci 0000:00:0a.1: reg 10 io port: [0xf800-0xf83f]                               
pci 0000:00:0a.1: reg 20 io port: [0xf400-0xf43f]                               
pci 0000:00:0a.1: reg 24 io port: [0xf000-0xf03f]                               
pci 0000:00:0a.1: PME# supported from D3hot D3cold                              
pci 0000:00:0a.1: PME# disabled                                                 
pci 0000:00:0b.0: reg 10 32bit mmio: [0xcffff000-0xcfffffff]                    
pci 0000:00:0b.0: supports D1 D2                                                
pci 0000:00:0b.0: PME# supported from D0 D1 D2 D3hot D3cold                     
pci 0000:00:0b.0: PME# disabled                                                 
pci 0000:00:0b.1: reg 10 32bit mmio: [0xcfffe000-0xcfffe0ff]                    
pci 0000:00:0b.1: supports D1 D2                                                
pci 0000:00:0b.1: PME# supported from D0 D1 D2 D3hot D3cold                     
pci 0000:00:0b.1: PME# disabled                                                 
pci 0000:00:0d.0: reg 20 io port: [0xec00-0xec0f]                               
pci 0000:00:0e.0: reg 10 io port: [0x9f0-0x9f7]                                 
pci 0000:00:0e.0: reg 14 io port: [0xbf0-0xbf3]                                 
pci 0000:00:0e.0: reg 18 io port: [0x970-0x977]                                 
pci 0000:00:0e.0: reg 1c io port: [0xb70-0xb73]                                 
pci 0000:00:0e.0: reg 20 io port: [0xd800-0xd80f]                               
pci 0000:00:0e.0: reg 24 32bit mmio: [0xcfffd000-0xcfffdfff]                    
pci 0000:00:0e.1: reg 10 io port: [0x9e0-0x9e7]                                 
pci 0000:00:0e.1: reg 14 io port: [0xbe0-0xbe3]                                 
pci 0000:00:0e.1: reg 18 io port: [0x960-0x967]                                 
pci 0000:00:0e.1: reg 1c io port: [0xb60-0xb63]                                 
pci 0000:00:0e.1: reg 20 io port: [0xc400-0xc40f]                               
pci 0000:00:0e.1: reg 24 32bit mmio: [0xcfffc000-0xcfffcfff]                    
pci 0000:00:0e.2: reg 10 io port: [0xc000-0xc007]                               
pci 0000:00:0e.2: reg 14 io port: [0xbc00-0xbc03]                               
pci 0000:00:0e.2: reg 18 io port: [0xb800-0xb807]                               
pci 0000:00:0e.2: reg 1c io port: [0xb400-0xb403]                               
pci 0000:00:0e.2: reg 20 io port: [0xb000-0xb00f]                               
pci 0000:00:0e.2: reg 24 32bit mmio: [0xcfffb000-0xcfffbfff]                    
pci 0000:00:0f.1: reg 10 32bit mmio: [0xcfff0000-0xcfff3fff]                    
pci 0000:00:0f.1: PME# supported from D3hot D3cold                              
pci 0000:00:0f.1: PME# disabled                                                 
pci 0000:00:11.0: reg 10 32bit mmio: [0xcfffa000-0xcfffafff]                    
pci 0000:00:11.0: reg 14 io port: [0xac00-0xac07]                               
pci 0000:00:11.0: reg 18 32bit mmio: [0xcfff9000-0xcfff90ff]                    
pci 0000:00:11.0: reg 1c 32bit mmio: [0xcfff8000-0xcfff800f]                    
pci 0000:00:11.0: supports D1 D2                                                
pci 0000:00:11.0: PME# supported from D0 D1 D2 D3hot D3cold                     
pci 0000:00:11.0: PME# disabled                                                 
pci 0000:00:12.0: reg 10 32bit mmio: [0xcfff7000-0xcfff7fff]                    
pci 0000:00:12.0: reg 14 io port: [0xa800-0xa807]                               
pci 0000:00:12.0: reg 18 32bit mmio: [0xcfff6000-0xcfff60ff]                    
pci 0000:00:12.0: reg 1c 32bit mmio: [0xcfff5000-0xcfff500f]                    
pci 0000:00:12.0: supports D1 D2                                                
pci 0000:00:12.0: PME# supported from D0 D1 D2 D3hot D3cold                     
pci 0000:00:12.0: PME# disabled                                                 
pci 0000:01:00.0: reg 10 32bit mmio: [0xcc000000-0xccffffff]                    
pci 0000:01:00.0: reg 14 64bit mmio: [0xb0000000-0xbfffffff]                    
pci 0000:01:00.0: reg 1c 64bit mmio: [0xca000000-0xcbffffff]                    
pci 0000:01:00.0: reg 24 io port: [0x9c00-0x9c7f]                               
pci 0000:01:00.0: reg 30 32bit mmio: [0x000000-0x01ffff]                        
pci 0000:00:03.0: bridge io port: [0x9000-0x9fff]                               
pci 0000:00:03.0: bridge 32bit mmio: [0xca000000-0xcdffffff]                    
pci 0000:00:03.0: bridge 64bit mmio pref: [0xb0000000-0xbfffffff]               
pci 0000:02:07.0: reg 10 32bit mmio: [0xcfdff000-0xcfdff7ff]                    
pci 0000:02:07.0: reg 14 32bit mmio: [0xcfdf8000-0xcfdfbfff]                    
pci 0000:02:07.0: supports D1 D2                                                
pci 0000:02:07.0: PME# supported from D0 D1 D2 D3hot                            
pci 0000:02:07.0: PME# disabled                                                 
pci 0000:00:0f.0: transparent bridge                                            
pci 0000:00:0f.0: bridge io port: [0x8000-0x8fff]                               
pci 0000:00:0f.0: bridge 32bit mmio: [0xcfd00000-0xcfdfffff]                    
pci 0000:00:0f.0: bridge 32bit mmio pref: [0xcfe00000-0xcfefffff]               
ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]                             
ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]                        
ACPI Warning (nspredef-0940): \_SB_.PCI0.HUB0._PRT: Return Package type mismatch at index 2 - found [NULL Object Descriptor], expected Integer/Reference [20081204]                                                                             
ACPI: PCI Interrupt Link [LNK1] (IRQs 5 7 9 10 11 14 15) *0, disabled.          
ACPI: PCI Interrupt Link [LNK2] (IRQs 5 7 9 10 11 14 15) *0, disabled.          
ACPI: PCI Interrupt Link [LNK3] (IRQs 5 7 9 10 11 14 15) *0, disabled.          
ACPI: PCI Interrupt Link [LNK4] (IRQs 5 7 9 *10 11 14 15)                       
ACPI: PCI Interrupt Link [LXV5] (IRQs 5 7 9 *10 11 14 15)                       
ACPI: PCI Interrupt Link [LXV6] (IRQs 5 7 9 10 11 14 15) *0, disabled.          
ACPI: PCI Interrupt Link [LXV7] (IRQs 5 7 9 10 11 14 15) *0, disabled.          
ACPI: PCI Interrupt Link [LXV8] (IRQs 5 7 9 10 11 14 15) *0, disabled.          
ACPI: PCI Interrupt Link [LUBA] (IRQs 5 7 9 *10 11 14 15)                       
ACPI: PCI Interrupt Link [LMC1] (IRQs *5 7 9 10 11 14 15)                       
ACPI: PCI Interrupt Link [LMAC] (IRQs *5 7 9 10 11 14 15)                       
ACPI: PCI Interrupt Link [LAZA] (IRQs 5 7 9 10 *11 14 15)                       
ACPI: PCI Interrupt Link [LSMB] (IRQs 5 7 9 10 11 14 15) *0, disabled.          
ACPI: PCI Interrupt Link [LUB2] (IRQs 5 7 9 10 *11 14 15)                       
ACPI: PCI Interrupt Link [LIDE] (IRQs 5 7 9 10 11 14 15) *0, disabled.          
ACPI: PCI Interrupt Link [LSA0] (IRQs 5 7 9 10 *11 14 15)                       
ACPI: PCI Interrupt Link [LSA1] (IRQs 5 7 9 10 *11 14 15)                       
ACPI: PCI Interrupt Link [LSA2] (IRQs 5 7 9 *10 11 14 15)                       
ACPI: PCI Interrupt Link [APC1] (IRQs 16) *0, disabled.                         
ACPI: PCI Interrupt Link [APC2] (IRQs 17) *0, disabled.                         
ACPI: PCI Interrupt Link [APC3] (IRQs 18) *0, disabled.                         
ACPI: PCI Interrupt Link [APC4] (IRQs 19) *0                                    
ACPI: PCI Interrupt Link [AXV5] (IRQs 16) *0                                    
ACPI: PCI Interrupt Link [AXV6] (IRQs 16) *0, disabled.                         
ACPI: PCI Interrupt Link [AXV7] (IRQs 16) *0, disabled.                         
ACPI: PCI Interrupt Link [AXV8] (IRQs 16) *0, disabled.                         
ACPI: PCI Interrupt Link [AUBA] (IRQs 20 21 22 23) *0                           
ACPI: PCI Interrupt Link [AMA1] (IRQs 20 21 22 23) *0                           
ACPI: PCI Interrupt Link [AMAC] (IRQs 20 21 22 23) *0                           
ACPI: PCI Interrupt Link [AAZA] (IRQs 20 21 22 23) *0                           
ACPI: PCI Interrupt Link [AACI] (IRQs 20 21 22 23) *0, disabled.                
ACPI: PCI Interrupt Link [AMCI] (IRQs 20 21 22 23) *0, disabled.                
ACPI: PCI Interrupt Link [ASMB] (IRQs 20 21 22 23) *0, disabled.                
ACPI: PCI Interrupt Link [AUS2] (IRQs 20 21 22 23) *0                           
ACPI: PCI Interrupt Link [AIDE] (IRQs 20 21 22 23) *0, disabled.                
ACPI: PCI Interrupt Link [ASA0] (IRQs 20 21 22 23) *0                           
ACPI: PCI Interrupt Link [ASA1] (IRQs 20 21 22 23) *0                           
ACPI: PCI Interrupt Link [ASA2] (IRQs 20 21 22 23) *0                           
SCSI subsystem initialized                                                      
libata version 3.00 loaded.                                                     
usbcore: registered new interface driver usbfs                                  
usbcore: registered new interface driver hub                                    
usbcore: registered new device driver usb                                       
PCI: Using ACPI for IRQ routing                                                 
NetLabel: Initializing                                                          
NetLabel:  domain hash size = 128                                               
NetLabel:  protocols = UNLABELED CIPSOv4                                        
NetLabel:  unlabeled traffic allowed by default                                 
pnp: PnP ACPI init                                                              
ACPI: bus type pnp registered                                                   
pnp: PnP ACPI: found 13 devices                                                 
ACPI: ACPI bus type pnp unregistered                                            
system 00:00: ioport range 0x1000-0x107f has been reserved                      
system 00:00: ioport range 0x1080-0x10ff has been reserved                      
system 00:00: ioport range 0x1400-0x147f has been reserved                      
system 00:00: ioport range 0x1480-0x14ff has been reserved                      
system 00:00: ioport range 0x1800-0x187f has been reserved                      
system 00:00: ioport range 0x1880-0x18ff has been reserved                      
system 00:02: ioport range 0x4d0-0x4d1 has been reserved                        
system 00:02: ioport range 0x295-0x314 has been reserved                        
system 00:02: ioport range 0x880-0x88f has been reserved                        
system 00:0b: iomem range 0xe0000000-0xefffffff has been reserved               
system 00:0c: iomem range 0xd5800-0xd7fff has been reserved                     
system 00:0c: iomem range 0xf0000-0xf7fff could not be reserved                 
system 00:0c: iomem range 0xf8000-0xfbfff could not be reserved                 
system 00:0c: iomem range 0xfc000-0xfffff could not be reserved                 
system 00:0c: iomem range 0x7fef0000-0x7fefffff could not be reserved           
system 00:0c: iomem range 0xffff0000-0xffffffff has been reserved               
system 00:0c: iomem range 0x0-0x9ffff could not be reserved                     
system 00:0c: iomem range 0x100000-0x7feeffff could not be reserved             
system 00:0c: iomem range 0xfec00000-0xfec00fff has been reserved               
system 00:0c: iomem range 0xd0000000-0xdfffffff has been reserved               
system 00:0c: iomem range 0xfee00000-0xfee00fff has been reserved               
system 00:0c: iomem range 0xfeff0000-0xfeff0000 has been reserved               
pci 0000:00:03.0: PCI bridge, secondary bus 0000:01                             
pci 0000:00:03.0:   IO window: 0x9000-0x9fff                                    
pci 0000:00:03.0:   MEM window: 0xca000000-0xcdffffff                           
pci 0000:00:03.0:   PREFETCH window: 0x000000b0000000-0x000000bfffffff          
pci 0000:00:0f.0: PCI bridge, secondary bus 0000:02                             
pci 0000:00:0f.0:   IO window: 0x8000-0x8fff                                    
pci 0000:00:0f.0:   MEM window: 0xcfd00000-0xcfdfffff                           
pci 0000:00:0f.0:   PREFETCH window: 0x000000cfe00000-0x000000cfefffff          
pci 0000:00:03.0: setting latency timer to 64                                   
pci 0000:00:0f.0: setting latency timer to 64                                   
pci_bus 0000:00: resource 0 io:  [0x00-0xffff]                                  
pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffffffffffff]                  
pci_bus 0000:01: resource 0 io:  [0x9000-0x9fff]                                
pci_bus 0000:01: resource 1 mem: [0xca000000-0xcdffffff]                        
pci_bus 0000:01: resource 2 mem: [0xb0000000-0xbfffffff]                        
pci_bus 0000:01: resource 3 mem: [0x0-0x0]                                      
pci_bus 0000:02: resource 0 io:  [0x8000-0x8fff]                                
pci_bus 0000:02: resource 1 mem: [0xcfd00000-0xcfdfffff]                        
pci_bus 0000:02: resource 2 mem: [0xcfe00000-0xcfefffff]                        
pci_bus 0000:02: resource 3 io:  [0x00-0xffff]                                  
pci_bus 0000:02: resource 4 mem: [0x000000-0xffffffffffffffff]                  
NET: Registered protocol family 2                                               
IP route cache hash table entries: 65536 (order: 7, 524288 bytes)               
TCP established hash table entries: 262144 (order: 10, 4194304 bytes)           
TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)                    
TCP: Hash tables configured (established 262144 bind 65536)                     
TCP reno registered                                                             
NET: Registered protocol family 1                                               
checking if image is initramfs... it is                                         
Freeing initrd memory: 3619k freed                                              
audit: initializing netlink socket (disabled)                                   
type=2000 audit(1254152598.583:1): initialized                                  
HugeTLB registered 2 MB page size, pre-allocated 0 pages                        
VFS: Disk quotas dquot_6.5.2                                                    
Dquot-cache hash table entries: 512 (order 0, 4096 bytes)                       
msgmni has been set to 3978                                                     
SELinux:  Registering netfilter hooks                                           
alg: No test for stdrng (krng)                                                  
Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)            
io scheduler noop registered                                                    
io scheduler anticipatory registered                                            
io scheduler deadline registered                                                
io scheduler cfq registered (default)                                           
pci 0000:01:00.0: Boot video device                                             
pcieport-driver 0000:00:03.0: setting latency timer to 64                       
  alloc irq_desc for 24 on cpu 0 node 0                                         
  alloc kstat_irqs on cpu 0 node 0                                              
pcieport-driver 0000:00:03.0: irq 24 for MSI/MSI-X                              
pci_hotplug: PCI Hot Plug PCI Core version: 0.5                                 
pciehp: PCI Express Hot Plug Controller Driver version: 0.4                     
acpiphp: ACPI Hot Plug PCI Controller Driver version: 0.5                       
input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0       
ACPI: Power Button (FF) [PWRF]                                                  
input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1                                                                              
ACPI: Power Button (CM) [PWRB]                                                  
processor ACPI_CPU:00: registered as cooling_device0                            
ACPI: Processor [CPU0] (supports 8 throttling states)                           
processor ACPI_CPU:01: registered as cooling_device1                            
hpet_acpi_add: no address or irqs in _CRS                                       
Non-volatile memory driver v1.3                                                 
Linux agpgart interface v0.103                                                  
Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled                         
Switched to high resolution mode on CPU 1                                       
Switched to high resolution mode on CPU 0                                       
serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A                            
00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A                                 
brd: module loaded                                                              
loop: module loaded                                                             
Fixed MDIO Bus: probed                                                          
input: Macintosh mouse button emulation as /devices/virtual/input/input2        
Driver 'sd' needs updating - please use bus_type methods                        
Driver 'sr' needs updating - please use bus_type methods                        
ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver                      
ACPI: PCI Interrupt Link [AUS2] enabled at IRQ 23                               
  alloc irq_desc for 23 on cpu 0 node 0                                         
  alloc kstat_irqs on cpu 0 node 0                                              
ehci_hcd 0000:00:0b.1: PCI INT B -> Link[AUS2] -> GSI 23 (level, low) -> IRQ 23 
ehci_hcd 0000:00:0b.1: setting latency timer to 64                              
ehci_hcd 0000:00:0b.1: EHCI Host Controller                                     
ehci_hcd 0000:00:0b.1: new USB bus registered, assigned bus number 1            
ehci_hcd 0000:00:0b.1: debug port 1                                             
ehci_hcd 0000:00:0b.1: cache line size of 128 is not supported                  
ehci_hcd 0000:00:0b.1: irq 23, io mem 0xcfffe000                                
ehci_hcd 0000:00:0b.1: USB 2.0 started, EHCI 1.00                               
usb usb1: New USB device found, idVendor=1d6b, idProduct=0002                   
usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1              
usb usb1: Product: EHCI Host Controller                                         
usb usb1: Manufacturer: Linux 2.6.29.4-167.fc11.x86_64 ehci_hcd                 
usb usb1: SerialNumber: 0000:00:0b.1                                            
usb usb1: configuration #1 chosen from 1 choice                                 
hub 1-0:1.0: USB hub found                                                      
hub 1-0:1.0: 10 ports detected                                                  
ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver                          
ACPI: PCI Interrupt Link [AUBA] enabled at IRQ 22                               
  alloc irq_desc for 22 on cpu 0 node 0                                         
  alloc kstat_irqs on cpu 0 node 0                                              
ohci_hcd 0000:00:0b.0: PCI INT A -> Link[AUBA] -> GSI 22 (level, low) -> IRQ 22 
ohci_hcd 0000:00:0b.0: setting latency timer to 64                              
ohci_hcd 0000:00:0b.0: OHCI Host Controller                                     
ohci_hcd 0000:00:0b.0: new USB bus registered, assigned bus number 2            
ohci_hcd 0000:00:0b.0: irq 22, io mem 0xcffff000                                
usb usb2: New USB device found, idVendor=1d6b, idProduct=0001                   
usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1              
usb usb2: Product: OHCI Host Controller                                         
usb usb2: Manufacturer: Linux 2.6.29.4-167.fc11.x86_64 ohci_hcd                 
usb usb2: SerialNumber: 0000:00:0b.0                                            
usb usb2: configuration #1 chosen from 1 choice                                 
hub 2-0:1.0: USB hub found                                                      
hub 2-0:1.0: 10 ports detected                                                  
uhci_hcd: USB Universal Host Controller Interface driver                        
PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1                          
PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp                                                                  
serio: i8042 KBD port at 0x60,0x64 irq 1                                        
mice: PS/2 mouse device common for all mice                                     
rtc_cmos 00:05: RTC can wake from S4                                            
rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0                           
rtc0: alarms up to one year, y3k, 114 bytes nvram                               
device-mapper: uevent: version 1.0.3                                            
device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: dm-devel@redhat.com
cpuidle: using governor ladder                                                  
cpuidle: using governor menu                                                    
usbcore: registered new interface driver hiddev                                 
usbcore: registered new interface driver usbhid                                 
usbhid: v2.6:USB HID core driver                                                
nf_conntrack version 0.5.0 (16384 buckets, 65536 max)                           
CONFIG_NF_CT_ACCT is deprecated and will be removed soon. Please use            
nf_conntrack.acct=1 kernel paramater, acct=1 nf_conntrack module option or      
sysctl net.netfilter.nf_conntrack_acct=1 to enable it.                          
ip_tables: (C) 2000-2006 Netfilter Core Team                                    
TCP cubic registered                                                            
Initializing XFRM netlink socket                                                
NET: Registered protocol family 17                                              
registered taskstats version 1                                                  
  Magic number: 9:398:741                                                       
Initalizing network drop monitor service                                        
Freeing unused kernel memory: 1304k freed                                       
Write protecting the kernel read-only data: 1844k                               
input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3                                                                              
[drm] Initialized drm 1.1.0 20060810                                            
ACPI: PCI Interrupt Link [AXV5] enabled at IRQ 16                               
  alloc irq_desc for 16 on cpu 0 node 0                                         
  alloc kstat_irqs on cpu 0 node 0                                              
pci 0000:01:00.0: PCI INT A -> Link[AXV5] -> GSI 16 (level, low) -> IRQ 16      
pci 0000:01:00.0: setting latency timer to 64                                   
nouveau 0000:01:00.0: Detected an NV50 generation card (0x092a00a2)             
[drm] Initialized nouveau 0.0.12 20060213 for 0000:01:00.0 on minor 0           
usb 1-5: new high speed USB device using ehci_hcd and address 3                 
sata_nv 0000:00:0e.0: version 3.5                                               
ACPI: PCI Interrupt Link [ASA0] enabled at IRQ 21                               
  alloc irq_desc for 21 on cpu 0 node 0                                         
  alloc kstat_irqs on cpu 0 node 0                                              
sata_nv 0000:00:0e.0: PCI INT A -> Link[ASA0] -> GSI 21 (level, low) -> IRQ 21  
sata_nv 0000:00:0e.0: Using SWNCQ mode                                          
sata_nv 0000:00:0e.0: setting latency timer to 64                               
scsi0 : sata_nv                                                                 
scsi1 : sata_nv                                                                 
ata1: SATA max UDMA/133 cmd 0x9f0 ctl 0xbf0 bmdma 0xd800 irq 21                 
ata2: SATA max UDMA/133 cmd 0x970 ctl 0xb70 bmdma 0xd808 irq 21                 
usb 1-5: New USB device found, idVendor=0951, idProduct=1603                    
usb 1-5: New USB device strings: Mfr=1, Product=2, SerialNumber=3               
usb 1-5: Product: DataTraveler 2.0                                              
usb 1-5: Manufacturer: Kingston                                                 
usb 1-5: SerialNumber: 0019E000C6C1A8C062CF002E                                 
usb 1-5: configuration #1 chosen from 1 choice                                  
usb 2-1: new full speed USB device using ohci_hcd and address 2                 
usb 2-1: New USB device found, idVendor=0ac8, idProduct=303b                    
usb 2-1: New USB device strings: Mfr=1, Product=2, SerialNumber=0               
usb 2-1: Product: PC Camera                                                     
usb 2-1: Manufacturer: Vimicro Corp.                                            
usb 2-1: configuration #1 chosen from 1 choice                                  
usb 2-6: new low speed USB device using ohci_hcd and address 3                  
ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)                          
ata1.00: ATA-7: ST3320620AS, 3.AAE, max UDMA/133                                
ata1.00: 625142448 sectors, multi 16: LBA48 NCQ (depth 31/32)                   
ata1.00: configured for UDMA/133                                                
isa bounce pool size: 16 pages                                                  
scsi 0:0:0:0: Direct-Access     ATA      ST3320620AS      3.AA PQ: 0 ANSI: 5    
sd 0:0:0:0: [sda] 625142448 512-byte hardware sectors: (320 GB/298 GiB)         
sd 0:0:0:0: [sda] Write Protect is off                                          
sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00                                       
sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA                                                                         
sd 0:0:0:0: [sda] 625142448 512-byte hardware sectors: (320 GB/298 GiB)         
sd 0:0:0:0: [sda] Write Protect is off                                          
sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00                                       
sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA                                                                         
 sda: sda1 sda2 sda3                                                            
sd 0:0:0:0: [sda] Attached SCSI disk                                            
sd 0:0:0:0: Attached scsi generic sg0 type 0                                    
usb 2-6: New USB device found, idVendor=046d, idProduct=c501                    
usb 2-6: New USB device strings: Mfr=1, Product=2, SerialNumber=0               
usb 2-6: Product: USB Receiver                                                  
usb 2-6: Manufacturer: Logitech                                                 
usb 2-6: configuration #1 chosen from 1 choice                                  
input: Logitech USB Receiver as /devices/pci0000:00/0000:00:0b.0/usb2/2-6/2-6:1.0/input/input4                                                                  
generic-usb 0003:046D:C501.0001: input,hidraw0: USB HID v1.10 Mouse [Logitech USB Receiver] on usb-0000:00:0b.0-6/input0                                        
ata2: SATA link down (SStatus 0 SControl 300)                                   
ACPI: PCI Interrupt Link [ASA1] enabled at IRQ 20                               
  alloc irq_desc for 20 on cpu 0 node 0                                         
  alloc kstat_irqs on cpu 0 node 0                                              
sata_nv 0000:00:0e.1: PCI INT B -> Link[ASA1] -> GSI 20 (level, low) -> IRQ 20  
sata_nv 0000:00:0e.1: Using SWNCQ mode                                          
sata_nv 0000:00:0e.1: setting latency timer to 64                               
scsi2 : sata_nv                                                                 
scsi3 : sata_nv                                                                 
ata3: SATA max UDMA/133 cmd 0x9e0 ctl 0xbe0 bmdma 0xc400 irq 20                 
ata4: SATA max UDMA/133 cmd 0x960 ctl 0xb60 bmdma 0xc408 irq 20                 
ata3: SATA link down (SStatus 0 SControl 300)                                   
ata4: SATA link down (SStatus 0 SControl 300)                                   
ACPI: PCI Interrupt Link [ASA2] enabled at IRQ 23                               
sata_nv 0000:00:0e.2: PCI INT C -> Link[ASA2] -> GSI 23 (level, low) -> IRQ 23  
sata_nv 0000:00:0e.2: Using SWNCQ mode                                          
sata_nv 0000:00:0e.2: setting latency timer to 64                               
scsi4 : sata_nv                                                                 
scsi5 : sata_nv                                                                 
ata5: SATA max UDMA/133 cmd 0xc000 ctl 0xbc00 bmdma 0xb000 irq 23               
ata6: SATA max UDMA/133 cmd 0xb800 ctl 0xb400 bmdma 0xb008 irq 23               
ata5: SATA link down (SStatus 0 SControl 300)                                   
ata6: SATA link down (SStatus 0 SControl 300)                                   
pata_acpi 0000:00:0d.0: setting latency timer to 64                             
EXT4-fs: barriers enabled                                                       
kjournald2 starting: pid 89, dev dm-0:8, commit interval 5 seconds              
EXT4-fs: delayed allocation enabled                                             
EXT4-fs: file extents enabled                                                   
EXT4-fs: mballoc enabled                                                        
EXT4-fs: mounted filesystem dm-0 with ordered data mode                         
type=1404 audit(1254152604.415:2): enforcing=1 old_enforcing=0 auid=4294967295 ses=4294967295                                                                   
SELinux: 8192 avtab hash slots, 123719 rules.                                   
SELinux: 8192 avtab hash slots, 123719 rules.                                   
SELinux:  8 users, 11 roles, 2722 types, 127 bools, 1 sens, 1024 cats           
SELinux:  74 classes, 123719 rules                                              
SELinux:  Completing initialization.                                            
SELinux:  Setting up existing superblocks.                                      
SELinux: initialized (dev dm-0, type ext4), uses xattr                          
SELinux: initialized (dev tmpfs, type tmpfs), uses transition SIDs              
SELinux: initialized (dev usbfs, type usbfs), uses genfs_contexts               
SELinux: initialized (dev selinuxfs, type selinuxfs), uses genfs_contexts       
SELinux: initialized (dev mqueue, type mqueue), uses transition SIDs            
SELinux: initialized (dev hugetlbfs, type hugetlbfs), uses genfs_contexts       
SELinux: initialized (dev devpts, type devpts), uses transition SIDs            
SELinux: initialized (dev inotifyfs, type inotifyfs), uses genfs_contexts       
SELinux: initialized (dev tmpfs, type tmpfs), uses transition SIDs              
SELinux: initialized (dev anon_inodefs, type anon_inodefs), uses genfs_contexts 
SELinux: initialized (dev pipefs, type pipefs), uses task SIDs                  
SELinux: initialized (dev debugfs, type debugfs), uses genfs_contexts           
SELinux: initialized (dev sockfs, type sockfs), uses task SIDs                  
SELinux: initialized (dev proc, type proc), uses genfs_contexts                 
SELinux: initialized (dev bdev, type bdev), uses genfs_contexts                 
SELinux: initialized (dev rootfs, type rootfs), uses genfs_contexts             
SELinux: initialized (dev sysfs, type sysfs), uses genfs_contexts               
type=1403 audit(1254152604.695:3): policy loaded auid=4294967295 ses=4294967295 
udev: starting version 141                                                      
i2c-adapter i2c-0: nForce2 SMBus adapter at 0xf400                              
i2c-adapter i2c-1: nForce2 SMBus adapter at 0xf000                              
Linux video capture interface: v2.00                                            
gspca: main v2.5.0 registered                                                   
gspca: probing 0ac8:303b                                                        
Initializing USB Mass Storage driver...                                         
scsi6 : SCSI emulation for USB Mass Storage devices                             
usb-storage: device found at 3                                                  
usb-storage: waiting for device to settle before scanning                       
usbcore: registered new interface driver usb-storage                            
USB Mass Storage support registered.                                            
pata_amd 0000:00:0d.0: version 0.4.1                                            
pata_amd 0000:00:0d.0: setting latency timer to 64                              
scsi7 : pata_amd                                                                
scsi8 : pata_amd                                                                
ata7: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xec00 irq 14                 
ata8: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xec08 irq 15                 
input: PC Speaker as /devices/platform/pcspkr/input/input5                      
ata7.00: ATAPI: TEAC DV-W516GDM, M4S2, max UDMA/66                              
ata7: nv_mode_filter: 0x1f39f&0x1f01f->0x1f01f, BIOS=0x1f000 (0xc5000000) ACPI=0x1f01f (30:600:0x13)                                                            
ata7.00: limited to UDMA/33 due to 40-wire cable                                
ata7.00: configured for UDMA/33                                                 
scsi 7:0:0:0: CD-ROM            TEAC     DV-W516GDM       M4S2 PQ: 0 ANSI: 5    
sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray           
Uniform CD-ROM driver Revision: 3.20                                            
sr 7:0:0:0: Attached scsi CD-ROM sr0                                            
sr 7:0:0:0: Attached scsi generic sg1 type 5                                    
ata8: port disabled. ignoring.                                                  
forcedeth: Reverse Engineered nForce ethernet driver. Version 0.62.             
ACPI: PCI Interrupt Link [AMAC] enabled at IRQ 22                               
forcedeth 0000:00:11.0: PCI INT A -> Link[AMAC] -> GSI 22 (level, low) -> IRQ 22
forcedeth 0000:00:11.0: setting latency timer to 64                             
nv_probe: set workaround bit for reversed mac addr                              
forcedeth 0000:00:11.0: ifname eth0, PHY OUI 0x5043 @ 1, addr 00:04:4b:05:18:da 
forcedeth 0000:00:11.0: highdma csum vlan pwrctl mgmt timirq gbit lnktim msi desc-v3                                                                            
ACPI: PCI Interrupt Link [APC4] enabled at IRQ 19                               
  alloc irq_desc for 19 on cpu 0 node 0                                         
  alloc kstat_irqs on cpu 0 node 0                                              
firewire_ohci 0000:02:07.0: PCI INT A -> Link[APC4] -> GSI 19 (level, low) -> IRQ 19                                                                            
firewire_ohci 0000:02:07.0: setting latency timer to 64                         
firewire_ohci: Added fw-ohci device 0000:02:07.0, OHCI version 1.10             
ACPI: PCI Interrupt Link [AAZA] enabled at IRQ 21                               
HDA Intel 0000:00:0f.1: PCI INT B -> Link[AAZA] -> GSI 21 (level, low) -> IRQ 21
HDA Intel 0000:00:0f.1: setting latency timer to 64                             
hda_codec: Unknown model for ALC883, trying auto-probe from BIOS...             
ALSA sound/pci/hda/hda_codec.c:3507: autoconfig: line_outs=4 (0x14/0x15/0x16/0x17/0x0)                                                                          
ALSA sound/pci/hda/hda_codec.c:3511:    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)    
ALSA sound/pci/hda/hda_codec.c:3515:    hp_outs=1 (0x1b/0x0/0x0/0x0/0x0)        
ALSA sound/pci/hda/hda_codec.c:3516:    mono: mono_out=0x0                      
ALSA sound/pci/hda/hda_codec.c:3524:    inputs: mic=0x18, fmic=0x19, line=0x1a, fline=0x0, cd=0x0, aux=0x0                                                      
ACPI: PCI Interrupt Link [AMA1] enabled at IRQ 20                               
forcedeth 0000:00:12.0: PCI INT A -> Link[AMA1] -> GSI 20 (level, low) -> IRQ 20
forcedeth 0000:00:12.0: setting latency timer to 64                             
nv_probe: set workaround bit for reversed mac addr                              
firewire_core: created device fw0: GUID 1aa205bc00044b06, S400                  
forcedeth 0000:00:12.0: ifname eth1, PHY OUI 0x5043 @ 2, addr 00:04:4b:05:18:db 
forcedeth 0000:00:12.0: highdma csum vlan pwrctl mgmt timirq gbit lnktim msi desc-v3                                                                            
zc3xx: probe 2wr ov vga 0x0000                                                  
zc3xx: probe 3wr vga 1 0xe001                                                   
zc3xx: probe sensor -> 0013                                                     
zc3xx: Find Sensor MI0360. Chip revision e001                                   
gspca: probe ok                                                                 
usbcore: registered new interface driver zc3xx                                  
zc3xx: registered                                                               
device-mapper: multipath: version 1.0.5 loaded                                  
EXT4 FS on dm-0, internal journal on dm-0:8                                     
kjournald starting.  Commit interval 5 seconds                                  
EXT3 FS on sda2, internal journal                                               
EXT3-fs: mounted filesystem with ordered data mode.                             
SELinux: initialized (dev sda2, type ext3), uses xattr                          
SELinux: initialized (dev tmpfs, type tmpfs), uses transition SIDs              
swap_cgroup: uses 16288 bytes of vmalloc for pointer array space and 8339456 bytes to hold mem_cgroup pointers on swap                                          
swap_cgroup can be disabled by noswapaccount boot option.                       
Adding 4169720k swap on /dev/mapper/vg_bfg2k8-LogVol02.  Priority:-1 extents:1 across:4169720k                                                                  
SELinux: initialized (dev binfmt_misc, type binfmt_misc), uses genfs_contexts   
platform microcode: firmware: requesting intel-ucode/0f-06-04                   
platform microcode: firmware: requesting intel-ucode/0f-06-04                   
Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba       
Microcode Update Driver: v2.00 removed.                                         
p4-clockmod: P4/Xeon(TM) CPU On-Demand Clock Modulation available               
usb-storage: device scan complete                                               
scsi 6:0:0:0: Direct-Access     Kingston DataTraveler 2.0 1.00 PQ: 0 ANSI: 2    
sd 6:0:0:0: [sdb] 15695872 512-byte hardware sectors: (8.03 GB/7.48 GiB)        
sd 6:0:0:0: [sdb] Write Protect is off                                          
sd 6:0:0:0: [sdb] Mode Sense: 23 00 00 00                                       
sd 6:0:0:0: [sdb] Assuming drive cache: write through                           
sd 6:0:0:0: [sdb] 15695872 512-byte hardware sectors: (8.03 GB/7.48 GiB)        
sd 6:0:0:0: [sdb] Write Protect is off                                          
sd 6:0:0:0: [sdb] Mode Sense: 23 00 00 00                                       
sd 6:0:0:0: [sdb] Assuming drive cache: write through                           
 sdb: sdb1                                                                      
sd 6:0:0:0: [sdb] Attached SCSI removable disk                                  
sd 6:0:0:0: Attached scsi generic sg2 type 0                                    
NET: Registered protocol family 10                                              
lo: Disabled Privacy Extensions                                                 
ip6_tables: (C) 2000-2006 Netfilter Core Team                                   
RPC: Registered udp transport module.                                           
RPC: Registered tcp transport module.                                           
SELinux: initialized (dev rpc_pipefs, type rpc_pipefs), uses genfs_contexts     
JBD: barrier-based sync failed on dm-0:8 - disabling barriers                   
nouveau 0000:01:00.0: Allocating FIFO number 1                                  
nouveau 0000:01:00.0: nouveau_fifo_alloc: initialised FIFO 1                    
nouveau 0000:01:00.0: Allocating FIFO number 2                                  
nouveau 0000:01:00.0: nouveau_fifo_alloc: initialised FIFO 2                    
  alloc irq_desc for 25 on cpu 0 node 0                                         
  alloc kstat_irqs on cpu 0 node 0                                              
forcedeth 0000:00:12.0: irq 25 for MSI/MSI-X                                    
eth1: no link during initialization.                                            
ADDRCONF(NETDEV_UP): eth1: link is not ready                                    
  alloc irq_desc for 26 on cpu 0 node 0                                         
  alloc kstat_irqs on cpu 0 node 0                                              
forcedeth 0000:00:11.0: irq 26 for MSI/MSI-X                                    
eth0: no link during initialization.                                            
ADDRCONF(NETDEV_UP): eth0: link is not ready                                    
nouveau 0000:01:00.0: nouveau_fifo_free: freeing fifo 2                         
nouveau 0000:01:00.0: nouveau_fifo_free: freeing fifo 1                         
nouveau 0000:01:00.0: Allocating FIFO number 1                                  
nouveau 0000:01:00.0: nouveau_fifo_alloc: initialised FIFO 1                    
nouveau 0000:01:00.0: Allocating FIFO number 2                                  
nouveau 0000:01:00.0: nouveau_fifo_alloc: initialised FIFO 2                    
audit(1254152677.897:38302): arch=c000003e syscall=2 success=no exit=-2 a0=1065c30 a1=0 a2=7fffa2131648 a3=ffffffe8 items=1 ppid=1491 pid=1792 auid=4294967295 uid=0 gid=0 euid=0 suid=0 fsuid=0 egid=0 sgid=0 fsgid=0 tty=(none) ses=4294967295 comm="hal-acl-tool" exe="/usr/libexec/hal-acl-tool" subj=system_u:system_r:hald_acl_t:s0 key=(null)                                                            
audit(1254152677.897:38302):  cwd="/usr/libexec"                                
audit(1254152677.897:38302): item=0 name="/var/lib/PolicyKit-public/org.freedesktop.hal.lock.defaults-override"                                                 
audit(1254152677.897:38302):                                                    
audit(1254152677.899:38303): auid=4294967295 ses=4294967295 subj=system_u:system_r:readahead_t:s0 op=remove rule key=(null) list=2 res=1                        
audit(1254152677.899:38304): audit_enabled=0 old=1 auid=4294967295 ses=4294967295 subj=system_u:system_r:readahead_t:s0 res=1                                   
CPU0 attaching NULL sched-domain.                                               
CPU1 attaching NULL sched-domain.                                               
CPU0 attaching sched-domain:                                                    
 domain 0: span 0-1 level CPU                                                   
  groups: 0 1                                                                   
CPU1 attaching sched-domain:                                                    
 domain 0: span 0-1 level CPU                                                   
  groups: 1 0                                                                   
CPU0 attaching NULL sched-domain.                                               
CPU1 attaching NULL sched-domain.                                               
CPU0 attaching sched-domain:                                                    
 domain 0: span 0-1 level CPU                                                   
  groups: 0 1                                                                   
CPU1 attaching sched-domain:                                                    
 domain 0: span 0-1 level CPU                                                   
  groups: 1 0                                                                   
ALSA sound/pci/hda/hda_intel.c:1101: Too big adjustment 32: adj=128, bytes=128, size=4096, periods=32                                                           
ALSA sound/pci/hda/hda_intel.c:1101: Too big adjustment 32: adj=128, bytes=128, size=4096, periods=32                                                           
ALSA sound/pci/hda/hda_intel.c:1101: Too big adjustment 32: adj=128, bytes=128, size=4096, periods=32                                                           
ALSA sound/pci/hda/hda_intel.c:1101: Too big adjustment 32: adj=128, bytes=128, size=4096, periods=32                                                           
ALSA sound/pci/hda/hda_intel.c:1101: Too big adjustment 32: adj=128, bytes=128, size=4096, periods=32                                                           
ALSA sound/pci/hda/hda_intel.c:1101: Too big adjustment 32: adj=128, bytes=128, size=4096, periods=32
ALSA sound/pci/hda/hda_intel.c:1101: Too big adjustment 32: adj=256, bytes=128,size=4096, periods=32
ALSA sound/pci/hda/hda_intel.c:1101: Too big adjustment 32: adj=128, bytes=128,size=4096, periods=32
ALSA sound/pci/hda/hda_intel.c:1101: Too big adjustment 32: adj=128, bytes=128,size=4096, periods=32
ALSA sound/pci/hda/hda_intel.c:1101: Too big adjustment 32: adj=384, bytes=384,size=12288, periods=32
ALSA sound/pci/hda/hda_intel.c:1101: Too big adjustment 32: adj=128, bytes=128,size=4096, periods=32
ALSA sound/pci/hda/hda_intel.c:1101: Too big adjustment 32: adj=128, bytes=128,size=4096, periods=32
ALSA sound/pci/hda/hda_intel.c:1101: Too big adjustment 32: adj=384, bytes=384,size=12288, periods=32
ALSA sound/pci/hda/hda_intel.c:1101: Too big adjustment 32: adj=128, bytes=128,size=4096, periods=32
ALSA sound/pci/hda/hda_intel.c:1101: Too big adjustment 32: adj=128, bytes=128,size=4096, periods=32
ALSA sound/pci/hda/hda_intel.c:1101: Too big adjustment 32: adj=384, bytes=384,size=12288, periods=32
ALSA sound/pci/hda/hda_intel.c:1101: Too big adjustment 32: adj=128, bytes=128,size=4096, periods=32
ALSA sound/pci/hda/hda_intel.c:1101: Too big adjustment 32: adj=128, bytes=128,size=4096, periods=32
ALSA sound/pci/hda/hda_intel.c:1101: Too big adjustment 32: adj=512, bytes=128,size=4096, periods=32
ALSA sound/pci/hda/hda_intel.c:1101: Too big adjustment 32: adj=128, bytes=128,size=4096, periods=32
ALSA sound/pci/hda/hda_intel.c:1101: Too big adjustment 32: adj=128, bytes=128,size=4096, periods=32
ALSA sound/pci/hda/hda_intel.c:1101: Too big adjustment 32: adj=128, bytes=128,size=4096, periods=32
ALSA sound/pci/hda/hda_intel.c:1101: Too big adjustment 32: adj=128, bytes=128,size=4096, periods=32
**[root@BFG-2k8 ~]#**
```

---

### Post by C0NSTANTIN on 2009-09-28
Further findings:

**Guaranteed things that trigger the bug:**
-Powering off HDD for less then 1 minute.
-Suspend
-Hibernate


**Partial Solution**
1.Have a fail-safe Windows XP Operating System installed on a separate partition.
2.Each time the Error occurs, boot Windows XP and install "NVIDIA Storage Driver" that came with the Mother Board, weather you have it installed already or not.
3.Reboot windows Xp so that the changes can take effect.

xUbuntu will now boot once again without any loss of data.

The only problem is that you will [COLOR="Red"]repeat this actions each time you power off/suspend to Disk/Suspend to RAM[/COLOR] ...
Also, Bootloader Menu might go blank [though not jam itself] and you would have to guess witch boot you chose.

Will a proper hotfix come in a new update soon?

---

### Post by C0NSTANTIN on 2009-09-30
That's it ... all the information one could ask from an user ...
3000 hits ...

is anyone noticing this?

---

### Post by Eskobar on 2009-10-05
> **C0NSTANTIN said:**
> That's it ... all the information one could ask from an user ...
3000 hits ...

is anyone noticing this?


Sorry your not getting any help with this bro.  I'm a newbie as well, so I haven't the slightest clue.  I have been trying to install arch on my machine for the past 3 days, but cant get it to boot right.  I just started getting this **"[   11.292011] ata1 SRST: failed (errno=-16)" **message as well.  The ironic part is....... i'm using an IDE drive.  I even disabled sata in bios.  I just reinstalled Ubuntu from a live cd.  I still get the error when I reboot, but it does boot.  I will continue to scour the web and if I find anything relevant, I will post back.  Oh I might also mention that I tried this with 3 different hard drives and all of them have the same error.   I had to pop in an xp cd to format the drive.......can someone please help.   Sounds like the Linux community is getting alot of folks that want to switch, but they are scared because of problems like this.  Some of us have time to tinker with our systems, but most dont and wont.  With that being said....... COME ON LINUX GURU'S...HELP THE NEWBS OUT!!!!!!!!!


EDIT : check this thread out  [http://ubuntuforums.org/showthread.php?t=300055](http://ubuntuforums.org/showthread.php?t=300055) if that helps post back.  If I try it out before you, I will do the same

---

### Post by jefelex on 2009-10-05
Im not sure about all the hassles you are having, but if you have to use microsloft to install device drivers for your hard drives, that is where I'd start! Are they running natively from your bios?

just my 2 cents!

John

---

### Post by Hubi5171 on 2009-10-22
My solution to this problem was -
cause: HDD jumper incorrect, fix: correction of the jumper
This problem is not limited to AMD 64 platform. The many occourances of this symptom seen on the web are different in detail, as it is the detailed messages, and most likely also the cause. My limited understanding is, that the kernel is not in harmony with the hardware.
My system affected has a Pentium 4 with 1700 MHz, the HDD is WDC WD800JB which is an 80GB parallel ATA drive. It is a test machine for me, and lately I have been installing serveral different Linux distribution (ZevenOS, slitaz, Puppy Linux and some more and later XBMC from Live CD, than Ubuntu Studio 9.04 and than XBMC, Mythbuntu, and now LinuxMCE).
On one or other occation I got "SRST: failed (errno=-16)", delaying the boot process but no real problem. Now with LinuxMCE, which is based on kubuntu 8.10-i386, the problem got persistent, Installation to entire drive, automatic partitioning, everything went O.K., but booting from HDD stops now with a long saga telling possible causes, ending with ALERT! /dev/disk/by - uuid/3f0fe.....(long hex string) does not exist Dropping to a shell
Busy Box v 1.102 (Ubuntu....
(initramfs) _ (blinking cursor)
My wonder-tool is "parted magic" (4.4 live CD or USB stick). Edited menu.lst to add "rootdelay=40" as an boot argument. Made the partition smaller to 32GB. Both did not help. Checked on wcd.com the jumpers for my drive, being the only drive and was jumperd as master with slave present.
Corrected this and the HDD booted up login screen, further desktop (KDE 4.10) Now I can further play around digging into LinuxMCE.
ciao   Hubi
PS: all I did was from tips I found in the WWW, thanks to the authors.

---

### Post by C0NSTANTIN on 2009-10-26
the problem is that [NVIDIA hotfix NV121906]("http://www.nvidia.com/object/680i_hotfix.html")
the problem was not address under linux.

if you're saying about jumpers, sata2 slots, dust cleaning, checksum burning .... then you did not had the same problem, since my problem persisted even after i tried all that.

[the benefits of having bugzilla working for your distro]("https://admin.fedoraproject.org/updates/kernel-2.6.30.9-90.fc11")
of course ... the kernel does not work for that flaw :) but things more much quicker then here. [COLOR=Red]3,978 views[/COLOR] ... soon 4k and no answer to this problem..  [srry]

---

