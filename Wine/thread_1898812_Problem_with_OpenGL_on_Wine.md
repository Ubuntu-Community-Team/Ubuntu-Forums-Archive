---
title: "Problem with OpenGL on Wine"
date: 2011-12-22
forum: Wine
---

### Post by Floating GFX on 2011-12-22
Hello everyone. Okay, let's just get to the point.

I've problem with my wine. Everytime I want to run an application, I always got this error:

> err:wgl:has_opengl Failed to load libGL: libGL.so.1: cannot open shared object file: No such file or directory
err:wgl:has_opengl OpenGL support is disabled.
fixme:advapi:SetEntriesInAclA 1 0x33f724 (nil) 0x33f75c
fixme:advapi:SetSecurityInfo stub
err:d3d_caps:WineD3D_CreateFakeGLContext Can't find a suitable iPixelFormat.
err:d3d:InitAdapters Failed to get a gl context for default adapter
Direct3D8 is not available without OpenGL.
fixme:advapi:SetEntriesInAclA 1 0x33f710 (nil) 0x33f758
fixme:advapi:SetSecurityInfo stub
fixme:advapi:SetEntriesInAclA 1 0x33f730 (nil) 0x33f778
fixme:advapi:SetSecurityInfo stub
fixme:system:SetProcessDPIAware stub!
fixme:dwmapi:DwmIsCompositionEnabled 0x33f0f0
fixme:iphlpapi:NotifyAddrChange (Handle 0xc8e8d8, overlapped 0xc8e8e0): stubI've already installed DirectX and configured it in Wine, but it didn't help at all. Please help me!

---

### Post by slavik on 2011-12-22
has nothing to do with programming, but:
1. do you have proper drivers installed?
2. glxinfo | grep direct

---

### Post by Floating GFX on 2011-12-22
I'm pretty sure I've already installed proper drivers. Can you please tell me about this glxinfo | grep direct?

---

### Post by fct on 2011-12-23
Running "glxinfo |grep direct" on the terminal will tell you if you have direct rendering (hardware acceleration).

You should also tell how you installed wine. Ubuntu repositories, ppa, compiled it yourself...?

---

### Post by Floating GFX on 2011-12-23
Well, I had Wine version 1.2.2. From Ubuntu repositories.

I tested "glxinfo |grep direct" and it said "direct rendering: Yes".

---

### Post by slavik on 2011-12-23
Moving to the Wine forum. Folks here should be able to assist better. :)

---

### Post by cwwilson721 on 2011-12-23
So little info given....

What:
[LIST]
[*]Is your hardware? (Post the ouput of 'lspci')
[*]Are you trying to run?
[*]Proprietary drivers have been installed?
[*]Have you checked with WineHQ's Database to see if the program is even working?
[/LIST]

Just saying 'everytime' does nothing to help. We need all the information.

---

### Post by Floating GFX on 2011-12-24
Alright. So, this is the software I want to run.

```
http://appdb.winehq.org/objectManager.php?sClass=version&iId=9594
```And this is my output of "lspci".

```
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 12)
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 12)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 05)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 05)
00:1f.2 IDE interface: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA IDE Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
00:1f.5 IDE interface: Intel Corporation 5 Series/3400 Series Chipset 2 port SATA IDE Controller (rev 05)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 05)
01:00.0 Ethernet controller: Broadcom Corporation NetLink BCM57780 Gigabit Ethernet PCIe (rev 01)
02:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)
ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 02)
ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 02)
ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 02)
ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 02)
ff:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
ff:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
```

---

