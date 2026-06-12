---
title: "a partition-logic for a new installation"
date: 2014-12-27
forum: openSUSE and SUSE Linux Enterprise
---

### Post by dilbert_one on 2014-12-27
want to do a fresh install of opensuse 13.1 

therefore i want to erase all the partition-logic and create a new one 


what about a three folded partition-logic

with root , swap and home 

is this useful: 


```
~> lsblk
NAME MAJ:MIN RM SIZE RO TYPE MOUNTPOINT
sda 8:0 0 465,8G 0 disk
&#9500;&#9472;sda1 8:1 0 156M 0 part /boot/efi
&#9500;&#9472;sda2 8:2 0 400M 0 part /boot
&#9492;&#9472;sda3 8:3 0 465,2G 0 part
&#9492;&#9472;cr_ata-ST500LT012-xxx_xxx-part3 254:0 0 465,2G 0 crypt
&#9500;&#9472;system-swap 254:1 0 2G 0 lvm [SWAP]
&#9500;&#9472;system-root 254:2 0 40G 0 lvm /
&#9492;&#9472;system-home 254:3 0 423,2G 0 lvm /home
```

---

### Post by TheFu on 2014-12-27
Why use LVM at all?  There are reasons, but you haven't articulated any worth the extra complexity.  Spanning file systems across different storage can lead to issues.  Encryption can work - but getting the Ubuntu installer to honor non-default partitioning with encryption is non-trivial. I've tried.

I don't have an EFI box and run many systems with just 1 partition - these are virtual machines with well-known requirements for disk, ram, cpu, and networking.  No swap at all.  Desktops always, always, always need swap. On a physical machine, I do this:

* /boot - 800MB - 500MB is probably fine, but watch that it doesn't get full. Less can lead to issues with too many kernels and running out of space mid-upgrade sucks. [http://blog.jdpfu.com/2013/02/23/cleanup-old-kernels-from-apt](http://blog.jdpfu.com/2013/02/23/cleanup-old-kernels-from-apt)
* / - 20G (or so).  Enough for programs - 20G is really overkill unless you want to try 20 different GUIs and never clean the unused versions/programs up.
* /var .... enough for the needed use on the machine. A single website might need 1G, but virtual machine servers probably need 1TB or more. Really just depends.
* /home - for a desktop with just me - 5G.  I don't keep media files there. This is a ton of storage for my perl development and documents.  Java and C/C++ programmers might want 30-40G for all the compiled stuff and libraries.  Python, perl, php, Ruby ... 5-10G is fine even if you use rvm or perlbrew.  I actually do perl development on a desktop (my primary desktop) running inside a virtual machine. Here's the storage for that box:
```
$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/vda1        14G   11G  1.6G  88% /
$ swapon -s
Filename                                Type            Size    Used    Priority
/dev/vda5                               partition       1591292 91248   -1

```
Yes - it really is 14G for everything.

