---
title: "My server crashed, n00b question on how to begin diagnosing..."
date: 2009-06-20
forum: x86 64-bit Users
---

### Post by dblagbro on 2009-06-20
So I'm playing with Ubuntu for the first time and I've decided that I'd start with server (because I think I enjoy a challenge :-) but alas need help... 

I know to start in my /var/log/messages and just before the crash I see the following but don't know what I'm looking at and how to parse it out and research each entry.  Could someone help?  Thanks in advance.
-d

Jun 20 11:14:22 ubuntu -- MARK --
Jun 20 11:34:22 ubuntu -- MARK --
Jun 20 11:46:19 ubuntu kernel: [ 4446.045741] PGD 191505067 PUD 188943067 PMD 0
Jun 20 11:46:19 ubuntu kernel: [ 4446.045833] CPU 3
Jun 20 11:46:19 ubuntu kernel: [ 4446.045870] Modules linked in: nls_cp437 cifs vmnet vsock(F) vmci vmmon iptable_filter ip_tables x_tables reiserfs parport_pc lp parport loop ipv6 sky2 evdev button shpchp pci_hotplug pcspkr ext3 jbd mbcache sr_mod cdrom sg sd_mod pata_marvell ata_generic usb_storage libusual pata_acpi skge libata floppy megaraid_sas scsi_mod uhci_hcd ehci_hcd usbcore thermal processor fan fbcon tileblit font bitblit softcursor fuse
Jun 20 11:46:19 ubuntu kernel: [ 4446.046253] Pid: 204, comm: pdflush Tainted: GF       2.6.24-23-server #1
Jun 20 11:46:19 ubuntu kernel: [ 4446.046308] RIP: 0010:[page_waitqueue+0x5e/0x80]  [page_waitqueue+0x5e/0x80] page_waitqueue+0x5e/0x80
Jun 20 11:46:19 ubuntu kernel: [ 4446.046396] RSP: 0018:ffff810223d77c50  EFLAGS: 00010246
Jun 20 11:46:19 ubuntu kernel: [ 4446.046442] RAX: 9436c67f1bc0c4b8 RBX: fbf6c67f1bc0c4b8 RCX: 0000000000000040
Jun 20 11:46:19 ubuntu kernel: [ 4446.046495] RDX: 0000000000001800 RSI: 2e00000000000000 RDI: 0000000000000000
Jun 20 11:46:19 ubuntu kernel: [ 4446.046549] RBP: ffff810223d77e80 R08: 7000000000000000 R09: 0000000000000000
Jun 20 11:46:19 ubuntu kernel: [ 4446.046602] R10: 000000000000003f R11: 0000000000000001 R12: 000000000000000b
Jun 20 11:46:19 ubuntu kernel: [ 4446.046655] R13: 0000000000000000 R14: ffff81018814a1a0 R15: 000000000000000e
Jun 20 11:46:19 ubuntu kernel: [ 4446.046708] FS:  0000000000000000(0000) GS:ffff810228001f00(0000) knlGS:0000000000000000
Jun 20 11:46:19 ubuntu kernel: [ 4446.046791] CS:  0010 DS: 0018 ES: 0018 CR0: 000000008005003b
Jun 20 11:46:19 ubuntu kernel: [ 4446.046839] CR2: 0000000000001f90 CR3: 00000001ad098000 CR4: 00000000000006e0
Jun 20 11:46:19 ubuntu kernel: [ 4446.046892] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
Jun 20 11:46:19 ubuntu kernel: [ 4446.046946] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
Jun 20 11:46:19 ubuntu kernel: [ 4446.046999] Process pdflush (pid: 204, threadinfo ffff810223d76000, task ffff810223d68fe0)
Jun 20 11:46:19 ubuntu kernel: [ 4446.047082] Stack:  ffff81022ea0c4b8 ffffffff80285a48 ffff81022ea0c4b8 ffffffff8028d10c
Jun 20 11:46:19 ubuntu kernel: [ 4446.047172]  ffff81018814a1a0 ffffffff8028cbc0 ffff8102234867b8 0000000022c5e4d8
Jun 20 11:46:19 ubuntu kernel: [ 4446.047259]  ffffffffffffffff 00000000802daeaa 000000000000000e 0000000000000000
Jun 20 11:46:19 ubuntu kernel: [ 4446.047317] Call Trace:
Jun 20 11:46:19 ubuntu kernel: [ 4446.047383]  [reiserfs:unlock_page+0x18/0x220] unlock_page+0x18/0x30
Jun 20 11:46:19 ubuntu kernel: [ 4446.047430]  [write_cache_pages+0x16c/0x340] write_cache_pages+0x16c/0x340
Jun 20 11:46:19 ubuntu kernel: [ 4446.047480]  [__writepage+0x0/0x30] __writepage+0x0/0x30
Jun 20 11:46:19 ubuntu kernel: [ 4446.047530]  [do_writepages+0x2b/0x40] do_writepages+0x2b/0x40
Jun 20 11:46:19 ubuntu kernel: [ 4446.047578]  [__writeback_single_inode+0xb0/0x380] __writeback_single_inode+0xb0/0x380
Jun 20 11:46:19 ubuntu kernel: [ 4446.047636]  [reiserfs:reiserfs_flush_old_commits+0x21/0xd0] :reiserfs:reiserfs_flush_old_commits+0x21/0xd0
Jun 20 11:46:19 ubuntu kernel: [ 4446.047719]  [sync_sb_inodes+0x1f9/0x300] sync_sb_inodes+0x1f9/0x300
Jun 20 11:46:19 ubuntu kernel: [ 4446.047768]  [writeback_inodes+0x92/0xd0] writeback_inodes+0x92/0xd0
Jun 20 11:46:19 ubuntu kernel: [ 4446.047817]  [wb_kupdate+0xa6/0x120] wb_kupdate+0xa6/0x120
Jun 20 11:46:19 ubuntu kernel: [ 4446.047865]  [pdflush+0x0/0x230] pdflush+0x0/0x230
Jun 20 11:46:19 ubuntu kernel: [ 4446.047911]  [pdflush+0x0/0x230] pdflush+0x0/0x230
Jun 20 11:46:19 ubuntu kernel: [ 4446.047957]  [pdflush+0x150/0x230] pdflush+0x150/0x230
Jun 20 11:46:19 ubuntu kernel: [ 4446.048003]  [wb_kupdate+0x0/0x120] wb_kupdate+0x0/0x120
Jun 20 11:46:19 ubuntu kernel: [ 4446.048051]  [kthread+0x4b/0x80] kthread+0x4b/0x80
Jun 20 11:46:19 ubuntu kernel: [ 4446.048097]  [child_rip+0xa/0x12] child_rip+0xa/0x12
Jun 20 11:46:19 ubuntu kernel: [ 4446.048145]  [kthread+0x0/0x80] kthread+0x0/0x80
Jun 20 11:46:19 ubuntu kernel: [ 4446.048190]  [child_rip+0x0/0x12] child_rip+0x0/0x12
Jun 20 11:46:19 ubuntu kernel: [ 4446.048236]
Jun 20 11:46:19 ubuntu kernel: [ 4446.048269]
Jun 20 11:46:19 ubuntu kernel: [ 4446.048269] Code: 2b 8a 90 07 00 00 48 01 f8 5b 48 d3 e8 48 8d 04 40 48 c1 e0
Jun 20 11:46:19 ubuntu kernel: [ 4446.048468]  RSP <ffff810223d77c50>
Jun 20 11:46:19 ubuntu kernel: [ 4446.048835] ---[ end trace aec46ff16c9b97c2 ]---

