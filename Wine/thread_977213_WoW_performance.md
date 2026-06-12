---
title: "WoW performance"
date: 2008-11-10
forum: Wine
---

### Post by uberlube on 2008-11-10
I just upgraded my cpu to an nvidia 8800, 4 gigs of ram and a new power supply. I assumed that i would have screaming performance as far as fps goes, and it does, but half the time it lingers at 9 to 17 fps. Is this normal or is there anything i can do to get the maximum performance out of my setup?

---

### Post by grazed on 2008-11-10
what type of cpu are you using? WoW depends somewhat heavily processor wise. you should also check the wattage of your power supply as well to make sure it can cover the new card.most prebuilt computers come with the lowest wattage psu they can get away with, so that may be your issue. 

also check to make sure the card is getting enough ventilation, that's also a common cause.

other than that, i'm not all that certain. might be a good idea to check performance on a windows partition if you have one. =/

---

### Post by arveeee on 2008-11-10
Try disabling Compiz and it's effects. System->Preferences->Appearance->Visual Effects-> None.

At least this made a huge difference on my Q3A performance.

---

### Post by uberlube on 2008-11-10
I have a AMD Athalon 64 7300. It is more than enough to run the game and also i have all the compiz setting turned off. I have used the ubuntu wow guild to set up the regedit file to use openGL as well. Any other suggestions?

---

### Post by uberlube on 2008-11-11
Also my power supply is more than enough for everything.

---

### Post by Neurasthenic on 2008-11-11
From the WoWWiki page: [http://www.wowwiki.com/Wine_(software](http://www.wowwiki.com/Wine_(software))

***_ Disabling pixel shaders_***

It seems since an early beta 3.0.2 patch, pixel shaders have been causing extreme troubles on nVidia cards:

    * [http://bugs.winehq.org/show_bug.cgi?id=15925](http://bugs.winehq.org/show_bug.cgi?id=15925)
    * [http://bugs.winehq.org/show_bug.cgi?id=15926](http://bugs.winehq.org/show_bug.cgi?id=15926)
    * [http://bugs.winehq.org/show_bug.cgi?id=15927](http://bugs.winehq.org/show_bug.cgi?id=15927) 

For a work around, open up winecfg, go to the Graphics tab and untick the box "Allow pixel shaders". You may see a significant performance gain. 




***_If you experience poor performance_***, graphical glitches, or the game doesn't run at all, then add the following options as well (to Config.wtf):

SET ffxDeath "0"
SET ffxGlow "0"
SET ffxSpecial "0"




Depending on your graphic card and drivers, WoW may or may not run out of the box. The following Config.wtf file sets a few important values which will make WoW run in an ideal, windowed, environment.

SET [[CVar gxApi|gxApi]] "opengl"
SET [[CVar gxCursor|gxCursor]] "0"
SET [[CVar gxFixLag|gxFixLag]] "0"
SET [[CVar gxResolution|gxResolution]] "1024x768"
SET [[CVar gxWindow|gxWindow]] "1"
SET [[CVar movie|movie]] "1"
SET [[CVar readEULA|readEULA]] "1"
SET [[CVar readScanning|readScanning]] "-1"
SET [[CVar readTOS|readTOS]] "1"
SET [[CVar Sound_OutputDriverName|Sound_OutputDriverName]] "System Default"
SET [[CVar Sound_VoiceChatInputDriverName|Sound_VoiceChatInputDriverName]] "System Default"
SET [[CVar Sound_VoiceChatOutputDriverName|Sound_VoiceChatOutputDriverName]] "System Default"
SET [[CVar videoOptionsVersion|videoOptionsVersion]] "1"




Give these a shot. You should probably look over that whole WoWWiki page, there's some useful stuff on there.

---

### Post by Cracauer on 2008-11-11
> **uberlube said:**
> I have a AMD Athalon 64 7300. It is more than enough to run the game and also i have all the compiz setting turned off. I have used the ubuntu wow guild to set up the regedit file to use openGL as well. Any other suggestions?

There's no such thing. I assume you mean a Athlon 64 3700, right? Since you have 4 GB RAM you have a 939 system, so you got a 2.2 GHz K8.

That's a lame duck that isn't capable of driving a 8800 GTX even in normal games and as people have pointed out, in WOW it's even worse and it takes a lot of CPU for itself.

Since DDR1 memory is about twice as expensive as DDR2 it would have been better to redirect some of the money for the memory torwards upgrading to a new mainboard and CPU using DDR2.

Maybe you should be a 2.6 or 2.8 GHz socket 939 CPU. But the only real kicker is a FX-57 which is still expensive.

---

### Post by Neurasthenic on 2008-11-11
> **Cracauer said:**
> There's no such thing. I assume you mean a Athlon 64 3700, right? Since you have 4 GB RAM you have a 939 system, so you got a 2.2 GHz K8.

That's a lame duck that isn't capable of driving a 8800 GTX even in normal games and as people have pointed out, in WOW it's even worse and it takes a lot of CPU for itself.

Since DDR1 memory is about twice as expensive as DDR2 it would have been better to redirect some of the money for the memory torwards upgrading to a new mainboard and CPU using DDR2.

Maybe you should be a 2.6 or 2.8 GHz socket 939 CPU. But the only real kicker is a FX-57 which is still expensive.
I'd say the limitation here is his configuration. Yes, he'll probably suffer quite a bottleneck with that processor. But WoW isn't very demanding, he should be running at framerates far higher than the low-teens.

---

### Post by Daedal on 2008-11-12
i don't know if it will help but try turning ground cluster density down in WoW's video settings.
i don't know if any updates in wine have changed the problem but the one setting used to cause my FPS to drop even below one.  

after setting everything up doing the regedit and adding opengl to the config.wtf i was still having problems and tried everything i could find. it kept happening anyway so in fear of having to boot into Vista everytime i wanted to play WoW i decided to test all of the in game settings one by one. just turning the one setting down actually stopped my problem.  i haven't turned it back up since but i play with every other setting at max and it's been running great.

---

### Post by Tea4all on 2008-11-12
Try Direct3D. It sometimes works better, in my case anyway!

---

### Post by Cracauer on 2008-11-13
> **Neurasthenic said:**
> I'd say the limitation here is his configuration. Yes, he'll probably suffer quite a bottleneck with that processor. But WoW isn't very demanding, he should be running at framerates far higher than the low-teens.

How? Even if he's using OpenGL (which we don't know), there's still a lot of translation going on. Definitely too much to feed a graphics card like that with a single core K8 at 2.2 GHz.

---

