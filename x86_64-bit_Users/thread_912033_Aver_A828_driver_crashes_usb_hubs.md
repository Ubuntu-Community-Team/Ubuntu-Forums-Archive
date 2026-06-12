---
title: "Aver A828 driver crashes usb hubs"
date: 2008-09-06
forum: x86 64-bit Users
---

### Post by TSAMoloTOFf on 2008-09-06
Hello there, I have some problems with Aver A828 Hybrid TV tuner usb stick - I installed the driver from avermedia.com(A828_0.18beta), and when I try to plug-in tuner, that message appears in dmesg:

```
Sep  6 11:03:59 tsa-laptop kernel: [  659.308711] Linux video capture interface: v2.00
Sep  6 11:03:59 tsa-laptop kernel: [  659.313730] AVerMedia USB Wrapper version 0.01 loaded
Sep  6 11:03:59 tsa-laptop kernel: [  659.325453] USB Hybrid+FM Volar version 0.19 loaded
Sep  6 11:03:59 tsa-laptop kernel: [  659.442182] A828 registered V4L2 device video0[video]
Sep  6 11:03:59 tsa-laptop kernel: [  659.442208] A828 registered V4L2 device video1[audio]
Sep  6 11:03:59 tsa-laptop kernel: [  659.442232] A828 registered V4L2 device radio0[radio]
Sep  6 11:03:59 tsa-laptop kernel: [  659.442260] A828 registered V4L2 device vbi0[vbi]
Sep  6 11:03:59 tsa-laptop kernel: [  659.442355] A828 registered ALSA sound card 1
Sep  6 11:03:59 tsa-laptop kernel: [  659.442361] DVB: registering new adapter (A828[0] DVB-T)
Sep  6 11:03:59 tsa-laptop kernel: [  659.442363] A828[0] DVB-T registered DVB adapter 0
Sep  6 11:03:59 tsa-laptop kernel: [  659.442603] DVB: registering frontend 0 (A828[0] DVB-T)...
Sep  6 11:03:59 tsa-laptop kernel: [  659.546966] usbcore: registered new interface driver USB Hybrid+FM Volar
Sep  6 11:04:47 tsa-laptop kernel: [  686.566548] usb 3-6: USB disconnect, address 3
Sep  6 11:04:47 tsa-laptop kernel: [  686.568588] hub 3-0:1.0: hub_port_status failed (err = -108)
Sep  6 11:04:47 tsa-laptop kernel: [  686.568598] hub 3-0:1.0: connect-debounce failed, port 6 disabled
Sep  6 11:04:47 tsa-laptop kernel: [  686.568604] hub 3-0:1.0: cannot disable port 6 (err = -108)
Sep  6 11:04:49 tsa-laptop kernel: [  687.777729] usb 3-6: new high speed USB device using ehci_hcd and address 4
Sep  6 11:04:49 tsa-laptop kernel: [  687.844369] usb 3-6: configuration #1 chosen from 1 choice
Sep  6 11:04:50 tsa-laptop kernel: [  687.901564] Unable to handle kernel NULL pointer dereference at 000000000000001c RIP: 
Sep  6 11:04:50 tsa-laptop kernel: [  687.901570]  [<ffffffff8852ea50>] :a828:_ZN6CUsbEP9ClearHaltEv+0x0/0xc
Sep  6 11:04:50 tsa-laptop kernel: [  687.901611] PGD 7c53a067 PUD 7c539067 PMD 0 
Sep  6 11:04:50 tsa-laptop kernel: [  687.901615] Oops: 0000 [1] PREEMPT SMP 
Sep  6 11:04:50 tsa-laptop kernel: [  687.901619] CPU 1 
Sep  6 11:04:50 tsa-laptop kernel: [  687.901621] Modules linked in: a828(P) dvb_core averusb videodev v4l2_common v4l1_compat i2c_dev binfmt_misc rfcomm l2cap bluetooth powernow_k8 cpufreq_powersave cpufreq_stats cpufreq_userspace cpufreq_ondemand freq_table cpufreq_conservative video output dock container sbs sbshc iptable_filter ip_tables x_tables af_packet snd_hda_intel serio_raw snd_pcm sbp2 snd_timer sdhci evdev psmouse i2c_piix4 ac ricoh_mmc mmc_core fglrx(P) snd battery button i2c_core soundcore snd_page_alloc ext3 jbd mbcache sg sr_mod cdrom sd_mod atiixp ide_core usbhid hid pata_acpi ohci1394 ieee1394 pata_atiixp sata_sil ehci_hcd ohci_hcd libata scsi_mod usbcore r8169 thermal processor fan fuse fbcon tileblit font bitblit softcursor
Sep  6 11:04:50 tsa-laptop kernel: [  687.901675] Pid: 1524, comm: khubd Tainted: P        2.6.24.3amd64 #4
Sep  6 11:04:50 tsa-laptop kernel: [  687.901678] RIP: 0010:[<ffffffff8852ea50>]  [<ffffffff8852ea50>] :a828:_ZN6CUsbEP9ClearHaltEv+0x0/0xc
Sep  6 11:04:50 tsa-laptop kernel: [  687.901701] RSP: 0018:ffff81005faf9a18  EFLAGS: 00010246
Sep  6 11:04:50 tsa-laptop kernel: [  687.901704] RAX: ffff8100487b9320 RBX: ffff8100477e3bc0 RCX: ffffffff80491e30
Sep  6 11:04:50 tsa-laptop kernel: [  687.901706] RDX: 0000000000000000 RSI: 0000000000000001 RDI: 0000000000000000
Sep  6 11:04:50 tsa-laptop kernel: [  687.901709] RBP: 00000000ffffff92 R08: 0000000000000465 R09: 0000000000000100
Sep  6 11:04:50 tsa-laptop kernel: [  687.901711] R10: 0000000000000001 R11: ffffffff80214900 R12: 0000000000000001
Sep  6 11:04:50 tsa-laptop kernel: [  687.901714] R13: ffffffff8855f100 R14: 0000000000000000 R15: ffff810048e06120
Sep  6 11:04:50 tsa-laptop kernel: [  687.901717] FS:  00007fc59af706e0(0000) GS:ffff81007dc01700(0000) knlGS:00000000f7b6fa40
Sep  6 11:04:50 tsa-laptop kernel: [  687.901720] CS:  0010 DS: 0018 ES: 0018 CR0: 000000008005003b
Sep  6 11:04:50 tsa-laptop kernel: [  687.901722] CR2: 000000000000001c CR3: 000000007d488000 CR4: 00000000000006e0
Sep  6 11:04:50 tsa-laptop kernel: [  687.901724] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
Sep  6 11:04:50 tsa-laptop kernel: [  687.901727] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
Sep  6 11:04:50 tsa-laptop kernel: [  687.901730] Process khubd (pid: 1524, threadinfo ffff81005faf8000, task ffff81007bfc37d0)
Sep  6 11:04:50 tsa-laptop kernel: [  687.901732] Stack:  ffffffff8853f6db ffff810048e06120 ffff8100477e3bc0 ffff810045486000
Sep  6 11:04:50 tsa-laptop kernel: [  687.901738]  0000000000000000 ffffffff8855f140 ffffffff8853eaf1 ffff810045486000
Sep  6 11:04:50 tsa-laptop kernel: [  687.901742]  ffffffff8853d6b8 0000000000000000 ffffffff8852f46c ffff810045486000
Sep  6 11:04:50 tsa-laptop kernel: [  687.901746] Call Trace:
Sep  6 11:04:50 tsa-laptop kernel: [  687.901774]  [<ffffffff8853f6db>] :a828:_ZN11Fx2Firmware15selectInterfaceEhh+0x79/0xa0
Sep  6 11:04:50 tsa-laptop kernel: [  687.901808]  [<ffffffff8853eaf1>] :a828:_ZN12CUsbInstance6InitHWEv+0x89/0x5c8
Sep  6 11:04:50 tsa-laptop kernel: [  687.901838]  [<ffffffff8853d6b8>] :a828:_Z8UsbCleanPv+0x0/0x1e0
Sep  6 11:04:50 tsa-laptop kernel: [  687.901863]  [<ffffffff8852f46c>] :a828:_ZN4CUsb4InitEPFvPvEi+0x3e/0x6e
Sep  6 11:04:50 tsa-laptop kernel: [  687.901893]  [<ffffffff8853d6ae>] :a828:UsbProbe+0xc4/0xce
Sep  6 11:04:50 tsa-laptop kernel: [  687.901917]  [usbcore:usb_match_id+0x32/0x60] :usbcore:usb_match_id+0x32/0x60
Sep  6 11:04:50 tsa-laptop kernel: [  687.901935]  [usbcore:usb_probe_interface+0xda/0x160] :usbcore:usb_probe_interface+0xda/0x160
Sep  6 11:04:50 tsa-laptop kernel: [  687.901945]  [driver_probe_device+0x9c/0x1c0] driver_probe_device+0x9c/0x1c0
Sep  6 11:04:50 tsa-laptop kernel: [  687.901950]  [__device_attach+0x0/0x10] __device_attach+0x0/0x10
Sep  6 11:04:50 tsa-laptop kernel: [  687.901955]  [ide_core:bus_for_each_drv+0x58/0x270] bus_for_each_drv+0x58/0x80
Sep  6 11:04:50 tsa-laptop kernel: [  687.901963]  [ide_core:device_attach+0x88/0x140] device_attach+0x88/0x90
Sep  6 11:04:50 tsa-laptop kernel: [  687.901968]  [bus_attach_device+0x55/0xa0] bus_attach_device+0x55/0xa0
Sep  6 11:04:50 tsa-laptop kernel: [  687.901973]  [usbcore:device_add+0x4ad/0x5a0] device_add+0x4ad/0x5a0
Sep  6 11:04:50 tsa-laptop kernel: [  687.901994]  [usbcore:usb_set_configuration+0x30b/0x5c0] :usbcore:usb_set_configuration+0x30b/0x5c0
Sep  6 11:04:50 tsa-laptop kernel: [  687.902022]  [usbcore:generic_probe+0x7c/0xb0] :usbcore:generic_probe+0x7c/0xb0
Sep  6 11:04:50 tsa-laptop kernel: [  687.902028]  [driver_probe_device+0x9c/0x1c0] driver_probe_device+0x9c/0x1c0
Sep  6 11:04:50 tsa-laptop kernel: [  687.902033]  [__device_attach+0x0/0x10] __device_attach+0x0/0x10
Sep  6 11:04:50 tsa-laptop kernel: [  687.902037]  [ide_core:bus_for_each_drv+0x58/0x270] bus_for_each_drv+0x58/0x80
Sep  6 11:04:50 tsa-laptop kernel: [  687.902045]  [ide_core:device_attach+0x88/0x140] device_attach+0x88/0x90
Sep  6 11:04:50 tsa-laptop kernel: [  687.902050]  [bus_attach_device+0x55/0xa0] bus_attach_device+0x55/0xa0
Sep  6 11:04:50 tsa-laptop kernel: [  687.902055]  [usbcore:device_add+0x4ad/0x5a0] device_add+0x4ad/0x5a0
Sep  6 11:04:50 tsa-laptop kernel: [  687.902075]  [usbcore:usb_new_device+0x63/0xb0] :usbcore:usb_new_device+0x63/0xb0
Sep  6 11:04:50 tsa-laptop kernel: [  687.902093]  [usbcore:hub_thread+0x514/0xef0] :usbcore:hub_thread+0x514/0xef0
Sep  6 11:04:50 tsa-laptop kernel: [  687.902109]  [<ffffffff80254c10>] autoremove_wake_function+0x0/0x30
Sep  6 11:04:50 tsa-laptop kernel: [  687.902128]  [usbcore:hub_thread+0x0/0xef0] :usbcore:hub_thread+0x0/0xef0
Sep  6 11:04:50 tsa-laptop kernel: [  687.902133]  [kthread+0x4b/0x80] kthread+0x4b/0x80
Sep  6 11:04:50 tsa-laptop kernel: [  687.902139]  [child_rip+0xa/0x12] child_rip+0xa/0x12
Sep  6 11:04:50 tsa-laptop kernel: [  687.902150]  [kthread+0x0/0x80] kthread+0x0/0x80
Sep  6 11:04:50 tsa-laptop kernel: [  687.902153]  [child_rip+0x0/0x12] child_rip+0x0/0x12
Sep  6 11:04:50 tsa-laptop kernel: [  687.902157] 
Sep  6 11:04:50 tsa-laptop kernel: [  687.902158] 
Sep  6 11:04:50 tsa-laptop kernel: [  687.902159] Code: 8b 77 1c 48 8b 3f e9 95 e9 fd ff 90 48 83 ec 28 49 89 f2 48 
Sep  6 11:04:50 tsa-laptop kernel: [  687.902169] RIP  [<ffffffff8852ea50>] :a828:_ZN6CUsbEP9ClearHaltEv+0x0/0xc
Sep  6 11:04:50 tsa-laptop kernel: [  687.902193]  RSP <ffff81005faf9a18>
Sep  6 11:04:50 tsa-laptop kernel: [  687.902195] CR2: 000000000000001c
Sep  6 11:04:50 tsa-laptop kernel: [  687.902208] ---[ end trace 8d2fcd63e19d4382 ]---
Sep  6 11:06:16 tsa-laptop kernel: [  735.030927] usbcore: deregistering interface driver USB Hybrid+FM Volar
Sep  6 11:07:41 tsa-laptop kernel: [  778.687971] irq 19: nobody cared (try booting with the "irqpoll" option)
Sep  6 11:07:41 tsa-laptop kernel: [  778.687983] Pid: 6595, comm: gnome-terminal Tainted: P      D 2.6.24.3amd64 #4
Sep  6 11:07:41 tsa-laptop kernel: [  778.687986] 
Sep  6 11:07:41 tsa-laptop kernel: [  778.687987] Call Trace:
Sep  6 11:07:41 tsa-laptop kernel: [  778.687990]  <IRQ>  [__report_bad_irq+0x1e/0x80] __report_bad_irq+0x1e/0x80
Sep  6 11:07:41 tsa-laptop kernel: [  778.688017]  [note_interrupt+0x2a3/0x2e0] note_interrupt+0x2a3/0x2e0
Sep  6 11:07:41 tsa-laptop kernel: [  778.688027]  [handle_fasteoi_irq+0xa3/0x110] handle_fasteoi_irq+0xa3/0x110
Sep  6 11:07:41 tsa-laptop kernel: [  778.688035]  [do_IRQ+0x7b/0x100] do_IRQ+0x7b/0x100
Sep  6 11:07:41 tsa-laptop kernel: [  778.688040]  [ret_from_intr+0x0/0x0a] ret_from_intr+0x0/0xa
Sep  6 11:07:41 tsa-laptop kernel: [  778.688043]  <EOI> 
Sep  6 11:07:41 tsa-laptop kernel: [  778.688055] handlers:
Sep  6 11:07:41 tsa-laptop kernel: [  778.688057] [usbcore:usb_hcd_irq+0x0/0x60] (usb_hcd_irq+0x0/0x60 [usbcore])
Sep  6 11:07:41 tsa-laptop kernel: [  778.688081] [usbcore:usb_hcd_irq+0x0/0x60] (usb_hcd_irq+0x0/0x60 [usbcore])
Sep  6 11:07:41 tsa-laptop kernel: [  778.688097] [usbcore:usb_hcd_irq+0x0/0x60] (usb_hcd_irq+0x0/0x60 [usbcore])
Sep  6 11:07:41 tsa-laptop kernel: [  778.688113] Disabling IRQ #19

```

If tuner was plugged in during the boot, it hangs hal and then all usb hubs seem to be offline.
It happens that way every time, regardless of 'plugging' moment(either when booting or when all gui things are up and working).

There's no way to made it work normally? 
(kernel 2.6.24-amd64(self-compiled and generic), AMD mobile processor(TL50) and gpu(M56), amd chipset(rX1150))

PS Sometimes it could launch, but then it usually hangs up after a period of time.

---

