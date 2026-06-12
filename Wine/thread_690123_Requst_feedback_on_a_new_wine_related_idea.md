---
title: "Requst feedback on a new wine related idea"
date: 2008-02-07
forum: Wine
---

### Post by Dave_Man on 2008-02-07
Hey guys, 

I have an Idea which I think would be perfect  for integrating wine better and easing its use.
I wrote a blueprint about it and would like some feedback.
Thanks.

[https://blueprints.launchpad.net/ubuntu/+spec/wine-config-packages](https://blueprints.launchpad.net/ubuntu/+spec/wine-config-packages)
Blueprint description:

I would like to suggest adding prebuilt wine packages that include the best configuration for a specific windows application.
These packages will install themselves to a local directory so many different, simultaneous, wine installations will be possible.
Each package will have a maintainer that will choose which specific wine version and configuration works best for that specific windows program.

Use cases:

1. John wants to install MS office 2003, john inserts the office CD in the drive, CD is autorun (using the planned autorun feature already in development).
Autorun checks the package database for the MS office 2003 wine package and asks the user for his password to install that package to office2003/.wine or whatever.
Wine package then automatically starts installing office from the CD with all the best configurations already there.
When the maintainer of the MS office 2003 package decides a newer wine version works better with that application or finds a better setting, it will update the package and its dependencies and the regular update manager will be able to update it.

2. Richard wants to play WoW, he inserts the WoW CD, package is automatically installed and the game installation starts. (no need to edit configuration files and other wine settings)

3. Paul wants to play a game that isn't supported by wine yet, Paul inserts the CD and is then alerted that the game isn't supported yet.
Paul clicks a button to request support for this specific game.
Paul is given the option of donating money to the developers to speed up that specific game's support.

---

### Post by gnelson on 2008-02-07
Sounds similar to how Cedega works.

---

### Post by cogadh on 2008-02-07
Or how Wine-Doors works.

---

