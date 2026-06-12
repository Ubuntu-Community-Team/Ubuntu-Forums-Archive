---
title: "TF2 goes black after the two first pictures at startup."
date: 2008-10-07
forum: Wine
---

### Post by madsc89 on 2008-10-07
To install TF2, I've followed a couple of guides which I found using google, and now I'm stuck at the load image at startup. The screen is completely black, but the game loads, and I can soon hear the menu music as well as the clicking sound when tuching the buttons in the menu. I am able of quitting normally, using my memory on roughly where the buttons are.

How can I fix this? This is the only thing keeping me from formatting my windows hardrive.

I'm relatively new to Linux, so please tell me what information you need:)

Thank you

Mads

---

### Post by PandaGoat on 2008-10-07
You need to rename the Warcraft III/Movies folder or delete it.  

Also if you get low fps run it with -opengl at the very end of the command.

---

### Post by Gcentrex on 2008-10-08
> **madsc89 said:**
> To install TF2, I've followed a couple of guides which I found using google, and now I'm stuck at the load image at startup. The screen is completely black, but the game loads, and I can soon hear the menu music as well as the clicking sound when tuching the buttons in the menu. I am able of quitting normally, using my memory on roughly where the buttons are.

How can I fix this? This is the only thing keeping me from formatting my windows hardrive.

I'm relatively new to Linux, so please tell me what information you need:)

Thank you

Mads

When you launch the game run it with the command line option -dxlevel 81 for then after that remove it it should now load correctly, unfortunatly the current DirectX9 implementation in wine is not complete currently thats the reason for the screen being black this is mentioned on the winehq app database also.

> **PandaGoat said:**
> You need to rename the Warcraft III/Movies folder or delete it.  

Also if you get low fps run it with -opengl at the very end of the command.

Wrong game entirely their this is Team Fortress 2 on steam.

---

### Post by madsc89 on 2008-10-08
Thank you for reply.

However, I am already doing this.

I've been trying around with this for some months now, and earlier, I actually got to connecting to server, but it crashed there. I've reinstalled several times after that, however. The steam (and tf2) install I'm using now is copy/pasted from my windows drive, but originally it was installed on this system. It works flawless on windows.

One other thing is on the main steam window, the mouse misses. Usually, it is the tip of the arrow, but on the main window (and only there) the point is right below the pointer. For example, I cant move the window.

Attached photos of the problem. In the second photo, the game is fully loaded and the menu music is playing. Also, the mouse flickers a little over that window.

---

### Post by Gcentrex on 2008-10-08
I myself sometimes get that mouse problem but not too often.

I'm wondering can you run Portal or EP2 at all? Basicly anything that is using the new source engine, the command line is wrong it should be just this "-dxlevel 81 -window" the + would only be used when adding for example an ip address when using a dedicated server.

Since you copy from a windows drive try this instead, move your steamapps folder to another location, remove your current .wine directly (rename it or anything else), now copy to the font folder the required font for steam to work correctly.

Now install only steam and geko engine when asked exit steam, copy your gcf files to the new steamapps folder but do not copy your account folder with saves over, then log back into steam again and set the launch option for TF2/Portal/EP2 as "-dxlevel 81 -window" then try to launch it.

Also make sure all visual effects are turned off,i'm guessing you already have the new drivers for your card if its an ATI try using -dxlevel 80 instead of -dxlevel 81

---

### Post by madsc89 on 2008-10-09
> **Gcentrex said:**
> I myself sometimes get that mouse problem but not too often.

I'm wondering can you run Portal or EP2 at all? Basicly anything that is using the new source engine, the command line is wrong it should be just this "-dxlevel 81 -window" the + would only be used when adding for example an ip address when using a dedicated server.

Since you copy from a windows drive try this instead, move your steamapps folder to another location, remove your current .wine directly (rename it or anything else), now copy to the font folder the required font for steam to work correctly.

Now install only steam and geko engine when asked exit steam, copy your gcf files to the new steamapps folder but do not copy your account folder with saves over, then log back into steam again and set the launch option for TF2/Portal/EP2 as "-dxlevel 81 -window" then try to launch it.

Also make sure all visual effects are turned off,i'm guessing you already have the new drivers for your card if its an ATI try using -dxlevel 80 instead of -dxlevel 81

I've done what you said now, but I still get the same problem.
First of all; I haven't installed any other games with that source generation, but I can do that if you want me to. However, CSS, also suffers from the same problem. I changed the command line in both games (-dxlevel 80 -window).

