---
title: "unable to copy big file to flash disk"
date: 2008-12-03
forum: x86 64-bit Users
---

### Post by wangjiajun on 2008-12-03
Dear all,

I have a problem when copying big files to flash drive in my Hardy. 

I have a 8GB Kingston flash drive. Whenever I want to copy to big file (such as a dvi which is >200MB). The copying progress bar appears and will stuck at almost 100%. After a few seconds, the flash drive is automatically unmounted. When I mount the flash drive again, no file is copyed. 

Tried the command line, 

it says something goes wrong in MAin.C during rename the file in the flash drive. My understanding is, when copying a.avi to flash drive, a temporary file is created. After copying, the temporary file is to be renamed a.avi. However, error happens when renaming. 

Anyone has such problem and knows how to fix it?

Thanks for any help!

---

### Post by felker2 on 2008-12-03
Can you post the output of the CLI cp command?

What filesystem is on the flash disk? (mount command, I think)
How big is the file you want to copy? (ls -al command)
How much space is unused on the flash disk? (df command)

---

### Post by cenwesi on 2008-12-03
i am betting your swap space might be the problem. I posted couple weeks ago about a similar issue i had with WebMin when copying a file over 400meg. Mind you i have 4gigs of ram and i am running 64bit Intrepid. Anyway way i ended up increasing my swap file to solve the problem.

---

### Post by wangjiajun on 2008-12-03
The filesystem is vfat, here is the mount command output for the flash drive:
/dev/sdc1 on /media/DT8GB type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed
,uid=1000,utf8,umask=077,flush)

One example of my file is an avi file which is 285.1MB. 

With 6.4GB free space in the 8GB flash drive, I can not copy that 285.1MB into the flash drive. Using copy paste in X-window would bring a progress bar which is stuck at 100% and disappear and unmount the flash drive. After remount my flash drive, no avi file is there. Interestingly, I can simple copy and paste that particular file into a 2GB flash drive without any problem. :(

Try to use the cp command in konsole, the commands finishes as if it had been successfully executed. However the flash is automatically unmounted and no avi file is there actually after remount. 

Try rsync command and get this error:
rsync: rename "/media/DT8GB/.2007 Fiesta Bowl-OT.avi.W87qdm" -> "2007 Fiesta Bowl-OT.avi": No such file or directory (2)
rsync error: some files could not be transferred (code 23) at main.c(977) [sender=2.6.9]



> **felker2 said:**
> Can you post the output of the CLI cp command?

What filesystem is on the flash disk? (mount command, I think)
How big is the file you want to copy? (ls -al command)
How much space is unused on the flash disk? (df command)

---

### Post by wangjiajun on 2008-12-03
I have a swap partition of 4GB. It is not convenient to increase it because I have to re-partition the whole disk. 

Anyway, I think 4GB should be enough for 285MB file copy. It is really fishy. 


> **cenwesi said:**
> i am betting your swap space might be the problem. I posted couple weeks ago about a similar issue i had with WebMin when copying a file over 400meg. Mind you i have 4gigs of ram and i am running 64bit Intrepid. Anyway way i ended up increasing my swap file to solve the problem.

---

### Post by adamitj on 2008-12-03
Does your pendrive supports that "Kingston protected area" (I don't know the exactly name)?

I had one Kingston pendrive of 512 MB (Yes, a very old one) which cames with a Windows software that creates 2 partitions in my pen-drive, one accessible only after a password input, and other "public", enabled only when no password is supplied.

Can you open your pen-drive into a Windows OS to check out if any password will be asked for?

---

### Post by wangjiajun on 2008-12-03
No ,it does not. 

It is just a simple 8GB flash with only one partition. 

In Windows, it is well recognized and no password is required for any kind of operation on the drive. 

Also the same problem in Ubuntu happens to my other flash drives. 


> **adamitj said:**
> Does your pendrive supports that "Kingston protected area" (I don't know the exactly name)?

I had one Kingston pendrive of 512 MB (Yes, a very old one) which cames with a Windows software that creates 2 partitions in my pen-drive, one accessible only after a password input, and other "public", enabled only when no password is supplied.

Can you open your pen-drive into a Windows OS to check out if any password will be asked for?

---

