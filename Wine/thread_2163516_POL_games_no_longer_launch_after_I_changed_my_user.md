---
title: "POL games no longer launch after I changed my username."
date: 2013-07-18
forum: Wine
---

### Post by Rytron on 2013-07-18
Hi.

After backing up my stuff, I formated my HDD and changed my username and then moved my stuff including the old PlayOnLinux dir "~/.PlayOnLinux" back onto the HDD. Now nothing works in POL. Wine works fine on other games + software. I can goto "/.PlayOnLinux/wineprefix" and launch the games fine with regular Wine. It must be pointing to my older username path (for arguments sake lets call it **bartholomew** and I changed my username to **bart**). Is there a way to sort this out without having to re-install everything as that would be utter tedium.

---

### Post by Toz on 2013-07-18
Have a look in ~/.PlayOnLinux/shortcuts. All your program shortcuts should be there. You'll need to edit each file and change the username from the old to the new.

---

### Post by Rytron on 2013-07-18
Toz, you are a star. POL works fine again. Cheers. ;-)

---

