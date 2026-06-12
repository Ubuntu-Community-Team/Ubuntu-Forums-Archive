---
title: "Samba Problems"
date: 2006-01-01
forum: x86 64-bit Users (Pre April '08)
---

### Post by razor7 on 2006-01-01
Hello I have Ubuntu 64 over VMware in windows XP.

The network is working, the pings are ok and even i have configured my ubuntu box with VHCS virtualhosting software and it works ok...but samba does not.

It shows me the windows network...the workgroup (MGS) but when i try to access the workgroup it tells me that "Can not show folder contents. Sorry I can not show the contents of Windows Network: mgs"

Any idea?


thanks

---

### Post by rplantz on 2006-01-01
I have three machines networked: Ubuntu, Windows 2000, Mac OSX. I was having lots of trouble with Samba, specifically from the Mac. I only tried to connect with the Windows machine a couple of times, and didn't try very hard.

I then learned that the version of Samba installed with Breezy, 3.0.14, does not work very well with at least the Mac. There is a later version, 3.0.20, in the Dapper development repositories that works fine for me, both with the Mac and Windows.

I desribe what I did to get it here:
[http://ubuntuforums.org/showthread.php?t=105462&referrerid=32044](http://ubuntuforums.org/showthread.php?t=105462&referrerid=32044)

Note that you have to be careful about mixing in packages from Dapper. I got carried away on another issue and ended up reinstalling my entire system. Even managed to trash my home directory along the way! I did something really stupid, but it sure showed me the value of making backups. (BTW, I've been in this business for forty years; even we experienced people make stupid mistakes.)

---

### Post by razor7 on 2006-01-04
Thanks, i'll test it.

---

