---
title: "folder/file ownership/permissions fail to change"
date: 2009-11-06
forum: x86 64-bit Users
---

### Post by cscott0108 on 2009-11-06
I am trying to change the permissions of some files, I have 
sudo chown -r chris:chris [file] to change the owner and hit enter it gives no error when it is done, but when I checked the folder it still had root:root ownership. after trying and failing for 10 minutes it still failed to change. Even after going strait su into the console. Finally I logged out of my user started console login and logged in as root started the x server and got into the root GUI to change the permissions and like before it would let me change the owner hit Okay with no problems but when i check the permissions again it was reading root again. What I was trying to do is make a .doc file read only, so what I decided to since I was root I would change the file to read only for all users and groups and that too let me change it with no problems, but when I checked the permissions it was back to full control.
 I use this folder group between two Linux machines I created it on my Kubuntu 9.04 machine and moved it via flash to my Laptop and pasted it in, I thought that was the reason so I created a new directory group and opened everything up to re save it on my laptop with my permissions but they came back up as root and full control when I tried to change the owner and permissions again it failed any ideas.
 Both the 9.04 and 9.10 machines are x64 so I would no think they are platform related issues.

---

### Post by cscott0108 on 2009-11-06
Okay I discovered the problem it is because I had the folder on a NTFS partition I was able to work around it with this command.

chris@chris-laptop-linux:~$ sudo umount /dev/sdb1
chris@chris-laptop-linux:~$ sudo mount /dev/sdb1 /media/sdb1/ -t ntfs-3g -o uid=1000,gid=1000,umask=000

anyone know how I can make this permanent in the /etc/fstab file so I can modify it thanks

---