* /D/*  ----- this is where I mount other storage as needed. Most systems get NFS storage from other machines. Only a few machine have extra disks added to be used as network storage for all the others.  Use autofs, to only mount storage when needed, which is great for USB storage, not just NFS stuff.   /D/T (TV), /D/V (home videos), /D/Music, /D/M (movies) .... you get the idea.

Everything needs to be backed up, so limiting the storage available to a system really is a management tool to limit the amount of backup storage required.  For the 30 systems here, daily, versioned, backups (60-120 days each) need about 500G of storage.  Media backups are different - can't keep versioned backups for all that stuff - too large.

My storage design is about backups, disaster recovery, and system upgrades. The goal is to minimize trouble in the future and to have a way to recover after logical or physical issues.  We talk about backups all the time, but that really is just 10% of it.  A backup that cannot be restored is completely worthless. Practice restoring, please.  Oh - and if you use encryption - backups are 100x more important. When bad things happen to encrypted disks, the only real solution is to restore.

Swap sizes depend on workload and whether you hibernate. For desktops, 4G of swap seems a reasonable amount or 1.1x the amount of RAM if you hibernate (whichever is larger).  I've found that 2G of swap on a 2G RAM netbook desktop is just a little too small. The system crashed with a few browser tabs opened. Going to 4G swap made all those crashes stop.  Swap slows down the system so we get a feeling that RAM is being over-committed and can free some resources. With SSDs, it takes more RAM swap to notice the slowdown, at least for me.

Anyway - hope all this helps.

---

### Post by coffeecat on 2014-12-27
Support, not a Cafe thread.

*Thread moved to **openSUSE and SUSE Linux Enterprise**.*

---

### Post by dilbert_one on 2014-12-29
hello dear ubuntulinux-experts, 

i am currently planning a new (totally new and fresh installation of opensuse linux version 13.2 

therefore i want to create new partitons on linux. 

by the way - how do you like this idea: a three folded partition

what about this sheme:

to create a file structure like so
```

~> lsblk
NAME MAJ:MIN RM SIZE RO TYPE MOUNTPOINT
sda 8:0 0 465,8G 0 disk
&#9500;&#9472;sda1 8:1 0 156M 0 part /boot/efi
&#9500;&#9472;sda2 8:2 0 400M 0 part /boot
&#9492;&#9472;sda3 8:3 0 465,2G 0 part
&#9492;&#9472;cr_ata-ST500LT012-xxx_xxx-part3 254:0 0 465,2G 0 crypt
&#9500;&#9472;system-swap 254:1 0 2G 0 lvm [SWAP]
&#9500;&#9472;system-root 254:2 0 40G 0 lvm /
&#9492;&#9472;system-home 254:3 0 423,2G 0 lvm /home

```
can i create this with gparted

well - how to do that?

.**update: ** to clear up all the things in this 

how is this being done

```


&#9492;&#9472;cr_ata-ST500LT012-xxx_xxx-part3 254:0 0 465,2G 0 crypt
&#9500;&#9472;system-swap 254:1 0 2G 0 lvm [SWAP]
&#9500;&#9472;system-root 254:2 0 40G 0 lvm /
&#9492;&#9472;system-home 254:3 0 423,2G 0 lvm /home
```


note: i want to do this with gparted! 

this line looks interesting. .... 
```


&#9492;&#9472;cr_ata-ST500LT012-xxx_xxx-part3 254:0 0 465,2G 0 crypt
```

how to do this with gparted

many thanks for any and all help

---

### Post by TheFu on 2014-12-29
You asked this already in another thread. And I responded there.

---

### Post by dilbert_one on 2014-12-29
hello you both 

many many thanks for your help and all the hints. great thing



> 
Why use LVM at all?  There are reasons, but you haven't articulated any  worth the extra complexity.  Spanning file systems across different  storage can lead to issues.  Encryption can work - but getting the  Ubuntu installer to honor non-default partitioning with encryption is  non-trivial. I've tried.

good ideas - food for thougth


many many thanks 

.** one last question though  **

just to understand this a bit more.
how is this being  done

```


&#9492;&#9472;cr_ata-ST500LT012-xxx_xxx-part3 254:0 0 465,2G 0 crypt
&#9500;&#9472;system-swap 254:1 0 2G 0 lvm [SWAP]
&#9500;&#9472;system-root 254:2 0 40G 0 lvm /
&#9492;&#9472;system-home 254:3 0 423,2G 0 lvm /home
```


**note: **i want to do this with gparted! 

this line looks interesting. .... 
```


&#9492;&#9472;cr_ata-ST500LT012-xxx_xxx-part3 254:0 0 465,2G 0 crypt
```

what is the deeper sense of this line. And finally: how to do this with gparted?

---

### Post by oldfred on 2014-12-29
Threads merged, please do not create duplicate threads with same issue.
We all are volunteers, so need to see other posts so we do not duplicate effort.

Does OpenSuse let you install to partitions or is its only install the LVM type install?
Gparted does not work on LVM partitions. 

       LVM - Logical Volume Management.
Advantages/Disadvantages LVM Post #9
[http://ubuntuforums.org/showthread.php?t=1586328&p=9917145#post9917145](http://ubuntuforums.org/showthread.php?t=1586328&p=9917145#post9917145)
[https://wiki.ubuntu.com/Lvm](https://wiki.ubuntu.com/Lvm)
[https://help.ubuntu.com/community/UbuntuDesktopLVM](https://help.ubuntu.com/community/UbuntuDesktopLVM)
2014_02_22_Preparing Logical Volumes For Ubuntu Installations
[http://members.iinet.net/~herman546/2014_02_22_Preparing%20Logical%20Volumes%20For%20Ubuntu%20Installations.html](http://members.iinet.net/~herman546/2014_02_22_Preparing%20Logical%20Volumes%20For%20Ubuntu%20Installations.html)

---

### Post by dilbert_one on 2014-12-29
hello again 

well since the line cr_ata... is the line which shows your CD/DVD drive. 

hmm gparted  should be fairly self-explanatory -lots of folks all over the planet use it. 
on the other handside we just could use  fdisk, bit it is a CLI-tool, so maybe this is just a bit more difficult
 

well the above mentioned line is the luks-container-line 
 
he takes over the encryption of all that is not root  
 
can i ceate all the above mentioned things with a cli-tool.  
hmm - guess gparted is pretty easy - easier than other tools

---

