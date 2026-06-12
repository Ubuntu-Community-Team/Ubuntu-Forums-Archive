---
title: "DMRaid Lost Partition Table"
date: 2007-08-23
forum: x86 64-bit Users (Pre April '08)
---

### Post by locque on 2007-08-23
I have 2 WD Raptor Drives 74GB Each that I am running a dual boot machine (Win-blows and Ubuntu) with dmraid and kernel version 2.6.15-27-amd64-k8. I was trying to update the kernel but because I am missing the partition table on one of the drives, it seems as though the NEW dmraid for the initrd is not able to properly find the array. I don't want to have to reinstall everything, although that is about where I am at. 

I was hoping that I could recover/recreate my partitions so that I can avoid the whole reinstallation mess..

The wierd thing is, that the machine works fine now. Ubuntu starts, Winblows starts, although lately Kubuntu has been freezing... So anyways, the array is there and working even though one drive has a corrupt partition table....

Any ideas???

---

### Post by kuja on 2007-08-23
You could try to use testdisk. That'd be the first place I'd start anyhow.

---

### Post by locque on 2007-08-24
Thanks for the tip!!!

Ok so here is what I got from the testdisk.log:

[HTML]Fri Aug 24 07:01:26 2007
Command line: TestDisk

TestDisk 6.5, Data Recovery Utility, October 2006
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org
Linux version (ext2fs lib: 1.40-WIP, ntfs lib: avaible, reiserfs lib: none)
Using locale 'C'.
file_read(4,4,buffer,0(0/0/1)) read err: Input/output error
Hard disk list
Disk /dev/hda - 316 MB / 301 MiB - CHS 10 255 63 (RO), sector size=2048
Disk /dev/hdb - 320 MB / 305 MiB - CHS 10 255 63 (RO), sector size=2048
Disk /dev/sda - 74 GB / 69 GiB - CHS 9039 255 63, sector size=512
Disk /dev/sdb - 74 GB / 69 GiB - CHS 9039 255 63, sector size=512
Disk /dev/sdc - 122 GB / 114 GiB - CHS 14946 255 63, sector size=512

Disk /dev/sdb - 74 GB / 69 GiB
Partition table type: Intel

Analyse Disk /dev/sdb - 74 GB / 69 GiB - CHS 9039 255 63
Current partition structure:

Partition sector doesn't have the endmark 0xAA55

search_part()
Disk /dev/sdb - 74 GB / 69 GiB - CHS 9039 255 63

Results

interface_write()

No partition found or selected for recovery

search_part()
Disk /dev/sdb - 74 GB / 69 GiB - CHS 9039 255 63

Results

interface_write()

No partition found or selected for recovery
simulate write!

write_mbr_i386: starting...
Store new MBR code
write_all_log_i386: starting...
No extended partition

TestDisk exited normally.


Fri Aug 24 07:08:44 2007
Command line: TestDisk

TestDisk 6.5, Data Recovery Utility, October 2006
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org
Linux version (ext2fs lib: 1.40-WIP, ntfs lib: avaible, reiserfs lib: none)
Using locale 'C'.
file_read(4,4,buffer,0(0/0/1)) read err: Input/output error
Hard disk list
Disk /dev/hda - 316 MB / 301 MiB - CHS 10 255 63 (RO), sector size=2048
Disk /dev/hdb - 320 MB / 305 MiB - CHS 10 255 63 (RO), sector size=2048
Disk /dev/sda - 74 GB / 69 GiB - CHS 9039 255 63, sector size=512
Disk /dev/sdb - 74 GB / 69 GiB - CHS 9039 255 63, sector size=512
Disk /dev/sdc - 122 GB / 114 GiB - CHS 14946 255 63, sector size=512

Disk /dev/sda - 74 GB / 69 GiB
Partition table type: Intel

Analyse Disk /dev/sda - 74 GB / 69 GiB - CHS 9039 255 63
Geometry from i386 MBR: head=255 sector=63
check_part_i386 failed for partition type 07
check_part_i386 failed for partition type 83
check_part_i386 failed for partition type 83
get_geometry_from_list_part_aux head=255 nbr=8
get_geometry_from_list_part_aux head=8 nbr=1
get_geometry_from_list_part_aux head=16 nbr=1
get_geometry_from_list_part_aux head=32 nbr=1
get_geometry_from_list_part_aux head=64 nbr=1
get_geometry_from_list_part_aux head=128 nbr=1
get_geometry_from_list_part_aux head=240 nbr=1
get_geometry_from_list_part_aux head=255 nbr=8
Current partition structure:
 1 P Linux                    0   1  1  8973 254 63  144167247
Invalid NTFS boot
 2 * HPFS - NTFS           8974   0  1 12621 254 63   58605120
 2 * HPFS - NTFS           8974   0  1 12621 254 63   58605120
No EXT2, JFS, Reiser, cramfs or XFS marker
 3 P Linux                17948   0  1 18078 254 63    2104515
 3 P Linux                17948   0  1 18078 254 63    2104515
No EXT2, JFS, Reiser, cramfs or XFS marker
 4 P Linux                12622   0  1 17947 254 63   85562190
 4 P Linux                12622   0  1 17947 254 63   85562190

search_part()
Disk /dev/sda - 74 GB / 69 GiB - CHS 9039 255 63

recover_EXT2: s_block_group_nr=0/549, s_mnt_count=288/32, s_blocks_per_group=32768
recover_EXT2: boot_sector=0, s_blocksize=4096
recover_EXT2: s_blocks_count 18020905
recover_EXT2: part_size 144167240
   D Linux                    0   1  1  8973 254 56  144167240
     EXT3 Large file Sparse superblock Recover, 73 GB / 68 GiB
get_geometry_from_list_part_aux head=255 nbr=2
get_geometry_from_list_part_aux head=8 nbr=1
get_geometry_from_list_part_aux head=16 nbr=1
get_geometry_from_list_part_aux head=32 nbr=1
get_geometry_from_list_part_aux head=64 nbr=1
get_geometry_from_list_part_aux head=128 nbr=1
get_geometry_from_list_part_aux head=240 nbr=1
get_geometry_from_list_part_aux head=255 nbr=2

Results
   * Linux                    0   1  1  8973 254 63  144167247
     EXT3 Large file Sparse superblock Recover, 73 GB / 68 GiB

interface_write()
 1 * Linux                    0   1  1  8973 254 63  144167247
simulate write!

write_mbr_i386: starting...
write_all_log_i386: starting...
No extended partition

TestDisk exited normally.
[/HTML]

I don't know if you can tell from the output, but it seems like it shows no partitions on /dev/sdb which is the problem that I've been having. My fakeRAID is made up of /dev/sda and /dev/sdb... Anything look out of the ordinary? I will try booting to a live CD and running on the unmounted drive without activating the raid array also...

---

### Post by locque on 2007-08-24
Just for completeness sakes... This is the result for ```
dmesg | grep sd
``` that caused me to be concerned:
[HTML][   31.388559] Driver 'sd' needs updating - please use bus_type methods
[   31.391023] SCSI device sda: 145226112 512-byte hdwr sectors (74356 MB)
[   31.391035] SCSI device sda: drive cache: write back
[   31.393061] SCSI device sda: 145226112 512-byte hdwr sectors (74356 MB)
[   31.393073] SCSI device sda: drive cache: write back
[   31.393077]  sda: sda1 sda2 sda3 sda4
[   31.402867] sd 0:0:0:0: Attached scsi disk sda
[   31.402908] SCSI device sdb: 145226112 512-byte hdwr sectors (74356 MB)
[   31.403800] SCSI device sdb: drive cache: write back
[   31.405738] SCSI device sdb: 145226112 512-byte hdwr sectors (74356 MB)
[   31.405749] SCSI device sdb: drive cache: write back
[   31.405752]  sdb: unknown partition table
[   31.410919] sd 1:0:0:0: Attached scsi disk sdb
[   31.445429] Buffer I/O error on device sda2, logical block 7325616
[   31.445446] Buffer I/O error on device sda2, logical block 7325616
[   31.445451] Buffer I/O error on device sda3, logical block 2104320
[   31.445453] Buffer I/O error on device sda3, logical block 2104321
[   31.445456] Buffer I/O error on device sda3, logical block 2104322
[   31.445458] Buffer I/O error on device sda3, logical block 2104323
[   31.445460] Buffer I/O error on device sda3, logical block 2104324
[   31.445463] Buffer I/O error on device sda3, logical block 2104325
[   31.445465] Buffer I/O error on device sda3, logical block 2104326
[   31.445467] Buffer I/O error on device sda3, logical block 2104327
[   41.165429] SCSI device sdc: 240119808 512-byte hdwr sectors (122941 MB)
[   41.165432] sdc: assuming drive cache: write through
[   41.166155] SCSI device sdc: 240119808 512-byte hdwr sectors (122941 MB)
[   41.166157] sdc: assuming drive cache: write through
[   41.166160]  sdc: sdc1
[   41.203011] sd 4:0:0:0: Attached scsi disk sdc
[   46.365323] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   46.365345] sd 1:0:0:0: Attached scsi generic sg1 type 0
[   46.365367] sd 4:0:0:0: Attached scsi generic sg2 type 0
[   47.031770] Buffer I/O error on device sda2, logical block 7325616
[   47.031804] Buffer I/O error on device sda2, logical block 7325616
[   47.031809] Buffer I/O error on device sda4, logical block 42780992
[   55.574153] Buffer I/O error on device sda2, logical block 7325616
[/HTML]

sda and sdb are the Raptor drives with sdc being a USB attached Maxtor drive...

---

### Post by kuja on 2007-08-24
I guess I should have been a tad more specific, first, fire up a live cd and (using apt) install dmraid and testdisk. If dmraid isn't picking up anything at all you might be screwed. Next things next, run a command like this "sudo testdisk /dev/mapper/randomgibberish"

If your raid drive isn't showing up in /dev/mapper, I'm not sure what to say, but that's not good. 

Also, if you look at the devices /dev/sda/b you shouldn't be able to see any partition information, that's normal.

---

