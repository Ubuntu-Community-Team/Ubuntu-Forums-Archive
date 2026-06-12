---
title: "Install Dota 2 with wine fully funcional?"
date: 2013-03-11
forum: Wine
---

### Post by alcobia on 2013-03-11
Can someone tell me how?
A  guide in youtube, site or here.
Im new to linux so you have to be clear and simple.
If it helps i use Bodhi Linux.
Intel.
Nvidia card.

---

### Post by Mark Phelps on 2013-03-11
In general, you go to the WineHQ website, the application compatibility database page, and look up the game and version you want to play.  It will then show ratings from garbage to platinum for the game and version.

The test results for each version give details on trying to install and use that version.

In your case, you will see that the ratings for Ubunti 12.10 are Silver and for Ubuntu 13.04 are Bronze:

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=24458]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=24458")

With ratings this poor, even if the game installs, you're not going to be able to play it.

---

### Post by aarons6 on 2013-03-12
i have no problems with dota2 on wine.. 
i just installed steam.. 
wine msiexec /i steam.msi 
and then used steam to install dota2.
it auto installs directx needed for the game to run.

edit.. forgot to say
rune steam with -no-dwrite option for the fonts to work.. 
so its
wine C:\path\to\steam.exe -no-dwrite

---

