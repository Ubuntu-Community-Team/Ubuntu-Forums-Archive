---
title: "Wow Error #132"
date: 2012-03-10
forum: Wine
---

### Post by htx1 on 2012-03-10
When i Login to World of Warcraft (cata) everything is running smooth but when i go in a high latency area like any major city, or even an instance the game crashes giving me the error 132 im currently using ubuntu 10.04 and wine 1.2.3, on my old jolicloud system wine 1.3.14 worked like a charm but now when i use the command sudo apt-get install wine1.3 it gives me some stupid wine 1.4-rc6 (beta.. which sucks ***) so if someone can help me because it has something to do with the memory wine is using or help me get the 1.3.14 back!


this is my WTF.config file or whatever
SET SoundOutputSystem "1"
SET SoundBufferSize "150"
SET gxApi "OpenGL"
SET locale "enUS"
SET enterWorld "1"
SET hwDetect "0"
SET gxWindow "1"
SET videoOptionsVersion "4"
SET playIntroMovie "4"
SET Gamma "1.000000"
SET lastCharacterIndex "9"
SET readTOS "1"
SET readEULA "1"
SET showToolsUI "1"
SET accounttype "CT"
SET Sound_OutputQuality "0"
SET Sound_MusicVolume "0.40000000596046"
SET Sound_AmbienceVolume "0.60000002384186"
SET Sound_EnableDSPEffects "0"
SET farclip "185"
SET particleDensity "10"
SET reflectionMode "0"
SET baseMip "1"
SET environmentDetail "50"
SET textureFilteringMode "0"
SET weatherDensity "0"
SET realmName "Ravencrest"
SET gameTip "2"



:popcorn:

---

### Post by cwwilson721 on 2012-03-10
> **htx1 said:**
> ... on my old jolicloud system wine 1.3.14 worked like a charm but now when i use the command sudo apt-get install wine1.3 it gives me some stupid wine 1.4-rc6 [COLOR="Red"](beta.. which sucks ***)[/COLOR] so if someone can help me because it has something to do with the memory wine is using or help me get the 1.3.14 back!

Just saying something "sucks", is NOT correct. Why does it "suck"? Is it (maybe) because your HARDWARE "sucks"? Or you can't install/configure wine correctly? 

1.4 is the recommended level, and it works fine. I use it as my WoW install, and no issues at all.

1.2 _will_ error out.

You can install a previous wine version, just [READ THE STICKY]("http://ubuntuforums.org/showthread.php?t=871535")

Just saying "wine sucks", and no info, and not reading the sticky..Well, you see what happens.

---

### Post by htx1 on 2012-03-10
Ha thanks for the fast reply.. although i shouldent say it sucks your right, i just dont know how to configure it correctly even though iv followed almost every guide i could find on google.. im gonna try uninstalling it with wine, reinstalling wine 1.4-rc6 then installing wow through wine 1.4-rc6 ill give an update when i do this to see if it changes anything.


Also the one thing that i like about the wine 1.4-rc6 is the Librarie Overrides are already set up.. so i guess thats a plus :P

---

### Post by cwwilson721 on 2012-03-11
No need to google. Just search this forum for "wow+wine+cata".

I guarantee that IF YOU FOLLOW THE STEPS, IT WILL WORK

---

### Post by Tweak42 on 2012-03-14
You shouldn't have to reinstall wow itself.  It's easier to move it out of the 1.3.x wine prefix, create a new 1.4.x one and move wow back in (or sym link it).

If you're worried about damaged game files the run the repair.exe in the wow directory once you got a clean prefix setup.  Also may want to clean install any addons cause those sometimes cause instability.

---

