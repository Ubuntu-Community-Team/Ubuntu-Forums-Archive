---
title: "tvtime, amd64, and the bttv driver (kernel dump)"
date: 2005-12-04
forum: x86 64-bit Users (Pre April '08)
---

### Post by jesterfred on 2005-12-04
I have an amd64 based system running Ubuntu 5.10 and can't use the tvtime television viewing application against the bttv driver.  If I install the x86 version of Ubuntu, I have no problems.  (Perhaps a buffer sizing problem?)

When I start tvtime on my amd64 system, I receive the following kernel dump:

> Dec  4 07:11:09 localhost kernel: [32896.283874] bttv0: PLL can sleep, using XTAL (28636363).
Dec  4 07:11:09 localhost kernel: [32896.412624] PGD 0
Dec  4 07:11:09 localhost kernel: [32896.412628] CPU 0
Dec  4 07:11:09 localhost kernel: [32896.412630] Modules linked in: nfs lockd sunrpc nls_utf8 nls_cp437 vfat fat vmnet vmmon rfcomm l2cap bluetooth powernow_k8 cpufreq_userspace cpufreq_stats freq_table cpufreq_powersave cpufreq_ondemand cpufreq_conservative autofs4 nvidia video tc1100_wmi sony_acpi pcc_acpi hotkey dev_acpi i2c_acpi_ec button battery container ac ipv6 af_packet floppy pcspkr tsdev usbhid usblp quickcam snd_seq_dummy snd_seq_oss snd_seq_midi snd_seq_midi_event snd_seq snd_via82xx gameport snd_ac97_codec snd_pcm_oss snd_mixer_oss snd_pcm snd_timer snd_page_alloc snd_mpu401_uart snd_rawmidi snd_seq_device snd soundcore i2c_viapro bt878 tuner bttv video_buf firmware_class i2c_algo_bit v4l2_common btcx_risc tveeprom i2c_core videodev ohci1394 evdev sr_mod sbp2 ieee1394 rtc psmouse mousedev parport_pc lp parport md ext3 jbd mbcache dm_mod thermal processor fan sd_mod usb_storage ehci_hcd uhci_hcd sata_via libata scsi_mod via_velocity crc_ccitt ide_cd cdrom ide_generic via82cxxx ide_core unix vesafb capa
Dec  4 07:11:09 localhost kernel: ility commoncap vga16fb vgastate softcursor cfbimgblt cfbfillrect cfbcopyarea fbcon tileblit font bitblit
Dec  4 07:11:09 localhost kernel: [32896.412673] Pid: 26326, comm: tvtime Tainted: P      2.6.12-10-amd64-k8
Dec  4 07:11:09 localhost kernel: [32896.412677] RIP: 0010:[sync_single+36/96] <ffffffff8011c8d4>{sync_single+36}
Dec  4 07:11:09 localhost kernel: [32896.412683] RSP: 0018:ffff81016b9ddae8  EFLAGS: 00010246
Dec  4 07:11:09 localhost kernel: [32896.412687] RAX: ffffffffe00009c2 RBX: ffff81016214c040 RCX: 0000000000000002
Dec  4 07:11:09 localhost kernel: [32896.412691] RDX: ffff810009045000 RSI: 0000000000001000 RDI: ffff81017f7bf070
Dec  4 07:11:09 localhost kernel: [32896.412695] RBP: 0000000000000002 R08: 0000000007516000 R09: ffffffff88228cd0
Dec  4 07:11:09 localhost kernel: [32896.412697] R10: 0000000000000000 R11: 0000000000000001 R12: 00000000000000a9
Dec  4 07:11:09 localhost kernel: [32896.412701] R13: 0000000000000002 R14: 00007f0000000000 R15: 0000000080000000
Dec  4 07:11:09 localhost kernel: [32896.412705] FS:  00002aaaac4c2900(0000) GS:ffffffff80403940(0000) knlGS:000000005556db80
Dec  4 07:11:09 localhost kernel: [32896.412709] CS:  0010 DS: 0000 ES: 0000 CR0: 000000008005003b
Dec  4 07:11:09 localhost kernel: [32896.412712] CR2: ffff80ff09049e10 CR3: 00000001700cb000 CR4: 00000000000006e0
Dec  4 07:11:09 localhost kernel: [32896.412717] Process tvtime (pid: 26326, threadinfo ffff81016b9dc000, task ffff81016200eb60)
Dec  4 07:11:09 localhost kernel: [32896.412719] Stack: 0000000000000000 ffffffff8011ca8b ffff81017f7bf070 0000000000000002
Dec  4 07:11:09 localhost kernel: [32896.412724]        ffff81017f7bf070 00000000000000a9 ffff81016214c000 0000000000000000
Dec  4 07:11:09 localhost kernel: [32896.412729]        ffff81016b9dde48 ffffffff8821d68c
Dec  4 07:11:09 localhost kernel: [32896.412733] Call Trace:<ffffffff8011ca8b>{swiotlb_sync_sg_for_cpu+171} <ffffffff8821d68c>{:video_buf:videobuf_dma_pci_sync+172}
Dec  4 07:11:09 localhost kernel: [32896.412760]        <ffffffff8821e1f7>{:video_buf:videobuf_dqbuf+167} <ffffffff88228335>{:bttv:bttv_do_ioctl+4869}
Dec  4 07:11:09 localhost kernel: [32896.412794]        <ffffffff88032221>{:unix:unix_write_space+49} <ffffffff8803467b>{:unix:unix_stream_recvmsg+1003}
Dec  4 07:11:09 localhost kernel: [32896.412829]        <ffffffff80155f5f>{buffered_rmqueue+463} <ffffffff88033eaf>{:unix:unix_stream_sendmsg+671}
Dec  4 07:11:09 localhost kernel: [32896.412860]        <ffffffff802bb5c4>{thread_return+0} <ffffffff80182073>{poll_freewait+67}
Dec  4 07:11:09 localhost kernel: [32896.412902]        <ffffffff8018255e>{do_select+1006} <ffffffff88227030>{:bttv:bttv_do_ioctl+0}
Dec  4 07:11:09 localhost kernel: [32896.412923]        <ffffffff881ff3f2>{:videodev:video_usercopy+386} <ffffffff801816fe>{do_ioctl+78}
Dec  4 07:11:09 localhost kernel: [32896.412964]        <ffffffff8018197d>{vfs_ioctl+621} <ffffffff80181a0a>{sys_ioctl+106}
Dec  4 07:11:09 localhost kernel: [32896.412977]        <ffffffff8010e6f6>{system_call+126}
Dec  4 07:11:09 localhost kernel: [32896.413006]
Dec  4 07:11:09 localhost kernel: [32896.413007] Code: 48 8b 3c c2 75 08 48 89 f2 4c 89 c6 eb 0d ff c9 75 10 48 89


Has anyone else had this problem?  Have you solved it?

---

### Post by f1d094 on 2005-12-04
I had a similar problem, but it was with the ivtv driver...the cure was to change the load order for the kernel modules. Check your driver module dependencies, and make sure they are loading first.

Food for thought.

---