---

### Post by dblagbro on 2009-06-20
still curious about this issue but in the mean time have ran memory test from Ubuntu Server CD and passed.  Since test has been stabile (1.5hrs).

-d

---

### Post by dblagbro on 2009-06-22
OK, crashed again last night, still happening - working on getting the latest log but this is still an active question if anyone can help me 'decode' the /var/log/messages logs.

The system was stabil since Saturday afternoon and crashed Sunday night / Monday early AM.

Now I can't boot it and am looking at a possible re-install - I'd rather know the root-cause before starting another reinstall.

tks,
-d

---

### Post by dblagbro on 2009-06-22
Additional info...  

Since rebooting this AM (had to re-install GRUB), the system has been pretty stabil even with these additions to the /var/log/messages:

Jun 22 14:24:52 ubuntu -- MARK --
Jun 22 14:28:38 ubuntu kernel: [ 2730.243634] vsock: no version for "VMCIDatagram_Send" found: kernel tainted.
Jun 22 14:29:05 ubuntu kernel: [ 2757.248388] device eth0 entered promiscuous mode
Jun 22 14:29:05 ubuntu kernel: [ 2757.248394] audit(1245695345.688:3): dev=eth0 prom=256 old_prom=0 auid=4294967295
Jun 22 14:29:05 ubuntu kernel: [ 2757.248398] bridge-eth0: enabled promiscuous mode
Jun 22 14:29:39 ubuntu kernel: [ 2791.312002] device eth0 left promiscuous mode
Jun 22 14:29:39 ubuntu kernel: [ 2791.312011] audit(1245695379.798:4): dev=eth0 prom=0 old_prom=256 auid=4294967295
Jun 22 14:29:39 ubuntu kernel: [ 2791.312017] bridge-eth0: disabled promiscuous mode
Jun 22 14:29:39 ubuntu kernel: [ 2791.312060] device eth0 entered promiscuous mode
Jun 22 14:29:39 ubuntu kernel: [ 2791.312063] audit(1245695379.798:5): dev=eth0 prom=256 old_prom=0 auid=4294967295
Jun 22 14:29:39 ubuntu kernel: [ 2791.312067] bridge-eth0: enabled promiscuous mode
Jun 22 14:30:03 ubuntu kernel: [ 2815.257664] rtc: lost 3 interrupts
Jun 22 14:33:33 ubuntu kernel: [ 3024.871330] rtc: lost 3 interrupts
Jun 22 14:44:52 ubuntu -- MARK --
Jun 22 15:04:52 ubuntu -- MARK --


I couldn't get a var/log/messages from last night's crash...  perhaps a disk controller problem is indicated then?  Since it couldn't flush the messages about the crash to the disk?????

Please, any help to point me in the right direction would be appreciated.

Tks,
-d

---

