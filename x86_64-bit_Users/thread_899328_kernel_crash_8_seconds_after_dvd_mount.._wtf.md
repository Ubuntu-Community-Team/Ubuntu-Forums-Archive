---
title: "kernel crash 8 seconds after dvd mount.. wtf?"
date: 2008-08-24
forum: x86 64-bit Users
---

### Post by deinstein on 2008-08-24
hi! 7-8 seconds after mounting a DVD, the all network connections brake up. After rebooting, I can read the following in kern.log. The server is a headless machine, running ubuntu server with xen kernel.

I tried booting with irqpoll, which makes it work, but simple stuff like 'cp' or 'top' wont work in 50% of the cases (just freeze up until killed). I also tried noapic, which makes the PC not boot any more.

Board is a GIGABYTE GA-EP35C-DS3R, with a SAMSUNG SH-D162 DVD drive connected to the onboard IDE controller (jmicron, see below).

/var/log/kern.log:
```
Aug 23 15:41:02 server kernel: [  329.741632] UDF-fs: Partition marked readonly; forcing readonly mount
Aug 23 15:41:02 server kernel: [  329.760359] UDF-fs INFO UDF 0.9.8.1 (2004/29/09) Mounting volume 'MUNICH', timestamp 2006/09/08 11:25 (1078)
Aug 23 15:41:10 server kernel: [  337.442072] irq 16: nobody cared (try booting with the "irqpoll" option)
Aug 23 15:41:10 server kernel: [  337.442152] Pid: 0, comm: swapper Tainted: GF       2.6.24-19-xen #1
Aug 23 15:41:10 server kernel: [  337.442154]
Aug 23 15:41:10 server kernel: [  337.442154] Call Trace:
Aug 23 15:41:10 server kernel: [  337.442156]  <IRQ>  [__report_bad_irq+0x1e/0x80] __report_bad_irq+0x1e/0x80
Aug 23 15:41:10 server kernel: [  337.442171]  [note_interrupt+0x2d9/0x310] note_interrupt+0x2d9/0x310
Aug 23 15:41:10 server kernel: [  337.442176]  [handle_level_irq+0xb3/0x120] handle_level_irq+0xb3/0x120
Aug 23 15:41:10 server kernel: [  337.442180]  [do_IRQ+0x5d/0xc0] do_IRQ+0x5d/0xc0
Aug 23 15:41:10 server kernel: [  337.442184]  [evtchn_do_upcall+0x135/0x260] evtchn_do_upcall+0x135/0x260
Aug 23 15:41:10 server kernel: [  337.442192]  [do_hypervisor_callback+0x1e/0x30] do_hypervisor_callback+0x1e/0x30
Aug 23 15:41:10 server kernel: [  337.442194]  <EOI>  [apparmor_file_permission+0x0/0x20] apparmor_file_permission+0x0/0x20
Aug 23 15:41:10 server kernel: [  337.442204]  [processor:xen_safe_halt+0x8f/0x4fa0] xen_safe_halt+0x8f/0xe0
Aug 23 15:41:10 server kernel: [  337.442207]  [xen_idle+0x48/0x90] xen_idle+0x48/0x90
Aug 23 15:41:10 server kernel: [  337.442209]  [cpu_idle+0x73/0xe0] cpu_idle+0x73/0xe0
Aug 23 15:41:10 server kernel: [  337.442214]  [start_kernel+0x2e5/0x390] start_kernel+0x2e5/0x390
Aug 23 15:41:10 server kernel: [  337.442217]  [x86_64_start_kernel+0x14e/0x160] _sinittext+0x14e/0x160
Aug 23 15:41:10 server kernel: [  337.442220]
Aug 23 15:41:10 server kernel: [  337.442221] handlers:
Aug 23 15:41:10 server kernel: [  337.442289] [usbcore:usb_hcd_irq+0x0/0x60] (usb_hcd_irq+0x0/0x60 [usbcore])
Aug 23 15:41:10 server kernel: [  337.442477] [ata_generic:ata_interrupt+0x0/0x240] (ata_interrupt+0x0/0x240 [libata])
Aug 23 15:41:10 server kernel: [  337.442663] [r8169:rtl8169_interrupt+0x0/0x3c0] (rtl8169_interrupt+0x0/0x3c0 [r8169])
Aug 23 15:41:10 server kernel: [  337.442840] Disabling IRQ #16
Aug 23 15:41:46 server kernel: [  373.298669] ip6_tables: (C) 
2000-2006 Netfilter Core Team
((( REBOOT )))
Aug 23 15:44:37 server kernel: Inspecting /boot/System.map-2.6.24-19-xen
Aug 23 15:44:37 server kernel: Loaded 27822 symbols from /boot/System.map-2.6.24-19-xen.
Aug 23 15:44:37 server kernel: Symbols match kernel version 2.6.24.
Aug 23 15:44:37 server kernel: Loaded 15881 symbols from 70 modules.
```

