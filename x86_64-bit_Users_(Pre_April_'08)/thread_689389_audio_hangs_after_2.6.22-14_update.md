---
title: "audio hangs after 2.6.22-14 update"
date: 2008-02-06
forum: x86 64-bit Users (Pre April '08)
---

### Post by mthome on 2008-02-06
After updating to any 2.6.22-14 kernel (I'm on gusty x86_64), any audio-related stuff that runs hangs hard on reboot. e.g. login session drumbeat doesn't play and desktop waits forever. Also, the system will not shut down by itself, as it hangs trying to stop ALSA services.

reverting to 2.6.22-13 (or prior) kernels works just fine.  I've tried -14.51 rt and generic.  Nothing obvious (to me) in the logs - no warnings or errors, just deadly quiet.

Suggestions?  Thanks.

---

### Post by mthome on 2008-02-13
A bit more poking - I *finally* saw the following in dmesg.  No wonder things are borked...
[FONT="Courier New"]
[   56.951107] Unable to handle kernel paging request at ffff81112bce4288 RIP: 
[   56.951207]  [<ffffffff88b6f8a1>] :snd_hda_intel:snd_hda_input_mux_info+0x31/0x50
[   56.951526] PGD 8063 PUD 0 
[   56.951857] Oops: 0000 [1] PREEMPT SMP 
[   56.952246] CPU 1 
[   56.952444] Modules linked in: snd_hda_intel snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device ipv6 snd nvidia(P) soundcore i2c_nforce2 psmouse snd_page_alloc pcspkr serio_raw i2c_core shpchp pci_hotplug evdev ext3 jbd mbcache sg sr_mod sd_mod cdrom amd74xx usb_storage usbhid hid ide_core libusual ohci1394 ieee1394 ata_generic sata_nv libata tg3 ohci_hcd ehci_hcd scsi_mod usbcore thermal processor fan fuse apparmor commoncap
[   56.957995] Pid: 4308, comm: alsactl Tainted: P       2.6.22-14-rt #1
[   56.958104] RIP: 0010:[<ffffffff88b6f8a1>]  [<ffffffff88b6f8a1>] :snd_hda_intel:snd_hda_input_mux_info+0x31/0x50
[   56.958321] RSP: 0018:ffff81012e0cdd48  EFLAGS: 00010206
[   56.958428] RAX: 0000000ffffffff0 RBX: ffff81012c8604c0 RCX: 00000000ffffffff
[   56.958533] RDX: 0000000000000000 RSI: ffff81012e0cdd88 RDI: ffff81012e0cdde0
[   56.958640] RBP: ffff81012e0cdd88 R08: ffff81012bce4290 R09: 000000000000000a
[   56.958782] R10: 0000000000000000 R11: 0000000000000246 R12: ffff81013367ad68
[   56.958889] R13: ffff81013367ac00 R14: ffff81012a3f38c0 R15: 00007fff901ce410
[   56.958999] FS:  00002b991b7d4af0(0000) GS:ffff810138405a40(0000) knlGS:0000000000000000
[   56.959115] CS:  0010 DS: 0000 ES: 0000 CR0: 000000008005003b
[   56.960277] CR2: ffff81112bce4288 CR3: 00000001294a4000 CR4: 00000000000006e0
[   56.960387] Process alsactl (pid: 4308, threadinfo ffff81012e0cc000, task ffff81012ca4f620)
[   56.960503] Stack:  00007fff901ce410 ffffffff88aa29a5 0000000000000000 00000000c1105511
[   56.961122]  00007fff901ce410 ffff81013367ac00 ffff81012a3f38c0 ffffffff88aa3d30
[   56.961607]  0000000000000001 0000000000000000 0000000000000000 0000000000000000
[   56.962030] Call Trace:
[   56.962242]  [<ffffffff88aa29a5>] :snd:snd_ctl_elem_info+0x55/0x150
[   56.962353]  [<ffffffff88aa3d30>] :snd:snd_ctl_ioctl+0x4c0/0x850
[   56.962469]  [<ffffffff802b03c5>] do_ioctl+0x35/0xe0
[   56.962576]  [<ffffffff802b04e4>] vfs_ioctl+0x74/0x2d0
[   56.962701]  [<ffffffff802b07d5>] sys_ioctl+0x95/0xb0
[   56.962825]  [<ffffffff80209fee>] system_call+0x7e/0x83
[   56.962932] 
[   56.963034] 
[   56.963035] Code: 4a 8b 74 00 08 e8 f5 37 7c f7 31 c0 48 83 c4 08 c3 66 66 66 
[   56.965294] RIP  [<ffffffff88b6f8a1>] :snd_hda_intel:snd_hda_input_mux_info+0x31/0x50
[   56.965508]  RSP <ffff81012e0cdd48>
[   56.965608] CR2: ffff81112bce4288
[/FONT]

---

### Post by mthome on 2008-03-05
FWIW, the "solution" I found was to add the following to a file in /etc/modprobe.d:
[FONT="Courier New"]
# this is needed for kernels> 2.6.22-13
options snd-hda-intel model=5stack
[/FONT]

I finally found a reference at 
[http://ph.ubuntuforums.com/showthread.php?t=182834&page=5](http://ph.ubuntuforums.com/showthread.php?t=182834&page=5)  There are plenty of other systems that seem to have this issue - bottom line is that the model detection got borked and has to be forced for now.

---

### Post by Yellow Pasque on 2008-03-06
yeah, ALSA's a b1tch. You might want to use this script to upgrade to the latest version.
[http://ubuntuforums.org/showpost.php?p=4298894&postcount=24](http://ubuntuforums.org/showpost.php?p=4298894&postcount=24)

---

