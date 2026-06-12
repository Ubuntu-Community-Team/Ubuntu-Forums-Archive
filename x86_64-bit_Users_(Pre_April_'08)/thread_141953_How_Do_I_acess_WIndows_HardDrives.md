---
title: "How Do I acess WIndows HardDrives"
date: 2006-03-09
forum: x86 64-bit Users (Pre April '08)
---

### Post by khalidmian on 2006-03-09
I have a windows based fat 32 back hard drive which i would like to access through ubuntu how do i do that
Please Help

---

### Post by bluevoodoo1 on 2006-03-09
This might help you. 
[http://ubuntuguide.org/#mountunmountfat](http://ubuntuguide.org/#mountunmountfat)
or
[http://ubuntuguide.org/#automountfat](http://ubuntuguide.org/#automountfat)

---

### Post by el3ktro on 2006-03-09
Very easy, first create a new directory where you want your Windows partition to be mounted, say /home/joe/windows-files. Then you have to find out which partition number your Windows partition has. If it is your D: drive for example, it will be most likely /dev/hda2. Then you can mount this partition like this:

mount -f vfat -o uid=1000,gid=1000 /dev/hda2 /home/joe/windows-files

The uid and gid parameter make the files on the Win partition to be owned by you, so you can read/write them without any problems.


Tom

---

### Post by khalidmian on 2006-03-09
ok heres the thing my backup disk drive D is a basic partition in fat 32 the reason i left it as fat 32 was so that i could share it between windows and ubuntu i.e have my media fles etc in it my C drive is NTFS, whilst i have been able to mount my C drive by Ddrive remains unaceesible can anyone help?

---

### Post by el3ktro on 2006-03-09
Did you try the links that bluevoodoo provided?

Tom

---

### Post by khalidmian on 2006-03-09
yes i did thats how i was able to mount my C drive in ntfs but not my D

---

### Post by Mustard on 2006-03-09
[QUOTE=khalidmian]yes i did thats how i was able to mount my C drive in ntfs but not my D[/QUOTE]

Can you show the output of these two comands please...

```
sudo fdisk -l
```

and..

```
cat /etc/fstab
```

---

