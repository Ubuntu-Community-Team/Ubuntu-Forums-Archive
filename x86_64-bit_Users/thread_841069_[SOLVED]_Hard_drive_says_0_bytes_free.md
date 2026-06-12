---
title: "[SOLVED] Hard drive says 0 bytes free"
date: 2008-06-26
forum: x86 64-bit Users
---

### Post by jcollins on 2008-06-26
Now I know my hard drive is not full, I have a seperate home partition and a 7 gb root partition. I started to get errors with programs complaining about space, so I checked it out and i found that my root drive was "full". But I knew it wasnt, but nonetheless fired up Gparted and added another 2 gigs. But sadly in about 2 days it says it is full again. I have installed no new software. I fired up the "disk usage analyzer" and it says I am only using 3.8gb of hard drive space.

please help

---

### Post by cariboo on 2008-06-26
Could you post the output of df -h . In a terminal type the following:

```
df -h
``` and post the output in your next post.

The reason being, that even if you haven't installed anything lately, if you have done any updates recently the updates do take up room on your hard drive, as apt caches all the updates in /var/cache/apt/archives.

Jim

---

### Post by felker2 on 2008-06-26
From the top of my head: post the output of "df -bM" (or "df -bm"). df means disk free.

---

### Post by jcollins on 2008-06-26
output of df -h:
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5             9.1G  9.1G     0 100% /
varrun               1007M  120K 1007M   1% /var/run
varlock              1007M     0 1007M   0% /var/lock
udev                 1007M   88K 1007M   1% /dev
devshm               1007M   12K 1007M   1% /dev/shm
lrm                  1007M   43M  965M   5% /lib/modules/2.6.24-17-generic/volatile
/dev/sda6              58G   33G   23G  59% /home
overflow              1.0M  208K  816K  21% /tmp
gvfs-fuse-daemon      9.1G  9.1G     0 100% /home/jake/.gvfs
/dev/scd0             4.4G  4.4G     0 100% /media/cdrom0

-b is not a df option

---

### Post by jcollins on 2008-06-26
There is nothing mounted in the .gvfs folder...

jake@jake-laptop:~$ ls -a .gvfs
.  ..
jake@jake-laptop:~$

i dont know what is going on here, but it seems to be a problem with the gvfs-fuse-daemon

---

### Post by jcollins on 2008-06-26
jake@jake-laptop:~$ df -m
Filesystem           1M-blocks      Used Available Use% Mounted on
/dev/sda5                 9284      9272         0 100% /
varrun                    1007         1      1007   1% /var/run
varlock                   1007         0      1007   0% /var/lock
udev                      1007         1      1007   1% /dev
devshm                    1007         1      1007   1% /dev/shm
lrm                       1007        43       965   5% /lib/modules/2.6.24-17-generic/volatile
/dev/sda6                59256     33456     23411  59% /home
overflow                     1         1         1  21% /tmp
gvfs-fuse-daemon          9284      9272         0 100% /home/jake/.gvfs
/dev/scd0                 4437      4437         0 100% /media/cdrom0


Its weird that the gvfs and /dev/sda5 have all the same numbers, even though gvfs should be on the /home partition

---

### Post by jcollins on 2008-06-26
wait i feel stupid, i remember something about gvfs being a mirror of the root file system, maybe thats not the problem

---

### Post by felker2 on 2008-06-26
> **jcollins said:**
> output of df -h:
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5             9.1G  9.1G     0 100% /


your / is full. That way the system can't do very much anymore.

Check /tmp (/temp) for old stuff.

---

### Post by forger on 2008-06-26
or
```

sudo apt-get autoclean
sudo apt-get autoremove --purge
```

---

### Post by jcollins on 2008-06-26
I tried that and cleaning all the cache files in /var/cache.

Its weird because only 3.8 gb of space can be accounted for, and 2gb of space was filled within 2 reboots.

any other ideas?

---

### Post by jcollins on 2008-06-26
I have attached a screenshot of disk usage analyzer. Now there is 333 MB free for some reason, but my guess is that it wont last long.

---

### Post by felker2 on 2008-06-26
> **jcollins said:**
> 
-b is not a df option


My mistake: capital B, thus "df -BM", with M for Megabyte:

```
sander@fujitsu:~$ df -BM
Filesystem           1M-blocks      Used Available Use% Mounted on
/dev/sda2                8447M     7446M      572M  93% /
varrun                    501M        1M      501M   1% /var/run
varlock                   501M        0M      501M   0% /var/lock
udev                      501M        1M      501M   1% /dev
devshm                    501M        1M      501M   1% /dev/shm
lrm                       501M       34M      468M   7% /lib/modules/2.6.22-14-generic/volatile
/dev/sda1               66316M    32454M    33862M  49% /media/sda1
sander@fujitsu:~$
```

