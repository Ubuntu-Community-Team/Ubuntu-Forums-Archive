---
title: "Getting Kernel Oops after command &quot;ls -la /&quot; (or any other mountpoints)"
date: 2008-09-18
forum: x86 64-bit Users
---

### Post by gabolander on 2008-09-18
Hi there,

I have a system like following:
PC "Phenom"
- Cpu **AMD Phenom 9500** (Quad-Core 64bit 2.2Ghz per core)
- Mobo **Asus M3A** :
[SIZE="1"][LIST]
[*]Host bridge: ATI Technologies Inc RX780/RX790 Chipset Host Bridge
[*]PCI bridge: ATI Technologies Inc RD790 PCI to PCI bridge
[*]SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
[*]USB Controller: ATI Technologies Inc SB600 USB (0-4) + Controller EHCI
[*]SMBus: ATI Technologies Inc SBx00 SMBus Controller
[*]IDE interface: ATI Technologies Inc SB600 IDE
[*]Audio device: ATI Technologies Inc SBx00 Azalia
[*]ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
[*]PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
[*]Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] HyperTransport Configuration, Address Map, DRAM Controller, Miscellaneous Control, Link Control
[*]Ethernet controller: Attansic Technology Corp. L1 Gigabit Ethernet Adapter
[/LIST][/SIZE]
- 2 GB **DDR2 667** Kingston
- **300~ GB HD** Maxtor 6V300F0 **SATA**  (Sata port # 1)
- **500~ GB HD** Seagate ST3500630AS **SATA** (Sata port # 2)
- **300~ GB HD Maxtor** 6V300F0 **SATA** (Sata port # 3)
- LG DVD-RAM dual Layer x20
- Video card **NVidia GeForce 8500GT**
- **Hauppauge WinTV PCI** Brooktree Corporation Bt878 TV/Radio card

I successfully installed a **_Ubuntu 8.04.1 64bit _**(amd64) constantly updated, with **kernel 2.6.24.19-generic** (but _I also reproduced the problem with customized vanilla kernel 2.6.26.5_).
As you may see in my PC configuration reported above, I have 3HD with mixed partitions types (both ext3 and reiserfs).
first hd is sda (with boot & root partitions), second is sdb, the third sdc.
My */etc/fstab* is like the following:

```
[FONT="Courier New"][COLOR="Blue"]# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=5ae1dcc3-90f9-4112-82af-6005c0012d71 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdc1
# UUID=8769c7d0-e35b-46c6-a25d-8ee98aed959d /OtherDistro    ext3    noauto,relatime   0   2
# /dev/sda2
UUID=0690592c-4a55-4d9b-b1da-7bf00d52ba29 /boot           ext3    relatime        0       2
# /dev/sdc6
UUID=2d8c1d97-86a9-4935-b0c4-90e124b6f8f3 /extra          reiserfs relatime,notail,noatime        0       2
# /dev/sdb10
UUID=7d487754-97da-434d-941e-cf51bc425945 /extra10        reiserfs relatime,notail,noatime        0       2
# /dev/sdb9
UUID=ad0f07be-0daa-41f8-8821-baad89d2fac2 /extra9         reiserfs relatime,notail,noatime        0       2
# /dev/sdb7
UUID=df6270cf-18f6-48c9-8f03-57ab9c35e18d /home           reiserfs relatime,notail,noatime        0       2
# /dev/sdb8
UUID=721ce6ce-713f-4fec-bb69-f278aac5047c /opt            reiserfs relatime,notail,noatime        0       2
# /dev/sda1
UUID=56804F91804F7711 /windows/C      ntfs    defaults,umask=007,gid=46 0       1
# /dev/sdc5
UUID=44C2-549C  /windows/D      vfat    utf8,umask=007,gid=46 0       1
# /dev/sda3
UUID=2b6dfc7d-f688-42b8-8883-f7ade72a7834 none            swap    sw              0       0
# /dev/sdb5
# UUID=06ed8cae-d2a7-46bd-a0f7-109b9ce12acb none            swap    sw              0       0
# /dev/sdc2
# UUID=5ee302b6-0f26-4a7e-918e-93891e30b22f none            swap    sw              0       0
# /dev/hda        /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0


# default for cdrom
/dev/scd0        /media/dvd0   udf,iso9660 user,noauto,exec,utf8 0       0[/COLOR]
[/FONT]
```


[SIZE="3"]**_Here the problem:_**[/SIZE]
When I open a terminal, and I enter the command .i.e. (both with root and standard user) "***ls -la /***", I get "***Killed***" and nothing else.. but if I see data by issueing '*dmesg*' command (or if I enter the command in a terminal screen such as /dev/tty1 or 2), the system shows me the **_kernel oops_** like the following:


```
[FONT="Courier New"][SIZE="1"][15009.355733] **_Unable to handle kernel paging request_** at 00000000619383d8 RIP:
[15009.355742]  [<ffffffff88cd7843>] :**reiserfs:sprintf_le_key+0x13/0x3d0**
[15009.355761] PGD 11c0a067 PUD 0
[15009.355765] **Oops**: 0000 [2] SMP
[15009.355768] CPU 3
[15009.355770] Modules linked in: binfmt_misc rfcomm l2cap bluetooth vboxdrv ppdev cpufreq_userspace cpufreq_powersave cpufreq_ondemand cpufreq_stats freq_table cpufreq_conservative dock video output container sbs sbshc battery iptable_filter ip_tables x_tables deflate zlib_deflate twofish twofish_common camellia serpent blowfish des_generic cbc ecb blkcipher xcbc sha256_generic sha1_generic crypto_null af_key nls_iso8859_1 nls_cp437 vfat fat reiserfs aes_x86_64 dm_crypt dm_mod ac parport_pc lp parport ipv6 bt878 tuner tea5767 tda8290 tuner_simple mt20xx tea5761 tvaudio msp3400 bttv ir_common compat_ioctl32 snd_hda_intel i2c_algo_bit videobuf_dma_sg videobuf_core btcx_risc tveeprom snd_hwdep nvidia(P) atl1 videodev usblp mii snd_bt87x snd_seq_dummy psmouse v4l2_common v4l1_compat snd_pcm_oss snd_mixer_oss snd_seq_oss serio_raw snd_seq_midi snd_rawmidi snd_pcm snd_seq_midi_event snd_page_alloc snd_seq snd_timer snd_seq_device snd shpchp pci_hotplug i2c_piix4 i2c_core button soundcore pcspkr evdev ext3 jbd mbcache sg usb_storage libusual sr_mod cdrom sd_mod atiixp ide_core ata_generic pata_acpi usbhid hid floppy pata_atiixp ehci_hcd ahci ohci_hcd libata scsi_mod usbcore thermal processor fan fuse vesafb fbcon tileblit font bitblit softcursor
[15009.355839] Pid: 16159, comm: **ls** Tainted: **P **     D **2.6.24-19-generic** #1
[15009.355841] RIP: 0010:[<ffffffff88cd7843>]  [<ffffffff88cd7843>] :**reiserfs:sprintf_le_key+0x13/0x3d0**
[15009.355853] RSP: 0018:ffff81007c4d1ad8  EFLAGS: 00010202
[15009.355855] RAX: 0000000000000028 RBX: 00000000619383d0 RCX: ffffffff88cfe2c8
[15009.355857] RDX: ffff81007c4d1bf8 RSI: 00000000619383d0 RDI: ffffffff88cfe2da
[15009.355858] RBP: ffff81007c4d1bb8 R08: 00000000619383d0 R09: 0000000000000000
[15009.355860] R10: 0000000000000002 R11: 000000006193535d R12: ffffffff88cfe2da
[15009.355862] R13: ffffffff88cfe6a0 R14: ffffffff88cfe2a0 R15: ffffffff88cfe6cc
[15009.355864] FS:  00007fde201db780(0000) GS:ffff81007dc01d00(0000) knlGS:00000000f4833b90
[15009.355866] CS:  0010 DS: 0000 ES: 0000 CR0: 000000008005003b
[15009.355867] CR2: 00000000619383d8 CR3: 0000000060abc000 CR4: 00000000000006e0
[15009.355869] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
[15009.355870] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
[15009.355872] Process ls (pid: 16159, threadinfo ffff81007c4d0000, task ffff810003b52000)
[15009.355874] Stack:  0000000000000001 ffff81007c4d1bb8 000000000000006b ffffffff88cd7ea9
[15009.355878]  0000000000000000 ffffffff802d7bd1 0000000000000000 ffff81000c3384e0
[15009.355881]  ffff81000c3384e0 ffffffff802d8080 0000004400000000 ffff81007e6ec8b8
[15009.355884] Call Trace:
[15009.355903]  [<ffffffff88cd7ea9>] :reiserfs : prepare_error_buf+0x2a9/0x5a0
[15009.355915]  [<ffffffff802d7bd1>] set_bh_page+0x21/0x50
[15009.355923]  [<ffffffff802d8080>] alloc_page_buffers+0x60/0xe0
[15009.355949]  [<ffffffff88cd77e0>] :reiserfs:reiserfs_warning+0x50/0xa0
[15009.355961]  [<ffffffff88ccb120>] :reiserfs:reiserfs_readpage+0x0/0x10
[15009.355969]  [<ffffffff80285319>] add_to_page_cache+0xb9/0xd0
[15009.355982]  [<ffffffff802854fd>] read_cache_page_async+0xed/0x150
[15009.356004]  [<ffffffff88cea3c1>] :reiserfs:reiserfs_xattr_get+0x201/0x250
[15009.356025]  [<ffffffff88ce976c>] :reiserfs:reiserfs_getxattr+0xbc/0xf0
[15009.356033]  [<ffffffff802d1276>] vfs_getxattr+0xb6/0x100
[15009.356043]  [<ffffffff802d1354>] getxattr+0x94/0x170
[15009.356075]  [<ffffffff802bdfea>] do_path_lookup+0x8a/0x250
[15009.356078]  [<ffffffff802bcb89>] getname+0x1a9/0x220
[15009.356092]  [<ffffffff802d149b>] sys_lgetxattr+0x6b/0xb0
[15009.356115]  [<ffffffff80468699>] error_exit+0x0/0x51
[15009.356124]  [<ffffffff8020c37e>] system_call+0x7e/0x83
[15009.356141]
[15009.356142]
[15009.356143] Code: 48 8b 46 08 48 c1 e8 3c 3c 03 77 18 89 c2 b9 01 00 00 00 83
[15009.356149] RIP  [<ffffffff88cd7843>] :**reiserfs:sprintf_le_key**+0x13/0x3d0
[15009.356157]  RSP <ffff81007c4d1ad8>
[15009.356158] CR2: 00000000619383d8
[15009.356162] ---[ end trace e5f0e83396d21ee3 ]---[/SIZE][/FONT]
```


Now, I get the same error entering "*ls -la*" in other directories, most times corresponding to mountpoints, such as "*ls -la /opt*" or "*ls -la /extra*" in my case ..
If I run only "ls" ( w/o -l ) the problem doesn't occur. In other cases, such as listing, directory over 2 or more levels of depth,  problem doesn't occur.
The weird thing, imho, that I get a kernel ops that refers to a reiserfs error _even if I ask a listing on a ext3_ partition ... (reiserfs module bug?).
When I get the  Oops, the system keeps working correctly all the time, except that in the next system boot I may have some "Filesystem NOT clean", or anyway "Filesystem clean" messages, but some "Transiction replied " on some reiser filesystems inodes.

I'll be very grateful to anyone would give me some help to solve this annoying matter.

PS. If someone wants to have more details (such as hw list, command outputs and so on), please let me now.

Thanks in advance.
[SIZE="4"][B][B][I]
_Gabo_[/I][/B][/B][/SIZE] ):P

---

### Post by IntuitiveNipple on 2008-09-18
Can't help you with your specific problem, although from the stack-trace it looks like there's a Reiser partition with corruption, or the driver is failing to allocate memory. Have you performed a **reiserfsck** on the unmounted partitions?

I've been trying to help another user that has a system with the Nvidia 8900GT and who can't get the driver to load. I noticed your system has that chip-set. If you are using the Nvidia proprietary driver (nvidia-glx-new) could you attach the /etc/X11/xorg.conf of the system to the other user's thread so he can compare the contents with his system? The thread is [8500GT Problem - 14 hours into this](http://ubuntuforums.org/showthread.php?t=915268)

---

### Post by andysmith3 on 2008-09-18
helloreplica.com  provides a wide array of [Replica Watches](http://www.helloreplica.com/) and professional customer sevrice, our goal is to make every customer 100% satsfied. We are more than ready to show our unique prowess and fortes to gain our footing. And we also provide fast delivery service, we guarantee our listing price is lower than other competitor. welcome to oursite  [Replica Rolex Watches](http://www.helloreplica.com/)  [Rolex Watches](http://www.rolex2u.com/)   [replica rolex watches](http://www.rolex2u.com/) [replica rolex](http://www.rolex2u.com/)

---

