---
title: "RAID Failed in middle of upgrade-ish"
date: 2008-10-30
forum: x86 64-bit Users
---

### Post by redbullmonsta on 2008-10-30
Hi All

Well i was brave (stupid)

I chose to login over ssh to my PC at home and upgrade from 8.04 to 8.10 (woooooo Ibex)

I changed the necessary file - cant remember which one, and ammended

```
prompt=lts 
``` 
to
```
prompt=normal
```

then ran 

```
do-release-upgrade
```

All was going well until

```
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.27-7-generic
ERROR lilo fails for new /boot/initrd.img-2.6.27-7-generic:

Warning: LBA32 addressing assumed
Fatal: Not all RAID-1 disks are active; use '-H' to install to active disks only
dpkg: subprocess post-installation script returned error exit status 1

*** The package "linux-restricted-modules-2.6.27-7-generic" failed to install or upgrade.

You can help the developers to fix the package by reporting the problem.

What would you like to do? Your options are:
  R: Report Problem...
  C: Cancel
Please choose (R/C):
```

So apparently i have lost a disk in my RAID array

so i check with 

```
root@redbull:~# cat /proc/mdstat

Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md7 : active raid1 sdf3[0]
      236251776 blocks [2/1] [U_]

md6 : active raid1 sdf2[0]
      128448 blocks [2/1] [U_]

md5 : active raid1 sdf1[0]
      7815488 blocks [2/1] [U_]

md4 : active raid5 sda1[0] sde1[4] sdd1[3] sdc1[2] sdb1[1]
      1250274304 blocks level 5, 64k chunk, algorithm 2 [5/5] [UUUUU]
```

So looks like a disk is offline, however if i do 

```
root@redbull:~# hdparm -Tt /dev/sdg1

/dev/sdg1:
 Timing cached reads:   6986 MB in  2.00 seconds = 3495.35 MB/sec
 Timing buffered disk reads:  176 MB in  3.01 seconds =  58.49 MB/sec
root@redbull:~# hdparm -Tt /dev/sdf1

/dev/sdf1:
 Timing cached reads:   7598 MB in  2.00 seconds = 3801.55 MB/sec
 Timing buffered disk reads:  176 MB in  3.01 seconds =  58.52 MB/sec
```

So the drives for my RAID 1 are online - erm help ! lol

How do i get the upgrade to continue.... i am guessing it will be best to fix the RAID after upgrade

how can i do this

```
ERROR lilo fails for new /boot/initrd.img-2.6.27-7-generic:

Warning: LBA32 addressing assumed
Fatal: Not all RAID-1 disks are active; use '-H' to install to active disks only
```

when all i have is the option

```
What would you like to do? Your options are:
  R: Report Problem...
  C: Cancel
Please choose (R/C):
```

Sorry for the long post

Thanks in advance

---

### Post by intel on 2008-10-30
nothing is wrong with your RAID 1
but you only have boot partition on 1 drive(master, md0 etc..)

let the install finish

then manually install grub on the other disk

something like 
```
#grub install /dev/sd[x]
```

---

### Post by intel on 2008-10-30
whoops ... looks like you are using lilo,

also it failed because we can't have /boot in a RAID partition, etc etc

& again ... why are you using lilo...thats so '90s

---

### Post by redbullmonsta on 2008-10-30
Hi, thanks for the replies...
> 
 nothing is wrong with your RAID 1

so why 

```
md7 : active raid1 sdf3[0]
      236251776 blocks [2/1] [U_]

md6 : active raid1 sdf2[0]
      128448 blocks [2/1] [U_]

md5 : active raid1 sdf1[0]
      7815488 blocks [2/1] [U_]
```

1 disk _**is**_ offline

> 
also it failed because we can't have /boot in a RAID partition, etc etc

I am afraid you _**can**_ have raid 1 for /boot (raid 0 and raid 5 are unsupported) the key is to have both drives listed in your lilo/grub/yaboot.conf files in case of drive failure.

> & again ... why are you using lilo...thats so '90s

I had an issue with Grub which is a bit long winded, lilo works well for me (or did until now lol), i agree i would prefer grub, but lilo was the only boot loader i could get working.

---

### Post by redbullmonsta on 2008-10-30
OK i found out how to rpair my raid... if anyone else needs to know heres what to do

Check the status with of your raid as i did with 

```
cat /proc/mdstat
```

you can check individual md devices with 

```
mdadm -D /dev/md#
```

if the drive is acctually working - i verified mine was, with hdparm...

now my raid1 partitions / /boot and swap are on /dev/sdf and /dev/sdg

/dev/sdg was missing so i done 
```

root@redbull:~# mdadm /dev/md6 -a /dev/sdg2
mdadm: re-added /dev/sdg2
root@redbull:~# mdadm /dev/md7 -a /dev/sdg3
mdadm: re-added /dev/sdg3
root@redbull:~# mdadm /dev/md5 -a /dev/sdg1
mdadm: re-added /dev/sdg1
```

now raid is repairing

```
root@redbull:~# cat /proc/mdstat 
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md7 : active raid1 sdg3[2] sdf3[0]
      236251776 blocks [2/1] [U_]
      [=>...................]  recovery =  6.4% (15281792/236251776) finish=103.6min speed=35544K/sec
      
md6 : active raid1 sdg2[1] sdf2[0]
      128448 blocks [2/2] [UU]
      
md5 : active raid1 sdg1[2] sdf1[0]
      7815488 blocks [2/1] [U_]
      	resync=DELAYED
      
md4 : active raid5 sda1[0] sde1[4] sdd1[3] sdc1[2] sdb1[1]
      1250274304 blocks level 5, 64k chunk, algorithm 2 [5/5] [UUUUU]
      
unused devices: <none>

```

Update:
And this morning i finished the upgrade, and Intel you will notice Lilo updated both /boot partitions in my raid1 ;)

```
The Master boot record of  /dev/sdf  has been updated.
Warning: /dev/sdg is not on the first disk
The Master boot record of  /dev/sdg  has been updated.
```

---

