---
title: "HowTo: Install Diablo II on Kubuntu 6.10 using WINE 0.9.29"
date: 2007-01-14
forum: Wine
---

### Post by dynacrylic on 2007-01-14
**_THE-CATALYST's HowTo: Install Diablo II on Kubuntu 6.10 using WINE 0.9.29_**
[I]made: 2007/01/12 | last updated: 2007/01/14
written by: THE-CATALYST @ us-west bNet,  dynacrylic @ ubuntu forum[/I]

**===================================================================**

**UPDATED VERSION**

There is an updated version to this HowTo for Ubuntu 7.04 with completed parts on multi-keys, multi-windows, maphack and more information on botting on the Ubuntu forums at [http://ubuntuforums.org/showthread.php?t=443821](http://ubuntuforums.org/showthread.php?t=443821).
**===================================================================**


This guide/walk through/how to/set of instructions for a Kubuntu 6.10 user trying to install Diablo II using WINE, but I'm sure you could apply them to other Ubuntu flavors, or other linux flavors for that matter. I've also used these steps for installing War Craft III too. With that, here it is...


**Requirements**
	[LIST]
		[*]working PC running Kubuntu 6.10 with at least the minimum hardware requirements listed
		[*]internet access or the Diablo II Classic 1.11b patch and Diablo II Expansion 1.11b patch
		[*]Diablo II and Diablo II Expansion pack
		[*]working CD-Keys for Diablo II and Diablo II Expansion pack
		[*]*tasty frozen Italian margarita or rum and coke (providing you're legally allowed to drink) and some good listening music (I recommend Tool, King Crimson or DJ Shadow)*
	[/LIST]


**Downloading and Installing WINE**
I prefer using the Adept Manager to install packages. Download and install WINE by:
	[LIST=1] 
		[*]Go to K Menu > System > Adept Manager Manage Packages. Enter superuser password to continue.
		[*]Go to Adept > Manage Repositories.
		[*]Towards the bottom of the window in the New Repository text box, type ***deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) edgy main***, then click the "Add" button
		[*]Click "Apply"
		[*]Once the WINE repository is added, in the Search text box, type ***wine***.
		[*]Expand "wine" by clicking on the arrow.
		[*]Click "Request install".
		[*]Expand "libwine" by clicking on the arrow.
		[*]Click "Request install".
		[*]Towards the top of the window, click "Apply Changes"
		[*]Once Adept Manager is done installing WINE close the window.
	[/LIST]
Alternate instructions for installing [Wine on Ubuntu, Debian, and Debian-based distributions]("http://www.winehq.com/site/download-deb") may be of some help too. If you have problems installing WINE beyond this, I recommend posting on a forum, like the [Ubuntu forums]("http://www.ubuntuforums.org/index.php"), or consulting someone on the [WINEHQ]("irc://irc.freenode.net/#winehq") channel (server: irc.freenode.net, port: 6667 channel: #winehq).


**Installing Diablo II**
	[LIST=1]
		[*]Put your Diablo II Install CD in your cd/dvd drive
		[*]Wait for the KDE Daemon window and then click on "Open in new window". Note what media bay the CD is in.
		[*]Go to K Menu > System > Konsole Terminal Program.
		[*]In the shell (Konsole Terminal Program), find out what media bay your Diablo II cd is in. Type ***wine /media/cdrom[your drive number]/install.exe***. If you use the tab key it helps locate the path; by tabbing when at "wine /media/" you'll see the different drive numbers; by the "1" and hitting tab, hopefully you'll see a the files on the Diablo II cd. You can also get the drive number from the shortcut on your desktop.
		[*]When prompted with the Diablo II splash screen click through it. Click "Install Diablo II".
		[*]Click  "Full Version"- not single player or multiplayer.
		[*]Agree to the License Agreement and click "Agree".
		[*]Enter the name.
		[*]Enter your working 16 character Diablo II cd-key.
		[*]When prompted to choose install directory, leave it at the default (c:\Program Files\Diablo II). Click "OK".
		[*]Do not create a desktop shortcut to Diablo II. Click "No". 
		[*]Install should begin. When prompted "Please insert the CD labeled 'Play Disc'". Swap out the Install disc with the Play disc. 
		[*]Close the media bay tray.
		[*]Wait for the KDE Daemon window and then click on "Open in new window".
		[*]Close the new window that just opened up showing the Diablo II Play disk contents.
		[*]Click "Ok" in the Insert Disc install window. Your PC should continue to install Diablo II.
		[*]When prompted "Please insert the CD labeled 'Cinematics Disc'". Swap out the Play disc with the Cinematics disc. 
		[*]Close the media bay tray.
		[*]Wait for the KDE Daemon window and then click on "Open in new window".
		[*]Close the new window that just opened up showing the Diablo II Play disk contents.
		[*]Click "Ok" in the install window. Your PC should continue to install Diablo II.
		[*]When prompted "Please insert the CD labeled 'Install Disc". Swap out the Cinematic disc with the Install disc. 
		[*]Close the media bay tray.
		[*]Wait for the KDE Daemon window and then click on "Open in new window".
		[*]Close the new window that just opened up showing the Diablo II Play disk contents.
		[*]Click "Ok" in the install window. Your PC should continue to install Diablo II.
		[*]When prompted "Would you like to view the ReadMe now?", click "No".
		[*]When prompted with the Register Diablo II Electronically window, click "No". Do not register the game.
		[*]Click "Exit Installer". Close out until the Diablo II installation is done. Click "X" on the Diablo II installer window; do not close the WINE window.
		[*]Optional: You might get prompted with the "Diablo II Setup- Video Test", click "Cancel". Do not run the video/graphic card test at this time.
	[/LIST]


**Installing Diablo II patch**
	[LIST=1]
		[*]Go to [BattleNet]("http://www.blizzard.com/support/?id=msc0387p")
		[*]Download the Original Windows version 1.11b Upgrade Patch. Save it to your Desktop. Wait until the patch is completely downloaded before proceeding.
		[*]In your shell, type ***wine /home/[your username]/Desktop/D2Patch_111b.exe***. The WINE window should open and a progress bar should be moving.
		[*]When the patch is finished installing, click "Ok".
		[*]Note: If you get the "CD-ROM drive error" window, click "Cancel".
	[/LIST]


**Installing Diablo II Expansion**
	[LIST=1]
		[*]Put your Diablo II Expansion CD in your cd/dvd drive
		[*]Wait for the KDE Daemon window and then click on "Open in new window". Note what media bay the CD is in.
		[*]In the shell, find out what media bay your Diablo II cd is in. Type ***wine /media/cdrom[your drive number]/install.exe***. If you use the tab key it helps locate the path; by tabbing when at "wine /media/" you'll see the different drive numbers; by the "01" and hitting tab, hopefully you'll see a the files on the Diablo II Expansion cd.
		[*]When prompted with the Diablo II splash screen, click "Upgrade To Lord Of Destruction (800mb)".
		[*]Agree to the License Agreement and click "Agree".
		[*]Enter your working 16 character Diablo II Expansion cd-key, then click "Ok".
		[*]When prompted to create a desktop shortcut, select either "Yes" or "No"- your choice. 
		[*]Install should begin. When prompted "Please insert the Diablo II CD labeled 'Play Disc'". Swap out the Expansion cd with the Play cd. 
		[*]Close the media bay tray.
		[*]Wait for the KDE Daemon window and then click on "Open in new window".
		[*]Close the new window that just opened up showing the Diablo II Play disk contents.
		[*]Click "Ok" in the install window. Your PC should continue to install Diablo II Expansion.
		[*]When prompted "Please insert the Diablo II CD labeled 'Expansion Disc'". Swap out the Play cd with the Expansion cd. 
		[*]Close the media bay tray.
		[*]Wait for the KDE Daemon window and then click on "Open in new window".
		[*]Close the new window that just opened up showing the Diablo II Play disk contents.
		[*]Click "Ok" in the install window. Your PC should continue to install Diablo II.
		[*]When prompted "Would you like to view the ReadMe now?", click "No".
		[*]When prompted with the Register Diablo II: Lord of Destruction Electronically window, click "No". Do not register the game. Do not register the Game.
		[*]Click "Upgrade Installation" in the Diablo II: Lord of Destruction Setup window.
		[*]Click "Upgrade from Multi-player to Full".
		[*]Click "Exit Installer". The WINE window should close.
	[/LIST]


**Installing Diablo II Expansion patch**
	[LIST=1]
		[*]Go to [BattleNet]("http://www.blizzard.com/support/?id=msc0387p")
		[*]Download the Expansion Windows version 1.11b Upgrade Patch. Save it to your Desktop. Wait until the patch is completely downloaded before proceeding.
		[*]In your shell, type ***wine /home/[your username]/Desktop/LODPatch_111b.exe***.
		[*]When the patch is finished installing, click "Ok". The WINE window should close; if it does not close, close it.
	[/LIST]
		

**Running the Video Test**
	[LIST=1]
		[*]In your shell, type ***wine /home/[your username]/.wine/drive_c/Program\ Files/Diablo\ II/D2VidTst.exe***.
		[*]When prompted with the Diablo II Setup- Video Test, click "Run Test".
		[*]In the Video Test Complete window, click "Ok". Leave whatever radial option was set to. The WINE window should close.
	[/LIST]
		

**Minor Troubleshooting**
Ok, so let's test this out and possibly jump on BattleNet to pown some noobs (j/k I suck at pvp).
To start D2, go to K Menu > Lost Programs > Diablo II.  Hopefully, everything starts right up and works for you.  If not, here are some problems that I had.
	[LIST]
		[*]CD-missing
			I never really figured a work-around for this.  I just changed the method I installed Diablo II and such and the problem hasn't occurred since.			
		[*]Poor graphics
			In the shell, type ***winecfg***. In the Graphics tab, check "Emulate a virtual desktop". Depending on you resolution, set it to a standard size.
		[*]Poor Sound
			In the shell, type ***winecfg***. In the Audio tab, make sure ALSA Driver is the only one checked.
		[*]Laggy/jumping sound and graphics and jumpy/slow mouse control.
			After many attempts and conversations in the #winehq, I figured out a solution to this.  The video setting for the game were too high, thus causing pc to work overtime. Rerun the Diablo II video test and change the settings to a lower setting. Also in the shell, type ***winecfg***; in the Graphics tab, check "Emulate a virtual desktop". Depending on you resolution, set it to a standard size.		
	[/LIST]


**Getting D2Loader to work**
	[LIST=1]
		[*]Obtain a copy of D2Loader. I don't know where you can get a copy of it.
		[*]In your /home/[your username]/.wine/drive_c/Program Files/Diablo II/ directory, rename ***Diablo II.exe*** to ***Diablo II_orig.exe***.
		[*]Copy D2Loader into /home/[your username]/.wine/drive_c/Program Files/Diablo II/.
		[*]Rename D2Loader to ***Diablo II.exe***
	[/LIST]
		

**Playing Diablo II without a CD**
Requirements: D2Loader properly installed
	[LIST=1]
		[*]Copy d2xmusic.mpq from your Diablo II Expansion CD to /home/[your username]/.wine/drive_c/Program Files/Diablo II/ directory
	[/LIST]


**Playing Multiple instances of Diablo II**
*Still working on this- if it can be done...*


**Botting for Diablo II**
*I haven't tried any type of botting using WINE yet. I only know of D2JSP and mmBot- both are geared for Windows. Since D2JSP is detectable, and is the Devil, I have no intention or motivation to discuss it further. I have not tried mmBot using WINE yet...*


**===================================================================**

**UPDATED VERSION**

There is an updated version to this HowTo for Ubuntu 7.04 with completed parts on multi-keys, multi-windows, maphack and more information on botting on the Ubuntu forums at [http://ubuntuforums.org/showthread.php?t=443821](http://ubuntuforums.org/showthread.php?t=443821).
**===================================================================**


Please post suggestions to the guide and I'll try to incorporate them in.

Special thanks to all those in irc.freenode.net#winehq, especially vitamin, for all your patience helping me through the troubleshooting.  Hopefully this guide will help others the way you all helped me. 

And to all you D2 junkies out there that want to switch over to the Ubuntu family or for those that just want to play Diablo II on a flavor of Ubuntu, here you go. If anyone is ever on bNet shoot me a message; I'm THE-CATALYST @ us-west (sorry I don't play any other realms right now). l8 and gl -Erin.
*I forgot my pen...*

---

### Post by Choad on 2007-01-14
for me, it installed fine and patched its self in-game fine when i tried to go to battlenet.

the only thing you have to beware of is do not call

wine setup.exe

when the current directory is within the cd it's self otherwise you wont be able to eject the cd. (busy error)

but none the less im sure this will be of help to some people

---

### Post by fj4 on 2007-02-08
How does one install the Lord of Destruction patch 1.11b? The patch for the original game installed fine, but the LODPatch_111b.exe refuses to start. I get:
wine: could not load L"J:\\Desktop\\LODPatch_111b.exe": Bad EXE format for
It seems like there should be something after "for" but that's the end of the error message.
Help plz! :)

---

### Post by nystire on 2007-02-09
Try redownloading the file again. It sounds like maybe you got a corrupted copy.

---

### Post by DARKGuy on 2007-02-09
Nice HowTo, very explained and all, been wanting one like this for weeks (though I just copy it from a windows partition :P)

About opening multiple D2s... you can, just get D2Loader and it's just as simple as "wine Diablo\ II.exe" . It'll spawn as many as you want.

About MapHack, I can say it fully works, you just need d2hackit (for auto-loading modules, as WINE has problems with running MapHack standalone). Install it and copy all the MapHack files inside the "plugin" folder. Run d2hashgen.exe or whatever the file is for generating the MapHack hash using your original CDKey and rename D2maphack.dll to d2maphack.vcb. Run Diablo II, enjoy :)

