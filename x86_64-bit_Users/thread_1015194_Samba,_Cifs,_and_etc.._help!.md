---
title: "Samba, Cifs, and etc.. help!"
date: 2008-12-18
forum: x86 64-bit Users
---

### Post by linuxn00b84 on 2008-12-18
I've been trying to network 2 computers together for a while now. (Both ubuntu 8.10) and thus far i've managed to install samba, and managed to mount the shares from pc 2 onto pc 1 (But they're only virtually mounted, eg: In nautilus, the bar shows it as: smb://192.168.0.186/anime_and_movies_ii/ ) But if I try to mount it in fstab like: //192.168.0.186/anime_and_movies_ii /mnt/D cifs credentials=/root/.smbcredentials,iocharset=utf8,gid=1000,uid=1000,nounix,file_mode=0777,dir_mode=0777 0 0

The folder in /mnt/D remains empty. i've also tried some other things with no help at all. Does anyone have any ideas on how i can get them from virtually mounted to mounted into /mnt/D? I'm at a loss, any help is appreciated.. Thanks.

---

### Post by Ehtetur on 2008-12-18
hey linuxn00b84 - If you're trying to connect two boxes that both run Linux, you really don't need samba.. Use NFS. it's a lot easier to configure... :twisted:

But since your question is on samba...  If you can manually connect to **smb://192.168.0.186/anime_and_movies_ii/** from nautilus but it does not automount, check to see that your username and password are correct in /root/.smbcredentials...

Also, since you've included a UID in your /etc/fstab, only the user with  UID=1000 can access the share.. You may want to try it without UID and GID, since the username/password is somewhat pretty good protections..

You also may want to check out dmizer's  [samba howto]("http://ubuntuforums.org/showthread.php?t=288534") to verify your other settings are correct.

---

### Post by linuxn00b84 on 2008-12-19
Yeah, thus far i've managed to mount it manually (and it works perfectly) but if i try to mount it from fstab it doesnt show files or folders at all.. it only shows free space.. weird, huh? Anyways the command i use to mount manually is: 

sudo mount -t cifs //192.168.0.186/anime_and_movies_ii /mnt/D -o username=login,password=passwordhere,iocharset=utf8,file_mode=0777,dir_mode=0777

Where as fstab is now (with your suggestion added)

//192.168.0.186/anime_and_movies_ii /mnt/D cifs credentials=/root/.smbcredentials,nounix,file_mode=0777,dir_mode=0777 0 0

And yeah, his guide was one of the first i came across upon my long search of ways to fix it...

---

### Post by Ehtetur on 2008-12-19
> **linuxn00b84 said:**
> And yeah, his guide was one of the first i came across upon my long search of ways to fix it...
darn it :twisted:

Hey, you never said if your username and password were in the file /root/.smbcredentials...


If not already, .smbcredentials will need to be rwx------
> sudo chmod 700 /root/.smbcredentials

I think you have a typo in fstab:
dir_mode=077 7 should be dir_mode=0777

You have iocharset=utf-8 in your manual mount command, but not in your fstab entry...

Try those steps.. everything else looks good! Let me know how it works out for you.

---

### Post by linuxn00b84 on 2008-12-20
Yeah, the user name and pass are already in credentials, and also the iocharset=utf-8 "was" in there, but i removed it to see if that would make it work or not.. and as far as typo's i'm not seeing any in my fstab: [http://pastebin.com/m17f5b5c1](http://pastebin.com/m17f5b5c1)

I'm at a loss... -_-

---

### Post by petersenmde on 2008-12-20
Try leaving the nounix option out.

I had to do this with my Debian Lenny workstation connecting to a samba server. With the nounix option it appeared that it would mount but the directory would be empty.

Mark

---

### Post by linuxn00b84 on 2008-12-20
Removed and still empty... ;[

---

