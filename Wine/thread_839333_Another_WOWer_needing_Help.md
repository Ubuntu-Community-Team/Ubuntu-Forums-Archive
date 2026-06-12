---
title: "Another WOWer needing Help"
date: 2008-06-24
forum: Wine
---

### Post by tehpyrate on 2008-06-24
Hey Folks, 

Before I begin crying/Wining ( What a Pun ) about my problem here is my hardware:

AMD Phenom x4 @ 2.2 Ghz Agena Core 9550.
MSI K9A2 CF-F w/ 790x Chipset
ATI RADEON x2900XT 512MB GFX
2GB OCZ RAM ATI CERTIFIED


I'm very very very new to Linux. The only things I've figured out so far has been how to install the OS, Some Software through their instructions, and ATI Drivers, but I probably did that wrong. 

 I installed PSLinuxOS last night. Installed the ATI Drivers from their website. Direct Rendering said Yes. Ran glxgears .. ran for about 40 seconds. It said I was getting around 10k Frames per second. 

So I moved on and installed Wine from the Repository present (9.8x).Sorry I don't remember the exact version I haven't gone to sleep since yesterday. 

Copied over my WoW Install into the /root/.wine/drive_c/progra files/World Of Warcaft/..

Changed the config.wtf to: SET gfxApi "opengl". Also used the shader line. Turned off Ffxglow and ffxdeath.. 

Opened program manager, went to File -> Execute -> WoW.exe .. Black Screen. I could see two gray text boxes.. entered login name and password enter enter got in game. Really Really Crummy frame rate. 8/9 FPS. in windows I get between 50/60 w/Vsync and everything turned up all the way inc 8x Software AA. That may be irrelevant information. 

So I've pretty much given up on that. I'm gonna go ahead and say that PCLinuxOS doesn't like wine?...

I'm at work now downloaded Ubuntu 8.04. Took me 2/3 mins to get it too. 

so You're probably saying now. Wow. This Child is an idiot. he's going around in circles! 

I've been doing alot of reading and it seems that Wine seems to work its best in Ubuntu. 

I'm looking for any advice you guys can give me regarding my installation. Any information that may be valuable and will keep me from smashing my head on my desk after I load up Wine and WoW... Better yet anything that'll keep me from Switching back to Windows. >.> I like the Penguin. I even have a penguin Bag.

Sorry for Hitting you guys with a wall of text.

-Best, 
  Pyrate.

---

### Post by pedro_orange on 2008-06-24
This has everything you really need.

[https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft)

Make sure you use a more up to date wine than in the repos (I've not checked repo version for a while, but last time I downloaded it, it wasn't 1.0 - which is what you want)

There is a good sticky in this forum that will tell you how to get the latest wine.

---

### Post by tehpyrate on 2008-06-24
thanks. I read through it. It should be simple enough. I think >.< I'll have to try it.

I can't understand what I did wrong yesterday. Maybe I didn't install my Graphics Card correctly. I was able to Run WoW in PCLinuxOS but was getting 8~10 FPS. 

I've also read that the ATI GfX Drivers are intended for the more mainstream Distros of Linux. Ubuntu Being one of them. 

There is no possible way that I could get 9~10k FPS in glxgears without a hardware rendering device right?

do I have to manually input the memory bandwidth and clock of my GPU? i.e 517Hz @ 512MB.. or will the Catalyst drivers take care of that for me?

---

### Post by Faud on 2008-06-24
Your ATI card is not going to perform nearly as well in linux as it does in windows....sorry.
In 8.04 ubuntu you can look in the repos for envy....this will auto install the corect drivers for your graphics card.
Install wine 1.0 also in the repos then copy it over as you did. Delete you config.wtf, make the changes you need to make and dont forget to include the shaders line.
Start up the game and good luck.
Expect your minimap to be white...ati actually said they are working on a fix for this.

Hope it works for you.

Faud

---

### Post by tehpyrate on 2008-06-25
Well. After hours of beating and kicking and what not. I ran into a bunch of problems...

1. Ubuntu Wouldn't boot. Reinstalled using the LiveCD like 5 times before I realized it wasn't Ubuntu, but the grub settings. At the OS window hit c then deleted root (hd2,1) and it booted. Then edited the grub to root (hd0,1)

2. During the ATI Driver install system stopped responding. Had to reboot and when I got back in. Everything went white. went into the Shell and finished the ATI Installer there. everything booted just fine afterwards. 

3. Installed Wine using the WoWiki How to Link. 

4. Copied my WoW Installation over made all the changes. 
5. Had a flickering problem. Turned off Visual Effects, and it went away. Ended up Installing KDE anyways. I like it for some reason. 

6. Tweaked everything WoW runs at about 30-40FPS... meh.
7. Logged in played for a bit Got my butt kicked. any who now i'm surfing about for cool themes.

---

### Post by MemoryDump on 2008-06-25
it really is a shame that Blizzard doesn't release a linux client. Performance would be soooo much better. It does run well until Wine, however performance (especially fps) takes a hit :(

---

