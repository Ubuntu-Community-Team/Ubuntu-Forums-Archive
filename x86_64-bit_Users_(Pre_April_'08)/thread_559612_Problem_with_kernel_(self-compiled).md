---
title: "Problem with kernel (self-compiled)"
date: 2007-09-25
forum: x86 64-bit Users (Pre April '08)
---

### Post by limaunion on 2007-09-25
Hi all

I've recently switched to a new computer (AMD64 4400) and installed Gutsy.

I've always used self-compiled kernels without a glitch but in this case I'm having some problems related to the new hardware, for some reason the SATA disk drive is not been recognized. This is the first time that I try to compile and run a kernel with the new libata code after having switched from an IDE hdd. 

This is the error:
VFS: Cannot open root device "sda1" or unknown-block(0,0)
Please append a correct "root=" boot option
Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)

These are the SCSI/SATA settings defined for my custom kernel (2.6.22.5-CFS-v20.2):
$ egrep -i '^config_(scsi|sata|blk)' .config
CONFIG_BLK_DEV_LOOP=m
CONFIG_BLK_DEV_CRYPTOLOOP=m
CONFIG_BLK_DEV_IDE=m
CONFIG_BLK_DEV_IDEDISK=m
CONFIG_BLK_DEV_IDECD=m
CONFIG_BLK_DEV_IDEACPI=y
CONFIG_BLK_DEV_IDEPCI=y
CONFIG_BLK_DEV_GENERIC=m
CONFIG_BLK_DEV_IDEDMA_PCI=y
CONFIG_BLK_DEV_AMD74XX=m
CONFIG_BLK_DEV_IDEDMA=y
CONFIG_SCSI=y
CONFIG_SCSI_PROC_FS=y
CONFIG_BLK_DEV_SD=y
CONFIG_BLK_DEV_SR=m
CONFIG_SCSI_MULTI_LUN=y
CONFIG_SCSI_WAIT_SCAN=m
CONFIG_SATA_NV=y

All the important SCSI and SATA drivers are compiled into the kernel, not as modules. 

If I run the stock kernel from Gutsy (works fine) I get the following modules loaded:
$ lsmod | egrep -i '(ata|scsi)'
ata_generic 9988 0
sata_nv 24068 3
libata 137904 2 ata_generic,sata_nv
scsi_mod 172728 3 sg,sd_mod,libata

My fstab and grub menues were chenged from UUID to sda due that I'm not using initrd because all the required drivers are inside the kernel:

fstab:
/dev/sda1 / ext3 defaults,errors=remount-ro,noatime 0 1
grub:
kernel /boot/vmlinuz-2.6.22.5-cfs-v20.2.amd64 root=/dev/sda1 ro noapic

lspci:
00:00.0 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a1)
00:01.0 ISA bridge: nVidia Corporation MCP61 LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP61 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP61 USB Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation MCP61 USB Controller (rev a2)
00:04.0 PCI bridge: nVidia Corporation MCP61 PCI bridge (rev a1)
00:05.0 Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP61 IDE (rev a2)
00:07.0 Bridge: nVidia Corporation MCP61 Ethernet (rev a2)
00:08.0 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:09.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
02:00.0 VGA compatible controller: nVidia Corporation Unknown device 016a (rev a1)

dmesg from Gutsy's kernel:
$ dmesg | egrep -i '(sata|scsi)'
[ 16.901509] SCSI subsystem initialized
[ 18.475896] sata_nv 0000:00:08.0: version 3.4
[ 18.476994] scsi0 : sata_nv
[ 18.477240] scsi1 : sata_nv
[ 18.477448] ata1: SATA max UDMA/133 cmd 0x000000000001e400 ctl 0x000000000001e082 bmdma 0x000000000001d880 irq 15
[ 18.477508] ata2: SATA max UDMA/133 cmd 0x000000000001e000 ctl 0x000000000001dc02 bmdma 0x000000000001d888 irq 15
[ 18.947224] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[ 19.303052] ata2: SATA link down (SStatus 0 SControl 300)
[ 19.313432] scsi 0:0:0:0: Direct-Access ATA WDC WD3200AAKS-0 12.0 PQ: 0 ANSI: 5
[ 19.332857] sd 0:0:0:0: [sda] Attached SCSI disk
[ 19.336393] sd 0:0:0:0: Attached scsi generic sg0 type 0

What am i missing ? Is this a kernel problem ? AFAIK the options are the right ones.

Thanks in advance for any help!
JC

---

