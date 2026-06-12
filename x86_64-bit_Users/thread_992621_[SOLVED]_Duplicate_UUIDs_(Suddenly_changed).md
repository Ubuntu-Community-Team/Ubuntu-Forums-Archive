---
title: "[SOLVED] Duplicate UUIDs (Suddenly changed?)"
date: 2008-11-24
forum: x86 64-bit Users
---

### Post by paradexes on 2008-11-24
I have an MDADM array I am running on Ubuntu 8.10 x64. I have an awful lot of data on there. I was running a software RAID5 setup.

After doing some troubleshooting I discovered that when I ran blkid 5 of my drives are showing up with the same UUID? This is odd as they used to be unique. Is there a way to fix this?

Here is the blkid output. 

```
/dev/sda1: UUID="ee96f702-12ef-4ab6-ac23-cc348408e1fe" TYPE="ext3" SEC_TYPE="ext2" 
/dev/sdm1: UUID="cb15fa5b-c72e-2d13-d7aa-239bd1dd4465" TYPE="mdraid" 
/dev/sdn1: UUID="cb15fa5b-c72e-2d13-d7aa-239bd1dd4465" TYPE="mdraid" 
/dev/sdi1: UUID="780091F70091BD16" LABEL="New Volume" TYPE="ntfs" 
/dev/sdj1: UUID="cb15fa5b-c72e-2d13-d7aa-239bd1dd4465" TYPE="mdraid" 
/dev/sdg1: UUID="780091F70091BD16" LABEL="New Volume" TYPE="ntfs" 
/dev/sdh1: SEC_TYPE="msdos" UUID="1C3F-D299" TYPE="vfat" 
/dev/sdm5: TYPE="swap" UUID="e190574e-326e-4b8b-b757-9b56a963a35f" 
/dev/sdb1: UUID="ba2bbb37-5111-4f08-8cb3-c78f64f16e3e" TYPE="reiserfs" 
/dev/sdc1: UUID="9e468ea2-a188-44b3-8b28-a60e5e3174be" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdd1: UUID="42d8e45d-9aae-4878-b00f-fa25b0e69db7" TYPE="reiserfs" 
/dev/sdg5: TYPE="swap" UUID="e190574e-326e-4b8b-b757-9b56a963a35f" 
/dev/sda5: TYPE="swap" UUID="e190574e-326e-4b8b-b757-9b56a963a35f" 
/dev/sdf1: SEC_TYPE="msdos" UUID="1C3F-D299" TYPE="vfat" 
/dev/sdk1: UUID="cb15fa5b-c72e-2d13-d7aa-239bd1dd4465" TYPE="mdraid" 
/dev/sdl1: UUID="cb15fa5b-c72e-2d13-d7aa-239bd1dd4465" TYPE="mdraid" 
/dev/sdo1: UUID="48adc5bf-d7f3-485f-b2f1-d4dac88a8c54" TYPE="ext3" 

```

Note that only the mdraid devices have the duplication issue. Could this be due to some raid5 related bug? 

This is really really strange. It was working fine for the last few months. I came home from work and suddenly it stopped working. No errors other than the unmounted volume were issues. 

I would like to be able to rebuild my drives and retrieve my data if at all possible. It seems like it is possible. I have been doing some searching and the answers I have found have been incomplete or not applicable here. 

I tried 

```
root@****:~# mdadm --assemble --scan
mdadm: No arrays found in config file
```

I also tried to change the UUID and got the following:

```
root@*****:~# tune2fs -U random /dev/sdk1
tune2fs 1.41.3 (12-Oct-2008)
tune2fs: Bad magic number in super-block while trying to open /dev/sdk1
Couldn't find valid filesystem superblock.
root@paradexes:~# tune2fs -U random /dev/sdk
tune2fs 1.41.3 (12-Oct-2008)
tune2fs: Bad magic number in super-block while trying to open /dev/sdk
Couldn't find valid filesystem superblock.

```

I should also note that the UUID for the /dev/md0 array used to exist. Now it just doesn't 
This is what happens when I run mount -a (this was in my fstab from the day I set up the array)

```
root@*****:~# mount -a
mount: special device /dev/disk/by-uuid/8ab2e558-6e0a-475b-81cb-913ca22035e4 does not exist

``` 

Any additional help here would be greatly appreciated. Thanks this community :guitar:

---

### Post by cariboo on 2008-11-25
If you run:

```
sudo blkid -s none
```

to refresh blkid.tab. This will straighten out the duplicates.

Jim

---

### Post by paradexes on 2008-11-25
That did not work. Any other suggestions? :P

I am sort of at the end of my rope here. I am pretty sure this can be fixed I just don't know how.

---

### Post by paradexes on 2008-11-25
Ok I fixed the issue. This appears to be a bug with the latest mdadm. 

Reverting to an older version (in my case 2.6.3 x64) worked just fine for me. I locked it so I dont update to that again. 

[http://ubuntuforums.org/showthread.php?t=107856&page=3](http://ubuntuforums.org/showthread.php?t=107856&page=3)

The bug is severe enough to be a problem. But I think as long as this workaround is well published and it should address the issue until an actual fix is released.

---

