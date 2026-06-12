---
title: "Ubuntu Ibex (8.10 x64) Opera + Java Problems"
date: 2008-11-06
forum: x86 64-bit Users
---

### Post by bapfreak on 2008-11-06
I am using the x64 version of Ubuntu and am having problems with Opera + Java. Opera is much more stable and much faster and therefore I prefer it to Firefox. The problem I am having is Java applets are not workings. They appear to be trying to load, but end up blank in the end. I have followed the directions on the Opera website:

locate libjava.so
Then point Opera to that file in Content

I have tried using OpenJDK, Sun Java, and have tried 32 and 64 bit versions of both. I have changed the jre in both Opera and in Ubuntu ( using java alternatives ). Nothing seems to week. I have installed the Icedtea plugin, but Opera uses Java directly.

Any help would be appreciated, except for suggestions of using Firefox or 32 bit Ubuntu. The 64 bit version is a huge performance increase for me ( Due to Phenom 9950 and over the 3Gb limit of ram, the 32 bit version just holds back my computer too much ). I have also grown tired of Firefox, and do not like Konqueror either.

---

### Post by gila_monster on 2008-11-07
It's not just you. I am having that problem as well. If I come up with a solution, I'll try to remember to post it here.

---

### Post by gila_monster on 2008-11-08
Bapfreak, this is apparently a known issue with 64-bit Opera versions since 9.50. At least as far as I can tell. So there isn't anything we can do about it yet.

---

### Post by vitdoc on 2008-11-27
I just loaded Ubunto 8.10 64bit for the first time.  I loaded the 32 bit version of Opera and used getlibs (search on the forums for this) to get Opera to work in the 64bit architecture.  Surprisingly it works and so does javascript so far.  It shows java available.  You need to force the 32 bit opera using dpkg -i --force-all opera*.deb.

---

### Post by Sef on 2008-12-11
> Bapfreak, this is apparently a known issue with 64-bit Opera versions since 9.50. At least as far as I can tell. So there isn't anything we can do about it yet.

I have updated to Opera 10 alpha.  The bug is still there.

---

### Post by josedb on 2008-12-12
Iam having problems to, when trying to upload photos in facebook.

---

### Post by gila_monster on 2008-12-13
> **Sef said:**
> I have updated to Opera 10 alpha.  The bug is still there.

Unfortunate. I tried to send in a bug report (although I know they already have one) in the hopes that it might prompt them to look into this, but the website gave an error when I submitted it.

I am really, really hoping they get this fixed.

---

