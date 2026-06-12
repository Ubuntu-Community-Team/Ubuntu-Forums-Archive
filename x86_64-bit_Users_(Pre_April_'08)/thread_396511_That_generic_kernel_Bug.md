---
title: "That generic kernel: Bug"
date: 2007-03-29
forum: x86 64-bit Users (Pre April '08)
---

### Post by Canada3332 on 2007-03-29
Whenever I try to run wine on the program HITOMIML.EXE I get some nasty errors, here is the output from dmesg:

[787260.751999] Oops: 0000 [1] SMP 
[787260.752001] CPU 0 
[787260.752003] Modules linked in: spca5xx videodev nls_iso8859_1 nls_utf8 vfat fat usb_storage libusual nls_cp437 isofs udf nfs battery ac thermal fan button forcedeth snd_rtctimer binfmt_misc rfcomm l2cap bluetooth nfsd exportfs lockd sunrpc ipx p8023 powernow_k8 cpufreq_userspace cpufreq_stats freq_table cpufreq_powersave cpufreq_ondemand cpufreq_conservative video tc1100_wmi sbs sony_acpi pcc_acpi i2c_ec hotkey dev_acpi container asus_acpi af_packet jfs it87 hwmon_vid eeprom i2c_isa lp snd_intel8x0 snd_ac97_codec snd_ac97_bus ipv6 snd_pcm_oss snd_pcm snd_mixer_oss snd_seq_dummy snd_seq_oss nvidia snd_seq_midi snd_rawmidi sg tsdev snd_seq_midi_event snd_seq snd_timer snd_seq_device snd soundcore snd_page_alloc i2c_core evdev psmouse serio_raw pcspkr parport_pc parport floppy shpchp pci_hotplug usbhid ext3 jbd ehci_hcd ohci_hcd usbcore ide_generic ide_cd cdrom generic sd_mod amd74xx sata_nv libata scsi_mod processor vesafb capability commoncap vga16fb cfbcopyarea vgastate cfbimgblt cfbfillrect fbcon tileblit font bitblit softcursor
[787260.752046] Pid: 6561, comm: HITOMIML.EXE Tainted: P      2.6.17-11-generic #2
[787260.752049] RIP: 0010:[<ffffffff887603c5>] <ffffffff887603c5>{:snd_seq_oss:snd_seq_oss_readq_puts+37}
[787260.752060] RSP: 0018:ffff8100229d9af8  EFLAGS: 00010206
[787260.752063] RAX: 0000000000000000 RBX: 000000003fffffa6 RCX: 0000000040000006
[787260.752066] RDX: 00000000000000a1 RSI: 0000000000000292 RDI: ffff81001dfb3c00
[787260.752070] RBP: ffffc20000073000 R08: 0000000000000002 R09: ffff81006f482d80
[787260.752073] R10: 0000000000000001 R11: 0000000000000246 R12: ffff81001dfb3bc0
[787260.752076] R13: ffff81006fb419c0 R14: 0000000000000000 R15: 0000000000000002
[787260.752080] FS:  000000007ffdc000(0063) GS:ffffffff805f3000(006b) knlGS:00000000f7cbb6b0
[787260.752083] CS:  0010 DS: 002b ES: 002b CR0: 000000008005003b
[787260.752087] CR2: ffffc20000073000 CR3: 0000000013f93000 CR4: 00000000000006e0
[787260.752091] Process HITOMIML.EXE (pid: 6561, threadinfo ffff8100229d8000, task ffff8100367d6f60)
[787260.752093] Stack: 0000000000000005 ffff8100229d9ca8 0000000000000286 ffff8100229d9ca8 
[787260.752099]        ffff81006edb3a40 ffff81006a68c800 ffff81006fb419c0 ffffffff8875ff0f 
[787260.752104]        0000000000007bfc 0000000000000000 
[787260.752107] Call Trace: <ffffffff8875ff0f>{:snd_seq_oss:snd_seq_oss_midi_input+399}
[787260.752124]        <ffffffff881f4493>{:snd_seq:snd_seq_client_use_ptr+371}
[787260.752140]        <ffffffff881f46fb>{:snd_seq:snd_seq_deliver_single_event+299}
[787260.752153]        <ffffffff881f76c9>{:snd_seq:queueptr+73} <ffffffff881f493a>{:snd_seq:snd_seq_deliver_event+266}
[787260.752188]        <ffffffff881f6092>{:snd_seq:snd_seq_kernel_client_dispatch+98}
[787260.752202]        <ffffffff88187098>{:snd_seq_dummy:dummy_input+104} <ffffffff881f46fb>{:snd_seq:snd_seq_deliver_single_event+299}
[787260.752223]        <ffffffff881f7320>{:snd_seq:snd_seq_cell_alloc+336}
[787260.752239]        <ffffffff881f4ec1>{:snd_seq:snd_seq_dispatch_event+305}
[787260.752252]        <ffffffff881f7559>{:snd_seq:snd_seq_event_dup+521} <ffffffff881f7b8e>{:snd_seq:snd_seq_check_queue+110}
[787260.752279]        <ffffffff881f7edf>{:snd_seq:snd_seq_enqueue_event+223}
[787260.752294]        <ffffffff881f4adf>{:snd_seq:snd_seq_client_enqueue_event+223}
[787260.752310]        <ffffffff881f4bb3>{:snd_seq:kernel_client_enqueue+131}
[787260.752325]        <ffffffff8875e484>{:snd_seq_oss:snd_seq_oss_write+484}
[787260.752338]        <ffffffff8024cf33>{set_close_on_exec+51} <ffffffff8875c1d6>{:snd_seq_oss:odev_write+22}
[787260.752354]        <ffffffff802167ae>{vfs_write+222} <ffffffff80217143>{sys_write+83}
[787260.752369]        <ffffffff80268844>{cstar_do_call+27}
[787260.752382] 
[787260.752383] Code: 0f b6 45 00 48 89 e6 4c 89 e7 83 eb 01 88 44 24 01 e8 85 fe 
[787260.752391] RIP <ffffffff887603c5>{:snd_seq_oss:snd_seq_oss_readq_puts+37} RSP <ffff8100229d9af8>
[787260.752401] CR2: ffffc20000073000
[787260.752402]  


This bugs me because in 6.06 there weren't generic kernels, and this didn't happen. I have an Athlon64 3200+. After this occurs, wine won't run ANYTHING, and the only way to fix it is to reboot. I'd like to request that there be a strictly NON-SMP kernel, and a strictly SMP kernel.

---

### Post by kleeman on 2007-03-29
Sounds like you are going to have to roll your own kernel as the devs are fixed on generic as one size fits all. The master kernel thread in this forum makes that job fairly easy. Check it out.....

---

