---
title: "[SOLVED] Screen resolution in WoW problem #1"
date: 2008-09-17
forum: Wine
---

### Post by Ghliofris on 2008-09-17
I have WoW running through Wine. Finally got sound to work. I have to run it in windows mode (problem #2). I have Wine set to 1280x768, which it opens to that size. When I run WoW, it automatically drops to 800x600, which is the game resolution. I have tried to change it in the game but get this error from WoW:

This application has encountered a critical error:
ERROR #132 (0x85100084) Fatal Exception
Program:    C:\Program Files\World of Warcraft\WoW.exe
Exception:  0xC0000005 (ACCESS_VIOLATION) at 0073:7DAB43C0

The instruction at "0x7DAB43C0" referenced memory at "0x000008F4".
The memory could not be written.

any ideas? WoW forums are for Windows users. I saw somewhere that it could be a 3D problem.....

---

From the beginning:

Started off with Ubuntu 8.04 Hardy. Had a Radeon 9000 Pro 128meg video card. Couldn't get it to run proper. Spent 2 months on this little project.

Downgraded to a Jaton MX400 Nvidia card. Worked better than the Radeon. But frame rate in WoW was down to 7! But could run it in full screen mode.

Bought a PNY Nvidia GeForce 6200 256meg. Seemed to install just fine, with some trouble shooting. 

I have an Acer AL1914 LCD monitor.

Now when I try to run WoW in full screen, The monitor pops up an annoying little message that dances around the screen saying "Input not supported"

I really would like to run in full screen mode. 

Also, sideline, noticed that if I have Firefox open while playing, my frame rate decreases. When I close it, the frame rate goes up. Which has me wondering, are the drivers for the video card installed and proper ones?

---

### Post by hikaricore on 2008-09-17
First off I hope you don't mind but I've merged your threads.

Given your hardware and the possible simplicity of the issue, it was easier for me and will likely be easier for others to help you in a central location.

For your issue with resolution there's been a long standing bug with WoW under wine involving changes to the video setting crashing the client.  There is a mod that I can suggest to you which will allow some of these setting to be changed without a crash and settings which may cause a crash to be ignored.

You can find this addon here:
[http://www.wowinterface.com/downloads/info5202-ApplyToForehead.html](http://www.wowinterface.com/downloads/info5202-ApplyToForehead.html)

Now for a simple resolution change if you're running the game windowed or full screen I'll have to suggest you change this manually in your Config.wtf file.
This file is located under ~/.wine/drive_c/Program\ Files/World\ of\ Warcraft/WTF/

You will find the line you need to change labeled "gxResolution" it is likely set at 800x600 by default.  While you're editing this file you may also want to look for a line labeled "gxApi" to see if its set to OpenGL.  If it's not or it doesn't exist add it like such:

> gxApi OpenGL

Anywhere in the file.  Being sure it doesn't already exist as a second entry will likely just be removed by the game and cause no change to take place.

Under linux running games that support OpenGL with hardware that has OpenGL support is key to a good gaming experience.  This may completely absolve your fps troubles, however if it does not, there are other things you can check.

After saving this file and starting your game if your video issues such as fps are still present, you'll need to check that your drivers are properly installed.

From a terminal window run the following:

> glxinfo | grep rendering

This should return to you a "direct rendering: Yes".
If it does not search around our forums for info on installing the latest Nvidia drivers or use a tool such as Envy to do it for you.  Personally i recommend doing it yourself as this will provide a better understanding of how to fix driver related issues you may have in the future.

Best of luck.

--Aaron

---

### Post by Ghliofris on 2008-09-18
> Now for a simple resolution change if you're running the game windowed or full screen I'll have to suggest you change this manually in your Config.wtf file.
This file is located under ~/.wine/drive_c/Program\ Files/World\ of\ Warcraft/WTF/

You will find the line you need to change labeled "gxResolution" it is likely set at 800x600 by default. While you're editing this file you may also want to look for a line labeled "gxApi" to see if its set to OpenGL. If it's not or it doesn't exist add it like such:

Quote:
gxApi OpenGL
Anywhere in the file. Being sure it doesn't already exist as a second entry will likely just be removed by the game and cause no change to take place.

Did the edit, added gxApi "OpenGL" and it worked in windows mode! Now I can play without my glasses:lolflag:.

Reset Wine to lay in full screen mode, it came up no problem, no more "input not supported" window. But now my keyboard doesn't work. :confused:
Mouse works fine. Dumped out of WoW and opened CounterStrike and same thing, no keyboard.

Here is my keyboard section from xorg.conf:

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Due to working on various video card problems, the first and second option doesn't look familiar.

<edit>I commented out the options in the keyboard section and still no keyboard in full screen mode.<edit>


Anyways, thanks again for your help. If you play WoW on Stonemaul I play Whisperra, Rnurserogue and Akina. Drop by for some mead, my treat :)

---

### Post by Ghliofris on 2008-09-18
Ok all set, just set Wine windows the same screen resolution as my desktop. Just like running full screen! :biggrin:

<edit>Frame rate is running a steady 40!<edit>

Thanks again.

---

