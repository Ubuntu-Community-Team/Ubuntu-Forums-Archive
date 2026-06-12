---
title: "(HOW TO) you Want to play WoW on Intel cards with Wine in OpenGL mode? NO CRASHES!!"
date: 2011-07-08
forum: Wine
---

### Post by samuaz on 2011-07-08
I start describing my computer. is a white macbook 4.1, Core2Duo processor at 2.16 mhz, 320 gb hard drive, 4GB of RAM, and of course .... VIDEO CARD Integrated Intel GMA X3100 or I965. 

my macbook is good for work, surf the Internet, chat, etc, your video card is integrated and is not the best you have to play but of course I'm not a gamer, a game the only thing is need for speed, and of course World of Warcraft. 

in world of warcraft osx on this card gives a 5-10 fps, OSX sucks TO PLAY. 

windows do better emulating shaders via software gives 15-30 fps (30 in some enclosed places), with config.wtf configured with all the effects to a minimum 

ubuntu with wine .... the game in OpenGL mode with the patch rgl to take advantage of dual-core processor gives better fps in windows ..... 20-30 but then, within seconds of starting the game, wine and world of warcraft crash and closed because of missing libraries in the intel drivers !!... asking and asking for help from the friendly community of free software, all responded, "impossible is no way the current intel drivers have bad support for OpenGL" "intel cards are crap, buy another pc" and etc, etc. 

truth has yet to provide reason intellinuxgraphics best drivers for intel video cards and the card is not made to play .. but what I have, and I play World of Warcraft and other games are not very heavy. 

I gave up with those answers and I said I have to work!, compile wine from source, but nothing crashed Seguia opengl mode, set config.wtf, the windows registry in wine, but nothing worked to avoid the crasheo install intel drivers unstable forced me to reinstall the system ... 

when suddenly an idea occurred to me .... WORKED! wine and world of warcraft no more crashing in OpenGL mode! and FPS was playable 
in places where many people 10-15 fps (as Stormwind) 
indoors in the city 15-25 fps, 
in the open as the world fps 12/15-20 

if clear ... are not the best fps but at least the game is playable 

with rgl-patch for more fps, this improves, giving almost 10 fps more! 
but when compiling "wine 1.3.23.1" with the patch applied but I did crash in the read and write access to RAM memory, so I proceeded to uninstall and install wine from the ppa for Ubuntu, until the patch is somewhat most advanced. 

GOING TO THE SUBJECT IF THE RUN WORLD OF WARCRAFT, in "OPENGL" CON "WINE1.3" closes and hangs up, the solution is as simple Impressive clarify that I have the intel drivers that come with ubuntu 11.04. 

we will ours, if the run World of Warcraft in OpenGL mode with wine1.3, closes and hangs up, this is your solution is so simple that it is not thought as before!. 

1. install wine 1.3 from the ubuntu ppa 
2. install world of warcraft 
3. driconf install, sudo apt-get install driconf 
4. For wine does not hang and crash in OpenGL mode: open driconf, go to the tab "image quality" and activate the S3TC texture compression, even if the software support is not available. (Default is "no" change to "yes") 
5. play world of warcraft in wine 

1.1: install wine 1.3 from the ppa to: 

sudo apt-add-repository ppa: ubuntu-wine/ppa 

sudo apt-get update 

sudo apt-get install wine1.3 

2.1 Once installed world of warcraft and modifies the config.wtf in / World of Warcraft / wtf / config.wtf 
and add the line: 
SET gxApi "OpenGL" 

I leave my config.wtf optionally with optimizations to improve the performance of World of Warcraft with all the options to a minimum: 

SET Sound_OutputQuality "0" 
SET Sound_MusicVolume "0.40000000596046" 
SET Sound_AmbienceVolume "0.60000002384186" 
SET farclip "177" 
SET particleDensity "10" 
SET reflectionMode "0" 
SET baseMip "1" 
SET environmentDetail "50" 
SET weatherDensity "0" 
SET ffx "0" 
SET hwPCF "1" 
SET shadowlod "0" 
SET timingmethod "1" 
SET showshadow "0" 
SET showfootprints "0" 
SET showfootprintparticles "0" 
SET overridefarclip "0" 
SET horizonfarclip "1305" 
SET detailDoodadAlpha "0" 
SET groundeffectdist "1" 
SET smallcull "1" 
SET skycloudlod "1" 
SET characterAmbient "0" 
SET extshadowquality "0" 
SET ffxGlow "0" 
SET ffxDeath "0" 
SET gxApi "OpenGL" 
SET ProcessAffinityMask "3" 
SET gxTextureCacheSize "384" 

can also do this regedit tweak to improve fps as they say and avoid crashes [https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft) # regedit tweaks 

with this we would have to be able to play World of Warcraft in OpenGL mode intel video card, 

tested and running on Ubuntu 11.04 with wine 1.3.23 on my intel gma x3100! 

sorry for my english im speak spanish!

greetings and luck

---

### Post by biffster1 on 2011-10-09
> **samuaz said:**
> solution is so simple that it is not thought as before!. 

1. install wine 1.3 from the ubuntu ppa 
2. install world of warcraft 
3. driconf install, sudo apt-get install driconf 
4. For wine does not hang and crash in OpenGL mode: open driconf, go to the tab "image quality" and activate the S3TC texture compression, even if the software support is not available. (Default is "no" change to "yes") 
5. play world of warcraft in wine 



Dude, you are soooo amazing! I would kiss you if I could! This worked perfectly! I can now play WoW in OpenGL mode and it kicks  ***!

Muchas gracias!!!!!!!!

:popcorn:

---

### Post by Nuvielle on 2011-10-14
Could that work with an ATI Card too ? Last time a tried to run WoW with wine i ran into the same OpenGL Crashes so i think it would work maybe

Best Greets

---

### Post by akhil1988 on 2011-11-02
i did all as you said, still did not work for me :( i am using a core 2 duo, 2gb ram laptop with Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03). can you help?

---

### Post by yourtheman on 2012-01-03
I just created a account on these forums for the sole purpose of telling you how awesome you are and that I love you.
after reading all the intel not compatible or whatever threads out there i began to fear that i would be forced to use windows when ever i wanted to play wow but you fixed that, thank you very much.

---

### Post by Christo6 on 2012-05-08
I am new to Ubuntu and I can't figure out how to get to that tab in Driconf. It might be because it is a newer version. 

Some info:
Wine version: 1.4
Driconf version: 0.9.1-2ubuntu1
Ubuntu version: 12.04
Graphics Driver: VESA: Intel(r)Cantiga Graphics
Graphics Card: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)

When I open Driconf I get this message: "Could not detect any configurable direct-rendering capable devices. DRIconf will be started in expert mode."
It opens an interface with the options "revert", "New", "about" and "quit"
Any idea how to make it detect the graphics device or otherwise change the setting described in the first post?

---

### Post by aj2460 on 2012-07-21
Thank u  samuaz

after installing driconf and setting the property S3TC texture
i was able to play wow in openGl with my Intel board.

Thanks a million times.. :)

---

### Post by CrazyGangster on 2012-08-01
Well done samuaz.
You guys can also try install xorg-edgers for better graphics performance [https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)
:popcorn:

---

### Post by fixarg on 2013-03-11
Still works!!! 

Finally wow is running under my ubuntu 12.10-64

---

