---
title: "mounted cd drive doesn't recognize cds"
date: 2016-11-14
forum: Wine
---

### Post by hunzelmann on 2016-11-14
hello there,

my problem is, that my pc, with lubuntu 16.04, just recognizes the first cd i insert after a restart, any further cd is ignored and the cd drive shown as empty

so i searched the internet and found the mount command but my cd drive is already mounted

the command
sudo lsblk -f
returns:
NAME   FSTYPE LABEL UUID                                                       MOUNTPOINT
sda                                                      
&#9500;&#9472;sda1 ext4                   fdee407b-94a8-49cc-9dcc-812e7cbc5341   /
&#9500;&#9472;sda2                                                   
&#9492;&#9472;sda5 swap                 65d00988-7bd5-4d93-98e2-c82162c55311   [SWAP]
sr0                                                                                                /media/friedrich/Disk2

don't really know what to do or to try, i need this for an installation via playonlinux with two cds
i'm thankful for any help :)

have a nice day,
friedrich

---

### Post by yancek on 2016-11-14
It isn't really clear how you are doing what you are doing.  The line below from lsblk output is your CD/DVD drive.

> sr0                                                                                                /media/friedrich/Disk2

When you put in the first CD, it should be available at the location above.  Before removing it to insert the second CD, you must first unmount the first CD:

```
sudo umount /media/friedrich/Disk1
```

Then put in the second CD which will probably be at the same location.  If not, simply mount it.  Why do you need to reboot?

If that isn't the problem, you will need to post more details on exactly what you have done and the result(s).

---

### Post by hunzelmann on 2016-11-17
hey, thank you very much for your answer :)

my steps:
i am starting playonlinux, insert the Disk 1 and automatically mounted
i start an installation with the cd, everything runs fine until the moment i need to insert Disk2

so i tried to unmount the Disk1 before removing it, when the installation told me to

> sudo umount /media/friedrich/Disk1

< umount: /media/friedrich/Disk1: target is busy
        (In some cases useful info about processes that
         use the device is found by lsof(8) or fuser(1).)

so i can't unmount it while the installation is using it :(

but i found a way to workaround:
i copied the files of Disk2 to a folder in my home directory and used this folder as "cd" for the second half of the installation
it worked, i need to put in the Disk1 to play, but the game is running now :)

thanks for your support, i appreciate it ;)
have a nice day

---

### Post by howefield on 2016-11-17
Moved to the "*Wine*" forum.

---

### Post by hunzelmann on 2016-11-17
do i need to close the thread now or mark it as solved?

---

### Post by howefield on 2016-11-17
Near the top of the page.. *Thread Tools > Mark this thread as solved...*

---

