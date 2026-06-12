---
title: "WG311v3 WORKING w/ 64-bit Kernel"
date: 2006-12-16
forum: x86 64-bit Users (Pre April '08)
---

### Post by dkrieger on 2006-12-16
I ventured quite a bit to get my card WG311v3 card working, it seemed everybody gave up trying to get it to work, but finally it has happened.  Let us look at the problem in detail:

The Problem:

1. Netgear, for whatever reason, does not support Windows X64, so there is no 64-bit driver for this card.
2.  Ndiswrapper should work great, however if you run a 64-bit kernel then your windows drivers too must be 64-bit.

The Solution:

Find the Netgear XP drivers (I googled and came up with this place):
[http://network.free-driver-download.com/NETGEAR/28325/NETGEAR-WG311v3-Wireless-PCI-Adapter-Driver-v3.10.html](http://network.free-driver-download.com/NETGEAR/28325/NETGEAR-WG311v3-Wireless-PCI-Adapter-Driver-v3.10.html) (beware the ads...)

Find Marvell 64-bit drivers:
[http://www.skd.de/e_en/support/driver_searchresults.html?navanchor=&term=typ.treiber+produkt.SK-54C1&produkt=produkt.SK-54C1&typ=typ.treiber&system=](http://www.skd.de/e_en/support/driver_searchresults.html?navanchor=&term=typ.treiber+produkt.SK-54C1&produkt=produkt.SK-54C1&typ=typ.treiber&system=)

Unzip the Netgear drivers and the Marvell drivers.

Copy MRV8335x64.sys from the Marvell drivers into the Netgear XP driver.
Remove WG311v3XP.sys from the XP drivers.
Move MRV8335x64.sys to WG311v3XP.sys

Now you can run your ndiswrapper install just as before.  It will read the 64-bit driver like it was the 32-bit driver (flawless so far).  FINALLY you will be able to use that Netgear WG311v3 with a 64-bit kernel.

Hopefully this helps, I'm not HOWTO writer, but I'll be happy to clarify what I have screwed up explaining.

---

### Post by lui04 on 2007-01-03
Very helpful!

Thank you

---

### Post by ummagumma82 on 2007-01-03
Thank you very much for the writeup! It got my card up & running perfectly.

---

### Post by eagleram13 on 2007-06-03
I am such a newbie to this right now.

You say copy the marvel sys file into the netgearxp sys file and then remove the xp file.

Can you be more specific on how to do this as I need it spelled out.

Thanks ahead of time.

---

### Post by dkrieger on 2007-06-12
> **eagleram13 said:**
> I am such a newbie to this right now.

You say copy the marvel sys file into the netgearxp sys file and then remove the xp file.

Can you be more specific on how to do this as I need it spelled out.

Thanks ahead of time.

Yeah, i'm not very good at writing these things up either.  If you haven't got it working yet:

When you unzip the two files, you will have two directories: the Marvell 64-bit drivers, and the Netgear one.

The Netgear directory will have 3 subdirs: WinXP, Win2000, and Win98(?).

Under the Marvell directory, copy MRV8335x64.sys into the WinXP directory under Netgear.  Then remove WG311v3XP.sys (the Netgear sys), and move MRV8335x64.sys to WG311x3XP.sys.  This essentially replaces the sys files, the Marvell one is nearly identical to the WG311 one, just with 64-bit support.

If you still need help  let me know, I'll try to keep an eye up here.  Sorry for the delay.

---

### Post by nowhere.elysium on 2007-07-27
MiLord dkrieger, thou art a genius!

Seriously though dude - you've saved the remnants of my hairline from being torn out entirely...
Thankyou :D

*bookmarks thread*

---

### Post by captainfullet on 2007-08-08
Those german Marvell Drivers are golden!! Thank you so much! I actually ended up just modifying the marvell .inf file, for whatever that's worth. It still took a lot of work after my device was recognized, but it DEFINITELY got me over the hill!

---

### Post by boomcat on 2007-08-18
I'm sorry, but I didn't understand this at all.

The instructions say to down load the Marvell drivers from the URL. But the URL has four download links on it. Which one of the four?

I don't have the directories specified in the instructions.

I'm taking this card out.

---

### Post by zevero on 2007-10-20
Didn't work here!
I have a fresh ubuntu gutsy desktop amd64.

```
ndiswrapper -i wg311v3.INF
```

worked nicely and

ndiswrapper -l confirms, that driver and device are working.

But when doing (after depmod -a)

```
modprobe ndiswrapper
```

I get the Message "Killed!"
Subsequent tries freeze the console.

The Log is as follows:

```
Oct 20 13:33:30 AAA kernel: [ 1147.038302] ndiswrapper version 1.48 loaded (smp=yes, preempt=no)
Oct 20 13:33:30 AAA kernel: [ 1147.046194] ndiswrapper (link_pe_images:576): fixing KI_USER_SHARED_DATA address in the driver
Oct 20 13:33:30 AAA kernel: [ 1147.047152] ndiswrapper: driver wg311v3 (NETGEAR,02/22/2005,3.1.1.7) loaded
Oct 20 13:33:30 AAA kernel: [ 1147.047638] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 17 (level, low) -> IRQ 17
Oct 20 13:33:30 AAA kernel: [ 1147.048293] ndiswrapper: using IRQ 17
Oct 20 13:33:30 AAA kernel: [ 1147.064513] PGD 84455067 PUD 9388b067 PMD 0 
Oct 20 13:33:30 AAA kernel: [ 1147.064521] CPU 1 
Oct 20 13:33:30 AAA kernel: [ 1147.064523] Modules linked in: ndiswrapper nls_cp437 isofs udf rfcomm l2cap bluetooth ppdev acpi_cpufreq cpufreq_powersave cpufreq_stats cpufreq_userspace cpufreq_ondemand cpufreq_conservative freq_table video container sbs button dock ac battery ext3 jbd mbcache lp snd_hda_intel snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device i2c_core sky2 iTCO_wdt iTCO_vendor_support psmouse parport_pc parport snd soundcore intel_agp serio_raw shpchp pci_hotplug pcspkr snd_page_alloc evdev reiserfs sg sr_mod cdrom sd_mod usbhid hid ata_piix pata_it821x ata_generic ehci_hcd libata scsi_mod uhci_hcd usbcore thermal processor fan fuse apparmor commoncap
Oct 20 13:33:30 AAA kernel: [ 1147.064570] Pid: 17860, comm: modprobe Tainted: P       2.6.22-14-generic #1
Oct 20 13:33:30 AAA kernel: [ 1147.064573] RIP: 0010:[phys_startup_64+22258843/-2147483648]  [phys_startup_64+22258843/-2147483648]
Oct 20 13:33:30 AAA kernel: [ 1147.064578] RSP: 0018:ffff8100b2d73790  EFLAGS: 00010202
Oct 20 13:33:30 AAA kernel: [ 1147.064580] RAX: 000000000004a6fc RBX: 000000000001eb82 RCX: ffffc20001596fb8
Oct 20 13:33:30 AAA kernel: [ 1147.064583] RDX: 0000000000000000 RSI: 0000000000000000 RDI: 0000000000000002
Oct 20 13:33:30 AAA kernel: [ 1147.064586] RBP: ffff8100ba7b7780 R08: ffffc20001595000 R09: 0000000000000000
Oct 20 13:33:30 AAA kernel: [ 1147.064589] R10: ffffffff883691d0 R11: ffffffff80422150 R12: 000000000000000a
Oct 20 13:33:30 AAA kernel: [ 1147.064592] R13: 0000000000000000 R14: 0000000000000000 R15: ffffc20001782950
Oct 20 13:33:30 AAA kernel: [ 1147.064596] FS:  00002b6f410066e0(0000) GS:ffff81003785e280(0000) knlGS:0000000000000000
Oct 20 13:33:30 AAA kernel: [ 1147.064599] CS:  0010 DS: 0000 ES: 0000 CR0: 000000008005003b
Oct 20 13:33:30 AAA kernel: [ 1147.064601] CR2: 000000000004a7f4 CR3: 0000000088214000 CR4: 00000000000006e0
Oct 20 13:33:30 AAA kernel: [ 1147.064605] Process modprobe (pid: 17860, threadinfo ffff8100b2d72000, task ffff8100b342c000)
Oct 20 13:33:30 AAA kernel: [ 1147.064608] Stack:  65626f7270646f6d 00006c616e696d00 00000000000045c4 0000000000000000
Oct 20 13:33:30 AAA kernel: [ 1147.064614]  000000000000001b 0000000000000000 ffff810083cbd000 ffff8100911a4e30
Oct 20 13:33:30 AAA kernel: [ 1147.064619]  ffff81009e0e7c00 0000000000000004 0000000000000002 ffffc2000173a620
Oct 20 13:33:30 AAA kernel: [ 1147.064623] Call Trace:
Oct 20 13:33:30 AAA kernel: [ 1147.064662]  [_end+131136100/2130332920] :ndiswrapper:IofCompleteRequest+0x8c/0x1a0
Oct 20 13:33:30 AAA kernel: [ 1147.064691]  [_end+131178911/2130332920] :ndiswrapper:win2lin2+0xe/0x11
Oct 20 13:33:30 AAA kernel: [ 1147.064713]  [_end+131133847/2130332920] :ndiswrapper:IofCallDriver+0x5f/0xc0
Oct 20 13:33:30 AAA kernel: [ 1147.064736]  [_end+131160032/2130332920] :ndiswrapper:mp_init+0xa8/0x1e0
Oct 20 13:33:30 AAA kernel: [ 1147.064756]  [_end+131133804/2130332920] :ndiswrapper:IofCallDriver+0x34/0xc0
Oct 20 13:33:30 AAA kernel: [ 1147.064780]  [_end+131139176/2130332920] :ndiswrapper:IoSyncForwardIrp+0x90/0xd0
Oct 20 13:33:30 AAA kernel: [ 1147.064804]  [_end+131160563/2130332920] :ndiswrapper:NdisDispatchPnp+0xdb/0xeb0
Oct 20 13:33:30 AAA kernel: [ 1147.064816]  [setup_object+25/80] setup_object+0x19/0x50
Oct 20 13:33:30 AAA kernel: [ 1147.064821]  [new_slab+438/608] new_slab+0x1b6/0x260
Oct 20 13:33:30 AAA kernel: [ 1147.064828]  [__slab_alloc+467/1024] __slab_alloc+0x1d3/0x400
Oct 20 13:33:30 AAA kernel: [ 1147.064848]  [_end+131136805/2130332920] :ndiswrapper:IoAllocateIrp+0x4d/0x80
Oct 20 13:33:30 AAA kernel: [ 1147.064870]  [_end+131136675/2130332920] :ndiswrapper:IoInitializeIrp+0x3b/0x70
Oct 20 13:33:30 AAA kernel: [ 1147.064896]  [_end+131178911/2130332920] :ndiswrapper:win2lin2+0xe/0x11
Oct 20 13:33:30 AAA kernel: [ 1147.064917]  [_end+131133847/2130332920] :ndiswrapper:IofCallDriver+0x5f/0xc0
Oct 20 13:33:30 AAA kernel: [ 1147.064940]  [_end+131133804/2130332920] :ndiswrapper:IofCallDriver+0x34/0xc0
Oct 20 13:33:30 AAA kernel: [ 1147.064961]  [_end+131137959/2130332920] :ndiswrapper:IoBuildSynchronousFsdRequest+0x2f/0x50
Oct 20 13:33:30 AAA kernel: [ 1147.064983]  [_end+131143556/2130332920] :ndiswrapper:IoSendIrpTopDev+0xac/0x100
Oct 20 13:33:30 AAA kernel: [ 1147.065010]  [_end+131144327/2130332920] :ndiswrapper:pnp_start_device+0x4f/0xa0
Oct 20 13:33:30 AAA kernel: [ 1147.065037]  [_end+131144892/2130332920] :ndiswrapper:wrap_pnp_start_device+0x1e4/0x280
Oct 20 13:33:30 AAA kernel: [ 1147.065064]  [_end+131145128/2130332920] :ndiswrapper:wrap_pnp_start_pci_device+0x50/0x60
Oct 20 13:33:30 AAA kernel: [ 1147.065072]  [sysfs_make_dirent+48/80] sysfs_make_dirent+0x30/0x50
Oct 20 13:33:30 AAA kernel: [ 1147.065079]  [pci_device_probe+241/368] pci_device_probe+0xf1/0x170
Oct 20 13:33:30 AAA kernel: [ 1147.065087]  [driver_probe_device+163/432] driver_probe_device+0xa3/0x1b0
Oct 20 13:33:30 AAA kernel: [ 1147.065093]  [__driver_attach+201/208] __driver_attach+0xc9/0xd0
Oct 20 13:33:30 AAA kernel: [ 1147.065098]  [__driver_attach+0/208] __driver_attach+0x0/0xd0
Oct 20 13:33:30 AAA kernel: [ 1147.065102]  [bus_for_each_dev+77/128] bus_for_each_dev+0x4d/0x80
Oct 20 13:33:30 AAA kernel: [ 1147.065110]  [bus_add_driver+175/496] bus_add_driver+0xaf/0x1f0
Oct 20 13:33:30 AAA kernel: [ 1147.065116]  [__pci_register_driver+102/176] __pci_register_driver+0x66/0xb0
Oct 20 13:33:30 AAA kernel: [ 1147.065133]  [_end+131094308/2130332920] :ndiswrapper:loader_init+0x13c/0x260
Oct 20 13:33:30 AAA kernel: [ 1147.065147]  [_end+128302511/2130332920] :ndiswrapper:wrapper_init+0xb7/0xc2
Oct 20 13:33:30 AAA kernel: [ 1147.065153]  [sys_init_module+411/6576] sys_init_module+0x19b/0x19b0
Oct 20 13:33:30 AAA kernel: [ 1147.065166]  [__up_write+33/304] __up_write+0x21/0x130
Oct 20 13:33:30 AAA kernel: [ 1147.065176]  [system_call+126/131] system_call+0x7e/0x83
Oct 20 13:33:30 AAA kernel: [ 1147.065184] 
Oct 20 13:33:30 AAA kernel: [ 1147.065185] 
Oct 20 13:33:30 AAA kernel: [ 1147.065186] Code: 80 b8 f8 00 00 00 01 0f 85 ed 00 00 00 48 8b 05 59 8c 04 00 
Oct 20 13:33:30 AAA kernel: [ 1147.065201]  RSP <ffff8100b2d73790> 
```

As I don't think the drivers are wrong, I suspected ndiswrapper to be faulty. I compiled the newest version 1.48, but it's still the same.

Anybody have an idea?

---

### Post by miximixim on 2007-10-22
:(, got the same problem with the WG311v3. Seems to be a problem with the 64-bit distribution or
ndiswrapper ? Have seen that it works with 7.04 64-bit version...

---

### Post by zevero on 2007-10-22
Thats nice to have some company!
I gave it a try and installed 7.04 amd64 and it still didnt work. Then I used the old 1.18 packages for ndiswrapper. At this point, there were no errors anymore, but also no wlan0  appeared - maybe I missed something?
Please go ahead and post if others have a similar problem!

---

### Post by thidranki on 2007-10-28
I have a similar problem. ndiswrapper installed fine, modprobe worked, etc. When I type iwconfig in the command line, I get

lo        no wireless extensions.


eth0   no wireless extensions.


I'm not sure how to get the wireless set up at this point.

Thanks

---

### Post by genti on 2007-12-10
> **thidranki said:**
> I have a similar problem. ndiswrapper installed fine, modprobe worked, etc. When I type iwconfig in the command line, I get

lo        no wireless extensions.


eth0   no wireless extensions.


I'm not sure how to get the wireless set up at this point.

Thanks

I am in a similar position but I know what is happening.
Check /var/log/dmseg for ndiswrapper related entries.
Probably it is saying that "couldn't initialize device" therefore the wireless adapter is not showing up and that is why iwconfig does not work.
I have a stupid Trendnet card but the trick did not work.
Trying the 64bit drivers only hangs my system.
Darn this 8335, i should have know better.

---

### Post by slaufer on 2007-12-27
For those having trouble with the driver packages, I've wrapped up what you need in a tidy little package on my site:

[http://endlessbeta.org/misc/wg311v3_ndis_amd64.tar.bz2]("http://endlessbeta.org/misc/wg311v3_ndis_amd64.tar.bz2")

Thanks a lot for this post, it was a great help as I would never have otherwise been able to get this wireless adapter working.

---

### Post by zartox on 2008-01-13
Hi,

Thanks for your driver packaging but I cant success to connect with a wpa-psk conf so if someone can help cause I start beeing fade up of rebooting to my dual-boot Xp session ... :(

Thanks again for you'r help

---

### Post by Jouke74 on 2008-01-13
I have a Marvell Wl-138g card from Asus and I am using a Windows 64 bit drivers as well. WPA fails here too, so I reverted to WEP 128 HEX plus MAC address identification.

---

### Post by TDNiXoN on 2008-01-26
Thanks dude...been trying to get this working for a week!

---

### Post by stefansmith on 2008-03-24
> **thidranki said:**
> I have a similar problem. ndiswrapper installed fine, modprobe worked, etc. When I type iwconfig in the command line, I get

lo        no wireless extensions.


eth0   no wireless extensions.


I'm not sure how to get the wireless set up at this point.

Thanks

ditto.
anyone worked this out???

---

### Post by stefansmith on 2008-03-28
tried all the various suggestions, but no joy.
I can only recommend people stay WELL CLEAR of the Netgear WG311v3 (a shame, as the V2 apears to be more Linux friendly, and Netgear seems to have a good reputation here)....

---

### Post by moosylog on 2008-07-09
Working with the 64 bit driver now for over 2 years. -works-

---

### Post by openess on 2008-07-10
Thanks a lot. I was almost about to buy a new WLAN-card.. Worked great for my new 64bit system

---

### Post by strungoutfan78 on 2008-07-14
FANTASTIC SOLUTION!  Thanks so much for this simple fix! :guitar:


*edit*
didn't realize this thread was so old!

---

