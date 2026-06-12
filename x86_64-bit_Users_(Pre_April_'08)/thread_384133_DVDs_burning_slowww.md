---
title: "DVDs burning slowww"
date: 2007-03-14
forum: x86 64-bit Users (Pre April '08)
---

### Post by sir_real on 2007-03-14
Hi,

I'm just starting to burn DVDs in Dapper Drake. While they burn successfully, it takes upwards of half an hour or more. 

I've tried burning with both Gnomebaker and Nautilus. I've tried both 16x single layers disks and 8x double layer disks. My burner is rated for these speeds. When burning I have tried both selecting maximum speed and the appropriate speed for the the disk I happen to be burning (16 or 8x).

No matter what, it takes half an hour or longer when it should take 10 minutes or less.

Any ideas?

Dapper 6.06 64-bit
SONY_DVD_RW_DW_Q30A

---

### Post by Kilz on 2007-03-14
> **sir_real said:**
> Hi,

I'm just starting to burn DVDs in Dapper Drake. While they burn successfully, it takes upwards of half an hour or more. 

I've tried burning with both Gnomebaker and Nautilus. I've tried both 16x single layers disks and 8x double layer disks. My burner is rated for these speeds. When burning I have tried both selecting maximum speed and the appropriate speed for the the disk I happen to be burning (16 or 8x).

No matter what, it takes half an hour or longer when it should take 10 minutes or less.

Any ideas?

Dapper 6.06 64-bit
SONY_DVD_RW_DW_Q30A

You could try k3b.

---

### Post by sir_real on 2007-03-14
> **Kilz said:**
> You could try k3b.

Thanks, but the problem would not appear to be application specific. Also, the the discs burn slow whether I'm burning an image, VIDEO_TS folder, or just plain data disks. 

I don't think a DVD authoring program is going to solve the problem.

---

### Post by John Jason Jordan on 2007-03-14
> **sir_real said:**
> Thanks, but the problem would not appear to be application specific. Also, the the discs burn slow whether I'm burning an image, VIDEO_TS folder, or just plain data disks. 
I don't think a DVD authoring program is going to solve the problem.
You are probably right, but try K3b anyway. It only takes a moment to install and it will shut up those who think the problem is in Gnomebaker and Nautilus.

As for where the problem really lies, I'd bet it is in how Ubuntu is seeing your DVD drive. I'd suggest running "dmesg | less" from the command line (hit spacebar to page down). Scan through the lines and see if something pops up that looks suspicious. Copy and paste here any lines that are questionable (but not the whole thing!).

---

### Post by sir_real on 2007-03-14
> **John Jason Jordan said:**
> You are probably right, but try K3b anyway. It only takes a moment to install and it will shut up those who think the problem is in Gnomebaker and Nautilus.

As for where the problem really lies, I'd bet it is in how Ubuntu is seeing your DVD drive. I'd suggest running "dmesg | less" from the command line (hit spacebar to page down). Scan through the lines and see if something pops up that looks suspicious. Copy and paste here any lines that are questionable (but not the whole thing!).

Installed K3b. Mistake. It installed all sorts of extra packages. (probably because it's a KDE app and I'm using Gnome) Then it wouldn't even load.

Here's my ouptut from "dmesg | less" or at least what seemed to be the relevant parts.

[   30.464745] NFORCE3-250: IDE controller at PCI slot 0000:00:08.0
[   30.464863] NFORCE3-250: chipset revision 162
[   30.464865] NFORCE3-250: not 100% native mode: will probe irqs later
[   30.464868] NFORCE3-250: BIOS didn't set cable bits correctly. Enabling workaround.
[   30.464870] NFORCE3-250: BIOS didn't set cable bits correctly. Enabling workaround.
[   30.464875] NFORCE3-250: 0000:00:08.0 (rev a2) UDMA133 controller
[   30.464884]     ide0: BM-DMA at 0xf900-0xf907, BIOS settings: hda:DMA, hdb:DMA
[   30.464893]     ide1: BM-DMA at 0xf908-0xf90f, BIOS settings: hdc:DMA, hdd:DMA
[   30.464900] Probing IDE interface ide0...
[   30.475077] Driver 'sd' needs updating - please use bus_type methods
[   30.478196] SCSI device sda: 586072368 512-byte hdwr sectors (300069 MB)
[   30.478209] SCSI device sda: drive cache: write back
[   30.480420] SCSI device sda: 586072368 512-byte hdwr sectors (300069 MB)
[   30.480432] SCSI device sda: drive cache: write back
[   30.480437]  sda: sda1
[   30.498743] sd 0:0:0:0: Attached scsi disk sda
[   30.498789] SCSI device sdb: 156301488 512-byte hdwr sectors (80026 MB)
[   30.499094] SCSI device sdb: drive cache: write back
[   30.503093] SCSI device sdb: 156301488 512-byte hdwr sectors (80026 MB)
[   30.506869] SCSI device sdb: drive cache: write back
[   30.506874]  sdb: sdb1
[   30.514477] sd 1:0:0:0: Attached scsi disk sdb
[   30.750742] hda: ST3160023A, ATA DISK drive
[   31.422071] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[   31.425636] Probing IDE interface ide1...
[   32.160341] hdc: LITE-ON DVD SOHD-16P9S, ATAPI CD/DVD-ROM drive
[   32.943009] hdd: SONY DVD RW DW-Q30A, ATAPI CD/DVD-ROM drive
[   32.999550] ide1 at 0x170-0x177,0x376 on irq 15
[   33.005985] hda: max request size: 1024KiB
[   33.013994] hda: 312581808 sectors (160041 MB) w/8192KiB Cache, CHS=19457/255/63, UDMA(100)
[   33.014238] hda: cache flushes supported
[   33.014373]  hda: hda1 hda2 < hda5 >
[   33.050362] hdc: ATAPI 48X DVD-ROM drive, 254kB Cache, UDMA(33)
[   33.050367] Uniform CD-ROM driver Revision: 3.20
[   33.053284] hdd: ATAPI 126X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache, UDMA(66)

[   44.766782] EXT3 FS on hda1, internal journal
[   44.932887] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
[   44.932890] md: bitmap version 4.39
[   45.319612] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: [email]dm-devel@redhat.com[/email]
[   45.610716] cdrom: open failed.
[   46.116307] cdrom: open failed.

---

### Post by Kilz on 2007-03-14
> **sir_real said:**
> Installed K3b. Mistake. It installed all sorts of extra packages. (probably because it's a KDE app and I'm using Gnome) Then it wouldn't even load.

The list is k3b trying to detect your drive. It should work regardeless of what desktop you are using. I am also on Dapper and Gnome and k3b starts. It takes awhile, but it dose start.

---

### Post by sir_real on 2007-03-15
> **Kilz said:**
> The list is k3b trying to detect your drive. It should work regardeless of what desktop you are using. I am also on Dapper and Gnome and k3b starts. It takes awhile, but it dose start.

I appreciate your help, but you're wrong again. K3b did not install correctly. I'm aware that KDE apps are *supposed* to work on Gnome. I'm glad it works on your system but it still has not come up on my system after more than an hour. But this is irrelevant since I'm not *trying* to get K3b to work. 

Also, the list has nothing to do with K3b.

---

### Post by John Jason Jordan on 2007-03-15
> **sir_real said:**
> I appreciate your help, but you're wrong again. K3b did not install correctly. I'm aware that KDE apps are *supposed* to work on Gnome. I'm glad it works on your system but it still has not come up on my system after more than an hour. But this is irrelevant since I'm not *trying* to get K3b to work. 
Also, the list has nothing to do with K3b.
OK, you have proved that Gnomebacker, K3b, and other applications are not the problem. I suspected they were not from the beginning, but now we know for a fact that they are not the issue.

Looking at your dmesg output, I think this is the problem:

[30.464900] Probing IDE interface ide0...
[ 30.475077] Driver 'sd' needs updating - please use bus_type methods

Unfortunately, I have no idea what to do to solve it. And I have a final exam in three days and can't take time to figure it out right now. But I'm convinced that that line is where the problem lies. Maybe google can help.

---

### Post by sir_real on 2007-03-15
> **John Jason Jordan said:**
> 

Unfortunately, I have no idea what to do to solve it. And I have a final exam in three days and can't take time to figure it out right now. But I'm convinced that that line is where the problem lies. Maybe google can help.

Thanks for the useful info. I'll see where I can go from here.

---

### Post by Kilz on 2007-03-15
> **sir_real said:**
> I appreciate your help, but you're wrong again. K3b did not install correctly. I'm aware that KDE apps are *supposed* to work on Gnome. I'm glad it works on your system but it still has not come up on my system after more than an hour. But this is irrelevant since I'm not *trying* to get K3b to work. 

Also, the list has nothing to do with K3b.

But my operating system and yours are the exact same thing, Ubuntu Dapper Drake 64bit. So it does point to some other problem, most likely the hardware.

---

### Post by sir_real on 2007-03-15
> **Kilz said:**
> But my operating system and yours are the exact same thing, Ubuntu Dapper Drake 64bit. So it does point to some other problem, most likely the hardware.

Which is what I've been trying to tell you all along: that it's not the burning software. Rather, there seems to be a problem with the way my drive is setup under Ubuntu.

Hence the following:
[30.464900] Probing IDE interface ide0...
[ 30.475077] Driver 'sd' needs updating - please use bus_type methods

If you, or anoyone else, can tell me what to do about this it would be much appreciated.

---

