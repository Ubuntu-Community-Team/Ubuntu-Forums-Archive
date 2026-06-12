---
title: "Newbie problem with WINE..."
date: 2008-03-06
forum: Wine
---

### Post by Mr.Thunderbird on 2008-03-06
Hi guys, I recently installed WINE, (to play CS), the install went good without problems... but when i try to run "SteamInstall" trough wine, I get this :

```
Warning: the specified Windows directory L"c:\\windows" is not accessible.
Warning: the specified System directory L"c:\\windows\\system32" is not accessible.
Warning: the specified Windows directory L"c:\\windows" is not accessible.
Warning: the specified System directory L"c:\\windows\\system32" is not accessible.
wine: could not load L"c:\\windows\\system32\\tool.exe": Module not found

```

Any idea why I'm getting this? :KS:KS

---

### Post by chewit on 2008-03-06
you might want adds these folders into your C:\ drive. i think it is unable to find them

---

### Post by tuxcanfly on 2008-03-06
hey I think you have installed CS on some removable media or hard disk but with wrong permissions ....Check if the place where you installed CS has read and write permission.
Also try to install all your wine applications to the default ( ~/.wine/drive_c) location as it minimizes problems.

---

### Post by Mr.Thunderbird on 2008-03-06
> **chewit said:**
> you might want adds these folders into your C:\ drive. i think it is unable to find them

They ARE there... :confused:



>  	
Re: Newbie problem with WINE...
hey I think you have installed CS on some removable media or hard disk but with wrong permissions ....Check if the place where you installed CS has read and write permission.
Also try to install all your wine applications to the default ( ~/.wine/drive_c) location as it minimizes problems.

I can't install Steam, so how could I install CS? :KS

---

### Post by Rae III on 2008-03-06
you might try adding sudo (root permissions) to the front of whatever command it is that you're running. It seems to fix a lot of my problems, and I don't know whether or not it will work for you, but it's worth a shot :)

---

### Post by Mr.Thunderbird on 2008-03-07
Ah well, I found a script on a German web site, which installed STEAM for me.. I donwloaded CS, launced it (CZ).. but it FLICKERS a LLOT! and because of that it begins to lagg.. any ideas guys? :)

---

### Post by Mr.Thunderbird on 2008-03-08
Never mind guys, everything works now! :) :)

Long live Ubuntu! :D

---

