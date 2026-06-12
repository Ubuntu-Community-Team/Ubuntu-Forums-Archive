---
title: "booting Windows Vista with virtual machine manager"
date: 2009-01-20
forum: x86 64-bit Users
---

### Post by mk6032 on 2009-01-20
I have a new AMD laptop that supports svm. It's configured dual boot with Vista living on the largest partition. Ubuntu 8.10 lives on the other. :

matt@matt-laptop:~$ sudo fdisk -l

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x46744a72

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       25903   208063456    7  HPFS/NTFS
/dev/sda2           29090       30401    10531840    7  HPFS/NTFS
/dev/sda3           25904       29003    24900750   83  Linux
/dev/sda4           29004       29089      690795   82  Linux swap / Solaris

Partition table entries are not in disk order
matt@matt-laptop:~$

I would like to boot the Vista partition from within Ubuntu using the virtual machine that way I wouldn't have to reboot in order to switch from one to the other. So far I've Googled and followed the installation instructions provided here: [https://help.ubuntu.com/community/KVM/Installation](https://help.ubuntu.com/community/KVM/Installation)

When I open the Virtual Machine Manager, and try to start a VM it will only let me A. Mount an ISO or B. Boot from CD/DVD. The disk is mounted as /media/disk, but I don't know how to point it there. Am I using the wrong tools for the job?

---

### Post by mk6032 on 2009-01-22
I did...
```

ln -s /media/disk test.iso

``` 
..then tried to point VM Manager to the test.iso, but that didn't work either. Then I discovered this within that link I posted earlier.
> 
Install on a raw block device

Ubuntu-vm-builder doesn't allow you to create the VM on a raw block device yet (like a standalone partition, or a iSCSI share). You can use ubuntu-vm-builder to create the qcow2 image and then move the VM to the block device with qemu-img though; if /dev/sdb is the disk device on which you want to move the virtual machine:
```

sudo qemu-img convert root.qcow2 -O raw /dev/sdb

```
Edit the XML definition file for the VM in /etc/libvirt/qemu/, and set the source file to be:
```

<source file='/dev/sdb'/>

```
Redefine the VM and start it; it is now running from /dev/sdb.

Ubuntu-vm-builder is a very powerful tool - to get a more detailed list of its capabilities, use ubuntu-vm-builder --help. 


Does this mean it's not possible yet?

---

### Post by cariboo on 2009-01-23
You might want to look at the [Canned OS Project]("http://canned-os.blogspot.com/2006/08/p2v-virtualizing-existing-os-install.html"). the instructions are for XP, but it should work for VIsta.

Jim

---

