---
title: "HowTo: Install Diablo II on Ubuntu 7.04 Feisty Fawn using WINE 0.9.37"
date: 2007-05-14
forum: Wine
---

### Post by dynacrylic on 2007-05-14
**_THE-CATALYST's HowTo: Install Diablo II on Ubuntu 7.04 Feisty Fawn using WINE 0.9.37_**
[I]original made 2007/01/12 for Kubuntu 6.10: [http://ubuntuforums.org/showthread.php?t=338542](http://ubuntuforums.org/showthread.php?t=338542) | last updated: 2007/05/14
written by: THE-CATALYST @ us-west bNet,  dynacrylic @ ubuntu forum[/I]

This guide/walk through/how to/set of instructions is for a Ubuntu 7.04 (Feisty Fawn) user trying to install Diablo II using WINE, but I'm sure you could apply them to other Ubuntu flavors, or other Linux flavors for that matter. I've also used these steps for installing War Craft III too. With that, here it is...

**Requirements**
	[LIST]
		[*]working PC running Ubuntu 7.04 with at least the minimum hardware requirements listed
		[*]internet access or the Diablo II Expansion 1.11b patch
		[*]Diablo II and Diablo II Expansion pack
		[*]working CD-Keys for Diablo II and Diablo II Expansion pack
		[*]*tasty frozen Italian margarita or rum and coke (providing you're legally allowed to drink) and some good listening music (I recommend Tool, King Crimson, Amon Tobin or DJ Shadow)*
	[/LIST]

**Downloading and Installing WINE**
I prefer using the shell to install packages. Download and install WINE by:
	[LIST=1] 
		[*]Go to Applications > Accessories > Terminal
		[*]Add the repository's key to your system's list of trusted APT keys by typing:
			```
wget -q http://wine.budgetdedicated.com/apt/387EE263.gpg -O- | sudo apt-key add -
``` 
		[*]Add the repository to your system's list of APT sources by typing:
			```
sudo wget http://wine.budgetdedicated.com/apt/sources.list.d/feisty.list -O /etc/apt/sources.list.d/winehq.list
```
		[*]Update apt-get by typing
			```
sudo apt-get update
```
		[*]Install Wine by typing
			```
sudo apt-get install wine
```
	[/LIST]
Instructions for installing [Wine on Ubuntu, Debian, and Debian-based distributions]("http://www.winehq.org/site/download-deb") may be of some help too. If you have problems installing WINE beyond this, I recommend posting on a forum, like the [Ubuntu forums]("http://www.ubuntuforums.org/index.php"), or consulting someone on the [WINEHQ]("irc://irc.freenode.net/#winehq") channel (server: irc.freenode.net, port: 6667 channel: #winehq).

**Installing Diablo II**
	[LIST=1]
		[*]Put your Diablo II Install CD in your cd/dvd drive.
		[*]In the shell (Terminal), find out what media bay your Diablo II cd is in. In the shell, type: ```
wine /media/cdrom[your drive number]/install.exe
``` If you use the tab key it helps locate the path; by tabbing when at "wine /media/" you'll see the different drive numbers; by the "1" and hitting tab, hopefully you'll see a the files on the Diablo II cd. You can also get the drive number from the shortcut on your desktop.
		[*]In Diablo II Setup, click through the Diablo II splash screen click until you select "Install Diablo II".
		[*]In Choose Installation Size, select "Full Version"- not single player or multi player.
		[*]In License Agreement, select "Agree" if you agree to their Terms of Services (ToS).
		[*]In Diablo II, enter the name.
		[*]Enter your working 16 character Diablo II cd-key. Click "Ok".
		[*]When prompted to choose install directory, leave it at the default (c:\Program Files\Diablo II). Click "OK".
		[*]In Desktop Shortcut, do not create a desktop shortcut to Diablo II. Click "No". 
		[*]Install should begin. 
		[*]When prompted "Please insert the CD labeled 'Play Disc'". Swap out the Install disc with the Play disc. 
		[*]Close the media bay tray.
		[*]Close the new window that just opened up showing the Diablo II Play disk contents.
		[*]Click "Ok" in the Insert Disc install window. Your installation should continue.
		[*]When prompted "Please insert the CD labeled 'Cinematics Disc'". Swap out the Play disc with the Cinematics disc. 
		[*]Close the media bay tray.
		[*]Click "Ok" in the install window. Your installation should continue.
		[*]When prompted "Please insert the CD labeled 'Install Disc". Swap out the Cinematic disc with the Install disc. 
		[*]Close the media bay tray.
		[*]Click "Ok" in the install window. Your installation should continue.
		[*]When prompted "Would you like to view the ReadMe now?", select "No".
		[*]When prompted with the Register Diablo II Electronically window, click "No". Do not register the game.
		[*]Click "Exit Installer". Close out until the Diablo II installation is done. Click "X" on the Diablo II installer window; do not close the WINE window.
		[*]Optional: You might get prompted with the "Diablo II Setup- Video Test", click "Cancel". Do not run the video/graphic card test at this time.
	[/LIST]

**Installing Diablo II Expansion**
	[LIST=1]
		[*]Put your Diablo II Expansion CD in your cd/dvd drive.
		[*]In the shell (Terminal), find out what media bay your Diablo II cd is in. Type ```
wine /media/cdrom[your drive number]/install.exe
```. If you use the tab key it helps locate the path; by tabbing when at "wine /media/" you'll see the different drive numbers; by the "01" and hitting tab, hopefully you'll see a the files on the Diablo II Expansion cd.
		[*]Diablo II : Lord of Destruction Setup, when prompted with the Diablo II splash screen, click "Upgrade To Lord Of Destruction (800mb)".
		[*]In License Agreement, select "Agree" if you agree to their Terms of Services (ToS).
		[*]Enter your working 16 character Diablo II Expansion cd-key, then click "Ok".
		[*]When prompted to create a desktop shortcut, select either "Yes". 
		[*]Install should begin. 
		[*]When prompted "Please insert the Diablo II CD labeled 'Play Disc'". Swap out the Expansion cd with the Play cd. 
		[*]Close the media bay tray.
		[*]Click "Ok" in the install window. Your installation should.
		[*]When prompted "Please insert the Diablo II CD labeled 'Expansion Disc'". Swap out the Play cd with the Expansion cd. 
		[*]Close the media bay tray.
		[*]Click "Ok" in the install window. Your installation should continue.
		[*]When prompted "Would you like to view the ReadMe now?", select "No".
		[*]When prompted with the Register Diablo II: Lord of Destruction Electronically window, click "No". Do not register the game. Do not register the Game.
		[*]Click "Upgrade Installation" in the Diablo II: Lord of Destruction Setup window.
		[*]Click "Upgrade from Multi-player to Full".
		[*]Click "Exit Installer". The Wine window should close.
	[/LIST]

**Installing Diablo II Expansion patch**
There are two ways to patch the Diablo II, either let the game auto update when you first connect to Battle.net or download and install the patch using the shell (Terminal).

To install using the shell (Terminal).
	[LIST=1]
		[*]Go to [BattleNet]("http://www.blizzard.com/support/?id=msc0387p")
		[*]Download the Expansion Windows version 1.11b Upgrade Patch. Save it to your Desktop. Wait until the patch is completely downloaded before proceeding.
		[*]In your shell, type: ```
wine /home/[your username]/Desktop/LODPatch_111b.exe
```
		[*]When the patch is finished installing, click "Ok". The WINE window should close; if it does not close, close it.
	[/LIST]

**Running the Video Test**
	[LIST=1]
		[*]In your shell, type ```
wine /home/[your username]/.wine/drive_c/Program\ Files/Diablo\ II/D2VidTst.exe
```.
		[*]When prompted with the Diablo II Setup- Video Test, click "Run Test".
		[*]In the Video Test Complete window, click "Ok". Leave whatever radial option was set to. The WINE window should close.
	[/LIST]

**Minor Troubleshooting**
Ok, so let's test this out and possibly jump on BattleNet to pown some noobs (j/k I suck at pvp).
To start D2, go to Applications > Wine > Programs > Diablo II.  Hopefully, everything starts right up and works for you.  If not, here are some problems that I had.
	[LIST]
		[*]CD-missing
			In the shell (Terminal), type ***winecfg***. In the Drives tab, click "Autodetect".
		[*]Poor graphics
			In the shell, type ***winecfg***. In the Graphics tab, check "Emulate a virtual desktop". Depending on you resolution, set it to a standard size (1024x768, 800x600, etc...).
			Another thing you can do is run the D2VidTest.exe. In your shell, type ```
wine /home/[your username]/.wine/drive_c/Program\ Files/Diablo\ II/D2VidTst.exe
``` Click "run", wait for the test and select 2D instead of 3D.		
		[*]Poor Sound
			In the shell, type ***winecfg***. In the Audio tab, make sure ALSA Driver is the only one checked.
		[*]Laggy/jumping sound and graphics and jumpy/slow mouse control.
			After many attempts and conversations in the #winehq, I figured out a solution to this.  The video setting for the game were too high, thus causing pc to work overtime. Rerun the Diablo II video test and change the settings to a lower setting. Also in the shell, type ***winecfg***; in the Graphics tab, check "Emulate a virtual desktop". Depending on you resolution, set it to a standard size.
		[*]Failed D2VidTst.exe
			In your shell, type ```
wine /home/[your username]/.wine/drive_c/Program\ Files/Diablo\ II/D2VidTst.exe
``` Click "Cancel" and then select the default 2D graphics option.				
			If your fail the D2VidTst.exe and you have no option to choose a setting, it means you do not have the drivers for your graphics card working properly.  You'll still be able to play D2 even if you fail the D2VidTst.exe.
		[*]Install Hangs/Freezes
			The most common problem when installing is when someone says the install hangs or freezes.  Most likely the windows informing you to switch CDs is behind another window. To resolve this, you might have to abort your current install. The in the shell type "winecfg", goto the Graphics tab and uncheck "Allow the Window Manager to control windows". Trying reinstalling D2 now. 	
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
		[*]Copy d2xmusic.mpq from your Diablo II Expansion CD to /home/[your username]/.wine/drive_c/Program Files/Diablo II/ directory.
	[/LIST]

**Playing Multiple instances of Diablo II**
I must provide partial credit of this to Murraysw on the Ubuntu forums. Murraysw's original post can be found here: [http://ubuntuforums.org/showthread.php?t=438724](http://ubuntuforums.org/showthread.php?t=438724).
	[LIST=1]
		[*]Download a copy of Onlyer's CD Key Refiller. I don't know where you can get a copy of it.
		[*]Read the instructions as to how to refill create the mpqs.Mmurraysw's directions might be helpful to you depending on what "version" of Onlyer's you have. Murraysw's directions are straight forward to key refilling as in Windows. 
			I had to do the following:
		[*]Make a copy of your registry settings. In the shell, type: ```
cp ~/.wine/user.reg user.reg.backup
```
		[*]I was unable to run the registry file as in the Onlyer's CD Key Refiller so I manually added the settings to the Wine registry. In the shell, type ```
gedit ~/.wine/user.reg
```
		[*]Look for the Entry similar to **[Software\\Blizzard Entertainment\\Diablo II] 1179110567**. In that stanza add the registry settings similar to registry settings provided in the Onlyer download and save the file.
			Note how I copied the registry settings to the bottom of the stanza. Mine looked like this:
```

[Software\\Blizzard Entertainment\\Diablo II] 1179110567
"AllowHardcore"=dword:00000001
"Always Run"=dword:00000001
"AutoMap Left"=dword:00000001
"AutoMapFade"=dword:00000000
"AutoMapMode"=dword:00000000
"Aux Battle.net"="216.148.XXX.XXX"
"Blended Shadows"=dword:00000000
"CmdLine"="-skiptobnet"
"Contrast"=dword:00000064
"DiabloIICD"="D:"
"DIFF_LEVEL"=dword:00000002
"GAMEOVER"=dword:00000000
"Gamma"=dword:0000009b
"Help Menu"=dword:00000001
"InstallPath"="c:\\Program Files\\Diablo II"
"Last BNet"="the-catalyst"
"Light Quality"=dword:00000000
"LVL_REST"=dword:0000029a
"MAX_PLAYER"=dword:00000004
"Mini Panel"=dword:00000001
"Music Volume"=dword:00000000
"NPC Speech"=dword:00000002
"Options Music"=dword:00000000
"PopupHireling"=dword:00000001
"Preferred Realm"="USWest"
"Program"="c:\\Program Files\\Diablo II\\Diablo II.exe"
"Resolution"=dword:00000001
"Save Path"="c:\\Program Files\\Diablo II\\save\\"
"Skip To Open"=dword:00000000
"SmallInstall"=dword:00000000
"Text Display Beta"=dword:00000001
"UseCmdLine"=dword:00000000
"owner"="Erin<3Maynard"
"d2cdkey"="MYCDKEYWITHOUTDASHES"
"d2xcdkey"="ANOTHERKEYNODASHES"
"d2cdkeympq"="cdkey_erin.mpq"
"d2xcdkeympq"="cdkey_erin.mpq"

```
		[*]Copy the .mpq file provided with Onlyer package to your D2 directory. In the shell, you'll type something similar to: ```
cp [path]/[name of generic mpq] ~/.wine/drive_c/Program\ Files/Diablo\ II/[name of the file you specified in your registry]
```
			I typed **cp blank.mpq ~/.wine/drive_c/Program\ Files/Diablo\ II/cdkey_erin.mpq**.

		[*]Copy Onlyer's CD Key Refiller to your D2 directory. In the shell, you'll type something similar to: ```
cp [path]/[name of Onlyer's CD Key Refiller] ~/.wine/drive_c/Program\ Files/Diablo\ II/
```
		[*]Run Onlyer's CD Key Refiller. In your shell, type:```
wine ~/.wine/drive_c/Program\ Files/Diablo\ II/[name of Onlyer's CD Key Refiller]
```
			I typed **wine ~/.wine/drive_c/Program\ Files/Diablo\ II/d2-cdkey.exe**.

		[*]In the Refiller, select "Refill both CD Keys". It may ask you for what directory Diablo 2 is installed; if it does, navigate it to you C:Program Files/Diablo II directory.
		[*]If you've had no problems so far then you need to make a copy of your Wine directory to allow multiple D2 Wine instances to be able to open at the same time. In the shell, type: ```

cd ~/
cp -r .wine .wine2

```
		[*]On your desktop, copy your Diablo II Wine launcher.
		[*]Right Click on the copy and rename it to "Diablo II- 2".
		[*]Now you need to change the properties to it to launch a new Wine instance of it. Right click on the the "Diablo II- 2" and select Launcher.
		[*]In the command, change it to ```
env WINEPREFIX="/home/[your username]/.wine2" wine "C:\Program Files\Diablo II\Diablo II.exe" -d3d9 -mpq [file name].mpq
```
			I typed: **env WINEPREFIX="/home/erin/.wine2" wine "C:\Program Files\Diablo II\Diablo II.exe" -d3d9 -mpq cdkey_erin.mpq**
		[*]Repeat the steps as necessary for more instances of D2.
[/LIST]
As an alternative to using Onlyer's CD Key Refiller and going through all those steps, if you already have the mpq files from a Windows box, just copy them over and change the short-cut to them.

**Botting for Diablo II**
I know of two well known bots- D2JSP and mmBot- both are geared for Windows. Since D2JSP is detectable, and is the Devil, I have no intention or motivation to discuss it further. 

I have tried mmBot .544b8u3 on Wine and was able to get it to sequence through multiple runs.  There seems to be two major problems: 1) stand skill not working (even after changing to 'g' instead of 'SHIFT'), and 2) read items on ground key not working (even after changing to 'c' instead of 'ALT'). Minor problems are: very low initiate run when entering room, reading items when selling to Mala and launching and finding the town portal, very long run time for ESP runs- like about 500 seconds per run. The 'END', INSERT' and 'PAUSE' keys don't work. But, like I said, only 2 major problems...

I've left the bot cycle through and basically the merc kills everything. It paths correctly though.

Keep you posted it seems other fellow mmBotters are taking an interest to mmBotting on Linux with Wine.

**Maphack for Diablo II**
I don't use maphack, but based on DARKGuy's post on the Ubuntu forum I was able to create rough instructions for maphack (I don't even know which maphack it is):
[LIST=1]
		[*] Download d2hackit.
		[*] Install and copy all maphack files inside "/home/[your username]/.wine/drive_c/Program\ Files/Diablo\ II/[plugin?]" directory
		[*] In the shell. type **wine d2hashgen.exe** or **wine [whatever the file is for generating the MapHack hash using your original CDKey]**
		[*] Rename **D2maphack.dll** to **d2maphack.vcb**.
[/LIST]

**Stealth.Bot**
*I have not tried Stealth.bot on Linux yet, as I've always wanted to make a public price bot for it so I imagine I'll try it sometime.*

**Creating a shortcut to you Diablo II directory**
	[LIST]
		[*]In the shell, type: 
```

cd ~/Desktop
ln -s ~/.wine/drive_c/Program\ Files/Diablo\ II/

```
	[/LIST]

**Finding out what IP your in**
	[LIST=1]
		[*]In the shell, type: 
```

netstat -putan

```
		[*]The line with port 4000 is the IP u look at-i.e. '63.241.83.##:4000'
		[*]The last subnet is the IP of the room your in, just like in windows.
	[/LIST]
 

**=** - **=** - **=** - **=** - **=** - **=** - **=**


Please post suggestions to the guide and I'll try to incorporate them in.

Special thanks to all those in irc.freenode.net#winehq, especially vitamin, for all your patience helping me through the troubleshooting.  Hopefully this guide will help others the way you all helped me. 

And to all you D2 junkies out there that want to switch over to the Ubuntu family or for those that just want to play Diablo II on a flavor of Ubuntu, here you go. If anyone is ever on bNet shoot me a message; I'm THE-CATALYST @ us-west (sorry I don't play any other realms). l8 and gl -Erin.
*I forgot my pen...*

---

### Post by GiantRobot on 2007-05-14
Wow! Amazing guide dude! :) 

I'm not a DiabloII player myself anymore but this will definatly come in handy if I ever decide to play again.

Again, nice work!

---

### Post by kebes on 2007-05-17
I'm thinking of installing Diablo II, but it would be for online multiplayer.

Have you tested whether network play works using this how-to?

---

### Post by dynacrylic on 2007-05-17
> **kebes said:**
> I'm thinking of installing Diablo II, but it would be for online multiplayer.

Have you tested whether network play works using this how-to?

I play online all the time through Battle.net. I have not tested the other multiplayer (meaning open or home network)

---

### Post by kebes on 2007-05-17
Thanks for the quick reply. That's good news for me. One other question, do you know if Diablo II will "play nice" with a dual-screen setup. I have two monitors, most games don't look good if they expand across both monitors (or worse, if they wind up as a small box right in the middle of the monitor-split!). Some games I can get to go fullscreen on only one monitor...

Do you know if this works with Diablo II? I've never played it, so I don't know if it launches into a window that you can adjust (maximize on a single screen) or whether it tries to go to fullscreen mode without any options.

No big deal if you don't know... I'm going to give this a try soon. Thanks for the excellent how-to!

---

### Post by dynacrylic on 2007-05-17
> **kebes said:**
> Thanks for the quick reply. That's good news for me. One other question, do you know if Diablo II will "play nice" with a dual-screen setup. I have two monitors, most games don't look good if they expand across both monitors (or worse, if they wind up as a small box right in the middle of the monitor-split!). Some games I can get to go fullscreen on only one monitor...

Do you know if this works with Diablo II? I've never played it, so I don't know if it launches into a window that you can adjust (maximize on a single screen) or whether it tries to go to fullscreen mode without any options.

No big deal if you don't know... I'm going to give this a try soon. Thanks for the excellent how-to!

No prob for the quick reply (I walked home and am on my lunch break).

Not sure about the dual monitor setup.  If you have any problems, you can always run D2 in the -w mode for a window rather than the full screen.

---

### Post by kebes on 2007-05-17
Excellent! Thanks again.

---

### Post by lazyfool11 on 2007-05-22
Hi,
I'm kinda noobish to linux.  I'm trying to install d2.  I insert the disc, and i've already downloaded and installed wine.  when i go to run the command wine /media/cdrom[0]/install.exe nothing happens.  but if i run wine /media/cdrom[0]/setup.exe nothing happens but i return to my normal prompt (that didn't happen with install.exe).  then if i try install.exe (after i've run the setup.exe) it starts up correctly.  I follow your guide through, and after it asks if I want to create a icon and i hit no it starts trying to install.  and then it freezes.  doesn't get anywhere in installing and my command window doesn't get any errors.  any ideas?  also, how do i kill the process cuz the install window takes focus and wont leave.

thanks,
Chris

---

### Post by marsm on 2007-05-27
Nice guide!!

Although it would be even better if it mentioned how much space WINE and/or D2 take up on the hard drive.

Also a link to a wiki which contains this guide would be good so people can add stuff to it.

---

### Post by dynacrylic on 2007-05-27
> **lazyfool11 said:**
> Hi,
I'm kinda noobish to linux.  I'm trying to install d2.  I insert the disc, and i've already downloaded and installed wine.  when i go to run the command wine /media/cdrom[0]/install.exe nothing happens.  but if i run wine /media/cdrom[0]/setup.exe nothing happens but i return to my normal prompt (that didn't happen with install.exe).  then if i try install.exe (after i've run the setup.exe) it starts up correctly.  I follow your guide through, and after it asks if I want to create a icon and i hit no it starts trying to install.  and then it freezes.  doesn't get anywhere in installing and my command window doesn't get any errors.  any ideas?  also, how do i kill the process cuz the install window takes focus and wont leave.

thanks,
Chris

What version of Wine and Ubuntu are you using?

---

### Post by ftmichael on 2007-05-27
I followed this howto to the letter, and had the following errors:

Diablo VideoTest errors during install:

> II\D2VidTst.exe: main/renderbuffer.c:2041: _mesa_add_renderbuffer: Assertion `bufferName == BUFFER_DEPTH || bufferName == BUFFER_STENCIL || fb->Attachment[bufferName].Renderbuffer == ((void *)0)' failed.
err:ntdll:RtlpWaitForCriticalSection section 0x7e36b980 "x11drv_main.c: X11DRV_CritSection" wait timed out in thread 001d, blocked by 001b, retrying (60 sec)

I saw in the howto where it says to run the VideoTest from the terminal, then *Click "Cancel" and then select the default 2D graphics option.*  I clicked Cancel and it just went away.  Nowhere can I find graphics options.

On clicking Technical Information, I see that I apparently don't have DirectX 7a installed.  Is it entirely necessary?  Apparently it can install it for me.  The last time I installed Diablo II (on Breezy, I think it was), it screwed up my video settings and my graphics went all weird and it was a big pain to fix them, so I'm a bit wary of it now.


Errors when trying to start the game (after full installation, including expansion):

* Little window pops up; title bar says "Diablo II Exception".  Window contents say "UNHANDLED EXCEPTION: Unknown Exception (80000101)"


When I run the game from a terminal, I get this upon clicking "Play Diablo II" (which had previously said "Install Diablo II"):

> II\Game.exe: main/renderbuffer.c:2041: _mesa_add_renderbuffer: Assertion `bufferName == BUFFER_DEPTH || bufferName == BUFFER_STENCIL || fb->Attachment[bufferName].Renderbuffer == ((void *)0)' failed.
err:dbghelp_msc:codeview_process_info Unknown CODEVIEW signature 2069bb68 in module L"game"
fixme:dbghelp:SymGetModuleInfo Wrong size
fixme:dbghelp:SymGetModuleInfo Wrong size
fixme:dbghelp:SymGetModuleInfo Wrong size
err:ntdll:RtlpWaitForCriticalSection section 0x7bc833c4 "loader.c: loader_section" wait timed out in thread 002a, blocked by 0029, retrying (60 sec)
err:ntdll:RtlpWaitForCriticalSection section 0x6ffa1408 "?" wait timed out in thread 0029, blocked by 002a, retrying (60 sec)
wine: Critical section 7bc833c4 wait failed at address 0x7bc303b0 (thread 002a), starting debugger...
err:seh:raise_exception Unhandled exception code c0000194 flags 0 addr 0x7bc303b0

What is going on?  How do I fix this?

Michael

---

### Post by Cyann0923 on 2007-05-30
Trying to use tblEdit on here.  Did everything just like on windows and it refuses to work.

```
wine "C:\Program Files\Diablo II\Diablo II.exe" -skiptobnet -direct -txt -act5
```

I am using D2loader and Glide Wrapper.  Did I do something wrong, or does it just no work on Linux?

---

### Post by yosser on 2007-06-01
I followed directions to install Diablo 2 and the expansion, the first part went off flawlessly.

but when I attempt to install the expansion, the popup window claims that I must install D2 first.

which I obviously already have. 

What is my problem? I can run D2 from the App/wine/programs menu quite simply.

---

### Post by Dokatz on 2007-06-01
Everything goes smooth until the actual install starts,I get the install progress bar, But it simply doesn't move at all and the CD spins down and nothing happens. When I do a single player install, For some reason it starts installing fine.

Anyone have any ideas on what to do?

---

### Post by Enverex on 2007-06-03
Just scanned this and there is one thing wrong:

wine /media/cdrom[your drive number]/install.exe

should be:

wine "D:\install.exe"

(assuming your winecfg is set up with your CD drive as D:)

---

### Post by Lothrimer on 2007-06-05
> **lazyfool11 said:**
> Hi,
I'm kinda noobish to linux.  I'm trying to install d2.  I insert the disc, and i've already downloaded and installed wine.  when i go to run the command wine /media/cdrom[0]/install.exe nothing happens.  but if i run wine /media/cdrom[0]/setup.exe nothing happens but i return to my normal prompt (that didn't happen with install.exe).  then if i try install.exe (after i've run the setup.exe) it starts up correctly.  I follow your guide through, and after it asks if I want to create a icon and i hit no it starts trying to install.  and then it freezes.  doesn't get anywhere in installing and my command window doesn't get any errors.  any ideas?  also, how do i kill the process cuz the install window takes focus and wont leave.

thanks,
Chris

I tried "wine /media/cdrom0/install.exe", follow the guide until i answer "no thanks, i don't want an icon installed" and then it freezes. I killed the process with KSysGuard (Kubuntu Performance Monitor).
(I remember having installed D2LoD once on my system maybe a year ago through WINE, but sadly i couldn't get my printer to work with that distribution...)

I'm using Kubuntu 7.04 and WINE 0.9.38 (had the same problem with Linux Mint 3.0).

Cheers

---

### Post by Lothrimer on 2007-06-05
Sorry for the semi-spam here, but i googled around a bit and found a straw for lazyfool to grasp:

---- The “change disc” (insert play disc) pops up behind the progress bar. Run winecfg, goto the graphics tab and uncheck "allow the window manager to control windows". This might help but i'm not sure. ----  -SlickMcRunfast

It helped me. I also had to fix it so that whenever I insert a CD into the drive it shows the CD's contents. That way I can close the window and I get a confirmation that it's been detected.

Cheers, Slick.

---

### Post by mzingg on 2007-06-10
everything goes smoothly until the actual install. Then it just sits there and dosnt install. whats happening?



EDIT::: Never Mind. I was stupid and didnt read the last post above me. Im installing it as I type

EDIT AGAIN::: D2 installed. but im getting the same problem as the person a couple post above me. when I attempt to install D2 LOD, it tells me I need to install D2. Help?

---

### Post by family on 2007-07-10
Hey, thanks for the great guide buddy. :guitar: The only problem was that Ubuntu (7.04) refused to recognize the 1.11b patch I downloaded. Oh well, is it safe to delete it?

---

### Post by dynacrylic on 2007-07-10
> **family said:**
> Hey, thanks for the great guide buddy. :guitar: The only problem was that Ubuntu (7.04) refused to recognize the 1.11b patch I downloaded. Oh well, is it safe to delete it?

You mean delete the 1.11b patch? yeah.

I re-installed D2 without downloading the patch separately and when I first connected to bNet it automatically downloaded the patch. Everything was smooth.

On some older versions of wine I had a problem with it automatically installing the updates when you first connected to bNet. So that's why I always just used to install them separately.

---

### Post by dynacrylic on 2007-07-10
> **mzingg said:**
> 
EDIT AGAIN::: D2 installed. but im getting the same problem as the person a couple post above me. when I attempt to install D2 LOD, it tells me I need to install D2. Help?

i'm not sure what the problem is, sorry.

but if you find out, let me know so I can update the guide.

---

### Post by Fowlwing on 2007-07-10
Hey i was also having the problem with the diablo 2 lod cd saying i couldn't install.

What you need to do is re-install diablo 2 and right after start installing LOD cause if you stop setup it will think that you need to re install diablo 2    so right after you install diablo 2  get started on installing  the expansion.

---

### Post by Tourney on 2007-07-10
Well, I've got the game installed and running on Bnet, but I seem to be having some graphical problems. At random intervals, the game freezes for about a second, then speeds up afterwards, catching up to the rest of the game. Any Idea why this is happening?

---

### Post by dynacrylic on 2007-07-11
> **Tourney said:**
> Well, I've got the game installed and running on Bnet, but I seem to be having some graphical problems. At random intervals, the game freezes for about a second, then speeds up afterwards, catching up to the rest of the game. Any Idea why this is happening?

might be the graphics settings (meaning 2d or 3d).

---

### Post by Fowlwing on 2007-07-11
hey  i have diablo 2 and the expansion all installed and nice and nice... but it wont let me play... it says i need to insert the expansion disk.... wich is already in there  i tried auto detecting it to and still nothing works... any ideas?

---

### Post by Tourney on 2007-07-11
> **dynacrylic said:**
> might be the graphics settings (meaning 2d or 3d).

I ran it in both 2D and 3D and had the same problem. I found somewhere a how-to in adding a 3rd graphics mode (says "glide" when i type /fps ingame). I still get the problem, though it seems to happen after a longer duration. Still, any other ways to maybe fix this? Might it be because I didn't completely follow the walkthrough? After installed D2 and LoD, I just downloaded the patches by clicking Battle.net ingame, and didn't download them off the site.

---

### Post by dynacrylic on 2007-07-11
> **Tourney said:**
> I ran it in both 2D and 3D and had the same problem. I found somewhere a how-to in adding a 3rd graphics mode (says "glide" when i type /fps ingame). I still get the problem, though it seems to happen after a longer duration. Still, any other ways to maybe fix this? Might it be because I didn't completely follow the walkthrough? After installed D2 and LoD, I just downloaded the patches by clicking Battle.net ingame, and didn't download them off the site.

the patch part should isn't the probably. it's probably ur video drivers

---

### Post by wCrabtree on 2007-07-11
I now have a problem installing LoD. I have installed D2. Then I try the Exp. I put the C.D. in, press upgrade and then it asks to put in the play cd. I did that and then after it loads allot from the cd, it asks for the play cd again. But the cd is already in the drive. I try to eject it out then back in but it doesn't do anything. I cant seem to find the answer to this :(

---

### Post by tombug on 2007-07-12
nice detail, and well put together
not to say this game is also one of blizzards best

---

### Post by wCrabtree on 2007-07-13
Well, I fixed it some how. Now I just need to make the game Windowed.
Well, I fixed that too.

---

### Post by fhco on 2007-07-15
Ok, great guide. Got the game working in Wine with this, when Cedega wasn't doing it for me.

However, I get the same problem when I try to play after installing LoD. When I go to play, it pops up a little error box that just has a bunch of question marks with "Cancel" and "Retry" options. I assume I don't have a font installed, and I also assume it is not recognizing my LoD disc. In the terminal, I get this error:

err:aspi:SCSI_GetDeviceName Could not open HKLM\HARDWARE\DEVICEMAP\Scsi\Scsi Port 1\Scsi Bus 0\Target Id 0\Logical Unit Id 5

I tried installing D2Loader, and voila, it worked. The only problem is that when I try and log on to Battle.net, it says it cannot recognize/verify my version. :(

So either I can play the game with D2Loader but no Bnet, or I can't play the game withOUT D2 loader. Any advice? This issue seems to have not been resolved over at Transgaming, either.

---

### Post by Tourney on 2007-07-16
> **dynacrylic said:**
> the patch part should isn't the probably. it's probably ur video drivers

That's probably it. When I was installing drivers, I was using some howto, and it had like 4 different links to use, and you checked a list of graphics cards, and whichever list your card was on, you used that link. I forgot / didn't bother looking to find out what card I'm using, and just grabbed the first link for the terminal code. Any way I can remove my drivers and re-do it?

Also, I'm not getting any sound in-game.

---

### Post by Dougie187 on 2007-08-14
Has anyone been able to get maphack to work? I need help with it.

---

### Post by dynacrylic on 2007-08-14
> **Dougie187 said:**
> Has anyone been able to get maphack to work? I need help with it.

I don't use MH, but I know some have gotten it to work.  There is a MH section in the howto. What MH are you trying to use?

---

### Post by Dougie187 on 2007-08-15
Well.. I was trying to use string's mh. but in the howto you say that you have to use d2hackit. And when I downloaded d2hackit, its just a loader.exe file with some .dll file. And whenever i run it, it doesnt do anything. And if D2 is open, it just closes it. So im not really sure what to do with d2.

---

### Post by dynacrylic on 2007-08-15
> **Dougie187 said:**
> Well.. I was trying to use string's mh. but in the howto you say that you have to use d2hackit. And when I downloaded d2hackit, its just a loader.exe file with some .dll file. And whenever i run it, it doesnt do anything. And if D2 is open, it just closes it. So im not really sure what to do with d2.

As much as I'm against using MH, Just for you i'll load up a junk key set and figure out how to get sting's working

(this doesn't mean I'm a cheater...i'm juyst trying to be helpful within my scope of what I know and what I can do)

i'll post back when i got it working

---

### Post by Dougie187 on 2007-08-15
thanks ma'am. I just dont know how to get it working and right now my alternative is to swap to windows when i need it.

PS. I only use it when I am rushing.

---

### Post by dynacrylic on 2007-08-15
> **Dougie187 said:**
> thanks dude. I just dont know how to get it working and right now my alternative is to swap to windows when i need it.

PS. I only use it when I am rushing.

no luck so far...

and i'm not a dude

---

### Post by Dougie187 on 2007-08-15
Replaced. Thanks again, let me know if you find anything. I'll also keep workin on it, and I will let you know if I get it to work somehow.

---

### Post by Dougie187 on 2007-08-16
I got a message back from Darkguy, from what he said I think that you have to use a loader for the game, and then use the maphack as a plugin for the loader, but i dont know how you would go about doing this. Though I already have a loader, as that was needed for making the multiclient work correctly.

---

### Post by Dougie187 on 2007-08-18
Ok, so.. I think that this needs the d2hackit to work correctly in linux. and I don't believe that d2hackit works with 1.11b currently, and noone is actively working on it. So.. I dont think that it is possible to get maphack to work with linux for 1.11b.

---

### Post by dynacrylic on 2007-08-19
> **Dougie187 said:**
> Ok, so.. I think that this needs the d2hackit to work correctly in linux. and I don't believe that d2hackit works with 1.11b currently, and noone is actively working on it. So.. I dont think that it is possible to get maphack to work with linux for 1.11b.


ah

---

### Post by green ken on 2007-08-24
Great guide, for starters.
But I am having some trouble... When I run the command wine /media/cdrom0/install.exe, a window pops up saying "please insert the install disc,"  Which would be fine if the install disc weren't already in the drive.  I figured I could just open and close my tray and see if the disc would load that way, only my computer will not allow me to open the tray because it says the disc is in use.
Any suggestions?

---

### Post by Dougie187 on 2007-08-27
Have you tried autodectecting the drives in winecfg?
Also,
Something that I remember having an issue with, is If you run the command from a terminal, and you are in the cd directory, then you cannot eject the drive until the terminal window is closed (which will end your wine session) So make sure you run the command from somewhere else (not in the cd directory). Then you should be able to eject the cd without any problems.

---

### Post by green ken on 2007-08-27
Bam!
Both those things worked, thank you!
The problem now is that I have D2 installed, but I can't play it.  Though I don't have the LOD expansion, I figured I'd still be able to play boring old  D2.  Am I mistaken?

When I try to run Diablo 2, a messages pops up saying that "Diablo II was unable to detect my CD-ROM drive.  Please make sure your Diablo II Play Disc is in your drive, then click retry."  Well, it's in there, and no matter how many times I click retry, it doesn't work.

---

### Post by dynacrylic on 2007-08-28
> **Dougie187 said:**
> Ok, so.. I think that this needs the d2hackit to work correctly in linux. and I don't believe that d2hackit works with 1.11b currently, and noone is actively working on it. So.. I dont think that it is possible to get maphack to work with linux for 1.11b.

Yeah, so I'm giving up on this...mainly due to, well below:

I tried several different Sting MH's- each one different.  I find it quite peculiar now that the CD-keys I used to test it with are all in use now.  I've never shared any of my PAID keys and now their all in use by other people...

Don't download the Stings MH from edgeofnowhere and newd2event.  One of is not what it seems and I feel so foolish for having tried.

---

### Post by meatsheets on 2007-08-29
ive read the entire guide
my diablo 2 is laggy, but when i went to look for different options, there is none
help please

---

### Post by dynacrylic on 2007-08-30
> **meatsheets said:**
> ive read the entire guide
my diablo 2 is laggy, but when i went to look for different options, there is none
help please

try changing your d2 video setup to 2d and not 3d. that's the quickest thing that comes to my mind without knowing the specifics.

---

### Post by meatsheets on 2007-08-30
i ran the video test and the only option it gives me is direct 3d: direct draw HAL
i have a 1.5 ghz processor 
512 ram
RIVA TNT2 Model 64 video card

---

### Post by Dougie187 on 2007-09-04
> **dynacrylic said:**
> Yeah, so I'm giving up on this...mainly due to, well below:

I tried several different Sting MH's- each one different.  I find it quite peculiar now that the CD-keys I used to test it with are all in use now.  I've never shared any of my PAID keys and now their all in use by other people...

Don't download the Stings MH from edgeofnowhere and newd2event.  One of is not what it seems and I feel so foolish for having tried.

Sorry to hear that. I have been using Stings from newd2event for about a month and a half in windows, and it works fine for me. Maybe the other one is causing a problem. But i am still unable to get it to work in linux. I sort of think its impossible, but maybe someone would be able to kindly correct me. Anyways, Thanks for your effort and sorry to hear all the CD keys are now stolen.

---

### Post by Baby Boy on 2007-09-18
This is one damn good how-to, Diablo 2 LOD runs like a charm \\:D/ . One can tell you've really tried to explain each step and provide answers for all troubleshooting. You rock man =D>.

---

### Post by Enverex on 2007-09-18
Two things, firstly you should never run Wine apps with a full Linux path and second you should never manually edit the Wine registry...

---

### Post by Elvish Legion on 2007-09-18
I have a question for those of you that play d2...anyone have any luck running d2 in using glide?

[http://www.svenswrapper.de/english/downloads.html](http://www.svenswrapper.de/english/downloads.html)

Everytime I try I get an unhandled exception...

---

### Post by saltedfish on 2007-09-26
I get a "missing BinkW32.dll" error when I try to run the setup.exe. Any help?

---

### Post by Bigdeath on 2007-09-26
Kind of long and don't have enough beer atm but I love this game. Does d2 loader work with it?

---

### Post by Enverex on 2007-09-26
> **saltedfish said:**
> I get a "missing BinkW32.dll" error when I try to run the setup.exe. Any help?

chdir to the folder that contains setup.exe first.

---

### Post by saltedfish on 2007-09-26
> **Enverex said:**
> chdir to the folder that contains setup.exe first.

sorry? you mean run the setup.exe from the console? or am I supposed to change a config file somewhere?

---

### Post by saltedfish on 2007-09-27
well, i solved the bink error by rolling back wine to 9.43

but now i get a start menu error

---

### Post by Baby Boy on 2007-09-27
> **Bigdeath said:**
> Kind of long and don't have enough beer atm but I love this game. Does d2 loader work with it?

Yes, it does. That's actually the only way I got it to work.

---

### Post by Enverex on 2007-09-27
> **Baby Boy said:**
> Yes, it does. That's actually the only way I got it to work.

Diablo 2's copy protection works fine with Wine, you shouldn't have to use a NoCD patch.

---

### Post by Baby Boy on 2007-09-27
> **Enverex said:**
> Diablo 2's copy protection works fine with Wine, you shouldn't have to use a NoCD patch.
I don't know why, but it kept asking me to insert the CD even though it was already there (I *do* have the original BTW ;) ). The only way I could bypass that was to use D2Loader. 
Oh well, this way I can play without the CD.

---

### Post by Enverex on 2007-09-27
Was your CD-Drive set to D: in winecfg and set to type "CD-Rom" in the drop down selector?

---

### Post by Bigdeath on 2007-09-27
I like to run 2 windows though. I have 2 cdkeys and it makes it easier to mule stuff yourself.

---

### Post by Baby Boy on 2007-09-27
> **Enverex said:**
> Was your CD-Drive set to D: in winecfg and set to type "CD-Rom" in the drop down selector?
Probably not :lolflag:. Doesn't matter anymore anyway.

---

### Post by saltedfish on 2007-09-27
Anyone know why I'm getting a 

"No program start menu found"

error?

---

### Post by saltedfish on 2007-09-27
determined bump

---

### Post by Elvish Legion on 2007-09-27
How do I uninstall? I entered the wrong cd key and when I try to play bnet it tells me it is in use (I gave that key to a friend a long time ago) so I need to put the right key in, do I need to uninstall (if so how) or can I just change the key some how

---

### Post by saltedfish on 2007-09-27
I seem to recall that there is an option somewhere that allows you to change the CD key... im not sure, its been a while. But as for uninstalling, I couldnt tell you because Im pretty new to wine.

---

### Post by saltedfish on 2007-09-28
Okay. Since all I was getting was a "no start menu" error, and apparently no one knows what that is, I installed Diablo II on ym friends computer, then copied the entirety of the D2 directory to my machine, and get it nice and nestled into my .wine folder.

My problem is that when I try to patch it using the downloadable patch, it cant find the path to the folder diablo II.exe is in.

Help?

---

### Post by saltedfish on 2007-09-28
any ideas?

---

### Post by dynacrylic on 2007-10-23
Is it worth updating this guide?

---

### Post by jimonade on 2007-12-01
yes!

D2 is a classic, gauntlet done right, slash fest.

and i hate to boot winxp.

---

### Post by dynacrylic on 2007-12-02
> **jimonade said:**
> yes!

D2 is a classic, gauntlet done right, slash fest.

and i hate to boot winxp.

Ok, I'll work in updating it

---

### Post by testic on 2008-03-13
Yes, please do keep this guide updated!

In the meantime perhaps you could help me :) I installed Diablo 2 Classic (I will install LoD at a later date) and it keeps asking me to insert the CD, which is already inserted (genuine CD, working key).

My drives appear to be correctly configured in winecfg, and the registry details are correctly set.

I am using Ubuntu Gutsy (2.6.22-14) and Wine-0.9.54.

I would prefer not to use D2Loader or any similar things, as I have already had my 30 day ban for using 3rd party programs ;)

Edit: I am starting the game with "wine /cdrom/setup.exe". The terminal shows the following:

fixme:aspi:SendASPI32Command ASPI: Partially implemented SC_HA_INQUIRY for adapter 0.
err:aspi:SCSI_OpenDevice Failed to open device /dev/hda: Permission denied
err:aspi:SCSI_OpenDevice Failed to open device /dev/hdb: Read-only file system
fixme:aspi:SendASPI32Command ASPI: Partially implemented SC_HA_INQUIRY for adapter 1.
err:aspi:SCSI_OpenDevice Failed to open device /dev/sg0: Permission denied
fixme:aspi:SendASPI32Command ASPI: Partially implemented SC_HA_INQUIRY for adapter 2.
err:aspi:SCSI_OpenDevice Failed to open device /dev/sg1: Permission denied
fixme:aspi:SendASPI32Command ASPI: Partially implemented SC_HA_INQUIRY for adapter 3.
err:aspi:SCSI_OpenDevice Failed to open device /dev/sg2: Permission denied
fixme:ntdll:FILE_GetNtStatus Converting errno 38 to STATUS_UNSUCCESSFUL
fixme:ntdll:FILE_GetNtStatus Converting errno 38 to STATUS_UNSUCCESSFUL

---

### Post by Enverex on 2008-03-13
Start the game by chdir'ing to the game's folder and running "wine whatever.exe" not by... whatever you're currently trying to do.

---

### Post by bred on 2008-03-13
nice taste for music Dynacrylic ;)

---

### Post by testic on 2008-03-25
Having chdir'd to the game directory as instructed I get the following:

```
$ wine "Diablo II.exe"
fixme:spoolsv:serv_main (0 (nil))
err:advapi:service_get_status service protocol error - failed to read pipe r = 0  count = 0!
err:alsa:ALSA_CheckSetVolume Could not find 'PCM Playback Volume' element
err:alsa:ALSA_CheckSetVolume Could not find 'PCM Playback Volume' element
fixme:mixer:ALSA_MixerInit No master control found on CA0106, disabling mixer
fixme:aspi:SendASPI32Command ASPI: Partially implemented SC_HA_INQUIRY for adapter 0.
err:aspi:SCSI_OpenDevice Failed to open device /dev/hda: Permission denied
err:aspi:SCSI_OpenDevice Failed to open device /dev/hdb: Read-only file system
fixme:aspi:SendASPI32Command ASPI: Partially implemented SC_HA_INQUIRY for adapter 1.
err:aspi:SCSI_OpenDevice Failed to open device /dev/sg0: Permission denied
fixme:aspi:SendASPI32Command ASPI: Partially implemented SC_HA_INQUIRY for adapter 2.
err:aspi:SCSI_OpenDevice Failed to open device /dev/sg2: Permission denied
fixme:aspi:SendASPI32Command ASPI: Partially implemented SC_HA_INQUIRY for adapter 3.
err:aspi:SCSI_OpenDevice Failed to open device /dev/sg1: Permission denied
fixme:ntdll:FILE_GetNtStatus Converting errno 38 to STATUS_UNSUCCESSFUL
fixme:ntdll:FILE_GetNtStatus Converting errno 38 to STATUS_UNSUCCESSFUL

```

---

### Post by dynacrylic on 2008-03-29
Woops. I forgot that I was supposed to update this...

I'm planning on installing 8.04 when it's "officially" out and I'll work on it then.

Sorry...

---

### Post by dynacrylic on 2008-04-03
I also plan on making this guide a wiki page, somewhere so that others can add and edit it too. 

I haven't played D2 in some time and I really don't want that monster sinking it's fangs or claws back into me. The think I shivered and convulsed the last time I went cold turkey from D2.  The cold sweating was unbearable too.

---

### Post by Ideastone on 2008-04-15
Oh man, Diablo 2, that's an addiction I don't need to revisit.

---

### Post by Cerny on 2008-04-15
I just remember playing that game and I would spend hours instead of play instead of doing homework. I'm glad I found this forum. I think I'm gonna give it a shoot to install it on Wine. Thanks

---

### Post by druciaki on 2008-07-02
Hello people!

This guide was very usefull for me, but im having some problems to update diablo with the newest patch.

If ( i run Diablo n try to connect to BNet ):
    it appears
    "UNABLE TO IDENTIFY VERSION
    Battle net is unable to properly
    identify your aplication version"

if ( i try to run Patch update by: sudo wine D2Patch_112a.exe )
    it appears:
    "Blizzard updater v2.72
    This Patch cannot be applied because it is for a diferent version of the game

    filename: Z:\home\druciaki\Diablo II\Game.exe
    fileversion: 1.0.7.0"

 :confused: Anyone got any clue of what could i do to resolve it? :confused:

thanks =D

---

### Post by Shadowmeph on 2008-07-04
> **druciaki said:**
> Hello people!

This guide was very usefull for me, but im having some problems to update diablo with the newest patch.

If ( i run Diablo n try to connect to BNet ):
    it appears
    "UNABLE TO IDENTIFY VERSION
    Battle net is unable to properly
    identify your aplication version"

if ( i try to run Patch update by: sudo wine D2Patch_112a.exe )
    it appears:
    "Blizzard updater v2.72
    This Patch cannot be applied because it is for a diferent version of the game

    filename: Z:\home\druciaki\Diablo II\Game.exe
    fileversion: 1.0.7.0"

 :confused: Anyone got any clue of what could i do to resolve it? :confused:

thanks =D

not sure if you fixed it yet but you have to make sure that your d2 is closed and then posible log out then back in again then use the updater . thats how I got it to work

---

### Post by dserver on 2008-07-06
Anyone found a way to run a maphack?
I've been playing with EPLite which sees the Diablo 2 process but fails to inject it. I'll keep playing with it and post if I find anything.

---

### Post by NeonSphinx on 2008-07-19
Any idea how to get plugins to work with d2loader?

Just little .dll files in ../Diablo II/plugin/

From what I know de2loader should check that dir and load them up automatically right away.  At least that's what happens on my m$ machine lol

I'm not sure if there's something I have to do with said dlls.  I'm still a beginner to open source

thanks for any help

---

### Post by inversionce on 2008-08-20
i was wondering how to fix my screen.
 all the black stays there all the time
[IMG]http://i71.photobucket.com/albums/i153/james-west/Screenshot.png[/IMG]

---

### Post by _Kesler_ on 2008-09-04
with only the screen shot to go by it looks like you are emulating a virtual desktop in wine and the "virtual" resolution is too high. go into wine config and change your virtual desktop size to a lower setting in the graphics tab. it is also a possibility that fore some reason your window manager is crashing when you load D2. in that case open a termanal and try "metacity --replace" if you are not running compiz, or "compiz --replace" if you are. if you run emerald you may need to run "emerald --replace" to restore your theme. all commands of course without the quotes.

---

### Post by hellz99 on 2008-09-30
running 8.04

Everything works fine, can actually play the game with no issues (other than holding down alt), but I play in window mode (-w) and if I click outside the window on accident, the mouse changes to the OS default and diablo won't get mouse focus back.  I try and click back in the window but it does nothing.

any ideas?

---

### Post by dynacrylic on 2008-10-02
> **hellz99 said:**
> running 8.04

Everything works fine, can actually play the game with no issues (other than holding down alt), but I play in window mode (-w) and if I click outside the window on accident, the mouse changes to the OS default and diablo won't get mouse focus back.  I try and click back in the window but it does nothing.

any ideas?

I haven't played D2 through WINE in a while (let alone D2 at all), but it sounds like a setting in WINE somewhere would resolve your problem.

---

### Post by CrazyArcher on 2008-10-20
I've read all 9 pages, but it still haven't cleared the question I have: I've read (and seen :)) that Battle.net works, but has anyone tried the Direct IP connection?

---

### Post by CrazyArcher on 2008-10-21
Ok I'm running Diablo under Windows, and my buddy tries to connect to me through DirecIP and has it in Wine. The thing is that it just doesn't want to connect, nothing just happens. Warcraft3 works fine for him, however. I've got all ports configed. Has anyone tried to playt through Wine and DirectIP?

---

### Post by transam020 on 2008-11-02
> **CrazyArcher said:**
> Ok I'm running Diablo under Windows, and my buddy tries to connect to me through DirecIP and has it in Wine. The thing is that it just doesn't want to connect, nothing just happens. Warcraft3 works fine for him, however. I've got all ports configed. Has anyone tried to playt through Wine and DirectIP?

i seem to be having the same issue.. im running D2 in wine ver 1.0.1 on my dell latitude D620 1.83ghz 2gig mem Intell vid Running Ubuntu 8.10 Intrepid it runs beautifully with compiz off but when i try a direct connect with my nephew it wont connect.. his ip shows up on his windows xp machine as 192.168.1.xxx and on my wine ver my ip shows up as 127.16.32.245. i know thats the issue but not how to correct it.. we are on the same network other wise, 192.168.1.xxx sub = 255.255.255.0 any one know why wine might connect to a local host (127.0.0.1) network?? how can it be corrected??

---

### Post by Enverex on 2008-11-02
> **transam020 said:**
> i seem to be having the same issue.. im running D2 in wine ver 1.0.1 on my dell latitude D620 1.83ghz 2gig mem Intell vid Running Ubuntu 8.10 Intrepid it runs beautifully with compiz off but when i try a direct connect with my nephew it wont connect.. his ip shows up on his windows xp machine as 192.168.1.xxx and on my wine ver my ip shows up as 127.16.32.245. i know thats the issue but not how to correct it.. we are on the same network other wise, 192.168.1.xxx sub = 255.255.255.0 any one know why wine might connect to a local host (127.0.0.1) network?? how can it be corrected??

As far as I'm aware, the fix for this was to open your /etc/hosts file and put your LAN IP and hostname (not localhost) on the first line. i.e:

-----------------------------
192.168.1.100 awesomepc
127.0.0.1 localhost
-----------------------------

---

### Post by transam020 on 2008-11-03
> **Enverex said:**
> As far as I'm aware, the fix for this was to open your /etc/hosts file and put your LAN IP and hostname (not localhost) on the first line. i.e:

-----------------------------
192.168.1.100 awesomepc
127.0.0.1 localhost
-----------------------------

that fixed it for me thanks... D2 works flawlessly all around now

---

### Post by Kaileo on 2009-01-24
I seem to be having problems with running the original Diablo 2 and installing the expansion... I finally got it installed after hours of trying to get the disks to mount themselves. It seems to be working on a trial-and-error basis; I've tried winecfg numerous times. 

Now, I tried to start up the original D2, but when I go into Applications>Wine>Programs>Diablo II>Diablo II, I get a window on my panel that says it's starting up D2 but I can still see the desktop, my mouse has the little loading thing, and then it just... Stops loading. The play disk was in and mounted, so I'm not sure what went wrong there; I had the patch downloaded and everything.

Now, when I try to install D2LOD, I get the similar disk mounting problems... Eventually it did mount, and I got the expansion startup going. Inserted the play disk, it mounted, then it asks me for the expansion disk, as usual. I put the expansion disk in, wait for it to mount [after opening the CD tray a few times over and over], click OK, and the window keeps re-popping up. I try to unmount / eject the disk and it tells me that I can't because some other application is using it / won't allow it to eject... And I have to cancel the install in order to get it to work again.

Any ideas?

---

### Post by westwood2 on 2009-06-27
I cant install wine for some reason, I am trying to install diablo 2 but i cant without wine when i try to install wine this is what it says
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  msttcorefonts
The following NEW packages will be installed:
  wine
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/7506kB of archives.
After this operation, 55.8MB of additional disk space will be used.
(Reading database ... 164192 files and directories currently installed.)
Unpacking wine (from .../wine_1.0.1-0ubuntu6_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/wine_1.0.1-0ubuntu6_i386.deb (--unpack):
 trying to overwrite `/usr/bin/widl', which is also in package wine-dev
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/wine_1.0.1-0ubuntu6_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
please can someone help me:(

---

### Post by Enverex on 2009-06-27
It tells you why, you have Wine-dev installed and need to remove that first. 1.0.1 is epically outdated though.

---

### Post by hermitcrabred on 2009-06-29
How did you get Wine?...Please help. Thanks

---

### Post by ArbiterOfTruth on 2009-10-02
Hey man, you seem to know your way around Ubuntu. I'm a noob to linux/ubuntu and was wondering can you make a guide for Quake 3 Engine games like Jedi Outcast or Jedi Academy or Soldier of Fortune 2 etc.? The only reason I really still use Windows is because of the games. If I find a way to get the games to work in Ubuntu I would be a full convert so to speak lol. Thanks in advance.

---

### Post by Diabolis on 2009-10-02
Use the Wine data base:
[http://www.winehq.org/search?cx=partner-pub-0971840239976722%3Aw9sqbcsxtyf&cof=FORID%3A10&ie=UTF-8&q=jedi+outcast#896](http://www.winehq.org/search?cx=partner-pub-0971840239976722%3Aw9sqbcsxtyf&cof=FORID%3A10&ie=UTF-8&q=jedi+outcast#896)

---

### Post by fou-lu on 2009-10-18
hey i have installed diablo 2 (full install no LOD) on ubuntu 9.0.4 jaunty and it will load and after it does the blizzard video thingy the screen goes black and then the left and bottom sides show the desktop and the rest is black and i cant see anything or do anything besides hit escape to close the window.
does anyone know how to fix this i would really like to play D2
thnks

---

### Post by tehGriggs on 2009-10-29
> **fou-lu said:**
> hey i have installed diablo 2 (full install no LOD) on ubuntu 9.0.4 jaunty and it will load and after it does the blizzard video thingy the screen goes black and then the left and bottom sides show the desktop and the rest is black and i cant see anything or do anything besides hit escape to close the window.
does anyone know how to fix this i would really like to play D2
thnks

Did you run and pass the graphics test? I just got it working on jaunty and the only problem i'm having is that joining games and the "join games" list seem to stop working after joining a couple of games...

---

### Post by lisati on 2009-10-29
Old thread! Discussions on newer versions might deserve their own thread.

---

### Post by cbbnewbie on 2010-06-21
hello im on ubuntu 10.04 , i want to install diablo 2 but im using the iso. files when i click install it says "insert diablo 2 install disk" how do i configure it ???

---

### Post by panzourlismos on 2011-02-24
Hi! I'm new here and 'cause my english is not good,hope, you'll excuse me for my mistakes!
I'd like your help... 
I'm on ubuntu 10.10, have wine wine-1.0.1 and an .iso disc of Diablo2
So, according to your guide : [B]Installing Diablo II
[/B]i follow the steps , with the differenece i don't use the terminal i mount the cd!
So, when i'am to go to step 
18: When prompted "Please insert the CD labeled 'Install Disc". Swap out the Cinematic disc with the Install disc.
the process doesnot ask the Install disc it just only shows me what you say on step 21:When prompted "Would you like to view the ReadMe now?", select "No".

so i select NO
and appears a windows asking for video test, i select NO
and after exit installer.

1st question!!! Why does it jump these steps?? Any idea??

Thought,that it might it's ok i tryied to go on.So,
[B]Installing Diablo II Expansion
[/B]Tryed to mount the Expansion CD
but then it occurs an error and i can't go on.
Could anybody help me????I have stuck here for too many hours!!!
I'll wait...
Thanks!

---

### Post by Vaphell on 2011-02-24
do you have windows partition with diablo 2 istalled? if so you can try running d2 from there, works for me :)

---

### Post by panzourlismos on 2011-02-24
> **Vaphell said:**
> do you have windows partition with diablo 2 istalled? if so you can try running d2 from there, works for me :)

I don't.. Any other idea??
Thank's for answering so fast!! :)

---

### Post by Vaphell on 2011-02-24
do you have windows partition at all? ;-)
does the vanilla D2 work for you?

---

### Post by panzourlismos on 2011-02-25
> **Vaphell said:**
> do you have windows partition at all? ;-)
does the vanilla D2 work for you?


I don't have windows partition.
What is vanila?

---

### Post by panzourlismos on 2011-02-25
Hello again!!
I really did tryied and i complete the first part of installion.
When i tryied to install the expansion disc, when i mount the cd this message appears

An error occured
 wrong fs type, bad option, bad superblock on /dev/loop0,       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

Could you tell me what to do??

---

