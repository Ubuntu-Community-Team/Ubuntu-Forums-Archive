---
title: "accesing the windows partition"
date: 2006-02-28
forum: x86 64-bit Users (Pre April '08)
---

### Post by major_doctor_techne on 2006-02-28
Hello,

When i try to access the windows partition, formatted with NTFS, i get the following error message

[SIZE="3"]**The folder contents could not be displayed**.[/SIZE]
You do not have the permissions necessary to view the contents of "sda1".

What can i do to have access to that partition???

Pls help!

---

### Post by alesdoc on 2006-02-28
Modify your fstab-windows-line as following

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
/dev/XXX       /XXX/XXX    ntfs    auto,users,rw,umask=0022     0       0

then

sudo umount /dev/XXX

sudo mount /dev/XXX

where XXX=your windows partition

bye

---

### Post by major_doctor_techne on 2006-02-28
Thank you very much, it works!!!

---

### Post by POWERade on 2006-02-28
[QUOTE=alesdoc]Modify your fstab-windows-line as following

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
/dev/XXX       /XXX/XXX    ntfs    auto,users,rw,umask=0022     0       0

then

sudo umount /dev/XXX

sudo mount /dev/XXX

where XXX=your windows partition

bye[/QUOTE]


um.. where exactly do i go to "modify fstab-windows-line " to type in the other stuff u said.

---

### Post by PrivatePickle on 2006-03-01
Hello,

Go to this link for the unofficial starter guide and scroll down to "15 Windows"

[http://easylinux.info/wiki/Ubuntu]("http://easylinux.info/wiki/Ubuntu")

It will walk you through manually mounting/unmounting windows partitions and setting to mount on boot-up.  Chapter 15.3 is probably the only one you need to follow.  Give it a try and if you have any more questions just ask.

---

### Post by POWERade on 2006-03-01
^Thank you  SO much! that link answered like 75% of the questions I regg'd on this msg board for.

---

### Post by spartan777 on 2006-03-01
but does this mean it will be read-only no matter what when you have ntfs partitions?

---

### Post by Cesium on 2006-03-01
Re: but does this mean it will be read-only no matter what when you have ntfs partitions?

Yeah, you can't write to NTFS in Linux, at least you don't want to. It could goof up the NTFS partition.

---

