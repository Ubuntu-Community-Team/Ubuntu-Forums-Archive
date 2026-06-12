---
title: "[SOLVED] Fireworks help please"
date: 2008-11-19
forum: Wine
---

### Post by Julian1968 on 2008-11-19
I have at last managed to get Fireworks working in wine on Ubuntu Feisty Fawn

The problem is my old Firework images are all on an external hard drive which I can access easily from my desktop

However, when I try to open the files from within Fireworks, the external drive just isnt there

How do I deal with this

Thanks

---

### Post by prshah on 2008-11-19
> **Julian1968 said:**
> 
However, when I try to open the files from within Fireworks, the external drive just isnt there

a) You can use the Wine config GUI (Applications-Wine-Configure Wine) to add your external drive, mapped to a drive letter

== OR ==

b) Create a link with a drive letter to your external drive for wine to use. Open a terminal (Applications-Accessories-Terminal) and give the commands:
```

cd ~/.wine/dosdevices
ln -s /media/disk x:
``` Replace /media/disk with the actual mount point for your external drive, and x: with a drive letter you'd like to use in Wine. This command will link the x: drive (in Wine) to your external harddisk, and make it's contents available at x:

If you have any difficulties, post back with the output of ```
sudo fdisk -l
mount
``` for more detailed instructions.

---

### Post by Julian1968 on 2008-11-19
High prshah

I am completely new to Ubuntu

The other drive is actually a secondary hard drive in my pc and not an external (my fault sorry)

I have no idea what a mount point is. On my desk top the hard drive I want to access is named sdb1 if that makes any difference

So I guess the question is how do I do the mount point ?

---

### Post by prshah on 2008-11-19
> **Julian1968 said:**
> 
The other drive is actually a secondary hard drive in my pc
On my desk top the hard drive I want to access is named sdb1

Fine. Open a terminal (Applications-Accessories-Terminal) and give the following commands, and post back the output. This will give us more information, and then we can give you a more specific command suited to your use.
```

mount | grep sdb
cat /etc/fstab | grep sdb
df -h | grep sdb
ls -l /media
```

---

### Post by Julian1968 on 2008-11-19
Thanks again

a@a-desktop:~$ mount | grep sdb
/dev/sdb1 on /media/sdb1 type ntfs (rw,nls=utf8,umask=007,gid=46)
a@a-desktop:~$ cat /etc/fstab | grep sdb
# /dev/sdb1
UUID=A41C0C171C0BE362 /media/sdb1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
a@a-desktop:~$ df -h | grep sdb
/dev/sdb1             150G  108M  149G   1% /media/sdb1
a@a-desktop:~$ ls -l /media
total 48
lrwxrwxrwx  1 root root        6 2008-10-27 04:00 cdrom -> cdrom0
drwxr-xr-x  2 root root     4096 2008-10-27 04:00 cdrom0
drwxr-xr-x  2 root root     4096 2008-10-27 04:00 cdrom1
drwx------ 24 a    root    32768 1970-01-01 01:00 LACIE
dr-xr-x---  1 root plugdev  4096 2008-11-19 14:08 sda1
dr-xr-x---  1 root plugdev  4096 2008-11-18 10:37 sdb1
a@a-desktop:~$

---

### Post by prshah on 2008-11-19
> **Julian1968 said:**
> Thanks again

a@a-desktop:~$ mount | grep sdb
/dev/sdb1 on /media/sdb1 type ntfs (rw,nls=utf8,umask=007,gid=46)


Fine, your /dev/sdb1 is mounted (accessible) at /media/sdb1. Now, open a terminal, and give the commands```

cd ~/.wine/dosdevices
ln -s /media/sdb1 g:

``` After this, start your Wine program (fireworks) and you should find a new drive "g:" which references your external drive.

If you get any errors with the above, post back with error message. (Eg., Permission Denied).

---

### Post by Julian1968 on 2008-11-20
Worked a treat

Thanks again for your help

---

### Post by prshah on 2008-11-20
> **Julian1968 said:**
> Worked a treat


Good. Can you please mark this thread as solved? Click on "Thread Tools" near the upper right hand side of this page, then click on "Mark As Solved"

---

