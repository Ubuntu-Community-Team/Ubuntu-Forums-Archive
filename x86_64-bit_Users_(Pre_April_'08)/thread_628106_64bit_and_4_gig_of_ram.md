---
title: "64bit and 4 gig of ram"
date: 2007-11-30
forum: x86 64-bit Users (Pre April '08)
---

### Post by rbprogrammer on 2007-11-30
i know there are a lot of threads here now with people trying to install 4 gigs of ram on a computer.  i have seen them all and i am in the process of getting mine to work.  it seems that in the 32bit version of gutsy (or i guess with any 32bit linux version), you need to recompile with a certain flag or what have you...

but i also saw somewhere that the 64bit version comes with that already enable.  now on my desktop i went with the 32bit version b/c i could not get my wireless card to work with the 64bit ubuntu feisty, so i went with the 32bit.  but now that gutsy is out, and i now have 2 extra sticks (4gigs total), i want to utilize all 4 gigs.

i am running the 64bit live cd and my wireless card is working.  so i *should* not be worrying about that when i install.  but when i go to System -> Administration -> System Monitor, it says i have **3.9GB** of ram.  and when i do the free command, i get:
```

ubuntu@ubuntu:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          **3960**        790       3169          0         96        413
-/+ buffers/cache:        280       3680
Swap:          980          0        980

```
but then when i do the lshw command i get:
```

ubuntu@ubuntu:~$ lshw
WARNING: you should run this program as super-user.
ubuntu                    
    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory:0
          description: System memory
          physical id: 3
          size: **4864MB**
     *-cpu
          product: AMD Athlon(tm) 64 X2 Dual Core Processor 3800+
          vendor: Advanced Micro Devices [AMD]
          physical id: 5
          bus info: cpu@0
          size: 2GHz
          capacity: 2GHz
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp x86-64 3dnowext 3dnow pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy cpufreq
     *-memory:1 UNCLAIMED
          description: Memory controller
          product: CK804 Memory Controller
          vendor: nVidia Corporation
          physical id: 0
          bus info: pci@0000:00:00.0
          version: a3
          width: 32 bits
          clock: 66MHz (15.2ns)
          capabilities: bus_master cap_list
          configuration: latency=0
     *-isa
          description: ISA bridge
          product: CK804 ISA Bridge
          vendor: nVidia Corporation
          physical id: 1
          bus info: pci@0000:00:01.0
          version: a3
          width: 32 bits
          clock: 66MHz
          capabilities: isa bus_master
          configuration: latency=0
     *-serial
          description: SMBus
          product: CK804 SMBus
          vendor: nVidia Corporation
          physical id: 1.1
          bus info: pci@0000:00:01.1
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: cap_list
          configuration: driver=nForce2_smbus latency=0 maxlatency=1 mingnt=3 module=i2c_nforce2
     *-usb:0
          description: USB Controller
          product: CK804 USB Controller
          vendor: nVidia Corporation
          physical id: 2
          bus info: pci@0000:00:02.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: ohci bus_master cap_list
          configuration: driver=ohci_hcd latency=0 maxlatency=1 mingnt=3 module=ohci_hcd
     *-usb:1
          description: USB Controller
          product: CK804 USB Controller
          vendor: nVidia Corporation
          physical id: 2.1
          bus info: pci@0000:00:02.1
          version: a3
          width: 32 bits
          clock: 66MHz
          capabilities: ehci bus_master cap_list
          configuration: driver=ehci_hcd latency=0 maxlatency=1 mingnt=3 module=ehci_hcd
     *-multimedia
          description: Multimedia audio controller
          product: CK804 AC'97 Audio Controller
          vendor: nVidia Corporation
          physical id: 4
          bus info: pci@0000:00:04.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: bus_master cap_list
          configuration: driver=Intel ICH latency=0 maxlatency=5 mingnt=2 module=snd_intel8x0
     *-ide:0
          description: IDE interface
          product: CK804 IDE
          vendor: nVidia Corporation
          physical id: 6
          bus info: pci@0000:00:06.0
          version: f2
          width: 32 bits
          clock: 66MHz
          capabilities: ide bus_master cap_list
          configuration: driver=AMD_IDE latency=0 maxlatency=1 mingnt=3 module=amd74xx
        *-ide
             description: IDE Channel 1
             physical id: 1
             bus info: ide@1
             logical name: ide1
             clock: 66MHz
           *-cdrom:0
                product: SONY DVD RW DRU-800A
                physical id: 0
                bus info: ide@1.0
                logical name: /dev/hdc
                capacity: 696MB
                capabilities: packet
           *-cdrom:1
                product: DVD RW DRU-820A
                physical id: 1
                bus info: ide@1.1
                logical name: /dev/hdd
                capabilities: packet
     *-ide:1
          description: IDE interface
          product: CK804 Serial ATA Controller
          vendor: nVidia Corporation
          physical id: 7
          bus info: pci@0000:00:07.0
          version: f3
          width: 32 bits
          clock: 66MHz
          capabilities: ide bus_master cap_list
          configuration: driver=sata_nv latency=0 maxlatency=1 mingnt=3 module=sata_nv
     *-ide:2
          description: IDE interface
          product: CK804 Serial ATA Controller
          vendor: nVidia Corporation
          physical id: 8
          bus info: pci@0000:00:08.0
          version: f3
          width: 32 bits
          clock: 66MHz
          capabilities: ide bus_master cap_list
          configuration: driver=sata_nv latency=0 maxlatency=1 mingnt=3 module=sata_nv
     *-pci:0
          description: PCI bridge
          product: CK804 PCI Bridge
          vendor: nVidia Corporation
          physical id: 9
          bus info: pci@0000:00:09.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: pci subtractive_decode bus_master
        *-network
             description: Wireless interface
             product: AR2413 802.11bg NIC
             vendor: Atheros Communications, Inc.
             physical id: 8
             bus info: pci@0000:01:08.0
             logical name: wifi0
             version: 01
             serial: 00:13:46:6f:21:b3
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list logical ethernet physical wireless
             configuration: broadcast=yes driver=ath_pci ip=192.168.1.3 latency=168 maxlatency=28 mingnt=10 module=ath_pci multicast=yes wireless=IEEE 802.11g
     *-bridge
          description: Ethernet interface
          product: CK804 Ethernet Controller
          vendor: nVidia Corporation
          physical id: a
          bus info: pci@0000:00:0a.0
          logical name: eth0
          version: a3
          serial: 00:50:8d:97:8d:e2
          width: 32 bits
          clock: 66MHz
          capabilities: bridge bus_master cap_list ethernet physical
          configuration: broadcast=yes driver=forcedeth driverversion=0.60 latency=0 maxlatency=20 mingnt=1 module=forcedeth multicast=yes
     *-pci:1
          description: PCI bridge
          product: CK804 PCIE Bridge
          vendor: nVidia Corporation
          physical id: b
          bus info: pci@0000:00:0b.0
          version: a3
          width: 32 bits
          clock: 33MHz
          capabilities: pci normal_decode bus_master cap_list
          configuration: driver=pcieport-driver
     *-pci:2
          description: PCI bridge
          product: CK804 PCIE Bridge
          vendor: nVidia Corporation
          physical id: c
          bus info: pci@0000:00:0c.0
          version: a3
          width: 32 bits
          clock: 33MHz
          capabilities: pci normal_decode bus_master cap_list
          configuration: driver=pcieport-driver
     *-pci:3
          description: PCI bridge
          product: CK804 PCIE Bridge
          vendor: nVidia Corporation
          physical id: d
          bus info: pci@0000:00:0d.0
          version: a3
          width: 32 bits
          clock: 33MHz
          capabilities: pci normal_decode bus_master cap_list
          configuration: driver=pcieport-driver
     *-pci:4
          description: PCI bridge
          product: CK804 PCIE Bridge
          vendor: nVidia Corporation
          physical id: e
          bus info: pci@0000:00:0e.0
          version: a3
          width: 32 bits
          clock: 33MHz
          capabilities: pci normal_decode bus_master cap_list
          configuration: driver=pcieport-driver
        *-display
             description: VGA compatible controller
             product: GeForce 8600 GT
             vendor: nVidia Corporation
             physical id: 0
             bus info: pci@0000:05:00.0
             version: a1
             width: 64 bits
             clock: 33MHz
             capabilities: vga bus_master cap_list
             configuration: latency=0
     *-pci:5
          description: Host bridge
          product: K8 [Athlon64/Opteron] HyperTransport Technology Configuration
          vendor: Advanced Micro Devices [AMD]
          physical id: 100
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:6
          description: Host bridge
          product: K8 [Athlon64/Opteron] Address Map
          vendor: Advanced Micro Devices [AMD]
          physical id: 101
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:7
          description: Host bridge
          product: K8 [Athlon64/Opteron] DRAM Controller
          vendor: Advanced Micro Devices [AMD]
          physical id: 102
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:8
          description: Host bridge
          product: K8 [Athlon64/Opteron] Miscellaneous Control
          vendor: Advanced Micro Devices [AMD]
          physical id: 103
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k8temp module=k8temp

```
clearly there is a contradiction.  now which one is the right value??  my thinking is that the lshw command is more accurate b/c it would take into account the memory with other devices on / connected-to my motherboard (ie video card, etc..).  am i right there.  and if i install the 64bit ubuntu, will it utilize (that is if i can fill up 4 gigs of ram) the 4 sticks??  and i am assuming that i dont need to enable anything in my BIOS b/c the live cd sees the full 4 gigs.  am i right on that assumption?

i guess my final question is, is everything working?  the contradictions appear in three places, so i am just a little confused.. maybe there are some software rounding errors??

comments, suggestions, advice is greatly appreciated. :guitar: ..

---

### Post by bonestonne on 2007-12-01
that last .1GB of RAM is used by other parts of the system. my sisters computer has 1gb of RAM and he computer only says there's 960MB installed. it depends on the memory swap with the graphics card/adapter.

i only have 3gb of RAM installed, but i use 64bit, but there's no sharing RAM with graphics, somehow, so i always see 3GB.

--its not a bad thing to share memory with graphics, it actually allows for a better display.

---

### Post by insane_alien on 2007-12-01
yeah, that would be a graphics chip reserving sytem RAM along with space for the kernel. and the fact you'r running a LiveCD that makes a ramdisk on startup so this area is no available to the system.

---

### Post by rbprogrammer on 2007-12-01
i dont get it though, now System -> Administration -> System Monitor says i have **3.2 gigs**.  but then there is :
```

$ free -m
             total       used       free     shared    buffers     cached
Mem:          **3277**       1763       1514          0         40       1255
-/+ buffers/cache:        468       2809
Swap:          980          0        980

```
and this:
```

$ lshw
...
     *-memory:0
          description: System memory
          physical id: 3
          size: **3327MB**
...

```
i understand that the system would subtract ram like that in the 32bit version, but why in the 64bit version??  should i open every program imaginable and start to use up 3.2 gigs, would it start to use the swap afterwards?? or would it continue to use the rest of that 0.8GB that is not being *seen*??

i thought the 64bit version can handle something like 16GB just because of the way it was programmed..

NOTE:
[LIST]
[*]i also had to add in the GRUB boot entry "mem=4096M" so that the system would not do its random reboots.
[*]i also enabled that "memory remapping" thing in my BIOS
[/LIST]
shouldn't my system be registering more that the 4 gigs of memory?? i mean i have the 4 one-gigabyte sticks in, with a graphics card that has 256megabytes, and whatever other devices have their own memory.

---

### Post by rbprogrammer on 2007-12-01
oh, i installed the 64bit ubuntu, and that are the readings i was getting..

---

### Post by fjgaude on 2007-12-01
What motherboard are you using?

---

### Post by rbprogrammer on 2007-12-01
abit kn9 :confused: ..

and for some reason, my computer rebooted a few minutes ago.. for no reason.. why are there so many problems with installing 4 gigabytes?? i thought it should of just been as easy as just putting the sticks in the ram slots

---

### Post by fjgaude on 2007-12-02
I would suspect that neither the software nor motherboard people test enough with that much RAM. Afterall such has only really been readily available for a short time. Sad state of affairs but it's a reality.

Do make sure you have looked into your BIOS and have it set to do big RAM.

---

### Post by rbprogrammer on 2007-12-04
> **fjgaude said:**
> I would suspect that neither the software nor motherboard people test enough with that much RAM. Afterall such has only really been readily available for a short time. Sad state of affairs but it's a reality.

Do make sure you have looked into your BIOS and have it set to do big RAM.
after doing some more googling, i have concluded to exactly what you have said.  i'm sure its possible to patch something to make this work, but i dont know how to do it and i dont know when someone else will do something to remedy this.

as far as my BIOS, everything seems to be configured correctly, and in GRUB i booted linux with the "mem=4096M" flag.  and i still read around 3.2GB.  hrm, i wonder if it is possible to put in a different value instead of 4096??  i will look into that later..

well, i guess i will just have to live with the 3.2GB for awhile then in a few months or so i will hop back on this topic and see if i can find anything progressive.

---

### Post by ian dobson on 2007-12-05
Hi,

Go into you bios an enable memory relocation. This will push some of your ram above the 4Gb boundry so it won't be "used" by your onboard cards.

On my big box Q6600, 4Gb ram, 5x500Gb harddisks I see about 3.8Gb ram when I enable the option in bios.

Regards
Ian Dobson

---

### Post by hutxubix on 2007-12-05
I also have 4 Gb and I see 3985584k total, what I have always thought to be ok since in 32bits I saw less than 3.2Gb

---

### Post by rbprogrammer on 2007-12-05
> **ian dobson said:**
> 
Go into you bios an enable memory relocation. This will push some of your ram above the 4Gb boundry so it won't be "used" by your onboard cards.

in my BIOS there is nothing called "memory location", but there is "memory remapping".  i enabled that, but i still have only 3.2gigs being registered but ubuntu.

---

### Post by rbprogrammer on 2007-12-05
> **hutxubix said:**
> I also have 4 Gb and I see 3985584k total, what I have always thought to be ok since in 32bits I saw less than 3.2Gb
are you saying that you have the 64bit ubuntu installed and you see all 4 gigs of ram? well, i guess 3.8 / 3.9.....

---

### Post by Alan Painter on 2007-12-29
Which BIOS do you have?  In the Phoenix BIOS, I don't see a Memory Relocation option.

---

