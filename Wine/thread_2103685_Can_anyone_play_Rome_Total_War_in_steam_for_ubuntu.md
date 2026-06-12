---
title: "Can anyone play Rome Total War in steam for ubuntu?"
date: 2013-01-10
forum: Wine
---

### Post by AM Ramakrishnan on 2013-01-10
I have not installed Steam on Ubuntu, but might if I can play RTW. RTW is the only game I play on Steam, and works on the Windows XP side of my dual boot with Ubuntu 12.04 LTS.
If anyone has played it, please tell me; games and other software like Steam is what is keeping me using XP!
Thanks, 
-AM

---

### Post by drawkcab on 2013-01-10
No.  RTW and about 99% of the Steam catalog is not available in Steam for Linux.

Here's what is, most notably Team Fortress 2:  [http://store.steampowered.com/browse/linux/](http://store.steampowered.com/browse/linux/)

However, I expect all of this to change very rapidly in the next year or so, especially as Steam is launching a console that is very likely based on Ubuntu.  I think we'll see more and more games made available to Linux player via Steam.

All of this is very good news but you're going to have to be patient and stick with your XP partition for a while longer.

The Total War series is great btw.

---

### Post by zombifier25 on 2013-01-11
There's Wine which can run Windows games on Linux. But it can't run all of them, it can only run some of them, so consult [http://appdb.winehq.org/](http://appdb.winehq.org/) to see if the app you want to install can be run on Wine.
(It's also recommended that you install PlayOnLinux (a front-end for Wine), which can automate the installation process of some apps)

---

### Post by mastablasta on 2013-01-11
wine has silver rating for this game. meh better stay on windows.
 
funny how soem older versions had gold rating while demo had even platinum....

---

### Post by oldrocker99 on 2013-01-11
Steam IS porting their own engine's games to Linux; Team Fortress II is evidence that it can work. Now, if they can just port the Elder Scrolls games to Linux, I can die a happy man;).

---

### Post by AM Ramakrishnan on 2013-01-16
Is it possible to run steam games without starting the steam app? I have found that the Steam.exe file does not work in wine.

---

### Post by Lightning Dragon on 2013-01-17
If you installed them, you could click their icon to start the game, but you will be prompted to log in, so I don't think it is possible. You can try installing Steam through PlayOnLinux instead if wine is refusing to execute the Steam.exe.

---

### Post by AM Ramakrishnan on 2013-01-30
I have tried it again, and now steam opens up. The only problem is, when I tried to play rtw it waited for a long time and then a red, black and yellow screen that seemed to be a twisted rtw start screen popped up. I had to end it by quitting wine.

---

### Post by bears on 2013-09-15
Yes, it is possible, but only under Wine, and it can be quite a chore to set up.

I currently have Ubuntu 13.04, with the Linux Steam Client, and the Windows Steam Client both available. I used Play On Linux to set up the Windows Steam Client, and am currently trying to move all my Windows-only Steam games to work in this envronment. The process for setting up a new Windows game under Wine/PoL depends on what you already have on your system. You often need to install additional libraries, but if you have already installed them for one game, then you don't notice when they are needed for another. This probably explains why there are so many Wine database reports that seem to conflict as to whether games work or not.

I did have to install some additional libraries under the Play on Linux Steam branch before RTW would work properly ( sadly I don't remember which libraries ), but I have just finished the game as Rome:Scipii, so I can assure you it is possible.

There are still a few issues though. Firstly, I have not yet managed to get the movies working; this is not particularly important, as they are only used as intros, and when you destroy civs. They dont affect the game really. Secondly, getting the game running under the Linux compositors/window managers is interesting! At the moment it is best to use the simplest environment possible, since the newer compositors like Unity or Gnome 3 tend to be more likely to interfere. I have found XFCE to work best. You should run nothing else, and not use task switchers whilst running the game. Even then, you sometimes have to restart the game if the mouse won't use the whole screen.

Of course, the performance is not all that good either; fortunately RTW is so old now that it works OK on a decent modern PC. It would be much better if they wrote the games with SteamPlay in mind, of course, but I don't think a lot of games developers are actually that good at understanding general software engineering. Most have grown up with Windows and don't seem to understand anything else, which is a shame.

R.

---

