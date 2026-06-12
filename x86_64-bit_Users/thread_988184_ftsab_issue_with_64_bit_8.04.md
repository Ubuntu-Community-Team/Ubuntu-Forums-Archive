---
title: "ftsab issue with 64 bit 8.04"
date: 2008-11-20
forum: x86 64-bit Users
---

### Post by lunafreestate on 2008-11-20
My automounted fat32 partion stops automouting.  I have tryed a couple of things like changing fstab entry and I can't seem to get it to stay consistent.  I dual boot vista.  Any help?

here is a copy of my fstab current entry
/dev/sda6	/media/storage	vfat utf8,uid=1000,gid=100,umask=022 0 0

I created the mount point directory storage.  The results of ls -l
drwxr-xr-x 10 thomas users 16384 1969-12-31 19:00 storage

does that date code look funny to you too?

this is just a little out of my range to figure out since mount -a still gets my partion mounted.  Is 64 bit ubuntu just this buggy?

---

### Post by lunafreestate on 2008-11-20
beginner mistake.   my gnome config was wrong after changing a few things.  I put different backgrounds on the two desktops and changed /apps/nautilus/preferences/show_desktop to no and it made me think that the partion wasn't mounting.  I lost my two different desktops backgrounds though.  any one know how to keep the different backgrounds and still have icons drawn by nautilus?

---

### Post by drs305 on 2008-11-20
> **lunafreestate said:**
> I lost my two different desktops backgrounds though.  any one know how to keep the different backgrounds and still have icons drawn by nautilus?

You can install an app called wallpapoz. [http://wallpapoz.akbarhome.com/index.html]("http://wallpapoz.akbarhome.com/index.html")

You can get the .deb file at [http://www.getdeb.net/]("http://www.getdeb.net/")   You register but there is no cost. The hardy version works fine in Intrepid.

You can include in startup sessions (Syst, Prefs, Sessions, Startup Programs: daemon_wallpapoz )

---

### Post by cariboo on 2008-11-20
Your date problem makes me think that you may have a bad CMOS battery. which may have something to do with your vfat drive not mounting. Set the correct date in the BIOS to see if that corrects the problem.

Jim

---

