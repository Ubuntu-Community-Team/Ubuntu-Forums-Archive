---
title: "[SOLVED] Hard Drive reporting incorrect free space"
date: 2008-08-16
forum: x86 64-bit Users
---

### Post by firstc624 on 2008-08-16
OK this just started happening, or at least i just noticed it.
I was setting up a virtual machine, knowign that my hard drive should have plenty of space since i keep the drive fairly cleaned up.  this is also a relatively new install of 8.04, only about a month old.

this is the output of df -H

[code] firstc624@firstc624-laptop:~$ df -H
Filesystem             Size   Used  Avail Use% Mounted on
/dev/sda5               28G    26G   601M  98% /
varrun                 1.1G   156k   1.1G   1% /var/run
varlock                1.1G      0   1.1G   0% /var/lock
udev                   1.1G    58k   1.1G   1% /dev
devshm                 1.1G    25k   1.1G   1% /dev/shm
lrm                    1.1G    47M   990M   5% /lib/modules/2.6.24-21-generic/volatile
[code]

and this is the output of fdisk -l

firstc624@firstc624-laptop:~$ sudo fdisk -l
[sudo] password for firstc624: 

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x95f3457a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         862     6915072   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2   *         862        4910    32516096    7  HPFS/NTFS
Partition 2 does not end on cylinder boundary.
/dev/sda3            4910       12161    58249800    5  Extended
Partition 3 does not end on cylinder boundary.
/dev/sda5            4910       11859    55823008+  83  Linux
/dev/sda6           11859       12161     2426728+  82  Linux swap / Solaris


Does anyone have any idea as to what is going on?

i  will try to attach pics to show what i mean.

---

### Post by IntuitiveNipple on 2008-08-16
You have Ubuntu installed in sda5, it is approximately 28 Giga-bytes in size. Approximately 26 Giga-bytes has been used.

Use this command to locate the large files on the system.
```

find / -xdev -size +1G 2>/dev/null

```
If it doesn't locate any reduce the size boundary it is looking for from +1G (1 Giga-byte) to +512M (512 Mega-bytes) and so-on until you find where the space is being used, and by what.
My guess is, you've had some aborted attempts at creating virtual-machine disk images which will quickly swallow up free-space.

---

### Post by firstc624 on 2008-08-16
I am currently running that, and i did see that the commands i listed show what you say, but if you look at the screenshot i posted as well, it shows that the partition for sda5 is 50 gigs.  so i am tring to figure out where the other 26 gig went?

this is result of that command

firstc624@firstc624-laptop:~$ find / -xdev -size +1G 2>/dev/null
/var/lib/vmware/Virtual Machines/Windows XP Professional/Windows XP Professional-f001.vmdk
firstc624@firstc624-laptop:~$ 

when i looked at that file it is only 2 gig.  which is the size i created for it.

---

### Post by IntuitiveNipple on 2008-08-16
> **firstc624 said:**
> ...but if you look at the screenshot i posted as well, it shows that the partition for sda5 is 50 gigs.  so i am tring to figure out where the other 26 gig went?

The file-system size is reported as 28GB ... if that is smaller than the partition it is in then you'll need to use **tune2fs** (or equivalent) to enlarge the file-system.

Have you run an fsck on the volume to ensure it is okay? What type is it?

---

### Post by firstc624 on 2008-08-16
> **IntuitiveNipple said:**
> The file-system size is reported as 28GB ... if that is smaller than the partition it is in then you'll need to use **tune2fs** (or equivalent) to enlarge the file-system.

Have you run an fsck on the volume to ensure it is okay? What type is it?

No i have not run fsck on the disk as i don't know the correct command.  what type of what do i have?  hard drive?  which part?  what would be the easiest way to let you know?
I did try to go to terminal and run it just now, but it says that the drive is mounted and that it could cause damage if i run it while mounted.

so how do i run it while the drive isn't mounted?  since this is my main drive it mounts automatically??

I also added a screenshot of just gparted showing the drive partition is 53Gig of space.

So i supposed Y is it saying the filesystem is only 28Gig?

Possible bug?

---

