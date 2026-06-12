---
title: "Tremulous"
date: 2006-07-13
forum: x86 64-bit Users (Pre April '08)
---

### Post by IbeeX on 2006-07-13
Hi

when I install tremulus on ubuntu 64 
with tremulous-1.1.0-installer.x86.run

i get this error message
tremulous
tremulous: error while loading shared libraries: libSDL-1.2.so.0: cannot open shared object file: No such file or directory

and I hawe it installed

locate libSDL-1.2.so.0
/usr/lib/libSDL-1.2.so.0
/usr/lib/libSDL-1.2.so.0.7.2

any idea?:rolleyes:

---

### Post by Kilz on 2006-07-13
> **IbeeX said:**
> Hi

when I install tremulus on ubuntu 64 
with tremulous-1.1.0-installer.x86.run

i get this error message
tremulous
tremulous: error while loading shared libraries: libSDL-1.2.so.0: cannot open shared object file: No such file or directory

and I hawe it installed

locate libSDL-1.2.so.0
/usr/lib/libSDL-1.2.so.0
/usr/lib/libSDL-1.2.so.0.7.2

any idea?:rolleyes:

Welcome to the fun and exciting ](*,) world of making 32 bit versions run on 64bit. :-D 

You are installing a x86 - i386 - 32bit version on a 64bit OS. The libs you are installing are 64bit and if installed in /usr/lib are 64 bit versions. You may need 32bit versions of the lib for 32bit applications. They would go in the /usr/lib32 folder.
When a 32bit program asks for a lib you can [search the contents of a package here]("http://packages.ubuntu.com/") for it. Then get the i386 version of [the deb file.]("http://packages.ubuntu.com/dapper/libs/libsdl1.2debian-all"). 
Now that you have the deb file we need to open it. Install this piece of software
```
sudo apt-get install dpkg-dev
```
It will let your archive program extract the .deb file. Once you have, there is a data.tar.gz file in it, extract that to your desktop. When you do there will be a /usr folder on your desktop. Inside that is a /lib folder. Copy the contents to /usr/lib32 in the file system
cp -r -p /~/Desktop/usr/lib/* /usr/lib32
Repeat this for all the lib's it asks for. Hopefullly it will run after that. :D

---

### Post by rmjb on 2006-07-13
> **Kilz said:**
> When a 32bit program asks for a lib you can [search the contents of a package here]("http://packages.ubuntu.com/") for it. Then get the i386 version of [the deb file.]("http://packages.ubuntu.com/dapper/libs/libsdl1.2debian-all"). 
Now that you have the deb file we need to open it. Install this piece of software
```
sudo apt-get install dpkg-dev
```
It will let your archive program extract the .deb file. Once you have, there is a data.tar.gz file in it, extract that to your desktop. When you do there will be a /usr folder on your desktop. Inside that is a /lib folder. Copy the contents to /usr/lib32 in the file system
cp -r -p /~/Desktop/usr/lib/* /usr/lib32
Repeat this for all the lib's it asks for. Hopefullly it will run after that. :D

Are all these steps the same as doing ```
sudo dpkg -i --force-architecture packagename_i386.deb
``` as metioned in [this]("http://www.ubuntuforums.org/showthread.php?t=191205") thread?

---

### Post by IbeeX on 2006-07-13
Any why it worked even with first metod all I needed was ine more deb package :)
libasound2_1.0.10-2ubuntu4_i386.deb

THX :p

---

### Post by Kilz on 2006-07-13
> **rmjb said:**
> Are all these steps the same as doing ```
sudo dpkg -i --force-architecture packagename_i386.deb
``` as metioned in [this]("http://www.ubuntuforums.org/showthread.php?t=191205") thread?

Unfortuantly no, Ubuntu is not Multiarch yet. Some distro's like SuSE,Fedora,Gentoo and some others are. What that meeans is that Ubuntu thinks its only 64bit. Multiarch is planned, it was even suposed to be in Edgy. But because the developers want to wait on Debian its been pushed back. 
IMHO this is sad because of the amount of eye candy they are adding to the 32bit version, while the 64bit version lacks functionality the hardware is capable of. [Dont think I didnt point this out]("http://www.ubuntuforums.org/showthread.php?t=203182"). Its been pointed out to me that the 64bit community is small. Maybe its because of the missing multiarch? Maybe if multiarch was in place the 64bit user base would be a lot larger [as my poll suggests]("http://www.ubuntuforums.org/showthread.php?t=203794").
Thats why we have to force the package in the first place. Because Ubuntu isnt multiarch. But it is capable of running 32bit applications because 64bit Ubuntu is getting ready to be multiarch.
Because it isnt multiarch yet, it cant install the 32bit libs automaticly like it can 64bit libs. So 64bit users have to copy the needed ones into place. Most of the time its only a few files for the very few 32bit applications that are needed.

---

