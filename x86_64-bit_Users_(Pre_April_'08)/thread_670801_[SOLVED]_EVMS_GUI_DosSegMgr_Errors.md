---
title: "[SOLVED] EVMS GUI DosSegMgr Errors"
date: 2008-01-17
forum: x86 64-bit Users (Pre April '08)
---

### Post by DantePasquale on 2008-01-17
Hi All, I've upgraded my computer from 6.06LTS to 7.10 without any big problems (except for that pesky imap_ssl thingy). But, now when I run the EVMS GUI, evmsgui, I get the following error:

```
DosSegMgr: Errors were found with the partition information on drive sdd.

Due to the errors, the drive will appear as though all the partitions were removed, 
with just an mbr and freespace segments showing. blah, blah, blah ...
Committing this change will cause any existing partition information to be 
discarded and an empty partition table created on the drive. ....

Question: Would you like to mark the drive dirty 
so that the partitions can be discarded?
```

Well, of course I said "No". But what the f is this? 

```

/dev/sda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw)
/dev/evms/lv-home on /home type ext3 (rw)
/dev/evms/www on /var/www type ext3 (rw,noatime,usrquota,grpquota)
/dev/evms/lv-vm on /var/vm type ext3 (rw)
/dev/evms/lv-media on /var/media type ext3 (rw)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
/dev/sdd5 on /media/disk type ext3 (rw,nosuid,nodev)
/dev/sdd1 on /media/disk-1 type ext3 (rw,nosuid,nodev)
```
 
evms-engine.log attached.

---

### Post by Cappy on 2008-01-17
The first thing I would try would be running e2fsckon the partition

```
e2fsck -f /dev/sdd
```
or
```
e2fsck -f /dev/sdd1
```

--

If that doesn't do anything you may want to install a tool called "testdisk" which is very good at editing partition information. This should be a last resort option as I've had it fix the broken partition and overwrite another partition's information.

---

### Post by DantePasquale on 2008-01-18
Well, color me stupid, but /dev/sdd is a usb drive. This drive is actually the internal hard disk on my laptop that fried, wrapped in a usb case! It is from Ubuntu 6.06LTS. I guess the partition table is too weird being a hard drive that's mounted via usb device. I unmounted and unplugged and now I can run the evmsgui. 

_Followup question_: Should that device be in placed in the evms.conf ignore section? What if I do have a valid evms partition on a usb drive?

---

