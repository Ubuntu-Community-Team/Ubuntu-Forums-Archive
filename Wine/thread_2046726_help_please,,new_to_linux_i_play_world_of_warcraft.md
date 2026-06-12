---
title: "help please,,new to linux i play world of warcraft"
date: 2012-08-23
forum: Wine
---

### Post by shiloamico on 2012-08-23
i am new to linux but i love it and wont go back to windows,,but i am have trouble i play world of warcraft  in the game i have very low fps but in windows i had 80fps i need to fix this i am useing hp g62 ATI Mobility Radeon HD 4200 Series ubuntu 10.10,,i need to upgrade my display driver but dont know how i did use the additional drivers and installed the driver it had but it is not working so well,,i have googled this but still cant figure out how to install the driver u download from the ati website if some1 can please help me,,also my computer has 4 gigs of ram and core dual 2 ghz

---

### Post by anewguy on 2012-08-23
Click on "Ubuntu Forums", then find the gaming and leisure forum and post there. You'll have better luck finding help on games there - and who knows, maybe a new friend in the process.

---

### Post by Cheesemill on 2012-08-23
I think your first step should be to use a version of Ubuntu that is still supported.

10.10 reached end of life 4 months ago so it no longer receives any support or software updates. This will make it very difficult to get updated versions of Wine and your graphics drivers.

---

### Post by Quackers on 2012-08-23
Thread moved to Gaming & Leisure forum as this seems to be the appropriate place :-)

---

### Post by Pierrick584 on 2012-08-23
I'm pretty sure that driver issue does not have its place in the gaming forum...  not like the problem its the game that need to be fixed

---

### Post by thatguruguy on 2012-08-23
> **Cheesemill said:**
> I think your first step should be to use a version of Ubuntu that is still supported.

10.10 reached end of life 4 months ago so it no longer receives any support or software updates. This will make it very difficult to get updated versions of Wine and your graphics drivers.

This. 12.04 will be supported until 2017.  If you don't like Unity, there are other desktop environments to choose from. There's precious little reason not to use 12.04.

---

### Post by anewguy on 2012-08-23
> **Pierrick584 said:**
> I'm pretty sure that driver issue does not have its place in the gaming forum...  not like the problem its the game that need to be fixed

Just so you know, you'd be real wise not to argue with a forum administrator.

Also, the gaming forum isn't just for "the game does this" issues.  It's for all things that happen when trying to get the game to work - and that includes drivers.  There are going to be a LOT of people over there dealing with WOW, and there will probably be either a pre-existing fix or at least a user that has already had similar problems and knows how to get around them.

The AB forum is for novices having problems with Ubuntu itself.  WOW is not part of Ubuntu, and hence the leisure and gaming forum.

---

### Post by thatguruguy on 2012-08-23
> **Pierrick584 said:**
> I'm pretty sure that driver issue does not have its place in the gaming forum...  not like the problem its the game that need to be fixed

Actually, this should be in the Wine forum, since there are numerous threads about World of Warcraft there.

To the OP: You should look at [WineHQ]("http://www.winehq.org/"), the official web page for Wine. In particular, you should look at [this page]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=20549"). In particular, you should read this as an initial step:
> [LEFT]**nVidia / ATI :** Make sure you have the proprietary driver for your  video card installed, or WoW will not run. Once they are installed,  check to see if Direct Rendering is enabled by typing the following code  into Terminal :-                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          
[/LEFT]
          [LEFT]glxinfo | grep "direct rendering"[/LEFT]
          If it returns **direct rendering:****Yes**, you're good to go!_[SIZE=4]             [/SIZE]_
Then you should read the other comments on the page.

---

### Post by thatguruguy on 2012-08-23
OP, you should also read [this]("http://askubuntu.com/questions/129597/how-do-i-fix-my-installation-of-ati-catalyst-video-drivers-in-12-04-lts").

---

### Post by Perfect Storm on 2012-08-23
Moved the thread to wine.

Though as other said, there's a couple of things you need to do first.
1) Install a newer version of Ubuntu
2) Install restricted driver
3) Get the latest version of wine: [http://www.winehq.org/download/](http://www.winehq.org/download/)
 When these things are up and running you can start messing with wine and wow.

---

