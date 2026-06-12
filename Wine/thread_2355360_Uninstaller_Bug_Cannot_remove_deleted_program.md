---
title: "Uninstaller Bug: Cannot remove deleted program"
date: 2017-03-12
forum: Wine
---

### Post by mr-good555 on 2017-03-12
A friend of mine wanted me to test a game he made called "Tricky", and it has long since played and forgotten. It uses a DotNet framework, I think, because I had to use Wine to run it.

I tried to uninstall it a few weeks ago but no uninstaller was provided. As a precaution, I checked ***wine uninstaller*** and uninstalled it there. Without me knowing, it, instead, uninstalled a different Wine Program, because the game's name was still there.

Trying to uninstall it again would ask ***wine uninstaller*** to uninstall my DotNet framework. So, in my rush, I just deleted it from my folders.

Today, as I tried to uninstall another item, the game is still there. I tried ***find -iname "tricky"*** and then browsed to the results to delete them. But ***wine uninstaller*** still shows Tricky installed, and still offering to uninstall my DotNet Framework if I click the Modify/Remove button.

How do I remove this game that doesn't exist?

---

### Post by deadflowr on 2017-03-14
I'm thinking you might look into registry cleaning.
Here's a couple to look at
[https://appdb.winehq.org/objectManager.php?sClass=application&iId=10313]("https://appdb.winehq.org/objectManager.php?sClass=application&iId=10313")
[https://appdb.winehq.org/objectManager.php?sClass=version&iId=12127]("https://appdb.winehq.org/objectManager.php?sClass=version&iId=12127")

---

### Post by mr-good555 on 2017-03-17
Oddly enough, despite both getting Platinum ratings, both don't work, and ended up clogging my uninstaller more. XDD

At least I know where I'm heading now. Thanks. ^w^

---

### Post by mr-good555 on 2017-05-09
An update.

I realized that There was an update for Wine (2.0). So I decided to upgrade, and I deleted the old `.wine` folder before doing so.

In trying to check for if my programs are still installed, sadly they were (I wanted a clean reinstall), but the "Tricky" program was now assigned to the proper uninstaller.

It may have something to do with the registry cleaners, too. I tried too many, and the one I didn't delete, somehow had only "Untitled" on it. But letting you know it didn't work until the re-install.

**So, in short, **re-install wine, and it should clean up easy.

---

