---
title: "Can not access windows partition"
date: 2005-10-14
forum: x86 64-bit Users (Pre April '08)
---

### Post by metal_head_3767 on 2005-10-14
Hi.  I went into the disks app in system.  I linked my windows partition to my desktop and to a folder called windows.  In the disks manager when I click browse I can see the data on the drive.  I can not write to it.  On the desktop on the icon there is a pen with a cross over it which I'm guessing means that I can not write to it.  I want to play music right off that partition but I think it needs to write something to open audio files.  I can open images fine off the drive.  When I try to open the files on the windows file on the desktop it says I "Do not have the permission necessary to view the contents of windows."  I am new to linux.  I have done extensive research on the net but it has given me nothing.  Please help!

---

### Post by DancingSun on 2005-10-15
Oops, double posted! Read the post below!

---

### Post by DancingSun on 2005-10-15
[QUOTE=metal_head_3767]Hi.  I went into the disks app in system.  I linked my windows partition to my desktop and to a folder called windows.  In the disks manager when I click browse I can see the data on the drive.  I can not write to it.  On the desktop on the icon there is a pen with a cross over it which I'm guessing means that I can not write to it.  I want to play music right off that partition but I think it needs to write something to open audio files.  I can open images fine off the drive.  When I try to open the files on the windows file on the desktop it says I "Do not have the permission necessary to view the contents of windows."  I am new to linux.  I have done extensive research on the net but it has given me nothing.  Please help![/QUOTE]
Not quite sure what you mean. Might want to be clearer.  What do you mean by you can open images fine, but then opening it gives you the permission error?
However, not being able to write to the windows drive is normal.
But try this:

[http://www.ubuntuguide.org/#automountntfs](http://www.ubuntuguide.org/#automountntfs)

Be sure to bookmark that site, it comes in very handy!

Edit: Ok, after re-reading a few times, I think you mean that in the file manager you can open the windows partition, but you cannot open the symlink (shortcut) that you created, right?  If so, try right-clicking the symlink (shortcut) and choose "Properties" from the menu.  Click on the "Permissions" tag, and see if the owner is you.  If it is, check the permissions, make sure you can at least have the "read" permission.

---

### Post by metal_head_3767 on 2005-10-15
It says the owner can ead and write and the group and others can do nothing.  On the folder that I linked it also has an eye with a cross through it.  I guess that means I also can not see the contents of the folder.  When I open up the folder, it is empty.  When I open it up in the disk manager I can see the contents.  Is there any way I can give myself complete access to the partition?  Thanks for your help.

---

### Post by DancingSun on 2005-10-15
Try re-creating the symlink.  You can hold ctrl+alt down while dragging the mounted folder from the file manager to your desktop.

If you use the mount method in the link that I gave you, it should give all users read access to the Windows NTFS partition.  Although it sounds like you already have read access to the partition, just not the symlink you created.  I don't know what's wrong with your sound files.  What media player are you using?  Totem-gstreamer works fine on my system when trying to play music files from my Windows partition on Ubuntu 5.04.

---

### Post by eph on 2005-10-19
i got the same problem with writing to fat filesystem.

i tried to chmod using root to change the permission to 777 but still it does not change, no error messages.

i tried changing the fstab parameters. i still cant get other users to write to the fat partition. only root can write to it but it cant change the permission of any folder.

im still figuring out what could be wrong

---

### Post by *zerk* on 2005-10-19
hi!

had the same problem...
i did:

 mount -t ntfs -o errors=recover /dev/hda1 /mnt/win_c

then it worked... hope it helps.
Don't know what the problem is?

---

### Post by RAOF on 2005-10-19
[QUOTE=eph]i got the same problem with writing to fat filesystem.

i tried to chmod using root to change the permission to 777 but still it does not change, no error messages.

i tried changing the fstab parameters. i still cant get other users to write to the fat partition. only root can write to it but it cant change the permission of any folder.

im still figuring out what could be wrong[/QUOTE]
The FAT filesystem has absolutely no support for permissions whatsoever - trying to change permissions on a FAT filesystem will do nothing.  What **can** help is the "umask" mount option in the fstab.  For no apparent reason the meaning of the numbers is reversed - umask=777 corresponds to **no** permissions, =000 corresponds to free-for-all.

Here is an example of my fstab containing a world-readable NTFS partition.
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>               <dump>  <pass>
proc            /proc           proc    defaults                0       0
/dev/sda2       /               reiserfs notail,user_xattr      0       1
/dev/sda4       /media/         reiserfs defaults,user_xattr    0       2
/dev/sda5       none            swap    sw                      0       0
/dev/hda        /media/cdrom    udf,iso9660 user,noauto         0       0
#I don't have a floppy anymore :)
#/dev/fd0        /media/floppy0  auto    rw,user,noauto         0       0
/dev/sda1       /mnt/WinXP      ntfs    defaults,umask=000      0       0
```If this were a FAT partition, it would also be world-writeable thanks to the umask=000, but there's no write support for NTFS.

---

### Post by eph on 2005-10-19
already got it working, all it needed was a reboot.

i thought doing mount -a would apply all the changes i made with the fstab.:D

---

### Post by DancingSun on 2005-10-19
[QUOTE=eph]i thought doing mount -a would apply all the changes i made with the fstab.:D[/QUOTE]
Hmm...interesting....would that be considered a bug?

---

### Post by toujours on 2005-10-19
I had the same issue with *sudo mount -a*.

It got me hunting fruitlessly for half an hour until I decided to reboot...

---

### Post by germac on 2005-10-19
sudo mount -a doesn't work apparently
I used sudo umount /dev/hda1 or /windows ; then sudo mount /dev/hda1 or /windows

Acces granted

---

