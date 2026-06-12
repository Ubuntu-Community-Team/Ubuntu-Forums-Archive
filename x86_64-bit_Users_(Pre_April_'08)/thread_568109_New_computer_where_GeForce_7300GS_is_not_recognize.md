---
title: "New computer where GeForce 7300GS is not recognized"
date: 2007-10-05
forum: x86 64-bit Users (Pre April '08)
---

### Post by sweRocker on 2007-10-05
[B]Hi, 

Well, I just installed Ubuntu 7.04 on my new computer with the following spec.:[/B]

AMD Athlon(tm) 64 X2 Dual Core Processor 4200+ (2.21 Ghz)
MSI K9N6SGM-V, nForce405+ GeForce 6100, Socket -AM2, m-ATX, DDR2, LAN, PCI-Ex8
2047 MB DDR-SDRAM
Gainward GeForce 7300GS 256MB DDR2, PCI-Express, "BP7300GS-256-TV-DVI"
(...)

**Everything is working perfectly, except for the graphic card wich cannot be detected. I tried using the lspci command and got the result:**

00:00.0 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a1)
00:01.0 ISA bridge: nVidia Corporation MCP61 LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP61 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3)
00:02.1 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3)
00:04.0 PCI bridge: nVidia Corporation MCP61 PCI bridge (rev a1)
00:05.0 Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP61 IDE (rev a2)
00:07.0 Bridge: nVidia Corporation MCP61 Ethernet (rev a2)
00:08.0 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:09.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0d.0 VGA compatible controller: nVidia Corporation GeForce 6100 nForce 405 (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control

```
**Running the command lshw gives all the hardware. Intresting is the PCI slots:**

     *-pci:0
          description: PCI bridge
          product: MCP61 PCI bridge
          vendor: nVidia Corporation
          physical id: 4
          bus info: pci@00:04.0
          version: a1
          width: 32 bits
          clock: 66MHz
          capabilities: pci subtractive_decode bus_master cap_list
     *-multimedia
          description: Audio device
          product: MCP61 High Definition Audio
          vendor: nVidia Corporation
          physical id: 5
          bus info: pci@00:05.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: bus_master cap_list
          configuration: driver=HDA Intel latency=0 maxlatency=5 mingnt=2
          resources: iomemory:dfff4000-dfff7fff irq:22
     *-ide:0
          description: IDE interface
          product: MCP61 IDE
          vendor: nVidia Corporation
          physical id: 6
          bus info: pci@00:06.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: ide bus_master cap_list
          configuration: driver=AMD_IDE latency=0 maxlatency=1 mingnt=3
          resources: iomemory:1f0-1f7 iomemory:3f0-3ef iomemory:170-177 iomemory:370-36f ioport:ffa0-ffaf
        *-ide
             description: IDE Channel 0
             physical id: 0
             bus info: ide@0
             logical name: ide0
             clock: 66MHz
           *-cdrom
                product: HL-DT-ST DVDRAM GSA-H44N
                physical id: 0
                bus info: ide@0.0
                logical name: /dev/hda
                capabilities: packet
     *-bridge
          description: Ethernet interface
          product: MCP61 Ethernet
          vendor: nVidia Corporation
          physical id: 7
          bus info: pci@00:07.0
          logical name: eth0
          version: a2
          serial: 00:19:db:d7:ca:c4
          width: 32 bits
          clock: 66MHz
          capabilities: bridge bus_master cap_list ethernet physical
          configuration: broadcast=yes driver=forcedeth driverversion=0.59 ip=130.243.217.114 latency=0 maxlatency=20 mingnt=1 multicast=yes
          resources: iomemory:dfff9000-dfff9fff ioport:e480-e487 irq:22
     *-ide:1
          description: IDE interface
          product: MCP61 SATA Controller
          vendor: nVidia Corporation
          physical id: 8
          bus info: pci@00:08.0
          logical name: scsi1
          logical name: scsi2
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: ide bus_master cap_list scsi-host
          configuration: driver=sata_nv latency=0 maxlatency=1 mingnt=3
          resources: ioport:e400-e407 ioport:e080-e083 ioport:e000-e007 ioport:dc00-dc03 ioport:d880-d88f iomemory:dfff8000-dfff8fff irq:20
     *-pci:1
          description: PCI bridge
          product: MCP61 PCI Express bridge
          vendor: nVidia Corporation
          physical id: 9
          bus info: pci@00:09.0
          version: a2
          width: 32 bits
          clock: 33MHz
          capabilities: pci normal_decode bus_master cap_list
          configuration: driver=pcieport-driver

```

[B]I did not assemble the computer myself, the vendor did. 

How shall I continue? Can it be a hardware error, a software error or some BIOS setting that has been done incorrectly?

Also, the vendor sent me a note with something called a PC report, where the graphics card is mentioned under "<Video System> / Adapter:", so i guess the card was responding before shipping.

Thank you for reading! Help appreciated![/B]

---

### Post by Kilz on 2007-10-05
> **sweRocker said:**
> [B]Hi, 

Well, I just installed Ubuntu 7.04 on my new computer with the following spec.:[/B]

AMD Athlon(tm) 64 X2 Dual Core Processor 4200+ (2.21 Ghz)
MSI K9N6SGM-V, nForce405+ GeForce 6100, Socket -AM2, m-ATX, DDR2, LAN, PCI-Ex8
2047 MB DDR-SDRAM
Gainward GeForce 7300GS 256MB DDR2, PCI-Express, "BP7300GS-256-TV-DVI"
(...)

**Everything is working perfectly, except for the graphic card wich cannot be detected. I tried using the lspci command and got the result:**

00:00.0 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a1)
00:01.0 ISA bridge: nVidia Corporation MCP61 LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP61 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3)
00:02.1 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3)
00:04.0 PCI bridge: nVidia Corporation MCP61 PCI bridge (rev a1)
00:05.0 Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP61 IDE (rev a2)
00:07.0 Bridge: nVidia Corporation MCP61 Ethernet (rev a2)
00:08.0 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:09.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0d.0 VGA compatible controller: nVidia Corporation GeForce 6100 nForce 405 (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control

```
**Running the command lshw gives all the hardware. Intresting is the PCI slots:**

     *-pci:0
          description: PCI bridge
          product: MCP61 PCI bridge
          vendor: nVidia Corporation
          physical id: 4
          bus info: pci@00:04.0
          version: a1
          width: 32 bits
          clock: 66MHz
          capabilities: pci subtractive_decode bus_master cap_list
     *-multimedia
          description: Audio device
          product: MCP61 High Definition Audio
          vendor: nVidia Corporation
          physical id: 5
          bus info: pci@00:05.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: bus_master cap_list
          configuration: driver=HDA Intel latency=0 maxlatency=5 mingnt=2
          resources: iomemory:dfff4000-dfff7fff irq:22
     *-ide:0
          description: IDE interface
          product: MCP61 IDE
          vendor: nVidia Corporation
          physical id: 6
          bus info: pci@00:06.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: ide bus_master cap_list
          configuration: driver=AMD_IDE latency=0 maxlatency=1 mingnt=3
          resources: iomemory:1f0-1f7 iomemory:3f0-3ef iomemory:170-177 iomemory:370-36f ioport:ffa0-ffaf
        *-ide
             description: IDE Channel 0
             physical id: 0
             bus info: ide@0
             logical name: ide0
             clock: 66MHz
           *-cdrom
                product: HL-DT-ST DVDRAM GSA-H44N
                physical id: 0
                bus info: ide@0.0
                logical name: /dev/hda
                capabilities: packet
     *-bridge
          description: Ethernet interface
          product: MCP61 Ethernet
          vendor: nVidia Corporation
          physical id: 7
          bus info: pci@00:07.0
          logical name: eth0
          version: a2
          serial: 00:19:db:d7:ca:c4
          width: 32 bits
          clock: 66MHz
          capabilities: bridge bus_master cap_list ethernet physical
          configuration: broadcast=yes driver=forcedeth driverversion=0.59 ip=130.243.217.114 latency=0 maxlatency=20 mingnt=1 multicast=yes
          resources: iomemory:dfff9000-dfff9fff ioport:e480-e487 irq:22
     *-ide:1
          description: IDE interface
          product: MCP61 SATA Controller
          vendor: nVidia Corporation
          physical id: 8
          bus info: pci@00:08.0
          logical name: scsi1
          logical name: scsi2
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: ide bus_master cap_list scsi-host
          configuration: driver=sata_nv latency=0 maxlatency=1 mingnt=3
          resources: ioport:e400-e407 ioport:e080-e083 ioport:e000-e007 ioport:dc00-dc03 ioport:d880-d88f iomemory:dfff8000-dfff8fff irq:20
     *-pci:1
          description: PCI bridge
          product: MCP61 PCI Express bridge
          vendor: nVidia Corporation
          physical id: 9
          bus info: pci@00:09.0
          version: a2
          width: 32 bits
          clock: 33MHz
          capabilities: pci normal_decode bus_master cap_list
          configuration: driver=pcieport-driver

```

[B]I did not assemble the computer myself, the vendor did. 

How shall I continue? Can it be a hardware error, a software error or some BIOS setting that has been done incorrectly?

Also, the vendor sent me a note with something called a PC report, where the graphics card is mentioned under "<Video System> / Adapter:", so i guess the card was responding before shipping.

Thank you for reading! Help appreciated![/B]

You have 2 different graphics cards, try taking one out.

---

### Post by John.Michael.Kane on 2007-10-05
> **sweRocker said:**
> [B]Hi, 

Well, I just installed Ubuntu 7.04 on my new computer with the following spec.:[/B]

AMD Athlon(tm) 64 X2 Dual Core Processor 4200+ (2.21 Ghz)
MSI K9N6SGM-V, nForce405+ **GeForce 6100**, Socket -AM2, m-ATX, DDR2, LAN, PCI-Ex8
2047 MB DDR-SDRAM
Gainward GeForce 7300GS 256MB DDR2, PCI-Express, "BP7300GS-256-TV-DVI"
(...)

You need to go into your bios, and disable the gefore6100. This should allow for your pci-e card to be seen by the bio, As well as Ubuntu.

---

### Post by sweRocker on 2007-10-05
**Thank you for the fast answer!  ** :)

