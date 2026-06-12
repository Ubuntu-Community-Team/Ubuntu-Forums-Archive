---
title: "Totem plays movies on all accounts simultaneously"
date: 2008-09-11
forum: x86 64-bit Users
---

### Post by bford16 on 2008-09-11
If I have two users logged in, and I insert a DVD, Totem opens on both accounts.  The movie starts to play, then stops with a "source may be encrypted error." Killing all Totems, ejecting the disk, reinserting it, manually opening Totem and playing the movie, is what it takes to get it working again.

What can I do so that when I insert a movie, it automatically plays on the active account only (mine).  I have the DVD-ROM drive mapped in /etc/fstab like this:

```
UID=335cc203-0874-4634-bb59-c89184b7377c none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 users,noauto,exec,utf8 0       0
```

---

### Post by Kilz on 2008-09-11
> **bford16 said:**
> If I have two users logged in, and I insert a DVD, Totem opens on both accounts.  The movie starts to play, then stops with a "source may be encrypted error." Killing all Totems, ejecting the disk, reinserting it, manually opening Totem and playing the movie, is what it takes to get it working again.

What can I do so that when I insert a movie, it automatically plays on the active account only (mine).  I have the DVD-ROM drive mapped in /etc/fstab like this:

```
UID=335cc203-0874-4634-bb59-c89184b7377c none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 users,noauto,exec,utf8 0       0
```

You could try this, remove it from the fstab and manually mount the dvd in the terminal. But I have to believe your problem isnt common. Not many people have 2 people logged in at once.

---

### Post by bford16 on 2008-09-12
> **Kilz said:**
> You could try this, remove it from the fstab and manually mount the dvd in the terminal. But I have to believe your problem isnt common. Not many people have 2 people logged in at once.

I almost always have myself and one other user logged in. Since we share the computer, only one of us is actually **using** the computer at a given time.

This behavior appeared some time after I installed Ubuntu 8.04. At first videos played just fine when I inserted the disk. I have no idea what may have changed, though.

---

### Post by Kilz on 2008-09-12
> **bford16 said:**
> I almost always have myself and one other user logged in. Since we share the computer, only one of us is actually **using** the computer at a given time.

This behavior appeared some time after I installed Ubuntu 8.04. At first videos played just fine when I inserted the disk. I have no idea what may have changed, though.

This sounds like it needs a bug report filed on launchpad.

---

### Post by bford16 on 2008-09-13
> **Kilz said:**
> This sounds like it needs a bug report filed on launchpad.

Agreed, but where do I file the bug?  Under totem, or under gnome-volume-manager?  Or somewhere else?

Filed bug under totem-xine: <https://bugs.launchpad.net/ubuntu/+source/totem/+bug/269824>

---

