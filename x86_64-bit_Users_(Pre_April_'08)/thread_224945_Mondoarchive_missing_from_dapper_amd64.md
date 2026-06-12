---
title: "Mondoarchive missing from dapper amd64"
date: 2006-07-28
forum: x86 64-bit Users (Pre April '08)
---

### Post by Sara Dawn on 2006-07-28
Hi,

i've search the forum and havent found anyone with the same problem, it seems that the mondoarchive package is missing from dapper amd64, and i cannot seem to get the source compiled.
Can anyone confirm it was left out on purpuse or will it ever be back?

Best Regards

Sara Dawn

---

### Post by Kilz on 2006-07-29
> **Sara Dawn said:**
> Hi,

i've search the forum and havent found anyone with the same problem, it seems that the mondoarchive package is missing from dapper amd64, and i cannot seem to get the source compiled.
Can anyone confirm it was left out on purpuse or will it ever be back?

Best Regards

Sara Dawn

Looking at the package site the Mondo rescue package has never been avaiable for the amd64 version. But there is good news, there looks to be a amd64 package for edgy. Unfortunatly it needs a libc version not avaiable for dapper at present. You might want to take a look in the [backports section]("http://www.ubuntuforums.org/forumdisplay.php?f=47") and ask how to go about requesting one of mondo and requirements. 
I did try and download the source for mondo, but the configure file is messed up and wont make a makefile.

---

