---
title: "wine 0.9.59"
date: 2008-04-05
forum: Wine
---

### Post by ekravche on 2008-04-05
Has anyone successfully installed wine 0.9.59? sudo apt-get update and sudo apt-get upgrade do not work for me in  gutsy 7.10...

Thanx in advance

---

### Post by cogadh on 2008-04-06
It looks like the the Ubuntu/Debian package for 0.9.59 is not available yet:
[http://wine.budgetdedicated.com/](http://wine.budgetdedicated.com/)

---

### Post by h4mx0r on 2008-04-06
I'm still waiting for the next animated cursor patch until I install 0.9.59.

---

### Post by Twitch6000 on 2008-04-06
good to know another version is out :).

---

### Post by cogadh on 2008-04-06
If history is any indication, it may be a while before we see the 0.9.59 package. With the pending release of a new Ubuntu version, packaging usually seems to get put on hold until after the release is complete. Once Hardy has been released, then we will likely see new 0.9.59 packages for both Hardy and Gutsy (Hardy will have 0.9.58 available by default).

---

### Post by wingnux on 2008-04-07
Package is up.

---

### Post by cogadh on 2008-04-07
It must not be available to everyone yet, I just tried to update and got nothing. Looking at the Wine repository, it still shows 0.9.58 as the latest.

---

### Post by Sukarn on 2008-04-07
> **wingnux said:**
> Package is up.

The latest wine package in the hardy repository is 0.9.58-0ubuntu3 which is the third repackage of 0.9.58

I think you might be confused because of the recent update to -ubuntu3 in hardy's package from -ubuntu2.

The latest wine package in winehq.org's repository (for gutsy) is 0.9.58~winehq0~ubuntu~7.10-1 which is again a package of 0.9.58, not 0.9.59


Please tell us all here if you found a package of 0.9.59 elsewhere, like some ppa or something.

---

