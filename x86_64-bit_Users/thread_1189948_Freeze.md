---
title: "Freeze"
date: 2009-06-17
forum: x86 64-bit Users
---

### Post by phidahl on 2009-06-17
Hi

i have a problem with my Thinkpad R61 (Ubuntu 9.04 x64).
sometimes and not reconstructable the system freezes. I alreade checked the RAM, which seems to be ok. I installed the 64bit Flashplugin.

here I post the kern.log there seems to be an error, but don't see what this log wants to tell me.

> Jun 17 14:28:02 phi-note kernel: [ 1886.708463] usb 1-3.2: new high speed USB device using ehci_hcd and address 8
Jun 17 14:28:02 phi-note kernel: [ 1886.801927] usb 1-3.2: configuration #1 chosen from 1 choice
Jun 17 14:28:02 phi-note kernel: [ 1886.914278] Initializing USB Mass Storage driver...
Jun 17 14:28:02 phi-note kernel: [ 1886.915364] scsi5 : SCSI emulation for USB Mass Storage devices
Jun 17 14:28:02 phi-note kernel: [ 1886.915597] usbcore: registered new interface driver usb-storage
Jun 17 14:28:02 phi-note kernel: [ 1886.915600] USB Mass Storage support registered.
Jun 17 14:28:02 phi-note kernel: [ 1886.916615] usb-storage: device found at 8
Jun 17 14:28:02 phi-note kernel: [ 1886.916618] usb-storage: waiting for device to settle before scanning
Jun 17 14:28:07 phi-note kernel: [ 1891.916303] usb-storage: device scan complete
Jun 17 14:28:07 phi-note kernel: [ 1891.916847] scsi 5:0:0:0: Direct-Access     WD       10EAVS External  1.05 PQ: 0 ANSI: 4
Jun 17 14:28:07 phi-note kernel: [ 1891.918826] sd 5:0:0:0: [sdb] 1953525168 512-byte hardware sectors: (1.00 TB/931 GiB)
Jun 17 14:28:07 phi-note kernel: [ 1891.919696] sd 5:0:0:0: [sdb] Write Protect is off
Jun 17 14:28:07 phi-note kernel: [ 1891.919699] sd 5:0:0:0: [sdb] Mode Sense: 21 00 00 00
Jun 17 14:28:07 phi-note kernel: [ 1891.919701] sd 5:0:0:0: [sdb] Assuming drive cache: write through
Jun 17 14:28:07 phi-note kernel: [ 1891.923937] sd 5:0:0:0: [sdb] 1953525168 512-byte hardware sectors: (1.00 TB/931 GiB)
Jun 17 14:28:07 phi-note kernel: [ 1891.924813] sd 5:0:0:0: [sdb] Write Protect is off
Jun 17 14:28:07 phi-note kernel: [ 1891.924816] sd 5:0:0:0: [sdb] Mode Sense: 21 00 00 00
Jun 17 14:28:07 phi-note kernel: [ 1891.924818] sd 5:0:0:0: [sdb] Assuming drive cache: write through
Jun 17 14:28:07 phi-note kernel: [ 1891.924824]  sdb: sdb1
Jun 17 14:28:07 phi-note kernel: [ 1891.934501] sd 5:0:0:0: [sdb] Attached SCSI disk
Jun 17 14:28:07 phi-note kernel: [ 1891.934579] sd 5:0:0:0: Attached scsi generic sg2 type 0
Jun 17 14:38:11 phi-note kernel: [ 2494.968064] BUG: unable to handle kernel paging request at ffffffffffffffff
Jun 17 14:38:11 phi-note kernel: [ 2494.968071] IP: [<ffffffff802e236c>] kmem_cache_alloc+0x5c/0xc0
Jun 17 14:38:11 phi-note kernel: [ 2494.968079] PGD 203067 PUD 204067 PMD 0 
Jun 17 14:38:11 phi-note kernel: [ 2494.968083] Oops: 0000 [#1] SMP 
Jun 17 14:38:11 phi-note kernel: [ 2494.968086] last sysfs file: /sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0/rfkill/rfkill0/state
Jun 17 14:38:11 phi-note kernel: [ 2494.968090] Dumping ftrace buffer:
Jun 17 14:38:11 phi-note kernel: [ 2494.968092]    (ftrace buffer empty)
Jun 17 14:38:11 phi-note kernel: [ 2494.968094] CPU 0 
Jun 17 14:38:11 phi-note kernel: [ 2494.968096] Modules linked in: usb_storage binfmt_misc ppdev bridge stp bnep vboxnetflt vboxdrv input_polldev qt1010 mt352 sbp2 lp parport joydev pcmcia hid_cherry arc4 ecb snd_hda_intel snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event iwlagn iwlcore snd_seq snd_timer snd_seq_device mac80211 psmouse snd soundcore pcspkr serio_raw yenta_socket rsrc_nonstatic pcmcia_core ricoh_mmc sdhci_pci sdhci iTCO_wdt iTCO_vendor_support cfg80211 thinkpad_acpi led_class nvram dvb_usb_m920x dvb_usb snd_page_alloc dvb_core usbhid nvidia(P) video output intel_agp ohci1394 ieee1394 e1000e fbcon tileblit font bitblit softcursor
Jun 17 14:38:11 phi-note kernel: [ 2494.968145] Pid: 9, comm: events/0 Tainted: P           2.6.28-11-generic #42-Ubuntu
Jun 17 14:38:11 phi-note kernel: [ 2494.968147] RIP: 0010:[<ffffffff802e236c>]  [<ffffffff802e236c>] kmem_cache_alloc+0x5c/0xc0
Jun 17 14:38:11 phi-note kernel: [ 2494.968152] RSP: 0018:ffff88013fba1d20  EFLAGS: 00010086
Jun 17 14:38:11 phi-note kernel: [ 2494.968153] RAX: 0000000000000000 RBX: ffffffffffffffff RCX: 00000000000000c0
Jun 17 14:38:11 phi-note kernel: [ 2494.968156] RDX: ffff88002802cca0 RSI: 0000000000000010 RDI: 0000000000000008
Jun 17 14:38:11 phi-note kernel: [ 2494.968158] RBP: ffff88013fba1d50 R08: 0000000000000000 R09: 000000000000ff51
Jun 17 14:38:11 phi-note kernel: [ 2494.968159] R10: 0000000000000000 R11: 0000000000000000 R12: 0000000000000282
Jun 17 14:38:11 phi-note kernel: [ 2494.968161] R13: ffffffff809b2cb8 R14: ffffffff8053008f R15: 0000000000000010
Jun 17 14:38:11 phi-note kernel: [ 2494.968164] FS:  0000000000000000(0000) GS:ffffffff80aa3000(0000) knlGS:0000000000000000
Jun 17 14:38:11 phi-note kernel: [ 2494.968166] CS:  0010 DS: 0018 ES: 0018 CR0: 000000008005003b
Jun 17 14:38:11 phi-note kernel: [ 2494.968168] CR2: ffffffffffffffff CR3: 0000000000201000 CR4: 00000000000006a0
Jun 17 14:38:11 phi-note kernel: [ 2494.968170] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
Jun 17 14:38:11 phi-note kernel: [ 2494.968172] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
Jun 17 14:38:11 phi-note kernel: [ 2494.968175] Process events/0 (pid: 9, threadinfo ffff88013fba0000, task ffff88013fb6d980)
Jun 17 14:38:11 phi-note kernel: [ 2494.968177] Stack:
Jun 17 14:38:11 phi-note kernel: [ 2494.968178]  000000083fba1d30 00000000fffffff4 ffff88013cdea000 0000000000000001
Jun 17 14:38:11 phi-note kernel: [ 2494.968182]  00000000000000c0 0000000000000000 ffff88013fba1db0 ffffffff8053008f
Jun 17 14:38:11 phi-note kernel: [ 2494.968186]  0000ff5100010001 8000078000000022 ffff88013d544800 ffffffff80240cfb
Jun 17 14:38:11 phi-note kernel: [ 2494.968191] Call Trace:
Jun 17 14:38:11 phi-note kernel: [ 2494.968193]  [<ffffffff8053008f>] usb_control_msg+0x4f/0x110
Jun 17 14:38:11 phi-note kernel: [ 2494.968203]  [<ffffffff80240cfb>] ? dequeue_entity+0x1b/0x250
Jun 17 14:38:11 phi-note kernel: [ 2494.968208]  [<ffffffffa08a80bf>] m920x_rc_query+0x6f/0x1f0 [dvb_usb_m920x]
Jun 17 14:38:11 phi-note kernel: [ 2494.968214]  [<ffffffffa089f860>] ? dvb_usb_read_remote_control+0x0/0xf0 [dvb_usb]
Jun 17 14:38:11 phi-note kernel: [ 2494.968220]  [<ffffffffa089f8a8>] dvb_usb_read_remote_control+0x48/0xf0 [dvb_usb]
Jun 17 14:38:11 phi-note kernel: [ 2494.968225]  [<ffffffff8026430a>] run_workqueue+0xba/0x190
Jun 17 14:38:11 phi-note kernel: [ 2494.968229]  [<ffffffff802645e7>] worker_thread+0xa7/0x120
Jun 17 14:38:11 phi-note kernel: [ 2494.968231]  [<ffffffff80268930>] ? autoremove_wake_function+0x0/0x40
Jun 17 14:38:11 phi-note kernel: [ 2494.968235]  [<ffffffff80264540>] ? worker_thread+0x0/0x120
Jun 17 14:38:11 phi-note kernel: [ 2494.968238]  [<ffffffff802684c9>] kthread+0x49/0x90
Jun 17 14:38:11 phi-note kernel: [ 2494.968241]  [<ffffffff80213979>] child_rip+0xa/0x11
Jun 17 14:38:11 phi-note kernel: [ 2494.968245]  [<ffffffff80268480>] ? kthread+0x0/0x90
Jun 17 14:38:11 phi-note kernel: [ 2494.968247]  [<ffffffff8021396f>] ? child_rip+0x0/0x11
Jun 17 14:38:11 phi-note kernel: [ 2494.968250] Code: fa 0f 1f 80 00 00 00 00 65 8b 04 25 24 00 00 00 48 98 49 8b 94 c5 e8 00 00 00 8b 7a 18 89 7d d4 48 8b 1a 48 85 db 74 47 8b 42 14 <48> 8b 04 c3 48 89 02 4c 89 e7 57 9d 66 0f 1f 44 00 00 66 45 85 
Jun 17 14:38:11 phi-note kernel: [ 2494.968282] RIP  [<ffffffff802e236c>] kmem_cache_alloc+0x5c/0xc0
Jun 17 14:38:11 phi-note kernel: [ 2494.968285]  RSP <ffff88013fba1d20>
Jun 17 14:38:11 phi-note kernel: [ 2494.968287] CR2: ffffffffffffffff
Jun 17 14:38:11 phi-note kernel: [ 2494.968289] ---[ end trace 9a7904e92e4d0b0c ]---the freeze also 
occures if the usb-DVB receiver is not connected.

and I have a Vertex SSD as harddrive. with the newest firmware, if that helps.


thank you in advance

phi

---

