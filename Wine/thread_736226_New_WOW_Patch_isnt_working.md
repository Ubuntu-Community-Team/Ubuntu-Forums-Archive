---
title: "New WOW Patch isnt working"
date: 2008-03-26
forum: Wine
---

### Post by byzantines2000 on 2008-03-26
I have Ubuntu 7.10. I downloaded the new WOW patch, and every time I get to the user-agreement, the game crashes. I have tried re-installing the game, and still no luck. If anyone wants to shed some light onto this, I would be more than grateful.

---

### Post by Resonance378 on 2008-03-26
Crashes HOW?

Locks up the pc?
Locks up the game?
Reports an error?  
Gives Wine output at the command line?

Last night I had to go and remove .mpq files with a 2 in their name.

So if there was a bill.mpq and a bill-2.mpq and the date was proper for the game upgrade on bill.mpq I deleted bill-2.mpq and that resolved crash type #153, #152, and #151 (as reported by the game client).

---

### Post by bdstetz on 2008-03-26
I am having trouble with WoW latest patch as well. Here is what I posted to the WoW forum and was told to take it the ubuntu community

This is the first post I have found for an issue with WoW, latest patched version 2.4, and Ubuntu 8.04. Ubuntu 8.04 is in beta so I would expect some issues, but not this. Please advise, help or forward. I posted this on another forum and was directed to this one. Hopefully I have supplied enough information for help.

Current set-up

Wow Latest Patch to 2.4 version
Ubuntu 8.04
Wine 0.9.58-ubuntu2
Directx 9.0c March 2008
Ati Radeon 1950 xtx
Amd x2 4600+
2 GB RAM
Asus A8R32-MVP
Raptor 78 gb

This set-up has worked on Ubuntu 7.10 and Wow 2.3, but is now not working for the 2.4 patch and Ubuntu 8.04

Problem Descriptions:

1) Initiate game. Start up Wow and the initial screen is displayed (provides options, play etc)
2) After play is depressed, no display. The screen is completely blank but the music plays.

3) Edit Config.wtf file. Set ffxGlow "0".
4) Initiate game. Starts up Wow and displays login screen with buttons BUT there are no graphics.
5) Enter Login. The character screen is displayed with the names of the characters, and buttons but no graphic of the character. That portion of the screen is empty
6) Enter World. Background scenery is displayed (i.e. grass, tress, rocks, etc) but no personal character and no other characters/monsters are displayed. Instead, black circles are shown where I assume characters/monsters would be standing.

Ok that's it. Does anyone have any suggestions? I am running with gxapi "opengl" since running Wow, via wine, in d3d6 mode causes WoW to crash on startup.

Thanks

---

### Post by Thoralex on 2008-03-27
> 1) Initiate game. Start up Wow and the initial screen is displayed (provides options, play etc)

I have to start wow.exe manually, the launcer just hangs.
> 2) After play is depressed, no display. The screen is completely blank but the music plays.

> **byzantines2000 said:**
> I have Ubuntu 7.10. I downloaded the new WOW patch, and every time I get to the user-agreement, the game crashes. I have tried re-installing the game, and still no luck. If anyone wants to shed some light onto this, I would be more than grateful.
I have the same problem, getting ERROR #132. ffxglow was already "0". I tried reinstalling a few times and discovered that 2.4 seems to work without BC, but when installing BC i get the same problem egain.
> 6) Enter World. Background scenery is displayed (i.e. grass, tress, rocks, etc) but no personal character and no other characters/monsters are displayed. Instead, black circles are shown where I assume characters/monsters would be standing.

I had that problem once, I can't remember how i solved it, but it was pretty simple.

Thanks if someone can help, keep in mind i'm not a very advanced user:)

---

### Post by Hairy_Palms on 2008-03-27
works fine here, but it wouldnt install till i had 3GB of free HD space, which was a bit of a pain in the ****.

---

### Post by Resonance378 on 2008-03-27
> **bdstetz said:**
> I am having trouble with WoW latest patch as well. Here is what I posted to the WoW forum and was told to take it the ubuntu community

This is the first post I have found for an issue with WoW, latest patched version 2.4, and Ubuntu 8.04. Ubuntu 8.04 is in beta so I would expect some issues, but not this. Please advise, help or forward. I posted this on another forum and was directed to this one. Hopefully I have supplied enough information for help.

Current set-up

Wow Latest Patch to 2.4 version
Ubuntu 8.04
Wine 0.9.58-ubuntu2
Directx 9.0c March 2008
Ati Radeon 1950 xtx
Amd x2 4600+
2 GB RAM
Asus A8R32-MVP
Raptor 78 gb

This set-up has worked on Ubuntu 7.10 and Wow 2.3, but is now not working for the 2.4 patch and Ubuntu 8.04

Problem Descriptions:

1) Initiate game. Start up Wow and the initial screen is displayed (provides options, play etc)
2) After play is depressed, no display. The screen is completely blank but the music plays.

3) Edit Config.wtf file. Set ffxGlow "0".
4) Initiate game. Starts up Wow and displays login screen with buttons BUT there are no graphics.
5) Enter Login. The character screen is displayed with the names of the characters, and buttons but no graphic of the character. That portion of the screen is empty
6) Enter World. Background scenery is displayed (i.e. grass, tress, rocks, etc) but no personal character and no other characters/monsters are displayed. Instead, black circles are shown where I assume characters/monsters would be standing.

Ok that's it. Does anyone have any suggestions? I am running with gxapi "opengl" since running Wow, via wine, in d3d6 mode causes WoW to crash on startup.

Thanks

*sigh* [http://www.wowwiki.com/Linux/Wine/Troubleshooting#ATI_no_Object_Textures.2FModels](http://www.wowwiki.com/Linux/Wine/Troubleshooting#ATI_no_Object_Textures.2FModels)

---

### Post by bdstetz on 2008-03-27
Thx for the update and link, resonance. I new it had to be something simple. Interesting though that the config file for WoW had not changed and, as far as I can tell, the ATI driver had not changed. Unless the latest version of Ubuntu 8.04 automatically installed a new ATI driver, I really cannot understand why it failed to work. However, I am glad that by setting the correct parameter it functions correctly.
BTW, do you have link to all the parameter settings for the config file in WoW?

---

### Post by byzantines2000 on 2008-03-27
Sorry to not be so specific, but my game crashes when I try to accept the user-agreement. The game just stops, and I get a crash message. I cannot remember what it is, and I un-installed WoW/cancelled my account. I might reinstall it with discs this time, but I don't think that will help me out much due to it working perfectly fine up until the accepting part everytime. But, it's worth a shot I guess...

---

### Post by MRiGnS on 2008-03-27
Try changing wine to winxp or win2k compatibility.

You can change that value via winecfg.

that did the trick for me.

---

### Post by rickggreen on 2008-03-28
I had the same problem after the WOW patch and latest Wine 58. All I did was change the dpi setting from 96 to 128 in the wine control panel. I am running the Heron beta, nvidia 8600.

---

