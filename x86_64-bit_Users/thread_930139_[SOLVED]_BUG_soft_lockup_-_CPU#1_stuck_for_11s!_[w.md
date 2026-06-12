---
title: "[SOLVED] BUG: soft lockup - CPU#1 stuck for 11s! [wish8.5:7344]"
date: 2008-09-25
forum: x86 64-bit Users
---

### Post by xanimedes on 2008-09-25
Hi all,

I Ubuntu is normally getting stalled, when checking the syslog I see this.

Sep 25 16:47:36 xanimedes kernel: [  349.076898] BUG: soft lockup - CPU#1 stuck for 11s! [wish8.5:7344]
Sep 25 16:47:36 xanimedes kernel: [  349.076901] CPU 1:
Sep 25 16:47:36 xanimedes kernel: [  349.076902] Modules linked in: binfmt_misc rfcomm l2cap bluetooth tun vboxdrv ppdev cpufreq_powersave cpufreq_conservative cpufreq_userspace cpufreq_stats cpufreq_ondemand freq_table sbs sbshc video output container dock battery iptable_filter ip_tables x_tables aes_x86_64 dm_crypt dm_mod ac lp snd_hda_intel snd_pcm_oss snd_mixer_oss snd_pcm snd_page_alloc snd_hwdep snd_seq_dummy snd_seq_oss ipv6 snd_seq_midi joydev nvidia(P) snd_rawmidi snd_seq_midi_event gspca snd_seq serio_raw tvaudio psmouse snd_timer snd_seq_device bttv ir_common snd compat_ioctl32 i2c_algo_bit videobuf_dma_sg videobuf_core btcx_risc tveeprom button soundcore i2c_nforce2 k8temp videodev v4l2_common v4l1_compat shpchp pci_hotplug evdev pcspkr i2c_core parport_pc parport ext3 jbd mbcache sr_mod cdrom usb_storage sg sd_mod pata_amd usbhid hid libusual ata_generic sata_nv pata_acpi ohci_hcd libata scsi_mod forcedeth ehci_hcd usbcore thermal processor fan fbcon tileblit font bitblit softcursor fuse
Sep 25 16:47:36 xanimedes kernel: [  349.076972] Pid: 7344, comm: wish8.5 Tainted: P        2.6.24-21-generic #1
Sep 25 16:47:36 xanimedes kernel: [  349.076974] RIP: 0010:[flush_tlb_page+0x36/0xa0]  [flush_tlb_page+0x36/0xa0] flush_tlb_page+0x36/0xa0
Sep 25 16:47:36 xanimedes kernel: [  349.076979] RSP: 0018:ffff810118a6d988  EFLAGS: 00000282
Sep 25 16:47:36 xanimedes kernel: [  349.076981] RAX: ffff81010bdc37a0 RBX: 0000000002800000 RCX: ffff81000000f000
Sep 25 16:47:36 xanimedes kernel: [  349.076983] RDX: 0000000000000001 RSI: 0000000002800000 RDI: ffff810118b08f20
Sep 25 16:47:36 xanimedes kernel: [  349.076985] RBP: ffff81010bdc37a0 R08: 0000000002800e18 R09: 00000000000003c4
Sep 25 16:47:36 xanimedes kernel: [  349.076987] R10: 0000000000000000 R11: 0000000000000001 R12: ffff8100be881000
Sep 25 16:47:36 xanimedes kernel: [  349.076990] R13: 0000000100000002 R14: ffffffff00000001 R15: 000000010be40680
Sep 25 16:47:36 xanimedes kernel: [  349.076993] FS:  00007ff05215f6e0(0000) GS:ffff81013c401800(0000) knlGS:00000000f73c5940
Sep 25 16:47:36 xanimedes kernel: [  349.076996] CS:  0010 DS: 0000 ES: 0000 CR0: 000000008005003b
Sep 25 16:47:36 xanimedes kernel: [  349.076998] CR2: 0000000002800000 CR3: 000000011892c000 CR4: 00000000000006e0
Sep 25 16:47:36 xanimedes kernel: [  349.077000] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
Sep 25 16:47:36 xanimedes kernel: [  349.077003] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
Sep 25 16:47:36 xanimedes kernel: [  349.077005]
Sep 25 16:47:36 xanimedes kernel: [  349.077005] Call Trace:
Sep 25 16:47:36 xanimedes kernel: [  349.077010]  [handle_mm_fault+0x2ab/0x7b0] handle_mm_fault+0x2ab/0x7b0
Sep 25 16:47:36 xanimedes kernel: [  349.077013]  [free_compound_page+0x0/0x20] free_compound_page+0x0/0x20
Sep 25 16:47:36 xanimedes kernel: [  349.077023]  [do_page_fault+0x1ab/0x840] do_page_fault+0x1ab/0x840
Sep 25 16:47:36 xanimedes kernel: [  349.077040]  [error_exit+0x0/0x51] error_exit+0x0/0x51
Sep 25 16:47:36 xanimedes kernel: [  349.077046]  [free_compound_page+0x0/0x20] free_compound_page+0x0/0x20
Sep 25 16:47:36 xanimedes kernel: [  349.077054]  [copy_user_generic_string+0x17/0x40] copy_user_generic_string+0x17/0x40
Sep 25 16:47:36 xanimedes kernel: [  349.077059]  [memcpy_toiovec+0x4d/0x70] memcpy_toiovec+0x4d/0x70
Sep 25 16:47:36 xanimedes kernel: [  349.077064]  [unix_stream_recvmsg+0x184/0x5e0] unix_stream_recvmsg+0x184/0x5e0
Sep 25 16:47:36 xanimedes kernel: [  349.077073]  [get_page_from_freelist+0x489/0x6d0] get_page_from_freelist+0x489/0x6d0
Sep 25 16:47:36 xanimedes kernel: [  349.077085]  [sock_aio_read+0x15d/0x170] sock_aio_read+0x15d/0x170
Sep 25 16:47:36 xanimedes kernel: [  349.077099]  [ext3:do_sync_read+0xd9/0xbb0] do_sync_read+0xd9/0x120
Sep 25 16:47:36 xanimedes kernel: [  349.077102]  [vma_adjust+0x149/0x4e0] vma_adjust+0x149/0x4e0
Sep 25 16:47:36 xanimedes kernel: [  349.077109]  [__up_read+0x21/0xb0] __up_read+0x21/0xb0
Sep 25 16:47:36 xanimedes kernel: [  349.077113]  [<ffffffff80253ba0>] autoremove_wake_function+0x0/0x30
Sep 25 16:47:36 xanimedes kernel: [  349.077124]  [do_brk+0x208/0x2c0] do_brk+0x208/0x2c0
Sep 25 16:47:36 xanimedes kernel: [  349.077130]  [vfs_read+0x185/0x190] vfs_read+0x185/0x190
Sep 25 16:47:36 xanimedes kernel: [  349.077135]  [sys_read+0x53/0x90] sys_read+0x53/0x90
Sep 25 16:47:36 xanimedes kernel: [  349.077141]  [system_call+0x7e/0x83] system_call+0x7e/0x83
Sep 25 16:47:36 xanimedes kernel: [  349.077150]

