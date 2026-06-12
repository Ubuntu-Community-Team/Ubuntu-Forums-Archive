---
title: "Mouse issues with GW2 and Wine"
date: 2013-07-02
forum: Wine
---

### Post by Chaemae on 2013-07-02
So I've been looking all day for a solution to this issue and have not found anything to help.
I recently partitioned my HDD to have Ubuntu 64bit alongside Windows since my 32bit version of Windows 7 was causing a lot of problems trying to play GW2 and run Skype at the same time.

Anyway, I just got Guild Wars 2 to play through Wine, but unlike in Windows, pressing my L and R mouse buttons together does not allow me to turn. Rather, I can only run straight. GW2 doesn't allow for mouse button mapping yet, and so far my search for mouse-to-keyboard mapping software has turned up empty.

I cannot stand to play as a keyboard turner. I usually use my mouse for running, turning, and fixing the camera angle. But with these mouse issues, I can't control my camera with the R mouse button like usual, and I can't turn my character with the mouse at all. I can only strafe with the mouse if I hit A or D while running with both main mouse buttons down. The middle button that I use to scroll works as it should, though.

After a couple searches, I found that mouse turning in GW2 just doesn't work for some people and it seems to occur randomly (as far as I can tell--no one has supplied any system specs that might help me figure out what's going on with my own).

I use an AMD processor, nVidia GeForce GTX 550 Ti graphics card, and Wine on Ubuntu 64 bit 12.10. I can only get GW2 to run by opening a terminal and commanding it with "wine ~/Desktop/Gw2.exe -dx9single". I am wondering if my mouse issue is Ubuntu or Wine-related. Unplugging it and plugging it back in with the game open doesn't help, and I have even tried swapping mouses.

Does anyone know a fix for this, or know of any keymapping software that will run on 12.10? Or if upgrading to Raring Ringtail might help?

---

### Post by Mark Phelps on 2013-07-03
Don't have a fix -- but the WineHQ website rates GW2 with Ubuntu 12.10 "Bronze" -- which is the worst rating a game can get that installs.

See the page for details:  [http://appdb.winehq.org/objectManager.php?sClass=version&iId=26558&iTestingId=75567]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=26558&iTestingId=75567")

---

### Post by Chaemae on 2013-07-03
Well, that's at least a start. It doesn't run poorly for me, especially considering I run everything but shadows on the highest graphics setting. I'll have to fiddle around with some updates to see if that helps to resolve the mouse issues.
Thanks :)

---

### Post by Thee on 2013-07-04
You might wanna try with PlayOnLinux, it has dedicated Wine builds for specific games. And judging by [this page]("http://appdb.winehq.org/objectManager.php?bShowAll=true&bIsQueue=false&bIsRejected=false&sClass=version&sTitle=&sReturnTo=&iId=26558"), Wine version 1.5.14 seems not to have mouse related problems.

I was wondering if you can tell me what FPS are you getting in GW2?
I was also thinking of installing GW2 on Ubuntu, but didn't thought it would run smooth so I didn't, but you seem to have luck, although, I have an ATI card, not Nvidia...

---

### Post by Chaemae on 2013-07-10
I'll try PlayOnLinux, but when I first installed it and tried to run GW2 through it, it would crash immediately. I'm going to give it another shot after some updates. 

Playing it through Wine, I get about 15-20FPS on maximum graphics (without shadows). I get less if there are a lot of particle effects going on, though.
Playing on my Windows 7 32bit partition, I get about 40 FPS using the frame limiter and graphics all at the highest settings, otherwise I get 50-60 FPS. However, running my graphics like that would cause GW2 to crash. From what I have seen, a lot of other people playing on Windos 7 32bit with NVidia cards get the same problem I have on max graphics where textures will drop and models will turn blue and green. It's not an overheating issue for sure as I have enough fans that the inside of my computer never gets above 50F. It didn't start happening until November though. Before that, all was fine.

A friend just bought me a copy of Windows 7 64bit that I'm going to install in place of 32bit Windows tonight but I'd like to get GW2 running on Ubuntu as well.

Update: I tried opening up PlayOnLinux, and as soon as I would tell it to run GW2, it would freeze my system.

---

