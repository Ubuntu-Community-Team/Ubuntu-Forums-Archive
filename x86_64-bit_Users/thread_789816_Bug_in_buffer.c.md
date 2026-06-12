---
title: "Bug in buffer.c"
date: 2008-05-10
forum: x86 64-bit Users
---

### Post by jimbolaya on 2008-05-10
I'm running x86-64 2.6.20-16-lowlatency on 7.10.  The primary use is a mythtv backend server.  I used to encounter a lot of problems when there was a lot of I/O, like when watching live tv or when it was doing commercial flagging.  Since I've been running 2.6.20-16-lowlatency, it's more informative.  I get the following error:

```

[45088.120241] ------------[ cut here ]------------
[45088.120252] kernel BUG at fs/buffer.c:444!
[45088.120258] invalid opcode: 0000 [1] PREEMPT SMP 
[45088.120267] CPU 0 
[45088.120272] Modules linked in: nfsd exportfs battery cpufreq_userspace cpufreq_stats cpufreq_powersave cpufreq_ondemand cpufreq_conservative ipv6 nfs lockd sunrpc af_packet xfs dm_mod powernow_k8 freq_table lp ide_cd cdrom bt878 snd_intel8x0 snd_ac97_codec xpad ac97_bus snd_usb_audio snd_usb_lib cx88_alsa snd_pcm_oss snd_mixer_oss snd_pcm tuner snd_seq_dummy snd_seq_oss bttv cx8802 cx8800 snd_hwdep cx88xx ir_common snd_mpu401 snd_mpu401_uart i2c_algo_bit video_buf tv
eeprom compat_ioctl32 btcx_risc videodev v4l2_common v4l1_compat snd_seq_midi parport_pc parport i2c_nforce2 i2c_core tsdev psmouse serio_raw k8temp shpchp pci_hotplug evdev snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device analog gameport pcspkr snd soundcore snd_page_alloc ext3 jbd mbcache raid456 md_mod xor usbhid hid forcedeth ehci_hcd ohci_hcd usbcore ide_generic ide_disk sg sd_mod sata_nv ata_generic libata scsi_mod generic amd74xx thermal processor 
fan fbcon tileblit font bitblit softcursor capability commoncap siimage
[45088.120446] Pid: 4311, comm: xfsdatad/0 Not tainted 2.6.20-16-lowlatency #2
[45088.120453] RIP: 0010:[<ffffffff8024a434>]  [<ffffffff8024a434>] end_buffer_async_write+0x14/0x190
[45088.120469] RSP: 0018:ffff8101378c9dd0  EFLAGS: 00010246
[45088.120476] RAX: 0000000000000025 RBX: ffff81003e45ff00 RCX: ffff810001008810
[45088.120484] RDX: ffff810001008810 RSI: 0000000000000001 RDI: ffff81003e45ff68
[45088.120492] RBP: ffff81003e45ff68 R08: 000000000000000c R09: ffff8101378c9d00
[45088.120500] R10: ffff81013c7a0568 R11: 0000000000000001 R12: ffff8101211c8fb0
[45088.120508] R13: 0000000000000213 R14: ffffffff88412500 R15: ffff81013b964800
[45088.120516] FS:  0000000049812950(0000) GS:ffffffff80556000(0000) knlGS:0000000000000000
[45088.120525] CS:  0010 DS: 0018 ES: 0018 CR0: 000000008005003b
[45088.120532] CR2: 00002b4e1dafc000 CR3: 00000000927df000 CR4: 00000000000006e0
[45088.120541] Process xfsdatad/0 (pid: 4311, threadinfo ffff8101378c8000, task ffff81013a19e080)
[45088.120549] Stack:  0000000000000000 0000000000000001 ffff81013a19e080 ffff81012d236860
[45088.120565]  0000000000001658 ffff81003e45ff00 ffff8101211c8f70 ffff8101211c8fb0
[45088.120579]  0000000000000213 ffffffff88412466 ffff81013b9647c0 ffff8101211c8fb8
[45088.120590] Call Trace:
[45088.120629]  [<ffffffff88412466>] :xfs:xfs_destroy_ioend+0x26/0x70
[45088.120642]  [<ffffffff80252e38>] run_workqueue+0xa8/0x160
[45088.120654]  [<ffffffff8024f070>] worker_thread+0x0/0x190
[45088.120662]  [<ffffffff802a7860>] keventd_create_kthread+0x0/0x90
[45088.120670]  [<ffffffff8024f1bb>] worker_thread+0x14b/0x190
[45088.120680]  [<ffffffff80291c50>] default_wake_function+0x0/0x10
[45088.120699]  [<ffffffff8024f070>] worker_thread+0x0/0x190
[45088.120707]  [<ffffffff80234e69>] kthread+0xd9/0x120
[45088.120716]  [<ffffffff802298ef>] schedule_tail+0x3f/0xc0
[45088.120728]  [<ffffffff80264ef8>] child_rip+0xa/0x12
[45088.120737]  [<ffffffff802a7860>] keventd_create_kthread+0x0/0x90
[45088.120755]  [<ffffffff80234d90>] kthread+0x0/0x120
[45088.120764]  [<ffffffff80264eee>] child_rip+0x0/0x12
[45088.120772] 
[45088.120776] 
[45088.120777] Code: 0f 0b eb fe 85 f6 4c 8b 67 10 74 07 90 0f ba 2f 00 eb 4e e8 
[45088.120810] RIP  [<ffffffff8024a434>] end_buffer_async_write+0x14/0x190
[45088.120820]  RSP <ffff8101378c9dd0>
[45088.120922]  


```

I've also used 2.6.22-14-generic with similar results.

Does anyone have this problem with the 2.6.24 kernels?

James

---