In the process of installing Steam over again, I also reinstalled Wine, and deleted the .Wine folder.
However, the wine item in the applications menu stayed there, and there was some old entries there, so I deleted it all, which I obviously shouldn't have done. Because, with the new wine install, there is nothing.
Also, when opening through my home folder - .wine - and so on, I get an error message, which I believe origins from crossover games (or some other similar program). Because when I choose to open with another program (Wine), it works.

When you say that I should turn off visual effects, Choosing Metacity from the Compiz Fusion Icon is sufficient?

Also I've got a ATI Radeon X1950 Pro (AGP), and the proprietary driver which Ubuntu found for it itself.

The pointer problem in the steam window is (at least from time to time) now fixed, but the issue with the game is the same.


Thank you for the help

Mads

---

### Post by madsc89 on 2008-10-13
No one?

Is choosing Metacity turning off visual effects?
Is my ATI driver good enough?
What else might cause the problem?

Thank you

---

### Post by nathan42100 on 2008-10-14
also, having this problem, tried dxlevel 81, 70, 90 and that in conjunction with:
metacity --replace &
wine etc.....
compiz --replace &

HELP! I want to play HL2! Regular HL is getting boring:lolflag:

---

### Post by Gcentrex on 2008-10-14
Hum I would try installing and running Half-Life 2 since it uses the original source engine and see if that works also try using this

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

That is used for installing Drivers and configuring its settings then try again but I did read right when you said your using an AGP card right?

Also ATI is known to run rather bad on anything but a windows based system OSX/Linux/BSD/FreeBSD.

---

### Post by madsc89 on 2008-10-14
> **Gcentrex said:**
> Hum I would try installing and running Half-Life 2 since it uses the original source engine and see if that works also try using this

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

That is used for installing Drivers and configuring its settings then try again but I did read right when you said your using an AGP card right?

Also ATI is known to run rather bad on anything but a windows based system OSX/Linux/BSD/FreeBSD.

Ok, I'll try HL2, although CSS is bad as well;)

Is the nvidia part of that link nothing to worry about? I guess so.

Yes, I've got a Sapphire radeon x1950 Pro 8x AGP 256 MB. My computer is a rather old Dell Dimension 4600. A year ago, my previous graphic card stopped working. I think it overheated, because some yellow gue came dripping out of it:S Anyway, I got BSOD's all the time, which I fund was a big Nvidia problem, so I deliberately bought a ATI card.

I'll let you know how this ([http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)) goes;)

Thank you

---

### Post by madsc89 on 2008-10-14
We are getting close!

It seems installing (and using) EnvyNG solved the main problem.
I installed it through Synaptic, searching for envyng, and installing the three entries I found.
Then I opened Envy (Applications/System tools), and chose ATI automatic. Remember to close Synaptic before clicking Apply!

