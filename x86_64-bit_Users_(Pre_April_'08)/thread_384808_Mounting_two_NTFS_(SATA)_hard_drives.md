---
title: "Mounting two NTFS (SATA) hard drives"
date: 2007-03-14
forum: x86 64-bit Users (Pre April '08)
---

### Post by NeilBlanchard on 2007-03-14
Greetings,

I followed the instructions on this page:

[http://www.psychocats.net/ubuntu/mountwindows]("http://www.psychocats.net/ubuntu/mountwindows")

...and it doesn't work.  I tried twice, and I think there may be two things that I might be doing wrong.  The first is, I cannot tell the difference (in terminal) between a 1 and an l in this line:

/dev/hda1 /windows ntfs nls=utf8,umask=0222 0 0

...but after I pasted it here I see it is 'nls', not 'n1s' -- so I typed it correctly.

The second thing is when I list the drives (sudo fdisk -l) (which is the first time I thought it was -1), the two NTFS drives are listed as sda1 and sdb1 -- but when I open the fstab file, they are listed as hdc1 and hdc5.

Which is correct?  Am I doing something else wrong?

---

### Post by jellyfisharepretty on 2007-03-14
Hello there,

First SATA drive will be identified in linux as sda, sdb, sdc, etc.  IDE drives will be hda, hdb, and so on.  This is the correct listing.  The fstab doesn't necessarily list what is truly in your system, it might be incorrect.  I am no linux guru but I have fiddled with it in the past and it is my understanding that the file is used to tell the system what partitions of which drives to mount on which directories of the root filesystem.  You can also specifies some mounting options and permissions.

The number indicates the partition you want to mount.  For example if you want to mount the 2nd partition  ("1") of the 1st SATA drive ("a") you would use "sda2" as in

/dev/sda1 /windows ntfs nls=utf8,umask=0222 0 0

Bear in mind that for this to work, the directory /windows needs to exist.  That will be the mounting point of sda1.

You can create it by using

sudo mkdir /windows

So to answer your question I think what you were doing wrong was using "hda1" instead of "sda1" and possibly the directory /windows didn't exist.

Hope this helps.

---

### Post by NeilBlanchard on 2007-03-18
Hello,

I'm still not able to "see" the NTFS drives.  I created two sub folders in the Windows folder, called C-Drive and F-Drive, and I attempted to edit the fstab file to get them to work, and still no go.  :( 

I used the sda1 and sdb1 designations.  Q: should the fstab be reverting to the original lines after a reboot?  I edit it and save it as I exit (as per the the instructions) and then after it doesn't work, I re-edit it and it has reverted to the original?  :confused: 

Any pointers or hints?

Sincerely, Neil

---

### Post by jellyfisharepretty on 2007-03-18
Ok, this is where ubuntu weirdness surpasses me.  AFAIK the fstab should not change after a reboot, but edgy (I assume you're using) might be doing some kind of drive auto-detection and coming up with its own.  I really don't know.

My fstab does contain stuff that's been put in by edgy that I don't know about like 

[FONT="Courier New"]# /dev/sda1 -- converted during upgrade to edgy
UUID=18C4419FC4417FCC /media/sda1 ntfs defaults,nls=utf8,umask=007,gid=46 0 1[/FONT]

Sorry I can't be of much help now.  Can a more advanced user help us ?

---

