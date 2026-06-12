---
title: "Can anyone run Battlefield 1942 under current ver of Wine?"
date: 2008-02-09
forum: Wine
---

### Post by BertP on 2008-02-09
The repository for Gutsy currently installs  Wine .946.  Has anyone gotten Battlefield 1942 to run under Wine .946 with Gutsy Gibbon?

alternatively:
At WineHQ,   Some comments in the app db  report platinum ratings for BF1942  under Gutsy Gibbon with Wine .952  or Wine .949.  Can anyone give instructions that a noob like me can understand for installing those versions of Wine?

all comments and suggestions are appreciated

---

### Post by GammaRay256 on 2008-02-10
I never really tried very hard to get Battlefield 1942 working through the Wine version in the repositories, so I don't know if it will work with that version; but I was able to install and run Battlefield 1492 flawlessly with Wine 0.9.52.

You can download a package to install Wine 0.9.52 on the [WineHQ .deb packages archive page.]("http://wine.budgetdedicated.com/archive/index.html")
Click on "Wine 0.9.52 i386" to download the .deb package; OR "Wine 0.9.52 amd64" (if you are running 64 bit).
Open a terminal window and remove your current wine install with:
sudo apt-get remove wine
Now double-click the downloaded .deb package from WineHQ and install it.

Next, configure wine by running:
winecfg

I've found everything seems to be a bit more reliable with the following configuration:
Go to the graphics tab and uncheck "Allow the window manager to control the windows".  Then check "Emulate a virtual desktop" and set "Desktop size" to 800 x 600.  (or anything you want depending on your screen resolution).

To install Battlefield 1942, insert the first installation disc, open a terminal and type:
wine 'd:\Setup.exe'
When you are prompted for the second disc, you can eject the current CD by opening a separate terminal and type:
wine eject d:

To run Battlefield 1942 when the install finishes, open a terminal and type:
wine ~/.wine/drive_c/Program\ Files/EA\ GAMES/Battlefield\ 1942/BF1942.exe

For me, everything seems to work fine, including the patches and mods for Battlefield 1942.
You can also change the graphics settings in winecfg and experiment to see what else works.

---

### Post by Ferrat on 2008-02-10
> **BertP said:**
> The repository for Gutsy currently installs  Wine .946.  Has anyone gotten Battlefield 1942 to run under Wine .946 with Gutsy Gibbon?

alternatively:
At WineHQ,   Some comments in the app db  report platinum ratings for BF1942  under Gutsy Gibbon with Wine .952  or Wine .949.  Can anyone give instructions that a noob like me can understand for installing those versions of Wine?

all comments and suggestions are appreciated

If you want to install them follow the link in my signature, that will help, it's an automated script for installing wine, it downloads the source and compiles it in to a .deb for easy install and removal

---

### Post by oskar2000 on 2008-02-10
Yes, apart from some glitches with the sound, it worked flawless. Well, the mouse-invert went crazy. I never installed it on windows, so I can't tell you if that's a linux thing. If you don't invert the mouse, you should be fine.

As far as I recall, I just started the installer, and then opened it through applications - wine. That was pretty much it.
Start the installer and the game from the command line, so you know what the error is if it crashes.

---

### Post by Cochise on 2008-02-10
to get the latest wine follow this:

