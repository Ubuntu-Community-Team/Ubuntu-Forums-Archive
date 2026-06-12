---
title: "Uninstall steam"
date: 2007-05-14
forum: Wine
---

### Post by paparappa on 2007-05-14
Well, i installed steam but then a after a few seconds i decided to remove it (at this time i used 6.10). Well It didnt wor kto uninstall it with the Steam uninstaller through wine so i just deleted the files (very stupid indeed). Well when i want to install the game again it doesent work since, well , the installer thinks the software still exists.

Now when i upgraded to 7.04 i noticed a tool called Wine Uninstaller, when i opened this software Steam stood there on the list well it doesent work to uninstall because the files for this capacity doesen't exist.

So I wonder if it's someone out here that has the steam files so i just can put them in my folder and then just uninstall it and then install it again with the original steam installer. Or is there an other way to do it?

---

### Post by bigud on 2007-05-14
god evening ....

if u have SteamInstall.msi ....open terminal and type:

cd ~/Desktop

# wine msiexec /i SteamInstall.msi

       (Uninstall is like windows ... remove .. next ... next ... ok)


but if u don't have the arquive .. download SteamInstall.msi at ... [www.steampowered.com](www.steampowered.com)


and do the same thing 

cd ~/Desktop

# wine msiexec /i SteamInstall.msi

       (Uninstall is like windows ... remove .. next ... next ... ok)




just it ...


Ricardo de Oliveira (BIguD)
Think Linux !

---

### Post by bigud on 2007-05-14
if u want an easier kind of uninstall ... run in terminal:


# wine uninstaller

than choose aplication and remove !!


Ricardo de Oliveira (BIguD)
Think Linux !

---

### Post by paparappa on 2007-05-15
thank you, the second suggestion didn't work however the first did! I now have steam working thorugh wine!

---

### Post by boast on 2007-10-26
it does not work for me. I even  delete the steam folder, but running the uninstaller makes the steam folder and the .exe appear again.

---

### Post by karth on 2007-10-26
For the record, you could also have recreated another wine environment dedicated to Steam using ```
wineprefixcreate /path/to/dir
``` and then installed Steam in it with ```
env WINEPREFIX="/path/to/dir" wine Setup.exe
```

That way you would have been able to install Steam in a safe place apart from the polluted registry that confused your primary environment, all of that using the same wine binaries. Just remember that anything that has something to do to your duplicate environment has to be launched that way ```
env WINEPREFIX="/path/to/dir" wine Your.exe
env WINEPREFIX="/path/to/dir" winecfg (to configure your second environment)
env WINEPREFIX="/path/to/dir" wine regedit.exe
etc...
```

Using launchers is a good thing ;)

---

### Post by sinisterzerox on 2008-08-05
thnx for the trubel the first way worked fine i am very thank full for this help 2 ;)

---

### Post by killchaos6669 on 2008-08-24
> **bigud said:**
> if u want an easier kind of uninstall ... run in terminal:


# wine uninstaller

than choose aplication and remove !!


Ricardo de Oliveira (BIguD)
Think Linux !


This worked perfectly. I was having problems with this. Thanks a ton.

---