I restarted the computer as asked, and when I got back in, I launched TF2.
Then, for the first time, I saw the loading screen. BUT it was all grainy and there was two duplicate screens. I pushed print screen (and pressed enter to save the image, because it is impossible to navigate. Then I pushed ctr alt backspace, and when I got back in, I learned that the image was flawless. That is: image from print screen shows nothing wrong, whilst on my actual screen, I could not even navigate. I took some pictures with my camera (see comparison pictures).

Also, when I first tried connecting to a server, I got the you're not logged in, problem, but when I restarted and tried again, it worked (still with the grainy problem). 

Note: if visual effects is not turned off, the screen flickers (darker areas rolls down the screen), but that's all.

---

### Post by Gcentrex on 2008-10-14
Yep that's the kind or error I have seen before on people with ATI configurations so I have an idea how to fix it now we can only try but at lease its getting some were now at the very least.

Open terminal/konsole then run regedit

Open the key

HKEY_CURRENT_USER\\Software\\Wine

Now open the key Direct3D if it is not their then create it, then creat these strings within it


"DirectDrawRenderer"="opengl"
"OffscreenRenderingMode"="backbuffer"
"PixelShaderMode"="enabled"
"UseGLSL"="disabled"
"VertexShaderMode"="hardware"
"VideoMemorySize"="128"

You might have to change PixelShaderMode to disabled as im not sure on that card but those settings should help you, before you try to re-run steam type this into the terminal/konsole 
wineserver -k
wineboot

That should kill the current wine server and do a simulated windows reboot its usefull to do it sometimes to be sure it uses the new settings.

Let me know how if these settings help.

---

### Post by madsc89 on 2008-10-14
I don't know how to attach strings...
Did I do it right?
Because I don't think what I did worked.

---

### Post by nathan42100 on 2008-10-14
Envyng worked for me, windowed, dxlevel 81

nvidia geforce fx 5200

I'll report back later on other stuff

Ok, not perfect, cinemetography is off, but the map loads

---

### Post by Gcentrex on 2008-10-14
> **madsc89 said:**
> I don't know how to attach strings...
Did I do it right?
Because I don't think what I did worked.

The first part is right the Direct3D folder but for strings 

New Value #1
DirectDrawRenderer

And its value would be opengl

you could open the file user.reg in your ./wine folder, search for this

```

[Software\\Wine\\Direct3D]
``` you will see were we got our wires crossed when you compare it to the what I put below.

Now change the current entry to this instead

```
"DirectDrawRenderer"="opengl"
"OffscreenRenderingMode"="backbuffer"
"PixelShaderMode"="enabled"
"UseGLSL"="disabled"
"VertexShaderMode"="hardware"
"VideoMemorySize"="128"
```

I have took a screen shot so you can see what I was getting at I only added one but you will get the idea

---

### Post by Gcentrex on 2008-10-14
> **nathan42100 said:**
> Envyng worked for me, windowed, dxlevel 81

nvidia geforce fx 5200

I'll report back later on other stuff

Ok, not perfect, cinemetography is off, but the map loads

With an Nvidia card it should run with no problems well mostly anyway.

Launch the game with these options 

-novid -dxlevel 81

These are good for most games rememeber after the first launch remove the -dxlevel 81 or it will reset your settings each time you run it again.

Also some other useful launch options are 
-heapsize 512000  <- set aside 512 ram instead of the default
+map_background none <- Good for Half-Life 2 but not the new games

Their are others but these are the usefull ones.

---

### Post by madsc89 on 2008-10-15
I'm going to try that out now.
Should my VideoMemorySize be 128? Because I've got 256...

Also, If it works, should I then remove -dxlevel 80 from launch options?

Thank you

---

### Post by madsc89 on 2008-10-15
Damn. It still doesn't work.

See the screen shot. Have I done it right?

Note that the screen goes bad the instance I push the launch button.

Also, when using the wineserver -k, nothing happens, and when using wineboot, I get some lines that start with "err:". I don't know what to look for, however. this is what it says: 
```

 CellID: Fetching server list from CSDS. . .
fixme:process:SetProcessShutdownParameters (00000100, 00000000): partial stub.
CellID: CSDS returned 168 servers.
CellID: Connecting to 69.28.151.170:27031. . .
CellID: Connect to 69.28.151.170:27031 took 200 MS
CellID: Nothing beat our old best time of 29 MS
err:ole:CoGetClassObject class {4590f811-1d3a-11d0-891f-00aa004b2e24} not registered
err:ole:CoGetClassObject no class object {4590f811-1d3a-11d0-891f-00aa004b2e24} could be created for context 0x1
fixme:shdocvw:ViewObject_SetAdvise (0x18f330)->(1 00000002 0x11e4f98)
fixme:shdocvw:PersistStreamInit_InitNew (0x18f330)
fixme:shdocvw:WebBrowser_put_RegisterAsBrowser (0x18f330)->(ffffffff)
fixme:shdocvw:WebBrowser_put_RegisterAsDropTarget (0x18f330)->(ffffffff)
fixme:shdocvw:ViewObject_SetAdvise (0x18f9a0)->(1 00000002 0x11e5000)
fixme:shdocvw:PersistStreamInit_InitNew (0x18f9a0)
fixme:shdocvw:WebBrowser_put_RegisterAsBrowser (0x18f9a0)->(ffffffff)
fixme:shdocvw:WebBrowser_put_RegisterAsDropTarget (0x18f9a0)->(ffffffff)
fixme:win:RegisterDeviceNotificationA (hwnd=0x10090, filter=0x33df78,flags=0x00000004),
	returns a fake device notification handle!

```

Also, I always push ctr alt backspace when the image gets grainy. Is that the right thing to do?

And my quit button in the upper right corner doesn't work, or at least, it takes a long time before anything happens, the computer is not responding in the mean time. Some days ago it did work, but when I then chose to shut down, restart etc. the computer hangs with only my background visible. This applies to restarts after updates as well. I think it first happened after I deleted a gutenprint entry in Synaptic. 
How do I fix this?

thank you

---

### Post by Gcentrex on 2008-10-15
It sounds like their is another issue here as using wineserver -k should shutdown all wine processes that are running everything, thats the reason for running the game in window mode so you can shut down the process if it goes wrong having a terminal already setup with the command typed out ready.

You have entered the information correctly into regedit thats perfect as far as I can see and also looks right considering the information posted on winehq's application database posts on half-life 2.

The reason for using 128 is because is half of your cards total ram thats just the way it is from my reading on winehq wiki.

Only thing I can think is can you run anything that uses opengl say a native linux game, since it sounds like you have another issue here if you could borrow an Nvidia card from someone to fit your pc then I would try it remove the driver Envy installed then use that card and use the correct driver for it and see if it works better.

The only thing I can say is if you can afford it maby a new PC or use windows xp again is the options I can think of myself maby look up about this error with the ATI driver see if their is a fix.

---

### Post by madsc89 on 2008-10-15
> **Gcentrex said:**
> It sounds like their is another issue here as using wineserver -k should shutdown all wine processes that are running everything, thats the reason for running the game in window mode so you can shut down the process if it goes wrong having a terminal already setup with the command typed out ready.

I think I misunderstood, because I believe there was no wine application running when I tried.. When Steam is running and I use that command, Steam just disappears. Which is what is supposed to happen? I just expected something to come up in terminal.

> **Gcentrex said:**
> 
Only thing I can think is can you run anything that uses opengl say a native linux game, since it sounds like you have another issue here 

I am at least able to run OpenArena and Compiz Fusion with advanced effects.. Also, a couple of months ago, I could enter TF2 without any obvious errors. That is, it crashed when connecting to a server. 

> **Gcentrex said:**
> 
The only thing I can say is if you can afford it maby a new PC or use windows xp again is the options I can think of myself maby look up about this error with the ATI driver see if their is a fix.

I really don't want to change back to XP.. GNU/Linux is so much better in so many ways. And when my computer works just fine with XP, and Ubuntu (except games), I don't want to spend a lot of money on new hardware.
Where would I look this error with ATI? Is there a link or something?

I would believe advanced Linux users could just look at some log and find the cause, but being that I'm still struggling with basic commands, I don't know a lot about Linux based systems.

You don't know anything about the shut down problems?

Thank you

---

### Post by madsc89 on 2008-10-15
> **nathan42100 said:**
> Envyng worked for me, windowed, dxlevel 81

nvidia geforce fx 5200

I'll report back later on other stuff

Ok, not perfect, cinemetography is off, but the map loads

My previous card actually was a FX 5200! I got seriously fed up with it, because it started leaking that yellow stuff, and I got BSOD's all the time. My current card is without doubt a better one. At least in Windows! XD

---

### Post by Gcentrex on 2008-10-15
> **madsc89 said:**
> I think I misunderstood, because I believe there was no wine application running when I tried.. When Steam is running and I use that command, Steam just disappears. Which is what is supposed to happen? I just expected something to come up in terminal.

Thats all its should do just shuts down everything to do with wineserver so thats anything run using wine :)



