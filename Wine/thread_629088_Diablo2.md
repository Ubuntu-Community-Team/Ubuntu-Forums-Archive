---
title: "Diablo2"
date: 2007-12-02
forum: Wine
---

### Post by diablo69-0621 on 2007-12-02
I got diablo 2 working under wine, but its not fullscreen...is there anyway I can change it to full screen, b/c when I go into wine cfg to change the size of the emulated desktop, it just reverts it back to the default even as a root user.

---

### Post by cogadh on 2007-12-02
NEVER, EVER RUN WINE AS ROOT! 

Using root or sudo to run Wine allows Wine full access to the entire system. In a best case scenario, this will mean that any applications installed with Wine will have root only permissions and a normal user will not be able to run them. In a worst case scenario, whatever you install hoses up your entire system or worse yet, gives a Windows virus full, unrestricted access to your system (not a good thing). If you tried configuring Wine as root, then you should delete your .wine directory and start fresh with one that has not been touched by root at all.

As for your full screen issue, just turn off the "Emulate virtual desktop" option and the game will go into full screen, provided the game is running at a resolution that is already present in your xorg.conf.

---

### Post by diablo69-0621 on 2007-12-02
I turned off the emulate desktop, and this time it refuses to open the game.

---

### Post by cogadh on 2007-12-02
I'm assuming that you have started fresh with an non-root affected .wine directory? If you have, then it is likely that whatever resolution the game is trying to run at is not available in your xorg.conf. Any error messages that were output to the terminal when you ran the app would be helpful in determining that. Post back with that info and we'll se what we can come up with.

---

### Post by diablo69-0621 on 2007-12-02
The error is as follows...

diablo69-0621@diablo69-0621-laptop:~$ wine /home/diablo69-0621/.wine/drive_c/Program\ Files/Diablo\ II/D2Loader-1.11b.exe 
libGL error: drmMap of framebuffer failed
ALSA lib conf.c:3949:(snd_config_expand) Unknown parameters 0
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL default:0
fixme:win:EnumDisplayDevicesW ((null),0,0x34f91c,0x00000000), stub!
fixme:ddraw:IDirectDrawImpl_SetCooperativeLevel (0x13c490)->(0x20024,00000011)
fixme:ddraw:IDirectDrawImpl_SetCooperativeLevel (0x13c490)->(0x20024,00000011)
fixme:x11drv:X11DRV_desktop_SetCurrentMode Cannot change screen BPP from 32 to 8
fixme:ddraw:IDirectDrawImpl_SetCooperativeLevel (0x13c490)->(0x20024,00000011)
fixme:x11drv:X11DRV_desktop_SetCurrentMode Cannot change screen BPP from 32 to 8
fixme:x11drv:X11DRV_desktop_SetCurrentMode Cannot change screen BPP from 32 to 16

---

### Post by cogadh on 2007-12-02
It looks like it might not be the resolution, but the bits per pixel, The game is trying to reset your desktop to 16 or 8 BPP from the default 32 (actually 24) and it can't. You should check your xorg.conf config to be sure those two BPP settings are available.

On a probably completely unrelated note, you shouldn't run the game using the long path command. Windows applications usually like to be running from the directory where they are installed, so it is better to change directories to the game directory first, then "wine" the executable:
```
cd ~/.wine/drive_c/Program\ Files/Diablo\ II/
wine D2Loader-1.11b.exe
```
Also, is that the correct name for the game's executable? It's been a while, but I thought it was simply "Diablo II.exe"?

---

### Post by diablo69-0621 on 2007-12-02
can you provide instructions on how to check my xorg conf and what to look for?

---

### Post by diablo69-0621 on 2007-12-02
> Also, is that the correct name for the game's executable? It's been a while, but I thought it was simply "Diablo II.exe"?


On  side note, that is a patch to run the game without the cd.

---

### Post by cogadh on 2007-12-02
That may be part of the problem, the game doesn't run well in Wine with a crack and its not required anyway, the copy protection for the game works.

As for checking your xorg.conf, the file is found in /etc/X11. Open it with the text editor (you won't be able to edit it) and look for the section marked "Screen". It will look something like this:
```
Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"SyncMaster"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
#		Virtual	1400	1050
		Modes		"1024x768@85"	"1024x768@75"	"1024x768@70"	"800x600@60"	"1024x768@60"	"800x600@85"	"800x600@75"	"640x480@85"	"640x480@75"	"640x480@60"
	EndSubSection
EndSection
```
Post the content of it and maybe we can come up with something.

---

### Post by diablo69-0621 on 2007-12-02
Here is what was in xorg

Section "Screen"
        Identifier      "Default Screen"
        Device          "Generic Video Card"
        Monitor         "Generic Monitor"
        Defaultdepth    24
        SubSection "Display"
                Modes           "1400x1050"
        EndSubSection
EndSection

---

