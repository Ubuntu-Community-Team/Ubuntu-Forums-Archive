---
title: "4GB in x64 Ubuntu?"
date: 2007-07-14
forum: x86 64-bit Users (Pre April '08)
---

### Post by elfstone214 on 2007-07-14
Hi all,

I have been running Ubuntu amd64 with 4GB for a while now and it always recognized 3.9GB RAM but I never thought any of it. However I recently installed Windows XP x64 and noticed it recognized all 4GB RAM. Is there a reason Ubuntu even though it is x64 does not recognize all 4GB of RAM? My video card has 256MB dedicated memory so it should not be taxed out of the RAM.

Thanks!

---

### Post by stmiller on 2007-07-15
Run top, and copy/paste the info about memory, etc. here.

---

### Post by cylon359 on 2007-07-15
dmesg | less

Look for the BIOS-e820 lines- - those indicate what parts of your memory are usable, and other for reserved data (such as ACPI).

windoze is probably just considering all of them as your total memory, even though slightly less is actually usable

---

### Post by jamesford on 2007-07-15
ive got 4 gigs too and it says 3.9, i just figured it had smt to do with the calculations, 1024 and all that

---

### Post by elfstone214 on 2007-07-15
This is part of the output of "dmesg | less" although I don't quite understand what it all means

> [    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000dfee0000 (usable)
[    0.000000]  BIOS-e820: 00000000dfee0000 - 00000000dfee3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000dfee3000 - 00000000dfef0000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000dfef0000 - 00000000dff00000 (reserved)
[    0.000000]  BIOS-e820: 00000000f0000000 - 00000000f4000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 0000000120000000 (usable)
[    0.000000] Entering add_active_range(0, 0, 159) 0 entries of 3200 used
[    0.000000] Entering add_active_range(0, 256, 917216) 1 entries of 3200 used
[    0.000000] Entering add_active_range(0, 1048576, 1179648) 2 entries of 3200 used
[    0.000000] end_pfn_map = 1179648
[    0.000000] DMI 2.4 present.
[    0.000000] ACPI: RSDP (v000 GBT                                   ) @ 0x00000000000f6f10
[    0.000000] ACPI: RSDT (v001 GBT    GBTUACPI 0x42302e31 GBTU 0x01010101) @ 0x00000000dfee3040
[    0.000000] ACPI: FADT (v001 GBT    GBTUACPI 0x42302e31 GBTU 0x01010101) @ 0x00000000dfee30c0
[    0.000000] ACPI: HPET (v001 GBT    GBTUACPI 0x42302e31 GBTU 0x00000098) @ 0x00000000dfee7d80
[    0.000000] ACPI: MCFG (v001 GBT    GBTUACPI 0x42302e31 GBTU 0x01010101) @ 0x00000000dfee7e00
[    0.000000] ACPI: MADT (v001 GBT    GBTUACPI 0x42302e31 GBTU 0x01010101) @ 0x00000000dfee7c80
[    0.000000] ACPI: DSDT (v001 GBT    GBTUACPI 0x00001000 MSFT 0x0100000c) @ 0x0000000000000000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-0000000120000000
[    0.000000] Entering add_active_range(0, 0, 159) 0 entries of 3200 used
[    0.000000] Entering add_active_range(0, 256, 917216) 1 entries of 3200 used
[    0.000000] Entering add_active_range(0, 1048576, 1179648) 2 entries of 3200 used
[    0.000000] Bootmem setup node 0 0000000000000000-0000000120000000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   DMA32        4096 ->  1048576
[    0.000000]   Normal    1048576 ->  1179648
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0:        0 ->      159
[    0.000000]     0:      256 ->   917216
[    0.000000]     0:  1048576 ->  1179648
[    0.000000] On node 0 totalpages: 1048191
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 1089 pages reserved
[    0.000000]   DMA zone: 2854 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 14280 pages used for memmap
[    0.000000]   DMA32 zone: 898840 pages, LIFO batch:31
[    0.000000]   Normal zone: 1792 pages used for memmap
[    0.000000]   Normal zone: 129280 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 (Bootup-CPU)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)


---

### Post by cylon359 on 2007-07-16
[ 0.000000] BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[ 0.000000] BIOS-e820: 0000000000100000 - 00000000dfee0000 (usable)
[ 0.000000] BIOS-e820: 0000000100000000 - 0000000120000000 (usable)

That works out to 3.99 GB, so when it says 3.9 it is likely just truncating.

---

### Post by elfstone214 on 2007-07-16
> **cylon359 said:**
> [ 0.000000] BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[ 0.000000] BIOS-e820: 0000000000100000 - 00000000dfee0000 (usable)
[ 0.000000] BIOS-e820: 0000000100000000 - 0000000120000000 (usable)

That works out to 3.99 GB, so when it says 3.9 it is likely just truncating.

cool thanks cylon!

---