---

### Post by dynacrylic on 2007-02-19
> **DARKGuy said:**
> 

About opening multiple D2s... you can, just get D2Loader and it's just as simple as "wine Diablo\ II.exe" . It'll spawn as many as you want.


But how do you inject the different CD-keys to tell loader which key set to use? That's where I got hung up. 

I know in windows you add "-mpq keyset1.mpq" to the shortcut, but how do I pass the same type of argument using WINE?

---

### Post by Xeora on 2007-02-19
I'm actually playing it again... I just copy and pasted from the windows (without getting the registry) and it come up in Open GL like that, works like a charm.

---

### Post by tyfn on 2007-04-12
hi everybody. I'm installed diablo II and started but I've major problem for vga, it's running like very old pc!!! anyone solve this problem?

---

### Post by dynacrylic on 2007-04-21
> **tyfn said:**
> hi everybody. I'm installed diablo II and started but I've major problem for vga, it's running like very old pc!!! anyone solve this problem?


What do you mean like "an old PC"?

Is the video jumping and slow?

---

### Post by philidox on 2007-05-07
> **DARKGuy said:**
> Nice HowTo, very explained and all, been wanting one like this for weeks (though I just copy it from a windows partition :P)

About opening multiple D2s... you can, just get D2Loader and it's just as simple as "wine Diablo\ II.exe" . It'll spawn as many as you want.

