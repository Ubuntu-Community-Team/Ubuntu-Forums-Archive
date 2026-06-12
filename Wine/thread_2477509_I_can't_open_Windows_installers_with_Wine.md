---
title: "I can't open Windows installers with Wine"
date: 2022-07-27
forum: Wine
---

### Post by gatajapa on 2022-07-27
Hello friends! Please welcome me as I am the newest Linux user who has migrated from Windows. I installed Ubuntu today on my machine because I was mad at Microsoft for a few reasons.

So, friends, as my first question is that I installed Wine through the Ubuntu store and when I right-click on the Windows installer and choose "Open with another application" I don't find it in the list. At the moment I am trying to install the program called Yumi. Remembering that I'm using the latest version of Ubuntu available on the site to download.

So, any help?

---

### Post by gatajapa on 2022-07-28
> **gatajapa said:**
> So, friends, as my first question is that I installed Wine through the Ubuntu store and when I right-click on the Windows installer and choose "Open with another application" I don't find it in the list. At the moment I am trying to install the program called Yumi. Remembering that I'm using the latest version of Ubuntu available on the site to download.

So, any help?

Hello friends! I found this tutorial below and it worked for me, but there's still something else.

[https://help.ubuntu.com/community/Wine](https://help.ubuntu.com/community/Wine)

It's just that, by the way, I'm going to have to keep opening the terminal every time I want to start a Windows application, and I don't want that at all. Well, this tutorial teaches a way to not need it anymore, but it turns out that new versions of Ubuntu no longer have this option to Create a Launcher by clicking with the right mouse button on the desktop.

So, how would I do it, friends?

---

### Post by mIk3_08 on 2022-07-28
> **gatajapa said:**
> Hello friends! Please welcome me as I am the  newest Linux user who has migrated from Windows. I installed Ubuntu  today on my machine because I was mad at Microsoft for a few reasons.

So, friends, as my first question is that I installed Wine through the  Ubuntu store and when I right-click on the Windows installer and choose  "Open with another application" I don't find it in the list. At the  moment I am trying to install the program called Yumi. Remembering that  I'm using the latest version of Ubuntu available on the site to  download.

So, any help?
I prefer using vm than wine. Wine needs a lot combination of  library/runtime library and packages to run successfully. If you are  first time using it, you might ruin your Linux Ubuntu system. 
Please run the command below and post the information here in this thread. Regards and cheers.
```
hostnamectl status
```

---

### Post by gatajapa on 2022-07-28
> **mIk3_08 said:**
>  Please run the command below and post the information here in this thread.
```
hostnamectl status
```

This appears:

 Static hostname: ganso-desktop
       Icon name: computer-desktop
         Chassis: desktop
      Machine ID: 7b428ce41eb54fe7b78d70428e447918
         Boot ID: 69513aea4dda458c924b15cb6c590216
Operating System: Ubuntu 22.04 LTS                
          Kernel: Linux 5.15.0-41-generic
    Architecture: x86-64
 Hardware Vendor: To Be Filled By O.E.M.
  Hardware Model: To Be Filled By O.E.M.

---

### Post by mIk3_08 on 2022-07-29
> **gatajapa said:**
> This appears:

 Static hostname: ganso-desktop
       Icon name: computer-desktop
         Chassis: desktop
      Machine ID: 7b428ce41eb54fe7b78d70428e447918
         Boot ID: 69513aea4dda458c924b15cb6c590216
Operating System: Ubuntu 22.04 LTS                
          Kernel: Linux 5.15.0-41-generic
    Architecture: x86-64
 Hardware Vendor: To Be Filled By O.E.M.
  Hardware Model: To Be Filled By O.E.M.
Please run this  command below in your terminal and post the results here in this thread.  This command will show the UbuntuForum community your system hardware  specifications because we want to know that your system is able to run  some applications simultaneously. Regards and cheers.

---

### Post by gatajapa on 2022-07-29
> **mIk3_08 said:**
> Please run this  command below in your terminal and post the results here in this thread.  This command will show the UbuntuForum community your system hardware  specifications because we want to know that your system is able to run  some applications simultaneously. Regards and cheers.

Hey friend, that's what I did and that's what turned up. But if you want to know my hardware, I have the following:

Core i5 6600
8 GB of RAM
Geforce GTX 750 Ti

If you need me to post anything else just say so. But could you help me with my question?

---

### Post by mIk3_08 on 2022-07-30
> **gatajapa said:**
> Hey friend, that's what I did and that's what turned up. But if you want to know my hardware, I have the following:

Core i5 6600
8 GB of RAM
Geforce GTX 750 Ti

If you need me to post anything else just say so. But could you help me with my question?
Oh I wasn't able to put the command. Here is the command. Regards and cheers.
```
sudo lshw
```

---

### Post by gatajapa on 2022-07-30
> **mIk3_08 said:**
> Oh I wasn't able to put the command. Here is the command. Regards and cheers.


Here it is:

```

ganso-desktop               
    descrição: Computador desktop
    produto: To Be Filled By O.E.M. (To Be Filled By O.E.M.)
    fabricante: To Be Filled By O.E.M.
    versão: To Be Filled By O.E.M.
    serial: To Be Filled By O.E.M.
    largura: 64 bits
    capacidades: smbios-2.8 dmi-2.8 smp vsyscall32
    configuração: boot=normal chassis=desktop family=To Be Filled By O.E.M. sku=To Be Filled By O.E.M. uuid=03000200-0400-0500-0006-000700080009
  *-core
       descrição: Placa-mãe
       produto: H110M-HG4
       fabricante: ASRock
       ID físico: 0
       serial: M8S-21651803056
     *-firmware
          descrição: BIOS
          fabricante: American Megatrends Inc.
          ID físico: 0
          versão: P7.50
          date: 01/06/2021
          tamanho: 64KiB
          capacidade: 6MiB
          capacidades: pci upgrade shadowing cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer acpi usb biosbootspecification uefi
     *-cache:0
          descrição: L1 cache
          ID físico: a
          slot: L1 Cache
          tamanho: 128KiB
          capacidade: 128KiB
          capacidades: synchronous internal write-back data
          configuração: level=1
     *-cache:1
          descrição: L1 cache
          ID físico: b
          slot: L1 Cache
          tamanho: 128KiB
          capacidade: 128KiB
          capacidades: synchronous internal write-back instruction
          configuração: level=1
     *-cache:2
          descrição: L2 cache
          ID físico: c
          slot: L2 Cache
          tamanho: 1MiB
          capacidade: 1MiB
          capacidades: synchronous internal write-back unified
          configuração: level=2
     *-cache:3
          descrição: L3 cache
          ID físico: d
          slot: L3 Cache
          tamanho: 6MiB
          capacidade: 6MiB
          capacidades: synchronous internal write-back unified
          configuração: level=3
     *-cpu
          descrição: CPU
          produto: Intel(R) Core(TM) i5-6600 CPU @ 3.30GHz
          fabricante: Intel Corp.
          ID físico: e
          informações do barramento: cpu@0
          versão: 6.94.3
          serial: To Be Filled By O.E.M.
          slot: CPUSocket
          tamanho: 3646MHz
          capacidade: 3900MHz
          largura: 64 bits
          clock: 100MHz
          capacidades: lm fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx pdpe1gb rdtscp x86-64 constant_tsc art arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc cpuid aperfmperf pni pclmulqdq dtes64 monitor ds_cpl vmx smx est tm2 ssse3 sdbg fma cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic movbe popcnt tsc_deadline_timer aes xsave avx f16c rdrand lahf_lm abm 3dnowprefetch cpuid_fault epb invpcid_single pti ssbd ibrs ibpb stibp tpr_shadow vnmi flexpriority ept vpid ept_ad fsgsbase tsc_adjust sgx bmi1 avx2 smep bmi2 erms invpcid mpx rdseed adx smap clflushopt intel_pt xsaveopt xsavec xgetbv1 xsaves dtherm ida arat pln pts hwp hwp_notify hwp_act_window hwp_epp md_clear flush_l1d arch_capabilities cpufreq
          configuração: cores=4 enabledcores=4 microcode=240 threads=4
     *-memory
          descrição: Memória do sistema
          ID físico: f
          slot: Placa do sistema ou placa-mãe
          tamanho: 8GiB
        *-bank:0
             descrição: DIMMProject-Id-Version: lshwReport-Msgid-Bugs-To: FULL NAME <EMAIL@ADDRESS>PO-Revision-Date: 2013-04-07 17:30+0000Last-Translator: Neliton Pereira Jr. <nelitonpjr@gmail.com>Language-Team: Brazilian Portuguese <pt_BR@li.org>MIME-Version: 1.0Content-Type: text/plain; charset=UTF-8Content-Transfer-Encoding: 8bitX-Launchpad-Export-Date: 2022-07-21 13:07+0000X-Generator: Launchpad (build 025a39fd866a641b6ae33074cda0d02a2c712d38) [vazio]
             ID físico: 0
             slot: ChannelA-DIMM0
        *-bank:1
             descrição: DIMM DDR4 Síncrono 2133 MHz (0,5 ns)
             produto: 9905702-137.A00G
             fabricante: Kingston
             ID físico: 1
             serial: 33112116
             slot: ChannelB-DIMM0
             tamanho: 8GiB
             largura: 64 bits
             clock: 2133MHz (0.5ns)
     *-pci
          descrição: Host bridge
          produto: Xeon E3-1200 v5/E3-1500 v5/6th Gen Core Processor Host Bridge/DRAM Registers
          fabricante: Intel Corporation
          ID físico: 100
          informações do barramento: pci@0000:00:00.0
          versão: 07
          largura: 32 bits
          clock: 33MHz
          configuração: driver=skl_uncore
          recursos: irq:0
        *-pci:0
             descrição: PCI bridge
             produto: 6th-10th Gen Core Processor PCIe Controller (x16)
             fabricante: Intel Corporation
             ID físico: 1
             informações do barramento: pci@0000:00:01.0
             versão: 07
             largura: 32 bits
             clock: 33MHz
             capacidades: pci pm msi pciexpress normal_decode bus_master cap_list
             configuração: driver=pcieport
             recursos: irq:121 porta de E/S:e000(tamanho=4096) memória:de000000-df0fffff porta de E/S:c0000000(tamanho=301989888)
           *-display
                descrição: VGA compatible controller
                produto: GM107 [GeForce GTX 750 Ti]
                fabricante: NVIDIA Corporation
                ID físico: 0
                informações do barramento: pci@0000:01:00.0
                nome lógico: /dev/fb0
                versão: a2
                largura: 64 bits
                clock: 33MHz
                capacidades: pm msi pciexpress vga_controller bus_master cap_list rom fb
                configuração: depth=32 driver=nouveau latency=0 resolution=1360,768
                recursos: irq:128 memória:de000000-deffffff memória:c0000000-cfffffff memória:d0000000-d1ffffff porta de E/S:e000(tamanho=128) memória:c0000-dffff
           *-multimedia
                descrição: Audio device
                produto: GM107 High Definition Audio Controller [GeForce 940MX]
                fabricante: NVIDIA Corporation
                ID físico: 0.1
                informações do barramento: pci@0000:01:00.1
                nome lógico: card1
                nome lógico: /dev/snd/controlC1
                nome lógico: /dev/snd/hwC1D0
                nome lógico: /dev/snd/pcmC1D10p
                nome lógico: /dev/snd/pcmC1D11p
                nome lógico: /dev/snd/pcmC1D12p
                nome lógico: /dev/snd/pcmC1D3p
                nome lógico: /dev/snd/pcmC1D7p
                nome lógico: /dev/snd/pcmC1D8p
                nome lógico: /dev/snd/pcmC1D9p
                versão: a1
                largura: 32 bits
                clock: 33MHz
                capacidades: pm msi pciexpress bus_master cap_list
                configuração: driver=snd_hda_intel latency=0
                recursos: irq:17 memória:df080000-df083fff
              *-input:0
                   produto: HDA NVidia HDMI/DP,pcm=8
                   ID físico: 0
                   nome lógico: input10
                   nome lógico: /dev/input/event10
              *-input:1
                   produto: HDA NVidia HDMI/DP,pcm=9
                   ID físico: 1
                   nome lógico: input11
                   nome lógico: /dev/input/event11
              *-input:2
                   produto: HDA NVidia HDMI/DP,pcm=10
                   ID físico: 2
                   nome lógico: input12
                   nome lógico: /dev/input/event12
              *-input:3
                   produto: HDA NVidia HDMI/DP,pcm=11
                   ID físico: 3
                   nome lógico: input13
                   nome lógico: /dev/input/event13
              *-input:4
                   produto: HDA NVidia HDMI/DP,pcm=12
                   ID físico: 4
                   nome lógico: input14
                   nome lógico: /dev/input/event14
              *-input:5
                   produto: HDA NVidia HDMI/DP,pcm=3
                   ID físico: 5
                   nome lógico: input8
                   nome lógico: /dev/input/event8
              *-input:6
                   produto: HDA NVidia HDMI/DP,pcm=7
                   ID físico: 6
                   nome lógico: input9
                   nome lógico: /dev/input/event9
        *-usb
             descrição: USB controller
             produto: 100 Series/C230 Series Chipset Family USB 3.0 xHCI Controller
             fabricante: Intel Corporation
             ID físico: 14
             informações do barramento: pci@0000:00:14.0
             versão: 31
             largura: 64 bits
             clock: 33MHz
             capacidades: pm msi xhci bus_master cap_list
             configuração: driver=xhci_hcd latency=0
             recursos: irq:125 memória:df210000-df21ffff
           *-usbhost:0
                produto: xHCI Host Controller
                fabricante: Linux 5.15.0-43-generic xhci-hcd
                ID físico: 0
                informações do barramento: usb@1
                nome lógico: usb1
                versão: 5.15
                capacidades: usb-2.00
                configuração: driver=hub slots=10 speed=480Mbit/s
              *-usb:0
                   descrição: Teclado
                   produto: SIGMACHIP USB Keyboard System Control
                   fabricante: SIGMACHIP
                   ID físico: 1
                   informações do barramento: usb@1:1
                   nome lógico: input3
                   nome lógico: /dev/input/event3
                   nome lógico: input3::capslock
                   nome lógico: input3::numlock
                   nome lógico: input3::scrolllock
                   nome lógico: input4
                   nome lógico: /dev/input/event4
                   nome lógico: input5
                   nome lógico: /dev/input/event5
                   versão: 1.10
                   capacidades: usb-1.10 usb
                   configuração: driver=usbhid maxpower=98mA speed=1Mbit/s
              *-usb:1
                   descrição: Mouse
                   produto: YSPRINGTECH USB OPTICAL MOUSE
                   fabricante: YSPRINGTECH
                   ID físico: 2
                   informações do barramento: usb@1:2
                   nome lógico: input6
                   nome lógico: /dev/input/event6
                   nome lógico: /dev/input/mouse0
                   versão: 0.00
                   capacidades: usb-2.00 usb
                   configuração: driver=usbhid maxpower=100mA speed=1Mbit/s
              *-usb:2
                   descrição: Dispositivo de interface humana
                   produto: Microntek              USB Joystick
                   fabricante: Microntek
                   ID físico: 7
                   informações do barramento: usb@1:7
                   nome lógico: input7
                   nome lógico: /dev/input/event7
                   nome lógico: /dev/input/js0
                   versão: 1.07
                   capacidades: usb-1.00 usb
                   configuração: driver=usbhid maxpower=500mA speed=1Mbit/s
           *-usbhost:1
                produto: xHCI Host Controller
                fabricante: Linux 5.15.0-43-generic xhci-hcd
                ID físico: 1
                informações do barramento: usb@2
                nome lógico: usb2
                versão: 5.15
                capacidades: usb-3.00
                configuração: driver=hub slots=4 speed=5000Mbit/s
        *-generic
             descrição: Signal processing controller
             produto: 100 Series/C230 Series Chipset Family Thermal Subsystem
             fabricante: Intel Corporation
             ID físico: 14.2
             informações do barramento: pci@0000:00:14.2
             versão: 31
             largura: 64 bits
             clock: 33MHz
             capacidades: pm msi cap_list
             configuração: driver=intel_pch_thermal latency=0
             recursos: irq:18 memória:df22e000-df22efff
        *-communication
             descrição: Communication controller
             produto: 100 Series/C230 Series Chipset Family MEI Controller #1
             fabricante: Intel Corporation
             ID físico: 16
             informações do barramento: pci@0000:00:16.0
             versão: 31
             largura: 64 bits
             clock: 33MHz
             capacidades: pm msi bus_master cap_list
             configuração: driver=mei_me latency=0
             recursos: irq:127 memória:df22d000-df22dfff
        *-sata
             descrição: SATA controller
             produto: Q170/Q150/B150/H170/H110/Z170/CM236 Chipset SATA Controller [AHCI Mode]
             fabricante: Intel Corporation
             ID físico: 17
             informações do barramento: pci@0000:00:17.0
             nome lógico: scsi1
             nome lógico: scsi3
             versão: 31
             largura: 32 bits
             clock: 66MHz
             capacidades: sata msi pm ahci_1.0 bus_master cap_list emulated
             configuração: driver=ahci latency=0
             recursos: irq:124 memória:df228000-df229fff memória:df22c000-df22c0ff porta de E/S:f050(tamanho=8) porta de E/S:f040(tamanho=4) porta de E/S:f020(tamanho=32) memória:df22b000-df22b7ff
           *-disk
                descrição: ATA Disk
                produto: SAMSUNG HD502HJ
                ID físico: 0
                informações do barramento: scsi@1:0.0.0
                nome lógico: /dev/sda
                versão: 0001
                serial: S2BWJ50ZC82118
                tamanho: 465GiB (500GB)
                capacidades: gpt-1.00 partitioned partitioned:gpt
                configuração: ansiversion=5 guid=7c44d40a-e4b5-4280-8a3c-df97067e8356 logicalsectorsize=512 sectorsize=512
              *-volume:0
                   descrição: BIOS Boot partition
                   fabricante: EFI
                   ID físico: 1
                   informações do barramento: scsi@1:0.0.0,1
                   nome lógico: /dev/sda1
                   serial: d0fa4516-e6ab-43b4-8895-bf39de69e01d
                   capacidade: 1023KiB
                   capacidades: nofs
              *-volume:1 DISPONÍVEL
                   descrição: Windows FAT volume
                   fabricante: mkfs.fat
                   ID físico: 2
                   informações do barramento: scsi@1:0.0.0,2
                   versão: FAT32
                   serial: 6cd5-b08a
                   tamanho: 510MiB
                   capacidade: 512MiB
                   capacidades: boot fat initialized
                   configuração: FATs=2 filesystem=fat name=EFI System Partition
              *-volume:2
                   descrição: volume EXT4
                   fabricante: Linux
                   ID físico: 3
                   informações do barramento: scsi@1:0.0.0,3
                   nome lógico: /dev/sda3
                   nome lógico: /
                   versão: 1.0
                   serial: d5c0757b-d045-4bc3-a1b9-eb40422c0f2a
                   tamanho: 465GiB
                   capacidades: journaled extended_attributes large_files huge_files dir_nlink recover 64bit extents ext4 ext2 initialized
                   configuração: created=2022-07-30 09:40:45 filesystem=ext4 lastmountpoint=/ modified=2022-07-30 11:19:05 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro mounted=2022-07-30 11:19:11 state=mounted
           *-cdrom
                descrição: DVD-RAM writer
                produto: DVDRAM GH22NS40
                fabricante: HL-DT-ST
                ID físico: 1
                informações do barramento: scsi@3:0.0.0
                nome lógico: /dev/cdrom
                nome lógico: /dev/sr0
                versão: NL02
                capacidades: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuração: ansiversion=5 status=nodisc
        *-pci:1
             descrição: PCI bridge
             produto: 100 Series/C230 Series Chipset Family PCI Express Root Port #5
             fabricante: Intel Corporation
             ID físico: 1c
             informações do barramento: pci@0000:00:1c.0
             versão: f1
             largura: 32 bits
             clock: 33MHz
             capacidades: pci pciexpress msi pm normal_decode bus_master cap_list
             configuração: driver=pcieport
             recursos: irq:122
        *-pci:2
             descrição: PCI bridge
             produto: 100 Series/C230 Series Chipset Family PCI Express Root Port #6
             fabricante: Intel Corporation
             ID físico: 1c.5
             informações do barramento: pci@0000:00:1c.5
             versão: f1
             largura: 32 bits
             clock: 33MHz
             capacidades: pci pciexpress msi pm normal_decode bus_master cap_list
             configuração: driver=pcieport
             recursos: irq:123 porta de E/S:d000(tamanho=4096) memória:df100000-df1fffff porta de E/S:d2100000(tamanho=1048576)
           *-network
                descrição: Ethernet interface
                produto: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
                fabricante: Realtek Semiconductor Co., Ltd.
                ID físico: 0
                informações do barramento: pci@0000:03:00.0
                nome lógico: enp3s0
                versão: 11
                serial: 70:85:c2:7e:db:41
                tamanho: 100Mbit/s
                capacidade: 1Gbit/s
                largura: 64 bits
                clock: 33MHz
                capacidades: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
                configuração: autonegotiation=on broadcast=yes driver=r8169 driverversion=5.15.0-43-generic duplex=full firmware=rtl8168g-2_0.0.1 02/06/13 ip=10.0.0.110 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
                recursos: irq:17 porta de E/S:d000(tamanho=256) memória:df100000-df100fff memória:d2100000-d2103fff
        *-isa
             descrição: ISA bridge
             produto: H110 Chipset LPC/eSPI Controller
             fabricante: Intel Corporation
             ID físico: 1f
             informações do barramento: pci@0000:00:1f.0
             versão: 31
             largura: 32 bits
             clock: 33MHz
             capacidades: isa bus_master
             configuração: latency=0
           *-pnp00:00
                produto: PnP device PNP0c02
                ID físico: 0
                capacidades: pnp
                configuração: driver=system
           *-pnp00:01
                produto: PnP device PNP0401
                ID físico: 1
                capacidades: pnp
                configuração: driver=parport_pc
           *-pnp00:02
                produto: PnP device PNP0501
                ID físico: 2
                capacidades: pnp
                configuração: driver=serial
           *-pnp00:03
                produto: PnP device PNP0c02
                ID físico: 3
                capacidades: pnp
                configuração: driver=system
           *-pnp00:04
                produto: PnP device PNP0c02
                ID físico: 4
                capacidades: pnp
                configuração: driver=system
           *-pnp00:05
                produto: PnP device PNP0b00
                ID físico: 5
                capacidades: pnp
                configuração: driver=rtc_cmos
           *-pnp00:06
                produto: PnP device INT3f0d
                ID físico: 6
                capacidades: pnp
                configuração: driver=system
           *-pnp00:07
                produto: PnP device PNP0c02
                ID físico: 7
                capacidades: pnp
                configuração: driver=system
           *-pnp00:08
                produto: PnP device PNP0c02
                ID físico: 8
                capacidades: pnp
                configuração: driver=system
           *-pnp00:09
                produto: PnP device PNP0c02
                ID físico: 9
                capacidades: pnp
                configuração: driver=system
           *-pnp00:0a
                produto: PnP device PNP0c02
                ID físico: a
                capacidades: pnp
                configuração: driver=system
        *-memory DISPONÍVEL
             descrição: Memory controller
             produto: 100 Series/C230 Series Chipset Family Power Management Controller
             fabricante: Intel Corporation
             ID físico: 1f.2
             informações do barramento: pci@0000:00:1f.2
             versão: 31
             largura: 32 bits
             clock: 33MHz (30.3ns)
             configuração: latency=0
             recursos: memória:df224000-df227fff
        *-multimedia
             descrição: Audio device
             produto: 100 Series/C230 Series Chipset Family HD Audio Controller
             fabricante: Intel Corporation
             ID físico: 1f.3
             informações do barramento: pci@0000:00:1f.3
             nome lógico: card0
             nome lógico: /dev/snd/controlC0
             nome lógico: /dev/snd/hwC0D0
             nome lógico: /dev/snd/pcmC0D0c
             nome lógico: /dev/snd/pcmC0D0p
             nome lógico: /dev/snd/pcmC0D2c
             versão: 31
             largura: 64 bits
             clock: 33MHz
             capacidades: pm msi bus_master cap_list
             configuração: driver=snd_hda_intel latency=32
             recursos: irq:129 memória:df220000-df223fff memória:df200000-df20ffff
           *-input:0
                produto: HDA Intel PCH Front Mic
                ID físico: 0
                nome lógico: input15
                nome lógico: /dev/input/event15
           *-input:1
                produto: HDA Intel PCH Rear Mic
                ID físico: 1
                nome lógico: input16
                nome lógico: /dev/input/event16
           *-input:2
                produto: HDA Intel PCH Line
                ID físico: 2
                nome lógico: input17
                nome lógico: /dev/input/event17
           *-input:3
                produto: HDA Intel PCH Line Out
                ID físico: 3
                nome lógico: input18
                nome lógico: /dev/input/event18
           *-input:4
                produto: HDA Intel PCH Front Headphone
                ID físico: 4
                nome lógico: input19
                nome lógico: /dev/input/event19
        *-serial
             descrição: SMBus
             produto: 100 Series/C230 Series Chipset Family SMBus
             fabricante: Intel Corporation
             ID físico: 1f.4
             informações do barramento: pci@0000:00:1f.4
             versão: 31
             largura: 64 bits
             clock: 33MHz
             configuração: driver=i801_smbus latency=0
             recursos: irq:16 memória:df22a000-df22a0ff porta de E/S:f000(tamanho=32)
  *-input:0
       produto: Sleep Button
       ID físico: 1
       nome lógico: input0
       nome lógico: /dev/input/event0
       capacidades: platform
  *-input:1
       produto: Power Button
       ID físico: 2
       nome lógico: input1
       nome lógico: /dev/input/event1
       capacidades: platform
  *-input:2
       produto: Power Button
       ID físico: 3
       nome lógico: input2
       nome lógico: /dev/input/event2
       capacidades: platform
```

---

### Post by mIk3_08 on 2022-07-31
> **gatajapa said:**
> I installed Wine through the Ubuntu store and when I right-click on the Windows installer and choose "Open with another application" I don't find it in the list. At the moment I am trying to install the program called Yumi. Remembering that I'm using the latest version of Ubuntu available on the site to download.
What kind of wine did you install from Ubuntu Store?  For more information about wine. Please [Click Here]("https://help.ubuntu.com/community/Wine"). Regards and cheers.

---

### Post by gatajapa on 2022-07-31
> **mIk3_08 said:**
> What kind of wine did you install from Ubuntu Store?  For more information about wine. Please [Click Here]("https://help.ubuntu.com/community/Wine"). Regards and cheers.

I installed Wine version 6.0.3~repack-1. What I want to know, friend, is if it is possible to install a Windows program with Wine and run it without having to type a command in the terminal.

---

### Post by mIk3_08 on 2022-08-01
> **gatajapa said:**
> I installed Wine version 6.0.3~repack-1. What I  want to know, friend, is if it is possible to install a Windows program  with Wine and run it without having to type a command in the  terminal. Sorry friend, I don't use wine and I haven't use wine  ever since. I prefer to use VM if you wanted to install and run MS  Windows program on Linux Operating System. Regards and Cheers.
For more information about Virtual Machine. Please Click Here
[Link 1]("https://en.wikipedia.org/wiki/Virtual_machine")
[Link 2]("https://www.parallels.com/")
[Link 3]("https://help.ubuntu.com/community/VirtualMachines")
[Link 4]("https://help.ubuntu.com/community/WindowsXPUnderQemuHowTo")

---

### Post by gatajapa on 2022-08-01
Anyway, friend, I appreciate you trying to help me, okay.

---

### Post by deadflowr on 2022-08-01
> **gatajapa said:**
> Hello friends! Please welcome me as I am the newest Linux user who has migrated from Windows. I installed Ubuntu today on my machine because I was mad at Microsoft for a few reasons.

So, friends, as my first question is that I installed Wine through the Ubuntu store and when I right-click on the Windows installer and choose "Open with another application" I don't find it in the list. At the moment I am trying to install the program called Yumi. Remembering that I'm using the latest version of Ubuntu available on the site to download.

So, any help?

Wine in Ubuntu does not ship with the default desktop launcher enabled in the usual location.
But it does ship with it, albeit in a rather obscure documentation folder.
to enable simply copy it like so
```
sudo cp /usr/share/doc/wine/examples/wine.desktop /usr/share/applications/
```
That should give you the Wine Program Loader option in the right click other applications; might need to select for the view all applications option.
See if that helps.

Whether or not your program can even run in wine is another story.

---

### Post by gatajapa on 2022-08-01
Thanks friend! Now Wine has appeared in the list of programs to open with the Windows executable.

But also, I had already discovered another solution that was to use Wine together with PlayOnLinux because with this second one, I don't need to use the terminal to install a Windows program.

---

### Post by TheFu on 2022-08-01
> **gatajapa said:**
> ... At the moment I am trying to install the program called Yumi.   ....

So, the Yumi program I know is a Windows tool to "burn" an ISO to a flash drive. This is typically use to create a bootable Linux installation or "Trial" environment.  So, this program in specific really shouldn't be used under Linux.  There are lots of programs which accomplish moving bits from A--->B on Linux already. I'm talking about native applications, which will always interact with hardware better than WINE does.

If you don't mind bloat, check out Etcher.  But there are a few other tools like Ventoy, mkusb, dd, ddrescue, or even 'cp' can be used for this purpose.  I use 'cp' myself, since all the others can be a bit more complex and I can type 
```
sudo cp /path/to/ubuntu.iso  /dev/sdZ 
```
pretty fast.

Etcher is very popular and easy to use, though it is about 20x larger than needed.

As for WINE and using WINE, in my experience, WINE is vastly oversold. It just doesn't work all that well for any of the programs I've tried.  There are always tweaks required - look up winetricks - to learn more.  It was able to get a Windows financial program mostly working (the main 80% of functions worked) about a decade ago. The next version of that program broke everything again. After spending a few weeks trying to get the new version working, I decided that my time was better spent using the program, not trying to get it working.  To that end, I installed it into a virtual machine that was already running a copy of Windows.  All the features work. No compromise, except the bloat required to have Windows.  I'm using the same version from 2013 today, on the same OS (yes, it isn't supported anymore), but it works and it isn't used for anything other than that single program and annual tax tools, drastically limiting the malware/AV risks for the system.