I have to restart the machine. No only with wish, 

Sep 25 15:04:27 xanimedes kernel: [  556.216627] kdeinit4[6942]: segfault at 10 rip 7f73a77ff5d0 rsp 7fffb238f2b0 error 6
Sep 25 15:04:27 xanimedes kernel: [  556.216672] Eeek! page_mapcount(page) went negative! (-1)
Sep 25 15:04:27 xanimedes kernel: [  556.216675]   page pfn = 121514
Sep 25 15:04:27 xanimedes kernel: [  556.216677]   page->flags = 200000000000014
Sep 25 15:04:27 xanimedes kernel: [  556.216679]   page->count = 0
Sep 25 15:04:27 xanimedes kernel: [  556.216681]   page->mapping = 0000000000000000
Sep 25 15:04:27 xanimedes kernel: [  556.216701]   vma->vm_ops = 0x0
Sep 25 15:04:27 xanimedes kernel: [  556.216711] ------------[ cut here ]------------
Sep 25 15:04:27 xanimedes kernel: [  556.216713] kernel BUG at /build/buildd/linux-2.6.24/mm/rmap.c:631!
Sep 25 15:04:27 xanimedes kernel: [  556.216715] invalid opcode: 0000 [1] SMP 
Sep 25 15:04:27 xanimedes kernel: [  556.216718] CPU 1 
Sep 25 15:04:27 xanimedes kernel: [  556.216721] Modules linked in: binfmt_misc rfcomm l2cap bluetooth tun vboxdrv ppdev cpufreq_powersave cpufreq_conservative cpufreq_userspace cpufreq_stats cpufreq_ondemand freq_table sbs sbshc video output container dock battery iptable_filter ip_tables x_tables aes_x86_64 dm_crypt dm_mod ac lp bt878 tvaudio bttv ipv6 joydev ir_common gspca evdev snd_hda_intel nvidia(P) i2c_algo_bit serio_raw compat_ioctl32 snd_pcm_oss snd_mixer_oss videobuf_dma_sg videobuf_core btcx_risc tveeprom psmouse snd_pcm videodev v4l2_common v4l1_compat snd_page_alloc snd_hwdep snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device i2c_nforce2 button snd shpchp i2c_core k8temp pcspkr parport_pc parport soundcore pci_hotplug ext3 jbd mbcache usb_storage sr_mod cdrom sg sd_mod pata_amd usbhid hid libusual ata_generic sata_nv pata_acpi forcedeth libata scsi_mod ehci_hcd ohci_hcd usbcore thermal processor fan fbcon tileblit font bitblit softcursor fuse
Sep 25 15:04:27 xanimedes kernel: [  556.216801] Pid: 6942, comm: kdeinit4 Tainted: P        2.6.24-21-generic #1
Sep 25 15:04:27 xanimedes kernel: [  556.216803] RIP: 0010:[page_remove_rmap+0x11a/0x130]  [page_remove_rmap+0x11a/0x130] page_remove_rmap+0x11a/0x130
Sep 25 15:04:27 xanimedes kernel: [  556.216811] RSP: 0000:ffff810126401bd8  EFLAGS: 00010246
Sep 25 15:04:27 xanimedes kernel: [  556.216813] RAX: 0000000000000000 RBX: ffff810140911c60 RCX: ffffffff803a77a0
Sep 25 15:04:27 xanimedes kernel: [  556.216815] RDX: 00000000ffffffff RSI: 0000000000000000 RDI: ffffffff80584ce4
Sep 25 15:04:27 xanimedes kernel: [  556.216817] RBP: ffff810126649f20 R08: 0000000000000000 R09: 00000000ffffffff
Sep 25 15:04:27 xanimedes kernel: [  556.216819] R10: 0000000000000000 R11: 0000000000000000 R12: 0000000000611000
Sep 25 15:04:27 xanimedes kernel: [  556.216822] R13: ffff810140911c60 R14: 00000000006a6000 R15: 00000000003eefff
Sep 25 15:04:27 xanimedes kernel: [  556.216824] FS:  00007f73aa363780(0000) GS:ffff81013c401800(0000) knlGS:0000000000000000
Sep 25 15:04:27 xanimedes kernel: [  556.216826] CS:  0010 DS: 0000 ES: 0000 CR0: 000000008005003b
Sep 25 15:04:27 xanimedes kernel: [  556.216828] CR2: 0000000000000010 CR3: 0000000126543000 CR4: 00000000000006e0
Sep 25 15:04:27 xanimedes kernel: [  556.216830] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
Sep 25 15:04:27 xanimedes kernel: [  556.216832] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
Sep 25 15:04:27 xanimedes kernel: [  556.216835] Process kdeinit4 (pid: 6942, threadinfo ffff810126400000, task ffff8101265637a0)
Sep 25 15:04:27 xanimedes kernel: [  556.216837] Stack:  0000000000000216 00000000006a6000 ffff810126642088 ffffffff802955d2
Sep 25 15:04:27 xanimedes kernel: [  556.216842]  0000000000000800 ffffffff806297a0 ffff81000102f7b8 00000000006a5fff
Sep 25 15:04:27 xanimedes kernel: [  556.216846]  0000000000000000 ffff810126401cf8 ffffffffffffffff 0000000000000000
Sep 25 15:04:27 xanimedes kernel: [  556.216850] Call Trace:
Sep 25 15:04:27 xanimedes kernel: [  556.216855]  [unmap_vmas+0x4f2/0x7e0] unmap_vmas+0x4f2/0x7e0
Sep 25 15:04:27 xanimedes kernel: [  556.216877]  [exit_mmap+0x78/0x100] exit_mmap+0x78/0x100
Sep 25 15:04:27 xanimedes kernel: [  556.216883]  [mmput+0x26/0xb0] mmput+0x26/0xb0
Sep 25 15:04:27 xanimedes kernel: [  556.216887]  [do_exit+0x1c0/0x950] do_exit+0x1c0/0x950
Sep 25 15:04:27 xanimedes kernel: [  556.216897]  [do_group_exit+0x2c/0x80] do_group_exit+0x2c/0x80
Sep 25 15:04:27 xanimedes kernel: [  556.216902]  [get_signal_to_deliver+0x2f7/0x4b0] get_signal_to_deliver+0x2f7/0x4b0
Sep 25 15:04:27 xanimedes kernel: [  556.216910]  [do_notify_resume+0xc4/0x810] do_notify_resume+0xc4/0x810
Sep 25 15:04:27 xanimedes kernel: [  556.216915]  [force_sig_info+0x9c/0xe0] force_sig_info+0x9c/0xe0
Sep 25 15:04:27 xanimedes kernel: [  556.216922]  [do_page_fault+0x3c1/0x840] do_page_fault+0x3c1/0x840
Sep 25 15:04:27 xanimedes kernel: [  556.216934]  [d_kill+0x48/0x70] d_kill+0x48/0x70
Sep 25 15:04:27 xanimedes kernel: [  556.216939]  [ext3:dput+0xab/0x340] dput+0xab/0x140
Sep 25 15:04:27 xanimedes kernel: [  556.216942]  [__fput+0x150/0x1e0] __fput+0x150/0x1e0
Sep 25 15:04:27 xanimedes kernel: [  556.216950]  [retint_signal+0x3d/0x85] retint_signal+0x3d/0x85
Sep 25 15:04:27 xanimedes kernel: [  556.216965] 
Sep 25 15:04:27 xanimedes kernel: [  556.216966] 
Sep 25 15:04:27 xanimedes kernel: [  556.216966] Code: 0f 0b eb fe 48 8b 53 10 e9 65 ff ff ff 66 0f 1f 84 00 00 00 
Sep 25 15:04:27 xanimedes kernel: [  556.216980] RIP  [page_remove_rmap+0x11a/0x130] page_remove_rmap+0x11a/0x130
Sep 25 15:04:27 xanimedes kernel: [  556.216984]  RSP <ffff810126401bd8>
Sep 25 15:04:27 xanimedes kernel: [  556.216986] ---[ end trace 6234b3ad1ef77084 ]---
Sep 25 15:04:27 xanimedes kernel: [  556.216988] Fixing recursive fault but reboot is needed!
Sep 25 15:04:31 xanimedes kernel: [  560.060084] ooffice[7281]: segfault at 7fff43f71bd7 rip 7fff43f71bd7 rsp 7fff43f71040 error 15
Sep 25 15:04:42 xanimedes kernel: [  571.439508] BUG: soft lockup - CPU#1 stuck for 11s! [ooffice:7272]
Sep 25 15:04:42 xanimedes kernel: [  571.439513] CPU 1:
Sep 25 15:04:42 xanimedes kernel: [  571.439514] Modules linked in: binfmt_misc rfcomm l2cap bluetooth tun vboxdrv ppdev cpufreq_powersave cpufreq_conservative cpufreq_userspace cpufreq_stats cpufreq_ondemand freq_table sbs sbshc video output container dock battery iptable_filter ip_tables x_tables aes_x86_64 dm_crypt dm_mod ac lp bt878 tvaudio bttv ipv6 joydev ir_common gspca evdev snd_hda_intel nvidia(P) i2c_algo_bit serio_raw compat_ioctl32 snd_pcm_oss snd_mixer_oss videobuf_dma_sg videobuf_core btcx_risc tveeprom psmouse snd_pcm videodev v4l2_common v4l1_compat snd_page_alloc snd_hwdep snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device i2c_nforce2 button snd shpchp i2c_core k8temp pcspkr parport_pc parport soundcore pci_hotplug ext3 jbd mbcache usb_storage sr_mod cdrom sg sd_mod pata_amd usbhid hid libusual ata_generic sata_nv pata_acpi forcedeth libata scsi_mod ehci_hcd ohci_hcd usbcore thermal processor fan fbcon tileblit font bitblit softcursor fuse
Sep 25 15:04:42 xanimedes kernel: [  571.439604] Pid: 7272, comm: ooffice Tainted: P      D 2.6.24-21-generic #1
Sep 25 15:04:42 xanimedes kernel: [  571.439607] RIP: 0010:[do_page_fault+0xc0/0x840]  [do_page_fault+0xc0/0x840] do_page_fault+0xc0/0x840
Sep 25 15:04:42 xanimedes kernel: [  571.439615] RSP: 0000:ffff810037885cd8  EFLAGS: 00000246
Sep 25 15:04:42 xanimedes kernel: [  571.439617] RAX: ffffffff80629640 RBX: ffff81010baf4060 RCX: 00007fff43f70fdc
Sep 25 15:04:42 xanimedes kernel: [  571.439620] RDX: ffff810080a06000 RSI: 0000000000000003 RDI: ffff810037885dd8
Sep 25 15:04:42 xanimedes kernel: [  571.439623] RBP: 0000000000000000 R08: ffff810037884000 R09: 0000000000000000
Sep 25 15:04:42 xanimedes kernel: [  571.439625] R10: 0000000000000000 R11: ffffffff80316c10 R12: ffff8100be899b80
Sep 25 15:04:42 xanimedes kernel: [  571.439628] R13: 0000000000000292 R14: 0000000000000010 R15: 0000000000000000
Sep 25 15:04:42 xanimedes kernel: [  571.439631] FS:  00007fa43bf546e0(0000) GS:ffff81013c401800(0000) knlGS:0000000000000000
Sep 25 15:04:42 xanimedes kernel: [  571.439634] CS:  0010 DS: 0000 ES: 0000 CR0: 000000008005003b
Sep 25 15:04:42 xanimedes kernel: [  571.439636] CR2: 00007fff43f70fdc CR3: 00000000378a8000 CR4: 00000000000006e0
Sep 25 15:04:42 xanimedes kernel: [  571.439639] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
Sep 25 15:04:42 xanimedes kernel: [  571.439642] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
Sep 25 15:04:42 xanimedes kernel: [  571.439644] 
Sep 25 15:04:42 xanimedes kernel: [  571.439645] Call Trace:
Sep 25 15:04:42 xanimedes kernel: [  571.439653]  [__alloc_pages+0xaa/0x3f0] __alloc_pages+0xaa/0x3f0
Sep 25 15:04:42 xanimedes kernel: [  571.439663]  [kprobe_flush_task+0x58/0xb0] kprobe_flush_task+0x58/0xb0
Sep 25 15:04:42 xanimedes kernel: [  571.439677]  [error_exit+0x0/0x51] error_exit+0x0/0x51
Sep 25 15:04:42 xanimedes kernel: [  571.439685]  [dummy_task_wait+0x0/0x10] dummy_task_wait+0x0/0x10
Sep 25 15:04:42 xanimedes kernel: [  571.439695]  [ipv6:__put_user_4+0x20/0x30] __put_user_4+0x20/0x30
Sep 25 15:04:42 xanimedes kernel: [  571.439701]  [do_wait+0x814/0xcf0] do_wait+0x814/0xcf0
Sep 25 15:04:42 xanimedes kernel: [  571.439717]  [<ffffffff80233fa0>] default_wake_function+0x0/0x10
Sep 25 15:04:42 xanimedes kernel: [  571.439727]  [system_call+0x7e/0x83] system_call+0x7e/0x83
Sep 25 15:04:42 xanimedes kernel: [  571.439738] 

