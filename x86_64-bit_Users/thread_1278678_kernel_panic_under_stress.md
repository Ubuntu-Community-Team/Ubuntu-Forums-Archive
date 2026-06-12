---
title: "kernel panic under stress"
date: 2009-09-29
forum: x86 64-bit Users
---

### Post by smoghal on 2009-09-29
I've got a really strange problem.  Let me provide some quick background first. I've been using Ubuntu 8.04.3 LTS server edition (32bit) Linux Kernel 2.6.x for over an year now. Never had any problems. I had been upgrading the kernel periodly and the last one I was on I believe was 2.6.24-24-60 (latest).  The hardware configuration was:

- Celeron D 2.4Ghz
- 6G RAM
- ASUS P5B board
- Adaptec RAID controller

Last weekend, I thought it's time to upgrade to bigger and better hardware. So I pop'ed in a Intel Q6600 (not as big but a significant jump from the Celeron process for me).

I thought everything would work smoothly, and on the surface it was. Until I started getting random crashes for some of the background processes I ran (BONINC processes, and XVNC server in headless mode)

Then I downloaded a stress tool (called "stress") and started stressing the system.  The first attempt brought down the server. I got lots of strange kernel panic messages.  The command line I used was:

```
stress --cpu 4 --io 4 --vm 4 --vm-bytes 128M --hdd 4 --timeout 120s
```

