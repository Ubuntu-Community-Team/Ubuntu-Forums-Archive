---
title: "[SOLVED] How to get rid of NOAPIC in HP notebooks?"
date: 2006-10-27
forum: x86 64-bit Users (Pre April '08)
---

### Post by beneedict on 2006-10-27
Hi!
I am running a HP Compaq nx6325 notebook with AMD TL-52 X2 in noapic mode.
Is there any way to work around noapic? Since I have read, that noapic makes the computer run on one processor only? 

edit: was now confirmed by a dmesg output

> [    0.000000] Aperture from northbridge cpu 0 too small (32 MB)
[    0.000000] No AGP bridge found
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] Built 1 zonelists
[    0.000000] Kernel command line: root=/dev/sda2 ro quiet splash noapic nolapic
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
[    0.000000] Disabling vsyscall due to use of PM timer
[    0.000000] time.c: Using 3.579545 MHz WALL PM GTOD PM timer.
[    0.000000] time.c: Detected 1596.031 MHz processor.
[   15.852261] Console: colour VGA+ 80x25
[   15.853115] Dentry cache hash table entries: 131072 (order: 8, 1048576 bytes)
[   15.854455] Inode-cache hash table entries: 65536 (order: 7, 524288 bytes)
[   15.867091] Memory: 891616k/917312k available (2129k kernel code, 25308k reserved, 1424k data, 188k init)
[   15.945274] Calibrating delay using timer specific routine.. 3196.05 BogoMIPS (lpj=6392101)
[   15.945342] Security Framework v1.0.0 initialized
[   15.945349] SELinux:  Disabled at boot.
[   15.945376] Mount-cache hash table entries: 256
[   15.945549] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   15.945553] CPU: L2 Cache: 512K (64 bytes/line)
[   15.945556] CPU 0/0(2) -> Node 0 -> Core 0
[   15.945578] SMP alternatives: switching to UP code
[   15.945888] checking if image is initramfs... it is
[   16.557455] Freeing initrd memory: 5673k freed
[   16.562000] ACPI: Core revision 20060707
[   16.562552] ACPI: Looking for DSDT ... not found!
[   16.600577] SMP motherboard not detected.
[   16.600583] Apic disabled
[   16.600585] Local APIC not detected. Using dummy APIC emulation.
[   16.600588] SMP disabled
[   16.600650] Brought up 1 CPUs
[   16.600660] testing NMI watchdog ... CPU#0: NMI appears to be stuck (0->0)!
[   16.640732] migration_cost=0


Most things seemed to work fine without NOAPIC (including the second CPU) but when I installed the fglrx driver for the ATI X1150 Chipset the xserver crashed without noapic.


Thank you,
Benedikt

---

### Post by beneedict on 2007-07-25
New Firmware and Feisty did the trick!!!

---