### Post by IntuitiveNipple on 2008-08-16
Use tune2fs:
```

 tune2fs -l /dev/sda5

```
and look at the **Block count** and **Block size**. Multiply the two and you'll have the size of the file-system in bytes. Compare that with the partition size and what **df** reports.
```

df -h /dev/sda5

```

---

### Post by firstc624 on 2008-08-16
> **IntuitiveNipple said:**
> Use tune2fs:
```

 tune2fs -l /dev/sda5

```
and look at the **Block count** and **Block size**. Multiply the two and you'll have the size of the file-system in bytes. Compare that with the partition size and what **df** reports.
```

df -h /dev/sda5

```


ok here is what i got.

firstc624@firstc624-laptop:~$ df -h /dev/sda5
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5              26G   25G  395M  99% /
firstc624@firstc624-laptop:~$ 

and for the size when i mulitplied those out are as follows

27892375552

now as i can see, that still doesn't account for the 53 Gig partition i have for it in te screenshot above

Help....

---

### Post by IntuitiveNipple on 2008-08-16
What is strange is that gparted is showing the "used" space in the partition as 51GB which is plainly wrong. The partition size appears correct though.

tune2fs seems to have confirmed that the file-system inside partition sda5 is 28GB, and fdisk seems to confirm the partition size is ~55GB.

If it weren't for the incorrect report by gparted I'd say all it needs is the file-system extending. To do that you'd boot the PC using a LiveCD so the PC's root file-system can be manipulated.
```

sudo umount /dev/sda5 
sudo tune2fs -O ^has_journal /dev/sda5
sudo resize2fs /dev/sda5
sudo fsck -n /dev/sda5
sudo tune2fs -j /dev/sda5

```
At that point the file-system should have expanded to fill the partition it is in, and the PC can be booted from the hard disk again as normal.

