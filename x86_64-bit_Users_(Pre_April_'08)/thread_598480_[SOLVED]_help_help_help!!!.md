---
title: "[SOLVED] help help help!!!"
date: 2007-10-31
forum: x86 64-bit Users (Pre April '08)
---

### Post by radopenev on 2007-10-31
I know-- I'm stupid,stupid man!
I'm Dapper x86_64 user
A while ago I attempted to install Cinelerra!
And get only errors,errors errors....:confused:
cinelerra: /lib/libc.so.6: version `GLIBC_2.4' not found (required by cinelerra)
And I do one stupid step :
1.download glibc-32bit-2.6.1-18.x86_64.rpm
2. sudo alien glibc-32bit-2.6.1-18.x86_64.rpm
Password:
Warning: Skipping conversion of scripts in package glibc-32bit: postinst
Warning: Use the --scripts parameter to include the scripts.
glibc-32bit_2.6.1-19_amd64.deb generated
3.GDebi Packege Installer
glibc-32bit_2.6.1-19_amd64.deb
and again errors,errors errors....
AND I(stupid,stupid):confused:
copy libc-2.6.1.so
rename like libc-2.3.6.so
save old     /lib/libc-2.3.6.so        like          libc-2.3.6.soOLD
and paste new one into /lib/
Now I have broken shell :can't run sudo or any shell command
edit :  And after restarting ,can't run Ubuntu...
I attempted with recovery mode,but :
error while open share file libc-2.6.1.so
Yes stupid ,but has anyone any idea without  reinstall Ubuntu!:confused:

---

### Post by radopenev on 2007-11-01
Please ,people!Help me !This night was sleepless for me!:confused:
I'm asking for advice!I think,I too closely to solution.
Through GRUB see:

grub>find /lib/libs.so.6
[49914936.0.10] (hd0,2)

grub>root (hd0,2)
filesystem type is **ext2fs** ,partition **0x83**

After that I use liveCD and attempt to mount :

sudo mount -t ext2fs '(hd0,2)' /mnt

but get error 1.unknown filesystem 2.dev (hd0,2) not exist
I think if exist any way to rename file through GRUB that is solution!
Sorry for my English!
Best regards!

---

### Post by kuja on 2007-11-01
hd0,2 refers to the third device on the first hard drive. 

To mount this partition, the command you need is likely something like this:

"sudo mkdir /media/something; sudo mount -t ext2 /dev/?da3 /media/something"

---

### Post by radopenev on 2007-11-01
:lolflag:
OK people!I've just got the solution!
Thank you for advices!
If anyone become at the same situation,think this help:
1.You need of liveCD 
2.After loading in terminal:

sudo fdisk -l

(on my PC I've got some OS and saw )
............
/dev/sda3            1913        4236    18667530   83  Linux
............
3.That is all I need!
sudo mount -t ext3 /dev/sda3 /mnt

4.After that all my broken Linux is on /mnt

sudo nautilus
And copy,rename,delete.....what you want!
After rebooting :guitar:
Sorry for my English!
Best regards!

---

