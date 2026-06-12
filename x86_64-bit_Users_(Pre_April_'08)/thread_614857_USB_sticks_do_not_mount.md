---
title: "USB sticks do not mount"
date: 2007-11-16
forum: x86 64-bit Users (Pre April '08)
---

### Post by hutxubix on 2007-11-16
Hi!!

Almost everything works fine but, when I introduce my USB stick, I get "Connot mount volume. Invalid mount option"

I have tried the advice in other thread (not for 64bits specifically) but it doesn't not work. (deleting line '/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0' from /etc/fstab)

Any ideas, please?

---

### Post by ptn107 on 2007-11-16
I don't know about you, but I'm using gutsy and my removable devices are handled in **mtab** not **fstab**.  I believe fstab is for devices you want mounted on every reboot.

My mtab is as follows:

```
/dev/hda1 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
procbususb /proc/bus/usb usbfs rw 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
/dev/hdb1 /media/hdb1 ext3 rw,errors=remount-ro 0 0
securityfs /sys/kernel/security securityfs rw 0 0
nfsd /proc/fs/nfsd nfsd rw 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
tmpfs /lib/modules/2.6.22-14-generic/volatile tmpfs rw,mode=0755 0 0
/dev/sda1 /media/disk vfat rw,nosuid,nodev,shortname=mixed,uid=1000,utf8,umask=077,usefree 0 0
```

The last entry:
**/dev/sda1 /media/disk vfat rw,nosuid,nodev,shortname=mixed,uid=1000,utf8,umask=077,usefree 0 0**

is for my flash drive.  Try adding a similar line to the end of your mtab.  If you want it mounted every boot put it in fstab instead (but it must be plugged in on every reboot).

---

### Post by ddrichardson on 2007-11-16
This also happens with some U3 USB drives, because of the hidden partition.

---

### Post by hutxubix on 2007-11-18
Hi!!

This is not a U3 drive. I added the line to mtab. Now, my mtab is

/dev/sda4 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
lrm /lib/modules/2.6.22-14-generic/volatile tmpfs rw 0 0
securityfs /sys/kernel/security securityfs rw 0 0
/dev/sda1 /media/disk vfat rw,nosuid,nodev,shortname=mixed,uid=1000,utf8,umask=077,usefree 0 0

I created the forder 'disk' in /media/, but it still DOESN'T WORK :confused:
I have seen that in your mtab you have these lines that I do not have:

procbususb /proc/bus/usb usbfs rw 0 0
/dev/hdb1 /media/hdb1 ext3 rw,errors=remount-ro 0 0
nfsd /proc/fs/nfsd nfsd rw 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
tmpfs /lib/modules/2.6.22-14-generic/volatile tmpfs rw,mode=0755 0 0

Do I need to add any other? (I am sorry but I am still a beginner trying to be able to leave Windows behind)

Finally, my fstab, just in case, is
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda4
UUID=488cad50-212c-4ab8-b778-b73f19f80b53 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda6
UUID=bae2c582-98b6-465d-b887-c63b098ba590 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

On the other hand, if I try 

sudo mount -t vfat /dev/sda1 /media/disk

I get

mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

and How do I know that the USB stick is in /dev/sda1???

Any clue?

Thanks

---

### Post by ddrichardson on 2007-11-18
Fstab contains partition information and how to mount them, mtab does not handle removeble devices, it just contains information about what is actually mounted and so shouldn't be edited.

Is this definately a vfat/fat32 formatted stick?

Can you give output of ```
sudo fdisk /dev/sda1?
```In fact, without it mounted, what is the output of ```
sudo fdisk -l
```

---

### Post by hutxubix on 2007-11-18
Hi!!

Without the USB stick, the output for 

sudo fdisk -l

is

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x48ae48ad

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       47806   384001663+   7  HPFS/NTFS
/dev/sda2           47807       53885    48829567+  83  Linux
/dev/sda3           60158       60801     5172930    5  Extended
/dev/sda4           53886       60157    50379840   83  Linux
/dev/sda5           60431       60801     2980026   82  Linux swap / Solaris
/dev/sda6           60158       60430     2192809+  82  Linux swap / Solaris

and for 
sudo fdisk /dev/sda1

is

The number of cylinders for this disk is set to 47805.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)

Any idea, please?

---

### Post by ddrichardson on 2007-11-18
Well then there's your problem, /dev/sda1 is an NTFS partition on your primary hard disk not a usb stick. My guess would be that it'll be at /dev/sdb

---

### Post by hutxubix on 2007-11-18
> **ddrichardson said:**
> Well then there's your problem, /dev/sda1 is an NTFS partition on your primary hard disk not a usb stick. My guess would be that it'll be at /dev/sdb

Hey! Thanks, it worked

sudo mount -t vfat /dev/sdb1 /media/disk

My last question is what do I have to do to make it automatic. Do I have to edit fstab?

Thanks

---

### Post by ddrichardson on 2007-11-18
You can put it in fstab. Not sure why it isn't mounting automagically though.```
/dev/sdb1  /media/disk  vfat auto,users 0 0
```Should do the trick

---

### Post by hutxubix on 2007-11-18
Well,

Now, nor does he mount neither does he displays the error popup!!

And I still have to write 'mount /media/disk/' to have it.

Any further idea? If not, unless I can use it like that! (though I think I shouldn't put it like [SOLVED] yet)

Thank you very much ddrichardson.

---

### Post by ddrichardson on 2007-11-18
You might have to specify UUID. You can find it by```
sudo vol_id /dev/sdb1
```
There's more about why [here]("http://ubuntuforums.org/showthread.php?t=278652").

---

### Post by binary_bob on 2007-11-18
This post prompted me to check my usb/flash storage devices.
MP3 player (my emergency file transfer device) automounts and is available.
1GB sd flash card automounts and is available.
Both of the above devices were last used on a windows system.
ddrichardson is right to say usb devices should automount.
Possible solutions to your problem..
1) usb device is corrupt. Try another
2) usb port is non functioning. Try another
3) OS install is corrupt. Re-install
Personally, i would have tried 1) and 2) before making any changes to the OS.
No solution, but you have to cover as many angles as possible.

---

### Post by ddrichardson on 2007-11-18
I think that's a little drastic, there are issues with mounting drives related to UUID, which is most likely why it isn't auto-mounting. I don't pretend to understand it, as block devices aren't my thing, but as I understand it there was a move to using the SCSI driver rather than ATA for such devices becuase it was more efficient and less problematic.

---

### Post by hutxubix on 2007-11-18
I've read the thread, but as far as I understand, if I define the UUID it will be automatic just for that specific USB stick. Am I right?

Anyway, what I get is:
ID_FS_USAGE=filesystem
ID_FS_TYPE=vfat
ID_FS_VERSION=FAT32
ID_FS_UUID=4C62-7D8C
ID_FS_UUID_ENC=4C62-7D8C
ID_FS_LABEL=KINGSTON
ID_FS_LABEL_ENC=KINGSTON
ID_FS_LABEL_SAFE=KINGSTON

What would be the line now? Could I write multimple lines for multimple USB sticks?

---

### Post by ddrichardson on 2007-11-18
The thing is that this should be getting picked up, if you can mount it using```
mount /dev/sdb1 /media/disk
```Then the fstab entry is correct (because of the auto).

---

### Post by hutxubix on 2007-11-18
> **binary_bob said:**
> This post prompted me to check my usb/flash storage devices.
MP3 player (my emergency file transfer device) automounts and is available.
1GB sd flash card automounts and is available.
Both of the above devices were last used on a windows system.
ddrichardson is right to say usb devices should automount.
Possible solutions to your problem..
1) usb device is corrupt. Try another
2) usb port is non functioning. Try another
3) OS install is corrupt. Re-install
Personally, i would have tried 1) and 2) before making any changes to the OS.
No solution, but you have to cover as many angles as possible.

I think it is not corrupt neither is the USB port as I can mount it manually and use it wihtout problems.

I suppose is something of the OS but I have not time to re-install it so, I will live with it manually.

Tant pis

Anyway, THANK YOU EVERYBODY for the help.

---

