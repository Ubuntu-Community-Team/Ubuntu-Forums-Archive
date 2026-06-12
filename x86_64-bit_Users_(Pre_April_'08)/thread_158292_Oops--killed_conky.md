---
title: "Oops--killed conky"
date: 2006-04-10
forum: x86 64-bit Users (Pre April '08)
---

### Post by dpny on 2006-04-10
I was happily running the version of conky in the Ubuntu repositories, but decided to try out the latest (1.4.1). I did an apt-get remove to get rid of the old version, downloaded the source, put it in a folder in /opt, compiled and installed. Unfortunately, the new version is having problems drawing the window in Ubuntu 5.10. I thought I'd remove the new version and apt-get the older version. I deleted the directory in /opt and installed the old version, but the new version is still in there. I thought maybe it was in a cache somewhere, but a reboot didn't change things.

Can anyone tell me where the version I installed is hiding, and how to get rid of it?

---

### Post by dpny on 2006-04-11
Figured it out: /usr/bin. Now there's just a link or something I have to fix to tell it where to look.

---