> **madsc89 said:**
> I am at least able to run OpenArena and Compiz Fusion with advanced effects.. Also, a couple of months ago, I could enter TF2 without any obvious errors. That is, it crashed when connecting to a server. 

Hum that seems really strange then as your able to run other applications in opengl but not windows games seems strange to me as hell :S , maby its the current wine version is bad for you, possibly try using wine 1.0 and not the new version and see if it works again you can always not update wine if that is the case.

> **madsc89 said:**
> I really don't want to change back to XP.. GNU/Linux is so much better in so many ways. And when my computer works just fine with XP, and Ubuntu (except games), I don't want to spend a lot of money on new hardware.
Where would I look this error with ATI? Is there a link or something?

I'm also the same I don't want to use windows anymore no way am I moving to Vista being a Beta tester and even tried the MSDN version told me everything I needed to know and that was I should really work on my Linux knowledge a lot more. I had read about it before now but not using an ATI card myself or anyone I know their was no need for me to read about it at the time. It might be a good idea to download the current drivers directly from the ATI web site and try to install them as I think even Envy does not install the most upto date version that might also help.

> **madsc89 said:**
> I would believe advanced Linux users could just look at some log and find the cause, but being that I'm still struggling with basic commands, I don't know a lot about Linux based systems.

You don't know anything about the shut down problems?

Thank you

Well I myself am not an advanced Linux user :lolflag: I have got my system up and running while learning as I go along and have no issues but I am using an Nvida card and they are better supported then ATI cards are in Linux thanks directly to ATI.

So only thing I can think of right now is looking more deeply into the issue with the ATI card I now don't even think this is a configuration issue but what has puzzled me is your able to run other applications just fine but not windows games maby a wine regression with ATI compatability I can't be sure.

As for the shut down issues I also do not have those also but my system is rather new, my old system about the same age as your one also runs just fine using Ubuntu 32bit even games no shutdown issue, best bet if you can is backup everything then reinstall Ubuntu do not use the new version of wine get a native linux game say openarena running then try wine versions from their or if we cant find anything then maby just use windows for the games for now but that is annoying.

