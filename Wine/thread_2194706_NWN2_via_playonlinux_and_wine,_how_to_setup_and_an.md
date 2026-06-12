---
title: "NWN2 via playonlinux and wine, how to setup and an issue with kaedrins prc"
date: 2013-12-20
forum: Wine
---

### Post by vanquishedangel on 2013-12-20
Here is the email I sent to kaedrin, author or kaedrins prc pack. This email tells you how to set up playonlux wine and gives some useful Ideas but I am posting this incase anyone knows why the prc pack isnt working.

Hi

I hope you dont mind this but I am hopeing you may be able to help me out with this issue. I cannot seem to log into the sites with the ability to make a bug report so I will write to you.

I am actually using a merge pack with your work in it from the vault, but when I download from here the issue persists.

First things first, my system:

HP dc 5750
CPU:         AMD Athalon x2 64bit 3.0 ghx (89 watt version)
RAM:         8 gigs ram
Graphics: Power color Radeon HD 7750
OS:            Ubuntu 13.10 64bit (I do have windows, but I hate it)

I use wine (version 1.5.27) along with playonlinux (has a testing script to install from disks or from GOG) to simulate windows xp, I have installed directx 9, direct x10, and directx 11, also vcrun 2005 and 2008. I have also used devendum.dll and dxdiag.ll set to native in winecfg.  I also have gdi and gdi plus installed but they are not needed for nwn2. here is the set up for my winereg:

[HKEY_CURRENT_USER\Software\Wine\Direct3D]
"DirectDrawRenderer"="opengl"
"OffscreenRenderingMode"="fbo"
"PixelShaderMode"="enabled"                          (pixel shaders)
"RenderTargetLockMode"="auto"                     (?)
"UseGLSL"="enabled"                                        (light shaders)
"VertexShaderMode"="hardware"                    (shaders to use grfx card))
"VideoDescription"="ATI Radeon HD 7750" (decription for games that need it)
"VideoDriver"="ati2dvag.dll"                             (Driver for ati cards)
"VideoMemorySize"="1024"                            (Video Ram)
"VideoPCIDeviceID"="dword:0000683f"       (This is card specific)
"VideoPCIVendorID"="dword:00001002"    (this is ATI's vendor ID, its for all ati cards)

Unless you use linux I dont really expect you to know what all the above is but incase you do, you might spot an issue, this set up works flawlessly for the vanilla campaign (incase you come across a linux user that needs help, or want to post it to a forum)

The issue is that when I make the last hit on the first shadow reaver in the swamp the game crashes, it does the same with the gargoyles near ammon jerro's haven and the greater shadows with the first reaver as well. This breaks the game for me, and that sucks because I wouldnt even play it without your prc pack. I have worked it down to what file seems to be causing the issue, this file is classes.2da. When I remove this file the game works great, except no fun classes. The debugger in playonlinux gave an error about  shaders, but many errors given have nothing to do with the crash. Here is what I have done to try to fix the issue:

1. I have installed a dirext x 10 patch for xp, I think it is really a wrapper to convert direct x 10 calls to opengl, from here: (this was to try to fix the crashing, wasnt applied previously)

[http://www.softpedia.com/get/System/OS-Enhancements/DirectX-10-for-Windows-XP.shtml](http://www.softpedia.com/get/System/OS-Enhancements/DirectX-10-for-Windows-XP.shtml)

2. I also installed full direct x 9 (available from playonlinux, same with direct x 10 and direct x 11 dll's, vcrun 2005, vcrun 2008, devendum.dll, gdi, gdi + etc.) This made the shader error go away but game still crashes.

3. I tried enabeling/disabeling different graphic settings to no avail.

4. I also added the lines under game options and server options in nwn2player.ini, albiet after I was playing and and I was crashing at the first shadow reaver:

Enforce Legal Characters=0
Single Player ItemLevelRestrictions=0
Single Player Enforce Legal Characters=0

I am hopeing you get this and maybe can see what is in common with the shadow reaver, greater shadow, and the gargoyles near ammon jerros tower, that are ivolved with your classes.2da file, or maybe they all have a leagal characters check? Do i have to replay my saved games after installing your pack? or useing the leagal charaters option?

Sorry for the long post but I like to be detailed, Thank you for your time and the best content made for nwn2!

here is a link to the merge I was useing but i also tried yours here from nexusmods.com (with a clean folder):

[http://nwvault.ign.com/View.php?view=NWN2HakpaksCombined.Detail&id=58](http://nwvault.ign.com/View.php?view=NWN2HakpaksCombined.Detail&id=58)

---

