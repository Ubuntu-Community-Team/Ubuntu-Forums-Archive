---
title: "Guild Wars doesnt load."
date: 2008-04-26
forum: Wine
---

### Post by Zatarg on 2008-04-26
Im using 8.04 Hardy & wine version 0.9.59

When started the "Connecting to ArenaNet" updating frame appears, but once it has reached 100%, the computer freezes. The guildwars window appears, but the updating frame is frozen on top of it and the rest of the window is blank.

The mouse and keyboard don't respond, and a minute or two later the app quits and i get back to the desktop.

Tried a few things to get it to load...
```
steven@steven-laptop:~$ wine "C:\Program Files\Guild Wars\Gw.exe" -windowed
ALSA lib pcm_dmix.c:874:(snd_pcm_dmix_open) unable to open slave
fixme:win:EnumDisplayDevicesW ((null),0,0x32f04c,0x00000000), stub!
fixme:d3d:IWineD3DImpl_CheckDeviceMultiSampleType Quality levels unsupported at present
fixme:d3d:IWineD3DResourceImpl_SetPriority (0x21bf9b8) : stub
fixme:d3d:IWineD3DResourceImpl_SetPriority (0x277f3b0) : stub
fixme:d3d:IWineD3DResourceImpl_SetPriority (0x277f9c0) : stub
fixme:d3d:IWineD3DResourceImpl_SetPriority (0x249f838) : stub
fixme:d3d:IWineD3DResourceImpl_SetPriority (0x21bf858) : stub
fixme:d3d:IWineD3DResourceImpl_SetPriority (0x277f3b0) : stub
Wars\Gw.exe: brw_curbe.c:87: calculate_curbe_offsets: Assertion `total_regs <= 32' failed.
err:ntdll:RtlpWaitForCriticalSection section 0x7e6108a0 "x11drv_main.c: X11DRV_CritSection" wait timed out in thread 002c, blocked by 0019, retrying (60 sec)
err:seh:raise_exception Exception frame is not in stack limits => unable to dispatch exception.

```

```
steven@steven-laptop:~$ wine "C:\Program Files\Guild Wars\Gw.exe" -windowed dx8 dsound
ALSA lib pcm_dmix.c:874:(snd_pcm_dmix_open) unable to open slave
fixme:win:EnumDisplayDevicesW ((null),0,0x32f04c,0x00000000), stub!
fixme:d3d:IWineD3DImpl_CheckDeviceMultiSampleType Quality levels unsupported at present
fixme:d3d:IWineD3DResourceImpl_SetPriority (0x249fa20) : stub
fixme:d3d:IWineD3DResourceImpl_SetPriority (0x21bf978) : stub
fixme:d3d:IWineD3DResourceImpl_SetPriority (0x277f3b0) : stub
fixme:d3d:IWineD3DResourceImpl_SetPriority (0x21bf840) : stub
fixme:d3d:IWineD3DResourceImpl_SetPriority (0x249f8c0) : stub
fixme:d3d:IWineD3DResourceImpl_SetPriority (0x277f3b0) : stub
Wars\Gw.exe: brw_curbe.c:87: calculate_curbe_offsets: Assertion `total_regs <= 32' failed.
err:ntdll:RtlpWaitForCriticalSection section 0x7e6258a0 "x11drv_main.c: X11DRV_CritSection" wait timed out in thread 002c, blocked by 0019, retrying (60 sec)
err:seh:raise_exception Exception frame is not in stack limits => unable to dispatch exception.

```

