---
title: "INTERNAL ERROR: Cannot create temporary directory!"
date: 2021-11-03
forum: Wine
---

### Post by buw20031220 on 2021-11-03
The Problem still exists, the problem is marked as "solved" but I got a better Workaround:
Supply Temp with a (virtual) Floppy Disk. VFAT is always writeable (unless mounted ro)

wine ./some.exe (typically Python ...)
[42] INTERNAL ERROR: cannot create temporary directory!

&#9484;&#9472;&#9472;(user&#12927;host)-[~/somedir]
&#9492;&#9472;$ file some.exe
some.exe: PE32+ executable (console) x86-64, for MS Windows

&#9484;&#9472;&#9472;(user&#12927;host)-[~/somedir]
&#9492;&#9472;$ ls -laFtr ~/.wine/drive_c/users/user/Temp                                                                                                                            255 &#10799;
total 0
drwxr-xr-x 1 user user 384 Nov  3 12:36 ../
d--------- 1 user user   0 Nov  3 18:01 _MEI424/
d--------- 1 user user   0 Nov  3 18:01 _MEI423/
d--------- 1 user user   0 Nov  3 18:01 _MEI422/
d--------- 1 user user   0 Nov  3 18:01 _MEI426/
d--------- 1 user user   0 Nov  3 18:01 _MEI425/
drwxr-xr-x 1 user user  70 Nov  3 18:01 ./

&#9484;&#9472;&#9472;(user&#12927;host)-[~/somedir]
&#9492;&#9472;$

&#9484;&#9472;&#9472;(user&#12927;host)-[~]
&#9492;&#9472;$ dd if=/dev/zero of=dos.img bs=1M count=100
100+0 records in
100+0 records out
104857600 bytes (105 MB, 100 MiB) copied, 0.0647699 s, 1.6 GB/s

&#9484;&#9472;&#9472;(user&#12927;host)-[~]
&#9492;&#9472;$ ll dos.img
-rw-rw-rw- 1 user user 104857600 Nov  3 17:07 dos.img

&#9484;&#9472;&#9472;(user&#12927;host)-[~]
&#9492;&#9472;$ mkfs.fat dos.img
mkfs.fat 4.2 (2021-01-31)

&#9484;&#9472;&#9472;(root&#128128;host)-[~]
&#9492;&#9472;# sudo vi /etc/fstab

      :
/home/user/dos.img /home/user/.wine/drive_c/users/user/Temp vfat loop,user       0       1

&#9484;&#9472;&#9472;(user&#12927;host)-[~/somedir]
&#9492;&#9472;$ mount /home/user/.wine/drive_c/users/user/Temp                                                                                                                

&#9484;&#9472;&#9472;(user&#12927;host)-[~/somedir]
&#9492;&#9472;$ df
Filesystem     1K-blocks      Used Available Use% Mounted on
   :
/dev/loop0        102182         4    102178   1% /home/user/.wine/drive_c/users/user/Temp

&#9484;&#9472;&#9472;(user&#12927;host)-[~/somedir]
&#9492;&#9472;$ ll /home/user/.wine/drive_c/users/user/Temp
total 22
drwxrwxrwx  3 user user 16384 Jan  1  1970 ./
drwxr-xr-x 17 user user  4096 Nov  3 12:36 ../
drwxrwxrwx  3 user user  2048 Nov  3 17:11 a/

&#9484;&#9472;&#9472;(user&#12927;host)-[~/somedir]
&#9492;&#9472;$ mkdir /home/user/.wine/drive_c/users/user/Temp/abc

&#9484;&#9472;&#9472;(user&#12927;host)-[~/somedir]
&#9492;&#9472;$ chmod u-rwx /home/user/.wine/drive_c/users/user/Temp/abc

&#9484;&#9472;&#9472;(user&#12927;host)-[~/somedir]
&#9492;&#9472;$ ll /home/user/.wine/drive_c/users/user/Temp/
total 24
drwxrwxrwx  4 user user 16384 Jan  1  1970 ./
drwxr-xr-x 17 user user  4096 Nov  3 12:36 ../
drwxrwxrwx  3 user user  2048 Nov  3 17:11 a/
drwxrwxrwx  2 user user  2048 Nov  3 18:29 abc/

&#9484;&#9472;&#9472;(user&#12927;host)-[~/somedir]
&#9492;&#9472;$ wine ./some.exe
   :
   running !

---

