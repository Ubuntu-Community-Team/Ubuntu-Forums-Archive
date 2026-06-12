---
title: "Hear multiple sounds using Both ESD &amp; ALSA under amd64"
date: 2005-05-24
forum: x86 64-bit Users (Pre April '08)
---

### Post by Leira on 2005-05-24
first of all, u should follow this [HOWTO: Hear multiple sounds using Both ESD & ALSA](http://www.ubuntuforums.org/showthread.php?t=32063&page=1&pp=10), except the first about libesd-alsa0, cause u will find there is no such a libesd-alsa0 package of amd64 arch. i've tried compile a amd64 package by my self from the src package, but it was not workable either. and maybe that is why it is not included in official packages.

but here is a temporary solution to use esd with aoss (absolutely temporary, cause i cannot find where gnome start esd):

1. mv /usr/bin/esd /usr/bin/esd.orig
2. make a script /usr/bin/esd:
```
#!/bin/sh
aoss /usr/bin/esd.orig $*
```
3. chmod a+x /usr/bin/esd

now, it just can work, and the gnome's event sound as well.

---

### Post by Grue on 2005-05-25
[QUOTE=Leira]
2. make a script /usr/bin/esd:
```
#!/bin/sh aoss

/usr/bin/esd.orig $*
```
3. chmod a+x /usr/bin/esd
[/QUOTE]

For this to work, you need to install the alsa-oss package where the aoss script is included.

I hope this will finaly solve my 64 bit sound mixing problems :).

Thanks.

Update:

I installed the alsa-oss package, but GNOME stalls for a long time at boot, and esd is spawned a great number of times. ALSA works, but ESD doesn't sadly. I was hoping for this to be it.

Any insight on this would be great :).

---

### Post by makushimu on 2005-05-25
[QUOTE=Grue]...GNOME stalls for a long time at boot, and esd is spawned a great number of times. ALSA works, but ESD doesn't sadly...[/QUOTE]

same here :(

EDIT: all other desktop apps (Firefox, Nautilus, etc) seem to start up slower then usual too....

---

### Post by Leira on 2005-05-29
Sorry for the Bad Code format after copy & paste, now it is updated:
```

#!/bin/sh
aoss /usr/bin/esd.orig $*

```

yes, i lost some thing:
1. you should install the alsa-oss package
2. u should modify your /etc/esound/esd.conf, it is like this (remember to remove "-d default"):
```

[esd]
auto_spawn=1
spawn_options=-terminate -nobeeps -as 20
spawn_wait_ms=100
# default options are used in spawned and non-spawned mode
default_options=

```
3. "killall esd", to stop esd, and use "aoss esd" to have a test if it works
4. if the 3rd step is OK, then make the /usr/bin/esd script as i said before

---