Anyway, as said: your / is full. Clean up and things will be OK.

---

### Post by jcollins on 2008-06-26
but thats the problem, only 3.5 gigs can be accounted for. If i sit and add up everything it is 3.5 gigs including hidden stuff. I think I am about to switch to suse. I have used ubuntu since 4.10, but its been getting better and worse at the same time.

---

### Post by cariboo on 2008-06-27
Remember 5% of the partition is reserved for root usage. This is the same across all distributions.

Jim

---

### Post by chrisccoulson on 2008-06-27
The Disk Usage Analyzer is misleading. What is the output of:
```
sudo du -hx --max-depth=1 /
```

It might take a little while

---

### Post by jcollins on 2008-06-27
jake@jake-laptop:~$ sudo du -hx --max-depth=1 /
[sudo] password for jake: 
74M	/boot
113M	/etc
4.0K	/mnt
0	/dev
4.0K	/initrd
16K	/lost+found
6.3M	/bin
4.0K	/srv
0	/proc
0	/tmp
0	/sys
4.0K	/home
3.7M	/lib32
2.5G	/usr
24K	/media
7.7M	/sbin
18M	/root
563M	/lib
5.4G	/var
4.0K	/opt
8.7G	/
jake@jake-laptop:~$ ls /var/archives
ls: cannot open directory /var/archives: Permission denied
jake@jake-laptop:~$ sudo ls /var/archives
jake-laptop-20080612.md5  jake-laptop-20080626.md5
jake-laptop-20080613.md5  jake-laptop-etc.20080622.master.tar.gz
jake-laptop-20080615.md5  jake-laptop-etc.20080625.master.tar.gz
jake-laptop-20080619.md5  jake-laptop-etc.20080626.master.tar.gz
jake-laptop-20080620.md5  jake-laptop-home.20080622.master.tar.gz
jake-laptop-20080621.md5  jake-laptop-home.20080625.master.tar.gz
jake-laptop-20080625.md5  jake-laptop-home.20080626.master.tar.gz
jake@jake-laptop:~$ 

chrisccoulson, thanks, but why is all this crap in /var/archives? It looks like some type of backup program. But i dont run backup. The crap totals about 5.6 GB

---

### Post by chrisccoulson on 2008-06-27
> **jcollins said:**
> jake@jake-laptop:~$ sudo du -hx --max-depth=1 /
[sudo] password for jake: 
74M	/boot
113M	/etc
4.0K	/mnt
0	/dev
4.0K	/initrd
16K	/lost+found
6.3M	/bin
4.0K	/srv
0	/proc
0	/tmp
0	/sys
4.0K	/home
3.7M	/lib32
2.5G	/usr
24K	/media
7.7M	/sbin
18M	/root
563M	/lib
5.4G	/var
4.0K	/opt
8.7G	/
jake@jake-laptop:~$ ls /var/archives
ls: cannot open directory /var/archives: Permission denied
jake@jake-laptop:~$ sudo ls /var/archives
jake-laptop-20080612.md5  jake-laptop-20080626.md5
jake-laptop-20080613.md5  jake-laptop-etc.20080622.master.tar.gz
jake-laptop-20080615.md5  jake-laptop-etc.20080625.master.tar.gz
jake-laptop-20080619.md5  jake-laptop-etc.20080626.master.tar.gz
jake-laptop-20080620.md5  jake-laptop-home.20080622.master.tar.gz
jake-laptop-20080621.md5  jake-laptop-home.20080625.master.tar.gz
jake-laptop-20080625.md5  jake-laptop-home.20080626.master.tar.gz
jake@jake-laptop:~$ 

chrisccoulson, thanks, but why is all this crap in /var/archives? It looks like some type of backup program. But i dont run backup. The crap totals about 5.6 GB

Those are definately backups of some kind, most likely automatically created by software such as SBackup. If you don't want them, you can delete them. Note, /var/archive isn't part of the Filesystem Hierarchy Standard, and doesn't even appear on a default Ubuntu install, so these have been created by some software which you have installed

---

### Post by PrivateAddress on 2008-08-05
How did you ever solve this problem? Was it due only to those files that were apparent back up files of some sort?

I have the exact same problem (hard drive "filling up on its own") although I am on Fedora 9. Last week suddenly the HD was full -- 0 bytes free -- without explanation. Couldn't solve the problem so I wiped everything and did a clean reinstall. Even after running all the updates the machine said yesterday 13 G free. This morning and afternoon still 13 G free. Tonight: 0 bytes free............

Any thoughts?

Thanks,

Ludo

---

