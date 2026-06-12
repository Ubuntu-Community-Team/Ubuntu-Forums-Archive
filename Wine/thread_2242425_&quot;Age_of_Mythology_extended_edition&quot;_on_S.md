---
title: "&quot;Age of Mythology extended edition&quot; on Steam"
date: 2014-09-01
forum: Wine
---

### Post by peewee3 on 2014-09-01
Hi everyone, I recently bought Age of Mythology Extended edition on Steam and tried running it using winetricked steam. When I open the game it says "First time setup: Installing Microsoft VC Redist package Step 1 of 1" 

I leave it running but nothing happens for over 2 hours...
Please help!

---

### Post by raptir on 2014-09-04
What version of Wine are you running? Looking at WineHQ it seems as though the Visual C++ Redistributable installer requires a fix that was implemented in 1.7.25. I would try updating to the development build through the PPA to see if that fixes it.

[https://www.winehq.org/download/ubuntu](https://www.winehq.org/download/ubuntu)

Some may disagree, but in general I would recommend the stable builds for running older "tried and true" software, but updating to the beta builds if you're trying to run new games.

---

### Post by f_j2 on 2014-09-15
> **peewee3 said:**
> Hi everyone, I recently bought Age of Mythology Extended edition on Steam and tried running it using winetricked steam. When I open the game it says "First time setup: Installing Microsoft VC Redist package Step 1 of 1" 

I leave it running but nothing happens for over 2 hours...
Please help!

Hello,

i am encountering the same problem, while using playonlinux. Im running the [COLOR=#000000]1.7.25 Version of Wine. 
Any suggestions?

Best regards[/COLOR]

---

### Post by EuclideanCoffee on 2014-09-15
According to WineHQ, you're out of luck; installation didn't seem to work in the latest test case.
[https://appdb.winehq.org/objectManager.php?sClass=version&iId=5323](https://appdb.winehq.org/objectManager.php?sClass=version&iId=5323)

With Steam applications, I recommend using PlayOnLinux rather than Wine. Steam is a changing application, and you'll need additional support and testing for it. I recommend using Skyrim's settings with configuring your virtual drive for PlayOnLinux: [https://appdb.winehq.org/objectManager.php?sClass=version&iId=24749](https://appdb.winehq.org/objectManager.php?sClass=version&iId=24749)

Most Steam games work out of the box with these settings.

---

### Post by f_j2 on 2014-09-15
Thanks for the help.
I came on step further due to using playforlinux. 
You can tell AoM not to install VC Redist by deleting or renaming the file "installscript.vdf" in /home/xxx/.PlayOnLinux/wineprefix/Steam/drive_c/Program Files/Steam/SteamApps/common/Age of Mythology/_CommonRedist/vcredist/2012/
Sadly I this only led to a new problem. When I start AoM in Steam it gives me the following error:
"Initialization Failed
Direct3D initialization failed. Frequent cause is an old or corrupted driver.
Please check the log file for more information"
Using google I found:
[https://bugs.winehq.org/show_bug.cgi?id=34008](https://bugs.winehq.org/show_bug.cgi?id=34008)
But that didn't really help.
Any more Ideas?

I really wanna play that game^^

---

