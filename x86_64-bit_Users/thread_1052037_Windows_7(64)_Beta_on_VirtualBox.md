---
title: "Windows 7(64) Beta on VirtualBox"
date: 2009-01-27
forum: x86 64-bit Users
---

### Post by xRes on 2009-01-27
I'm having an issue with an install of Windows 7 Beta 64 on VirtualBox. 
I have Ubuntu 64 8.04 and VBox 64 2.1.2 but on each attempt on install I get an error saying:
"Attempting to load a 64-bit application, however this CPU is not compatible with 64-bit mode"

I have 'ACPI, IO APIC & Enable VT-x/AMD-V' all enabled.

Has anyone got Windows 7 64 running on their Ubuntu machine?

---

### Post by jocko on 2009-01-27
Are you sure that  VT-x or AMD-V is activated in your bios?

---

### Post by doobrain on 2009-01-27
*deleted*

---

### Post by sagen on 2009-01-27
I've got it running fine. 

Not sure if it's what makes the difference, but i've got "Enable PAE/NX" checked, and running "Other Windows" as Version. 
You didn't mention those, so just my 2 cents :)

---

### Post by sanderj on 2009-01-27
> **xRes said:**
> I'm having an issue with an install of Windows 7 Beta 64 on VirtualBox. 
I have Ubuntu 64 8.04 and VBox 64 2.1.2 but on each attempt on install I get an error saying:
"Attempting to load a 64-bit application, however this CPU is not compatible with 64-bit mode"

I have 'ACPI, IO APIC & Enable VT-x/AMD-V' all enabled.


Can you run any other 64-bit OS, like Ubuntu 64-bit, on your VirtualBox?

---

### Post by Tubes6al4v on 2009-01-28
I am pretty sure that virtual box will not emulate a 64 bit system. I got the same response for Ubuntu 64. I have windows 7 32 bit running fine on my AMD64 machine. 

I think some other virtualization software will run 64 bit (vmware?)

---

### Post by sanderj on 2009-01-28
> **Tubes6al4v said:**
> I am pretty sure that virtual box will not emulate a 64 bit system.

Not true: VirtualBox can handle 64-bit guests. See [http://en.wikipedia.org/wiki/VirtualBox](http://en.wikipedia.org/wiki/VirtualBox) :

Feature set: 
    * 64-bit guests 

However, you have to enable a certain option in VirtualBox, which the OP has done AFAIK.

---

### Post by Tubes6al4v on 2009-01-28
Thanks for the correction brother. I will look into how that is done. But is anyone running enough RAM in their system to make 64 bit worth it? I can only use 1gb for virtualbox (I have 2gb total)

---

### Post by mgranet on 2009-01-28
VirtualBox will most certainly run a 64bit guest on a 64 bit host. You simply need to have a processor with virtualization support (VT-x/AMD-V), and you need to enable that option in the settings for your guest machine.

---

### Post by sanderj on 2009-01-29
I checked on my own 64-bit setup, and I can run 64-bit Ubuntu on VirtualBox on Ubuntu 64-bit. I just had to enable the VT-X/AMD-V.

So, yes, VirtualBox can run 64-bit guests.

To the OP: can I just download and run Windows 7, or do I need to register (which I don't want to do)?

---

### Post by sanderj on 2009-01-29
> **Tubes6al4v said:**
> But is anyone running enough RAM in their system to make 64 bit worth it? I can only use 1gb for virtualbox (I have 2gb total)

With my 4GB RAM, VirtualBox can give a guest up to 3.5 GB or so, by just sliding the slider ...

HTH

---

### Post by novafluxx on 2009-01-29
The latest version of VirtualBox includes Windows 7 as a Windows Version to select from. Also, yes, you must register for a key.

---

### Post by xRes on 2009-01-29
Some great ideas so thanks all. I have tried a whole combination of settings on VirtualBox with no joy, so I think the most likely issue is something to do with VT-x or AMD-V being set on my BIOS as suggested by Jocko. 
Now the issue here is my BIOS is version 1.06 on an Acer Aspire 5720 does not allow any changes other than boot order and other simple stuff. That version does appear to be well out of date though according to the Acer support site who offers version 1.42 so I'm going to give that a go and hopefully it will work. Only problem is I cant download my current BIOS version meaning if my brick my laptop I might not be able to revert back to a BIOS that works. Any ideas?

---

### Post by norcim on 2009-01-29
Just my 2 cents... Install the full win7 and you will see a dramatic difference. You can even use the virtual install to load the iso into a usb for installation. Just be sure to have a Live CD handy so you can restore grub if you have it.

---

### Post by jimav on 2009-02-16
I got the same "this CPU is not compatible with 64-bit mode" error while booting Win7 Beta on VirtualBox 2.1.2 and Ubuntu 8.10 64-bit on an Intel Core i7 machine.

The problem appears to be related to enabling nested page tables and/or PAE.  When I turn them off in VBox, it works great.

Below is the output from "VBoxManage list vms".  You could try running the same command and diffing the results with mine to maybe figure out why yours does not work.

P.S. Once you get it working, be sure to try "Machine->Seamless Mode" -- it is just fabulous (Win7 windows appear on your Linux desktop).  I won't ever struggle with Xen again!

```

VirtualBox Command Line Management Interface Version 2.1.2
(C) 2005-2009 Sun Microsystems, Inc.
All rights reserved.

Name:            Win7B64
Guest OS:        Windows 7 (64 bit)
UUID:            redacted
Config file:     /redacted/.VirtualBox/Machines/Win7B64/Win7B64.xml
Memory size:     2048MB
VRAM size:       64MB
Boot menu mode:  message and menu
ACPI:            on
IOAPIC:          on
PAE:             off
Time offset:     0 ms
Hardw. virt.ext: on
Nested Paging:   off
VT-x VPID:       off
State:           powered off (since 2009-02-16T06:23:22.000000000)
Monitor count:   1
3D Acceleration: on
Floppy:          empty
SATA:            disabled
IDE Controller:  PIIX4
Primary master:  /redacted/.VirtualBox/diskimages/Win7B64_disk.vdi (UUID: redacted)
DVD:             empty
NIC 1:           MAC: redacted, Attachment: Host Interface 'eth0', Cable connected: on, Trace: off (file: none), Type: 82540EM, Reported speed: 0 Mbps
NIC 2:           disabled
NIC 3:           disabled
NIC 4:           disabled
NIC 5:           disabled
NIC 6:           disabled
NIC 7:           disabled
NIC 8:           disabled
UART 1:          disabled
UART 2:          disabled
Audio:           disabled (Driver: Unknown, Controller: Unknown)
Clipboard Mode:  Bidirectional
VRDP:            disabled
USB:             disabled

USB Device Filters:

<none>

Shared folders:

Name: 'jima', Host path: '/redacted' (machine mapping), writable

Guest:

Statistics update:                   disabled


```

---

