---
title: "Unable to copy a file from Ubuntu to Windows"
date: 2009-05-08
forum: x86 64-bit Users
---

### Post by Cheezespread on 2009-05-08
Hi guys,

I upgraded Ubuntu from Ibex to Jaunty a week back . When i mounted my windows drives and tried to copy a file from Ubuntu to Windows , it's throwing me an error " Permission denied" and the paste option doesnt appear. But when i try to move the file using terminal using sudo , the file gets moved successfully. Is there any settings that i need to change since the same is clearly not letting me copy without the sudo command and through terminal?

Thanks a lot in advance

---

### Post by milton1 on 2009-05-08
The sudo command is giving you root permissions to move the file. If you want to access write capability in the windows folder without sudo, you will need to change ownership of the folder, or allow any user to write to it. Either of the following codes will do this.

```
 sudo chown <user>:<group> <filename>
```
```
 sudo chmod 777 <filename> 
```

---

### Post by Cheezespread on 2009-05-08
Thanks for the reply. The permissions in mounted windows directory or folders within it  are not changing with the chmod command. And hence i am not able to write any file to that folder or directory .

I had even tried the below :
```
sudo chmod o+rwx /media/NewVolume
```

NewVolume is the name of the mounted Windows directory.

This is current settings for my windows drives.
```
cheeze@Giza:~/Desktop$ ls -lr /media/
total 48
dr-xr-xr-x 1 root root 36864 2009-05-07 22:30 windows
dr-xr-xr-x 1 root root  4096 2009-05-08 19:41 NewVolume
dr-xr-xr-x 1 root root  4096 2009-05-02 15:43 HPRecovery
drwxr-xr-x 2 root root  4096 2009-04-29 01:54 cdrom0
lrwxrwxrwx 1 root root     6 2009-04-29 01:54 cdrom -> cdrom0
```

Any help would be appreciated.Only root is able to move any file from my Ubuntu drive to Windows.

---

### Post by Cheezespread on 2009-05-10
Any help would be greatly appreciated since my sis also uses my laptop and she finds it easier with the GUI copy and paste. Thanks a lot in advance.

---

### Post by aimonas on 2009-05-12
> **Cheezespread said:**
> Any help would be greatly appreciated since my sis also uses my laptop and she finds it easier with the GUI copy and paste. Thanks a lot in advance.
try to use the recursive option of chmod for your windows folder: 
```
chmod -R +rw ./WindowsFolder
```
I don't know if it will help but it's worth a try

alternatively you may try 
```
gksu nautilus
``` 
to perform the operations you want as root from the graphical environment

greets

---

### Post by wabbalee on 2009-05-12
another way is to mount the windows drive permanently by editing your /etc/fstab file and set permissions there:

/dev/sdxy  /mnt/sdxy ntfs defaults,umask=000,uid=1000,gid=100,auto,rw,user 0 2

assuming your windrive is ntfs. sdxy where x is the letter of your drive, possibly just 'a' and y is the partition number. you will have to create a directory inside the /mnt directory named (example) 'sda1'.

then after reboot this folder will contain the contents of your windows drive and you can read, write, edit and last but not least DELETE everything on that partition, so be warned and careful.

the only thing I am not certain about is the ntfs bit in the syntax, it could be ntfs3g... but that's just a matter of getting the spelling right.

the last time I done this was on a FAT32 drive and then you just write vfat in the syntax instead of ntfs.

---

### Post by sahabcse on 2009-05-12
For mounting NTFS/FAT32 partition pls follow below url

[http://sahabm.blogspot.com/2009/03/mount-ntfs-fat32-windows-drive-in.html](http://sahabm.blogspot.com/2009/03/mount-ntfs-fat32-windows-drive-in.html)

---

### Post by Cheezespread on 2009-05-12
Thanks a lot to all :) .. I had permanently mounted the windows drive a bit back after i had to reinstall Jaunty and i had done mistake in the permissions part.Thanks a lot again

---

