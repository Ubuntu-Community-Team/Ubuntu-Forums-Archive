---
title: "Samba sharing is not working in 9.10"
date: 2009-11-01
forum: x86 64-bit Users
---

### Post by gretarsson on 2009-11-01
Samba or network sharing is not working, I can not share any of my maps in my pc if I try Alt+F2 "gksudo nautilus" and try to share any maps I allways got this: Failed to execute child process "testparm" (No such file or directory)
Any idea?

---

### Post by Dropbear on 2009-11-01
Try running 

> sudo /etc/init.d/samba restart

see if that works
If it does then samba is not starting at boot.
A workaround is here [http://ubuntuforums.org/showthread.php?t=1290204]("http://ubuntuforums.org/showthread.php?t=1290204")

---

### Post by gretarsson on 2009-11-01
> **Dropbear said:**
> Try running 


see if that works
If it does then samba is not starting at boot.
A workaround is here [http://ubuntuforums.org/showthread.php?t=1290204]("http://ubuntuforums.org/showthread.php?t=1290204")
It is not that, if I try to ad some map into samba share and ok bottom is not working and if I close and open again  then my map is not there and sharing local map inside my pc is not working too, I put in clean install of 9.10

---

### Post by indiandruid on 2009-11-14
Go to Synaptic, seach samba-common-bin, 'Mark for Upgrade' and hit apply.

Folder sharing should now work, without the need for a samba or system restart.

Dependency bug involving 'testparm' methinks.

---

### Post by Zetheroo on 2009-11-14
indiandruid, Thanks! I applied all updates and it worked!

---

### Post by jgeewax on 2009-11-15
Thanks for this, worked perfectly for me:

```
sudo apt-get upgrade samba-common-bin
```

---

### Post by Muley63 on 2009-11-15
Indiandruid,

Thanks for the tip. I couldn't share between two Karmic computers and could not figure it out until your tip. This is something that should have been caught before Karmic was released. Sharing files is so common between computers and it doesn't work between two 9.10s? I really like Ubuntu, but common computer tasks should just work. Plus, they removed 'share' from the administration menu. Why?

---

### Post by gretarsson on 2009-11-15
> **Muley63 said:**
> Indiandruid,

Thanks for the tip. I couldn't share between two Karmic computers and could not figure it out until your tip. This is something that should have been caught before Karmic was released. Sharing files is so common between computers and it doesn't work between two 9.10s? I really like Ubuntu, but common computer tasks should just work. Plus, they removed 'share' from the administration menu. Why?
hey they removed Login from administration too and know we can not use Login menu or replaced, it is lot of mis fail stuff in 9.10 so  I went back to 9.04, I dont like when I haft to spent lot of hour to fix my pc after new install

---

### Post by RAMDrive on 2009-11-16
> **jgeewax said:**
> Thanks for this, worked perfectly for me:

```
sudo apt-get upgrade samba-common-bin
```

Worked here too, thank you.  9.10 x86 32bit.

---

### Post by FirstByté on 2009-11-17
As this is a very crucial tool to virtualizers,

It would just make more sense to have this 'samba-common-bin' thingy 'backport'ed' or pushed into the samba core.

I spent weeks trying to unravel why I couldn't share files between my host and guest OS's. A thing that worked in Ubuntu 9.04. Ubuntu 9.10 is great. This omission or bug should be rectified :popcorn:

Keep sharing guys! Keep Ubunt'ing :P

NOTE:
It worked for me too: > ~$ uname -ar
Linux P34CE 2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:04:26 UTC 2009 i686 GNU/Linux

~$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 9.10
Release:	9.10
Codename:	karmic



---

### Post by indiandruid on 2009-11-18
[COLOR=White]deleted[/COLOR]

---