About MapHack, I can say it fully works, you just need d2hackit (for auto-loading modules, as WINE has problems with running MapHack standalone). Install it and copy all the MapHack files inside the "plugin" folder. Run d2hashgen.exe or whatever the file is for generating the MapHack hash using your original CDKey and rename D2maphack.dll to d2maphack.vcb. Run Diablo II, enjoy :)
I"m new to ubuntu in fact this is my first time using this forum.  I'm playing LOD on my ubunut computer but for the life of me I can't get the maphack working.  Please help me!!!  I"ve been trying for 2 months now with no luck very frustrated.  I got the d2 loader going though.  Could someone explain to me STEP BY STEP on how to get this maphack working with ubuntu.  Its my last job before I can say good bye to windows.  You said install the d2hackhit but how? Using wine, or is it standalone program.  And where are the plugin files located for the d2hackit program?  Remember I'm new so detailed instruction would be perfect.  Thanks

---

### Post by dynacrylic on 2007-05-11
> **philidox said:**
> I"m new to ubuntu in fact this is my first time using this forum.  I'm playing LOD on my ubunut computer but for the life of me I can't get the maphack working.  Please help me!!!  I"ve been trying for 2 months now with no luck very frustrated.  I got the d2 loader going though.  Could someone explain to me STEP BY STEP on how to get this maphack working with ubuntu.  Its my last job before I can say good bye to windows.  You said install the d2hackhit but how? Using wine, or is it standalone program.  And where are the plugin files located for the d2hackit program?  Remember I'm new so detailed instruction would be perfect.  Thanks

