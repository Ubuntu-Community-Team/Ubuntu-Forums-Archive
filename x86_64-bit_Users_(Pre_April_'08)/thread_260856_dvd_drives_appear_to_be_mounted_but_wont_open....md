---
title: "dvd drives appear to be mounted but wont open..."
date: 2006-09-19
forum: x86 64-bit Users (Pre April '08)
---

### Post by anvil1 on 2006-09-19
Howdy. I am running Ubuntu6/06 64 bit. This is my third install, and still no luck. 

I have multiple problems but will focus on the dvd drives for now. here is my fstab file:

# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
/dev/sdb3 / ext3 defaults,errors=remount-ro 0 1
/dev/sdb7 none swap sw 0 0
/dev/hdb /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/hda /media/cdrom1 udf,iso9660 user,noauto 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto 0 0

/dev/sda1 /media/windows ntfs nls=utf8,umask=0222 0 0
/dev/sda2 /media/windows ntfs nls=utf8,umask=0222 0 0
/dev/sda5 /media/windows ntfs nls=utf8,umask=0222 0 0 
/dev/sda6 /media/windows ntfs nls=utf8,umask=0222 0 0 
/dev/sda7 /media/windows ntfs nls=utf8,umask=0222 0 0 
/dev/sdb1 /media/windows ntfs nls=utf8,umask=0222 0 0 
/dev/sdb2 /media/windows ntfs nls=utf8,umask=0222 0 0
/dev/sdb5 /media/windows ntfs nls=utf8,umask=0222 0 0
/dev/sdb6 /media/windows ntfs nls=utf8,umask=0222 0 0
/dev/sdb7 /media/windows ntfs nls=utf8,umask=0222 0 0

they show upin "Place", but when i double click on either icon for the dvd's i get this: 

"Opening cd-rw\dvd=+- RW drive. you can stop this operation by clicking Cancel."

then nothing,, they just dont open up. 

I noticed a log reader and read one,, i think it was the kernel log,, not sure. I saw a msg that seemd to regenerate every so often:

"lost interrupt". this was for the drive that had the ubuntu disk installed. 

The second problem,,and i think it must be related, is when i shut down. it scrolls thru all items that it is closing and then stops at this one:

"Shutting Down LVM Volume Groups"

and as when i click on the dvd icon, it just stops. then reverts to a text screen, with this same msg at the bottom. I then have to power down to restart my machine. 


Again i think this must be associated with the above. I have installed the files (Ext2IFS_1_10b.exe) that allows me to give a drive letter to ext3 partitions,and read them in Windows. After a fresh install, i have no problem accessing linux partitions in windows,,but after the above shutdown i can no longer access the / partition. I can access my /home partition which is different from /. The author of this program's faq indicates that i need to properly unmount my faulty partition, and remount it. But since this is the partition that contains the os,,i don't know how to do this,, 

I don't think for what its worth, that this program (Ext2IFS_1_10b.exe) is the source of the problem as i have these problems whether it is installed or not. 

Thanks in advance..

anvil

---

### Post by kuja on 2006-09-19
Try changing the lines regarding the cd drives to this
```

/dev/hda /media/cdrom0  auto   user,noauto,exec,ro 0 0
/dev/hdb /media/cdrom1  auto   users,noauto,exec,ro 0 0

```

Perhaps that will help. Also, try mounting them manually:

sudo mount /media/cdrom0 (or /media/cdrom1)

Also, why are ten partitions mounting on the same mount point?

---

### Post by anvil1 on 2006-09-19
Thanks i will give that a try,, 

thats an oops on my part,,sorry, i had copied the fstab file from linux and pasted to my Windows fat32 folder.  when i first installed ubuntu, it did not show my windows drives,so found the solution here.  I forgot to delete the old fstab,and posted it here by mistake.. here is the working one...


# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sdb3       /               ext3    defaults,errors=remount-ro 0       1
/dev/sdb7       none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hda        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto
 0       0
/dev/sda1 /media/windows ntfs nls=utf8,umask=0222
 0       0
/dev/sda5 /media/Utilities ntfs nls=utf8,umask=0222
 0       0
/dev/sda6 /media//Internet ntfs nls=utf8,umask=0222
 0       0
/dev/sda7 /media/Graphics ntfs nls=utf8,umask=0222
 0       0
/dev/sdb1 /media/Games ntfs nls=utf8,umask=0222 
 0       0
/dev/sdb5 /media/Pics ntfs nls=utf8,umask=0222
 0       0
/dev/sdb6 /media/Data ntfs nls=utf8,umask=0222
 0       0

---

### Post by anvil1 on 2006-09-20
things seem to be going from bad to worse,,now when i boot up to ubuntu,,i get another error message after the desktop is active,, "HAL layer not initiated" or something similer..

if i cannot access my dvd i cannot install my modem which needs dependencies added,, thus i cannot get on line to upgrade my system,, what a catch 22... help please

anvil

---

### Post by anvil1 on 2006-09-21
the hal error went away,, but still no access to my dvd's.  any suggestions? sheesh there is no other place to go..

anvil

---

### Post by anvil1 on 2006-09-22
Interesting,,this is obviously not for people who have very little linux experience,,and here i am at the Ubuntu support forum,,and i can get no help... alas I am disappointed

anvil

---

