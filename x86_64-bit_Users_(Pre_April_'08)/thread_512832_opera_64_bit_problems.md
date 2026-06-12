---
title: "opera 64 bit problems"
date: 2007-07-29
forum: x86 64-bit Users (Pre April '08)
---

### Post by kyrhash on 2007-07-29
Ok so i tried to install opera on my 64 bit fiesty install.  I downloaded it to my desktop and did:

kyle@kyle-desktop:~/Desktop$ sudo dpkg --force-architecture -i opera-static_9.20-20070409.1-qt_en_i386.deb

Then it came up with this:

dpkg - warning, overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
(Reading database ... 123569 files and directories currently installed.)
Preparing to replace opera-static 9.20-20070409.1 (using opera-static_9.20-20070409.1-qt_en_i386.deb) ...
Unpacking replacement opera-static ...
Setting up opera-static (9.20-20070409.1) ...
File '/usr/share/applications/Swiftfox.desktop' contains invalid MIME type '' that is missing a slash

I have no idea why it doesnt like my swift fox install or is that even the problem.  Help please.

---

### Post by Kilz on 2007-07-29
> **kyrhash said:**
> Ok so i tried to install opera on my 64 bit fiesty install.  I downloaded it to my desktop and did:

kyle@kyle-desktop:~/Desktop$ sudo dpkg --force-architecture -i opera-static_9.20-20070409.1-qt_en_i386.deb

Then it came up with this:

dpkg - warning, overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
(Reading database ... 123569 files and directories currently installed.)
Preparing to replace opera-static 9.20-20070409.1 (using opera-static_9.20-20070409.1-qt_en_i386.deb) ...
Unpacking replacement opera-static ...
Setting up opera-static (9.20-20070409.1) ...
File '/usr/share/applications/Swiftfox.desktop' contains invalid MIME type '' that is missing a slash

I have no idea why it doesnt like my swift fox install or is that even the problem.  Help please.

Removing Swiftfox should do the trick. If you like optimized versions of Firefox, try swiftweasel, it may work better for you.

---

### Post by kyrhash on 2007-07-29
Never mind got it working.

used:

sudo nano -w /usr/share/applications/Swiftfox.desktop

then deleted the stray ; after the MIME line.

This is one of the reasons never to use Automatix on any ubuntu install, especially a 64 bit one.

---

### Post by kyrhash on 2007-07-29
Kilz i have a core 2 duo processor could you point me to the correct 64 bit version of swiftfox for my processor.

---

### Post by Kilz on 2007-07-30
> **kyrhash said:**
> Kilz i have a core 2 duo processor could you point me to the correct 64 bit version of swiftfox for my processor.

I would use the nocana build of [Swiftweasel]("http://swiftweasel.sourceforge.net/") for that processor.

---

