---
title: "How-To Gothic 2 under wine"
date: 2007-05-23
forum: Wine
---

### Post by lordhebe on 2007-05-23
This is my first how-to for the forums, so tell me whether it's good.

Gothic 2 is an Oblivion-esque Single player rpg, sporting a large world filled with hidden dangers and forgotten treasures. Battle against a swarming host of orcs, dragons and other mystical creatures. Experience three different character classes by selecting a career  in the militia, mercenary or sorcerer guilds. Use alchemy to create magical elements, like runes, scrolls and potions that you can use in you quest to fight evil. Gothic 2 has been working for a while with wine, with some tweaking. This guide explains what is necessary to get Gothic 2 working with wine 0.9.37.

**Step 1:** Install wine (Follow the steps on this guide, the exact area where it points :[https://help.ubuntu.com/community/Wine#head-c97ec1aafb204ea048a8139dd2ee466b2cdbb731]("https://help.ubuntu.com/community/Wine#head-c97ec1aafb204ea048a8139dd2ee466b2cdbb731"))

**Step 2:** Install Gothic. The installer works without problems on recent versions, so just start it by using the command ```
wine /path/to/dvdorcdrom/Autorun.exe
``` and select Install.

**Step 3:** Winecfg. Type ```
winecfg
``` into a terminal and click on the Audio tab. Use these settings:
```
ALSA driver= checked (Leave all else unchecked)
Hardware acceleration= Emulation
Default sample rate= 22050
Default bits per sample= 16
```

**Step 4:** Browse to you Gothic 2/System/ directory, and open Gothic.ini. find ```
playLogoVideos=1

; ... if set to 0 no intro logo videos will be played


```
and change it to: ```
playLogoVideos=0

; ... if set to 0 no intro logo videos will be played

```
This is not necessary, but it is highly recommended as the videos has terrible sound issues and are un-skip able. (Sound in movies are A LOT better with sound set on Emulation rather than full) The game's intro movie also has the same issues, but this cannot be disabled through the ini file (if anyone finds a way to do so tell me and I will add it to this guide) Some people may find that deleting or renaming the video file (in /_work/Data/) may work.

Then find ```
musicEnabled=1
```

and change it to ```
musicEnabled=0
```

This prevents a crash on the main menu, music in-game does not work unfortunately.

**Step 5:** Play the game! The game should now be working, but there may be fullscreen issues. If these occur, changing the games resolution to the one currently used by you OS in the options menu should solve it.

---

### Post by Swarms on 2007-05-23
Best rpg ever, should do this even if I would have played it through for the 5th time.

---

### Post by lordhebe on 2007-05-26
Yeah I love this game, I'm totally addicted to it right now (Pulling me away from WOW, at last) It's amazing how accessible this game is, considering how huge the world is. Okay so it's a shame that the beginning area of the game is very hard (With you coming across 3 goblins AND a bandit who wants you dead) but after that the game evens out. Once you get to the higher levels you start to really enjoy this game. It's fantastic, and wine support is really good right now. I would recommend this game to anyone who likes RPGs, especially the Elder Scrolls (Oblivion, Morrowind) It's also the perfect game to keep you going until better Oblivion support!

I have noticed a visual glitch in the sky, where half the sky is blank and just with a stock colour. In front of you there is a sort of cone, where beneath it you see the proper sky, and above it you see just a blank sky completely made up of one colour depending on the time of day. Looking directly up at the sky in third person allows you to see the whole sky, but looking down, or in first person mode the glitch still occurs. Don't know why this happens.

---

### Post by Jenda on 2007-07-03
Hmm... I'm getting an error: "Conflict: a hook process was found. Please deactivate all anti-virus and anti-trojan programs and debuggers. After clicking OK, it dies with:
> jenda@nienor:~/.wine/drive_c/Gothic1$ wine Autorun
fixme:wave:ALSA_AddCaptureDevice Add support for DSCapture
fixme:msg:pack_message msg 14 (WM_ERASEBKGND) not supported yet
fixme:msg:pack_message msg 14 (WM_ERASEBKGND) not supported yet
fixme:msg:pack_message msg 14 (WM_ERASEBKGND) not supported yet
[email]jenda@nienor:~/.wine[/email]/drive_c/Gothic1$ fixme:process:IsWow64Process (0xffffffff 0x174fea4) stub!
fixme:process:IsWow64Process (0xffffffff 0x174fea4) stub!


Anyone got a clue what to do with this?

---

### Post by lordhebe on 2007-07-04
You seem to be installing Gothic 1, so I'm sorry I wouldn't know. But try just running the setup program directly, instead of the autorun. It may help you bypass this problem.

---

### Post by Mjölner on 2008-02-10
Hello Lordhebe,

Thanks for this how-to! 
It's absolutely spot on and has also given me the first game that I can play in wine!

I had to setup Wine to run GothicII as windows 98.

I found though that I wasn`t able to see the life and mana bars at the bottom of the screen, (they where rendered offsreen) so I've changed my old CRT monitor to 1280x1024 and then use the widesreen game resolution to have the largest windowed surface area. Do you have any other suggestions?
As an extra: I used the ingame brightness, contrast and gamma controls, and after I shut Wine down my PC kept the game settings. Is this normal?

---

### Post by aestrivex on 2008-07-27
i can't make gothic II work and i've fiddled with it for rather a while.

i managed to fool it into installing correctly, so that's not the issue.  instead, the game crashes immediately following startup.  appDB and other people indicates that other people have it working very well.

running wine 1.1.0 on 64 bit ubuntu with GeForce 8800 (wine 1.1.1 messes up oblivion and other games, so i reverted back to 1.1.0 and will hold it there for the moment until the bug is fixed; probably until the next clean version).


i've tried everything in this thread and everything else i could find anywhere about getting this game to work in wine.

to anybody who has gothic II running: what are your specs and configurations, what version of wine are you running, and what other suggestions might you offer to get it to work.


possible things that i think might be wrong with it:

no DLL files were imported to make it run.  should i have?
edits that i made to the registry configuration to get oblivion to run might be messing up something.


thanks.

---

### Post by mriedel on 2009-02-16
Has anyone ever tried getting Gothic / Gothic 2 (same engine, it probably doesn't matter) to run in windowed mode under wine?

Fullscreen seems to work fine, but when i try using windowed mode (by modifying the ini file), i get a window that spans both my screen (no matter how small a resolution i choose in the ini file), showing garbage. I do hear sound though, so its entirely a display problem.

**[color=red]Edit:[/color]** Running Gothic II in a virtual desktop ("emulate virtual desktop" option in the wine config dialog) solved my problem. Gothic II itself being set to fullscreen mode of course. That also solved another multi-monitor problem I was having: When i opened documents (i.e. maps) in game, only half of them were shown. Apparently they were being scaled to fit my total dual monitor resolution (3360x1050) and then cut off to fit wine's display area, which was just my primary screen.

---

