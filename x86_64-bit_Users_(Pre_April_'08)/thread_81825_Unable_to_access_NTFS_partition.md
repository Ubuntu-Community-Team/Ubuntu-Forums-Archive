---
title: "Unable to access NTFS partition"
date: 2005-10-25
forum: x86 64-bit Users (Pre April '08)
---

### Post by Randar on 2005-10-25
I have Windows 2000 and Ubuntu 5.04 x86_64 on the same hard drive. when I'm using ubuntu, The Windows partition is mounted as "/media/hdd1", but it is inaccessible. It says
> You do not have the permissions necessary to view the contents of "hdd1".
when I try to open it, so I have no clue what to do.

It also shows the owner as "root".

Thanks in advance.

---

### Post by Blixter on 2005-10-25
[QUOTE=Randar]I have Windows 2000 and Ubuntu 5.04 x86_64 on the same hard drive. when I'm using ubuntu, The Windows partition is mounted as "/media/hdd1", but it is inaccessible. It says

when I try to open it, so I have no clue what to do.

It also shows the owner as "root".

Thanks in advance.[/QUOTE]

How does your fstab look like??

---

### Post by jon_gunnar on 2005-10-25
[QUOTE=Randar]I have Windows 2000 and Ubuntu 5.04 x86_64 on the same hard drive. when I'm using ubuntu, The Windows partition is mounted as "/media/hdd1", but it is inaccessible. It says

when I try to open it, so I have no clue what to do.

It also shows the owner as "root".

Thanks in advance.[/QUOTE]

You may have to add / change something in /etc/fstab . Post you're file, then it is much easier to answer. As an example, this it my fstab 

/dev/sda1       /media/windows  ntfs    nls=utf8,umask=0222 0       0

---

### Post by HankB on 2005-10-25
I went through the same thing. I would up with an entry in /etc/fstab that looks like:

 /dev/hda1       /c:	     	ntfs    defaults,gid=100,umask=0222  0  0

and made sure that I was a member of the group user (gid=100 => user)

  hbarta@baobab:~$ grep user /etc/group
  users:\x:100:hbarta

HTH,
hank

---

### Post by Ferrat on 2005-10-26
I'm having the same problem but when I added the lines for my other disks in them same fashion that you have Unbuntu can't mount the drives when loading and it can't create or find a mounting point.

Will get screen asap but am currently struggleing with my WiFi WLAN USB so I have to use Internet via Windows

---

### Post by Randar on 2005-11-02
Sorry I took so long here it is

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdd6       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdd3       /home           ext3    defaults        0       2
/dev/hdd1       /media/hdd1     ntfs    defaults        0       0
/dev/hdd5       none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0

Thank you for the help

---

### Post by superhew on 2005-11-02
you need to replace **defaults** with **umask=0222.**
so instead of:```
 # /etc/fstab: static file system information.
 #
 # <file system> <mount point>   <type>  <options>       <dump>  <pass>
 proc            /proc           proc    defaults        0       0
 /dev/hdd6       /               ext3    defaults,errors=remount-ro 0       1
 /dev/hdd3       /home           ext3    defaults        0       2
 /dev/hdd1       /media/hdd1     ntfs  **  defaults**        0       0
 /dev/hdd5       none            swap    sw              0       0
 /dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0
``` 
change it to:```
 # /etc/fstab: static file system information.
 #
 # <file system> <mount point>   <type>  <options>       <dump>  <pass>
 proc            /proc           proc    defaults        0       0
 /dev/hdd6       /               ext3    defaults,errors=remount-ro 0       1
 /dev/hdd3       /home           ext3    defaults        0       2
 /dev/hdd1       /media/hdd1     ntfs    **umask=0222**      0       0
 /dev/hdd5       none            swap    sw              0       0
 /dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0
``` 
make sure you unmount and mount again, or just reboot.

---

### Post by Randar on 2005-11-04
thank you the "umask=0222" made my disk readable but I can't write to the disk. I tried to add "rw,umask=0222" but that did'nt help. Am I missing somthing or does linux just not read ntfs yet?

Thank you

EDIT: I hear it is unsafe to do this, so I don't think I want to take the risk.

---

### Post by jon_gunnar on 2005-11-04
[QUOTE=Randar]thank you the "umask=0222" made my disk readable but I can't write to the disk. I tried to add "rw,umask=0222" but that did'nt help. Am I missing somthing or does linux just not read ntfs yet?

Thank you

EDIT: I hear it is unsafe to do this, so I don't think I want to take the risk.[/QUOTE]

Read access is no problem, and I've been using this for years without any trouble. Write access is something different.
You may have a look at this page for more information about this.
[http://linux-ntfs.sourceforge.net/]("http://linux-ntfs.sourceforge.net/")

---

