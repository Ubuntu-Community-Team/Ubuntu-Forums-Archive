---
title: "Machine crash logging"
date: 2009-10-12
forum: x86 64-bit Users
---

### Post by captainKrash on 2009-10-12
Hi There,

My machine is crashing about every 10 mins or so. I don't know why. 

This happened before and plagued me for a day or so, then everything was ok for weeks.

How can I find out the cause? Which log files would give a pointer? Is there anything I can do to find out the cause?

Sorry if these questions appear to be dumb!

---

### Post by prshah on 2009-10-12
> **captainKrash said:**
> 
My machine is crashing about every 10 mins or so. I don't know why. 

Your system may be getting overheated; check the internal fans. You can also check this by adding the "Hardware sensors monitor" applet; right click your gnome bar, choose "Add to Panel" and choose  "Hardware sensors monitor" from the choices that pop up.

Be aware that this applet is not always accurate. It's accuracy varies from system to system.

You can check /var/log/messages and /var/log/messages.1 for clues to why it's crashing.

If you find that date and time is not being maintained, it could possibly be the Internal CMOS battery has reached End Of Life. This can be easily replaced (relatively) and costs only about a dollar or so.

---

### Post by captainKrash on 2009-10-12
Thank you for the reply.

I am on Ubuntu hardy 8.04 (64 bit), there is no +Add to Panel option of that name. System time and date is A OK too.

I have pasted the last few hundred lines from /var/log/messages, though it is all dutch to me I am afraid. :confused:

