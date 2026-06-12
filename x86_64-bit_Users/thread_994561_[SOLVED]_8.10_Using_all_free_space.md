---
title: "[SOLVED] 8.10 Using all free space"
date: 2008-11-26
forum: x86 64-bit Users
---

### Post by jmacx81 on 2008-11-26
I am having a problem and Ubuntu 8.10 is showing that I have no free space on my 120 gb hard drive when nothing else is installed on it except ubuntu 8.10 I can't save even 20KB text files. Anyone have any idea about this? I'm pretty new to Ubuntu but this seems strange, Please help

Mac
[email]jmacx81@gmail.com[/email]

---

### Post by cariboo on 2008-11-26
To clear up some space on your hard drive open a Applications--Accessories-->Terminal and run the following coomands:

```
sudo apt-get clean
```

and

```
sudo apt-get autoremove
```

This command will remove the archived packages that were downloaded during installation and upgrades.

While you have the terminal open can you paste the output of:

```
df -h
```

in to your next post.

Jim

---

### Post by jmacx81 on 2008-11-27
I ran auto clean and remove and this is what I came up with

mac@mac-laptop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             107G  100G  1.3G  99% /
tmpfs                1004M     0 1004M   0% /lib/init/rw
varrun               1004M  112K 1004M   1% /var/run
varlock              1004M     0 1004M   0% /var/lock
udev                 1004M  2.8M 1002M   1% /dev
tmpfs                1004M  104K 1004M   1% /dev/shm
lrm                  1004M  2.4M 1002M   1% /lib/modules/2.6.27-7-generic/volatile
overflow              1.0M   32K  992K   4% /tmp

I'm not really sure what I'm looking at here.

Thanks
Mac

---

### Post by jmacx81 on 2008-11-27
Hey thanks Jim, everything seems to be working great now.

---

### Post by ve2dmn on 2008-11-27
have you tried Applications->Accessories->Disk Usage Analyzer ?

---

### Post by cariboo on 2008-11-27
Looking at the output of the df command you have Ubuntu installed on one partition. From the listing you had 1.3Gb of free space. Clearing out the archive packages will give you more free space, but keep an eye on your home partition and don't aloow it to fill up or you will run into the same problem to find out how much space your home partition is using, in a terminal type:

```
du -h
```

This will give you the total size of all the files in your home directory.

Jim

---

### Post by jmacx81 on 2008-11-27
> **cariboo907 said:**
> Looking at the output of the df command you have Ubuntu installed on one partition. From the listing you had 1.3Gb of free space. Clearing out the archive packages will give you more free space, but keep an eye on your home partition and don't aloow it to fill up or you will run into the same problem to find out how much space your home partition is using, in a terminal type:

```
du -h
```

This will give you the total size of all the files in your home directory.

Jim


The strange thing is that the only thing that is on this computer is 2 120 gig hard drives and Ubuntu, Sure I have a few programs installed on them but nothing that should take up much space. After I did what you said I now have 95 gigs free but when I was running it it said it would clear up 120 megs. Not sure what happed but all is well now.

---

### Post by jmacx81 on 2008-11-27
> **ve2dmn said:**
> have you tried Applications->Accessories->Disk Usage Analyzer ?

Yup tried that but really didn't tell me much because the whole thing was full under username and just a little was full under other dir's

mac

---