Unfortunately it did not fix the problem...

I checked my bios, and it seems like **the motherboard recognizes the alternative graphics card.** 

From bios: "OnChip and PCIe VGA selection (Disable Onchip VGA)"

This was also mentioned in the motherboard manual: 
"Note:
System default is to disable the onboard VGA when you insert a PCI-E graph card, in order to
optimize the system performance. If you would like to use both onboard and expansion card
graph functions, you have to enter the mainboard BIOS and select Advanced Chipset Features
-> OnChip and PCIe VGA selection -> Both exist and Oncip VGA by frame buffer select."

How many ways can you disable the integrated graphics card in, could it be that I have missed one? Could it be something else?

---

### Post by Kilz on 2007-10-05
> **sweRocker said:**
> **Thank you for the fast answer!  ** :)

Unfortunately it did not fix the problem...

I checked my bios, and it seems like **the motherboard recognizes the alternative graphics card.** 

From bios: "OnChip and PCIe VGA selection (Disable Onchip VGA)"

This was also mentioned in the motherboard manual: 
"Note:
System default is to disable the onboard VGA when you insert a PCI-E graph card, in order to
optimize the system performance. If you would like to use both onboard and expansion card
graph functions, you have to enter the mainboard BIOS and select Advanced Chipset Features
-> OnChip and PCIe VGA selection -> Both exist and Oncip VGA by frame buffer select."

