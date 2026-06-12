---
title: "new to ubuntu...trying to download world of warcraft"
date: 2012-11-16
forum: Wine
---

### Post by pandeybear on 2012-11-16
Today my computer crashed and I was unable to restore, so I downloaded Ubuntu and Wine. 
Now I am trying to download the installer from WOW website but when I go  to download it into windows using wine, it just leads me to save it on  start.exe and I do not know what to do.
I am NOT literate with Ubuntu or Wine, and I am COMPLETELY lost as to how to even download this. Anyone care to help me?

---

### Post by Paqman on 2012-11-16
Not quite sure I understand your exact problem, but essentially what you need to do is:

[LIST=1]
[*]Download the Windows .exe file for your game
[*]Run that .exe through Wine (you might need to right click and tell it to open it with Wine instead of the archive manager)
[*]This will install it into a fake C drive that's inside your Ubuntu home folder.
[*]Then just launch the game the same as you would in Windows, but through Wine
[/LIST]

A couple of things to bear in mind:
Ubuntu is not Windows. Trying to get Windows software like WoW to run in Linux is often difficult and has disappointing results. If you want to play a lot of Windows games then the best OS to install is Windows, not Linux (there's always dual-boot!). Having said that I believe that WoW is one of the lucky games that does run alright through Wine.

You may want to install [PlayOnLinux]("apt:playonlinux"), it's a front-end for Wine that seems to take a lot of the pain out of using it, and should be able to set up WoW for you and make any tweaks required to get it working ok.

---

### Post by pandeybear on 2012-11-16
The problem I am running into is that when I try to download/save the file, I am unsure of the destination that I need to download that file from. The next problem is that I do nt know how to 'run it in wine'.

---

### Post by pandeybear on 2012-11-16
It is all this hot mess of the opening, extracting, and when I extract it is just doc files...

---

### Post by sffvba[e0rt on 2012-11-16
Perhaps read through this and see if it answers some of your questions - [https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft)


404

---

### Post by Paqman on 2012-11-17
> **pandeybear said:**
> The problem I am running into is that when I try to download/save the file, I am unsure of the destination that I need to download that file from. The next problem is that I do nt know how to 'run it in wine'.

You can save it to anywhere you like. Your desktop is fine. To run it, right click and "open with" the choose Wine from the list. You could also tell it to use Wine for all .exe files by default.

Seriously, have a look at PlayOnLinux. It's specifically designed to make all this easier.

---

