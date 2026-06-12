---
title: "Swap Partition for 64 Bit Ubuntu"
date: 2009-07-19
forum: x86 64-bit Users
---

### Post by seabiscuit on 2009-07-19
Hi, 

I am a linux newbie. I heard great things about this forum and I am hoping that I will get some help from the experts here.

I have a Dell Laptop XPS M1530 that I organized as a dual boot ubuntu 32bit/ ubuntu 64 bit boot with a partition for 32 and one for 64 bits. The reason I needed to do this is not important for the posting (basically I have some programs that are compiled for 32 and they aren't backward compatible).

My question is about the swap partition. 

I am working on my Ubuntu 64 and expected to be able to use all my 4 GB RAM and the swap partition. My original linux-swap partition had less than 4GB. When I tried to run a scientific program that required more than 8 GB memory usage, my program crashed.

I went ahead and used the GParted tool and I extended now my linux-swap partition to 13.16 GB.

However when running on 64 bits, it seems that my machine does not recognize that I have so much more swap now and therefore I cannot run my program :(

My question is: what should I do to be able to use all the 13+ GB of swap partition now?? (while running a program in the 64 ubutu, program that would require more than 8 GB memory...)

Please see below the output of my command: top. It shows that my machine sees less than 4GB of the swap:

top - 20:39:18 up 16 min,  3 users,  load average: 0.00, 0.05, 0.07
Tasks: 142 total,   2 running, 140 sleeping,   0 stopped,   0 zombie
Cpu(s):  1.6%us,  0.3%sy,  0.0%ni, 98.0%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   3998964k total,   579004k used,  3419960k free,    17032k buffers
S**wap:  3542292k total,        0k used,  3542292k free,   216912k cached**
     

Thank you very much for your help!!!

---

### Post by seabiscuit on 2009-07-20
I posted this also in the General forum, however no answer yet :( hope this forum will be more responsive...
 
Hi, 
 
I am a linux newbie. I heard great things about this forum and I am hoping that I will get some help from the experts here.
 
I have a Dell Laptop XPS M1530 that I organized as a dual boot ubuntu 32bit/ ubuntu 64 bit boot with a partition for 32 and one for 64 bits. The reason I needed to do this is not important for the posting (basically I have some programs that are compiled for 32 and they aren't backward compatible).
 
My question is about the swap partition. 
 
I am working on my Ubuntu 64 and expected to be able to use all my 4 GB RAM and the swap partition. My original linux-swap partition had less than 4GB. When I tried to run a scientific program that required more than 8 GB memory usage, my program crashed.
 
I went ahead and used the GParted tool and I extended now my linux-swap partition to 13.16 GB.
 
However when running on 64 bits, it seems that my machine does not recognize that I have so much more swap now and therefore I cannot run my program :sad:
 
My question is: what should I do to be able to use all the 13+ GB of swap partition now?? (while running a program in the 64 ubutu, program that would require more than 8 GB memory...)
 
Please see below the output of my command: top. It shows that my machine sees less than 4GB of the swap:
 
top - 20:39:18 up 16 min, 3 users, load average: 0.00, 0.05, 0.07
Tasks: 142 total, 2 running, 140 sleeping, 0 stopped, 0 zombie
Cpu(s): 1.6%us, 0.3%sy, 0.0%ni, 98.0%id, 0.0%wa, 0.0%hi, 0.0%si, 0.0%st
Mem: 3998964k total, 579004k used, 3419960k free, 17032k buffers
S**wap: 3542292k total, 0k used, 3542292k free, 216912k cached**
 
 
Thank you very much for your help!!!

---

### Post by az on 2009-07-20
Run

sudo parted -l

Then, run

cat /etc/fstab

and then

sudo swapon -s

And post the result of all of those.  That will list 1- all your partitions, 2- all the partitions that are supposed to be used and then all the partitions that are currently being used for swap.

---

### Post by seabiscuit on 2009-07-21
> **az said:**
> Run

sudo parted -l

Then, run

cat /etc/fstab

and then

sudo swapon -s

And post the result of all of those.  That will list 1- all your partitions, 2- all the partitions that are supposed to be used and then all the partitions that are currently being used for swap.

Thanks az for your reply. Please see below the answers to the commands you suggested:

 > sudo parted -l

Model: ATA ST9320421ASG (scsi)
Disk /dev/sda: 320GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system  Flags
 1      32.3kB  98.7MB  98.7MB  primary   fat16             
 2      98.7MB  3323MB  3224MB  primary   fat32             
 3      3323MB  118GB   115GB   primary   ext3         boot 
 4      118GB   320GB   202GB   extended                    
 6      118GB   263GB   145GB   logical   ext3              
 7      263GB   306GB   42.6GB  logical   ext3              
 5      306GB   320GB   14.1GB  logical   linux-swap        

Note: seems that it sees the linux-swap above with 14.1 GB

> cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda6 during installation
UUID=058da287-2e09-4490-89fc-ff0544449c59 /               ext3    relatime,errors=remount-ro 0       1
# /data was on /dev/sda7 during installation
UUID=2ddd6984-5b19-43a7-a380-5157080072ea /data           ext3    relatime        0       2
# /ubuntu32 was on /dev/sda3 during installation
UUID=3549dcfe-054b-4f97-9291-c676911b1714 /ubuntu32       ext3    relatime        0       2
# swap was on /dev/sda5 during installation
UUID=cf35bd98-9617-4791-b4f2-7cd4dc7aa9a6 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0


sudo swapon -s

 cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda6 during installation
UUID=058da287-2e09-4490-89fc-ff0544449c59 /               ext3    relatime,errors=remount-ro 0       1
# /data was on /dev/sda7 during installation
UUID=2ddd6984-5b19-43a7-a380-5157080072ea /data           ext3    relatime        0       2
# /ubuntu32 was on /dev/sda3 during installation
UUID=3549dcfe-054b-4f97-9291-c676911b1714 /ubuntu32       ext3    relatime        0       2
# swap was on /dev/sda5 during installation
UUID=cf35bd98-9617-4791-b4f2-7cd4dc7aa9a6 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
bogdan@bogdan-laptop:~$ sudo swapon -s
Filename                Type        Size    Used    Priority
/dev/sda5                               partition    3542292    0    -1

Note: seems that here the swap is seen with only 3542292 which is consistent with the "Swap: 3542292k  total"  I get when running top from the command line.

I would appreciate guidance here about how to make it see the 14.1 GB that I assigned to the swap partition.

Thank you very much!

---

### Post by Sef on 2009-07-21
merged dup threads.

---

### Post by az on 2009-07-21
Perhaps you increased the size of the swap partition without increasing the swapspace (the swap "filesystem")?  Recreate the swap space on the partition.

sudo swapoff -av
sudo mkswap /dev/sda5 -U cf35bd98-9617-4791-b4f2-7cd4dc7aa9a6

That should use the whole thing.

Then try it:

sudo swapon -av
free

(post the output)

---

### Post by litspliff on 2009-07-21
this is a problem with your /etc/fstab i think.
this is the config file for automounting your partitions.
make sure both versions of ubuntu have fstab setup properly.

use "vol_id [device path]" at the commanad line to get your UUID for the partition. make sure that UUID is correctly set in fstab for your swap partition.

it's quite possible that the version you ran gparted in has the fstab correct, and the other version has an incorrect UUID or other parameter. i don't know very much about the UUID, but i suspect it changes when you resize the partition.

---

### Post by az on 2009-07-21
> **litspliff said:**
> this is a problem with your /etc/fstab i think.
this is the config file for automounting your partitions.
make sure both versions of ubuntu have fstab setup properly.


If that were the case, then the swap would not be mounted at all.  Here, 3.5 gigs of swap is being used - so the old UUID is still there.

---

### Post by litspliff on 2009-07-21
> 
Filename                         Type                Size                Used          Priority
/dev/sda5                                       partition        3542292         0                -1



allegedly allocated, but not used.....i haven't seen anything that suggests that any data is actually being paged to it.
once again...use the command to verify your UUID

resizing a partition should change the UUID according to the links below.

[http://www.opengroup.org/dce/info/draft-leach-uuids-guids-01.txt](http://www.opengroup.org/dce/info/draft-leach-uuids-guids-01.txt)
[http://en.wikipedia.org/wiki/Universally_Unique_Identifier](http://en.wikipedia.org/wiki/Universally_Unique_Identifier)

just the fact that UUID utilises a timestamp would necessitate a change because the resize happened at a later time.

also, dude......were you in 64 or 32 when you resized....i'm guessing 32.

---

### Post by seabiscuit on 2009-07-22
> **litspliff said:**
> this is a problem with your /etc/fstab i think.
this is the config file for automounting your partitions.
make sure both versions of ubuntu have fstab setup properly.

use "vol_id [device path]" at the commanad line to get your UUID for the partition. make sure that UUID is correctly set in fstab for your swap partition.

it's quite possible that the version you ran gparted in has the fstab correct, and the other version has an incorrect UUID or other parameter. i don't know very much about the UUID, but i suspect it changes when you resize the partition.

litsliff:

Per your suggestion, I have used the command you indicated to find the UUID for the swap partition. Please see output below:

vol_id /dev/sda5 

ID_FS_USAGE=other
ID_FS_TYPE=swap
ID_FS_VERSION=2
ID_FS_UUID=cf35bd98-9617-4791-b4f2-7cd4dc7aa9a6
ID_FS_UUID_ENC=cf35bd98-9617-4791-b4f2-7cd4dc7aa9a6
ID_FS_LABEL=
ID_FS_LABEL_ENC=

The UUID seems to be consistent with what I have in my fstab:

 cat fstab
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda6 during installation
UUID=058da287-2e09-4490-89fc-ff0544449c59 /               ext3    relatime,errors=remount-ro 0       1
# /data was on /dev/sda7 during installation
UUID=2ddd6984-5b19-43a7-a380-5157080072ea /data           ext3    relatime        0       2
# /ubuntu32 was on /dev/sda3 during installation
UUID=3549dcfe-054b-4f97-9291-c676911b1714 /ubuntu32       ext3    relatime        0       2
# swap was on /dev/sda5 during installation
UUID=cf35bd98-9617-4791-b4f2-7cd4dc7aa9a6 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

PS: I will try to follow az's advice as the next step

---

### Post by seabiscuit on 2009-07-22
> **az said:**
> Perhaps you increased the size of the swap partition without increasing the swapspace (the swap "filesystem")?  Recreate the swap space on the partition.

sudo swapoff -av
sudo mkswap /dev/sda5 -U cf35bd98-9617-4791-b4f2-7cd4dc7aa9a6

That should use the whole thing.

Then try it:

sudo swapon -av
free

(post the output)


Yuppie!

Thanks a lot az!!! 

Your solution worked!!!

here is the sequence of commands i tried per your suggestion and the outputs:

sudo swapoff -av
swapoff on /dev/sda5

sudo mkswap /dev/sda5 -U cf35bd98-9617-4791-b4f2-7cd4dc7aa9a6
Setting up swapspace version 1, size = 13799828 KiB
no label, UUID=cf35bd98-9617-4791-b4f2-7cd4dc7aa9a6

sudo swapon -av
swapon on /dev/sda5

free
             total       used       free     shared    buffers     cached
Mem:       3998964     604356    3394608          0      15876     198836
-/+ buffers/cache:     389644    3609320
Swap:     13799824          0   13799824

Also I tried "top" my naive way to check memory and swap and got:

Swap: 13799824k total,        0k used, 13799824k free,   198912k cached

Thank you so much!

It is truly awesome that there are people out there both experts and kind enough to explain ...

PS: so basically, to recap what I did wrong: I "increased the size of the swap partition without increasing the swapspace (the swap "filesystem")"
Interesting, as i get now the concepts more clear...i thought that resizing partition should be enough.

---

