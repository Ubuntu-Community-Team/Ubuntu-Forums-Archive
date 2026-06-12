---
title: "Eve-Online working... but not quite"
date: 2008-07-15
forum: Wine
---

### Post by couzin2000 on 2008-07-15
OK. I wanna play this game Eve-Online, but I can't get it to work.

Here's what I have:
[LIST]
[*]AMD Athlon X2 5600+
[*]NVidia GT7300
[*]Asus board
[*]no issues of any kind with anything.
[/LIST]

Here's what I run:
[LIST]
[*]Ubuntu Hardy heron 8.04
[*]Wine 1.1
[/LIST]

Here's what I did:
[LIST]
[*]followed the steps in this thread: [http://ubuntuforums.org/showthread.php?t=804171]("http://ubuntuforums.org/showthread.php?t=804171")
[*]also followed this thread: [http://ubuntuforums.org/showthread.php?t=839646]("http://ubuntuforums.org/showthread.php?t=839646")
[*]and did what was done in here: [http://ubuntuforums.org/showpost.php?p=5037271&postcount=9]("http://ubuntuforums.org/showpost.php?p=5037271&postcount=9")
[*]I especially followed this here: [http://appdb.winehq.org/objectManager.php?sClass=version&iId=9971]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=9971")
[/LIST]

And what I get is a partly working game. When I disable Compiz-Fusion, and go back to Metacity, I finally get the game to open up in all black, fullscreen, but that's all I get. I can see the mouse's contour change color when I hover over something that should be there, but I can't see any game content at all.
I accidentally hit ESC, and up popped the config menu! I tried running a few changes in the display config, tried downloading the premium graphics content but I get an error, and although I do hear sound, I can't get any graphics but a black screen. I can't apply anny patches, since my game is a more recent version (running the Windows version 58188, latest patch is 56866).

What am I missing here?

---

### Post by t.rei on 2008-07-16
What I did to get it running on my 8.04:
* deleted my old .wine directory, since there were several "experiments" in there.
* installed wine from the official winehq repository ( [http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb) )
* downloaded the windows premium client ( [http://www.eve-online.com/download/windows.asp](http://www.eve-online.com/download/windows.asp) )
* installed the client.
* copied the *arial.ttf *(from a windows partition) to the *~/.wine/drive_c/windows/Fonts/* directory
* copied the *d3dx9_35.dll* (from windows) to the *~/.wine/drive_c/windows/system32/* directory
* ran winecfg , went to 'Audio' Tab and enabled "Emulated" (at the bottom)
* started eve
* logged in to update
* on next start - disabled premium graphics in settings and logged in again

(thats it, if I didn't miss anything)

Now the only issues I'm having is low(er) fps. Strangely when alot of UI elements are shown or in space. :/ x700 - ati card probably being the reason.

---

### Post by couzin2000 on 2008-07-17
After trying out a few things, I finally uninstalled the Windows version and installed the Linux version with Cedega. It runs, I've managed to play quite a few hours and the game has remained stable -- however, I do get corrupted textures... I'm looking for the threads to fix this, but I can hardly find anything in here. Help out?

---

### Post by t.rei on 2008-07-21
I had no luck getting the Official-Linux-Client to run properly.

It would give me white space backgrounds and messed up character portraits.

---

### Post by couzin2000 on 2008-07-22
I've managed to play for quite a while with the Linux client now, running Cedega. It runs - but that's all. I get corrupted textures on my ship, on stations, on asteroids (less on them though) and since yesterday I,ve started to see corruption in the transparent textures that make up the "warp bubble" when travelling. I've also seen warp accelerator modules and jump gates with NO textures - just white filling. The shape is there, but textures are messed up everywhere.

Now that the game runs on Ubuntu Hardy with Cedega, I'll give a try to the Windows premium version on Wine. In Appdb, *even the **premium** client runs* - so there *must* be a way to run it.

If anyone has a suggestion, I would love to make this a big thread. Trying to usurp other people's threads didn't work (sorry guys :oops: ) so hopefully anyone with a problem with running their own client on Linux will come here and try to discuss this game.

Thanks!

---

### Post by olsmithy on 2008-10-06
It all boils down to lazy programmers and "Eve" CCP developers are known for pushing buggy patches on windows never mind linux.

What gets me is why you would push out a product and not make it accessible to people using ATI graphics cards for over 5 years?

This nightmare will never end...

Mark my words CCP = Pathetic

Don't even bother it's a good game and the concept is great. Don't get me wrong. But the follow through of the developers is absolutely lowsy.
It's clear they don't know what is going on when it comes to developing software for linux based environments.

They should really learn to take the stance of the OpenBSD team since they really need it. 

Develop -> Patch -> Beta Test -> Public Release -> New Version

This is how I'm pretty sure it is working now

Develop -> Public Release -> Beta Test on the public -> Add new features to make up for bad coding and bugs. 

P.S. Next time your in Jita have a serious lag courtesy of them.

---

### Post by Chii on 2008-10-16
I am curious... when was the last time you played?  :>  They fixed Jita about a month back, by way of upgrading to a 64 bit architecture, and doing some other stuff (Just regurgitating what I remember as I am no programmer).  As a result, Jita even at 950 people is pretty free of lag.

As far as stability, I think it really depends on the hardware you are using.  Because on my laptop, I can run it on wine seemingly just fine... until I start messing with drones.  And then when my drones are attacking random items and I recall them or send a command to them for them to do something the game at times will freeze, but other than this... it runs just fine.

For the Linux/Cedega clients, it all works except that the fps are a tad bit lower and sound does not work.  

In either case it is not bad... just requires tweaks to make it work with your system.

I am curious though, for anyone who has gotten it running in wine.  Have you encountered this issue?  If so how did you resolve this?  As this is among the last obstacles keeping Vista on my lappy :>

---

### Post by Burigufutsushide on 2008-10-20
I'm a bit disappointed that my method of running EVE-Online was not among the voting options. I'm using CrossOver Games to run the Premium version and I have not found any differences from running it in Windows yet.

Installation was pretty much straightforward, just install the Crossover .deb and fed it the EVE Premium setupfile afterwards, worked right out of the box.

---

