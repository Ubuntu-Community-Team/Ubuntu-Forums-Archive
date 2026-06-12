---
title: "unable to partition hd using live-CD"
date: 2009-09-02
forum: x86 64-bit Users
---

### Post by greythorne on 2009-09-02
ok as per the title....

using 9.04 but i do not understand why i am unable to partition my only hd which is SATA 2 160gig. I am posting this thread using the live-cd now but unable to partition the hd.

the attached images may tell you what i mean....
The hd contain windows 7... could that be the reason why i am unable to partition?

my system:
C2D E8400 
4gig DDR2 ram
nvidia 8800gts 320mb

not sure what else to do... so any help would be much appreciated.

thanks.

---

### Post by fela on 2009-09-02
Windows 7 would almost certainly not have anything to do with this.

What do you do when you try to partition, and what is the error?

EDIT: from a livecd, post the output of:

sudo fdisk -l

in the terminal. That will give me information on how your disks are setup.

---

### Post by greythorne on 2009-09-02
> **fela said:**
> Windows 7 would almost certainly not have anything to do with this.

What do you do when you try to partition, and what is the error?

EDIT: from a livecd, post the output of:

sudo fdisk -l

in the terminal. That will give me information on how your disks are setup.

thanks for fast reply...

here is the output of the said command.

```
ubuntu@ubuntu:~$ sudo fdisk -l

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 160.0 GB, 160041885696 bytes
224 heads, 19 sectors/track, 73444 cylinders
Units = cylinders of 4256 * 512 = 2179072 bytes
Disk identifier: 0xe9b50e91

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          49      102400    7  HPFS/NTFS
/dev/sda2              49       73444   156183552    7  HPFS/NTFS

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe2a74f39

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       30401   244196001    7  HPFS/NTFS
ubuntu@ubuntu:~$ 
```

---

### Post by fela on 2009-09-02
OK, for one thing why are you using a GUID partition table? Just wondering as this isn't standard.

My next move would be to try using gparted to see what the problem is, as I don't know of any command line tools to check GUID drives.

---

### Post by greythorne on 2009-09-02
> **fela said:**
> OK, for one thing why are you using a GUID partition table? Just wondering as this isn't standard.

My next move would be to try using gparted to see what the problem is, as I don't know of any command line tools to check GUID drives.

i installed windows 7 then wanted to dual boot ubuntu but when using the live cd and issuing the fdisk command then i came to know that the hd partition table is GUID.

previously i was running OSX which i partitioned the hd in GUID maybe because of that?

possible to changing to MBR partition w/o destroying the hd since i would like to keep my existing windows 7 installation for use.

and as per the image attached in my first post using gparted it just shows the whole partition as an unused hd...

thanks.

---

### Post by fela on 2009-09-02
> **greythorne said:**
> i installed windows 7 then wanted to dual boot ubuntu but when using the live cd and issuing the fdisk command then i came to know that the hd partition table is GUID.

previously i was running OSX which i partitioned the hd in GUID maybe because of that?

possible to changing to MBR partition w/o destroying the hd since i would like to keep my existing windows 7 installation for use.

and as per the image attached in my first post using gparted it just shows the whole partition as an unused hd...

thanks.

You don't need to use MBR, ubuntu can be installed to GUID partitions (is this a EFI Mac or a standard BIOS IBM compatible PC?).

What HDD is listed as being empty? I see you have two HDDs. It would be nice if you attached 2 screenshots of gparted with each disk selected, just to get a clearer picture (that's what fdisk -l would have done, except it doesn't seem compatible with GUID).

---

### Post by greythorne on 2009-09-03
> **fela said:**
> You don't need to use MBR, ubuntu can be installed to GUID partitions (is this a EFI Mac or a standard BIOS IBM compatible PC?).

What HDD is listed as being empty? I see you have two HDDs. It would be nice if you attached 2 screenshots of gparted with each disk selected, just to get a clearer picture (that's what fdisk -l would have done, except it doesn't seem compatible with GUID).

Oh this is standard BIOS IBM compatible PC.

ok here is the output of fdisk -l again:
```
ubuntu@ubuntu:~$ sudo fdisk -l

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 160.0 GB, 160041885696 bytes
224 heads, 19 sectors/track, 73444 cylinders
Units = cylinders of 4256 * 512 = 2179072 bytes
Disk identifier: 0xe9b50e91

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          49      102400    7  HPFS/NTFS
/dev/sda2              49       73444   156183552    7  HPFS/NTFS

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe2a74f39

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       30401   244196001    7  HPFS/NTFS
ubuntu@ubuntu:~$ 
```

and the image of the 2 hd is attached.

Any help on this?

thanks

---

### Post by fela on 2009-09-03
OK, this is my guess:
You have 2 disks, one 250GB and one 160~GB.

The 250GB is formatted as NTFS and has windows 7 on it right?

And the 160GB one is unformatted.

You can install Ubuntu on the 160GB one, it should detect the windows 7 install and put it in the GRUB bootloader menu.

---

### Post by greythorne on 2009-09-03
> **fela said:**
> OK, this is my guess:
You have 2 disks, one 250GB and one 160~GB.

The 250GB is formatted as NTFS and has windows 7 on it right?

And the 160GB one is unformatted.

You can install Ubuntu on the 160GB one, it should detect the windows 7 install and put it in the GRUB bootloader menu.

oh ok.

actually the 250GB hd is an USB drive which contains my datas. The 160GB is the one that contain windows 7 and the thing is gparted detects it to be unallocated which can be see from the image i attached.

thanks

---

### Post by greythorne on 2009-09-03
is there qt parted which i can try and partition the hd and see if it works?

---

### Post by fela on 2009-09-03
Try mounting each harddrive and seeing what's on it (that'll give a clue as to what it is).

Do you mean a gparted but using the qt toolkit? There wouldn't be much point but I think it exists. Or do you mean something else?

---

### Post by greythorne on 2009-09-03
> **fela said:**
> Try mounting each harddrive and seeing what's on it (that'll give a clue as to what it is).

Do you mean a gparted but using the qt toolkit? There wouldn't be much point but I think it exists. Or do you mean something else?

ok i did mount the drives it contents the windows 7  and pretty much that....

still no idea...


thanks

---

### Post by Yellow Pasque on 2009-09-03
Perhaps you need a more recent version of the partitioning tools? Try a Parted Magic CD.

> is there qt parted which i can try and partition the hd and see if it works? qtparted is very old/unmaintained (at least the one I'm thinking of). Besides, it would just be a Qt frontend on the same libparted backend that gparted uses.

---

