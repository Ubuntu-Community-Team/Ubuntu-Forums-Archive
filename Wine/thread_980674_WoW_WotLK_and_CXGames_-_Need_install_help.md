---
title: "WoW WotLK and CXGames - Need install help"
date: 2008-11-13
forum: Wine
---

### Post by Bahb on 2008-11-13
I am running Crossover Games, and just like Wine Users I am unable to install due to permissions errors. However, Unlike Wine Users, I a do not have a vast community of people to go to for help, CX forums are pretty much dead, I guess they are all here or something. Any help I could get would be greatly appreciated, especially if I can actually get it installed.

---

### Post by tcoffeep on 2008-11-13
[http://ubuntuforums.org/showthread.php?t=980629](http://ubuntuforums.org/showthread.php?t=980629)

the answer here worked for me.

---

### Post by Gcentrex on 2008-11-14
After doing that the accept buttun will not work for cxgames still but I have a way to get it working but it will require two native files from IE6sp1

mshtml.dll
wininet.dll

Go into the system32 folder of your wow bottle and rename the ones that are in that folder to something else you may need them again later, now copy in those two files now open up crossover games and do click configure on the bottle and pick winecfg change wininet.dll to native,builtin, mshtml.dll is already set correctly for this to work, now launch the installer and it will alow you to press the accept button. When I have have time later I will find a better way to do this so it works with all bottles by using some files from wine 1.1.8.

I would change those files back after it is installed so html rendering works again.

---