I don't use MH, but I'm guessing (and I mean only guessing) that this might work based on DARKGuy's post:

1) download d2hackit
2) install and copy all MH files inside "/home/[your username]/.wine/drive_c/Program\ Files/Diablo\ II/[plugin?]" directory
3) run "wine d2hashgen.exe" or "wine [whatever the file is for generating the MapHack hash using your original CDKey]"
4) rename D2maphack.dll to d2maphack.vcb

remember when you want to run most windows-based executables, run as "wine [name of file]"

---

### Post by DARKGuy on 2007-05-12
> **dynacrylic said:**
> I don't use MH, but I'm guessing (and I mean only guessing) that this might work based on DARKGuy's post:

1) download d2hackit
2) install and copy all MH files inside "/home/[your username]/.wine/drive_c/Program\ Files/Diablo\ II/[plugin?]" directory
3) run "wine d2hashgen.exe" or "wine [whatever the file is for generating the MapHack hash using your original CDKey]"
4) rename D2maphack.dll to d2maphack.vcb

remember when you want to run most windows-based executables, run as "wine [name of file]"

You got it right! ;)

---

### Post by dynacrylic on 2007-05-12
> **DARKGuy said:**
> You got it right! ;)

let me know what MH you were using and what extra things you might have had to do so I can enclose it in the main post

