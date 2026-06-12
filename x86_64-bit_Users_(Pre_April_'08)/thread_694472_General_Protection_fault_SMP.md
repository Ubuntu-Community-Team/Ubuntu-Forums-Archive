---
title: "General Protection fault SMP"
date: 2008-02-12
forum: x86 64-bit Users (Pre April '08)
---

### Post by lynwode on 2008-02-12
Guys,
When copying data via Samba I get a GPF. I have no idea of where start so any help would be appreciated. below is the output from the syslog
Cheers,
Tim.

Feb 10 09:45:58 homer kernel: [489896.514089] general protection fault: 0000 [1] SMP
Feb 10 09:45:58 homer kernel: [489896.514178] CPU 0
Feb 10 09:45:58 homer kernel: [489896.514237] Modules linked in: sony_acpi tc1100_wmi pcc_acpi dev_acpi battery container sbs ac i2c_ec dock video asus_acpi backlight button ipv6 sbp2 lp snd_hda_intel af_packet snd_hda_codec snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device parport_pc snd soundcore psmouse pcspkr parport serio_raw snd_page_alloc k8temp i2c_nforce2 i2c_core tsdev evdev ext3 jbd mbcache sg ide_cd cdrom sd_mod ehci_hcd ohci_hcd ohci1394 usbcore forcedeth floppy amd74xx ieee1394 sata_nv ata_generic libata scsi_mod generic raid456 md_mod xor thermal processor fan fbcon tileblit font bitblit softcursor vesafb cfbcopyarea cfbimgblt cfbfillrect capability commoncap
Feb 10 09:45:58 homer kernel: [489896.516214] Pid: 206, comm: pdflush Not tainted 2.6.20-15-server #2
Feb 10 09:45:58 homer kernel: [489896.516261] RIP: 0010:[find_get_pages_tag+82/144]  [find_get_pages_tag+82/144] find_get_pages_tag+0x52/0x90
Feb 10 09:45:58 homer kernel: [489896.516353] RSP: 0018:ffff810037f03bf0  EFLAGS: 00010002
Feb 10 09:45:58 homer kernel: [489896.516400] RAX: 000000007eefd640 RBX: 0000000000000000 RCX: 000000000000000d
Feb 10 09:45:58 homer kernel: [489896.516466] RDX: 010000000000082c RSI: ffff81002ffa4b08 RDI: 000000000000000e
Feb 10 09:45:58 homer kernel: [489896.516530] RBP: ffff810037f03c70 R08: 000000000000000e R09: 000000000000001b
Feb 10 09:45:58 homer kernel: [489896.516594] R10: ffff81007eefd678 R11: 000000000000000e R12: 000000000000000e
Feb 10 09:45:58 homer kernel: [489896.516659] R13: ffff81006e424518 R14: ffff810037f03ce8 R15: 000000000000000e
Feb 10 09:45:58 homer kernel: [489896.516723] FS:  00002b5f9907b210(0000) GS:ffffffff80562000(0000) knlGS:0000000000000000
Feb 10 09:45:58 homer kernel: [489896.516789] CS:  0010 DS: 0018 ES: 0018 CR0: 000000008005003b
Feb 10 09:45:58 homer kernel: [489896.516835] CR2: 0000000000521100 CR3: 0000000069c6e000 CR4: 00000000000006e0
Feb 10 09:45:58 homer kernel: [489896.516900] Process pdflush (pid: 206, threadinfo ffff810037f02000, task ffff81007c711040)
Feb 10 09:45:58 homer kernel: [489896.516966] Stack:  ffff810037f03c60 0000000000000000 ffff810037f03e40 ffff81006e424518
Feb 10 09:45:58 homer kernel: [489896.517138]  0000000000000000 ffffffff80249f2a 0000000000000001 ffffffff802c341e
Feb 10 09:45:58 homer kernel: [489896.517289]  0000000000000000 ffff81007ce727f0 0000000000000000 ffffffff8822dc90
Feb 10 09:45:58 homer kernel: [489896.517402] Call Trace:
Feb 10 09:45:58 homer kernel: [489896.517482]  [pagevec_lookup_tag+26/48] pagevec_lookup_tag+0x1a/0x30
Feb 10 09:45:58 homer kernel: [489896.517535]  [generic_writepages+702/800] generic_writepages+0x2be/0x320
Feb 10 09:45:58 homer kernel: [489896.517597]  [_end+129543436/2130038908] :ext3:ext3_ordered_writepage+0x0/0x190
Feb 10 09:45:58 homer kernel: [489896.517666]  [do_writepages+39/64] do_writepages+0x27/0x40
Feb 10 09:45:58 homer kernel: [489896.517717]  [__writeback_single_inode+470/912] __writeback_single_inode+0x1d6/0x390
Feb 10 09:45:58 homer kernel: [489896.517778]  [sync_sb_inodes+478/704] sync_sb_inodes+0x1de/0x2c0
Feb 10 09:45:58 homer kernel: [489896.517830]  [writeback_inodes+147/240] writeback_inodes+0x93/0xf0
Feb 10 09:45:58 homer kernel: [489896.517881]  [pdflush+0/512] pdflush+0x0/0x200
Feb 10 09:45:58 homer kernel: [489896.517929]  [background_writeout+146/208] background_writeout+0x92/0xd0
Feb 10 09:45:58 homer kernel: [489896.517987]  [pdflush+0/512] pdflush+0x0/0x200
Feb 10 09:45:58 homer kernel: [489896.518034]  [keventd_create_kthread+0/144] keventd_create_kthread+0x0/0x90
Feb 10 09:45:58 homer kernel: [489896.518082]  [pdflush+340/512] pdflush+0x154/0x200
Feb 10 09:45:58 homer kernel: [489896.518130]  [background_writeout+0/208] background_writeout+0x0/0xd0
Feb 10 09:45:58 homer kernel: [489896.518181]  [kthread+219/288] kthread+0xdb/0x120
Feb 10 09:45:58 homer kernel: [489896.518234]  [child_rip+10/18] child_rip+0xa/0x12
Feb 10 09:45:58 homer kernel: [489896.518282]  [keventd_create_kthread+0/144] keventd_create_kthread+0x0/0x90
Feb 10 09:45:58 homer kernel: [489896.518335]  [physflat_send_IPI_mask+0/128] physflat_send_IPI_mask+0x0/0x80
Feb 10 09:45:58 homer kernel: [489896.518388]  [kthread+0/288] kthread+0x0/0x120
Feb 10 09:45:58 homer kernel: [489896.518437]  [child_rip+0/18] child_rip+0x0/0x12
Feb 10 09:45:58 homer kernel: [489896.518485]
Feb 10 09:45:58 homer kernel: [489896.518522]
Feb 10 09:45:58 homer kernel: [489896.518523] Code: f0 ff 42 08 83 c1 01 39 cf 75 e3 8d 47 ff 48 8b 44 c5 00 48
Feb 10 09:45:58 homer kernel: [489896.519055] RIP  [find_get_pages_tag+82/144] find_get_pages_tag+0x52/0x90

---

### Post by lynwode on 2008-02-12
Anyone?

---

### Post by Yellow Pasque on 2008-02-12
I did a quick search on the error message and saw some other people with various flavors of Linux having the same problem. Curiously, all were running 64-bit. This might be one of those times when it's worth running a 32-bit install. If you could do the Samba stuff from a LiveCD, that would be even better, as you wouldn't have to install anything.

---

### Post by medya on 2008-06-21
I have the same problem, i posted mine here
[http://ubuntuforums.org/showthread.php?p=5231541#post5231541](http://ubuntuforums.org/showthread.php?p=5231541#post5231541)

I also 64bit inter core2 ,and the error happens when I connect to internet by my dial up modem.

---