:confused:

Any Idea what it could be.. I my board faulty???

I am using Linux xanimedes.homelinux.com 2.6.24-21-generic #1 SMP Mon Aug 25 16:57:51 UTC 2008 x86_64 GNU/Linux

[   44.280760] powernow-k8: Found 1 AMD Athlon(tm) 64 X2 Dual Core Processor 4800+ processors (2 cpu cores) (version 2.20.00)
4GB ram and a GeForce7200GS 256mb

Any help will really be appreciated

---

### Post by Sef on 2008-09-26
If you run a Live CD, do you have the same problem?

---

### Post by uniko on 2008-09-26
Can you reproduce the soft lockup? If so, write down the steps and report the bug. 

Something to try in the meanwhile: Try disabling compiz, if you're using it. I see the second entry is for ooffice.

See this bug:  [https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.24/+bug/251048]("https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.24/+bug/251048") might be same issue.

---

### Post by xanimedes on 2008-09-26
> **Sef said:**
> If you run a Live CD, do you have the same problem?

To be truly never lasted on CD more than in the installation process but will do the test.

---

### Post by xanimedes on 2008-09-26
> **uniko said:**
> Can you reproduce the soft lockup? If so, write down the steps and report the bug. 

Something to try in the meanwhile: Try disabling compiz, if you're using it. I see the second entry is for ooffice.

See this bug:  [https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.24/+bug/251048]("https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.24/+bug/251048") might be same issue.

It's on various softwares. The machine just starts to hang until it stalls.. but will take note.

Thnx

---

### Post by xanimedes on 2008-09-30
Reading a little more about my issue and catching and error I say this word AIEE, looked for info and basicly told about disabling APIC LAPIC APCI  in BIOS and un the GRUB.

Did it and well seems stable to me. So I could say it is solved.

Thanks to all.

Now how do I put this ion solved :popcorn:

---