With this one, the screen behind goes blue but its still frozen etc.
```
steven@steven-laptop:~$ wine explorer /desktop=MyDesktopName,1024x768 "C:\Program Files\Guild Wars\Gw.exe"
ALSA lib pcm_dmix.c:874:(snd_pcm_dmix_open) unable to open slave
fixme:win:EnumDisplayDevicesW ((null),0,0x33f04c,0x00000000), stub!
fixme:d3d:IWineD3DImpl_CheckDeviceMultiSampleType Quality levels unsupported at present
fixme:d3d:IWineD3DDeviceImpl_EvictManagedResources (0x13a580) : stub
fixme:d3d:IWineD3DDeviceImpl_EvictManagedResources (0x13a580) : stub
fixme:d3d:IWineD3DDeviceImpl_EvictManagedResources (0x13a580) : stub
fixme:d3d:IWineD3DDeviceImpl_EvictManagedResources (0x13a580) : stub
fixme:d3d:IWineD3DDeviceImpl_EvictManagedResources (0x13a580) : stub
fixme:d3d:IWineD3DDeviceImpl_EvictManagedResources (0x13a580) : stub
fixme:d3d:IWineD3DDeviceImpl_EvictManagedResources (0x13a580) : stub
fixme:d3d:IWineD3DDeviceImpl_EvictManagedResources (0x13a580) : stub
fixme:d3d:IWineD3DDeviceImpl_EvictManagedResources (0x13a580) : stub
fixme:d3d:IWineD3DDeviceImpl_EvictManagedResources (0x13a580) : stub
fixme:d3d:IWineD3DDeviceImpl_EvictManagedResources (0x13a580) : stub
fixme:d3d:IWineD3DDeviceImpl_EvictManagedResources (0x13a580) : stub
fixme:d3d:IWineD3DDeviceImpl_EvictManagedResources (0x13a580) : stub
fixme:d3d:IWineD3DDeviceImpl_EvictManagedResources (0x13a580) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0x13a580) : stub
Wars\Gw.exe: brw_curbe.c:87: calculate_curbe_offsets: Assertion `total_regs <= 32' failed.
err:ntdll:RtlpWaitForCriticalSection section 0x7e61c8a0 "x11drv_main.c: X11DRV_CritSection" wait timed out in thread 002c, blocked by 001c, retrying (60 sec)
err:seh:raise_exception Exception frame is not in stack limits => unable to dispatch exception.

