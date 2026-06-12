---
title: "Firefox no longer saves bookmarks"
date: 2009-06-03
forum: x86 64-bit Users
---

### Post by acidblue on 2009-06-03
Using Unbuntu 8.10 with Firefox 3.0.10.
Just like the title says, when i bookmark a web page it shows in the bookmark tab, but when i restart firefox it disappears.
This also happens when i try to make a folder it just disappears after
a restart.
There has to be a fix for this, i can't use a web browser that dosn't save bookmarks.

---

### Post by sanderj on 2009-06-04
Are you running off a live-CD?

How much disk space is free? Check with "df -BM".

---

### Post by acidblue on 2009-06-04
I've should have been a bit more specific.
No i'm not using the live cd it's all installed to HD.
I have lots of free space on my drive.

Iv'e installed Opera for now and it works fine, but i prefer Firefox.
Just seems strange that all of a sudden it stopped saving bookmarks.

I've upgraded to 9.04 but still have the same problem with Firefox.

---

### Post by sanderj on 2009-06-04
SO if you create a folder in your home directory on harddisk, it is gone after reboot?

---

### Post by Xamiga on 2009-06-04
File permissions on your home/.mozilla directory is not correct.  In that case only the defaults are read upon program startup.

---

### Post by acidblue on 2009-06-04
> **Xamiga said:**
> File permissions on your home/.mozilla directory is not correct.  In that case only the defaults are read upon program startup.

Ok how do i change permissions ?
I ask becuase right now it won't let me, even when i run Nautilus as root
it won't let me change file access

---

