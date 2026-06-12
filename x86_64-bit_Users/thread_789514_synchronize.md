---
title: "synchronize"
date: 2008-05-10
forum: x86 64-bit Users
---

### Post by hvacr on 2008-05-10
I want to synchronize files over to my 2 nas units, but cannot find any software to do this. I have tried conduit, but can honestly say that it is the worst piece of software I have tried. Does anyone know of any software that works over a network.

---

### Post by tamoneya on 2008-05-10
you could use SSH with rsync as decribed in this post:
[http://ubuntuforums.org/showthread.php?t=535407](http://ubuntuforums.org/showthread.php?t=535407)

---

### Post by hvacr on 2008-05-10
Seems rsync will not let you sync from one nas to another.

---

### Post by tamoneya on 2008-05-10
as long as you have ssh on both of them you should be okay.  Look at post 6 on the above thread.  Just replace the first location with a location in the form of user@remotepc:/myfolder

---

### Post by hvacr on 2008-05-10
I am not backing up to a windows machine though. I am synching to a nas unit from ubuntu, and want to sync between the 2 nas units. I am not being asked for any passwords at all. My nas are not set up to use passwords.

---

### Post by tamoneya on 2008-05-10
the important thing on the post is that it isnt windows.  It is using openSSH to do all of the transfers.

EDIT: If you still dont like this you need to tell us more about your NAS servers.  What are they running.  Are they just repurposed computers with linux running.  If not what is the model number.  What are their capabilities.

---

### Post by hvacr on 2008-05-10
they are d-link dns 323 units

---

### Post by tamoneya on 2008-05-10
okay.  These only have FTP capabilities which is important. You could use a variety of solutions.  I have however never done this myself so I cant tell you which I prefer but I have seen ftpsync ([http://sourceforge.net/projects/ftpsync/](http://sourceforge.net/projects/ftpsync/)) and ftpmirror:```
sudo apt-get install ftpmirror
```

---

### Post by hvacr on 2008-05-10
Thanks. Not sure how ftpmirror works, not much info around about it. I am trying fireftp at this time, seems to work ok, will keep searching for something better.

---

