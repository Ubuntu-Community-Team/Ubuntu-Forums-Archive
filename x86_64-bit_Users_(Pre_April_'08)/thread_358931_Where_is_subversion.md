---
title: "Where is subversion???"
date: 2007-02-11
forum: x86 64-bit Users (Pre April '08)
---

### Post by cmost on 2007-02-11
I tried to install subversion via apt today and it's not there?!?!?  Where has subversion gone?

---

### Post by Kilz on 2007-02-11
> **cmost said:**
> I tried to install subversion via apt today and it's not there?!?!?  Where has subversion gone?

Subversion may not have a menu entry, some applications do not. Try opening a terminal and typing in subversion.

---

### Post by cmost on 2007-02-11
Thanks, for the suggestion, but you've misunderstood me.  I mean to say that Subversion is no longer in the repositories.  I have all the standard Ubuntu repos enabled (including universe and multiverse.)  I tried googling and by all accounts, Subversion WAS part of the standard Ubuntu repos.  I wonder why it's not in there any longer....  I guess I'll have to compile from source, or, find another repository that hosts Subversion.

---

### Post by kuja on 2007-02-12
It's definitely there. Try switching mirrors. If all else fails the manual download would be here: [http://archive.ubuntu.com/ubuntu/pool/main/s/subversion/](http://archive.ubuntu.com/ubuntu/pool/main/s/subversion/)

---

### Post by cmost on 2007-02-12
Thanks Kuja for the info.  This might sound like a newb question but how do I go about switching mirrors?  I've always assumed all Ubuntu repos were all created equal.  I'm using the amd64 version of ubuntu 6.10.  Thanks!

---

### Post by kuja on 2007-02-12
In your /etc/apt/sources.list file, the mirror you're using is [noturl]http://@@.archive[/noturl]......... either change the two letters before the first dot, or remove them (along with the dot) to change the mirror. To edit the file open it with kdesu kate (kubuntu) or gksudo gedit (ubuntu).

---

