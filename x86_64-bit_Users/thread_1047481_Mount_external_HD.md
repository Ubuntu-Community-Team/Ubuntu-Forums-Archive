---
title: "Mount external HD"
date: 2009-01-22
forum: x86 64-bit Users
---

### Post by retiree on 2009-01-22
What is the best way to mount a 1TB external Maxtor USB harddrive? 
Running X86 64 bit HH 8.04
It will not mount auto out of the box.
Thanks for any help, Retiree

---

### Post by cariboo on 2009-01-22
Open an Applications-->Accessories-->Terminal and type:

```
dmesg | tail -n10
```

just after you've plugged your external drive in.

The output should look something like this:

```
[ 5850.978821] sd 6:0:0:0: [sdd] Write Protect is off
[ 5850.978825] sd 6:0:0:0: [sdd] Mode Sense: 43 00 00 00
[ 5850.978828] sd 6:0:0:0: [sdd] Assuming drive cache: write through
[ 5850.993955] sd 6:0:0:0: [sdd] 1981440 512-byte hardware sectors: (1.01 GB/967 MiB)
[ 5850.995798] sd 6:0:0:0: [sdd] Write Protect is off
[ 5850.995801] sd 6:0:0:0: [sdd] Mode Sense: 43 00 00 00
[ 5850.995803] sd 6:0:0:0: [sdd] Assuming drive cache: write through
[ 5850.995809]  sdd: sdd1
[ 5851.059103] sd 6:0:0:0: [sdd] Attached SCSI removable disk
```

The above output is what I get when I plug in a 1Gb usb stick. the output should be similar when you plug in your external drive. Note the sdd1, this is the device label that is assigned automatically by Linux.

Linux will assign a similar label to your external drive use that to mount your drive.

THe first thing to do is to create a mount point for your drive. in the same terminal type:

```
sudo mkdir /media/external
```

enter your password when asked, it will not echo anything back. The next thing to do is to mount your drive, in the same terminal type:

```
sudo mount /dev/sdb1 /media/external
```

replace /dev/sdb1 with your device label. To be able to read/write to your external drive you will need to change the permissions of /media/external, in the same terminal type:

```
sudo chmod -R 777 /media/extrenal
```

the drive should now show up in Places-->Home Folder.

Jim

---

### Post by retiree on 2009-01-22
Thanks Cariboo907 for the help, it is much appreciated!!

I have been out all evening trying to help my son move!!

Retiree

---

