---
title: "USB doesn't work"
date: 2008-01-21
forum: x86 64-bit Users (Pre April '08)
---

### Post by ciccero on 2008-01-21
Hi, I have several problems with my HP pavillon tx1332la, but i think to solve one by one, the first a more critical is fix the usb, i have kubuntu 7.1 gutsy, 64 bit installed version and my USB doesn't work, i'm new in linux word but i like the challenge (and want to have the control of my computer).
i do a lsusb i a have this:
```
cuitlahuac@cic-ciiaas:~$ lspci
00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:05.0 VGA compatible controller: nVidia Corporation C51 [Geforce 6150 Go] (rev a2)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
00:0a.3 Co-processor: nVidia Corporation MCP51 PMU (rev a3)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev f1)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev f1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
03:00.0 Network controller: Broadcom Corporation BCM4328 802.11a/b/g/n (rev 03)
cuitlahuac@cic-ciiaas:~$ lsusb
Bus 002 Device 002: ID 03f0:171d Hewlett-Packard
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 006: ID 0eef:0001 D-WAV Scientific Co., Ltd eGalax TouchScreen
Bus 001 Device 005: ID 08ff:1600 AuthenTec, Inc.
Bus 001 Device 004: ID 0c45:62c0 Microdia
Bus 001 Device 002: ID 04b4:6560 Cypress Semiconductor Corp. CY7C65640 USB-2.0 "TetraHub"
Bus 001 Device 001: ID 0000:0000

```

i install with the -noapic option, could be this the problem?
there are commands to test the usb port manually?

HELP

atte.
ciccero

---

### Post by intel on 2008-01-22
what do you mean USB is not working?

which device are you trying to use under linux?
does the same device work perfectly under windows?

---

### Post by Jouke74 on 2008-01-22
Could you also please post the last 30 lines or so from a "dmesg" command run in a terminal? after you connected the USB device.

---

### Post by ciccero on 2008-01-23
hi Jouke74 last 30 lines are:
```

[   34.597997] powernow-k8: Found 2 AMD Turion(tm) 64 X2 Mobile Technology TL-58
 processors (version 2.00.00)
[   34.597483] powernow-k8:    0 : fid 0xb (1900 MHz), vid 0x11
[   34.597489] powernow-k8:    1 : fid 0xa (1800 MHz), vid 0x12
[   34.597492] powernow-k8:    2 : fid 0x8 (1600 MHz), vid 0x13
[   34.597494] powernow-k8:    3 : fid 0x0 (800 MHz), vid 0x1e
[   35.600204] eth0: no link during initialization.
[   36.633072] ppdev: user-space parallel port driver
[   36.980947] audit(1201101667.014:3):  type=1503 operation="inode_permission"
requested_mask="a" denied_mask="a" name="/dev/tty" pid=5449 profile="/usr/sbin/c
upsd"
[   40.286970] Bluetooth: L2CAP ver 2.8
[   40.286977] Bluetooth: L2CAP socket layer initialized
[   40.307406] Bluetooth: RFCOMM socket layer initialized
[   40.307423] Bluetooth: RFCOMM TTY layer initialized
[   40.307427] Bluetooth: RFCOMM ver 1.8
[   57.365733] uvcvideo: Failed to query (1) UVC control 9 (unit 3) : -32 (exp.
2).
[   65.192970] NET: Registered protocol family 10
[   65.193296] lo: Disabled Privacy Extensions
[   65.193569] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   65.193739] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   76.682357] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   81.243232] wlan0: no IPv6 routers present
[  142.705867] irq 7: nobody cared (try booting with the "irqpoll" option)
[  142.705873]
[  142.705874] Call Trace:
[  142.705877]  <IRQ>  [<ffffffff8026aade>] __report_bad_irq+0x1e/0x80
[  142.705903]  [<ffffffff8026adc3>] note_interrupt+0x283/0x2c0
[  142.705912]  [<ffffffff8026bbbc>] handle_level_irq+0x10c/0x140
[  142.705920]  [<ffffffff8020c6ab>] do_IRQ+0x7b/0x100
[  142.705923]  [<ffffffff80209010>] default_idle+0x0/0x40
[  142.705928]  [<ffffffff8020a3a1>] ret_from_intr+0x0/0xa
[  142.705931]  <EOI>  [<ffffffff804221d0>] unix_poll+0x0/0xb0
[  142.705943]  [<ffffffff80209039>] default_idle+0x29/0x40
[  142.705949]  [<ffffffff802090c0>] cpu_idle+0x70/0xc0
[  142.705965]
[  142.705966] handlers:
[  142.705968] [<ffffffff88038d30>] (usb_hcd_irq+0x0/0x60 [usbcore])
[  142.705990] Disabling IRQ #7

```

I cann't see any change before and after i connect a "USB memory" device, 

the computer has 3 ubs port and none of them are working.

i think i answer you question INTEL?

atte.
ciccero

saludos

---

### Post by Jouke74 on 2008-01-23
Any messages errors about the USB in the total dmesg file?

This also does not look good:
irq 7: nobody cared (try booting with the "irqpoll" option)

[  142.705874] Call Trace:
[  142.705877]  <IRQ>  [<ffffffff8026aade>] __report_bad_irq+0x1e/0x80

[  142.705968] [<ffffffff88038d30>] (usb_hcd_irq+0x0/0x60 [usbcore])
[  142.705990] Disabling IRQ #7

Did you try booting with the NOAPIC option in your grub as well, not only during install?
And I suggest after you try NOAPIC, you then check the additional IRQPOLL option as well?

Grub is the bootlader. You can edit the kernel line to add and delete these options. 

I am not sure however if you want to use a laptop this way, as most power saving will be disabled I guess.. :(

---

### Post by vacadepollo on 2008-01-23
I have similar problems in my compaq Presario F500



Add **noapic irqpool** to kernel boot (grub)


check usb modules boot

**dmesg | grep usb**

check modules loaded

**lsmod | grep usb**

Is it* usb-storage*?

if not,
[B]
sudo aptitude install modconf

sudo modconf [/B]

go to  *kernel/drivers/usb/storage*  and run!

reboot and check

---

### Post by ciccero on 2008-01-23
Thank you so much, jouke74 and vacadepollo, yours comments solved my problem, i modified the kernel boot in grub with the option "irqpool" (the noapic option was by default i think when i intalled the kubuntu), and now i have the 3 usb ports working, 

Thank you.

atte.
ciccero

by the way where can i read about these options?

---

### Post by Jouke74 on 2008-01-24
Is it Irqpoll or Irqpool? I never heard of Irqpool until now. I think the modconf install did more to be honest.

---

### Post by ciccero on 2008-01-25
I don't understand, i use 'irqpool' and the usb work, and use 'irqpoll' and the usb work again..... I remember in cisco router programming you don't need to put all command to execute it, you only put a short word like 'inter' instead 'interfase', could be this the reason of the 'irqpool' and 'irqpoll' work on my laptop?:)

atte.
ciccero

---

### Post by Jouke74 on 2008-01-25
Yup that could be true. Irqpoll is the one that for sure exists reading some Google pages about Kernel parameters. Anyway, it works.

---