```

I dont know what hardware is relevant, so i've just dumped the output for lshw here.

```
steven-laptop             
    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 2017MiB
     *-cpu
          product: Intel(R) Core(TM)2 Duo CPU     T7300  @ 2.00GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          version: 6.15.10
          serial: 0000-06FA-0000-0000-0000-0000
          size: 2001MHz
          capacity: 2001MHz
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe x86-64 constant_tsc arch_perfmon pebs bts pni monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr lahf_lm ida cpufreq
          configuration: id=1
        *-logicalcpu:0
             description: Logical CPU
             physical id: 1.1
             width: 64 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 1.2
             width: 64 bits
             capabilities: logical
     *-pci
          description: Host bridge
          product: Mobile PM965/GM965/GL960 Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel module=intel_agp
        *-display:0 UNCLAIMED
             description: VGA compatible controller
             product: Mobile GM965/GL960 Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 03
             width: 64 bits
             clock: 33MHz
             capabilities: vga_controller bus_master cap_list
             configuration: latency=0
        *-display:1 UNCLAIMED
             description: Display controller
             product: Mobile GM965/GL960 Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 03
             width: 64 bits
             clock: 33MHz
             capabilities: cap_list
             configuration: latency=0
        *-usb:0
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:1
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #5
             vendor: Intel Corporation
             physical id: 1a.1
             bus info: pci@0000:00:1a.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:2
             description: USB Controller
             product: 82801H (ICH8 Family) USB2 EHCI Controller #2
             vendor: Intel Corporation
             physical id: 1a.7
             bus info: pci@0000:00:1a.7
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0 module=ehci_hcd
        *-multimedia
             description: Audio device
             product: 82801H (ICH8 Family) HD Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 03
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=HDA Intel latency=0 module=snd_hda_intel
        *-pci:0
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
        *-pci:1
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
        *-pci:2
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 3
             vendor: Intel Corporation
             physical id: 1c.2
             bus info: pci@0000:00:1c.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
           *-network
                description: Ethernet interface
                product: NetLink BCM5787M Gigabit Ethernet PCI Express
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:05:00.0
                logical name: eth0
                version: 02
                serial: 00:16:d4:d9:f7:7f
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical
                configuration: broadcast=yes driver=tg3 driverversion=3.86 firmware=5787m-v3.22 latency=0 module=tg3 multicast=yes
        *-pci:3
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 4
             vendor: Intel Corporation
             physical id: 1c.3
             bus info: pci@0000:00:1c.3
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
           *-network
                description: Wireless interface
                product: PRO/Wireless 3945ABG Network Connection
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:06:00.0
                logical name: wmaster0
                version: 02
                serial: 00:19:d2:65:ee:30
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list logical ethernet physical wireless
                configuration: broadcast=yes driver=iwl3945 ip=192.168.1.65 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11g
        *-usb:3
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:4
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:5
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:6
             description: USB Controller
             product: 82801H (ICH8 Family) USB2 EHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0 module=ehci_hcd
        *-pci:4
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: f3
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
           *-firewire
                description: FireWire (IEEE 1394)
                product: R5C832 IEEE 1394 Controller
                vendor: Ricoh Co Ltd
                physical id: 0
                bus info: pci@0000:07:00.0
                version: 05
                width: 32 bits
                clock: 33MHz
                capabilities: ohci bus_master cap_list
                configuration: driver=ohci1394 latency=64 maxlatency=4 mingnt=2 module=ohci1394
           *-system:0
                description: SD Host controller
                product: R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter
                vendor: Ricoh Co Ltd
                physical id: 0.1
                bus info: pci@0000:07:00.1
                version: 22
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=sdhci latency=64 module=sdhci
           *-system:1
                description: System peripheral
                product: R5C592 Memory Stick Bus Host Adapter
                vendor: Ricoh Co Ltd
                physical id: 0.2
                bus info: pci@0000:07:00.2
                version: 12
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=ricoh-mmc latency=0 module=ricoh_mmc
           *-system:2 UNCLAIMED
                description: System peripheral
                product: xD-Picture Card Controller
                vendor: Ricoh Co Ltd
                physical id: 0.3
                bus info: pci@0000:07:00.3
                version: 12
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: latency=0
           *-generic UNCLAIMED
                product: Illegal Vendor ID
                vendor: Illegal Vendor ID
                physical id: 0.4
                bus info: pci@0000:07:00.4
                version: ff
                width: 32 bits
                clock: 66MHz
                capabilities: bus_master vga_palette cap_list
                configuration: latency=255 maxlatency=255 mingnt=255
        *-isa
             description: ISA bridge
             product: 82801HEM (ICH8M) LPC Interface Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master
             configuration: driver=ata_piix latency=0 module=ata_piix
        *-storage
             description: SATA controller
             product: 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 03
             width: 32 bits
             clock: 66MHz
             capabilities: storage ahci_1.0 bus_master cap_list
             configuration: driver=ahci latency=0 module=ahci
        *-serial UNCLAIMED
             description: SMBus
             product: 82801H (ICH8 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 03
             width: 32 bits
             clock: 33MHz
             configuration: latency=0

```

Any ideas?

---

### Post by Pr0zAck on 2008-04-27
I am having the same problem when I try and launch Guild Wars with 8.04 and Wine 0.9.59.

This command helped me solve a memory error that was showing up for me:
 sudo sysctl -w vm.mmap_min_addr=0

But I still am getting 
ALSA lib pcm_dmix.c:874:(snd_pcm_dmix_open) unable to open slave

Guild Wars will just go to a black screen and then exit.

Anyone have a solution to this

Thanks

---

### Post by Gunman1982 on 2008-04-30
> **Pr0zAck said:**
> 
But I still am getting 
ALSA lib pcm_dmix.c:874:(snd_pcm_dmix_open) unable to open slave

Close all other programs who access the soundcard. This command tells you which programs are using the soundcard:

lsof | grep snd

---

### Post by Pr0zAck on 2008-04-30
so i just installed version 0.9.59 of WINE and the sound error is gone but now a guild wars window opens and says my video card is not compatible or something along those lines.

I am using a radeon 9800 pro and the drivers are installed for it.

---

### Post by Pr0zAck on 2008-05-01
I am just going to dual boot with XP so i can play all my games on Windows. Problem solved.

---

### Post by S0VERE1GN on 2008-05-18
grrrr f*ck windows..... 

there HAS to be a way to make Guild wars work on wine on hardy 

FORUM TECH?! SOMEBODY?!?! there's a lot of us that need your halp!

---

### Post by Gunman1982 on 2008-05-18
Which problem do you have? Refering to winehq's appdb its working fine for many people.

---

### Post by S0VERE1GN on 2008-05-18
I seem to be having the recurring lights problem, or so it is called, where guild wars starts up , the cursor changes, and then it closes right after.  I used the fix as found in this thread [http://ubuntuforums.org/showthread.php?t=283122&highlight=Guild+Wars](http://ubuntuforums.org/showthread.php?t=283122&highlight=Guild+Wars)
but still no dice.... i've seen a few other people with the same problem.


i get this: 

fixme:win:EnumDisplayDevicesW ((null),0,0x32f034,0x00000000), stub!
err:d3d:WineD3D_ChoosePixelFormat Can't find a suitable iPixelFormat
fixme:d3d:IWineD3DDeviceImpl_SetDialogBoxMode (0x1330a8) Dialogs cannot be disabled yet
fixme:d3d:IWineD3DResourceImpl_SetPriority (0x22005b0) : stub
fixme:d3d:IWineD3DResourceImpl_SetPriority (0x2200aa8) : stub
fixme:d3d:IWineD3DResourceImpl_SetPriority (0x2200fa0) : stub
err:d3d:WineD3D_ChoosePixelFormat Can't find a suitable iPixelFormat
fixme:d3d:IWineD3DDeviceImpl_SetDialogBoxMode (0x1330a8) Dialogs cannot be disabled yet
fixme:d3d:IWineD3DResourceImpl_SetPriority (0x2510050) : stub
fixme:d3d:IWineD3DResourceImpl_SetPriority (0x147900) : stub
fixme:d3d:IWineD3DResourceImpl_SetPriority (0x2820050) : stub
Mesa 7.0.3-rc2 implementation error: i915_program_error: Exceeded max temporary reg
Please report at bugzilla.freedesktop.org
DRM_I830_CMDBUFFER: -22


if i open it through the terminal, and then guild wars closes again.

---

### Post by mesartwell on 2008-09-26
I installed Guild Wars under Wine 1.0 and I have the Intel 965 graphics chipset.  Whenever I load Guild Wars I get the same result: Computer locks up after running the Arena Net updater with only the GW cursor showing up. Ultimately I have to do a hard shutdown. Any suggestions?

---

### Post by Torgas Prim on 2008-09-30
From my several installs of Ubuntu to get Guild Wars working properly, I can tell you one thing, when GW acts like that it is video related...as in video card or drivers.
Most times it is an ATI card causing this.
If your GW shortcut is already on your desktop, edit the launcher and add these switches:
**-dx8 -noshaders -dsound**

If it loads properly, you are good to go.

Personally, replace any ATI product with an nVidia product, they just work.

---

### Post by MiscMau on 2008-09-30
Hey :)

I installed Ubuntu 8.04 Hardy Heron a few day ago - first time I'm trying a Linux based OS, and so far it seems to work very nicely. However, the only Windows-dependent program I'd like to run is Guild Wars, hence I installed Wine and tried running GW, and that is now causing me endless trouble. 

It connects fine to Anet's server, but the fog/mist on the login screen is moving very slowly and laggy. On the charaacter selection screen all my characters' armor have a shiny metallic effect, but the faces seem normal. Upon loading a character, the load screen runs fine, albeit the sound does make a few small loops once in a while, but as soon as it reaches 100%, GW closes, and I get an error report a mile long where it repeats the same things over and over, namely:

OR
fixme:d3d:set_tex_op Unhandled texture operation WINED3DTOP_MODULATEALPHA_ADDCOLOR
fixme:d3d:set_tex_op Unhandled texture operation WINED3DTOP_MODULATEALPHA_ADDCOLOR
fixme:d3d:set_tex_op Unhandled texture operation WINED3DTOP_MODULATEALPHA_ADDCOL

and 

OR
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0x13cf90) : stub
fixme:d3d:set_tex_op Unhandled texture operation WINED3DTOP_ADDSMOOTH
fixme:d3d:set_tex_op Unhandled texture operation WINED3DTOP_MODULATEALPHA_ADDCOL

and 

fixme:d3d:IWineD3DDeviceImpl_EvictManagedResources (0x13cf90) : stub
fixme:d3d:IWineD3DDeviceImpl_EvictManagedResources (0x13cf90) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0x13cf90) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0x13cf90) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0x13cf90) : stub
err:d3d:WineD3D_ChoosePixelFormat Can't find a suitable iPixelFormat
fixme:d3d:IWineD3DDeviceImpl_EvictManagedResources (0x13cf90) : stub
fixme:d3d:IWineD3DDeviceImpl_EvictManagedResources (0x13cf90) : stub
fixme:d3d:IWineD3DDeviceImpl_EvictManagedResources (0x13cf90) : stub
fixme:d3d:IWineD3DDeviceImpl_EvictManagedResources (0x13cf90) : stub
fixme:d3d:IWineD3DDeviceImpl_EvictManagedResources (0x13cf90) : stub
fixme:d3d:IWineD3DDeviceImpl_EvictManagedResources (0x13cf90) : stub
fixme:d3d:IWineD3DDeviceImpl_EvictManagedResources (0x13cf90) : stub
fixme:d3d:IWineD3DDeviceImpl_EvictManagedResources (0x13cf90) : stub
fixme:d3d:IWineD3DDeviceImpl_EvictManagedResources (0x13cf90) : stub
fixme:d3d:IWineD3DDeviceImpl_EvictManagedResources (0x13cf90) : stub
fixme:d3d:IWineD3DDeviceImpl_EvictManagedResources (0x13cf90) : stub
fixme:d3d:IWineD3DDeviceImpl_EvictManagedResources (0x13cf90) : stub
fixme:d3d:IWineD3DDeviceImpl_EvictManagedResources (0x13cf90) : stub
fixme:d3d:IWineD3DDeviceImpl_EvictManagedResources (0x13cf90) : stub
fixme:d3d:IWineD3DDeviceImpl_EvictManagedResources (0x13cf90) : stub
fixme:d3d:IWineD3DDeviceImpl_EvictManagedResources (0x13cf90) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0x13cf90) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0x13cf90) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0x13cf90) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0x13cf90) : stub
Segmentation fault

I run Gw.exe from the Terminal with -dx8 and -noshaders added after the path. Wine is ver. 1.0, set to run as Win98, and the OS is 8.04 Hardy. Computer is an Acer Travelmate 2410 laptop with Intel mobile 910GML onboard video card - I know it's not the most fancy of computers, but it ran GW flawlessly in Windows XP. In the Guild Wars options screen all graphical settings have been turned off or set to low, but it seems that no matter what I do, it still crashes upon finishing loading. 

My guess is that it's some sort of shader/graphical issue that's causing the crash, as my characters' armor look so shiny and metallic and because it crashes right after loading is complete, i.e. when it's supposed to actually start rendering things. I read that others have been having similar problems with ATI cards and that enabling OpenGL instead of fglrx, but I'm not certain how or if that will affect an Intel onboard card, plus I'm not even certain if my Intel onboard card can run in OpenGL or, if it does, how I enable it. 

Sorry for such a long and probably bothersome post, but any suggestions are much appreciated. If more information on specs, settings etc are needed, I shall try to provide them  if possible. 

Thank you in advance.

-Mia

---

