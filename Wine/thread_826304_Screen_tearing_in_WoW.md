---
title: "Screen tearing in WoW"
date: 2008-06-11
forum: Wine
---

### Post by kamasabi on 2008-06-11
I've come across a rather annoying little issue after finally getting WoW installed.  Once I spawn in game at the very beginning of the game, it seems to run fine, I can run around and kill some of those little ogres or whatever just fine.  However, whenever I go inside the castle, my game goes completely on the fritz.  Here is a picture of what I am talking about.

[[IMG]http://img505.imageshack.us/img505/6338/screenshotcb2.th.png[/IMG]](http://img505.imageshack.us/my.php?image=screenshotcb2.png)

here is also a copy of my config.wtf.  Anyone have any ideas of how to fix this?  Like said, it doesn't happen when I'm outside, it only happens when I go inside the castle, however, if I go back outside after going in the castle, it still happens.  Also, text doesn't appear when I talk to the captain.

```
SET readTOS "1"
SET readEULA "1"
SET readScanning "-1"
SET readContest "-1"
SET locale "enGB"
SET gxApi "opengl"
SET hwDetect "0"
SET gxColorBits "24"
SET gxDepthBits "24"
SET gxResolution "800x600"
SET gxRefresh "60"
SET gxMultisampleQuality "0.000000"
SET gxFixLag "0"
SET fullAlpha "1"
SET SmallCull "0.070000"
SET DistCull "500.000000"
SET trilinear "1"
SET frillDensity "24"
SET farclip "177"
SET specular "1"
SET pixelShaders "1"
SET particleDensity "1.000000"
SET unitDrawDist "300.000000"
SET movie "0"
SET expansionMovie "0"
SET realmlist "logon.wowscape.net"
SET ffxDeath "0"
SET ffxGlow "0"
SET M2UseShaders "0"
SET gxWindow "1"
SET readTerminationWithoutNotice "1"
SET coresDetected "1"
SET videoOptionsVersion "1"
SET showToolsUI "1"
SET Sound_OutputDriverName "System Default"
SET gxCursor "0"
SET textureFilteringMode "0"
SET Gamma "1.000000"
SET Sound_VoiceChatInputDriverName "System Default"
SET Sound_VoiceChatOutputDriverName "System Default"
SET baseMip "1"
SET spellEffectLevel "0"
SET groundEffectDist "70"
SET weatherDensity "0"
SET cameraPitchMoveSpeed "90"
SET cameraPitchSmoothSpeed "45"
SET gameTip "5"
SET uiScale "1"
SET realmName "WoWcrack (Blizz High-Rate)"
```

Thanks,

Kama

---

### Post by kamasabi on 2008-06-11
anyone?

---

### Post by Sleaka J on 2008-06-12
Is this the legit retail version of WoW or a private server you're trying to run?

SET realmName "WoWcrack (Blizz High-Rate)" would indicate private server and you won't get help for a non-legit version as most have some sort of issue when running.

---

### Post by thisismalhotra on 2008-06-12
> **kamasabi said:**
> anyone?

MKost likely its and Ati card you are using and this is been a known issue for a while ... I have tried many things did not work for me but same things have worked for others. First of all try turning compiz off ... or else try this link ...

Hey what the Deal with WoWCrack we dont support keycrackers etc etc here lol


[http://ubuntuforums.org/showthread.php?t=770939](http://ubuntuforums.org/showthread.php?t=770939)

---

### Post by takumidesh on 2008-06-12
Wowcrack is a private server not a keycrack, that is just the name.

---

### Post by kamasabi on 2008-06-13
> **takumidesh said:**
> Wowcrack is a private server not a keycrack, that is just the name.

^that

It is a legitimate version, however I go on this server from time to time for the epic leveling and having some fun with friends.  *look at realmlist*

Anyway, I finally wound up using the registry fix (tried the second time and it worked?) and it fixed about 90% of the problems....minimap freaks when I go inside and it crashed once when I went to the world map, but otherwise it seems to be working fine.

---

### Post by thisismalhotra on 2008-06-13
> **kamasabi said:**
> ^that

It is a legitimate version, however I go on this server from time to time for the epic leveling and having some fun with friends.  *look at realmlist*

Anyway, I finally wound up using the registry fix (tried the second time and it worked?) and it fixed about 90% of the problems....minimap freaks when I go inside and it crashed once when I went to the world map, but otherwise it seems to be working fine.

There is a linux minimap addon which did save me from that trouble?? Google it...

---

