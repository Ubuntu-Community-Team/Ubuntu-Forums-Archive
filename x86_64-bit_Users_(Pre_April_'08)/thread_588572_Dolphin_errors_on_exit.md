---
title: "Dolphin errors on exit"
date: 2007-10-23
forum: x86 64-bit Users (Pre April '08)
---

### Post by revchris on 2007-10-23
Every time I close Dolphin I get an error: 

"Unable to save bookmarks in /home/mattmiller/.kde/share/apps/d3lphin/bookmarks.xml. 
Reported error was: Permission denied.  This error message will only be shown once. The cause of the error needs to be fixed as quickly as possible, which is most likely a full hard drive."

The drive is far from full.  I checked the permissions on bookmarks.xml and it is owned by root.  Shouldn't it be owned by the user?

Thanks

---

### Post by sparky64 on 2007-10-23
Having the same problem.
Tried changing ownership but still get the same fault.

---

### Post by mini_g on 2007-10-24
I am also having the same issue under the i386 7.10 architecture.

I found that kdesudo version kdesudo_1.1-0ubuntu3 is buggy via this [_bug report_]("https://bugs.launchpad.net/ubuntu/+source/kdesudo/+bug/155032"), so whenever "Open as Root" is selected, it transfers both group and user ownership over to root.  When attempting to edit the ownership back with that link, it rewrites the ownership back to root.  Also arriving via "sudo dolphin" within terminal does the same thing.

There is a fixed i386 version (kdesudo_1.1-0ubuntu5) of kdesudo that is offered and is currently being tested. It is accepted into the gutsy-proposed repo. I am unsure as to if the x86_64 version is patched in the repo yet.
[CENTER]_______[/CENTER]

Whatever the case, to remove the error run in terminal:
```
sudo chown *your user* ~/.kde/share/apps/d3lphin/bookmarks.xml
```
```
sudo chgrp *your group* ~/.kde/share/apps/d3lphin/bookmarks.xml
```
This shall give the user and group ownership back to you.
[CENTER]_______[/CENTER]

*Note*: You may have a backup file in there also; this bug affects that file also.  In that case, just run "*~/.kde/share/apps/d3lphin/bookmarks.xml ~/.kde/share/apps/d3lphin/bookmarks.xml.bak*" for each command.

Good luck!

---

### Post by revchris on 2007-10-24
I changed the ownership and group but when I logout then back in, they are back to root.  Its just a pain to have to change them everytime.

thanks

---

### Post by mini_g on 2007-10-24
> **revchris said:**
> I changed the ownership and group but when I logout then back in, they are back to root.  Its just a pain to have to change them everytime.

thanks

:(

I hope that they get the fix out soon into the main repo's.

---

### Post by tmray on 2007-10-25
That worked for me. Thanks!

---

### Post by sveden on 2007-10-27
Worked for me as well. Thanks.

---

### Post by gamerchick02 on 2007-11-23
Thanks.  This worked for me.

Amy

---

### Post by gagnon88 on 2008-07-18
Works fine! Thanks!

---

