---
title: "Software to burn ISO CDs"
date: 2009-05-06
forum: x86 64-bit Users
---

### Post by j0eb0b on 2009-05-06
I need to download some executable software and save it as an ISO file.  Any recommendation of a package to accomplish this?

---

### Post by cariboo on 2009-05-06
Use Brasero it is installed by default, find it in Applications-->Sound & Video

---

### Post by lensman3 on 2009-05-06
From the command line use:

growisofs -speed=6.0 -Z /dev/dvd -dvd-video .

to create a dvd-video.  Note the dot at the end!  This command has to be run form the root of the directory (tree) that you are copying to the dvd. This command builds the iso on the fly.  The man page also has the howto for doing cd's (data and music) as well as doing dvd's (video and data).

Hope this helps.

---

