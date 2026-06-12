---
title: "Ubuntu 8.04 Server &amp; MDADM"
date: 2008-07-11
forum: x86 64-bit Users
---

### Post by Krupski on 2008-07-11
Hi all,

I've got a homebuilt network attached storage box using Ubuntu v8.04 server, 64 bit on an Intel Core 2 Duo, Intel mobo based system. The storage is two 1TB SATA drives setup as RAID 1 (mirror).

It all works nicely, but I have one question:

When I do a fresh Linux install (on a small 4GB compact flash card) and then boot with the two blank HDD's attached and finally install MDADM (via APT-GET INSTALL), it *automatically* sets up a RAID 1 mirror system using my two blank 1TB drives.

Now, that's what I *want* by coincidence... but why does MDADM just assume and go off and do it that way? Note: I never run a command to setup a RAID device, MDADM just goes and does it all by itself and creates /dev/md0 out of my two drives.

What if I wanted a 2 TB stripe set instead? :confused:

-- Roger

---

### Post by Ocxic on 2008-07-12
mdadm will detect the drive RAID partitions and scan this for the setup. it will see that the drives have been setup as a RAID1 set and treat them as such. if you want different then you would have to erase the drives and setup a strip (RAID0) setup.

---

### Post by santhony on 2008-07-12
I'm trying to remove my raid5 build and cannot seem to get the drives out to format...

Will this fully remove the old array and allow me to rebuild?

sudo mdadm --stop /dev/md0
sudo mdadm --remove /dev/md0

Is there anything else needed to remove the RAID 5 and have my drives free again?

---

### Post by Krupski on 2008-07-12
> **Ocxic said:**
> mdadm will detect the drive RAID partitions and scan this for the setup. it will see that the drives have been setup as a RAID1 set and treat them as such. if you want different then you would have to erase the drives and setup a strip (RAID0) setup.

The thing is... the two drives were not setup as anything. They were both zero-filled and the motherboard raid was *not* used.

As far as Linux was concerned, they were two unpartitioned, unformatted drives just "sitting there" (/dev/sdb and /dev/sdc).

I just wondered why MDADM took it upon itself to setup those drives as a RAID 1 array without being told to?

Oh well... :confused:

---

### Post by santhony on 2008-07-12
I've had similiar experiences.. After totally tearing down the raid, formatting my drives....  They system will still pull up the old UUID after installing a new raid set...

I think the drives are stamped with previous raid information still....

Even if I move them to a new box that has never had mdadm installed, when I first installed mdadm, the UUID in mdadm.conf showed my previous ARRAY details, including 4 drives, which I only had installed 3 drives...  The 4 drives were from the old build....

I had totally removed, formated those drives before bringing over...

---

### Post by santhony on 2008-07-12
I just removed my whole raid 5 set, deleted the partitions, formated ext3 and also removed mdadm.  I wanted to start fresh all over again..

I then deleted the partions again, and reformated my 3 drives again.. just to be sure..  

Next I installed mdadm again.. and guess what... The default ARRAY in my mdadm file shows the previous RAID that was on the drive.. 

Here it is...
# definitions of existing MD arrays
ARRAY /dev/md0 level=raid5 num-devices=3 UUID=f88fa600:e5cedf45:0f5b4e61:2c17f314
   spares=2

I couldn't get the two spares in there to move out or resync... that's why I couldn't use that array...

I wonder where this INFO is hiding ? On the disk or in the OS ?

---

### Post by gm04030276 on 2008-07-16
try purging the install of mdadm to make sure all files are gone (hopefully)
before trying that or as well as, you could dd the disks to completely wipe them (gota do it several times)

use a little bash script just

```

dd if=/dev/zero of=/dev/sdb #(or what ever)
dd if=/dev/zero of=/dev/sdb #(or what ever)
dd if=/dev/zero of=/dev/sdb #(or what ever)

```

make one for each drive and just run them, leave for a day or so (two, three, depends how many times you erase; 7 = industry standard) to complete (on 1TB drives, takes aaaaaaaaaaaaaaagggeeesss)

Then try again?! :D

---

