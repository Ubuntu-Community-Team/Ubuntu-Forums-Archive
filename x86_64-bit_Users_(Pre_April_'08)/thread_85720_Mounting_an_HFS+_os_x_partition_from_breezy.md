---
title: "Mounting an HFS+ os x partition from breezy"
date: 2005-11-03
forum: x86 64-bit Users (Pre April '08)
---

### Post by tmeier on 2005-11-03
I have a Tibook 1.25ghz 60gb hd and have split into two partions. 50gb for OS X and 10gb for Breezy.  I have successfully installed breezy and everything is working well including the airport card.  I however would like access to my files on the os X partion.  What is the process to get that done so that it mounts as I login.  Thanks for any help.

Thomas

---

### Post by farruinn on 2005-11-03
You need to add a line in your /etc/fstab for the Mac OS X partition.  This is what my fstab looks like for my iBook:

```
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda4       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hda3       /mnt/Mac        hfsplus user    0       0
``` 

My OS X partition is on /dev/hda3.  It's the first partition on the drive with an OS.

The one thing I haven't acomplished is setting the user/group mask such that I can access my home folder with my normal ubuntu user account. Currently I have to 'sudo cp /mnt/Mac/Users/nathan/* ~/' to copy files to Ubuntu.

---

### Post by slux on 2005-11-03
[QUOTE=farruinn]
The one thing I haven't acomplished is setting the user/group mask such that I can access my home folder with my normal ubuntu user account. Currently I have to 'sudo cp /mnt/Mac/Users/nathan/* ~/' to copy files to Ubuntu.[/QUOTE]

You just need to make the UIDs (and optionally GIDs) for your users the same in both operating systems. Probably could be done in either OS but easiest in Ubuntu. Don't think it's possible thru the graphical tool, but a "usermod -u <desired UID> username" will suffice from a root shell.

Pretty much the best way to achieve the desired effect. If there's another way, do tell.

---

### Post by tmeier on 2005-11-03
Thanks to all for your information.  It has made life easier to have this access.  

Thomas

---

### Post by farruinn on 2005-11-06
Thanks for the tip, that command worked well for me.  I also changed the group number for my user.  A note for others who change their group number: run 'sudo groupmod -g <number> <groupname>' and then 'sudo chown -R /home/<username>/.*'  The groupmod command doesn't change ownership on hidden directories and files in your home directory.

---

### Post by Rxke on 2005-11-07
Doest this work with journaled and the new Tiger case-sensitive (or whatever it is named, I never used Tiger) setups?

---

### Post by tmeier on 2005-11-07
I changed the user ID to be the same for both OS's.  My Tibook is running 10.4.2 and Breezy Badger and once I changed the UID I was able to mount and have access to my home folder files.  For me it did work with Tiger.

Thomas

---

### Post by farruinn on 2005-11-07
I *believe* that the hfsplus kernel driver mounts it without journalling.  I don't know if there is a way to turn journalling on, but I would suspect it would be experimental and only useful for bugtesting.  I can't comment on the hfs+ case sensitive though as I went with just hfs+ journalled on this os x install (I've heard of problems with some frameworks under the case sensitive filesystem).

---

