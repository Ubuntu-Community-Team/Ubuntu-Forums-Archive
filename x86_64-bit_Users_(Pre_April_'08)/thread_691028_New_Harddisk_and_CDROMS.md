---
title: "New Harddisk and CDROMS"
date: 2008-02-08
forum: x86 64-bit Users (Pre April '08)
---

### Post by sepia-shots on 2008-02-08
Hi,

I've just added a 750Gb Hitachi Drive to my system and replaced two EIDE CDROMs (one a CDROM, One a DVD RW) with two sata Pioneer DVD RW's. 

Making my existing system (dual boot between 32/64bit Ubuntu)
2x Pioneer sata DVD RW's
1 x 120Gb Maxtor HD (has Ubuntu 32bit loaded)
1 x 250Gb (has Ubuntu 64bit loaded)
1 x 750Gb Hitachi (not formatted)

However fstab is showing

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=f341c3fd-4f2c-4b84-b915-e44a99476388 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=85d11e2a-6604-476d-a3f8-368be8ed2959 none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/hdb        /media/cdrom1   udf,iso9660 user,noauto,exec 0     

and if I look at my computer I see
CD-ROM1
CD-ROM2
CD RW/DVD Drive
108 Gb Volume (32bit Ubuntu drive)
Filesystem (64bit Ubuntu drive)

If I run a mount I get 

/dev/sdc1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
nfsd on /proc/fs/nfsd type nfsd (rw)
/dev/sdb1 on /media/disk type ext3 (rw,nosuid,nodev)

Questions
1) How do I get the 750Gb Drive recognised correctly and formatted (as ext3)
2) Why is one of the sata DVD drives showing as a CDROM

Regards

Pete

---

### Post by logos34 on 2008-02-08
Use Gparted to format the drive as ext3 and then follow [this guide ]("http://www.psychocats.net/ubuntu/mountlinux")to mount it.

read this also:
[https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)

Do the dvd drives otherwise work ok (read+write)?

---

### Post by sepia-shots on 2008-02-08
You're a star. 

The Harddisk is sorted now thanks. The DVD Roms will wait till tomorrow.

---

