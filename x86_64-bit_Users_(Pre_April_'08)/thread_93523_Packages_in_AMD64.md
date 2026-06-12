---
title: "Packages in AMD64"
date: 2005-11-22
forum: x86 64-bit Users (Pre April '08)
---

### Post by Vermyndax on 2005-11-22
I was just curious, since I'm a relative newcomer to the way Ubuntu is managed... (but not a newcomer to Linux in general).
 
I'm waiting for updates of Evolution in Breezy and MythTV fixes - both for AMD64.  MythTV won't install because of dependency issues (packages just aren't built that are required) and Evolution is... well... buggy at best and has had several updates.
 
Why aren't the AMD64 packages getting updated?  I see that the i386 versions are being updated, but it's like no one is even touching AMD64.  There have been maybe 10 package updates since Breezy was released in AMD64.  Do we have to wait until Dapper gets released for these programs to work?
 
Not to mention, many items just plain segfault in the AMD64 versions (yes, I filed bugs in Malone, but those are mostly just sitting there too).
 
What's the problem?

---

### Post by garciadc on 2005-11-22
IMO, lack of support is due to lack of people wokring on updating amd64 computers as well as people not reporting bugs; the majority of people here have ix86 processors which I would assume gives them preferencial treatment due to higher demand.  I don't think it's an evil plot against adm64 users.  It's just like Windows64 support, only no one is getting paid for it.  I too have a amd64 and have realised that the planet is slow on keeping up.  I have been using evolution, and haven't found any problems.  I guess you could ask people to report their bugs, but I would like to know what I, a computer programming retard, can do to help expedite development.  Anyone?

---

### Post by BathroomNinja on 2005-11-22
I feel the same way.  I'm so frustrated with the number of broken packages, that I'm wiping the system tonight and installing i386 version.  It seems to run a lot smoother.

---

### Post by RAOF on 2005-11-22
I haven't had many problems with Breezy64.  What do you have that's segfaulting?  I, too, haven't had any problems with evolution, but I don't use it very hard, and I know that there are problems out there (particularly with exchange support).

You can, if you want to, build the AMD64 packages yourself.  In fact, given that I know how do to this, I might look into submitting a patch or something so that the repository gets working packages :)  In the meantime, [this thread has the information on how to build the mythtv packages]("http://www.ubuntuforums.org/showthread.php?t=74660").

---

### Post by Padraic on 2005-11-22
RAOF is there a HOWTO on building a package along with all it's dependencies, *.desktop files for gnome and submitting to the official repository or multiverse?  I might be able to help as well (on the weekends anyway).

Thanks!

Padraic

---

### Post by Vermyndax on 2005-11-22
Packages that segfault in AMD64 that I know for sure (and I filed bugs against in Malone, only to have them sit there): abuse and slune.
 
The problems I have with Evolution are mainly centered around the Exchange support, but it's not the Exchange server's fault.  Evolution frequently forgets the password used on the account and/or the folders set up in the account for Drafts and Sent Items.  I think these are both fixed in subsequent releases of evolution, but there have been no updates in any Ubuntu repository.
 
As for Mythtv, it's just plain broke on AMD64.  myth-frontend and myth-backend aren't up to date (they are still version 17.1 or something, I can't recall) so MythTV as a whole refuses to install on AMD64.  There have been bugs filed on this as well... again, with no action.
 
Frustrating!

---

### Post by RAOF on 2005-11-22
[QUOTE=Vermyndax]...I think these are both fixed in subsequent releases of evolution, but there have been no updates in any Ubuntu repository.
 
As for Mythtv, it's just plain broke on AMD64.  myth-frontend and myth-backend aren't up to date (they are still version 17.1 or something, I can't recall) so MythTV as a whole refuses to install on AMD64.  There have been bugs filed on this as well... again, with no action.
 
Frustrating![/QUOTE]
Yeah, I know.  I filed that mythtv malone bug :)

About Evolution, has the i386 version got the update(s)?  You could download the source packages and build them (apt-get source -b evolution, for example).  If the i386 version doesn't have them, though, it's likely that they're not going to be packaged for breezy.  At least in the official repos.  You might get them added to the backports, though.

---

### Post by Vermyndax on 2005-11-22
Well, that's disheartening.  I was rather hoping I could get away from doing the compiling/repackaging thing after a long, long stint with Gentoo :)

---

### Post by RAOF on 2005-11-23
Almost all of the time you can.  Breezy64 is just slightly less supported than the i386 version, and only for things in Universe/Multiverse, which are sort of unsupported anyway.

At least the compiling/repackaging thing is easy.

---

### Post by Vermyndax on 2005-11-25
RAOF... have any links that can give us some HOWTO on the repackaging?  I know about how to compile... that far I'm good, it's the Ubuntu/Debian Packaging I need help with.
 
Also, what's the bug # for that mythtv bug report?

---

