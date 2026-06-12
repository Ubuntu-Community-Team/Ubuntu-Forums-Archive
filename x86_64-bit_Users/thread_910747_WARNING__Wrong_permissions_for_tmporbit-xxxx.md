---
title: "WARNING **: Wrong permissions for /tmp/orbit-xxxx"
date: 2008-09-04
forum: x86 64-bit Users
---

### Post by sumanc on 2008-09-04
Whenever I start any application that needs to access the /tmp I get the following warning:

** (gvim:10645): WARNING **: Wrong permissions for /tmp/orbit-xxxx

** (gedit:10659): WARNING **: Wrong permissions for /tmp/orbit-xxxx

Even chmod -R 777 /tmp/orbit-xxxx does not work. Permissions are shown below.

drwxrwxrwt   25 root root 12288 2008-09-05 06:32 tmp
drwxrwxrwx  2 xxxx xxxx     4096 2008-09-03 00:33 orbit-xxxx

Any suggestion to get rid of this warning? It seems /tmp has become unusable for this particular user. This warning is not displayed if I use sudo.

---

