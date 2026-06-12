---
title: "Unable to handle kernel paging request at..."
date: 2008-04-11
forum: x86 64-bit Users (Pre April '08)
---

### Post by Sewi79 on 2008-04-11
Dear forum,

I'm using Linux since 1997 and ubuntu for some years (started at v5, I think).
I'm trying my first 64bit system (server) now.

Everything seems to be fine, but after some time (minutes up to multiple hours) OOPS's occur:

[ 8975.139361] Unable to handle kernel paging request at ffffffff88e69558 RIP: 
[ 8975.139404]  [<ffffffff88248431>] :xfs:xfs_vn_permission+0x11/0x20
[ 8975.139509] PGD 203067 PUD 205063 PMD 0 
[ 8975.139594] Oops: 0000 [1] SMP 
[ 8975.139660] CPU 0 
[ 8975.139708] Modules linked in: nls_cp437 isofs udf sbp2 parport_pc lp parport loop ipv6 sr_mod cdrom psmouse pcspkr e1000_ich9 heci shpchp pci_hotplug serio_raw intel_agp evdev xfs sg sd_mod usb_storage ide_core libusual ohci1394 ieee1394 pata_jmicron ahci ehci_hcd uhci_hcd usbcore ata_generic libata scsi_mod raid10 raid456 xor raid1 raid0 multipath linear md_mod thermal processor fan fuse apparmor commoncap
[ 8975.140691] Pid: 10259, comm: dpkg Not tainted 2.6.22-14-server #1
[ 8975.140731] RIP: 0010:[<ffffffff88248431>]  [<ffffffff88248431>] :xfs:xfs_vn_permission+0x11/0x20
[ 8975.140814] RSP: 0018:ffff8100c0dbdcf8  EFLAGS: 00010246
[ 8975.140852] RAX: ffffffff88e69500 RBX: ffff8100bfe102a8 RCX: 0000000000000117
[ 8975.140893] RDX: 0000000000000000 RSI: 0000000000000040 RDI: ffff8100bfe0b700
[ 8975.140934] RBP: 0000000000000001 R08: 0000000000000027 R09: 6573656d616e2f61
[ 8975.140975] R10: 000000000000004b R11: 0000000000000000 R12: ffff8100c0dbdec8
[ 8975.141016] R13: ffff8100c0dbdec8 R14: ffff8100bf8f4000 R15: 0000000000f66aa0
[ 8975.141058] FS:  00002ae4341306e0(0000) GS:ffffffff80574000(0000) knlGS:0000000000000000
[ 8975.141112] CS:  0010 DS: 0000 ES: 0000 CR0: 000000008005003b
[ 8975.141151] CR2: ffffffff88e69558 CR3: 00000000c6c11000 CR4: 00000000000006e0
[ 8975.141192] Process dpkg (pid: 10259, threadinfo ffff8100c0dbc000, task ffff810124fba000)
[ 8975.141246] Stack:  ffff8100c0dbdd58 ffffffff802a1b21 ffff8100bf8f4013 ffff8100bfe102a8
[ 8975.141383]  00000000000041ed ffffffff802a373f 0000000100000000 0000001000000000
[ 8975.141502]  ffffffff806335e0 ffffffff80273bf7 0000000000000049 ffff81000000fe68
[ 8975.141592] Call Trace:
[ 8975.141656]  [<ffffffff802a1b21>] permission+0x71/0x140
[ 8975.141695]  [<ffffffff802a373f>] __link_path_walk+0x7f/0xed0
[ 8975.141735]  [<ffffffff80273bf7>] __alloc_pages+0x67/0x340
[ 8975.141776]  [<ffffffff802a45ea>] link_path_walk+0x5a/0xf0
[ 8975.141815]  [<ffffffff80299d11>] generic_file_llseek+0x61/0xc0
[ 8975.141855]  [<ffffffff80299f22>] sys_lseek+0x72/0x90
[ 8975.141894]  [<ffffffff802a48cc>] do_path_lookup+0xbc/0x230
[ 8975.141933]  [<ffffffff802a31a5>] getname+0xf5/0x220
[ 8975.141972]  [<ffffffff802a5045>] do_rmdir+0x55/0x130
[ 8975.142011]  [<ffffffff80299d11>] generic_file_llseek+0x61/0xc0
[ 8975.142050]  [<ffffffff80299f22>] sys_lseek+0x72/0x90
[ 8975.142089]  [<ffffffff80209e8e>] system_call+0x7e/0x83
[ 8975.142128] 
[ 8975.142159] 
[ 8975.142159] Code: ff 50 58 48 83 c4 08 f7 d8 c3 0f 1f 44 00 00 41 54 55 48 89 
[ 8975.142583] RIP  [<ffffffff88248431>] :xfs:xfs_vn_permission+0x11/0x20
[ 8975.142650]  RSP <ffff8100c0dbdcf8>
[ 8975.142684] CR2: ffffffff88e69558

Multiple (seems to be random) tasks are affected and usually the first oops is followed by some others soon. The system is unstable from now on and some times even won't shut down. A simple reboot solves this problem for some time.

System configuration:
Asus P5E VM (with Intel e1000 & JMicron controller)
Intel Core2Duo E8200 6MB Cache
2x2GB DDR2 800
1GB IDE-Flash (pIDE)
3x500GB SATA HDD
MD RAID5

Kernel: Ubuntu 2.6.22-14-amd64-server (installed by Ubuntu 7.10) and Ubuntu 2.6.22-52-amd64-server (by apt-get upgrade).

Debian amd64 seems to be stable but kernel version 2.6.18 (this is what debian calls "current") doesn't support the e1000 or SATA controller.

The OOPS's occur when using the raid as rootfs and the flash for /boot and also when using the flash as rootfs without mounting the raid.

I'll try out Ubuntu i386 during the weekend if nobody knows any hints.

Thank you all,
Sebastian

---

### Post by Marabu on 2008-04-11
Looks like a BUG in the xfs kernel module to me. Maybe the inode passed to xfs_vn_permission is not a member of bhv_vnode_t... But it't only a guess...

---

### Post by Sewi79 on 2008-04-13
Some updates:

After some (unsuccessful) tests with different Ubuntu versions, Debian and CentOS, I tried a full reinstall with Ubuntu 7.10 32bit today. I even set up the RAID5 with a different size for the phy partitions to force a complete rebuild.

I used Ext2 for all partions (root and boot). It took some time, but I also got the kernel panics. After the reboot I gut the next panic during the first few percent of the fsck. Next reboot, other kernel, same result.

It doesn't seem to be a x64 problem at all, but the board seems to be the reason of the problems. I'm currently looking for a new one. I think, either the Biostar P35D2-A7 (already working for some month in another server) or the Tyan Toledo q35T (S5220) (should work even if the CPU is not listed in the supported-CPU-list) will make it.

Thank you for looking at the problem.

Best Regards,
Sebastian Willing

---