If I can dig up information on the ATI card problem I will post about it.

---

### Post by madsc89 on 2008-10-15
Thanks for good reply.

I don't want to give up on this.

I did some googling and found this forum thread, where they fixed a similar problem, but being a Linux noob, I can't get that much sense out of it.
Maybe you could take a look at it?
[http://bbs.archlinux.org/viewtopic.php?id=51577&p=2](http://bbs.archlinux.org/viewtopic.php?id=51577&p=2)

Thanks a lot.

---

### Post by Gcentrex on 2008-10-15
I did a little look also it "seems" (cant be sure be its worth a shot) the 8.5 ATI drivers do not have this issue so its worth a try the instructions to install ATI drivers are here

```
http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide
```

And a link to 8.5 installer is this
```
https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-8-5-x86.x86_64.run
```

I would follow the guide and just download the above version instead of the latest driver listed on the guide, properly un-install envy and the driver it install should do it easy enough just check the site to do that.

---

### Post by madsc89 on 2008-10-16
It's working!

Whoopdidoo! :P

However, not perfect.

My log on screen is now completely off. It's stretched a lot vertically. This actually means that I can't turn off my computer. Because the quit button doesn't work, I always use ctr alt backspace and choose to shut down at the log on screen.

Also, the game lags a lot.

I'll try messing around with the video settings in game...

Thank you!

---

### Post by Gcentrex on 2008-10-16
Hum when you have logged on look at the resloution and check what rate it is set to and also try different resolution settings might help with the screen stretch issue. While your at it make sure "Visual Effects" are set to none again it might have been re-enabled after installing the new drivers.

As for the games try removing the changes we did to wine firstly, then when you have the game is launched try change the Filtering mode to a lower one, if it seems to play better after that then make sure you remove the launch option from the game ```
-dxlevel 81 or -dxlevel 80
``` it might also be possible to launch the games using ```
-dxlevel 70
``` but use that as a last resort measure.

Then you will be able to save your settings from then on also consider using this launch option ```
-novid
``` it will disable the startup video for source engine based games.

Other things I can say is make sure the steamapps folder is on a Linux drive and not just linked to the Linux system, also check that the files have not become fragmented you can do this by doing a right click over the game and picking "properties" from their pick "Local files" if it shows fragmentation then pick the "defragment cache files"

Also if you notice your text is hard to read in game that is an easy fix, go to your windows drive and copy your fonts folder (windows format C:\windows\fonts\) copy all .ttf files to wine's font folder then you will have better fonts in windows applications from then on.

---

### Post by madsc89 on 2008-10-16
> **Gcentrex said:**
> Hum when you have logged on look at the resloution and check what rate it is set to and also try different resolution settings might help with the screen stretch issue. While your at it make sure "Visual Effects" are set to none again it might have been re-enabled after installing the new drivers.

As for the games try removing the changes we did to wine firstly, then when you have the game is launched try change the Filtering mode to a lower one, if it seems to play better after that then make sure you remove the launch option from the game ```
-dxlevel 81 or -dxlevel 80
``` it might also be possible to launch the games using ```
-dxlevel 70
``` but use that as a last resort measure.

Then you will be able to save your settings from then on also consider using this launch option ```
-novid
``` it will disable the startup video for source engine based games.

Other things I can say is make sure the steamapps folder is on a Linux drive and not just linked to the Linux system, also check that the files have not become fragmented you can do this by doing a right click over the game and picking "properties" from their pick "Local files" if it shows fragmentation then pick the "defragment cache files"

Also if you notice your text is hard to read in game that is an easy fix, go to your windows drive and copy your fonts folder (windows format C:\windows\fonts\) copy all .ttf files to wine's font folder then you will have better fonts in windows applications from then on.

My resolution is 1280 x 1024 @ 75 Hz, as it's always been... My monitor's max... It's like the resolution changes for the login screen, then changes back when I log on.


Do you want me to remove all the strings I added in regedit? 

I've removed all the launch options already;)

Files is not fragmented, and the steamapps was created when installing steam where it is.

The visual experience in the game menus is almost as windows. No bad font or anything.

I've found that the game crashes a lot, though! It's always crashed after 5 minutes or so after joining a server. Then I have to pull the plug, because nothing responds.

---

### Post by madsc89 on 2008-10-16
I solved the login screen resolution problem.

I had to change this entry in my /etc/X11/xorg.conf file:

```

Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[0]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
		EndSubSection
EndSection

```

Into this (the preferred resolutions for your screen): 
```

Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[0]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
		Modes		"1280x1024" "1024x768" "1280x960" "640x480" "800x600"

	EndSubSection
EndSection

```

---