```
Oct 12 14:02:06 lamp-desktop kernel: [   38.924096] powernow-k8:    2 : fid 0xe (2200 MHz), vid 0xd
Oct 12 14:02:06 lamp-desktop kernel: [   38.924097] powernow-k8:    3 : fid 0xc (2000 MHz), vid 0xf
Oct 12 14:02:06 lamp-desktop kernel: [   38.924099] powernow-k8:    4 : fid 0xa (1800 MHz), vid 0x11
Oct 12 14:02:06 lamp-desktop kernel: [   38.924100] powernow-k8:    5 : fid 0x2 (1000 MHz), vid 0x12
Oct 12 14:02:07 lamp-desktop kernel: [   39.693984] ppdev: user-space parallel port driver
Oct 12 14:02:08 lamp-desktop kernel: [   41.245140] audit(1255352528.646:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5439 profile="/usr/sbin/cupsd" namespace="default"
Oct 12 14:02:09 lamp-desktop dhcdbd: Started up.
Oct 12 14:02:09 lamp-desktop kernel: [   41.991552] Clocksource tsc unstable (delta = -300006374 ns)
Oct 12 14:02:11 lamp-desktop kernel: [   42.563420] Bluetooth: Core ver 2.11
Oct 12 14:02:11 lamp-desktop kernel: [   42.563576] NET: Registered protocol family 31
Oct 12 14:02:11 lamp-desktop kernel: [   42.563578] Bluetooth: HCI device and connection manager initialized
Oct 12 14:02:11 lamp-desktop kernel: [   42.563581] Bluetooth: HCI socket layer initialized
Oct 12 14:02:11 lamp-desktop kernel: [   42.576876] Bluetooth: L2CAP ver 2.9
Oct 12 14:02:11 lamp-desktop kernel: [   42.576880] Bluetooth: L2CAP socket layer initialized
Oct 12 14:02:11 lamp-desktop kernel: [   42.612495] Bluetooth: RFCOMM socket layer initialized
Oct 12 14:02:11 lamp-desktop kernel: [   42.612592] Bluetooth: RFCOMM TTY layer initialized
Oct 12 14:02:11 lamp-desktop kernel: [   42.612595] Bluetooth: RFCOMM ver 1.8
Oct 12 14:02:14 lamp-desktop motion: [0] Processing thread 0 - config file /etc/motion/motion.conf
Oct 12 14:02:14 lamp-desktop motion: [0] Motion 3.2.11 Started
Oct 12 14:02:19 lamp-desktop kernel: [   45.830001] hda-intel: Invalid position buffer, using LPIB read method instead.
Oct 12 14:02:36 lamp-desktop kernel: [   52.610289] usb 5-1.4: new low speed USB device using ohci_hcd and address 4
Oct 12 14:02:36 lamp-desktop kernel: [   52.653903] usb 5-1.4: configuration #1 chosen from 1 choice
Oct 12 14:02:36 lamp-desktop kernel: [   52.659970] input: Logitech USB Optical Mouse as /devices/pci0000:00/0000:00:13.4/usb5/5-1/5-1.4/5-1.4:1.0/input/input6
Oct 12 14:02:36 lamp-desktop kernel: [   52.674179] input,hidraw2: USB HID v1.10 Mouse [Logitech USB Optical Mouse] on usb-0000:00:13.4-1.4
Oct 12 14:02:42 lamp-desktop kernel: [   55.271535] Inbound IN=eth0 OUT= MAC=00:50:8d:be:50:8b:00:1d:68:0a:aa:1c:08:00 SRC=64.4.34.216 DST=192.168.1.249 LEN=41 TOS=0x00 PREC=0x00 TTL=114 ID=29975 DF PROTO=TCP SPT=1863 DPT=42178 WINDOW=64866 RES=0x00 ACK URGP=0 
Oct 12 14:02:44 lamp-desktop kernel: [   55.708729] Inbound IN=eth0 OUT= MAC=00:50:8d:be:50:8b:00:1d:68:0a:aa:1c:08:00 SRC=64.4.34.216 DST=192.168.1.249 LEN=41 TOS=0x00 PREC=0x00 TTL=114 ID=4652 DF PROTO=TCP SPT=1863 DPT=42178 WINDOW=64866 RES=0x00 ACK URGP=0 
Oct 12 14:02:45 lamp-desktop kernel: [   56.145446] Inbound IN=eth0 OUT= MAC=00:50:8d:be:50:8b:00:1d:68:0a:aa:1c:08:00 SRC=64.4.34.216 DST=192.168.1.249 LEN=41 TOS=0x00 PREC=0x00 TTL=114 ID=12053 DF PROTO=TCP SPT=1863 DPT=42178 WINDOW=64866 RES=0x00 ACK URGP=0 
Oct 12 14:02:46 lamp-desktop kernel: [   56.582661] Inbound IN=eth0 OUT= MAC=00:50:8d:be:50:8b:00:1d:68:0a:aa:1c:08:00 SRC=64.4.34.216 DST=192.168.1.249 LEN=41 TOS=0x00 PREC=0x00 TTL=114 ID=19419 DF PROTO=TCP SPT=1863 DPT=42178 WINDOW=64866 RES=0x00 ACK URGP=0 
Oct 12 14:02:47 lamp-desktop kernel: [   57.019672] Inbound IN=eth0 OUT= MAC=00:50:8d:be:50:8b:00:1d:68:0a:aa:1c:08:00 SRC=64.4.34.216 DST=192.168.1.249 LEN=41 TOS=0x00 PREC=0x00 TTL=114 ID=27241 DF PROTO=TCP SPT=1863 DPT=42178 WINDOW=64866 RES=0x00 ACK URGP=0 
Oct 12 14:22:06 lamp-desktop -- MARK --
Oct 12 14:31:57 lamp-desktop kernel: [  987.257523] Inbound IN=eth0 OUT= MAC=00:50:8d:be:50:8b:00:1d:68:0a:aa:1c:08:00 SRC=38.99.186.24 DST=192.168.1.249 LEN=72 TOS=0x00 PREC=0x00 TTL=47 ID=1896 PROTO=ICMP TYPE=11 CODE=0 [SRC=192.168.1.249 DST=38.99.186.27 LEN=44 TOS=0x00 PREC=0x00 TTL=1 ID=26670 DF PROTO=TCP SPT=59562 DPT=80 WINDOW=5840 RES=0x00 SYN URGP=0 ] 
Oct 12 14:32:05 lamp-desktop kernel: [  995.051276] Inbound IN=eth0 OUT= MAC=00:50:8d:be:50:8b:00:1d:68:0a:aa:1c:08:00 SRC=38.99.186.24 DST=192.168.1.249 LEN=72 TOS=0x00 PREC=0x00 TTL=47 ID=1897 PROTO=ICMP TYPE=11 CODE=0 [SRC=192.168.1.249 DST=38.99.186.27 LEN=44 TOS=0x00 PREC=0x00 TTL=1 ID=57215 DF PROTO=TCP SPT=59638 DPT=80 WINDOW=5840 RES=0x00 SYN URGP=0 ] 
Oct 12 14:32:06 lamp-desktop kernel: [  995.977200] Inbound IN=eth0 OUT= MAC=00:50:8d:be:50:8b:00:1d:68:0a:aa:1c:08:00 SRC=38.99.186.24 DST=192.168.1.249 LEN=72 TOS=0x00 PREC=0x00 TTL=47 ID=1898 PROTO=ICMP TYPE=11 CODE=0 [SRC=192.168.1.249 DST=38.99.186.27 LEN=44 TOS=0x00 PREC=0x00 TTL=1 ID=26672 DF PROTO=TCP SPT=59562 DPT=80 WINDOW=5840 RES=0x00 SYN URGP=0 ] 
Oct 12 14:32:08 lamp-desktop kernel: [  998.046874] Inbound IN=eth0 OUT= MAC=00:50:8d:be:50:8b:00:1d:68:0a:aa:1c:08:00 SRC=38.99.186.24 DST=192.168.1.249 LEN=72 TOS=0x00 PREC=0x00 TTL=47 ID=1899 PROTO=ICMP TYPE=11 CODE=0 [SRC=192.168.1.249 DST=38.99.186.27 LEN=44 TOS=0x00 PREC=0x00 TTL=1 ID=57216 DF PROTO=TCP SPT=59638 DPT=80 WINDOW=5840 RES=0x00 SYN URGP=0 ] 
Oct 12 14:32:37 lamp-desktop kernel: [ 1025.791965] Inbound IN=eth0 OUT= MAC=00:50:8d:be:50:8b:00:1d:68:0a:aa:1c:08:00 SRC=38.99.186.24 DST=192.168.1.249 LEN=72 TOS=0x00 PREC=0x00 TTL=47 ID=1900 PROTO=ICMP TYPE=11 CODE=0 [SRC=192.168.1.249 DST=38.99.186.27 LEN=44 TOS=0x00 PREC=0x00 TTL=1 ID=9835 DF PROTO=TCP SPT=59816 DPT=80 WINDOW=5840 RES=0x00 SYN URGP=0 ] 
Oct 12 14:32:46 lamp-desktop kernel: [ 1030.707343] Inbound IN=eth0 OUT= MAC=00:50:8d:be:50:8b:00:1d:68:0a:aa:1c:08:00 SRC=38.99.186.24 DST=192.168.1.249 LEN=72 TOS=0x00 PREC=0x00 TTL=47 ID=1901 PROTO=ICMP TYPE=11 CODE=0 [SRC=192.168.1.249 DST=38.99.186.27 LEN=44 TOS=0x00 PREC=0x00 TTL=1 ID=9837 DF PROTO=TCP SPT=59816 DPT=80 WINDOW=5840 RES=0x00 SYN URGP=0 ] 
Oct 12 14:56:19 lamp-desktop kernel: [ 1862.768450] usb 5-1.4: USB disconnect, address 4
Oct 12 14:57:25 lamp-desktop kernel: [ 1888.936298] usb 5-1.4: new low speed USB device using ohci_hcd and address 5
Oct 12 14:57:25 lamp-desktop kernel: [ 1888.979917] usb 5-1.4: configuration #1 chosen from 1 choice
Oct 12 14:57:25 lamp-desktop kernel: [ 1888.983588] input: Logitech USB Optical Mouse as /devices/pci0000:00/0000:00:13.4/usb5/5-1/5-1.4/5-1.4:1.0/input/input7
Oct 12 14:57:25 lamp-desktop kernel: [ 1888.997050] input,hidraw2: USB HID v1.10 Mouse [Logitech USB Optical Mouse] on usb-0000:00:13.4-1.4
Oct 12 15:22:06 lamp-desktop -- MARK --
Oct 12 15:42:06 lamp-desktop -- MARK --
Oct 12 15:44:13 lamp-desktop kernel: [ 3233.872712] usb 5-1.4: USB disconnect, address 5
Oct 12 15:44:34 lamp-desktop kernel: [ 3242.555782] usb 5-1.4: new low speed USB device using ohci_hcd and address 6
Oct 12 15:44:34 lamp-desktop kernel: [ 3242.599002] usb 5-1.4: configuration #1 chosen from 1 choice
Oct 12 15:44:34 lamp-desktop kernel: [ 3242.605255] input: Logitech USB Optical Mouse as /devices/pci0000:00/0000:00:13.4/usb5/5-1/5-1.4/5-1.4:1.0/input/input8
Oct 12 15:44:35 lamp-desktop kernel: [ 3242.619502] input,hidraw2: USB HID v1.10 Mouse [Logitech USB Optical Mouse] on usb-0000:00:13.4-1.4
Oct 12 16:02:06 lamp-desktop -- MARK --
Oct 12 16:22:06 lamp-desktop -- MARK --
Oct 12 16:42:06 lamp-desktop -- MARK --
Oct 12 16:49:49 lamp-desktop kernel: [ 5011.274321] usb 5-1.4: USB disconnect, address 6
Oct 12 16:57:51 lamp-desktop kernel: [ 5203.483838] usb 5-1.4: new low speed USB device using ohci_hcd and address 7
Oct 12 16:57:51 lamp-desktop kernel: [ 5203.527058] usb 5-1.4: configuration #1 chosen from 1 choice
Oct 12 16:57:51 lamp-desktop kernel: [ 5203.534236] input: Logitech USB Optical Mouse as /devices/pci0000:00/0000:00:13.4/usb5/5-1/5-1.4/5-1.4:1.0/input/input9
Oct 12 16:57:51 lamp-desktop kernel: [ 5203.555513] input,hidraw2: USB HID v1.10 Mouse [Logitech USB Optical Mouse] on usb-0000:00:13.4-1.4
Oct 12 17:17:27 lamp-desktop kernel: [ 5732.334520] usb 5-1.4: USB disconnect, address 7
Oct 12 17:17:53 lamp-desktop kernel: [ 5742.640925] usb 5-1.4: new low speed USB device using ohci_hcd and address 8
Oct 12 17:17:53 lamp-desktop kernel: [ 5742.684540] usb 5-1.4: configuration #1 chosen from 1 choice
Oct 12 17:17:53 lamp-desktop kernel: [ 5742.691148] input: Logitech USB Optical Mouse as /devices/pci0000:00/0000:00:13.4/usb5/5-1/5-1.4/5-1.4:1.0/input/input10
Oct 12 17:17:53 lamp-desktop kernel: [ 5742.712721] input,hidraw2: USB HID v1.10 Mouse [Logitech USB Optical Mouse] on usb-0000:00:13.4-1.4
Oct 12 17:42:06 lamp-desktop -- MARK --
Oct 12 17:51:39 lamp-desktop syslogd 1.5.0#1ubuntu1: restart.
Oct 12 17:51:39 lamp-desktop kernel: Inspecting /boot/System.map-2.6.24-24-generic
Oct 12 17:51:40 lamp-desktop kernel: Loaded 28536 symbols from /boot/System.map-2.6.24-24-generic.
Oct 12 17:51:40 lamp-desktop kernel: Symbols match kernel version 2.6.24.
Oct 12 17:51:35 lamp-desktop kernel: Loaded 18438 symbols from 93 modules.
Oct 12 17:51:35 lamp-desktop kernel: [    0.000000] Initializing cgroup subsys cpuset
Oct 12 17:51:35 lamp-desktop kernel: [    0.000000] Initializing cgroup subsys cpu
Oct 12 17:51:35 lamp-desktop kernel: [    0.000000] Linux version 2.6.24-24-generic (buildd@crested) (gcc version 4.2.4 (Ubuntu 4.2.4-1ubuntu4)) #1 SMP Fri Sep 18 16:16:18 UTC 2009 (Ubuntu 2.6.24-24.61-generic)
Oct 12 17:51:35 lamp-desktop kernel: [    0.000000] Command line: root=UUID=91f75113-58d1-4256-90e5-6f67389d33e5 ro quiet splash
Oct 12 17:51:35 lamp-desktop kernel: [    0.000000] BIOS-provided physical RAM map:
Oct 12 17:51:35 lamp-desktop kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f400 (usable)
Oct 12 17:51:35 lamp-desktop kernel: [    0.000000]  BIOS-e820: 000000000009f400 - 00000000000a0000 (reserved)
Oct 12 17:51:35 lamp-desktop kernel: [    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
Oct 12 17:51:35 lamp-desktop kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 00000000cfff0000 (usable)
Oct 12 17:51:35 lamp-desktop kernel: [    0.000000]  BIOS-e820: 00000000cfff0000 - 00000000cfff3000 (ACPI NVS)
Oct 12 17:51:35 lamp-desktop kernel: [    0.000000]  BIOS-e820: 00000000cfff3000 - 00000000d0000000 (ACPI data)
Oct 12 17:51:35 lamp-desktop kernel: [    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
Oct 12 17:51:35 lamp-desktop kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
Oct 12 17:51:35 lamp-desktop kernel: [    0.000000]  BIOS-e820: 0000000100000000 - 0000000130000000 (usable)
Oct 12 17:51:35 lamp-desktop kernel: [    0.000000] end_pfn_map = 1245184
Oct 12 17:51:35 lamp-desktop kernel: [    0.000000] DMI 2.5 present.
Oct 12 17:51:35 lamp-desktop kernel: [    0.000000] ACPI: RSDP signature @ 0xFFFF8100000F81D0 checksum 0
Oct 12 17:51:35 lamp-desktop kernel: [    0.000000] ACPI: RSDP 000F81D0, 0024 (r2 AMD770)
Oct 12 17:51:35 lamp-desktop kernel: [    0.000000] ACPI: RSDT CFFF3000, 0038 (r1 AMD770 AWRDACPI 42302E31 AWRD        0)
Oct 12 17:51:35 lamp-desktop kernel: [    0.000000] ACPI: FACP CFFF3080, 0074 (r1 AMD770 AWRDACPI 42302E31 AWRD        0)
Oct 12 17:51:35 lamp-desktop kernel: [    0.000000] ACPI: DSDT CFFF3100, 51E2 (r1 AMD770 AWRDACPI     1000 MSFT  3000000)
Oct 12 17:51:35 lamp-desktop kernel: [    0.000000] ACPI: FACS CFFF0000, 0040
Oct 12 17:51:35 lamp-desktop kernel: [    0.000000] ACPI: SSDT CFFF83C0, 028A (r1 PTLTD  POWERNOW        1  LTP        1)
Oct 12 17:51:35 lamp-desktop kernel: [    0.000000] ACPI: HPET CFFF8680, 0038 (r1 AMD770 AWRDACPI 42302E31 AWRD       98)
Oct 12 17:51:35 lamp-desktop kernel: [    0.000000] ACPI: MCFG CFFF86C0, 003C (r1 AMD770 AWRDACPI 42302E31 AWRD        0)
Oct 12 17:51:35 lamp-desktop kernel: [    0.000000] ACPI: APIC CFFF8300, 0084 (r1 AMD770 AWRDACPI 42302E31 AWRD        0)
Oct 12 17:51:35 lamp-desktop kernel: [    0.000000] Scanning NUMA topology in Northbridge 24
Oct 12 17:51:35 lamp-desktop kernel: [    0.000000] CPU has 2 num_cores
Oct 12 17:51:35 lamp-desktop kernel: [    0.000000] No NUMA configuration found
Oct 12 17:51:35 lamp-desktop kernel: [    0.000000] Faking a node at 0000000000000000-0000000130000000
Oct 12 17:51:35 lamp-desktop kernel: [    0.000000] Bootmem setup node 0 0000000000000000-0000000130000000
Oct 12 17:51:35 lamp-desktop kernel: [    0.000000] Zone PFN ranges:
Oct 12 17:51:35 lamp-desktop kernel: [    0.000000]   DMA             0 ->     4096
Oct 12 17:51:35 lamp-desktop kernel: [    0.000000]   DMA32        4096 ->  1048576
Oct 12 17:51:35 lamp-desktop kernel: [    0.000000]   Normal    1048576 ->  1245184
Oct 12 17:51:35 lamp-desktop kernel: [    0.000000] Movable zone start PFN for each node
Oct 12 17:51:35 lamp-desktop kernel: [    0.000000] early_node_map[3] active PFN ranges
Oct 12 17:51:35 lamp-desktop kernel: [    0.000000]     0:        0 ->      159
Oct 12 17:51:35 lamp-desktop kernel: [    0.000000]     0:      256 ->   851952
Oct 12 17:51:35 lamp-desktop kernel: [    0.000000]     0:  1048576 ->  1245184
Oct 12 17:51:35 lamp-desktop kernel: [    0.000000] ATI board detected. Disabling timer routing over 8254.
Oct 12 17:51:35 lamp-desktop kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x4008
Oct 12 17:51:35 lamp-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Oct 12 17:51:35 lamp-desktop kernel: [    0.000000] Processor #0 (Bootup-CPU)
Oct 12 17:51:35 lamp-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
Oct 12 17:51:35 lamp-desktop kernel: [    0.000000] Processor #1
Oct 12 17:51:35 lamp-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] disabled)
Oct 12 17:51:35 lamp-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x03] disabled)
Oct 12 17:51:35 lamp-desktop kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
Oct 12 17:51:35 lamp-desktop kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
Oct 12 17:51:35 lamp-desktop kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
Oct 12 17:51:35 lamp-desktop kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] high edge lint[0x1])
Oct 12 17:51:35 lamp-desktop kernel: [    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
Oct 12 17:51:35 lamp-desktop kernel: [    0.000000] IOAPIC[0]: apic_id 4, address 0xfec00000, GSI 0-23
Oct 12 17:51:35 lamp-desktop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Oct 12 17:51:35 lamp-desktop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
Oct 12 17:51:35 lamp-desktop kernel: [    0.000000] Setting APIC routing to flat
Oct 12 17:51:35 lamp-desktop kernel: [    0.000000] ACPI: HPET id: 0x10b9a201 base: 0xfed00000
Oct 12 17:51:35 lamp-desktop kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Oct 12 17:51:35 lamp-desktop kernel: [    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
Oct 12 17:51:35 lamp-desktop kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000f0000
Oct 12 17:51:35 lamp-desktop kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000000f0000 - 0000000000100000
Oct 12 17:51:35 lamp-desktop kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000cfff0000 - 00000000cfff3000
Oct 12 17:51:35 lamp-desktop kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000cfff3000 - 00000000d0000000
Oct 12 17:51:35 lamp-desktop kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000d0000000 - 00000000e0000000
Oct 12 17:51:35 lamp-desktop kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000e0000000 - 00000000f0000000
Oct 12 17:51:35 lamp-desktop kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000f0000000 - 00000000fec00000
Oct 12 17:51:35 lamp-desktop kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000fec00000 - 0000000100000000
Oct 12 17:51:35 lamp-desktop kernel: [    0.000000] Allocating PCI resources starting at d1000000 (gap: d0000000:10000000)
Oct 12 17:51:35 lamp-desktop kernel: [    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs
Oct 12 17:51:35 lamp-desktop kernel: [    0.000000] PERCPU: Allocating 34656 bytes of per cpu data
Oct 12 17:51:35 lamp-desktop kernel: [    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 1030202
Oct 12 17:51:35 lamp-desktop kernel: [    0.000000] Policy zone: Normal
Oct 12 17:51:35 lamp-desktop kernel: [    0.000000] Kernel command line: root=UUID=91f75113-58d1-4256-90e5-6f67389d33e5 ro quiet splash
Oct 12 17:51:35 lamp-desktop kernel: [    0.000000] Initializing CPU#0
Oct 12 17:51:35 lamp-desktop kernel: [    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
Oct 12 17:51:35 lamp-desktop kernel: [    0.000000] TSC calibrated against HPET
Oct 12 17:51:35 lamp-desktop kernel: [   19.645474] Marking TSC unstable due to TSCs unsynchronized
Oct 12 17:51:35 lamp-desktop kernel: [   19.645476] time.c: Detected 2500.218 MHz processor.
Oct 12 17:51:35 lamp-desktop kernel: [   19.647353] Console: colour VGA+ 80x25
Oct 12 17:51:35 lamp-desktop kernel: [   19.647355] console [tty0] enabled
Oct 12 17:51:35 lamp-desktop kernel: [   19.647369] Checking aperture...
Oct 12 17:51:35 lamp-desktop kernel: [   19.647371] CPU 0: aperture @ 4000000 size 32 MB
Oct 12 17:51:35 lamp-desktop kernel: [   19.647373] Aperture too small (32 MB)
Oct 12 17:51:35 lamp-desktop kernel: [   19.657588] No AGP bridge found
Oct 12 17:51:35 lamp-desktop kernel: [   19.657592] Your BIOS doesn't leave a aperture memory hole
Oct 12 17:51:35 lamp-desktop kernel: [   19.657593] Please enable the IOMMU option in the BIOS setup
Oct 12 17:51:35 lamp-desktop kernel: [   19.657595] This costs you 64 MB of RAM
Oct 12 17:51:35 lamp-desktop kernel: [   19.682376] Mapping aperture over 65536 KB of RAM @ 4000000
Oct 12 17:51:35 lamp-desktop kernel: [   19.682382] swsusp: Registered nosave memory region: 0000000004000000 - 0000000008000000
Oct 12 17:51:35 lamp-desktop kernel: [   19.713545] Memory: 4047428k/4980736k available (2494k kernel code, 146424k reserved, 1318k data, 320k init)
Oct 12 17:51:35 lamp-desktop kernel: [   19.713574] SLUB: Genslabs=12, HWalign=64, Order=0-1, MinObjects=4, CPUs=4, Nodes=1
Oct 12 17:51:35 lamp-desktop kernel: [   19.713587] Calibrating delay loop (skipped), using tsc calculated value.. 5000.43 BogoMIPS (lpj=10000872)
Oct 12 17:51:35 lamp-desktop kernel: [   19.713613] Security Framework initialized
Oct 12 17:51:35 lamp-desktop kernel: [   19.713617] SELinux:  Disabled at boot.
Oct 12 17:51:35 lamp-desktop kernel: [   19.713628] AppArmor: AppArmor initialized
Oct 12 17:51:35 lamp-desktop kernel: [   19.713631] Failure registering capabilities with primary security module.
Oct 12 17:51:35 lamp-desktop kernel: [   19.713878] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
Oct 12 17:51:35 lamp-desktop kernel: [   19.716049] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
Oct 12 17:51:35 lamp-desktop kernel: [   19.716991] Mount-cache hash table entries: 256
Oct 12 17:51:35 lamp-desktop kernel: [   19.717098] Initializing cgroup subsys ns
Oct 12 17:51:35 lamp-desktop kernel: [   19.717101] Initializing cgroup subsys cpuacct
Oct 12 17:51:35 lamp-desktop kernel: [   19.717112] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
Oct 12 17:51:35 lamp-desktop kernel: [   19.717114] CPU: L2 Cache: 512K (64 bytes/line)
Oct 12 17:51:35 lamp-desktop kernel: [   19.717116] CPU 0/0 -> Node 0
Oct 12 17:51:35 lamp-desktop kernel: [   19.717117] CPU: Physical Processor ID: 0
Oct 12 17:51:35 lamp-desktop kernel: [   19.717118] CPU: Processor Core ID: 0
Oct 12 17:51:35 lamp-desktop kernel: [   19.717137] SMP alternatives: switching to UP code
Oct 12 17:51:35 lamp-desktop kernel: [   19.717597] Early unpacking initramfs... done
Oct 12 17:51:35 lamp-desktop kernel: [   19.988634] ACPI: Core revision 20070126
Oct 12 17:51:35 lamp-desktop kernel: [   19.988676] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
Oct 12 17:51:35 lamp-desktop kernel: [   20.035631] Using local APIC timer interrupts.
Oct 12 17:51:35 lamp-desktop kernel: [   20.075579] Detected 12.501 MHz APIC timer.
Oct 12 17:51:35 lamp-desktop kernel: [   20.075656] SMP alternatives: switching to SMP code
Oct 12 17:51:35 lamp-desktop kernel: [   20.076015] Booting processor 1/2 APIC 0x1
Oct 12 17:51:35 lamp-desktop kernel: [   20.086501] Initializing CPU#1
Oct 12 17:51:35 lamp-desktop kernel: [   20.163896] Calibrating delay using timer specific routine.. 5000.48 BogoMIPS (lpj=10000964)
Oct 12 17:51:35 lamp-desktop kernel: [   20.163901] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
Oct 12 17:51:35 lamp-desktop kernel: [   20.163903] CPU: L2 Cache: 512K (64 bytes/line)
Oct 12 17:51:35 lamp-desktop kernel: [   20.163905] CPU 1/1 -> Node 0
Oct 12 17:51:35 lamp-desktop kernel: [   20.163906] CPU: Physical Processor ID: 0
Oct 12 17:51:35 lamp-desktop kernel: [   20.163907] CPU: Processor Core ID: 1
Oct 12 17:51:35 lamp-desktop kernel: [   20.163991] AMD Athlon(tm) 64 X2 Dual Core Processor 4800+ stepping 02
Oct 12 17:51:35 lamp-desktop kernel: [   20.163623] Brought up 2 CPUs
Oct 12 17:51:35 lamp-desktop kernel: [   20.163936] net_namespace: 120 bytes
Oct 12 17:51:35 lamp-desktop kernel: [   20.164254] Time: 16:51:20  Date: 10/12/09
Oct 12 17:51:35 lamp-desktop kernel: [   20.164280] NET: Registered protocol family 16
Oct 12 17:51:35 lamp-desktop kernel: [   20.164433] ACPI: bus type pci registered
Oct 12 17:51:35 lamp-desktop kernel: [   20.164492] PCI: Using configuration type 1
Oct 12 17:51:35 lamp-desktop kernel: [   20.170095] ACPI: Interpreter enabled
Oct 12 17:51:35 lamp-desktop kernel: [   20.170100] ACPI: (supports S0 S3 S4 S5)
Oct 12 17:51:35 lamp-desktop kernel: [   20.170117] ACPI: Using IOAPIC for interrupt routing
Oct 12 17:51:35 lamp-desktop kernel: [   20.174168] ACPI: PCI Root Bridge [PCI0] (0000:00)
Oct 12 17:51:35 lamp-desktop kernel: [   20.174350] pci 0000:00:12.0: set SATA to AHCI mode
Oct 12 17:51:35 lamp-desktop kernel: [   20.175239] PCI: Transparent bridge - 0000:00:14.4
Oct 12 17:51:35 lamp-desktop kernel: [   20.196547] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 11) *0, disabled.
Oct 12 17:51:35 lamp-desktop kernel: [   20.196636] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 11) *0, disabled.
Oct 12 17:51:35 lamp-desktop kernel: [   20.196722] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 10 11) *0, disabled.
Oct 12 17:51:35 lamp-desktop kernel: [   20.196808] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 11) *0, disabled.
Oct 12 17:51:35 lamp-desktop kernel: [   20.196893] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11) *0, disabled.
Oct 12 17:51:35 lamp-desktop kernel: [   20.196979] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11) *0, disabled.
Oct 12 17:51:35 lamp-desktop kernel: [   20.197065] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 5 6 7 10 11) *0, disabled.
Oct 12 17:51:35 lamp-desktop kernel: [   20.197151] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 5 6 7 10 11) *0, disabled.
Oct 12 17:51:35 lamp-desktop kernel: [   20.197246] Linux Plug and Play Support v0.97 (c) Adam Belay
Oct 12 17:51:35 lamp-desktop kernel: [   20.197268] pnp: PnP ACPI init
Oct 12 17:51:35 lamp-desktop kernel: [   20.197276] ACPI: bus type pnp registered
Oct 12 17:51:35 lamp-desktop kernel: [   20.199231] pnp: PnP ACPI: found 10 devices
Oct 12 17:51:35 lamp-desktop kernel: [   20.199233] ACPI: ACPI bus type pnp unregistered
Oct 12 17:51:35 lamp-desktop kernel: [   20.199432] PCI: Using ACPI for IRQ routing
Oct 12 17:51:35 lamp-desktop kernel: [   20.199434] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
Oct 12 17:51:35 lamp-desktop kernel: [   20.215399] NET: Registered protocol family 8
Oct 12 17:51:35 lamp-desktop kernel: [   20.215401] NET: Registered protocol family 20
Oct 12 17:51:35 lamp-desktop kernel: [   20.215460] PCI-DMA: Disabling AGP.
Oct 12 17:51:35 lamp-desktop kernel: [   20.215758] PCI-DMA: aperture base @ 4000000 size 65536 KB
Oct 12 17:51:35 lamp-desktop kernel: [   20.215761] PCI-DMA: using GART IOMMU.
Oct 12 17:51:35 lamp-desktop kernel: [   20.215763] PCI-DMA: Reserving 64MB of IOMMU area in the AGP aperture
Oct 12 17:51:35 lamp-desktop kernel: [   20.215915] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
Oct 12 17:51:35 lamp-desktop kernel: [   20.215918] hpet0: 4 32-bit timers, 14318180 Hz
Oct 12 17:51:35 lamp-desktop kernel: [   20.216965] AppArmor: AppArmor Filesystem Enabled
Oct 12 17:51:35 lamp-desktop kernel: [   20.219390] Time: hpet clocksource has been installed.
Oct 12 17:51:35 lamp-desktop kernel: [   20.227392] system 00:01: ioport range 0x4100-0x411f has been reserved
Oct 12 17:51:35 lamp-desktop kernel: [   20.227395] system 00:01: ioport range 0x228-0x22f has been reserved
Oct 12 17:51:35 lamp-desktop kernel: [   20.227397] system 00:01: ioport range 0x40b-0x40b has been reserved
Oct 12 17:51:35 lamp-desktop kernel: [   20.227400] system 00:01: ioport range 0x4d6-0x4d6 has been reserved
Oct 12 17:51:35 lamp-desktop kernel: [   20.227402] system 00:01: ioport range 0xc00-0xc01 has been reserved
Oct 12 17:51:35 lamp-desktop kernel: [   20.227404] system 00:01: ioport range 0xc14-0xc14 has been reserved
Oct 12 17:51:35 lamp-desktop kernel: [   20.227406] system 00:01: ioport range 0xc50-0xc52 has been reserved
Oct 12 17:51:35 lamp-desktop kernel: [   20.227409] system 00:01: ioport range 0xc6c-0xc6d has been reserved
Oct 12 17:51:35 lamp-desktop kernel: [   20.227411] system 00:01: ioport range 0xc6f-0xc6f has been reserved
Oct 12 17:51:35 lamp-desktop kernel: [   20.227413] system 00:01: ioport range 0xcd0-0xcd1 has been reserved
Oct 12 17:51:35 lamp-desktop kernel: [   20.227415] system 00:01: ioport range 0xcd2-0xcd3 has been reserved
Oct 12 17:51:35 lamp-desktop kernel: [   20.227418] system 00:01: ioport range 0xcd4-0xcdf has been reserved
Oct 12 17:51:35 lamp-desktop kernel: [   20.227420] system 00:01: ioport range 0x4000-0x40fe has been reserved
Oct 12 17:51:35 lamp-desktop kernel: [   20.227422] system 00:01: ioport range 0x4210-0x4217 has been reserved
Oct 12 17:51:35 lamp-desktop kernel: [   20.227424] system 00:01: ioport range 0xb10-0xb1f has been reserved
Oct 12 17:51:35 lamp-desktop kernel: [   20.227433] system 00:07: ioport range 0x4d0-0x4d1 has been reserved
Oct 12 17:51:35 lamp-desktop kernel: [   20.227440] system 00:09: iomem range 0xf0000-0xfffff could not be reserved
Oct 12 17:51:35 lamp-desktop kernel: [   20.227443] system 00:09: iomem range 0x0-0x1fffff could not be reserved
Oct 12 17:51:35 lamp-desktop kernel: [   20.227446] system 00:09: iomem range 0xfed00000-0xfed000ff has been reserved
Oct 12 17:51:35 lamp-desktop kernel: [   20.227449] system 00:09: iomem range 0xcfff0000-0xcfffffff could not be reserved
Oct 12 17:51:35 lamp-desktop kernel: [   20.227451] system 00:09: iomem range 0xffff0000-0xffffffff has been reserved
Oct 12 17:51:35 lamp-desktop kernel: [   20.227453] system 00:09: iomem range 0x0-0x9ffff could not be reserved
Oct 12 17:51:35 lamp-desktop kernel: [   20.227456] system 00:09: iomem range 0x100000-0xcffeffff could not be reserved
Oct 12 17:51:35 lamp-desktop kernel: [   20.227458] system 00:09: iomem range 0xfec00000-0xfec00fff has been reserved
Oct 12 17:51:35 lamp-desktop kernel: [   20.227461] system 00:09: iomem range 0xfee00000-0xfee00fff could not be reserved
Oct 12 17:51:35 lamp-desktop kernel: [   20.227463] system 00:09: iomem range 0xfff80000-0xfffeffff has been reserved
Oct 12 17:51:35 lamp-desktop kernel: [   20.227792] PCI: Bridge: 0000:00:02.0
Oct 12 17:51:35 lamp-desktop kernel: [   20.227795]   IO window: d000-dfff
Oct 12 17:51:35 lamp-desktop kernel: [   20.227797]   MEM window: f8000000-fbffffff
Oct 12 17:51:35 lamp-desktop kernel: [   20.227799]   PREFETCH window: d0000000-dfffffff
Oct 12 17:51:35 lamp-desktop kernel: [   20.227802] PCI: Bridge: 0000:00:0a.0
Oct 12 17:51:35 lamp-desktop kernel: [   20.227803]   IO window: e000-efff
Oct 12 17:51:35 lamp-desktop kernel: [   20.227805]   MEM window: fde00000-fdefffff
Oct 12 17:51:35 lamp-desktop kernel: [   20.227807]   PREFETCH window: fdf00000-fdffffff
Oct 12 17:51:35 lamp-desktop kernel: [   20.227809] PCI: Bridge: 0000:00:14.4
Oct 12 17:51:35 lamp-desktop kernel: [   20.227811]   IO window: c000-cfff
Oct 12 17:51:35 lamp-desktop kernel: [   20.227816]   MEM window: fdd00000-fddfffff
Oct 12 17:51:35 lamp-desktop kernel: [   20.227819]   PREFETCH window: fdc00000-fdcfffff
Oct 12 17:51:35 lamp-desktop kernel: [   20.227858] NET: Registered protocol family 2
Oct 12 17:51:35 lamp-desktop kernel: [   20.263417] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
Oct 12 17:51:35 lamp-desktop kernel: [   20.264484] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
Oct 12 17:51:35 lamp-desktop kernel: [   20.268298] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
Oct 12 17:51:35 lamp-desktop kernel: [   20.268787] TCP: Hash tables configured (established 524288 bind 65536)
Oct 12 17:51:35 lamp-desktop kernel: [   20.268790] TCP reno registered
Oct 12 17:51:35 lamp-desktop kernel: [   20.279415] checking if image is initramfs... it is
Oct 12 17:51:35 lamp-desktop kernel: [   20.774333] Freeing initrd memory: 7553k freed
Oct 12 17:51:35 lamp-desktop kernel: [   20.778605] audit: initializing netlink socket (disabled)
Oct 12 17:51:35 lamp-desktop kernel: [   20.778615] audit(1255366280.100:1): initialized
Oct 12 17:51:35 lamp-desktop kernel: [   20.780237] VFS: Disk quotas dquot_6.5.1
Oct 12 17:51:35 lamp-desktop kernel: [   20.780295] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
Oct 12 17:51:35 lamp-desktop kernel: [   20.780397] io scheduler noop registered
Oct 12 17:51:35 lamp-desktop kernel: [   20.780399] io scheduler anticipatory registered
Oct 12 17:51:35 lamp-desktop kernel: [   20.780400] io scheduler deadline registered
Oct 12 17:51:35 lamp-desktop kernel: [   20.780479] io scheduler cfq registered (default)
Oct 12 17:51:35 lamp-desktop kernel: [   20.918963] assign_interrupt_mode Found MSI capability
Oct 12 17:51:35 lamp-desktop kernel: [   20.919059] assign_interrupt_mode Found MSI capability
Oct 12 17:51:35 lamp-desktop kernel: [   20.941602] Real Time Clock Driver v1.12ac
Oct 12 17:51:35 lamp-desktop kernel: [   20.941773] Linux agpgart interface v0.102
Oct 12 17:51:35 lamp-desktop kernel: [   20.941775] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
Oct 12 17:51:35 lamp-desktop kernel: [   20.942658] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
Oct 12 17:51:35 lamp-desktop kernel: [   20.942714] input: Macintosh mouse button emulation as /devices/virtual/input/input0
Oct 12 17:51:35 lamp-desktop kernel: [   20.942822] PNP: No PS/2 controller found. Probing ports directly.
Oct 12 17:51:35 lamp-desktop kernel: [   21.194324] serio: i8042 KBD port at 0x60,0x64 irq 1
Oct 12 17:51:35 lamp-desktop kernel: [   21.206012] mice: PS/2 mouse device common for all mice
Oct 12 17:51:35 lamp-desktop kernel: [   21.206042] cpuidle: using governor ladder
Oct 12 17:51:35 lamp-desktop kernel: [   21.206043] cpuidle: using governor menu
Oct 12 17:51:35 lamp-desktop kernel: [   21.206166] NET: Registered protocol family 1
Oct 12 17:51:35 lamp-desktop kernel: [   21.206247] registered taskstats version 1
Oct 12 17:51:35 lamp-desktop kernel: [   21.206342]   Magic number: 13:960:893
Oct 12 17:51:35 lamp-desktop kernel: [   21.206398]   hash matches device ptyy3
Oct 12 17:51:35 lamp-desktop kernel: [   21.206448] /build/buildd/linux-2.6.24/drivers/rtc/hctosys.c: unable to open rtc device (rtc0)
Oct 12 17:51:35 lamp-desktop kernel: [   21.206451] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Oct 12 17:51:35 lamp-desktop kernel: [   21.206452] EDD information not available.
Oct 12 17:51:35 lamp-desktop kernel: [   21.206458] Freeing unused kernel memory: 320k freed
Oct 12 17:51:35 lamp-desktop kernel: [   21.206804] Write protecting the kernel read-only data: 1036k
Oct 12 17:51:35 lamp-desktop kernel: [   22.395047] fuse init (API version 7.9)
Oct 12 17:51:35 lamp-desktop kernel: [   22.440286] ACPI: Fan [FAN] (on)
Oct 12 17:51:35 lamp-desktop kernel: [   22.444416] ACPI Exception (processor_core-0824): AE_NOT_FOUND, Processor Device is not present [20070126]
Oct 12 17:51:35 lamp-desktop kernel: [   22.444426] ACPI Exception (processor_core-0824): AE_NOT_FOUND, Processor Device is not present [20070126]
Oct 12 17:51:35 lamp-desktop kernel: [   22.847669] ACPI: Thermal Zone [THRM] (37 C)
Oct 12 17:51:35 lamp-desktop kernel: [   22.992164] SCSI subsystem initialized
Oct 12 17:51:35 lamp-desktop kernel: [   23.038193] ACPI: PCI Interrupt 0000:00:12.0[A] -> GSI 22 (level, low) -> IRQ 22
Oct 12 17:51:35 lamp-desktop kernel: [   23.038353] ahci 0000:00:12.0: controller can't do 64bit DMA, forcing 32bit
Oct 12 17:51:35 lamp-desktop kernel: [   23.038359] ahci 0000:00:12.0: controller can't do PMP, turning off CAP_PMP
Oct 12 17:51:35 lamp-desktop kernel: [   23.045366] usbcore: registered new interface driver usbfs
Oct 12 17:51:35 lamp-desktop kernel: [   23.045382] usbcore: registered new interface driver hub
Oct 12 17:51:35 lamp-desktop kernel: [   23.045402] usbcore: registered new device driver usb
Oct 12 17:51:35 lamp-desktop kernel: [   23.129543] Floppy drive(s): fd0 is 1.44M
Oct 12 17:51:35 lamp-desktop kernel: [   23.150035] FDC 0 is a post-1991 82077
Oct 12 17:51:35 lamp-desktop kernel: [   24.038828] ahci 0000:00:12.0: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl SATA mode
Oct 12 17:51:35 lamp-desktop kernel: [   24.038833] ahci 0000:00:12.0: flags: ncq sntf ilck led clo pio 
Oct 12 17:51:35 lamp-desktop kernel: [   24.039659] scsi0 : ahci
Oct 12 17:51:35 lamp-desktop kernel: [   24.039877] scsi1 : ahci
Oct 12 17:51:35 lamp-desktop kernel: [   24.039999] scsi2 : ahci
Oct 12 17:51:35 lamp-desktop kernel: [   24.040113] scsi3 : ahci
Oct 12 17:51:35 lamp-desktop kernel: [   24.040177] ata1: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f100 irq 22
Oct 12 17:51:35 lamp-desktop kernel: [   24.040180] ata2: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f180 irq 22
Oct 12 17:51:35 lamp-desktop kernel: [   24.040184] ata3: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f200 irq 22
Oct 12 17:51:35 lamp-desktop kernel: [   24.040187] ata4: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f280 irq 22
Oct 12 17:51:35 lamp-desktop kernel: [   24.349416] ata1: SATA link down (SStatus 0 SControl 300)
Oct 12 17:51:35 lamp-desktop kernel: [   24.660965] ata2: SATA link down (SStatus 0 SControl 300)
Oct 12 17:51:35 lamp-desktop kernel: [   25.136277] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Oct 12 17:51:35 lamp-desktop kernel: [   25.137324] ata3.00: ATA-7: MAXTOR STM3250310AS, 3.AAC, max UDMA/133
Oct 12 17:51:35 lamp-desktop kernel: [   25.137328] ata3.00: 488397168 sectors, multi 1: LBA48 NCQ (depth 31/32)
Oct 12 17:51:35 lamp-desktop kernel: [   25.138068] ata3.00: configured for UDMA/133
Oct 12 17:51:35 lamp-desktop kernel: [   25.447817] ata4: SATA link down (SStatus 0 SControl 300)
Oct 12 17:51:35 lamp-desktop kernel: [   25.448354] scsi 2:0:0:0: Direct-Access     ATA      MAXTOR STM325031 3.AA PQ: 0 ANSI: 5
Oct 12 17:51:35 lamp-desktop kernel: [   25.449030] ACPI: PCI Interrupt 0000:00:13.0[A] -> GSI 16 (level, low) -> IRQ 16
Oct 12 17:51:35 lamp-desktop kernel: [   25.449173] ohci_hcd 0000:00:13.0: OHCI Host Controller
Oct 12 17:51:35 lamp-desktop kernel: [   25.449397] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 1
Oct 12 17:51:35 lamp-desktop kernel: [   25.449419] ohci_hcd 0000:00:13.0: irq 16, io mem 0xfe02e000
Oct 12 17:51:35 lamp-desktop kernel: [   25.455372] Driver 'sd' needs updating - please use bus_type methods
Oct 12 17:51:35 lamp-desktop kernel: [   25.455445] sd 2:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
Oct 12 17:51:35 lamp-desktop kernel: [   25.455455] sd 2:0:0:0: [sda] Write Protect is off
Oct 12 17:51:35 lamp-desktop kernel: [   25.455470] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Oct 12 17:51:35 lamp-desktop kernel: [   25.455507] sd 2:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
Oct 12 17:51:35 lamp-desktop kernel: [   25.455514] sd 2:0:0:0: [sda] Write Protect is off
Oct 12 17:51:35 lamp-desktop kernel: [   25.455527] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Oct 12 17:51:35 lamp-desktop kernel: [   25.455529]  sda: sda1 sda2 < sda5 >
Oct 12 17:51:35 lamp-desktop kernel: [   25.492471] sd 2:0:0:0: [sda] Attached SCSI disk
Oct 12 17:51:35 lamp-desktop kernel: [   25.495898] sd 2:0:0:0: Attached scsi generic sg0 type 0
Oct 12 17:51:35 lamp-desktop kernel: [   25.508777] usb usb1: configuration #1 chosen from 1 choice
Oct 12 17:51:35 lamp-desktop kernel: [   25.508798] hub 1-0:1.0: USB hub found
Oct 12 17:51:35 lamp-desktop kernel: [   25.508809] hub 1-0:1.0: 2 ports detected
Oct 12 17:51:35 lamp-desktop kernel: [   25.612585] ACPI: PCI Interrupt 0000:00:13.1[B] -> GSI 17 (level, low) -> IRQ 17
Oct 12 17:51:35 lamp-desktop kernel: [   25.612734] ohci_hcd 0000:00:13.1: OHCI Host Controller
Oct 12 17:51:35 lamp-desktop kernel: [   25.612787] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 2
Oct 12 17:51:35 lamp-desktop kernel: [   25.612809] ohci_hcd 0000:00:13.1: irq 17, io mem 0xfe02d000
Oct 12 17:51:35 lamp-desktop kernel: [   25.672516] usb usb2: configuration #1 chosen from 1 choice
Oct 12 17:51:35 lamp-desktop kernel: [   25.672538] hub 2-0:1.0: USB hub found
Oct 12 17:51:35 lamp-desktop kernel: [   25.672548] hub 2-0:1.0: 2 ports detected
Oct 12 17:51:35 lamp-desktop kernel: [   25.775842] ACPI: PCI Interrupt 0000:00:13.2[C] -> GSI 18 (level, low) -> IRQ 18
Oct 12 17:51:35 lamp-desktop kernel: [   25.775995] ohci_hcd 0000:00:13.2: OHCI Host Controller
Oct 12 17:51:35 lamp-desktop kernel: [   25.776044] ohci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 3
Oct 12 17:51:35 lamp-desktop kernel: [   25.776067] ohci_hcd 0000:00:13.2: irq 18, io mem 0xfe02c000
Oct 12 17:51:35 lamp-desktop kernel: [   25.835772] usb usb3: configuration #1 chosen from 1 choice
Oct 12 17:51:35 lamp-desktop kernel: [   25.835793] hub 3-0:1.0: USB hub found
Oct 12 17:51:35 lamp-desktop kernel: [   25.835802] hub 3-0:1.0: 2 ports detected
Oct 12 17:51:35 lamp-desktop kernel: [   25.935588] ACPI: PCI Interrupt 0000:00:13.3[B] -> GSI 17 (level, low) -> IRQ 17
Oct 12 17:51:35 lamp-desktop kernel: [   25.935734] ohci_hcd 0000:00:13.3: OHCI Host Controller
Oct 12 17:51:35 lamp-desktop kernel: [   25.935784] ohci_hcd 0000:00:13.3: new USB bus registered, assigned bus number 4
Oct 12 17:51:35 lamp-desktop kernel: [   25.935800] ohci_hcd 0000:00:13.3: irq 17, io mem 0xfe02b000
Oct 12 17:51:35 lamp-desktop kernel: [   25.995539] usb usb4: configuration #1 chosen from 1 choice
Oct 12 17:51:35 lamp-desktop kernel: [   25.995557] hub 4-0:1.0: USB hub found
Oct 12 17:51:35 lamp-desktop kernel: [   25.995565] hub 4-0:1.0: 2 ports detected
Oct 12 17:51:35 lamp-desktop kernel: [   26.095365] ACPI: PCI Interrupt 0000:00:13.4[C] -> GSI 18 (level, low) -> IRQ 18
Oct 12 17:51:35 lamp-desktop kernel: [   26.095508] ohci_hcd 0000:00:13.4: OHCI Host Controller
Oct 12 17:51:35 lamp-desktop kernel: [   26.095564] ohci_hcd 0000:00:13.4: new USB bus registered, assigned bus number 5
Oct 12 17:51:35 lamp-desktop kernel: [   26.095581] ohci_hcd 0000:00:13.4: irq 18, io mem 0xfe02a000
Oct 12 17:51:35 lamp-desktop kernel: [   26.155298] usb usb5: configuration #1 chosen from 1 choice
Oct 12 17:51:35 lamp-desktop kernel: [   26.155315] hub 5-0:1.0: USB hub found
Oct 12 17:51:35 lamp-desktop kernel: [   26.155323] hub 5-0:1.0: 2 ports detected
Oct 12 17:51:35 lamp-desktop kernel: [   26.255205] ACPI: PCI Interrupt 0000:00:14.1[A] -> GSI 16 (level, low) -> IRQ 16
Oct 12 17:51:35 lamp-desktop kernel: [   26.255309] scsi4 : pata_atiixp
Oct 12 17:51:35 lamp-desktop kernel: [   26.255361] scsi5 : pata_atiixp
Oct 12 17:51:35 lamp-desktop kernel: [   26.256000] ata5: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xf900 irq 14
Oct 12 17:51:35 lamp-desktop kernel: [   26.256002] ata6: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xf908 irq 15
Oct 12 17:51:35 lamp-desktop kernel: [   26.407341] usb 4-2: new full speed USB device using ohci_hcd and address 2
Oct 12 17:51:35 lamp-desktop kernel: [   26.574625] ata5.00: ATAPI: TSSTcorp CDDVDW SH-S202J, SB00, max UDMA/66
Oct 12 17:51:35 lamp-desktop kernel: [   26.623652] usb 4-2: configuration #1 chosen from 1 choice
Oct 12 17:51:35 lamp-desktop kernel: [   26.746342] ata5.00: configured for UDMA/66
Oct 12 17:51:35 lamp-desktop kernel: [   26.902866] scsi 4:0:0:0: CD-ROM            TSSTcorp CDDVDW SH-S202J  SB00 PQ: 0 ANSI: 5
Oct 12 17:51:35 lamp-desktop kernel: [   26.902918] scsi 4:0:0:0: Attached scsi generic sg1 type 5
Oct 12 17:51:35 lamp-desktop kernel: [   26.902551] ACPI: PCI Interrupt 0000:00:13.5[D] -> GSI 19 (level, low) -> IRQ 19
Oct 12 17:51:35 lamp-desktop kernel: [   26.902696] ehci_hcd 0000:00:13.5: EHCI Host Controller
Oct 12 17:51:35 lamp-desktop kernel: [   26.902749] ehci_hcd 0000:00:13.5: new USB bus registered, assigned bus number 6
Oct 12 17:51:35 lamp-desktop kernel: [   26.902788] ehci_hcd 0000:00:13.5: debug port 1
Oct 12 17:51:35 lamp-desktop kernel: [   26.902803] ehci_hcd 0000:00:13.5: irq 19, io mem 0xfe029000
Oct 12 17:51:35 lamp-desktop kernel: [   26.934091] usb 5-1: new full speed USB device using ohci_hcd and address 2
Oct 12 17:51:35 lamp-desktop kernel: [   26.945641] ehci_hcd 0000:00:13.5: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Oct 12 17:51:35 lamp-desktop kernel: [   26.945735] usb usb6: configuration #1 chosen from 1 choice
Oct 12 17:51:35 lamp-desktop kernel: [   26.945754] hub 6-0:1.0: USB hub found
Oct 12 17:51:35 lamp-desktop kernel: [   26.945762] hub 6-0:1.0: 10 ports detected
Oct 12 17:51:35 lamp-desktop kernel: [   27.002512] usb 4-2: USB disconnect, address 2
Oct 12 17:51:35 lamp-desktop kernel: [   27.054592] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
Oct 12 17:51:35 lamp-desktop kernel: [   27.054597] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
Oct 12 17:51:35 lamp-desktop kernel: [   27.080951] Driver 'sr' needs updating - please use bus_type methods
Oct 12 17:51:35 lamp-desktop kernel: [   27.085712] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
Oct 12 17:51:35 lamp-desktop kernel: [   27.085717] Uniform CD-ROM driver Revision: 3.20
Oct 12 17:51:35 lamp-desktop kernel: [   27.229367] Attempting manual resume
Oct 12 17:51:35 lamp-desktop kernel: [   27.261000] EXT3-fs: INFO: recovery required on readonly filesystem.
Oct 12 17:51:35 lamp-desktop kernel: [   27.261004] EXT3-fs: write access will be enabled during recovery.
Oct 12 17:51:35 lamp-desktop kernel: [   27.786872] kjournald starting.  Commit interval 5 seconds
Oct 12 17:51:35 lamp-desktop kernel: [   27.786885] EXT3-fs: sda1: orphan cleanup on readonly fs
Oct 12 17:51:35 lamp-desktop kernel: [   27.894727] EXT3-fs: sda1: 2 orphan inodes deleted
Oct 12 17:51:35 lamp-desktop kernel: [   27.894728] EXT3-fs: recovery complete.
Oct 12 17:51:35 lamp-desktop kernel: [   27.896582] EXT3-fs: mounted filesystem with ordered data mode.
Oct 12 17:51:35 lamp-desktop kernel: [   28.052465] usb 4-2: new full speed USB device using ohci_hcd and address 3
Oct 12 17:51:35 lamp-desktop kernel: [   28.269387] usb 4-2: configuration #1 chosen from 1 choice
Oct 12 17:51:35 lamp-desktop kernel: [   28.584194] usb 5-1: new full speed USB device using ohci_hcd and address 3
Oct 12 17:51:35 lamp-desktop kernel: [   28.796637] usb 5-1: configuration #1 chosen from 1 choice
Oct 12 17:51:35 lamp-desktop kernel: [   28.798578] hub 5-1:1.0: USB hub found
Oct 12 17:51:35 lamp-desktop kernel: [   28.800557] hub 5-1:1.0: 4 ports detected
Oct 12 17:51:35 lamp-desktop kernel: [   29.120113] usb 5-1.1: new low speed USB device using ohci_hcd and address 4
Oct 12 17:51:35 lamp-desktop kernel: [   29.243035] usb 5-1.1: configuration #1 chosen from 1 choice
Oct 12 17:51:35 lamp-desktop kernel: [   32.973713] ip_tables: (C) 2000-2006 Netfilter Core Team
Oct 12 17:51:35 lamp-desktop kernel: [   33.016763] nf_conntrack version 0.5.0 (16384 buckets, 65536 max)
Oct 12 17:51:35 lamp-desktop kernel: [   33.501174] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Oct 12 17:51:35 lamp-desktop kernel: [   33.526649] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Oct 12 17:51:35 lamp-desktop kernel: [   33.570411] input: Power Button (FF) as /devices/virtual/input/input1
Oct 12 17:51:35 lamp-desktop kernel: [   33.600938] ACPI: Power Button (FF) [PWRF]
Oct 12 17:51:35 lamp-desktop kernel: [   33.601004] input: Power Button (CM) as /devices/virtual/input/input2
Oct 12 17:51:35 lamp-desktop kernel: [   33.632887] ACPI: Power Button (CM) [PWRB]
Oct 12 17:51:35 lamp-desktop kernel: [   33.863190] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 18 (level, low) -> IRQ 18
Oct 12 17:51:35 lamp-desktop kernel: [   33.863356] sky2 0000:02:00.0: v1.20 addr 0xfdefc000 irq 18 Yukon-EC Ultra (0xb4) rev 3
Oct 12 17:51:35 lamp-desktop kernel: [   33.863731] sky2 eth0: addr 00:50:8d:be:50:8b
Oct 12 17:51:35 lamp-desktop kernel: [   33.905934] piix4_smbus 0000:00:14.0: Found 0000:00:14.0 device
Oct 12 17:51:35 lamp-desktop kernel: [   34.013357] usblp0: USB Bidirectional printer dev 3 if 0 alt 0 proto 2 vid 0x1A86 pid 0x7584
Oct 12 17:51:35 lamp-desktop kernel: [   34.013389] usbcore: registered new interface driver usblp
Oct 12 17:51:35 lamp-desktop kernel: [   34.145523] input: PC Speaker as /devices/platform/pcspkr/input/input3
Oct 12 17:51:35 lamp-desktop kernel: [   34.181162] usbcore: registered new interface driver hiddev
Oct 12 17:51:35 lamp-desktop kernel: [   34.197231] input: HID 046a:0021 as /devices/pci0000:00/0000:00:13.4/usb5/5-1/5-1.1/5-1.1:1.0/input/input4
Oct 12 17:51:35 lamp-desktop kernel: [   34.220079] input,hidraw0: USB HID v1.11 Keyboard [HID 046a:0021] on usb-0000:00:13.4-1.1
Oct 12 17:51:35 lamp-desktop kernel: [   34.240096] input: HID 046a:0021 as /devices/pci0000:00/0000:00:13.4/usb5/5-1/5-1.1/5-1.1:1.1/input/input5
Oct 12 17:51:35 lamp-desktop kernel: [   34.263999] input,hidraw1: USB HID v1.11 Device [HID 046a:0021] on usb-0000:00:13.4-1.1
Oct 12 17:51:35 lamp-desktop kernel: [   34.264017] usbcore: registered new interface driver usbhid
Oct 12 17:51:35 lamp-desktop kernel: [   34.264020] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
Oct 12 17:51:35 lamp-desktop kernel: [   34.766714] ACPI: PCI Interrupt 0000:00:14.2[A] -> GSI 16 (level, low) -> IRQ 16
Oct 12 17:51:35 lamp-desktop kernel: [   34.789081] hda_codec: Unknown model for ALC883, trying auto-probe from BIOS...
Oct 12 17:51:35 lamp-desktop kernel: [   35.490927] sky2 eth0: enabling interface
Oct 12 17:51:35 lamp-desktop kernel: [   35.925137] lp: driver loaded but no devices found
Oct 12 17:51:35 lamp-desktop kernel: [   36.046486] Adding 9936160k swap on /dev/sda5.  Priority:-1 extents:1 across:9936160k
Oct 12 17:51:35 lamp-desktop kernel: [   37.230191] sky2 eth0: Link is up at 100 Mbps, full duplex, flow control rx
Oct 12 17:51:35 lamp-desktop kernel: [   37.314702] EXT3 FS on sda1, internal journal
Oct 12 17:51:35 lamp-desktop kernel: [   37.322347] NET: Registered protocol family 10
Oct 12 17:51:35 lamp-desktop kernel: [   37.322573] lo: Disabled Privacy Extensions
Oct 12 17:51:35 lamp-desktop kernel: [   39.062213] No dock devices found.
Oct 12 17:51:35 lamp-desktop kernel: [   39.356812] powernow-k8: Found 1 AMD Athlon(tm) 64 X2 Dual Core Processor 4800+ processors (2 cpu cores) (version 2.20.00)
Oct 12 17:51:35 lamp-desktop kernel: [   39.356482] powernow-k8:    0 : fid 0x11 (2500 MHz), vid 0xa
Oct 12 17:51:35 lamp-desktop kernel: [   39.356486] powernow-k8:    1 : fid 0x10 (2400 MHz), vid 0xb
Oct 12 17:51:35 lamp-desktop kernel: [   39.356488] powernow-k8:    2 : fid 0xe (2200 MHz), vid 0xd
Oct 12 17:51:35 lamp-desktop kernel: [   39.356489] powernow-k8:    3 : fid 0xc (2000 MHz), vid 0xf
Oct 12 17:51:35 lamp-desktop kernel: [   39.356491] powernow-k8:    4 : fid 0xa (1800 MHz), vid 0x11
Oct 12 17:51:35 lamp-desktop kernel: [   39.356492] powernow-k8:    5 : fid 0x2 (1000 MHz), vid 0x12
Oct 12 17:51:35 lamp-desktop kernel: [   40.192560] ppdev: user-space parallel port driver
Oct 12 17:51:37 lamp-desktop kernel: [   41.735926] audit(1255366297.333:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5392 profile="/usr/sbin/cupsd" namespace="default"
Oct 12 17:51:37 lamp-desktop dhcdbd: Started up.
Oct 12 17:51:38 lamp-desktop kernel: [   43.010441] usb 5-1.4: new low speed USB device using ohci_hcd and address 5
Oct 12 17:51:38 lamp-desktop kernel: [   43.069745] Clocksource tsc unstable (delta = -80602465 ns)
Oct 12 17:51:38 lamp-desktop kernel: [   43.094634] usb 5-1.4: configuration #1 chosen from 1 choice
Oct 12 17:51:38 lamp-desktop kernel: [   43.100467] input: Logitech USB Optical Mouse as /devices/pci0000:00/0000:00:13.4/usb5/5-1/5-1.4/5-1.4:1.0/input/input6
Oct 12 17:51:38 lamp-desktop kernel: [   43.136657] input,hidraw2: USB HID v1.10 Mouse [Logitech USB Optical Mouse] on usb-0000:00:13.4-1.4
Oct 12 17:51:42 lamp-desktop motion: [0] Processing thread 0 - config file /etc/motion/motion.conf
Oct 12 17:51:42 lamp-desktop motion: [0] Motion 3.2.11 Started
Oct 12 17:51:48 lamp-desktop kernel: [   47.356902] hda-intel: Invalid position buffer, using LPIB read method instead.
lamp@lamp-desktop:~$ 


```

---

