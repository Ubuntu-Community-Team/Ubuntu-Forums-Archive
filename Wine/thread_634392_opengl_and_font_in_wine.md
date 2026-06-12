---
title: "opengl and font in wine"
date: 2007-12-07
forum: Wine
---

### Post by loonytune on 2007-12-07
hi
i want to run a very (VERY) old game in wine. it requires 265 colors and 800x66 so i run it in wine in vnc!
when i enter wine FALLEN.EXE in the shell in vnc it gets all dark and i'm informed that an unexpected error occurred.

the log file of the vnc servers says:
Fri Dec 7 15:16:10 2007
vncext: VNC extension running!
vncext: Listening for VNC connections on port 5902
vncext: created VNC server for screen 0
Could not init font path element /usr/share/fonts/X11/TTF/, removing from list!
Could not init font path element /usr/share/fonts/X11/OTF, removing from list!
Could not init font path element /usr/share/fonts/X11/CID/, removing from list!
twm: line 1: ignoring unknown keyword: include
twm: line 1: error in input file: syntax error
twm: line 1: ignoring unknown keyword: defs
twm: errors found in twm string list

the shell in the vnc says:
Xlib: extension "GLX" missing on display ":2.0".
err:wgl:X11DRV_WineGL_InitOpenglInfo couldn't initialize OpenGL, expect problems
Xlib: extension "GLX" missing on display ":2.0".
err:wgl:X11DRV_WineGL_InitOpenglInfo couldn't initialize OpenGL, expect problems

some help would be nice, P.

---

### Post by cogadh on 2007-12-07
Why are you running it through VNC? That adds an extra layer of potential problems to running Wine and I would imagine that it is not recommended. Also, what game are you trying to run?

---

### Post by loonytune on 2007-12-07
I'm running Fallen Haven. I run it in vnc because it requires 256 colors. I haven't found a way of setting my wine to 256 colors. I've already tried to set my ubuntu(ubuntu 7.10 gnome) to 256 colors by changing the config file. => disaster, my laptop wasn't able to boot anymore. so i thought it is the easiest way to do this that way ...

EDIT: this is proposed by the wine homepage as a "256-colors-problem-workaround"

---

### Post by cogadh on 2007-12-07
Well, that game is not even listed on Wine's Application Database, which is almost always not a good sign. Every game I have found that is not listed on AppDB won't run at all.

All you should need to do to get 256 colors is add an available option for 8 bit colors to your xorg.conf, but AFAIK, most laptop screens can't do lower than 16 bit color.

---

### Post by loonytune on 2007-12-08
how can i add an option to the xorg.conf. I'tried everything and the only way I found to change my colors is in the config file, and as I already said - this didn't work.

---

### Post by cogadh on 2007-12-08
All you should have to do is add an entry for 8 bit depth to the screen section in your xorg.conf. Here's what mine looks like:
```
Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"SyncMaster"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Modes		"1024x768@85"	"1024x768@75"	"1024x768@70"	"800x600@60"	"1024x768@60"	"800x600@85"	"800x600@75"	"640x480@85"	"640x480@75"	"640x480@60"
                Depth   16
                Modes		"1024x768@85"	"1024x768@75"	"1024x768@70"	"800x600@60"	"1024x768@60"	"800x600@85"	"800x600@75"	"640x480@85"	"640x480@75"	"640x480@60"
		Depth	8
		Modes		"1024x768@85"	"1024x768@75"	"1024x768@70"	"800x600@60"	"1024x768@60"	"800x600@85"	"800x600@75"	"640x480@85"	"640x480@75"	"640x480@60"
	EndSubSection
EndSection
```
Don't directly copy mine, it will likely not work for you at all. However, like I said, most laptop screens can't do 8 bit color, so if you already tried this, that may be why it couldn't boot.

---

### Post by loonytune on 2007-12-08
already tried that, as i said - couldn't boot anymore ...
maybe this game just won't work ....

---

