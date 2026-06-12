---
title: "World of Warcraft screenshot + open thread"
date: 2007-07-18
forum: Wine
---

### Post by CrownP10:8 on 2007-07-18
Well to start things off here's a screen shot of WoW running in windowed mode on Ubuntu Feisty Fawn 7.04 (I disabled UI for the screen shot):

[IMG]http://i137.photobucket.com/albums/q204/linemandot/moonkin-ubuntu.png[/IMG]

Everything works perfectly in windowed mode, with better performance in fullscreen mode, with the exception of the things that are mentioned as non-working in the upstream Wine+WoW application documentation: 

[http://appdb.winehq.org/appview.php?iVersionId=6482](http://appdb.winehq.org/appview.php?iVersionId=6482)

The only problem I have encountered during normal usage is a crash when I attempt to change Video settings changes. This is documented in various sources, and is expected with this app under Wine since I'm running in OpenGL mode. The workaround is to edit video settings in WTF/Config.WTF manually (my preferred solution) or to run in Direct3D mode as described on the WoWWiki page:

[http://www.wowwiki.com/Linux/Wine](http://www.wowwiki.com/Linux/Wine)

If anyone is having trouble running WoW in Ubuntu, post here and let's see if we can fix your problem! Or if you just have a nice screenshot (preferably with Ubuntu in it too!) post that as well. :)

Also, here is the How-To for Ubuntu and WoW, please make sure you've read this in case it answers your question.

[https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft)

---

### Post by Nkari on 2007-07-18
Thats a good idea seems to be a lot of Broken WoW threads floating around at the moment.

I was amazed how easy it was to get it installed and updating correctly, my account needed more funds added after I finally got all the patches so I didn't get to play and see what the frame rates where like.

But the Little movies from both WoW and Burning crusade looked super sweet, nice and smooth. 

Then I went to play, it logged in all looked good, selected a character to use and discovered the progress bar on the splash screen didn't move at all and that is as far as I could get.

At this point I read more about setting it up and realised most people have more success Running in GL mode and how to set this in the WTF File. Tried that and it was worse, just got an error from WoW that my accelerator card was not supported and to get one with dual-tmu support (I think that is what is said).

Then I went back to D3D mode to see how else I could crash it, on the odd chance I just couldn't use my existing characters at that point in time.

Character creation seemed like as good a place as any. Tested the rotation of the character view, nice and smooth, tried changing hair and skin, all worked as expected, tried changing race and it crashed. Started again tried changing class, also crashed.

So basically this leaves me with non loading in GL Mode, or crashing on World loading in D3D mode.

I've got a pretty new machine, only built it a week or two ago it an Asus P5N32-E SLI motherboard with a Core2Duo E6600 in it, two 512M Nvidia 7600s in at and 2G of RAM, running the 64 version of feisty, latest Nvidia drivers, latest version of Wine.

Direct Rendering is on when I tested that at command line, GL Screensavers work, Gears works and spits out some silly big number in Frames Per Second.

In the WTF file I  have tried turning the Glow setting to off as this seemed to sometimes cause problems for some people.   

I must be mising something, I am thinking that it will need something like the Non-Loading trouble shooting tip for ATI cards, but it probably needs some sort of changing to make it more suitable for Nvidia Cards, not sure exactly what would be required here or how those entrys were even discovered.

Unfortunately I think this means I need to set up a windows partition so I can play until this gets figured out, because I'm pretty stuck now. 

Perhaps I need to crash the game some more to make some error logs for people that actually know what they mean.

---

### Post by DoktorSeven on 2007-07-18
Broken WoW seemed to happen to a lot of people after the latest Wine update; someone have a .deb of the last version of Wine?

Also, there could be a problem with certain graphics settings causing this; try tweaking Config.wtf (in WTF/ under your install directory).

Course it could be an unrelated or random issue, so who knows.  Just throwing in my ideas.

---

### Post by misfitpierce on 2007-07-18
I had no success editing anything with this game running on ATI Xpress 200... Game gets well over 40 FPS in windows on friends same laptop but through wine I scored maybe 8 FPS lol

---

### Post by CrownP10:8 on 2007-07-18
Nkari, can you post the contents of your Config.wtf? I've got only a single NVidia card, a GeForce 7600 2Go, but maybe I can look at my Config.wtf settings and note any differences there.

Also if you can launch WoW from a terminal window and paste the output here too, that might help...

---

### Post by Nkari on 2007-07-19
I'll paste that in when I get back on that machine after work, was trying to sort out a dualboot setup in the reverse order to how most people do it last night so I could play in the mean time, my guildmates are getting lonely without me being around.

A 2GO is likely a very different beast, if I'm not mistaken that is a mobile Nvidia chipset designation.

I'm sure I am having a fairly common problem, so figuring it out should help a lot of other people too.

---

### Post by xxrealmsxx on 2007-07-19
> **misfitpierce said:**
> I had no success editing anything with this game running on ATI Xpress 200... Game gets well over 40 FPS in windows on friends same laptop but through wine I scored maybe 8 FPS lol

The xpress 200 cards just have really really really bad performance in Opengl its not linux i'm afraid.

Try playing Quake 3 in windows and you will see what I mean.

At least thats my experience with the card in my laptop (Radeon 200m).

---

### Post by Nkari on 2007-07-19
Here is the contents of the WTF as it stands, not forcing GL because I get further without it.



SET hwDetect "0"
SET gxColorBits "24"
SET gxDepthBits "24"
SET gxResolution "1280x1024"
SET gxRefresh "59"
SET gxMultisampleQuality "0.000000"
SET gxFixLag "0"
SET fullAlpha "1"
SET doodadAnim "0"
SET lodDist "100.000000"
SET SmallCull "0.070000"
SET DistCull "450.000000"
SET trilinear "1"
SET frillDensity "12"
SET farclip "350.000000"
SET specular "1"
SET pixelShaders "1"
SET particleDensity "0.600000"
SET unitDrawDist "300.000000"
SET movie "0"
SET readTOS "1"
SET readEULA "1"
SET readScanning "-1"
SET readContest "-1"
SET locale "enUS"
SET expansionMovie "0"
SET realmList "us.logon.worldofwarcraft.com"
SET showToolsUI "1"
SET patchlist "us.version.worldofwarcraft.com"
SET realmName "Dath'Remar"
SET gameTip "19"
SET ffxGlow "0"

---

### Post by Nkari on 2007-07-19
If someone could tell me how to change directory via command line to a directory with a space in it (since WoW&#347; default pathhangs off C:\Program Files then I could run it from command line.

Would perhaps the logs that wine generates when it has a crash be useful?

---

### Post by Sandlst on 2007-07-19
> **Nkari said:**
> If someone could tell me how to change directory via command line to a directory with a space in it (since WoW&#347; default pathhangs off C:\Program Files then I could run it from command line.

Would perhaps the logs that wine generates when it has a crash be useful?

I'm not sure about the log, but in a terminal you can change directories with spaces in them by adding quotes like so:```
cd "~/.wine/drive_c/Program Files/"
```
If you haven't already, I would also edit the terminal profile (Edit/Current Profile/Title and Command) In order to make the terminal stay open after a command exits, or else it will probably close when wow crashes, which wouldn't be of much help!

---

### Post by RotoGrip on 2007-07-19
Hi all,

 Im unable to get past winecfg my computer locks up and i have to reboot. Crossover does the same thing.

p4 2.2
nvidia 5700le
1 gig ram

 glxgears gave me the following

'7221 frames in 5.0 seconds = 1444.000 FPS
8018 frames in 5.0 seconds = 1603.535 FPS
8252 frames in 5.0 seconds = 1650.260 FPS
8152 frames in 5.0 seconds = 1630.317 FPS

I am able to play games like sauerbraten, urban terror, and so on. But Wine is not playing nice when i try to install WOW

---

### Post by Nkari on 2007-07-19
Ok so I launched from command line, since it stays open trying to do something I could copy and paste.

Three were many lines of the following error prior to me atempting to enter the world:

err:d3d:IWineD3DSwapChainImpl_Present glXGetVideoSyncSGI failed(retval = 5



Right I tried to start with my character and the splash screen sort of just sat there this error popped up:

glx_texture_compression.c:58: __indirect_glGetCompressedTexImageARB: Assertion `image_bytes >= ((4 * reply.length) - 3)' failed.

Mean anything to anyone?

This is when GL mode is not selected as it gets further that way, GL command line errors to follow.

---

### Post by Nkari on 2007-07-19
Here is what the command line says when WoW is spitting out the error message about a non supported video acellerator, get one with Dual-TMU support.



fixme:wave:ALSA_AddCaptureDevice Add support for DSCapture
fixme:advapi:SetSecurityInfo stub
fixme:system:SystemParametersInfoW Unimplemented action: 112 (SPI_GETMOUSESPEED)
fixme:win:EnumDisplayDevicesW ((null),0,0x33edac,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f2d0,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f5b0,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f5a8,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f530,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f520,0x00000000), stub!
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
err:wgl:ConvertPixelFormatWGLtoGLX invalid iPixelFormat 0
fixme:win:EnumDisplayDevicesW ((null),0,0x33f008,0x00000000), stub!

---

### Post by cupps on 2007-07-20
I get almost the exact same text as the above poster when I launch WoW. I have an old ATI card that runs glxgears at 350-375 fps.

When I run WoW, it'll load the launcher, and then the opening video... and then it just closes. If I disable the movies, I get bupkis.

---

### Post by Nkari on 2007-07-20
Radically different hardware here, and I'm getting over 5000 fps in Gears, whatever that actually means

---

### Post by doomster on 2007-07-20
ive been playing wow since long time in ubuntu without any problems.
the only thing is i would like to use multiple sound sources ( listen to 
music / play wow/ use TS or ventrilo). when i use  aoss program, 
it seems to make some glitches , and unordinary cuts and noise to 
wow's sound.. anyone has had the same problem as me?

---

### Post by Nkari on 2007-07-20
I'll let you know if I ever get far enough to have said problem

---

### Post by uph0ria on 2007-07-21
Hey, I got WoW running great on Feisty today and have but one question... I would like to run WoW in Fullscreen mode without the bottom and top getting cut off, is that possible?

---

### Post by Nkari on 2007-07-21
you probably just need to set the correct resolution in your WTF file to make it look right.

---

### Post by Spot1234 on 2007-07-22
Ive got the choppy sound too so anything that people know would be apprecated, its a shame Ive got a dual boot system and I only got it running because I was board but now I see there are benefits to running in Linux over XP  no unexplained system slowdowns, its a lot easer to switch to a browser wile playing, really helpful if you need to look on thott for that elusive NPC. Have a look at this screenshot pretty impressive if you ask me.

---

### Post by Nkari on 2007-07-23
Well the Movies where nice and smooth for me under Ubuntu, but that could just be the new PC. 

I didn't think to watch them on the windows install I ended up having to make because my guild mates where getting lonely without me there to start random strange conversations.

---

### Post by Lux9698 on 2007-07-26
Hello Guys,

Sorry to make that Thread a spin more complicated.
But does one of you guys use Ventrilo with WoW,

If so, could you please, put here a step by step instruction ?

Btw, my WoW runs literally 10 times better and more stable over Ubuntu then on Micropoop XP.
No doubt it wasn't easy to configure, at least for me.



Hope, I hear something from you Forum.


Thanks

---

### Post by CrownP10:8 on 2007-08-01
There should be a sound option in Config.WTF, have you tried adjusting sound quality down? Sounds like a latency problem...

---

### Post by CrownP10:8 on 2007-08-01
> **Lux9698 said:**
> Hello Guys,

But does one of you guys use Ventrilo with WoW,

If so, could you please, put here a step by step instruction ?


I got everything working by following directions on this page (and linked from this page).

[http://wowwiki.com/Linux/Wine#Voice_Chat](http://wowwiki.com/Linux/Wine#Voice_Chat)

 I remember having to change a lot of settings in WineCFG and Ventrilo before everything worked just right, but it was just the same in WindowsXP! :lolflag:

---

### Post by madsmeg on 2007-08-15
Ok im stuck, got wow installed and get to character screen, when i try to log on, i get the loading screen with no loading bar, it waits for 5 mins then i get the wow error report and it closes, i dont have a config.wtf folder and i dont know how to create one. i have gone through so many posts and its just confusing me, if anyone can tell me how to create a config.wtf file in the wtf folder, im not sure if it would help but it would be a start.



if it helps here are PC Specs,

2gig ram
athlon 64 3400 ( i think)
2 x 7300GT's (newest Drivers)
hope someone can help, been without WoW for three days, cant lose my addiction now

Here is terminal stuff
```


fixme:advapi:SetSecurityInfo stub
fixme:system:SystemParametersInfoW Unimplemented action: 112 (SPI_GETMOUSESPEED)fixme:powrprof:DllMain (0x611a0000, 1, (nil)) not fully implemented
fixme:ntdll:NtPowerInformation Unimplemented NtPowerInformation action: 11
fixme:powrprof:DllMain (0x611a0000, 0, (nil)) not fully implemented
fixme:win:EnumDisplayDevicesW ((null),0,0x33edac,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f2d0,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f5b0,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f5a8,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f584,0x00000000), stub!
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)fixme:d3d:IWineD3DDeviceImpl_GetAvailableTextureMem (0x1753c8) : stub, simulating 64MB for now, returning 64MB left
fixme:d3d:IWineD3DDeviceImpl_CreateQuery (0x1753c8) Event query: Unimplemented,but pretending to be supported
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)err:wave:DSDB_MapBuffer Could not map sound device for direct access (Input/output error)
err:wave:DSDB_MapBuffer Please run winecfg, open "Audio" page and set
"Hardware Acceleration" to "Emulation".
err:wave:DSDB_MapBuffer Could not map sound device for direct access (Input/output error)
err:wave:DSDB_MapBuffer Please run winecfg, open "Audio" page and set
"Hardware Acceleration" to "Emulation".
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000):STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT not supported on protocol 4
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000):STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT not supported on protocol 4
fixme:reg:GetNativeSystemInfo (0x374026c4) using GetSystemInfo()
fixme:process:IsWow64Process (0xffffffff 0x61992524) stub!
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB
err:d3d_draw:blt_to_drawable Blitting surfaces from sysmem not supported yet
err:d3d_draw:blt_to_drawable Blitting surfaces from sysmem not supported yet
W.exe: glx_texture_compression.c:58: __indirect_glGetCompressedTexImageARB: Assertion `image_bytes >= ((4 * reply.length) - 3)' failed.
Killed

```

not sure if the code has anything to do with it, also would i be better intalling feisty?

i just installed 6.06 last night

---

### Post by Nkari on 2007-08-16
I think I have the same problem here but I am running 7.04,  with an Intel E6600 CPU and 2x 7600s.

It does that in in D3d Mode, and I think if you go into openGL mode it will tell also you that you need a card with dual TMU support.

Also if you try and make a new character it will sort of work to a point, changing any features like skin colour or hairstyle works, but as soon as you change race or  class it will crash however.

You will have the WTF file already there also. It is just hard to navigate to the WoW directory becasue part of the path to wine is hidden due to the . / 

I am just about to try pulling out one of my cards and see what happens to linux and wow there under

---

### Post by Nkari on 2007-08-16
Removing one card does not break linux, nor does it fix WoW. 

Back to working on getting the dualboot setup working for me I think.

---

### Post by rhenrick on 2007-08-16
I have a Dell Inspiron E1505 with Dual Core, 1GB RAM, and what ever video card it came with. I installed the latest version of WINE, setup a FAT32 partition to share between Windows and Ubuntu, and moved my WoW folder to that partition. I originally installed WoW on windows a while back, so this isn't clean installed into Linux.

When i start WoW, it looks fine up until i actually start playing. There isn't any sound, which doesn't bother me (i always turn sound off), but there is horrible lag!

Any idea what would cause this? It played perfectly on WinXP Pro.

---

### Post by Nkari on 2007-08-17
Are you running it in openGL or D3D. That, seems to make a big difference to those that can get it working

---

### Post by rhenrick on 2007-08-17
I do not know what that means, or how to find out, so i couldn't tell ya. Which is better to run in, and how do i do it?

---

### Post by Nkari on 2007-08-18
apparently it is far better under openGL, easiest way is to just edit the icon properties and after the last " leave one space and enter -opengl, I think it defaults to D3D

---

### Post by graigsmith on 2007-08-18
heres my druid making potions :)   i use an ati 9200 and have no problems with stability and it just works great.   however the 9200 is pretty slow. im just used to 10 fps alot of the time.  in instances it goes up to 20-30

---

### Post by Swarms on 2007-08-18
[http://www.wowinterface.com/downloads/info5202-ApplyToForehead.html](http://www.wowinterface.com/downloads/info5202-ApplyToForehead.html)

---

### Post by Pikestaff on 2007-09-07
Normally I play fullscreen but I took these in Windowed mode to show that I'm playing in Kubuntu Dapper!

Two screenshots, the first one showing you my decent FPS (it was actually hovering around 45 and dipped down during the screenshot) and the second showing the name of my pet, as an homage to the operating system I game on ;)

This character has been leveled from 1-47 exclusively on Linux and I fully intend on getting to 70 on Linux :p

AMD Athlon 64, 1022MB RAM, NVIDIA GeForce 6800 XT, and the latest version of Wine.

(apologies for the relatively small size and poor quality of the images)

---

### Post by derekr44 on 2007-09-07
You alliance heathen!  FOR THE HORDE!

[Pic here]("http://www.canofrags.com/guildvids/linux_wow.jpg")

---

### Post by hikaricore on 2007-09-07
:guitar:

---

### Post by derekr44 on 2007-09-07
9074 crit?  Very nice!

As prot spec, I've yet to break 4300.

---

### Post by hikaricore on 2007-09-07
> **derekr44 said:**
> 9074 crit?  Very nice!

As prot spec, I've yet to break 4300.

That may have been on a quest mob, I don't remember where the stat came from it's been a long time since I've played my rogue.
I guess she has decent equipment: [http://www.wowarmory.com/character-sheet.xml?r=Bronzebeard&n=Cloudskipper](http://www.wowarmory.com/character-sheet.xml?r=Bronzebeard&n=Cloudskipper)
along with my own custom build: [http://www.wowarmory.com/character-talents.xml?r=Bronzebeard&n=Cloudskipper](http://www.wowarmory.com/character-talents.xml?r=Bronzebeard&n=Cloudskipper)

I'm not really a full combat dps whore like most rogues.
I was pure sub until I fixed my spec after 2.0 screwed it all up.

---

### Post by derekr44 on 2007-09-07
I'm set deep Prot and almost ready for Karazhan.  Our small casual guild is just now getting attuned so we can try it out.

I'll post Armory when I get home, since it's blocked here at work.

---

### Post by derekr44 on 2007-09-07
[Armory](http://www.wowarmory.com/character-sheet.xml?r=The+Scryers&n=Corianton)

7/10/44 prot build
476 Defense

---

### Post by Norrbagge on 2007-10-06
heya all... My ubuntu forum virginity has been taken... Oh dear...

I decided last night, after having Ubuntu installed on my second computer for a while that i wanted to get completly rid of windows on my main computer... And yes, WoW has been my excuse for not uninstalling Win XP, later on Vista... I am very, very new to Ubuntu. so there is a ******** of things i dont understand anything off. beeing a windows user since way back... But Ubuntu seem to be a good choice for trying another way then the M$ way...

Now i have gotten it installed and its currently updating the patches... Now over to my questions, that i have tried to find answers for here on the forum:

First: short description off specs:
P4 3,00 Ghz
2Gig DDR2 RAM
XFX Geforce 6800GS 256Mb

1: i have only started it, logged in and when i did so, it just seemed to run so damn slow. it lagged (best english word i came up with) alot. I see alot here talking about running it in Open GL. But how do i change or check what its running in???

2: i cant play without addons, i see that people here is using it... do we install it in the regular way??? extracting it into the addon folder???

3: I have read that it crashes WoW changing the graphic settings in-game. do i have to change this in the  config file i have read about here??? where do i find this???

as said. i have tried to find good answers to this on the forum, but i havent found anything answering my question... 

Hope someone here can help me out...:)

EDIT1: As i understand many here play in windowed mode... Is that whats recomended or does it run like in windows in fullscreen mode too??? does it work to change this ingame or does all changes have to be done in the config file???

---

### Post by Sammi on 2007-10-06
@Norrbagge

I don't play WoW anymore, but I have been a maintainer of  the community WoW/Wine howto guide for some time now, so I have a few tips to give.

(Find the guide here: [http://ubuntuforums.org/showthread.php?t=312482](http://ubuntuforums.org/showthread.php?t=312482) )

Firstly I'm glad to tell you that your graphics card is pretty well support for Ubuntu. My system specs are very similar to yours, and WoW runs well in Wine for me. 
The vanilla graphics drivers in Feisty Fawn and Gutsy Gibbon should be fine, but if you would like to take your chances, then this little app is a fine choice to use for updating the driver: [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

Reply to questions:
1. Read all the tips in the guide to get the best results. OpenGL is recomended and it's explainded in the guide.

2. Addons are installed exactly as in Windows. Just place them in the addons folder. By default you will find you main WoW folder in "/home/<user>/.wine/drive_c/Program Files/World\ of Warcraft/"

3. I'm not 100% sure, but I've heard that this bug is gone in the newest version of Wine. Anyway there's is a workaround in the guide, so just use that if it doesn't work.

4. Should work fine in fullscreen mode with your graphics card.

---

### Post by Norrbagge on 2007-10-06
thanks for the reply... just got home now, so will try the guide...

BTW: tried to change settings in-game, and it crashed...  just to have said that. i might have been unlucky of course...

update will follow...


Update1:
Well... now everything works really well... i do notice a drop in FPS sometimes, that i didnt get when playing in windows. but it runs much better then expected... I have now installed compiz fusion and kibe-dock which dont run well with WoW. But if i turn both off it works as usual again... what i wondered if anyone could help me with is: is there any easy way of deactivating Compiz Fusion when turning on WoW??? Kibe-Dock is no problem. I just close it, then open it when i am done playing... It is Compiz Fusion i would like help with. The hard way is ofc a reboot. but i do hope it is some easier way that i dont know about... Any help is much appreciated :)

---

### Post by blackmars0 on 2007-10-08
Anyone tried running it on a laptop? 

I've got a 64mb onboard card, it runs in windows (although it looks like crap), so I thought I'd give it a shot in ubuntu... well... just look...

[IMG]http://img105.imageshack.us/img105/2351/screenshotxm0.png[/IMG]

I have it running on D3D, openGL is a LOT worse than that (looks like a really badly artifacting video card.)
My laptop is a LG LS50a, (1.7GHz, 1gb ram, 64mb onboard video).

Any ideas?

---

### Post by derekr44 on 2007-10-08
> **Norrbagge said:**
> is there any easy way of deactivating Compiz Fusion when turning on WoW???

I had this same problem with WoW running in full-screen mode.  This is what I have done...

I have a script that starts up Compiz (start_compiz.sh):
```
#!/bin/bash
compiz --replace &
sleep 5
emerald --replace
```

And a script to shut it off (stop_compiz.sh):
```
metacity --replace
```

Bear in mind that this is for Gnome, I'm not sure if it works for KDE.  But this allows me to manually turn on/off compiz when I want the eye candy and when I want to play WoW.

---

### Post by Jovec on 2007-10-08
Warsong Gulch action shot (1680x1050) under Ubuntu 7.04.  WoW runs smooth, with no real issues, including 164 Ace2 mods and libs.

---

### Post by Norrbagge on 2007-10-09
> **derekr44 said:**
> I had this same problem with WoW running in full-screen mode.  This is what I have done...

I have a script that starts up Compiz (start_compiz.sh):
```
#!/bin/bash
compiz --replace &
sleep 5
emerald --replace
```

And a script to shut it off (stop_compiz.sh):
```
metacity --replace
```

Bear in mind that this is for Gnome, I'm not sure if it works for KDE.  But this allows me to manually turn on/off compiz when I want the eye candy and when I want to play WoW.

Thanks alot... I will try this when i get home from work... I am running Ubuntu Feisty, which is Gnome right??? atleast it says gnome when i check the system menu... just wanted to check and see if i got it right...:-k


EDIT:1
Awesome... The commands work. Thanks for the help on  that :) ... But is there any way to make files, so i am able to run the start/stop_compiz.sh commands in terminal and i turn it on and off??? could somone please help me on that subject???

BTW: it seems that compiz - fusion aint running correctly when i try to turn it on again. Do i have to use " emerald --replace"??? i wonder since i am using compiz fusion and as far as i know, i aint using emerald. i have it installed though...

---

### Post by mithbuntu on 2007-10-16
Hey guys, I am having a problem with wow myself.

I believe all of my textures are not loading, but I don't know how to go about figuring out how to fix them.   Here are two pics to show you what's going on with my game once I open it up.

[http://img135.imageshack.us/img135/2067/wowss1ce9.png](http://img135.imageshack.us/img135/2067/wowss1ce9.png)



[http://img505.imageshack.us/img505/7406/screenshotzg2.png](http://img505.imageshack.us/img505/7406/screenshotzg2.png)


Any help is appreciated.

Graphics card: Radeon x1800xt
vid mode: OpenGL

---

### Post by mithbuntu on 2007-10-16
I switched to D3D with  SET ffxGlow "0" and it seems to run fine.

edit: ... or not.   I cannot see the World with D3D :(

[[IMG]http://img518.imageshack.us/img518/2103/screenshotnd8.th.png[/IMG]](http://img518.imageshack.us/my.php?image=screenshotnd8.png)

---

### Post by merlyn on 2007-10-18
Hi all,

here's my offering, with my newish character having recently installed Burning Crusade.

The only I would like to get happening now is full screen rather than windowed mode. Any suggestions / advice as such will be greatly appreciated.

Cheers.

---

### Post by spliner on 2007-10-19
The biggest problem I have had so far is slow load times when changing zones.  I have a 7800 and 2 gig ram and an x2 processor so it's not that.. runs fine in XP, loads are fast.  Just seems to thrash badly when entering new zones with lots of activity.  Might improve over time, only played it for a few minutes so far after 7.10 fresh install and wine install.  Will post more later this weekend.

---

### Post by Zypher on 2007-10-21
[[img]http://media-shack.net/thumbs/large/4843_nlmfy/screenshot.png[/img]](http://media-shack.net/view/full/4843_nlmfy)

d[-_-]b

still trying to get my Mic to work under Ventrilo but other than that, i have good fps on max settings.

7900GS - SLI

---

### Post by davebgimp on 2008-03-12
I run WoW on Ubuntu 7.10 with Wine on my Lenovo N100. The game flies, windowed or fullscreen (I prefer windowed so I can use Skype and Firefox easily), with graphics pumped pretty high.

WoW is definitely my  best Ubuntu + Wine + game experience.

---

### Post by Plisob on 2008-03-13
Ok, When I try to play WOW, it works pretty fine for a few minutes, then the computer fan is very activated, like it works alot, this happens when having many youtubes at the same time too. So, it works fine for a few minutes, then it hangs. The whole computer hangs, no response, have to restart it. No matter if I do it fullscreen or windowed.

My computer is 1024 mb ram, geforce 256mb graphic card. 

The sound is a bit laggy at the loading world screen as it hacks a litlle bit.

I have modified all the "SET" values like instructed and changed the key too.

wine version is 0.9.57

Graphics tab:  Mark in first two boxes.

 vertex shader support turned off 

120 dpi

pressing the "sound" tab take a few second to load, this may be part of the problem?  Alsa and OSS turned on

directsound hardware acceleration number 2 from bottom

44100   16

no driver emulation

windows version: xp

it has worked fine in some previous wine version

Here is my config.wtf, all naked, for you

SET locale "enGB"
SET coresDetected "1"
SET hwDetect "0"
SET gxColorBits "24"
SET gxDepthBits "24"
SET gxResolution "800x600"
SET gxRefresh "60"
SET gxMultisample "1"
SET gxMultisampleQuality "0.000000"
SET videoOptionsVersion "1"
SET movie "0"
SET expansionMovie "0"
SET readTOS "1"
SET readEULA "1"
SET readTerminationWithoutNotice "1"
SET showToolsUI "1"
SET Sound_OutputDriverName "System Default"
SET realmList "eu.logon.worldofwarcraft.com"
SET patchlist "eu.version.worldofwarcraft.com"
SET SmallCull "0.040000"
SET DistCull "500.000000"
SET farclip "477"
SET particleDensity "1.000000"
SET spellEffectLevel "0"
SET groundEffectDensity "24"
SET realmName "Hellscream"
SET gameTip "8"
SET Sound_VoiceChatInputDriverName "System Default"
SET Sound_VoiceChatOutputDriverName "System Default"
SET mouseSpeed "1.5"
SET Gamma "1.000000"
SET lastCharacterIndex "4"
SET Sound_MasterVolume "1"
SET Sound_SFXVolume "1"
SET Sound_MusicVolume "0.40000000596046"
SET Sound_AmbienceVolume "0.60000002384186"
SET lod "1"
SET Sound_SoundOutputSystem "1"
SET Sound_SoundBufferSize "150"
SET groundEffectDist "70"
SET ffxGlow "0"
SET ffxDeath "0"
SET cameraYawMoveSpeed "270"
SET cameraYawSmoothSpeed "90"
SET cameraSmoothStyle "0"
SET cameraSmoothTrackingStyle "0"
SET cameraDistanceMaxFactor "2"
SET AutoInteract "1"
SET minimapZoom "0"
SET uiScale "1"
SET deselectOnClick "0"
SET assistAttack "1"
SET stopAutoAttackOnTargetChange "1"
SET autoSelfCast "1"
SET shadowLOD "0"
SET SoundOutputSystem "1"
SET SoundBufferSize "150"
SET gxApi "OpenGL"

Plz help :popcorn:

---

### Post by Resonance378 on 2008-03-13
Please don't cross post Plisob

---

