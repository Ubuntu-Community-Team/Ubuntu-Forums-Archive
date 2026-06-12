---
title: "Server get unresponsive once a day - kernel error"
date: 2007-03-15
forum: x86 64-bit Users (Pre April '08)
---

### Post by simcax1 on 2007-03-15
I am running Ubuntu 6.10 (64 bit) on an AMD64 3200+.

Right after boot I get this :

[  825.016266] Unable to handle kernel paging request at ffff81000000b300 RIP: 
[  825.016273] [<ffff81000000b300>]
[  825.016282] PGD 8063 PUD 9063 PMD 80000000000001e3 PTE f000efd2f000e82e
[  825.016287] Oops: 0011 [1] SMP 
[  825.016290] CPU 0 
[  825.016291] Modules linked in: binfmt_misc rfcomm l2cap bluetooth xt_limit xt_tcpudp iptable_mangle ipt_LOG ipt_MASQUERADE ip_nat ipt_TOS ipt_REJECT ip_co
nntrack_irc ip_conntrack_ftp xt_state ip_conntrack nfnetlink iptable_filter ip_tables x_tables video tc1100_wmi sbs sony_acpi pcc_acpi i2c_ec hotkey dev_acpi
 button battery container ac asus_acpi ipv6 it87 hwmon_vid eeprom lm90 i2c_isa lp sg tsdev i2c_nforce2 parport_pc parport r1000 r8169 i2c_core pcspkr evdev p
smouse serio_raw shpchp pci_hotplug ext3 jbd ehci_hcd ohci_hcd usbcore ide_generic sd_mod sata_via ide_cd cdrom generic amd74xx sata_nv libata scsi_mod therm
al processor fan vesafb capability commoncap vga16fb cfbcopyarea vgastate cfbimgblt cfbfillrect fbcon tileblit font bitblit softcursor
[  825.016325] Pid: 5387, comm: gam_server Tainted: G   M  2.6.17-11-generic #2
[  825.016329] RIP: 0010:[<ffff81000000b300>] [<ffff81000000b300>]
[  825.016333] RSP: 0018:ffff810001eb9b60  EFLAGS: 00010282
[  825.016337] RAX: ffff81000000cc10 RBX: 0000000000000020 RCX: ffff810001eb9f78
[  825.016341] RDX: ffff81000000cc10 RSI: ffff8100057e1d80 RDI: ffff8100043d29c0
[  825.016345] RBP: ffff8100057e1d80 R08: ffff810001eb8000 R09: 0000000000000001
[  825.016348] R10: 0000000000000436 R11: ffffffff88083310 R12: ffff8100043d29c0
[  825.016351] R13: 0000000000000000 R14: 0000000000000005 R15: ffff810001eb9e18
[  825.016355] FS:  00002b2586223f20(0000) GS:ffffffff805f3000(0000) knlGS:0000000000000000
[  825.016358] CS:  0010 DS: 0000 ES: 0000 CR0: 000000008005003b
[  825.016361] CR2: ffff81000000b300 CR3: 0000000001c8f000 CR4: 00000000000006e0
[  825.016365] Process gam_server (pid: 5387, threadinfo ffff810001eb8000, task ffff810004a6c380)
[  825.016367] Stack: ffffffff802e6f5e 0000000000000020 ffff810001eb9e18 ffff8100043d29c0 
[  825.016373]        ffffffff80231a0d ffff81000000cc10 ffff810001eb9bc8 ffff810001eb9f78 
[  825.016379]        0000000000520410 ffff810001eb9e18 
[  825.016382] Call Trace: <ffffffff802e6f5e>{inotify_poll+46} <ffffffff80231a0d>{do_sys_poll+477}
[  825.016399]        <ffffffff8021f060>{__pollwait+0} <ffffffff8028ddf0>{default_wake_function+0}
[  825.016414]        <ffffffff8028ddf0>{default_wake_function+0} <ffffffff8028ddf0>{default_wake_function+0}
[  825.016425]        <ffffffff8028ddf0>{default_wake_function+0} <ffffffff8028ddf0>{default_wake_function+0}
[  825.016438]        <ffffffff8023b318>{do_sock_write+216} <ffffffff8024ce7f>{sock_aio_write+79}
[  825.016448]        <ffffffff8023791d>{follow_page+381} <ffffffff80217fd7>{do_sync_write+199}
[  825.016467]        <ffffffff8021f25e>{free_pgtables+62} <ffffffff802a3ad0>{autoremove_wake_function+0}
[  825.016482]        <ffffffff80232690>{unix_poll+0} <ffffffff802521ba>{sys_poll+58}
[  825.016494]        <ffffffff802657d6>{system_call+126}
[  825.016505] 
[  825.016506] Code: ff 1d 00 00 00 00 00 00 bc 02 00 00 00 00 00 00 6b 03 00 00 
[  825.016514] RIP [<ffff81000000b300>] RSP <ffff810001eb9b60>
[  825.016519] CR2: ffff81000000b300

And 1-2 hours after boot, my cpu load goes to above 1.00 from 0.05. This level cpu load holds for 10 hours or so, and the server get unresponsive, and I have to kill it on the power switch. 

Can someone help me here ? I am running  2.6.17-11.35-generic kernel.

Best regards - and big hopes
Carsten

---

### Post by prince_niceguy on 2007-03-16
while it not advisable.. check if you can upgrade to feisty and check...  but do this as last resort.

---

