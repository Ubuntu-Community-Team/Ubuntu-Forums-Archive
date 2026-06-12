---
title: "Diablo II Digital Download"
date: 2008-07-09
forum: Wine
---

### Post by denali on 2008-07-09
Ok, so Blizzard has set it up so you can download your games from their store if you still have your CD Key.

WC III ROC and WC III TFT seem to work fine from their store.  However, Diablo II has a problem.  I can't get past the EULA acceptance screen.  I scroll down like it says, but the Accept button won't light up.

Anyone else able to get the digital download version of D2 to install?  If so, did you have this problem?  How did you get past it?

(Please note: This is NOT the 3 CD version of D2.  This is the version you can download from Blizz's online store.)

---

### Post by svuntcake on 2008-07-09
[https://www.blizzard.com/account/management/add-game.xml](https://www.blizzard.com/account/management/add-game.xml)

--

*Which game keys can I attach to my Blizzard Account?*

The following games are supported by the Games page at this time:

    *         StarCraft, StarCraft Battlechest, StarCraft Anthology
    *         Warcraft III, Warcraft III: The Frozen Throne, Warcraft Battlechest
    *         Diablo II, Diablo II: Lord of Destruction, Diablo II Battlechest **(Diablo II downloads will be made available soon)**

---

### Post by Valok on 2008-07-09
I used that service to dowload D2 and LoD about a week ago now.  So it certainly does work.  However, I did it in windows, so I don't have much insight into your problem other than the fact that the download is in fact working.

---

### Post by denali on 2008-07-09
> **svuntcake said:**
> [https://www.blizzard.com/account/management/add-game.xml](https://www.blizzard.com/account/management/add-game.xml)

--

*Which game keys can I attach to my Blizzard Account?*

The following games are supported by the Games page at this time:

    *         StarCraft, StarCraft Battlechest, StarCraft Anthology
    *         Warcraft III, Warcraft III: The Frozen Throne, Warcraft Battlechest
    *         Diablo II, Diablo II: Lord of Destruction, Diablo II Battlechest **(Diablo II downloads will be made available soon)**

[http://www.blizzard.com/store/details.xml?id=110000047](http://www.blizzard.com/store/details.xml?id=110000047)

Please note the box half way down the page where it says "Digital Download".  Also, people who were using the service in May noticed that when they registered their Diablo II key, the download link was not live.  It apparently went live in June.

[http://blizzardguru.com/2008/06/diablo-2-now-available-at-blizzard-store/](http://blizzardguru.com/2008/06/diablo-2-now-available-at-blizzard-store/)

---

### Post by denali on 2008-07-09
> **Valok said:**
> I used that service to dowload D2 and LoD about a week ago now.  So it certainly does work.  However, I did it in windows, so I don't have much insight into your problem other than the fact that the download is in fact working.

Cool.  That at least proves it's not an installer issue, but rather a WINE issue.

Did you, perchance, install it in Windows and copy the files to WINE?  If so, did it work?

---

### Post by karth on 2008-07-09
edit: bad answer, my mistake

---

### Post by karth on 2008-07-09
I, for sure, confirm that moving a Diablo 2 directory (i.e. C:\Program Files\Diablo II once it is installed in windows) into a Wine tree works perfectly

Add: [http://appdb.winehq.org/objectManager.php?sClass=version&iId=12889&iTestingId=28139](http://appdb.winehq.org/objectManager.php?sClass=version&iId=12889&iTestingId=28139)

This is interesting (comment about ies4linux)

---

### Post by Tyrfing on 2008-07-09
Just wanted to add that I am having the same problem, and IES4LINUX did not solve it. If anyone has any ideas, please share. I really want to play.

---

### Post by denali on 2008-07-10
> **karth said:**
> I, for sure, confirm that moving a Diablo 2 directory (i.e. C:\Program Files\Diablo II once it is installed in windows) into a Wine tree works perfectly

Add: [http://appdb.winehq.org/objectManager.php?sClass=version&iId=12889&iTestingId=28139](http://appdb.winehq.org/objectManager.php?sClass=version&iId=12889&iTestingId=28139)

This is interesting (comment about ies4linux)

Hi Karth,

Thanks for confirming I can move it from Windows to Linux.  I may end up doing that.

Concerning the appdb link, each Blizzard Digital Distribution has two parts: Downloader and Installer.  Dan is correct about using IES4LINUX to use the Downloader.  However, IES4LINUX will NOT fix the issue with the Installer.  That is a separate executable with a separate issue.  Currently, my problem is with the Installer and not the Downloader.  Honestly, the Downloader is a modified bittorrent client.

---

### Post by Tirune on 2008-07-11
I have the same problem with Diablo 2. I've downloaded the online version of the games through ies4linux, and that worked... but:
If I install from the directories through wine, I can't get past the EULA... I've tried with and without gecko installed. Without gecko installed it doesn't display the html, with gecko installed the accept button doesn't work.
If I install through ies4linux and the blizzard downloader (it installs it to ~/ies4linux/drive_c/Diablo2) Diablo 2 works perfectly... but the LOD expansion installer gives an error that I have processes open that interfere with the install (Waiting for files to close...). I checked all processes, and I didn't have diablo2, or any other installer/ie open. This even happens after a computer restart, and changing the windows version wine emulates didn't help. Running the diablo 2 installed this way (without expansion) works, but it doesn't work with wine settings, as for example the virtual desktop doesn't appear...

What SHOULD work is installing it through wine if the license agreement page would work. I tried copying the mshtml.dll files from internet explorer to the wine windows win32 map, to no avail, it still asks for installing gecko (which by the way doesn't work in wine 1.1.0 gecko 0.1.0 through running an application that needs it anymore. Even on a fresh wine install I experienced the exact same problems.

What could work if there was a way for wine to force the internet explorer html processor to work instead of gecko. That would allow the EULA agreement to work, and most likely the expansion to work, and everything through wine itself, in a wine directory. Does anyone know of a way to force this? Or any other solution to my problem? Help is much appreciated ^^

TiRune

PS: wine 1.1.0, ubuntu 8.04 Hardy Heron, amd 64 3500+ processor and x800 ati vid card. If anyone needs to know ^^

Edit: What works is placing the ~/ies4linux/drive_c/Diablo 2 files into the wine directory... Then the LOD installer goes past the 'you have to buy diablo 2' and proceeds with the install normally, however still can't get past the EULA :/

Edit2: What also might work, if someone has an installed Diablo2 and expansion... since the installed folder can just be moved to the wine folder to work... the person could perhaps share the folder for download somewhere, and it can just be inserted into the wine directory, although one would have to change the key for the game ^^

---

### Post by Innova on 2010-06-13
No solution for not being able to accept the EULA?

---

### Post by Elvish Legion on 2010-06-13
With the latest wine I didn't have any issues getting past the Eula.

Also check the post above about ie4linux

---

