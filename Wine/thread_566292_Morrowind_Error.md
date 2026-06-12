---
title: "Morrowind Error"
date: 2007-10-03
forum: Wine
---

### Post by MMalen on 2007-10-03
Ok I've installed Morrowind on my laptop, and I know how to run it now.  But everytime I start it up I get this error.  

Music Error: Can not play file.  Data Files/Music/Special/morrowindtitle.mp3

the only option is to click ok.  I've read quite a few posts on this but none of them really have any solution for it.  If anybody that had this problem knows how to fix it please let me know here.  I don't want to get rid of the music files.  There must be a way to make them run.  Is there some patch somewhere you need?  

--Mass--

---

### Post by TidusBlade on 2007-10-03
Im not an expert or anything but Im guessing the file isint there so maybe try finding it on the CD or maybe it's renamed or something, just a thought :D

---

### Post by MMalen on 2007-10-03
No, that's not it.  I just found this solution on the wine website:

```
Music has to be erased from Data Files/Music prior running the game (required only for Wine < 0.9.36).
When game ask about mp3 files, press Esc.

In winecfg set vertex shader mode to hardware.
In winecfg set winver=win98 for best application behavior.

Make following changes in Morrowind.ini file:

;; Reduce CPU load
MaxFPS=40

;; Reduce crashes
SkipProgramFlows=1
DontThreadLoad=1

;; Improve loading times
;; RAM specific options (1/4 of total RAM for interior, 3/4 for exterior)
;; Examples for 1GB RAM machine
Interior Cell Buffer=256
Exterior Cell Buffer=768


You can get much better water rendering and rid of red inventory person artifacts using 3D acceleration:


[HKEY_CURRENT_USER\Software\Wine\Direct3D]
"OffscreenRenderingMode"="fbo"
"UseGLSL"="enabled"
"VideoMemorySize"="128" 
```

and it's running now but not in a playable way.  The screen is black and if you alt+tab out and back to it it is a little further forward in the opening video but it won't play normally at all.  Basically I start it up, it's a black screen with some fuzz in the corner.  If I alt+tab out of it and then back in again I catch a few seconds of the image as it loads plays the menu and I can move the mouse, then it goes black again or it just freezes on a frame. I can alt+tab again and once I managed to actually hit 'New" and start the opening video but eventually it just freezes completely and I have to reboot my computer.

---

### Post by MMalen on 2007-10-03
Delete

---

### Post by MMalen on 2007-10-09
Bump

Aaaaanybody at all?

---

### Post by Sklasko on 2007-10-09
The last time I tried Morrowind in WINE I had very little luck. There may be a workaround for your problem, but I would honestly suggest dual booting with Windows for gaming. WINE is rarely a sufficient solution.

---

### Post by NeoFax on 2007-12-01
Change the name of the mp3 file to ***.mp3.bak.  The game will still play.  Also, many of the problems that the Wine Wiki states and has possible solutions are not needed.  However, I use the Max FPS=40 and the SkipPorgramFlows=1 and DontThread=1 settings in my Morrowind.ini.  The only problems I have are the character screen when you right click is white and the mini-map is black and there is no way to tell in which direction you are going.  Other than this it is very playable.  If you need any help, let me know and I can send you my Morrowind.ini file.

---

### Post by ikeysmo on 2011-09-24
This is a little late, but the solution that worked for me was to use "Playonlinux" with latest wine version and on its options menu, go to install packages and install "Quartz" and "devenum" and it should load right up :)

---

