---
title: "gnome applications crashing under root user."
date: 2008-04-17
forum: x86 64-bit Users (Pre April '08)
---

### Post by gtaskeraus on 2008-04-17
When I run nautilus under gutsy as normal user it goes fine but as root user it core dumps on start up.  i.e. sudo nautilus

I am also having the same problem with synaptic and other gnome based applications.

Has this been seen before and if so what is the resolution to this problem.

I've already tried killing all my gnome settings.

---

### Post by daengbo on 2008-04-17
Please post the error

---

### Post by ajgreeny on 2008-04-17
It may not make a difference but try ```
gksudo nautilus
```  You should always use **gksudo** not just **sudo** for gnome gui applications and **kdesu** for KDE applications.

---

### Post by gtaskeraus on 2008-04-23
From the command line as root user I do the following.

root@mycomputer:/home/myuser# nautilus

In response I get the following message.

(nautilus:28567): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
Initializing gnome-mount extension
Segmentation fault (core dumped)

I only did this because when I right clicked on a folder in Nautilus and selected "Open as Administrator" script nothing happened as previously.

I then went to the command line to see if it would give me any more information.  Interestingly none of gnome the programs that are to run as su will work.

Synaptic also dies.

Oh, and gksudo nautilus does nothing either.

---

