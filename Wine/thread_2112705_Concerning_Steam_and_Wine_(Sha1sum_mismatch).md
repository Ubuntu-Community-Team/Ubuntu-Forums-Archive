---
title: "Concerning Steam and Wine (Sha1sum mismatch)"
date: 2013-02-05
forum: Wine
---

### Post by Crawdiddy on 2013-02-05
Beforehand, I must apologize for any and all stupid questions. I am new to Ubuntu, and pretty much everything about it.

Anyways, I'm attempting to download Steam in order to run Skyrim. I have the latest version of Ubuntu, Wine, and Winetricks. I have followed many videos in order to install said software, yet I get the Sha1sum Mismatch error. I researched how to fix it, and got "Install latest Wine and Winetricks". I already knew I had the latest, but I installed it again and still got the same message. I'm somewhat confused... Can anyone please help me to resolve this issue?

---

### Post by DarthTibault on 2013-02-06
The winetricks in the repo is a bit outdated I'm afraid. You'll have to either wait, file a bugreport, or just download [the new version manually]("http://winetricks.googlecode.com/svn/trunk/src/winetricks").

So if you want Steam you could just do:
```
wget http://winetricks.googlecode.com/svn/trunk/src/winetricks
chmod u+x winetricks
./winetricks steam
```

---

