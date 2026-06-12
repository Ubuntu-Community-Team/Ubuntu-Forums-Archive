---
title: "Is this possible?"
date: 2008-07-06
forum: Wine
---

### Post by RB2610 on 2008-07-06
I already have many games installed under XP, and would like the convenience of being able to play a couple of them in Ubuntu. But I'm getting short on HD space and I am reluctant to install a game that is already installed on my system a second time, especially when games take up 5GB each :(

Is it possible to get wine to run a game using the original install folders from XP, any help would be greatly appreciated.

(I am new to both Ubuntu and Wine, having only got them today :) )

---

### Post by cogadh on 2008-07-06
Wine is not made to work with an existing Windows installation and trying to get Wine to do that can screw up the Windows partition, leaving it unbootable. The proper way to use Wine is to install any software you are trying to run into the Linux partition. You may be able to link your saved games files from the Wine install to the Windows install, but I really don't recommend it. Usually when I am trying games out in Wine, if I find that it works perfectly I will copy the saved games from my Windows installation to the Wine installation, then uninstall the game from Windows, thereby freeing up the space in Windows.

---

### Post by Felson on 2008-07-09
I have all my games on a partition separate from my Windows and Linux installs. Works without issue with any older games that don't use the winblows registry. I also got Oblivion to work by "moving" the original install as a backup, installing with wine to the same place as windows wants it. After a bit of testing to make sure I didn't pooch it, I deleted that backup. As cogadh says, this can be a little dangerous, but as far as the partition table goes, I have had no issues at all yet. If your partition is NTFS, install ntfs-3g. Personally I like to do it the other way though. I run my partition as ext3, and install [http://www.fs-driver.org/](http://www.fs-driver.org/) on the windows side. That way, on linux side, you have real file permissions. Plus, I am in Linux WAY more then winblows.

---

### Post by ooobuntooo on 2008-07-09
> **cogadh said:**
> Wine is not made to work with an existing Windows installation and trying to get Wine to do that can screw up the Windows partition, leaving it unbootable. The proper way to use Wine is to install any software you are trying to run into the Linux partition. You may be able to link your saved games files from the Wine install to the Windows install, but I really don't recommend it. Usually when I am trying games out in Wine, if I find that it works perfectly I will copy the saved games from my Windows installation to the Wine installation, then uninstall the game from Windows, thereby freeing up the space in Windows.

What?! I do this all the time!
Are you seriously suggesting that I could be ******* up my Windows partition?
I better stop doing this!

---

### Post by Felson on 2008-07-09
I personaly wouldn't panic. I have been doing this for clsoe too 2 years myself. I think the fear stems from every ntfs mount system before ntfs-3g having a big warning that they may corupt your data, and to use at your own risk. IMO, that was just a CYA (Cover Your Assets) since none of them wanted to get sued if they made a mistake.

---

