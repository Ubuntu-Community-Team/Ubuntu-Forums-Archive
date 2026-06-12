---
title: "Firefox takes FOREVER to load..."
date: 2005-05-21
forum: x86 64-bit Users (Pre April '08)
---

### Post by joekr on 2005-05-21
Hey all,

I've noticed that somtimes Firefox takes upwards to about a minute to launch (on a AMD64 4000+ machine).

I think it may have something to do with the screensaver.  I would return from my blank-screen screensaver, and Firefox just takes forever to load.

I've temporarily disabled the screen saver and now manually turn off my LCD when I'm not at my desk.  Is this a common bug?  Are there any other solutions?

AMD64 4000+
1 GB RAM
6600 vid card

[UPDATE]

After a few days of observation, I ***believe*** the problem is directly related to forceful unmounting of a samba fileshare.

My computer boots up with mounted Samba shares (so I can access files on my server locally).  There are times where I wish to unmount the share because the server is off (or in windows).  When entering 

```
sudo umount /home/joe/p4box
``` 

I get the error

> joe@amd64box:~$ sudo umount p4box
umount: /home/joe/p4box: device is busy
umount: /home/joe/p4box: device is busy
joe@amd64box:~$ 

So, I then proceed to

```
sudo umount /home/joe/p4box -l
``` 

and I successfully (force) unmount the share.  However, once this is done, Firefox takes forever to load.

Is there a graceful way to unmount a samba share?

---

### Post by joekr on 2005-05-26
edit

---

