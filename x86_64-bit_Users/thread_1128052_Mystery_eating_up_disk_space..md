---
title: "Mystery eating up disk space."
date: 2009-04-17
forum: x86 64-bit Users
---

### Post by X-Seti on 2009-04-17
Ubuntu 8.10 intrepid (Server) 
Hardware; Laptop motherboard (PSU 80Watts) and Tower case running of a VGA monitor, 320Gb HHD with 2Gb of ram. 

I installed this box last Sunday on 2 partitions, One was for the main distro (Ubuntu Server edition) and the other was just an empty partition with my backed up home contents from my previous Ubuntu distro.

I have a 320 Gb HD installed on this box..

200Gigs was for the Linux on Ext2, 5Gbs for Swap - however this was showing up full (0 bytes in the gnome window)?, When only 109Gbs was actually being used?

I deleted the other partition that had the backup home stuff and added this to the Linux main partition, So there should be 283.4 GBs in total.

[[IMG]http://img4.imageshack.us/img4/2659/16137130.th.png[/IMG]](http://img4.imageshack.us/my.php?image=16137130.png)

[[IMG]http://img245.imageshack.us/img245/1825/whatgives.th.png[/IMG]](http://img245.imageshack.us/my.php?image=whatgives.png)

I have looked around the web for reason why this could be, but so far I have come up with nothing and I do not feel like re-installing again. :(

---

### Post by pastalavista on 2009-04-17
Happened to me once when I deleted a partition. I fixed it by booting from a live CD, open the terminal and type:```
sudo e2fsck /dev/sda1
```. Can't guarantee it will work for you though..

---

### Post by X-Seti on 2009-04-17
Been there and done that.

No worky :(

---

### Post by drs305 on 2009-04-17
Take a look at this guide for restoring lost disk space. It's pretty new so if you don't find a solution perhaps it can be expanded. The guide is rather long but if you are in a hurry jump down to Sections 6 and 8.

[_HOWTO: Recover Lost Disk Space_]("http://ubuntuforums.org/showthread.php?t=1122670")

---

### Post by X-Seti on 2009-04-17
Thankyou.

Giving this a try. :)

Edit; I found the problem -Just looking in the dirs for very large files..

```

sudo du -hx --max-depth=1 /var/archives/

events-20090413.md5                events-etc.20090416.master.tar.gz
events-20090414.md5                events-etc.20090417.master.tar.gz
events-20090415.md5                events-home.20090413.master.tar.gz
events-20090416.md5                events-home.20090414.master.tar.gz
events-20090417.md5                events-home.20090415.master.tar.gz
events-etc.20090413.master.tar.gz  events-home.20090416.master.tar.gz
events-etc.20090414.master.tar.gz  events-home.20090417.master.tar.gz
events-etc.20090415.master.tar.gz

```

I would like to know what program generates these?

So I can uninstall and stop this from happening.

---

### Post by drs305 on 2009-04-17
I don't use it but I do know that MySQL uses the term "events" and probably makes logs with that term included.

You might also get an idea of what program it is by looking at the time the files are created, then check crontab (crontab -l or sudo crontab -l) and "cat /etc/anacrontab" to see if there are any listings therein.

---

### Post by X-Seti on 2009-04-18
Ok..
```

usage:	crontab [-u user] file
	crontab [-u user] { -e | -l | -r }
		(default operation is replace, per 1003.2)
	-e	(edit user's crontab)
	-l	(list user's crontab)
	-r	(delete user's crontab)
	-i	(prompt before deleting user's crontab)
k@events:~$ sudo crontab -l
no crontab for root
k@events:~$ 


```

This is starting to be a problem, as the unknown process is overloading this box, slowing everything else down (heating the box up)

I really need to know what program is doing this, because as far as I know, I did not install anything to make backups like this.

I do my backups on a weekly basis, cloning the HD and dumping sqls.
The term 'events' is my box name.

The files that are being created are around 20-50Gbs in size?


Edit; Looking around the crons, daily, I found backup-manager.. :)

I found the problem, I found the config file in /etc/backup-manager.conf,:)

---

