---
title: "Today New ATI Driver 8.476"
date: 2008-04-16
forum: x86 64-bit Users (Pre April '08)
---

### Post by bestguy on 2008-04-16
new Ati Driver released . 

Version 8.476

Some Issues are resolved and some new are added. 

Read here for details [https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/catalyst_84_linux.html#194698]("https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/catalyst_84_linux.html#194698")

A nice one is the :

*early look support for Ubuntu 8.04 which is also known as Hardy Heron*

if i figured out what this mean and how to enable it  :-)

Anyway. I installed it on my AMD X2 / Ati 9800 @  1280x1024 and 1680x1050  Dualscreen and it works. Only thing i noticed that is not fixed is that the catalyst center dont start if runing xinerama. 

best regards

---

### Post by Kilz on 2008-04-16
> **bestguy said:**
> new Ati Driver released . 

Version 8.476

Some Issues are resolved and some new are added. 

Read here for details [https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/catalyst_84_linux.html#194698]("https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/catalyst_84_linux.html#194698")

A nice one is the :

*early look support for Ubuntu 8.04 which is also known as Hardy Heron*

if i figured out what this mean and how to enable it  :-)

Anyway. I installed it on my AMD X2 / Ati 9800 @  1280x1024 and 1680x1050  Dualscreen and it works. Only thing i noticed that is not fixed is that the catalyst center dont start if runing xinerama. 

best regards

The Hardy part should mean that it is able to create hardy packages.

---

### Post by bestguy on 2008-04-16
> **Kilz said:**
> The Hardy part should mean that it is able to create hardy packages.

But they wrote "look support" . I understand this like an extension for using some hardy things on gutsy. 

Anyway.. its stable an fast. Even if i wish that i can use compiz with dualscreen Xinerama. Maybe on Hardy this will work or i must switch to a Nvidia Card:)

---

### Post by Kilz on 2008-04-16
[COLOR="Red"][SIZE="5"]WARNING[/SIZE][/COLOR] there is a bug that returns the error

diversion of /usr/X11R6/lib32/libGL.so.1 to /usr/X11R6/lib32/fglrx/libGL.so.1.2.xlibmesa by xorg-driver-fglrx' clashes with `diversion of /usr/X11R6/lib32/libGL.so.1.2 to /usr/X11R6/lib32/fglrx/libGL.so.1.2.xlibmesa by xorg-driver-fglrx'

[A work around is now avilable.]("http://ubuntuforums.org/showthread.php?t=757298")

---

### Post by Angus77 on 2008-04-17
> WARNING there is a bug that returns the error

diversion of /usr/X11R6/lib32/libGL.so.1 to /usr/X11R6/lib32/fglrx/libGL.so.1.2.xlibmesa by xorg-driver-fglrx' clashes with `diversion of /usr/X11R6/lib32/libGL.so.1.2 to /usr/X11R6/lib32/fglrx/libGL.so.1.2.xlibmesa by xorg-driver-fglrx'

I have no idea what this means.  Is this a big enough issue to avoid the update?

---

### Post by Kilz on 2008-04-17
> **Angus77 said:**
> I have no idea what this means.  Is this a big enough issue to avoid the update?

No, but it will stop you from installing it. I have [written a work around]("http://ubuntuforums.org/showthread.php?t=757298") that will let it install.

---

