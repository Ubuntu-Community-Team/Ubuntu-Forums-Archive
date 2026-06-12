---
title: "Cannot mount NTFS"
date: 2008-11-17
forum: x86 64-bit Users
---

### Post by Vishnu V on 2008-11-17
i cann't mount NTFS partition from my administrative account directly
When i tried to mount NTFS partition it shows the error message
"The volume uses the NTFS file system which is not supported by your system."
and if i mount ntfs partition from any desktop user account and then i can mount the ntfs partition from administrative account.  


what can i do to mount it directly...



thanks in advance


sorry for my bad english

---

### Post by ronnielsen1 on 2008-11-17
**

---

### Post by Zafrusteria on 2008-11-17
If you install the drivers for NTFS eg. ntfs-3g, Then you can mount the disk with the mount command or at boot time and use read/write.

Install and Mount Commands
```
sudo apt-get install ntfs-3g
sudo mount -t ntfs-3g /dev/sda1 /media/win_c

```

If you want to mount the drive automatically when the host is booted then you need to add something like the following in your /etc/fstab

```
/dev/sda1 /media/win_c ntfs-3g defaults,umask=007,gid=46 0 7 
```

Hope that helps.

---

### Post by Bonster on 2008-11-17
Go: Add/remove
Install NTFS configuration tool
or use Storage Device manager

---

### Post by drs305 on 2008-11-17
The specifics for what Bonster recommends, which is probably the easiest method to auto-mount ntfs partitions:

Install ntfs-config and ntfsprogs:
```
sudo apt-get install ntfs-config ntfsprogs
```

Then run *ntfs-config*: 
From the main menu, System Tools, NTFS Configuration Tool.
Enable internal/external write support.
You will be asked to name a mountpoint. You can type in an existing folder or, if it doesn't exist, a new mountpoint will be created. The mountpoint should be in, or will be created in, /media. 
Examples:
You already have a mountpoint at /media/myfiles:  type in '*myfiles*'
You don't have a mountpoint: type in '*myfiles*' and /media/myfiles will be created.
An entry in fstab will be created so the ntfs partition will be automatically mounted.

*ntfsprogs* is a useful tool to have installed. It enables older versions of gparted to work with ntfs partitions (newer versions already can do this) and also have apps to create ntfs labels. In terminal, type 'man ntfsprogs' to see what this app can do.

---

### Post by Vishnu V on 2008-11-26
thanx

     my problem solved

---

