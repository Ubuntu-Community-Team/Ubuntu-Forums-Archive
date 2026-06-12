---
title: "WoW missing terrain and buttons"
date: 2008-07-24
forum: Wine
---

### Post by Hurrz88 on 2008-07-24
I just installed WoW on my dual booted machine on the Windows side and am running it in Wine on Hardy. Everything seemed fine until I loaded into the world and the terrain was missing and my buttons were freaking out. I have a couple of screen shots if anyone could check them out and see what is going on. I changed my WTF file to whatever it says to change it to on the WoW install forums, but nothing seems to help. [IMG]http://i80.photobucket.com/albums/j168/Hurrz_88/WoW_Terrain.png[/IMG][IMG]http://i80.photobucket.com/albums/j168/Hurrz_88/Screenshot.png[/IMG]

---

### Post by Mahinva on 2008-07-24
From your second screenshot, I see that the minimap is whited out when indoors. From what I've learned through reading these forums, that is a problem with your ATI video card. I'm not sure if the white minimap occurs for all ATI users, or if it depends on your video card and corresponding driver. I read somewhere that ATI was aware of this particular bug and was working on a fix. However, I am not sure if a fix has been implemented in a driver yet. So for the minimap, unless someone says there's been a fix for it, you'll have a white minimap while indoors (or in instances).

As for the textures, I (a nVidia user) had my outdoor ground textures look like your first screenshot if I did not have the following line in my Config.wtf:

SET gxApi "openGL".

Depending on the instructions you've followed, you may or may not have already set that line to "openGL". "d3d" (Direct 3D) mode tends to give better fps and allow for hardware cursor, but can mess up textures.

Have you followed [https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft) by any chance? You say you've followed everything on the WoW install forums, but that link isn't a forum.

I think an ATI user or someone who knows more about ATI and WoW would be able to help you further than what I can offer.

---

### Post by Hurrz88 on 2008-07-24
Well I am playing on a Dell E1505 laptop with Intel 945 graphics card, suckky I know, so I don't have ATI. I changed the WTF file to openGL but it still has the problem. Here is the list that is in the Config.wtf file

SET readTOS "1"
SET readEULA "1"
SET readScanning "-1"
SET readContest "-1"
SET locale "enUS"
SET hwDetect "0"
SET gxColorBits "24"
SET gxDepthBits "24"
SET gxResolution "1280x800"
SET gxRefresh "60"
SET gxMultisampleQuality "0.000000"
SET gxFixLag "0"
SET doodadAnim "0"
SET SmallCull "0.010000"
SET DistCull "350.000000"
SET MaxLights "1"
SET frillDensity "8"
SET farclip "237"
SET particleDensity "0.400000"
SET baseMip "1"
SET movie "0"
SET expansionMovie "0"
SET realmList "us.logon.worldofwarcraft.com"
SET readTerminationWithoutNotice "-1"
SET coresDetected "2"
SET videoOptionsVersion "1"
SET pixelShaders "1"
SET showToolsUI "1"
SET Sound_OutputDriverName "System Default"
SET patchlist "us.version.worldofwarcraft.com"
SET spellEffectLevel "6"
SET accountName "hurrz88"
SET Gamma "1.000000"
SET Sound_VoiceChatInputDriverName "System Default"
SET Sound_VoiceChatOutputDriverName "System Default"
SET groundEffectDist "70"
SET realmName "Korialstrasz"
SET cameraPitchMoveSpeed "90"
SET cameraPitchSmoothSpeed "45"
SET gameTip "5"
SET uiScale "1"
SET gxApi "openGL"
SET ffxDeath "0"
SET M2UseShaders "0"
SET ffxGlow "0"
SET gxWindow "1"
SET gxCursor "0"
SET DesktopGamma "1"
SET SoundOutputSystem "1"
SET SoundBufferSize "150"

---

### Post by Shadowhack on 2008-07-24
add

SET UIFaster "2" for the messed up icons

---

### Post by Mahinva on 2008-07-25
> **Hurrz88 said:**
> Well I am playing on a Dell E1505 laptop with Intel 945 graphics card, suckky I know, so I don't have ATI. I changed the WTF file to openGL but it still has the problem. Here is the list that is in the Config.wtf file

[snip]



I really have no guess as to why your minimap is white; I had only ever heard of that being a ATI problem.

I'm sorry my suggestions weren't of much help.

I am curious if the line Shadowhack suggests will also fix your minimap.

---

### Post by tye959 on 2008-07-25
Hmm well maybe you should reinstall the games? Thats the only suggestion I know of. It could be the game...

---

### Post by Shadowhack on 2008-07-25
well i got that from wowwiki and for me it only fixes icons and nothing else and i get a white minimap inside building but not outdoors

---

### Post by Zhiro on 2008-08-25
I have a Dell XPS M1330 that I'm running it on with an Intel card and I also had the white minimap thing and corrupt button images.  I added the line:

SET UIFaster "2"

like Shadow said, and that fixed the button images right away.  As far as the white minimap, I haven't found a fix for that yet, but I've been trying to get WoW working for a while now, so I was just happy that I had text and buttons and it wasn't crashing, haha.

I still do have some terrain problems I haven't had fixes for yet, such as no terrain (just black empty space) or incomplete terrain (there are colors and shades but not the finished product).  If anyone knows how I can fix those, please let me know! =)

---

### Post by ooobuntooo on 2008-08-26
The minimap is white for me :(

---

### Post by ooobuntooo on 2008-08-26
> **tye959 said:**
> Hmm well maybe you should reinstall the games? **Thats the only suggestion I know of.** It could be the game...

If you don't know what your talking about the please don't post anything.
I had the same problem and *SET UIFaster "2"* solved the problem!

---

### Post by intwaid on 2008-09-14
I'm having the same problem for the white terrain. 

but i had recently re-wiped my HDD to try and dual-boot with windows for my games, and ubuntu for my work. nonetheless, i had everything working before that mal-initiated idea. so if anyone has ideas, send em out?

---

### Post by Eviljim on 2008-09-15
The white minimap is a known Ati driver bug.

See here [http://ubuntuforums.org/showthread.php?t=720625]("http://ubuntuforums.org/showthread.php?t=720625")

A quick check via google also indicates the Intel 945 chip (intel GMA950) also have problems with OpenGl and pBuffers.

Hope that helps.

---

### Post by brookswm on 2008-09-25
> **Zhiro said:**
> I still do have some terrain problems I haven't had fixes for yet, such as no terrain (just black empty space) or incomplete terrain (there are colors and shades but not the finished product).

I'm having the incomplete terrain problem as well, I have an nvidia card.  It's not every texture, but most outdoor ground textures are just really basic, there will be no road or distinguishing features.  I dont have the problem with buildings or with the instances I've been in.

---

