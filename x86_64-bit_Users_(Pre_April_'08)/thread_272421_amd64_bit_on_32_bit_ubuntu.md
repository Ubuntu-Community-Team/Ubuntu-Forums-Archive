---
title: "amd64 bit on 32 bit ubuntu"
date: 2006-10-06
forum: x86 64-bit Users (Pre April '08)
---

### Post by IbeeX on 2006-10-06
Hi

is it posible to install ubuntu 686 and then install on it packages for amd64 with force archicecture?

---

### Post by Hallavej on 2006-10-06
No

---

### Post by Kilz on 2006-10-06
> **IbeeX said:**
> Hi

is it posible to install ubuntu 686 and then install on it packages for amd64 with force archicecture?

It is on the other hand possible to do the reverse. Install the amd64 version of Ubuntu then force archicecture any 32bit packages you may need.

---

### Post by IbeeX on 2006-10-07
> **Kilz said:**
> It is on the other hand possible to do the reverse. Install the amd64 version of Ubuntu then force archicecture any 32bit packages you may need.

Can somebady explain quickly whiy it is not posible the other way around?

---

### Post by Kilz on 2006-10-07
> **IbeeX said:**
> Can somebady explain quickly whiy it is not posible the other way around?
Because a 64bit operating system is designed to run both 64bit code and 32bit code. It uses the 64bit kernel and other files to run the 32bit code. All that is needed is a few libraries the 32bit application calls for. 
The 32bit kernel cant run 64bit code, and you cant put a 64bit kernel in because it wont work with the rest of the 32bit operating system. 
That's why its better for 64bit system owners to run the 64bit os. Because they can run both. Therefore there is nothing they cant run.

---

### Post by IbeeX on 2006-10-08
I there anything to solve module dependicies when you are ucing dpkg force arcitehture,
I usaly istall deb than try to run program then gook for file it is mising search it on package page than force new deb it would be nice if a[ptitude can install 32 bit packages? or anything else

---

### Post by Kilz on 2006-10-08
> **IbeeX said:**
> I there anything to solve module dependicies when you are ucing dpkg force arcitehture,
I usaly istall deb than try to run program then gook for file it is mising search it on package page than force new deb it would be nice if a[ptitude can install 32 bit packages? or anything else

Thats called multiarch. Dapper isnt multiarch. There i no way to make it that way. But its lucky we can add libraries on our own. There are a few pre packaged 32bit libraries. They start with ia32 , but most of them are already installed.
You should never force in a library, it may replace a needed 64bit one of the same name. That would make your system unstable. You have to extract the files and copy them into /usr/lib32

---