### Post by Game_boy on 2008-04-07
[http://mepislovers.org/forums/showthread.php?p=116556](http://mepislovers.org/forums/showthread.php?p=116556)

Mepis is almost binary-compatible with Ubuntu, right? That package worked from my Hardy installation.

---

### Post by cogadh on 2008-04-07
I believe it is, by why risk using a potentially incompatible package? There will be a "real" Ubuntu/Debian package eventually.

---

### Post by Sukarn on 2008-04-07
In any case, that is a i386 package and I'm on a amd64 machine.

I tried making a checkinstall package today but it failed to make the package. It installed fine via **sudo make install** even though **sudo checkinstall** failed to build the package, so go figure.

---

### Post by KhaaL on 2008-04-07
> **Sukarn said:**
> In any case, that is a i386 package and I'm on a amd64 machine.

I tried making a checkinstall package today but it failed to make the package. It installed fine via **sudo make install** even though **sudo checkinstall** failed to build the package, so go figure.

In the same boots as you, bro'

---

### Post by ekravche on 2008-04-08
Update Manager could not download the following
[http://wine.budgetdedicated.com/apt/dists/gutsy/Release.gpg](http://wine.budgetdedicated.com/apt/dists/gutsy/Release.gpg)
[http://wine.budgetdedicated.com/apt/dists/gutsy/main/i18n/Translation-en_CA.bz2](http://wine.budgetdedicated.com/apt/dists/gutsy/main/i18n/Translation-en_CA.bz2)

Strange. It's been like this for hours

---

### Post by ekravche on 2008-04-08
To be more precise I get the following error

Could not download all repository indexes 
[http://wine.budgetdedicated.com/apt/dists/gutsy/Release.gpg](http://wine.budgetdedicated.com/apt/dists/gutsy/Release.gpg): Cannot initiate the connection to wine.budgetdedicated.com:80 (2001:4de0:aaac:0:2456::2). - connect (101 Network is unreachable) [IP: 2001:4de0:aaac:0:2456::2 80]
[http://wine.budgetdedicated.com/apt/dists/gutsy/main/i18n/Translation-en_CA.bz2](http://wine.budgetdedicated.com/apt/dists/gutsy/main/i18n/Translation-en_CA.bz2): Cannot initiate the connection to wine.budgetdedicated.com:80 (2001:4de0:aaac:0:2456::2). - connect (101 Network is unreachable) [IP: 2001:4de0:aaac:0:2456::2 80]

---

### Post by Sukarn on 2008-04-08
> **ekravche said:**
> To be more precise I get the following error

Could not download all repository indexes 
[http://wine.budgetdedicated.com/apt/dists/gutsy/Release.gpg](http://wine.budgetdedicated.com/apt/dists/gutsy/Release.gpg): Cannot initiate the connection to wine.budgetdedicated.com:80 (2001:4de0:aaac:0:2456::2). - connect (101 Network is unreachable) [IP: 2001:4de0:aaac:0:2456::2 80]
[http://wine.budgetdedicated.com/apt/dists/gutsy/main/i18n/Translation-en_CA.bz2](http://wine.budgetdedicated.com/apt/dists/gutsy/main/i18n/Translation-en_CA.bz2): Cannot initiate the connection to wine.budgetdedicated.com:80 (2001:4de0:aaac:0:2456::2). - connect (101 Network is unreachable) [IP: 2001:4de0:aaac:0:2456::2 80]

Yeah, getting the same.

Something is wrong with their server.

---

### Post by FlyingIsFun1217 on 2008-04-08
If you don't mind the idea of using non-native packages, go ahead and try the Mepis .deb's. I've been using them since... 0.9.52 I think... and I've never really encountered a problem.

FlyingIsFun1217

---

### Post by Sukarn on 2008-04-08
Its not much of a problem compiling wine, now that it has been announced in the weekly newsletter that 8.04 is gonna ship with 0.9.58 because 0.9.59 was released one day after package freeze.

Anyway, as far as I know, the mepis packages are only for i386 and i'm on a amd64 machine. Why install an i386 package when I can just compile it on my machine?

I know wine runs in 32 bit mode even on a 64 bit machine, but (from personal experience) the 32 bit libraries are better mapped if a package for 64 bit is installed instead of forcing the architecture.

---

### Post by Nameless_one on 2008-04-08
The budgetdedicated repository is down for me.

---

### Post by Melcar on 2008-04-08
A problem with the server perhaps.  I can't update from it either.

---

### Post by Sukarn on 2008-04-08
The ip is actually refusing connections for me. Definitely something wrong with the servers.

It would be better if people stopped talking about it now, though.

Anyone who reads this far into the thread would know that the wine budgetdedicated repository is currently not working.

The next time I want to hear about it would be when it comes back up or if there is some news about the issue.

---

### Post by Weichpudding on 2008-04-08
Wine repo is back up and running, however 0.9.59 is not available as of yet.

---

### Post by badrunner on 2008-04-08
> **Weichpudding said:**
> Wine repo is back up and running, however 0.9.59 is not available as of yet.

But 0.9.59-ubuntu1 has been uploaded to hardy.

---

### Post by cogadh on 2008-04-08
Still not available for Gutsy, though.

---

### Post by Sukarn on 2008-04-09
> **badrunner said:**
> But 0.9.59-ubuntu1 has been uploaded to hardy.

Go to [https://wiki.ubuntu.com/UbuntuWeeklyNewsletter/Issue85](https://wiki.ubuntu.com/UbuntuWeeklyNewsletter/Issue85)
Check under Meeting Summaries - Wine Team
It says that
> Wine 0.9.58 will be the version in Hardy, as 0.9.59 comes out a day after full freeze

That is why I said earlier that hardy will be shipping with 0.9.58

I guess they changed their mind as 0.9.59 is up now.

---

### Post by Myke Greywolf on 2008-04-09
Well, this version solves a problem with window refreshing on XnView that was introduced in 0.9.58, and that was irritating me, so it's thumbs up all the way from me! :D

---

### Post by soxs on 2008-04-09
Well, they fixed some bugs, but caused some new. Now the tray is not synced / shown properly anymore :-(

---

### Post by Sukarn on 2008-04-09
> **soxs said:**
> Well, they fixed some bugs, but caused some new. Now the tray is not synced / shown properly anymore :-(

Yeah, I noticed that one too.

---

### Post by melchiorre on 2008-04-09
Hi all, I've packaged wine 0.9.59 for hardy and for gutsy, and it works fine.
Here is the link to my blog, it's in italian, but you need only the two links in this page to download wine package.

[http://melchiorre.wordpress.com/2008/04/06/uscito-wine-0959-ecco-il-pacchetto-deb/]("http://melchiorre.wordpress.com/2008/04/06/uscito-wine-0959-ecco-il-pacchetto-deb/")

---

### Post by Sukarn on 2008-04-10
No need for you to host a wine package for hardy as there is already a wine package in the official hardy repository for wine 0.9.59

The one for amd64 has also been repackaged once. I do not know about the package for i386.

---

### Post by Sukarn on 2008-04-10
> **Sukarn said:**
> The one for amd64 has also been repackaged once. I do not know about the package for i386.

Correction - second repackage just came up.

Edit : third repackage is up now. Maybe I should just stop reporting about this now.

---

### Post by Sukarn on 2008-04-10
> **soxs said:**
> Well, they fixed some bugs, but caused some new. Now the tray is not synced / shown properly anymore :-(

Try updating to 0.9.59-0ubuntu3 or 0.9.59-0ubuntu4

At [https://launchpad.net/ubuntu/+source/wine](https://launchpad.net/ubuntu/+source/wine) the version history shows that 0.9.59-0ubuntu3 has "Backport patch to fix system tray regression"

---

### Post by CarpKing on 2008-04-10
Thanks for the Gutsy package, seems to work.

---

### Post by coolkid5 on 2008-04-11
It's up now

---

### Post by Starks on 2008-04-11
Wine 0.9.59 competely breaks when you attempt to minimize an open Wine'd application.

The application simply disappears and you have to close it by killing the process.

---

### Post by soxs on 2008-04-11
> **Sukarn said:**
> Try updating to 0.9.59-0ubuntu3 or 0.9.59-0ubuntu4

At [https://launchpad.net/ubuntu/+source/wine](https://launchpad.net/ubuntu/+source/wine) the version history shows that 0.9.59-0ubuntu3 has "Backport patch to fix system tray regression"

thx, did not do any google searching so far

---

### Post by mjuhasz on 2008-04-12
> **Starks said:**
> Wine 0.9.59 competely breaks when you attempt to minimize an open Wine'd application.

The application simply disappears and you have to close it by killing the process.

Bugreport: [https://bugs.launchpad.net/ubuntu/+source/wine/+bug/216235](https://bugs.launchpad.net/ubuntu/+source/wine/+bug/216235)

---

### Post by soxs on 2008-04-12
initial bugreport @ winehq.org [http://bugs.winehq.org/show_bug.cgi?id=12362](http://bugs.winehq.org/show_bug.cgi?id=12362)

---

