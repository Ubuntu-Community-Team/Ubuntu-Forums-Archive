---
title: "It`s like i`m not the admin user"
date: 2007-10-20
forum: x86 64-bit Users (Pre April '08)
---

### Post by lnenad on 2007-10-20
Sudo doesn`t work, when i try to install a new package or do a sudo command for the first time i get the following error (for example when i tried to change the sources.list file i got this error)

[IMG]http://www.mycity.co.yu/imgs/57167_91759730_greska.jpg[/IMG]

It`s like i`m not the admin user, and under the system>administrator menu i only have 5 menu items (:)) what did i do wrong and how do i fix this :confused:

---

### Post by DRAGONPOWER on 2007-10-20
go to system> administration>users and groups

click on root user, then properties, u have to setup a root password. close windows

then go to system> administration> login, click on security tab and enable "Allow local system administrator login".

reboot

now u can login as root user with your password u setup :KS

---

### Post by lnenad on 2007-10-20
I don`t have users and groups under my admin menu

---

### Post by DRAGONPOWER on 2007-10-20
find it then

it should be there ... anyways

---

### Post by lnenad on 2007-10-20
Well i`ve tried to edit the menu and i tick the Users and Groups menu to appear under the admin menu but when my mouse leaves the box it unticks itself (!!!) ???

I`ve tried to access the menu with this gksu users-admin but it gives me the same error like with the sources.list editing ?

---

### Post by DRAGONPOWER on 2007-10-20
no bro, read carefully.

on your desktop go to the system menu, ok? u select administration > users and groups, ok so far? 

then do like i said b4.

dont use the console ...

---

### Post by lnenad on 2007-10-20
I guess you assumed i'm a retard :) i know what you meant

I wiped the system and installed it again and now it works...

---

### Post by DMills on 2007-10-20
FWIW, by default only the first user created has permission to sudo to root, got me as well. 

This can be changed (by that user) but initially only by that user...

Regards, Dan.

---

### Post by aysiu on 2007-10-20
In the future, if *sudo* gets messed up, you don't need to reinstall. Follow this guide instead:
[http://www.psychocats.net/ubuntu/sudo](http://www.psychocats.net/ubuntu/sudo)

---

