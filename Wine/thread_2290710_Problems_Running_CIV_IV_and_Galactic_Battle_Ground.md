---
title: "Problems Running CIV IV and Galactic Battle Ground on Ubuntu 14.04 - Lenovo 3000V100"
date: 2015-08-14
forum: Wine
---

### Post by Juan_Romo on 2015-08-14
Hello Everyone,

I just move from Windows XP to Ubuntu to my Lenovo 3000V100, instalation goes very good and works a lot better than Windows. So I start to install my games and see if they work, after I try many times I get them to work and I have the following issue. on CIV IV the game start well, when I get into the selections of the type of maps it will not disply the graphics, I just did not care too much and try to go into the game, after finish loading the game. It just get SLOW and I mean SLOW like 5 to 10 minuts to show the graphics of the game, then is so slow that I can not make any move or actually play, my computer use the [COLOR=#545454][FONT=arial]Intel [/FONT][/COLOR]*Graphics*[COLOR=#545454][FONT=arial] Media Accelerator 950. Any Help will be great. Thanks

By the way on Galactic Battle Ground, goes well but graphics are not that great. [/FONT][/COLOR]

---

### Post by Simon_Tomoko on 2015-08-16
First I am going to make a lot of assumptions. That your WINE version is 1.6.2 which seems to be the standard release for 14.04. If anyone asks your WINE version you can find out using terminal command;
wine --version or run the Configure Wine from the menu and read the About TAB.

Next, by "Galactic Battle Ground" do you mean Star Wars: Galactic Battlegrounds? If so, most of the test data reports it runs perfect in WINE. Unless you have Clone Campaigns 1.0 which requires a virtual desktop.

[INDENT]To try a virtual desktop all you need to do is run a command line like this one;

wine explorer /desktop="Title of Desktop",640x480 "/fullpathto/game.exe" 

The break down on that line is, WINE starts its own version of explorer but tells the explorer program that your desktop is a different size. The game gets passed this information from the virtual desktop. Your game is then displayed inside a window.
[/INDENT]

Civilization IV was tested on Ubuntu 14.10 using WINE 1.7.40 and rated no issues. However all testing prior to this requires you to use external msxml3.dll. I doubt this is your problem -but it could be- users report, it won't install or run without and since you are running, I just don't know. 
[INDENT]Can't hurt to try; WINEDLLOVERRIDES="msxml3=n" wine "/fullpathto/game.exe"[/INDENT]
[INDENT]If the line works you can set the overrides using the Configure Wine program or use it in a desktop shortcut as shown above.[/INDENT]

Finally you can always experiment with winetricks. After the menu starts, look in this section: Select Default Wine Prefix --> Change Settings.

This menu has a lot of Video and Audio tweaks. Tweaking is simple as clicking on a button, running the program and if it makes things worse then turn off the tweak.

---

### Post by Juan_Romo on 2015-08-18
Ok, thanks for the help. I mean Star Wars Galactic Battlegrounds. It runs OK now. So no more problems with that.

Regarding CIV. I'm ussing Play On Linux tool to install and customize the Wine. and that tool install the CIV on Win 1.4.1. I try to change to 1.7.40 or other newers that 1.4.1 but did not work. So I put it back into 1.4.1 and I make the changes that you recomend about the Display, first I create a Virtual Desktop of 1024 X 728, that make it more stable, then I change under Configuration-Display-Memory size to 4096 and Configuration-Display-OffScreen Rendiring mode to Backbuffer and that make the type of Maps to appear. So that is better. Now the game still very slow, it seems it is because it generate some kind of error, so I run the PlayOnLinux with Debug mode and I get the following messages that may give a clue about the problem:

Running wine-1.4.1 Civ4BeyondSword.exe (Working directory /home/jromo/.PlayOnLinux/wineprefix/Civilization4/drive_c/Program Files/2K Games/Firaxis Games/Sid Meier's Civilizatiofixme:system:SystemParametersInfoW Unimplemented action: 55 (SPI_SETMOUSEKEYS)
fixme: system:SystemParametersInfoW Unimplemented action: 59 (SPI_SETSTICKYKEYS)
fixme: gameux:GameExplorerImpl_VerifyAccess (0x1445a8, L"\\Program Files\\2K Games\\Firaxis Games\\Sid Meier's Civilization 4 Complete\\Beyond the Sword\\Civ4BeyondSword.exe", 0x33fb18)
fixme:wtsapi: WTSRegisterSessionNotification Stub 0x100ec 0x00000000
'import site' failed; use -v for traceback
fixme: win:EnumDisplayDevicesW ((null),0,0x33eeec,0x00000000), stub!
fixme: win:EnumDisplayDevicesW ((null),0,0x33f424,0x00000000), stub!
fixme: win:EnumDisplayDevicesW ((null),0,0x33f430,0x00000000), stub!
fixme: d3d:resource_check_usage Unhandled usage flags 0x8.
fixme: d3d:resource_check_usage Unhandled usage flags 0x8.
fixme: d3d:resource_check_usage Unhandled usage flags 0x8.
fixme: d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:msvcrt: pf_printf_w multibyte characters printing not supported [COLOR=#ff0000](This one repeats many times, so I just cut it the ther first 5)[/COLOR]
fixme:msvcrt: pf_printf_w multibyte characters printing not supported
fixme:msvcrt: pf_printf_w multibyte characters printing not supported
fixme:msvcrt: pf_printf_w multibyte characters printing not supported
fixme:msvcrt: pf_printf_w multibyte characters printing not supported
fixme:d3d:wined3d_buffer_preload Too many declaration changes or converting dynamic buffer, stopping converting
fixme:d3d:state_zenable Z buffer disabled, but ARB_depth_clamp isn't supported.
fixme:d3d:state_lastpixel Last Pixel Drawing Disabled, not handled yet
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:win:EnumDisplayDevicesW ((null),0,0x33ef78,0x00000000), stub!
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
ALSA lib pcm.c:7843: (snd_pcm_recover) underrun occurred
fixme:msvcrt: pf_printf_w multibyte characters printing not supported [COLOR=#ff0000](This one repeats many times, so I just cut it the ther first 5)[/COLOR]
fixme:msvcrt: pf_printf_w multibyte characters printing not supported

fixme:msvcrt: pf_printf_w multibyte characters printing not supported
fixme:msvcrt: pf_printf_w multibyte characters printing not supported
fixme:msvcrt: pf_printf_w multibyte characters printing not supported
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:wtsapi:WTSUnRegisterSessionNotification Stub 0x100ec

---

### Post by Simon_Tomoko on 2015-08-22
Sorry for not getting back to this right away. msvcrt.dll is a MS Visual C library. First I would try to install a higher WINE version, but it that doesn't work.

You can try this; run winetricks at the menu --> select the prefix --> Install Windows DLL or component. 

At this point scroll down the list to the section that starts VCRUN 2003. Those are the Visual C libraries you need, also [here is a page]("https://appdb.winehq.org/objectManager.php?sClass=version&iId=10158&iTestingId=89415") that shows under 1.4.1 you will also need core fonts and many others. Scroll down that page to the section labeled "HOWTO".

---

### Post by Juan_Romo on 2015-09-27
Ok my Friend, I try to install on 1.7.40, but did not work. The only version that seems to work is 1.4.1. I still have issues with how slow the game became when I start to play. 5 to 10 minutes to make a move. Any idea where to look to see the issue..

---

