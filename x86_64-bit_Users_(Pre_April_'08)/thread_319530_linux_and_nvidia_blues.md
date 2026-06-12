---
title: "linux and nvidia blues"
date: 2006-12-15
forum: x86 64-bit Users (Pre April '08)
---

### Post by xstaticxgpx on 2006-12-15
Well i went back to windows for a short period of time to play games, I go really into WoW, and recently windows fed up twice in less than 4 days.. i relized I could play WoW on linux so i switched back. But during the period of time i was using windows, I got a nvidia video card (i used to have an ati, which worked perfectly with ubuntu). Now that im in ubuntu, nvidia has given me nothing but problem after problem... I thought nvidia was supposed to be better in linux? Not from what i can tell. It took me a long time to actually get the nvidia drivers working, and when they did work, my resolution wont stay. I try setting the resoluton to 1280x1024 in the nvidia settings panel, but in ubuntu they keep going back to 1024x768 (with 60 refresh rate). I tried adding 1280x1024 to my monitor modes in xorg.conf, but now ubuntu only recognizes it with a 50 refresh rate... I just want a stable computer so i dont have to reinstall everything 3 times a week... please can anyone help me with this nvidia problem?

---

### Post by rplantz on 2006-12-15
Ubuntu has always played nice with my nvidia geforce fx5200, 128 MB card. Beryl even works nicely with it.

But when I tried kde, I had problems similar to yours. I don't recall if I was ever able to fix it. I had lots of other problems with kde, so I simply went back to gnome.

If you're running kde, you might try searching the forums for kde and nvidia. And you might try changing the subject of your post to include "kde."

---

### Post by xstaticxgpx on 2006-12-18
No, i use gnome, kde is a memory hog.

well, i got my driver working, and i must say im impressed with how well WoW works with wine, very happy about that. But now theres a new problem, nvidia-settings wont save its settings, i got me res to work, but now my refresh rate wont stay at 75, in the ubuntu res app, it says the only refresh rates i can use are 50, 51, an 54. And when i set the refresh rate to 75 in nvidia settings, in ubuntu it says the refresh rate is 91. That doesnt really matter, but every time i restart my computer or restart x i have to go back into nvidia-settings and set my refresh rate. Same thing with my over clocks. I enabled cool bits for my drivers, and i found the "optimal frequencies" but everytime i restart my computer or restart x, they reset. I dont know whats going on, i just wish this would work as well as my ati.

---

### Post by RAOF on 2006-12-19
You need to set nvidia-settings to load on startup (in System->Preferences->Settings).  That way it'll reload your stuff.

And the crazy refresh-rate thing is a "feature" of the new nVidia drivers, AFAIK.

---

### Post by xstaticxgpx on 2006-12-22
sry i havnt replied, but ive been busy... still doesnt work adding nvidia-settings to startup

---

### Post by stfriesen on 2006-12-23
> **xstaticxgpx said:**
> sry i havnt replied, but ive been busy... still doesnt work adding nvidia-settings to startup

You need to add the "-l" parameter to load your settings.

nvidia-settings -l

---

### Post by xstaticxgpx on 2006-12-23
this is getting really stupid, it still doesnt work after adding nvidia-settings -l to start up... doesnt save my refresh rate or overclocking... it doesnt even save the "Enable Overclocking" checkbox option


EDIT**

i also get a bunch of error outputs when i start nvidia-settings in terminal

> xsx@xsx-desktop:~$ sudo nvidia-settings
Password:

ERROR: Cannot open display 'xsx-desktop:0.0'.


ERROR: Unable to assign attribute DigitalVibrance specified on line 19 of
       configuration file '/home/xsx/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute ImageSharpening specified on line 20 of
       configuration file '/home/xsx/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute SyncToVBlank specified on line 21 of
       configuration file '/home/xsx/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute AllowFlipping specified on line 22 of
       configuration file '/home/xsx/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute LogAniso specified on line 23 of
       configuration file '/home/xsx/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute FSAA specified on line 24 of configuration
       file '/home/xsx/.nvidia-settings-rc' (no Display connection).


ERROR: Unable to assign attribute TextureSharpen specified on line 25 of
       configuration file '/home/xsx/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute ForceGenericCpu specified on line 26 of
       configuration file '/home/xsx/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute CursorShadow specified on line 27 of
       configuration file '/home/xsx/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute CursorShadowXOffset specified on line 28 of
       configuration file '/home/xsx/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute CursorShadowYOffset specified on line 29 of
       configuration file '/home/xsx/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute CursorShadowAlpha specified on line 30 of
       configuration file '/home/xsx/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute CursorShadowRed specified on line 31 of
       configuration file '/home/xsx/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute CursorShadowGreen specified on line 32 of
       configuration file '/home/xsx/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute CursorShadowBlue specified on line 33 of
       configuration file '/home/xsx/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute FSAAAppControlled specified on line 34 of
       configuration file '/home/xsx/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute LogAnisoAppControlled specified on line 35 of
       configuration file '/home/xsx/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute RedBrightness specified on line 36 of
       configuration file '/home/xsx/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute GreenBrightness specified on line 37 of
       configuration file '/home/xsx/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute BlueBrightness specified on line 38 of
       configuration file '/home/xsx/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute RedContrast specified on line 39 of
       configuration file '/home/xsx/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute GreenContrast specified on line 40 of
       configuration file '/home/xsx/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute BlueContrast specified on line 41 of
       configuration file '/home/xsx/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute RedGamma specified on line 42 of
       configuration file '/home/xsx/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute GreenGamma specified on line 43 of
       configuration file '/home/xsx/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute BlueGamma specified on line 44 of
       configuration file '/home/xsx/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute OpenGLImageSettings specified on line 45 of
       configuration file '/home/xsx/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute XVideoTextureSyncToVBlank specified on line
       46 of configuration file '/home/xsx/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute XVideoBlitterSyncToVBlank specified on line
       47 of configuration file '/home/xsx/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute XVideoSyncToDisplay specified on line 48 of
       configuration file '/home/xsx/.nvidia-settings-rc' (no Display
       connection).


---

### Post by jacek2v on 2006-12-24
> **xstaticxgpx said:**
> ... It took me a long time to actually get the nvidia drivers working, and when they did work, my resolution wont stay. I try setting the resoluton to 1280x1024 in the nvidia settings panel, but in ubuntu they keep going back to 1024x768 (with 60 refresh rate). I tried adding 1280x1024 to my monitor modes in xorg.conf, but now ubuntu only recognizes it with a 50 refresh rate... I just want a stable computer so i dont have to reinstall everything 3 times a week... please can anyone help me with this nvidia problem?

Hi,

I previous use a ATI card - its work inUbuntu, next I switch to nvidia and ... its working better in Ubuntu :)
I have simmilary problems, that you have,  with ATI card.
Maybe you dont clean your configuration - ATI settings, check this:
[http://www.ubuntuforums.org/showthread.php?t=75074&highlight=nvidia](http://www.ubuntuforums.org/showthread.php?t=75074&highlight=nvidia)

Now I use 1600x1200x85Hz.
I dont use nvidia-settings - explicity :)

Here is part of my xorg.conf (important is monitor settings):
<part of xorg>
Section "Monitor"
	Identifier	"Compaq P900"
	Option		"DPMS"
	HorizSync	30-120
	VertRefresh	50-160
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA 6600GT"
	Monitor		"Compaq P900"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1600x1200" "1280x1024" "1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1600x1200" "1280x1024" "1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1600x1200" "1280x1024" "1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1600x1200" "1280x1024" "1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1600x1200" "1280x1024" "1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1600x1200" "1280x1024" "1024x768" "800x600"
	EndSubSection
EndSection

</part of xorg>

---

### Post by iamhugeinjapan on 2006-12-25
xstaticxgpx, it might help if you told us what nvidia video card you have now, what driver version you installed and how you installed the drivers.

I've never heard of putting nvidia-settings into the start up dialog, I don't do it myself either. But maybe it is necessary for some cards.

Are you using the same xorg.conf used with the ATI card or have you made a fresh one?

You can make a fresh one by going:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

