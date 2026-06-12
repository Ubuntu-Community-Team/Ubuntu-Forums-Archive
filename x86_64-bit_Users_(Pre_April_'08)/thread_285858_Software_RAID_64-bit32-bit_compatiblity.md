---
title: "Software RAID 64-bit/32-bit compatiblity?"
date: 2006-10-27
forum: x86 64-bit Users (Pre April '08)
---

### Post by Chris on 2006-10-27
I have a software raid0 XFS array that I have been using in 32-bit Dapper (kernel 2.6.15.2).  When I try to mount this in 64-bit Edgy the kernel just explodes (see below for trace).

Is there some incompatibility between a 32-bit software RAID setup and 64-bit?  Or something with XFS maybe?  I can mount other XFS drives but not the RAID array.


```
[   99.694394] SGI XFS with ACLs, security attributes, realtime, large block/inode numbers, no debug enabled
[   99.694520] SGI XFS Quota Management subsystem
[   99.695886] Filesystem "md0": Disabling barriers, not supported by the underlying device
[   99.696574] XFS mounting filesystem md0
[   99.786441] Starting XFS recovery on filesystem: md0 (logdev: internal)
[   99.787447] Unable to handle kernel NULL pointer dereference at 0000000000000000 RIP:
[   99.787451] <ffffffff802ba0d0>{page_to_pfn+0}
[   99.787458] PGD 6bd5c067 PUD 6baf2067 PMD 0
[   99.787461] Oops: 0000 [1] SMP
[   99.787463] CPU 0
[   99.787464] Modules linked in: xfs binfmt_misc rfcomm l2cap bluetooth cpufreq_userspace cpufreq_stats freq_table cpufreq_powersave cpufreq_ondemand cpufreq_conservative video tc1100_wmi sony_acpi sbs pcc_acpi i2c_ec hotkey dev_acpi container button battery asus_acpi ac sbp2 parport_pc lp parport ipv6 tsdev af_packet usblp nvidia snd_intel8x0 snd_ac97_codec snd_ac97_bus sg snd_pcm_oss snd_mixer_oss snd_pcm usbhid psmouse evdev snd_timer serio_raw pcspkr floppy snd shpchp pci_hotplug i2c_nforce2 i2c_core soundcore snd_page_alloc ext3 jbd raid0 md_mod forcedeth ehci_hcd ohci1394 ieee1394 ohci_hcd usbcore ide_generic ide_disk ide_cd cdrom generic amd74xx sd_mod sata_nv libata scsi_mod thermal processor fan vesafb capability commoncap vga16fb cfbcopyarea vgastate cfbimgblt cfbfillrect fbcon tileblit font bitblit softcursor
[   99.787500] Pid: 5329, comm: mount Tainted: P      2.6.17-10-generic #2
[   99.787503] RIP: 0010:[page_to_pfn+0/64] <ffffffff802ba0d0>{page_to_pfn+0}
[   99.787507] RSP: 0018:ffff81006bafb710  EFLAGS: 00010256
[   99.787511] RAX: ffff81006b421780 RBX: 0000000000000000 RCX: ffff81006b421600
[   99.787513] RDX: 0000000000000000 RSI: 0000000000000000 RDI: 0000000000000000
[   99.787516] RBP: ffff81006d522840 R08: 0000000000000000 R09: ffff81006b421780
[   99.787520] R10: ffff81006b427000 R11: 0000000000000004 R12: ffff81006b421600
[   99.787523] R13: ffff81006be05000 R14: ffff81006d5227c0 R15: 0000000000000000
[   99.787526] FS:  00002b0f618d36d0(0000) GS:ffffffff805f3000(0000) knlGS:0000000000000000
[   99.787529] CS:  0010 DS: 0000 ES: 0000 CR0: 000000008005003b
[   99.787532] CR2: 0000000000000000 CR3: 000000006b8bb000 CR4: 00000000000006e0
[   99.787536] Process mount (pid: 5329, threadinfo ffff81006bafa000, task ffff810037c96100)
[   99.787538] Stack: ffffffff8897cc99 ffff81006d522800 ffffffff88964a7d 0000000000009857
[   99.787544]        000000008807da1a ffff81007ca11b80 ffffffff804d33c0 0000000000000282
[   99.787548]        0000000000000000 ffff81007cafe4b8
[   99.787551] Call Trace: <ffffffff8897cc99>{:xfs:xfs_buf_offset+57}
[   99.787614]        <ffffffff88964a7d>{:xfs:xlog_recover_commit_trans+1917}
[   99.787660]        <ffffffff889657fb>{:xfs:xlog_recover_process_data+475}
[   99.787698]        <ffffffff8896643c>{:xfs:xlog_do_recovery_pass+620} <ffffffff88967b03>{:xfs:xlog_recover+259}
[   99.787779]        <ffffffff88963756>{:xfs:xfs_log_mount+1462} <ffffffff88978b5b>{:xfs:kmem_alloc+107}
[   99.787848]        <ffffffff88969fd1>{:xfs:xfs_mountfs+2401} <ffffffff8020bf12>{_atomic_dec_and_lock+66}
[   99.787893]        <ffffffff889712dc>{:xfs:xfs_mount+2428} <ffffffff88983078>{:xfs:xfs_fs_fill_super+152}
[   99.787960]        <ffffffff8026af52>{__down_write+18} <ffffffff80233afe>{strlcpy+78}
[   99.787969]        <ffffffff802dae72>{get_filesystem+18} <ffffffff802d274f>{sget+927}
[   99.787978]        <ffffffff802d1f90>{set_bdev_super+0} <ffffffff802d34e0>{bd_claim+32}
[   99.787988]        <ffffffff802d2f7a>{get_sb_bdev+266} <ffffffff88982fe0>{:xfs:xfs_fs_fill_super+0}
[   99.788027]        <ffffffff802d2acd>{vfs_kern_mount+189} <ffffffff802d2bfa>{do_kern_mount+74}
[   99.788040]        <ffffffff802dcc49>{do_mount+1849} <ffffffff80222ad1>{__up_read+33}
[   99.788049]        <ffffffff8026d989>{do_page_fault+1273} <ffffffff802406fb>{__get_free_pages+27}
[   99.788080]        <ffffffff8025227b>{sys_mount+155} <ffffffff8026580e>{system_call+126}
[   99.788098]
[   99.788099] Code: 48 8b 07 48 c1 e8 3a 48 8b 14 c5 40 d0 5f 80 48 b8 b7 6d db
[   99.788106] RIP <ffffffff802ba0d0>{page_to_pfn+0} RSP <ffff81006bafb710>
[   99.788111] CR2: 0000000000000000
```

---

### Post by spankminister on 2007-01-28
Hi, I have the exact same problem.  I'd be interested to know how or if you ever fixed it.  Thanks!

---

### Post by spankminister on 2007-01-28
No sooner did I reply than I found the answer elsewhere-- what you need to do is xfs_repair -L /dev/md0.  The problem is a journal incompatibility.  I had to reboot my system so my kernel wasnt' screwy, and then ran that command first thing.  That command should delete the journal and make a new one for the new computer.  The wikipedia page says:

On the Linux XFS implementations, compatibility issues between different architectures exists due to journaling-optimization. This can be solved by running xfs_repair (to clean the journal) before mounting the file system on a different architecture.

Hope that helps.

---