thanks

-erin

---

### Post by SubOne on 2007-08-10
I never could get map hack or the cd key filler to work. I've been using d2hackmap, but it won't work in wine for some reason. I have figured out how to get more than one to run though.

Copy your /home/user/.wine directory to /home/user/.wine2. Feel free to delete all the apps in Program Files for wine2 that you won't need duplicated if you have any installed. Install diablo and expansion as usual. Then install them again into wine2 by running this command:

env WINEPREFIX="/home/user/.wine2" wine "E:\SETUP.EXE"

Replace "user" with your user name and "E" with whatever your cd rom drive letter is in wine. Repeat the same command to install the expansion. When the "insert disk" dialog comes up behind the progress dialog just right click the task bar button for it and choose move to move it from behind the progress window. Patch up both installations remembering to run the "env" command above before running d2x for the second install.

After you are all patched up and have your d2loader installed and the d2xmusic.mpq & d2xvideo.mpq copied over test to make sure both installs work at the same time. Of course you have to have unique keys for each installation to play on bnet.

You can free up more space in wine2 by deleting all of the mpq files and putting links to the same files from your original wine directory. The files d2sfx.mpq and d2char.mpq seem to contain at least MY key data, but I'm not sure if that's always the case, so don't use a link for those. That way the second install will still run without the excessive space used up. I wouldn't worry about the other files. After the mpqs are replaced the d2 directory is only like 9mb.

---

### Post by loudnlownoma on 2007-08-17
First off - very nice guide, thorough and really helpful!  Have been using kubuntu and Wine for all of a day or so now, and walked right through the install fairly painlessly

> **dynacrylic said:**
> What do you mean like "an old PC"?

Is the video jumping and slow?

That's the problem I'm having.  D2 is installed.  Video test only gave one video option for direct draw HAL and the game loads okay, but once it gets to the menu and from there on, it's extremely sluggish, cursor jumps around, very choppy overall.  The video intro's in the beginning play great and I also have Starcraft running in Wine without trouble.  Using a no-cd patch with it, but does the same this way or with the CD in...  Any ideas?

---

### Post by DARKGuy on 2007-08-17
> **loudnlownoma said:**
> First off - very nice guide, thorough and really helpful!  Have been using kubuntu and Wine for all of a day or so now, and walked right through the install fairly painlessly



That's the problem I'm having.  D2 is installed.  Video test only gave one video option for direct draw HAL and the game loads okay, but once it gets to the menu and from there on, it's extremely sluggish, cursor jumps around, very choppy overall.  The video intro's in the beginning play great and I also have Starcraft running in Wine without trouble.  Using a no-cd patch with it, but does the same this way or with the CD in...  Any ideas?

What's your video card / CPU / RAM? what are your WINE settings? and the WINE version? does the video test pop up more options?

---

### Post by loudnlownoma on 2007-08-17
> **DARKGuy said:**
> What's your video card / CPU / RAM? what are your WINE settings? and the WINE version? does the video test pop up more options?

Using an HP Pavilion zd8000 series laptop - P4 2.8 GHz w/ HT, 1 GB RAM, ATI mobile video(can't remember exact model number but can find if needed, its a 128 MB dedicated card)

Wine 0.9.33 - Set to run in Windows 98, but have tried XP as well with the same results.  Graphics tab only has "Emulate a virutal desktop" option check, with 800x600 resolution.  Have tried different sizes, as well as removing that option with no luck.  The video test only has one option -Direct3D: DirectDraw HAL


Edit:  Sorry, I just realized I completely missed the beginning of the post saying that there was another install thread for 7.0.4...  That's the version of kubuntu I'm using and didn't realize there were separate threads...Should I repost over in that thread instead?

---

