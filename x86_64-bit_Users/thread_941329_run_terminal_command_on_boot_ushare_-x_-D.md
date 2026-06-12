---
title: "run terminal command on boot ushare -x -D"
date: 2008-10-08
forum: x86 64-bit Users
---

### Post by taseedorf on 2008-10-08
Probably very easy solution...I looked around and people are posting similar things, but not exactly what I want.

I want the command 

ushare -x -D 

to be run when my computer boots, preferably 20 seconds after boot or so.
I tried creating a script to do this, but I think I wrote it wrong.

It is VERY annoying, because I have to manually type this into a terminal after every reboot

---

### Post by ilrudie on 2008-10-08
I mentioned this in my answer to your other post but the ushare startup script is /etc/init.d/ushare.

In order to make sure it starts you need to do ```
ls -l /etc/rc`who -r | awk '{printf("%s",$2)}'`.d | grep ushare
```  If a result is returned and it starts with a capital letter S ushare should start at boot.  If not you must make a soft/symbolic link to the /etc/init.d/ushare script with ```
sudo ln -s /etc/init.d/ushare /etc/rc2.d/S20ushare
```In order to make this work with the xbox 360 you must change the /etc/init.d/ushare script slightly.  I believe i just change the line ```
DAEMON=/usr/bin/ushare
``` to ```
DAEMON=/usr/bin/ushare -x
``` but I can look when I get home and make sure if that doesn't work for you.  Just let me know.

---

### Post by taseedorf on 2008-10-08
thanks a bunch.  My script I created was no where near as complex as that one, and I had renamed it to ushare in init.d, luckily I made a backup.

If it is in that folder though, shoulder all scripts be run automatically at boot?

---

### Post by ilrudie on 2008-10-08
> **taseedorf said:**
> If it is in that folder though, shoulder all scripts be run automatically at boot?

Only scripts in or linked to in a runlevel (/etc/rc*.d) get run at boot.  That's what the soft link in rc2.d does.

---