So I took some preventive measures (after going through the forums and googl'ing):

- Upgraded P5B bios to the latest
- Went through all the options in BIOS in details and ensure everything is set properly (to the best of my understanding).  There aren't many options in P5B.
- Ran a 24hr "memtest" using Ubuntu kernel CD to ensure that memory checks out, which it did
- Ran several CPU stress tests using stress tool above (with --cpu parameter combinations up to 8 ). CPU alone doesn't cause the system to crash

After going through these actions above, Ubuntu still crashed. So I backed up my existing data and reinstalled Ubuntu 8.04.03 32bit. Upon running the stress tool, same kernel panic message appeared and system crashed. Finally, I switched to Ubuntu 8.04.3 64bit in hopes that it would be stable. Still no luck.  

I'm posting this cry for help in the AMD64 section because I still have 64Bit version installed.

The last kernel panic message I received was as follows.  Again, notice it was caused as a result of running the stress problem

```
stress --cpu 4 --io 4 --vm 4 --vm-bytes 128M --hdd 4 --timeout 120s
```


```
Sep 29 20:08:48 jupiter kernel: [ 2685.893168] ------------[ cut here ]------------
Sep 29 20:08:48 jupiter kernel: [ 2685.898734] kernel BUG at /build/buildd/linux-2.6.24/fs/buffer.c:2867!
Sep 29 20:08:48 jupiter kernel: [ 2685.904420] invalid opcode: 0000 [1] SMP
Sep 29 20:08:48 jupiter kernel: [ 2685.910154] CPU 0
Sep 29 20:08:48 jupiter kernel: [ 2685.915788] Modules linked in: iptable_filter ip_tables x_tables ipv6               parport_pc lp parport loop af_packet serio_raw snd_hda_intel psmouse s3fb svgalib vgastate snd_pcm snd_ti              mer snd_page_alloc snd_hwdep snd iTCO_wdt iTCO_vendor_support soundcore button evdev intel_agp shpchp pci              _hotplug pcspkr ext3 jbd mbcache sr_mod cdrom sg sd_mod pata_acpi ata_generic usbhid hid floppy pata_jmic              ron aacraid tulip ahci libata scsi_mod ehci_hcd uhci_hcd r8169 usbcore thermal processor fan fbcon tilebl              it font bitblit softcursor fuse
Sep 29 20:08:48 jupiter kernel: [ 2685.962057] Pid: 5571, comm: stress Not tainted 2.6.24-24-server #1
Sep 29 20:08:48 jupiter kernel: [ 2685.969195] RIP: 0010:[jbd:submit_bh+0x115/0x120]  [jbd:submit_bh+0x11              5/0x120] submit_bh+0x115/0x120
Sep 29 20:08:48 jupiter kernel: [ 2685.983735] RSP: 0000:ffff810197da1c38  EFLAGS: 00010246
Sep 29 20:08:48 jupiter kernel: [ 2685.991257] RAX: 0000000055ce8b40 RBX: ffff810155ce8b40 RCX: 000000000              0000024
Sep 29 20:08:48 jupiter kernel: [ 2685.999021] RDX: 0000000000000013 RSI: ffff810155ce8b40 RDI: 000000000              0000001
Sep 29 20:08:48 jupiter kernel: [ 2686.006892] RBP: 0000000000000001 R08: ffff81019a001149 R09: ffff81019              7da1b78
Sep 29 20:08:48 jupiter kernel: [ 2686.014832] R10: ffff81019f9d2b60 R11: 0000000000000000 R12: ffff81015              5ce8b40
Sep 29 20:08:48 jupiter kernel: [ 2686.022860] R13: 0000000000000001 R14: ffff81019f9d2b60 R15: 000000000              0001000
Sep 29 20:08:48 jupiter kernel: [ 2686.030952] FS:  00007fa49599f6e0(0000) GS:ffffffff805c6000(0000) knlG              S:0000000000000000
Sep 29 20:08:48 jupiter kernel: [ 2686.047024] CS:  0010 DS: 0000 ES: 0000 CR0: 000000008005003b
Sep 29 20:08:48 jupiter kernel: [ 2686.055204] CR2: 000000000062e008 CR3: 000000019640a000 CR4: 000000000              00006e0
Sep 29 20:08:48 jupiter kernel: [ 2686.063594] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 000000000              0000000
Sep 29 20:08:48 jupiter kernel: [ 2686.071947] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 000000000              0000400
Sep 29 20:08:48 jupiter kernel: [ 2686.080190] Process stress (pid: 5571, threadinfo ffff810197da0000, ta              sk ffff810198cbd7d0)
Sep 29 20:08:48 jupiter kernel: [ 2686.096750] Stack:  ffff810155ce8b40 ffff810155ce8b40 ffff810155ce8b40               ffffffff802dc2d0
Sep 29 20:08:48 jupiter kernel: [ 2686.114099]  ffff810194c922e8 0000000000001000 ffff810197da1ee8 ffffff              ff881c6650
Sep 29 20:08:48 jupiter kernel: [ 2686.131498]  ffff8101940b7cc8 ffff81019f9d2b60 ffff810155ce8b40 000000              0094c922e8
Sep 29 20:08:48 jupiter kernel: [ 2686.140648] Call Trace:
Sep 29 20:08:48 jupiter kernel: [ 2686.158186]  [__block_write_full_page+0x1b0/0x310] __block_write_full_              page+0x1b0/0x310
Sep 29 20:08:48 jupiter kernel: [ 2686.167145]  [ext3:ext3_get_block+0x0/0x120] :ext3:ext3_get_block+0x0/              0x120
Sep 29 20:08:48 jupiter kernel: [ 2686.175928]  [ext3:ext3_ordered_writepage+0xc0/0x180] :ext3:ext3_order              ed_writepage+0xc0/0x180
Sep 29 20:08:48 jupiter kernel: [ 2686.184584]  [__writepage+0xa/0x30] __writepage+0xa/0x30
Sep 29 20:08:48 jupiter kernel: [ 2686.192965]  [write_cache_pages+0x24e/0x340] write_cache_pages+0x24e/0              x340
Sep 29 20:08:48 jupiter kernel: [ 2686.201155]  [__writepage+0x0/0x30] __writepage+0x0/0x30
Sep 29 20:08:48 jupiter kernel: [ 2686.209125]  [__dequeue_entity+0x3d/0x50] __dequeue_entity+0x3d/0x50
Sep 29 20:08:48 jupiter kernel: [ 2686.216940]  [do_writepages+0x2b/0x40] do_writepages+0x2b/0x40
Sep 29 20:08:48 jupiter kernel: [ 2686.224548]  [__writeback_single_inode+0xb0/0x380] __writeback_single_              inode+0xb0/0x380
Sep 29 20:08:48 jupiter kernel: [ 2686.232161]  [thread_return+0x3a/0x59a] thread_return+0x3a/0x59a
Sep 29 20:08:48 jupiter kernel: [ 2686.239670]  [pagevec_lookup_tag+0x1a/0x30] pagevec_lookup_tag+0x1a/0x              30
Sep 29 20:08:48 jupiter kernel: [ 2686.247295]  [sync_sb_inodes+0x1f9/0x300] sync_sb_inodes+0x1f9/0x300
Sep 29 20:08:48 jupiter kernel: [ 2686.254907]  [sync_inodes_sb+0x94/0xb0] sync_inodes_sb+0x94/0xb0
Sep 29 20:08:48 jupiter kernel: [ 2686.262428]  [__sync_inodes+0x79/0xc0] __sync_inodes+0x79/0xc0
Sep 29 20:08:48 jupiter kernel: [ 2686.269856]  [sync_inodes+0x11/0x30] sync_inodes+0x11/0x30
Sep 29 20:08:48 jupiter kernel: [ 2686.277112]  [do_sync+0x38/0x70] do_sync+0x38/0x70
Sep 29 20:08:48 jupiter kernel: [ 2686.284104]  [sys_sync+0xe/0x20] sys_sync+0xe/0x20
Sep 29 20:08:48 jupiter kernel: [ 2686.290925]  [system_call+0x7e/0x83] system_call+0x7e/0x83
Sep 29 20:08:48 jupiter kernel: [ 2686.297614]
Sep 29 20:08:48 jupiter kernel: [ 2686.304207]
Sep 29 20:08:48 jupiter kernel: [ 2686.304207] Code: 0f 0b eb fe 0f 1f 80 00 00 00 00 55 48 89 fd 48 89 f              7 53 48
Sep 29 20:08:48 jupiter kernel: [ 2686.324019] RIP  [jbd:submit_bh+0x115/0x120] submit_bh+0x115/0x120
Sep 29 20:08:48 jupiter kernel: [ 2686.330622]  RSP <ffff810197da1c38>
Sep 29 20:08:48 jupiter kernel: [ 2686.349553] ---[ end trace 9003fd1a4c879ba5 ]---
```


Any pointers? Thoughts.  Please do share!  I've run out of ideas.

---

### Post by mgranet on 2009-09-30
Almost sounds like your PSU is insufficient. How many watts, and how old is it?

---

### Post by smoghal on 2009-09-30
The server enclosure is Antec 550 and it came with Antec's 550 PSU.  I thought it would take the quad core CPU load.

[http://www.cluboc.net/REVIEWS/cases/antec/Titan550/index.htm](http://www.cluboc.net/REVIEWS/cases/antec/Titan550/index.htm)

---

### Post by scheuri on 2009-09-30
Hi there

I would HIGHLY recommend to check your RAM (with memtest) and your harddisk (fschk and hdparm (SMART)).

I think it is pretty obvious (at least from the information you provided) that the issue is caused by the hardware change.

You also might want to try to put back the celeron processor (if you can) and stress-test the machine with that processor.
But I guess that is only of the tests with RAM and HD dont show any troubles.

cheers
scheuri

---

### Post by mgranet on 2009-09-30
> **smoghal said:**
> The server enclosure is Antec 550 and it came with Antec's 550 PSU.  I thought it would take the quad core CPU load.

[http://www.cluboc.net/REVIEWS/cases/antec/Titan550/index.htm](http://www.cluboc.net/REVIEWS/cases/antec/Titan550/index.htm)

It depends. If you have a recent, high performance video card (or 2), a bunch of drives, fans, etc, 550 may be cutting it kind of close. You can google for power supply calculators that can help you decide what size you need.

I'm leaning against RAM or CPU problems, as you tested independently for them. You already had the mobo working with the Celeron, so I would lean to that being ok. That really only leaves a problem with the PSU, the video card(?), or a software issue.

---

### Post by theZoid on 2009-10-01
> **mgranet said:**
> It depends. If you have a recent, high performance video card (or 2), a bunch of drives, fans, etc, 550 may be cutting it kind of close. You can google for power supply calculators that can help you decide what size you need.

I'm leaning against RAM or CPU problems, as you tested independently for them. You already had the mobo working with the Celeron, so I would lean to that being ok. That really only leaves a problem with the PSU, the video card(?), or a software issue.

I was planning on building a quad and figured an 800 watt supply or thereabouts...550 may be close IMO...I'd do some math.

---

### Post by smoghal on 2009-10-05
> **mgranet said:**
> It depends. If you have a recent, high performance video card (or 2), a bunch of drives, fans, etc, 550 may be cutting it kind of close. You can google for power supply calculators that can help you decide what size you need.

I'm leaning against RAM or CPU problems, as you tested independently for them. You already had the mobo working with the Celeron, so I would lean to that being ok. That really only leaves a problem with the PSU, the video card(?), or a software issue.

I must apologize for not posting my progress in the forum. And I didn't check up on your post ahead of time either.

Here's the exact list of devices in the system (minus the CPU)

- PCI S3/Trio32 Card (super old and shitty card)
- Adaptec 3805 8-Chan SATA PCI-Express 4x RAID controller
- 5 SATA Drives
- 1 DVDROM
- 2 92mm Fans
- 1 120mm Fan
- 1 80 mm Fan
- 4 DDR2 RAM sticks (2G + 4G)
- 1 3.5 floppy disk
- thermalright U120 CPU Cooler
- 550 W PSU

During the PD process last week, I've done the following:

- installed the latest 2.6.31-1 kernel in Ubuntu 8.04. It worked fine when no load was thrown at the system. However, undress stress, kernel panic errors would show up.  

- then I decided to ditch linux all together and installed original WinXP (without SP). It ran fine. However, as soon as I installed SP3, the system would continuously reboot off the start-up screen.

- I also tried Vista32. Installation went fine, but the system never booted into Windows. It gave BSOD and rebooted.

Note, when I was testing the alternate OS setup above, all devices were plugged in except the Adaptec RAID controller, I took out the card but the drives were still on.

I shall give it another shot tomorrow and unhook all redundant devices other than 1 SATA drive, CDROM and 120mm fan to narrow down on the PSU.  However, I did a quick test on thermaltake PSU calculator (as you advised, [http://www.thermaltake.outervision.com/Power](http://www.thermaltake.outervision.com/Power)) .  It suggested 280W, which is almost close to half of what I have in the system.

Following are some alternatives I had been thinking about:

- Try Q9550 (that I have in another system) to see if that makes any difference. I will be shocked if it's a problem with CPU.  As indicated earlier in the thread, stressing CPU alone (stress --cup 8 --timeout 120s) didn't cause the crash.  

- Rig off 650W Seasonic PSU I have in another system and try it out on this system.

- Replace the motherboard (which I realllly do not want to do)

If you have any more pointers, I will appreciate.

---

### Post by smoghal on 2009-10-05
> **scheuri said:**
> Hi there

I would HIGHLY recommend to check your RAM (with memtest) and your harddisk (fschk and hdparm (SMART)).

I think it is pretty obvious (at least from the information you provided) that the issue is caused by the hardware change.

You also might want to try to put back the celeron processor (if you can) and stress-test the machine with that processor.
But I guess that is only of the tests with RAM and HD dont show any troubles.

cheers
scheuri

I saw your note earlier and I did as you suggested

- stressed the system with original celeron D processor and it passed with flying colors. I even tried a really huge load (for celeron at least) as follows. And there were no issues.

```
stress --cpu 8 --io 8 --vm 8 --vm-bytes 128M --hdd 8 --timeout 120s
```

- I've tested the memory with memtest (kernel option) and there were no issues. The test ran over night.

- I've done several fsck (forced checks) to ensure HD is fine. The primary HD that is used for OS and boot is as follows. 
#1 /boot
#2 / 
#3 /opt (data)
#4 swap

---

### Post by smoghal on 2009-10-10
It seems that my P5B board does not like the Q6600 CPU.  I swapped PSU's with a 650W PSU and still had the same problem.

Finally, I swapped the CPU with Q9550. System has been stable since.  Stressed the system heavily and both 32bit and 64bit Ubuntu work fine.

This Q6600 works fine on a P5E3 Duluxe WIFI board where I took it out from. So it really blows my mind why it wouldn't work on P5B.

Anyways, I'm in the process of testing Q6600 again on P5E3 Duluxe WIFI and hoping it hasn't gone bad.

Thanks for all your help and valuable pointers. It really helped narrow down the problem.

---

### Post by smoghal on 2009-10-10
Here's some additional info about this Q6600, for the records and for anyone who is having the same hardware problem on this config:

- 05A type

serial/lot #'s:
- L739B770
- 2L74550
- 1A0286

---

### Post by Artemis3 on 2009-10-10
Where are your temperature readings? Don't stress stuff without checking temperature! It is way too common for people to buy new cpus to make a mistake putting the fan cooler, example some fan sinks come with a tiny plastic sheet covering the thermal grease attached, which you are supposed to remove, yet some people leave it there!

Use [Systester](http://systester.sourceforge.net/) to stress your cpu, make sure you use 4 threads.

As for your motherboard, there might be a bios upgrade, or if you are an expert, a little of voltage increase (overclock style). Sometimes its the memories, with the fastest ones being the most troublesome (memtest should show errors).

---

### Post by smoghal on 2009-10-11
> **Artemis3 said:**
> Where are your temperature readings? Don't stress stuff without checking temperature! It is way too common for people to buy new cpus to make a mistake putting the fan cooler, example some fan sinks come with a tiny plastic sheet covering the thermal grease attached, which you are supposed to remove, yet some people leave it there!

Use [Systester](http://systester.sourceforge.net/) to stress your cpu, make sure you use 4 threads.

As for your motherboard, there might be a bios upgrade, or if you are an expert, a little of voltage increase (overclock style). Sometimes its the memories, with the fastest ones being the most troublesome (memtest should show errors).

I wasn't using the stock fan. Q6600 had a thermalright U-120 with 120mm fan on top. The CPU temperature and the MB temperatures under stress (with open top lid) were close to 35.  

The BIOS is also the latest for P5B.

I chose to use 'stress' program as it's command-line based. Don't have the ubuntu server setup with a GUI or had VNC setup to run any GUI apps.

The idea of overclocking Q6600 didn't cross my mind, and is an excellent one!! I will have to give that a shot sometime.  ATM I've got a stable ubuntu 8.03.4 server with Q9550+P5B (OCZ DDR2 RAM) and I'm a happy camper :)  Q6600 has gone back in the P5E3 Duluxe WIFI board (primarily used as HTPC).

---