```
keinstein@server:~$ uname -a
Linux server 2.6.24-19-xen #1 SMP Sat Jul 12 00:15:59 UTC 2008 x86_64 GNU/Linux
```

```
keinstein@server:~$ lspci
00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation 82G33/G31/P35/P31 Express PCI Express Root Port (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 02)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92)
00:1f.0 ISA bridge: Intel Corporation 82801IR (ICH9R) LPC Interface Controller (rev 02)
00:1f.2 RAID bus controller: Intel Corporation 82801 SATA RAID Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation G72 [GeForce 7300 SE] (rev a1)
03:00.0 SATA controller: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 02)
03:00.1 IDE interface: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 02)
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller (rev 20)
```

I searched the net, couldn't find anything (i.e. too much).

plz halp! ^^

edit: okay, aparently only eth0 crashes (disabling irq 16...) I had another problem with wlan, but now it works.

```
keinstein@server:~$ cat /proc/interrupts
           CPU0       CPU1       CPU2       CPU3
  1:         55          0          0          0  Phys-irq-level     i8042
  7:          0          0          0          0  Phys-irq-level     parport0
  8:          0          0          0          0  Phys-irq-level     rtc
  9:          0          0          0          0  Phys-irq-level     acpi
 16:    3240798          0          0          0  Phys-irq-level     uhci_hcd:usb3, libata, peth0
 18:          0          0          0          0  Phys-irq-level     ehci_hcd:usb1, uhci_hcd:usb5, uhci_hcd:usb8
 19:     218663          0          0          0  Phys-irq-level     uhci_hcd:usb7, ahci, ahci
 20:     316588          0          0          0  Phys-irq-level     wlan0
 21:          0          0          0          0  Phys-irq-level     uhci_hcd:usb4
 22:        128          0          0          0  Phys-irq-level     HDA Intel
 23:          0          0          0          0  Phys-irq-level     ehci_hcd:usb2, uhci_hcd:usb6
256:    3869054          0          0          0  Dynamic-irq-level     timer0
257:       6390          0          0          0  Dynamic-irq-level     resched0
258:         69          0          0          0  Dynamic-irq-level     callfunc0
259:          0      27745          0          0  Dynamic-irq-level     resched1
260:          0         94          0          0  Dynamic-irq-level     callfunc1
261:          0    3612236          0          0  Dynamic-irq-level     timer1
262:          0          0      43627          0  Dynamic-irq-level     resched2
263:          0          0         94          0  Dynamic-irq-level     callfunc2
264:          0          0    3612166          0  Dynamic-irq-level     timer2
265:          0          0          0     104708  Dynamic-irq-level     resched3
266:          0          0          0         82  Dynamic-irq-level     callfunc3
267:          0          0          0    3630222  Dynamic-irq-level     timer3
268:         82          0          0          0  Dynamic-irq-level     xenbus
269:          0          0          0          0  Dynamic-irq-level     console
NMI:          0          0          0          0   Non-maskable interrupts
RES:       6390      27745      43627     104708   Rescheduling interrupts
CAL:         69         94         94         82   function call interrupts
```

---

### Post by Ehtetur on 2008-08-25
Hi deinstein - One of these devices **uhci_hcd:usb3, libata, peth0** on IRQ16 may be generating a bunch of bogus interrupt requests which may then be pissing off the kernel.. Then when you mount the DVD, it may just be enough to push the kernel over edge... :evil:

I would try two things:
1. boot up with the non-Xen kernel and then try mounting your dvd...
2. if you have any diagnostic software, run hardware diags on your ATA devices and network card.

---

### Post by deinstein on 2008-08-25
well, the all those things are on-board, so the board must be broken :(

I "fixed" it with noirqdebug for now... ugh.

can I just move ethernet and usb to another irq?

otherwise, screw it, I dont have the patience to deal with it right now ;)

---

### Post by joze7205 on 2008-09-11
I have the same problem. It happens when I insert a DVD or a CD into the computer. 

It worked perfectely when I used Feisty Fawn one week ago and when I did fresh installs with Hardy, but when everything is installed, the problem starts. So I don't think there is anything wrong with my hardware.

Perhaps I should mention that my DVD-drive is an IDE-drive. I wonder if it has anything to do with this. I noticed that my "dev/cdrom" is symbolically linked to "scd0". Feisty didn't use SCSI emulation.

My computer is running Ubuntu 8.04 Desktop edition.

---

### Post by Poolcrack on 2009-04-20
I had the same problem when I insert a DVD or a CD into the computer. It was very annoying. The same drive: SAMSUNG SH-D162 DVD
(IDE), two harddisks (1 IDE, 1 SATA). I am using Ubuntu 8.10 Desktop Edition. Under Windows XP SP3 I have no problems.

Solution for me: I flashed the latest firmware on the DVD drive. Since this everything works fine now. :D

---