What OS version and gparted version are you using (I'm not sure it will tell us anything but it is always worth knowing) ?
```

$ uname -a
Linux hephaestion 2.6.24-21-generic #1 SMP Tue Aug 12 13:03:01 UTC 2008 x86_64 GNU/Linux

$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 8.04.1
Release:	8.04
Codename:	hardy

$ dpkg-query -s gparted | egrep 'Version|Architecture'
Architecture: amd64
Version: 0.3.5-1ubuntu3

```

---

### Post by firstc624 on 2008-08-16
here is the os stuff you asked for

firstc624@firstc624-laptop:~$ uname -a
Linux firstc624-laptop 2.6.24-21-generic #1 SMP Tue Aug 12 13:03:01 UTC 2008 x86_64 GNU/Linux
firstc624@firstc624-laptop:~$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 8.04.1
Release:	8.04
Codename:	hardy
firstc624@firstc624-laptop:~$ dpkg-query -s gparted | egrep 'Version|Architecture'
Architecture: amd64
Version: 0.3.5-1ubuntu3
firstc624@firstc624-laptop:~$


Should i try that other stuff?

---

### Post by IntuitiveNipple on 2008-08-16
Ideally I'd want to figure out why gparted is reporting the way it is.

If you could prove that is an error in gparted and therefore you could ignore those values, then resizing the file-system would be a reasonable step.
Right now I think the wisest course of action is to hold off until you know for certain what the state of play is.

Can you report here the output of:
```

$ dumpe2fs -h /dev/sda5

```

I've got the source-code of gparted here and am looking at the code that gets and calculates those values. It simply executes the command above, scans the output for "Free blocks" and "Block size" and does some math on those values. 
With your disk's values I cam maybe figure out how it gets the values you see and then we can know if it is a gparted bug or not.

---

### Post by IntuitiveNipple on 2008-08-16
Okay, good news. I can confirm it is a bug in gparted. Here's an explanation.

It has two classes, Partition and FileSystem. There are sub-classes of the generic FileSystem class for each file-system type such as ext2, etc3, reiserfs, fat32, ntfs, etc.

The ext3 class uses dumpe2fs to get the **file-system**'s number of free sectors (calculated from those block-values I mentioned previously).

Then, it sets the containing ***Partition***'s unused sectors based on that value, which at the same time calculates the used space in the Partition as:

sectors_in_partition - unused_sectors_in_filesystem

You see the problem?

You've got a partition, sda5, that has approximately 110,000,000 sectors (~52GB). In sda5 you have an ext3 file-system that has about 1,191,400 sectors (610MB) free.

So it calculates the used partition value as 110,000,000 - 1,191,400 ~= 108,808,593.

Multiply that by 512 (bytes per sector) and you get close to 53GB used in sda5!

So, I think (after backing-up vital data files) the procedure for expanding the file-system to fill the partition using the LiveCD is okay to follow.

---

### Post by firstc624 on 2008-08-16
here is the output that you asked for


firstc624@firstc624-laptop:~$ sudo dumpe2fs -h /dev/sda5
[sudo] password for firstc624: 
dumpe2fs 1.40.8 (13-Mar-2008)
Filesystem volume name:   <none>
Last mounted on:          <not available>
Filesystem UUID:          180b65de-7552-4ae1-9197-8d473a28c2d5
Filesystem magic number:  0xEF53
Filesystem revision #:    1 (dynamic)
Filesystem features:      has_journal ext_attr resize_inode dir_index filetype needs_recovery sparse_super large_file
Filesystem flags:         signed_directory_hash 
Default mount options:    (none)
Filesystem state:         clean
Errors behavior:          Continue
Filesystem OS type:       Linux
Inode count:              1703936
Block count:              6809662
Reserved block count:     272386
Free blocks:              303955
Free inodes:              1508408
First block:              0
Block size:               4096
Fragment size:            4096
Reserved GDT blocks:      1022
Blocks per group:         32768
Fragments per group:      32768
Inodes per group:         8192
Inode blocks per group:   256
Filesystem created:       Thu Aug  7 16:15:42 2008
Last mount time:          Sat Aug 16 19:54:43 2008
Last write time:          Sat Aug 16 19:54:43 2008
Mount count:              28
Maximum mount count:      29
Last checked:             Thu Aug  7 17:02:20 2008
Check interval:           15552000 (6 months)
Next check after:         Tue Feb  3 16:02:20 2009
Reserved blocks uid:      0 (user root)
Reserved blocks gid:      0 (group root)
First inode:              11
Inode size:		  128
Journal inode:            8
First orphan inode:       807207
Default directory hash:   tea
Directory Hash Seed:      9152ee23-c5cc-4ce7-8fac-defd2d96c10d
Journal backup:           inode blocks
Journal size:             128M

firstc624@firstc624-laptop:~$ 



I will keep this alive as long as i have to to help the community.  i will prolly end up redoing this drive afterward, but i want to help in anyway possible.

Thanks again for helping with this.

---

### Post by IntuitiveNipple on 2008-08-17
I think our last postings crossed. As I said in [commment #11](http://ubuntuforums.org/showpost.php?p=5605014&postcount=11), there is a bug in gparted so I think you're okay to use the LiveCD to expand the file-system to fill the partition.

---

### Post by firstc624 on 2008-08-17
You were correct i didn't see that begore i posted.   

I went ahead and did what you suggested and it looks like gparted is reporting 26 gig free now.  here is the output of df -h /dev/sda5  as well.

firstc624@firstc624-laptop:~$ df -h /dev/sda5
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5              53G   25G   27G  48% /
firstc624@firstc624-laptop:~$ 


OK seems fixed.  Thank You for all you have done to help me  :-)


Now my next question is what do we do about the bug?  I was thinking of having you report it cuase you seem to know what happened.  or do you think i should, but if i do i don't know what to say.

let me know

---

### Post by IntuitiveNipple on 2008-08-17
> **firstc624 said:**
> 
Now my next question is what do we do about the bug?  I was thinking of having you report it cuase you seem to know what happened.  or do you think i should, but if i do i don't know what to say.

let me know

I'll check with upstream and Launchpad. I suspect it is well known since elsewhere in the source-code was a FIXME comment that described a similar issue.

Glad you got it sorted out - that gparted report is grossly misleading and likely to confuse even experts.

---

### Post by firstc624 on 2008-08-17
Well i am very glad that you were able to figure it out, as i don't know that much about going into the source code and stuff.  I love to help where i can, bug reports and such, but this one had me totally confused.

Thank You  :-)

---

