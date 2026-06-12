---
title: "Paradox 9 BDE  network share"
date: 2008-01-11
forum: Wine
---

### Post by markbann on 2008-01-11
I have installed Corel's paradox 9 and BDE (borland database engine 5.2 and 5.11).
I am having trouble with the BDE and I'm pretty sure it has to do with the way I have set up the network share from a Samba server.  All other clients on this systems on Win XP.
I mount it in fstab with:
[INDENT//LINUXHOST/data  /media/data cifs    credentials=/root/.smbcredentials,iocharset=utf8,gid=1001,uid=1000,rw,file_mode=0777,dir_mode=0777,noperm 0 0][/INDENT]

There is a directory on this share that contains the locking files the BDE uses to manager file sharing.  The BDE must have full access to it at all times.  If I do not first open examine the properties of the network lock file before I open paradox, Paradox will not run because the BDE will not have access to the network.
After I get paradox running I can create and manager local database tables but cannot access network tables (I can see them in directory listings and open Paradox scripts and other paradox UI files from the network-as long as they do not open network tables themselves).

Paradox requires the BDE to have access to the network lock file and it appears that it cannot access it with full permissions.  How can I remedy this?

---

### Post by e_james on 2008-02-21
I discovered this thread while looking for Paradox solutions for myself. If you have solved your problem, it is unlikely that I can contribute anything new. If you still have a problem, we might be able to work together towards solutions for both of us. I have used Paradox 7 since Windows 95 and also have Paradox 10 which I don't use much because the IDE is less familiar.

The problem I am trying to solve is running Paradox 7 using wine in ubuntu 7.04. I have a lot of customised Object Pal code which I do not want to redevelop in a new environment.

---

