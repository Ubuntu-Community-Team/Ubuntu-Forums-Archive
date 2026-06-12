---
title: "uninstall microsoft office"
date: 2014-01-29
forum: Wine
---

### Post by jrmchess on 2014-01-29
I am trying to uninstall ms office which I installed via wine but can't. I tried it through "uninstall wine software" in the dash. I also tried to uninstall it by clicking on the ms office setup icon but am unable to do so. The icons for ms office appear in the dash home and when I click them they launch the office software.


also when I tried to write vba code for excel it crashes. is there a fix?

Please help

Thanks

---

### Post by krustybaguette on 2014-01-30
A couple of days ago I was running  WINE 1.4 in my Linux Mint installation. The three or four Windows apps I use worked well with that older version of WINE. I needed to upgrade from MS Office 2003 to 2010 and the install under 1.4 just didn't work. So I ended up upgrading via PPA to Wine1.7. There were problems so I tried PlayOnLinux but old wineprefix (i.e. Wine1.7) is gone. Is it possible and safe to run both POL and plain WINE on the same Linux installation? If I have to choose I'll go back to plain WINE as I also have the option of running MS Office in a Virtual Box Windows 7 installation.

PS @jrmchess I had the same issue with uninstalling MS Office 2010 after I had installed it under Wine1.7. Eventually I used winetricks to delete the entire wine prefix (which appears to be "winespeak" for wine and all its installed apps. However, I had to manually remove all the menu items by right click on Menu button/Edit Menu.

---

### Post by PotatoHead007 on 2014-02-01
Not sure if this will work, give it a try: Go to your .wine folder, into drive_c. Look around there, you should have a MS folder there. Try deleting that, and then go into Dash again to check if it is gone. I removed a few programs like that, maybe it works :)

---