I understand that using tools that you've used on some other OS is a comfort, but change is the name here.  

Windows and Linux/Unix have different core philosophies. 

Best to learn to embrace the Linux philosophy sooner than later. It will drastically reduce frustration.  
The Unix Philosophy (5 tenants): [https://www.linuxfordevices.com/tutorials/linux/unix-philosophy](https://www.linuxfordevices.com/tutorials/linux/unix-philosophy)
Remember that Linux isn't Windows. [http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)
Learn to think the Unix way: [https://blog.jdpfu.com/2012/02/15/beginning-linux-thought-shift-needed](https://blog.jdpfu.com/2012/02/15/beginning-linux-thought-shift-needed)

---

### Post by gatajapa on 2022-08-01
Okay friend, I already solved my two problems.

> **TheFu said:**
> If you don't mind bloat, check out Etcher.  But there are a few other tools like Ventoy, mkusb, dd, ddrescue, or even 'cp' can be used for this purpose.

I used Ventoy to create the multiboot pendrive.

> **TheFu said:**
> As for WINE and using WINE, in my experience, WINE is vastly oversold. It just doesn't work all that well for any of the programs I've tried. There are always tweaks required - look up winetricks - to learn more. It was able to get a Windows financial program mostly working (the main 80% of functions worked) about a decade ago. The next version of that program broke everything again. After spending a few weeks trying to get the new version working, I decided that my time was better spent using the program, not trying to get it working. To that end, I installed it into a virtual machine that was already running a copy of Windows. All the features work. No compromise, except the bloat required to have Windows. I'm using the same version from 2013 today, on the same OS (yes, it isn't supported anymore), but it works and it isn't used for anything other than that single program and annual tax tools, drastically limiting the malware/AV risks for the system.

And I did what @deadflowr said. I used this command:

```
sudo cp /usr/share/doc/wine/examples/wine.desktop /usr/share/applications/
```

I thank everyone for all the help!

---

### Post by TheFu on 2022-08-01
> **gatajapa said:**
> Okay friend, I already solved my two problems.
 

If it is SOLVED, please, please, please use the "thread tools" button near the top of the page to mark this thread as solved solved so people looking for answers to similar problems can find it easily and people like me don't waste time. 

I knew it was solved.  My post was more about "why not" and to try to reset expectations for WINE.  I think that saying what to type for some issues is easy, but the "why" (or why not) is at least as important.

---

