---
title: "Wine"
date: 2012-08-15
forum: Wine
---

### Post by ericsonlouis on 2012-08-15
Hello i am thinking of downloading wine so i can run my windows games but i am lost and i have some questions 

1) How do i install wine the download link and how to install games        for it?

2) Do i need i windows cd to install wine?

3) And which is better for running games Oracle VM VirtualBox or Wine?



Thanks

---

### Post by Curtis6767 on 2012-08-15
First go over to [WineHG]("http://appdb.winehq.org/") and look for your games and see how they're rated. Some will will fine under Wine. Others won't. Wine is available in the Software Center so you don't need a CD to install it.

If you have a Windows install disk, then you could run your games in Virtual Box once you've installed Windows. You'd install them just as you would in any other Windows install.

There is a Wine-specific sub forum, where this post is probably going to be moved to, and you might get more help there. Plus, there's a Virtualization sub forum where you can get more help on Virtual Box.

Hope this helps.

---

### Post by ubudog on 2012-08-15
*Thread moved to the Wine sub-forum.*

You should get some more help here. :)

---

### Post by na5h on 2012-08-15
1. You can install Wine from the Software Center, but I would recommend that you try out PlayOnLinux (also found in the Software Center)! PlayOnLinux is a front-end for Wine (installing it will also install Wine) which makes the installation of Windows games and applications a lot easier. It also allows you to use different versions of Wine with different applications/games.

2. No, Wine does not require a Windows license.

3. Oracle VM and Virtualbox are used to create and run virtual machines. Virtual (Windows) machines require a license just like any physical machine would. [Wine]("http://www.winehq.org/") is a compatibility layer that can run some Windows applications very well while others don't work at all. Check out the Wine Application Database for more information regarding which applications you can use with Wine:
[http://appdb.winehq.org/](http://appdb.winehq.org/)

Virtual Machines also require a ton of resources from the host-computer, I've heard that Wine can achieve near native performance while running certain Windows applications/games...

---

### Post by TheFu on 2012-08-15
> **ericsonlouis said:**
> Hello i am thinking of downloading wine so i can run my windows games but i am lost and i have some questions 
1) How do i install wine the download link and how to install games        for it?
2) Do i need i windows cd to install wine?
3) And which is better for running games Oracle VM VirtualBox or Wine?


I fear you have set too high expectations for WINE.  When WINE works well, it really, really works well. When it doesn't, it will not work.  WINE is preferred over VirtualBox or other HVM solutions because it requires much less overhead. Some Windows games actually run better and faster in WINE than on native Windows.

Running low end games under Virtualbox can be enjoyable, but the graphics simply cannot keep up with the latest games unless the game-team specifically went out of their way to make it work. This applies to WINE as well.

So whether any specific game works well or not, is really a crapshoot.  The only way to get an answer there, is to check out the app/game database on winehq.org - when you are there,  read over the detailed instructions required to get each game working. Most need more than just an installation - you'll likely have to tweak the WINE environment for any success. Get ready to learn all about DLL dependencies .... or you can buy the commercial solutions for WINE that pre-bundle the dependencies and make installation much easier. I think those tools are about $20.  **Bordeaux** is one of the commercial WINE tools.  Supporting them supports WINE development.

For high-end graphical games, you'll probably need to dual-boot. Sorry, but this is the reality.

---

### Post by ericsonlouis on 2012-08-15
Thanks i think i will try wine and check out what you guyes said :)

---

### Post by na5h on 2012-08-16
A little off topic, but you can also find many native games in the Software Center. [Desura]("http://www.desura.com/") for Linux is also quite nice for gaming, and Steam is coming soon...

---