[http://ubuntuforums.org/showthread.php?t=624644](http://ubuntuforums.org/showthread.php?t=624644)

---

### Post by BertP on 2008-02-10
Thanks GamaRay256.  I followed your instructions and have gotten it to play under some conditions but I am seeing some wierdness.

First on the strange list is that if I copy  your execution string and paste it to the terminal, it doesnt work BUT if  replace  "wine" with "cd" and cut off "BF1942.exe" from the end of the string,  I can successfully cd to the program directory and then next successfully run "wine BF1942.exe"....   Do you have any idea about why this is happenning?

This seems to work when I have Ubuntu resolution set to 800/600 and winecfg resolution set to 800/600.  but when I set Ubuntu to a higher res (1024x768) but leave wine in  800x600, the game comes up in a window and dies when the player is about to spawn.
here are the terminal messages:
-----------------------
{several pages of "found key" messages}
fixme:thread:NtQueryInformationThread Cannot get kerneltime or usertime of other threads
fixme:dinput:SysMouseAImpl_Acquire Clipping cursor to (0,0)-(800,600)
fixme:d3d_shader:vshader_set_limits Unrecognized vertex shader version 0
-----------

I have only one GB of memory so perhaps this is a memory issue?

when it worked, I tried playing Wake Island, single player cooperative mode; Gameplay seems fine, fips and sound seems fine.  the only problem is the top 10% of the text everywhere in the game is cut-off making it difficult but not impossible to read

Any ideas?   You have been a great help so I am going ahead and pressing your thanked button  ;-)

---

### Post by oskar2000 on 2008-02-10
> **BertP said:**
> First on the strange list is that if I copy  your execution string and paste it to the terminal, it doesnt work BUT if  replace  "wine" with "cd" and cut off "BF1942.exe" from the end of the string,  I can successfully cd to the program directory and then next successfully run "wine BF1942.exe"....   Do you have any idea about why this is happenning?
Did you copy the ~ too? It has to be an absolute path. 

> when it worked, I tried playing Wake Island, single player cooperative mode; Gameplay seems fine, fips and sound seems fine.  the only problem is the top 10% of the text everywhere in the game is cut-off making it difficult but not impossible to read

maybe you need to install the windows fonts. I don't know where I got them from... They might be included in the restricted-extras package.

---

### Post by GammaRay256 on 2008-02-10
I'm not sure about the screen resolution problems (I had them too (same error messages), I'm not sure what I did, but after playing around with the wine configurations, it eventually started working...); I seem to be able to run the game if I check "Allow the window manager to control the windows" and uncheck "Emulate a virtual desktop".  However, I've got some weird results sometimes, so I suggested that you try emulating a virtual desktop first...

As for the crashing when you spawn, I ran in to the same problem.  I seemed to be able to fix it by waiting a while to spawn.  I haven't been having the problem recently, but I was able to prevent it from crashing before by waiting about 20 seconds (or whatever the spawn time is set to) for the second spawn wave...

You may also want to check into downloading some of the Microsoft TrueType fonts... I'm not sure if they will help the problem with the text, but I had them installed before I installed the game and I don't have any problems with the text.  SourceForge has .exe files with the fonts on [this page]("http://sourceforge.net/project/showfiles.php?group_id=34153&package_id=56408").  You can just run the .exe files with Wine to install them.

---

### Post by BertP on 2008-02-11
I tried the true type fonts and even reinstalled BF1942 but it didn't help.  I kinda doubt that BF uses true type fonts anyway...  I remember from my Windows experience playing this game a couple of years ago that even when they're showing  correctly those fonts were never too easy on the eyes.

I went ahead and did the patch to 1.619   and now it works!  :-) 

  I see online that most of the servers appear dark;  Is 1.619 the latest patch or are all those  dark severs running a mod or some kind?. (I would kind of expect that now that the game is so old)

 I do wish,  however,  reading the text was easier....If so I could have been able to read why punkbuster just  kicked me off the server I was just playing    :p

-------

Well at least it's  playable now  and I will let you know if I figure out the text problem.

Thanks to everyone who generously  offered help!  you guys rock!

---

### Post by GammaRay256 on 2008-02-11
There is another patch to install after 1.6.19, 1.61, it is a small 6.4mb patch.  You can download it [here]("ftp://largedownloads.ea.com/pub/patches/battlefield_1942_incremental_patch_v1.6_to_v1.61b.exe").

Although I don't play online, I know most of the servers are running the DesertCombat mod (or one of the variations of DesertCombat).

---

