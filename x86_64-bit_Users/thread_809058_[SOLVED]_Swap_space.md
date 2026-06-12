---
title: "[SOLVED] Swap space"
date: 2008-05-27
forum: x86 64-bit Users
---

### Post by egamal on 2008-05-27
I'm using ubuntu 8.04 beta release on my Acer aspire 5100 turion X2  .. and I didn't add a swap partition while the installation and 
I have a 1 GB ram that means that I should have a 2GB swap space ..!

So after installing the system it simply hangs as I'm over loading it, and I'm wondering if I just can add a swap space ..

Hint:
Swap files will not help me .. I've no partitioned space enough only a swap partition  will help as I already have a non-partitioned space about 5 GB

So is there any way to Swap that empty space then mount it as a swap


Thanks in advance

---

### Post by soxs on 2008-05-27
Partition tool:```
sudo apt-get install gparted
```
Run it from the terminal via ```
sudo gparted
``` or from system->System... -> gparted. Edit your left free space on your hd to a swap partition.

Next step is to add a line to your /etc/fstab, so it gets outmounted on your next reboot:
```
sudo gedit /etc/fstab
```
I e.g. have:```

UUID=39dbeed3-d6d2-4444-a74d-630b8e81d7b4 none            swap    sw              0       0
```

to get your UUID for oyur partition use: ```
sudo blkid
```
replace it from my example with your one (WITHOUT " " ", mucho importante!),
add it to your /etc/fstab, save and reboot

check with
```
mount
``` wether it worked or not.
;-)

---

### Post by egamal on 2008-05-27
well, first of all thanks for your help :)

Second of all, "beforre your reply" I did got the *gparted* utility and tried to create a swap formated partition in the unallocated space, but it simply didn't got recognized ..
So instead I partitioned it ext3 to create a swap file ..

and now you replied I tried to follow your instruction but...

Simply the unallocated space have no UUID as it's NOT allocated space :) ; that's what I have just found :D

Anyway, I tried what you posted in the empty ext3 partition I mentioned up there ..

You said that I can check it by the *mount* command; I don't know but here's the out put of the command after doing your steps to the ext3 empty partition and rebooting :)
```

/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-16-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
gvfs-fuse-daemon on /home/gamal/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=gamal)

```


Thanks again for your help soxs :)

---

### Post by soxs on 2008-05-27
mount will show you all mounted partitions, so it only will shouw your swap/ext3/fat/vfat/resierfs/ext2, if you added it to your etc fstab.
Note: In case you allready have 4 primary partitions, where one includes secondary ones, and swap is  away from the seondary sector (so it can't be an secondary partition), you have bad luck and will have to sacrifice a part of your existing hd (shrink it from x  GB to x-2 GB and make those 2 GB your swap)
that's the only reason it does not work a I can think of atm... sry

Plx add a screenshoot of gparted when it loaded all info and you make your hardware device show which should include the swap 2 GB partition.

---

### Post by Sef on 2008-05-27
> I have a 1 GB ram that means that I should have a 2GB swap space ..!

With 1 gb ram, I would make a 1 gb swap.  1 1/2 - 2 times holds for less ram, but once you have 1 gb or more, swap becomes less important.

---

### Post by egamal on 2008-05-27
> With 1 gb ram, I would make a 1 gb swap. 1 1/2 - 2 times holds for less ram, but once you have 1 gb or more, swap becomes less important.
Thanks for the info but may be because I'm enabling the compiz very -Memory using- visual effects and I -somehow- don't trust that 3d acceleration driver I'm using + my very small space for the / ..

a 1.5 GB swap won't hurt :D ... that what I thought about ..

anyway .. I do agree with you, ThanQ :)

about gparted screenshots:
I have 3 options in the combo box in the up right corner ..
so the three of them ..

[[IMG]http://img135.imageshack.us/img135/1152/screenshotdevmappervolgfb5.th.png[/IMG]](http://img135.imageshack.us/my.php?image=screenshotdevmappervolgfb5.png)
[[IMG]http://img504.imageshack.us/img504/7265/screenshotdevmappervolgml2.th.png[/IMG]](http://img504.imageshack.us/my.php?image=screenshotdevmappervolgml2.png)

**This space is used to be a swap for old fedora, and I'm now intending to use it as a swap for UBUNTU  .. this is life :D**
note: it's inside a volume group [logical partition]

[[IMG]http://img292.imageshack.us/img292/5736/screenshotdevsdagpartedjj9.th.png[/IMG]](http://img292.imageshack.us/my.php?image=screenshotdevsdagpartedjj9.png)

---

### Post by aaron.d on 2008-05-27
OK SO... It looks like you are a bit confused, and have confused at least me a bit in reading this thread.

what I see to be the facts at this time are:


- you have one primary partition with your root files system on it.
- two other partitions are primaries: both NTFS
- the forth partition is extended and contains: a) a small boot partition b)a volume group

The volume group is where you wish to put the swap, correct? Specifically, the swap shoud occupy the 1.46 gigs of unallocated space on logvol01, correct?

-----------------
EDITORS NOTE: this is the confusing part. If the above is correct, why did you say in your initial post:

> ... a swap partition will help as I already have a non-partitioned space about 5 GB

If you ARE trying to use the 1.46 gigs, keep reading. If you were initially referring to the unallocated 6.5 gigs NOT in a VG, then thats another story. Please do fill us in.
-----------------

If this is the case, I see no reason why you cannot create a  swap on that partition. 

once you do that, blkid should be able to identify the swap space (if you even care, you CAN just use device id, which is conveniently given to you already in gparted ... '/dev/mapper/VolGroup00-LogVol01' or also '/dev/VolGroup00/LogVol01'). from there, it's a simple matter of following the steps for making swap, turning it on and adding to fstab (with or without UUID).

You may, at some point want to think about cleaning up your partitioning scheme a bit, but this should work.

---

### Post by egamal on 2008-05-27
ThanQ :)

I just tried to make it a swap again .. 
and it just worked .. after blkid it listed it as a swap partition 
and now I've a question do I need to activate it or something ??

I believe that ubuntu is wise enough to know that there is a swap partition to use ?? but just wondering ??

ThanQ all again :)

---

### Post by aaron.d on 2008-05-27
No, it's only enabled if it shows up in 'free'.

You most likely need to:


```
sudo mkswap /dev/mapper/VolGroup00-LogVol01
``` MAKE SURE THAT DEVICE IS THE CORRECT ONE!

and then

```
sudo swapon sudo swapon
```

and then make it perm like:


```
sudo gedit
``` or your fave txt ed


and add the line:

```
/dev/mapper/VolGroup00-LogVol01 none            swap    sw              0       0
```
always make sure '/dev/mapper/VolGroup00-LogVol01' is the right partition on which you have your swap.


check it like so:
```

$ free
             total       used       free     shared    buffers     cached
Mem:     
-/+ buffers/cache:   
Swap:     

```

---

### Post by egamal on 2008-05-27
done :)
ThanQ .. and please edit the last post as I think this post is going to be a nice references for newbies like me :)

exactly I meant
```

sudo swapon /dev/mapper/VolGroup00-LogVol01

```

ThanQ again,

---