How many ways can you disable the integrated graphics card in, could it be that I have missed one? Could it be something else?

Have you tried removing the card and reinstalling it? Just to make sure its seated right.

---

### Post by sweRocker on 2007-10-08
Problems solved!

Well, it turns out I am more of a n00b than I first thought...

I am writing this how-to mostly for myself, but please comment if there is something strange in the list. 
[LIST=1]
[*]Use the motherboards [VGA]("http://sv.wikipedia.org/wiki/VGA") connection to connect the screen with the motherboard.
[*]Start the computer and insert the Ubuntu 7.04 installation CD. 
[*]Check for defects on the CD and burn a new one if there are.
[*]Install Ubuntu 7.04 (no [disk partitions]("http://en.wikipedia.org/wiki/Disk_partitioning"))
[*]Reboot
[*]Change the BIOS settings to inactivate the integrated graphics card.
[*]Reboot
[*]Remove the cable from the motherboards VGA connection and instead connect it to the graphics cards VGA connection. (:biggrin: this is the part I have missed before)
[*]Start the computer again, and receive an ugly error message where it says that the X-server is malfunctioning. Press no when it asks if I want to read some error-logs.
[*]Log in with my user name and password.
[*]Give the command: ```
sudo dpkg-reconfigure -phigh xserver-xorg
```
[*]Choose Vesa in the list.
[*]Choose my screen resolution 1440x900.
[*]Give the command: ```
startx
```
[*]Ubuntu will start, so open the **Restricted Drivers Manager**: System>Administration>Restricted Drivers Manager.
[*]Activate the "NVIDIA accelerated graphics driver".
[*]Reboot
[*]Open the terminal.
[*]Give the command: ```
sudo apt-get install nvidia-settings
```
[*]Give the command:```
 nvidia-settings
```
[*]The Nvidia settings manager is now open. Change the screen resolution to 1440x900.
[*]DONE!
[/LIST]

I have changed from VGA to [DVI]("http://en.wikipedia.org/wiki/Dvi") and it seems to work just fine.

**I still have some questions though...**[LIST=1]
[*]My screens recommended frequency is 60Hz using DVI and that is what the nvidia-settings manager is set to. But when I check Ubuntu's own screen resolution manager, it says it is 50Hz. Which one should I trust?
[*]The changes I do in nvidia-settings manager wont save between reboots, even though I try to save them in the xorg.conf (through the settings manager, no hacking!). The settings manager is also giving me some error messages. Both when I start it: ```
(nvidia-settings:7161): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

``` And when I try to save se xorg.conf ```
ERROR: Unable to create backup file '/etc/X11/xorg.conf.backup'.

```
[/LIST]

/sweRocker

---

### Post by forestpixie on 2007-10-08
> I still have some questions though...

1 - I'd love to know the answer to this too :) 

2 - are you running nvidia-settings with root access? sounds like you're not to me

```
gksudo nvidia-settings
```

---

### Post by John.Michael.Kane on 2007-10-08
@sweRocker you can try disabling Dynamic Twin View in /etc/X11/xorg.conf.

Add this line to xorg's card device section, and reboot..
```
Option "DynamicTwinView" "False"
```

---

