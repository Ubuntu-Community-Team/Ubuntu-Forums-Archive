---
title: "fifa 08 and wine"
date: 2007-11-26
forum: Wine
---

### Post by sourcemorph on 2007-11-26
ok i tried running fifa 08 with wine and im facing a couple of problems...

1. the game doesn't run fullscreen... a couple of times i managed to get it full screen but i don't know how it happened.

2. the speed of the game becomes weird sometimes, it doesn't freeze but it sort of the change of frames becomes uneven n it gives a very blurry kinda performance.

and yeah i have a compaq presario v3150, it has nvidia 6150 controller.. which graphics card driver shud i use? nvidia 6 series (open/propreitery) or nvidia 256 or nvidia integrated thing... ??

---

### Post by TidusBlade on 2007-11-26
I dont know much about the video problems, but you can try using the nVidia driver from the Restricted drivers manager, if you have, or it dosen't work, then try the other ones. If both dont work at solving your problem try messing around the WINE settings by typing 'winecfg' in the terminal ;)

---

### Post by sourcemorph on 2007-11-27
yeah the fullscreen prob got solved by deselecting the "allow the windor manager to control the windows" option...

what can i do for the awkward frames??

---

### Post by ozanuzay on 2010-10-08
i could not open the setup exe file :( 
how can i install the fifa 2008 ????

---

### Post by ozanuzay on 2010-10-09
i opened exe file But now, There is a Grafic requirement error on fifa 2008 !!

---

### Post by ronnielsen1 on 2010-10-09
Here's some suggestions from winehq

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=9051](http://appdb.winehq.org/objectManager.php?sClass=version&iId=9051)
> I'll suggest to add a "local.ini" file in the game directory with these settings (change them as you want): 

RESOLUTION = 1280x800x32 
QUALITY = 2 
RENDER_QUALITY = 2 
WINDOWED = 0 
WIDESCREEN = 1 
VIDEO = 1 
AUDIO = 1 
SPEECH = 1 
NO_EXTRA_TIME = 0 
NEVERENDING_GAME = 0 
SKIP_TITLE = 1 

You can find more settings in google, those are the ones I'm using in my laptop... 

Btw, using enabling the UseGLSL Direct3D registry string, or setting the real amount of vram in VideoMemorySize the game, goes too quick :P. 

I get better fps using "fbo" or "pbuffer" OffscreenRenderingMode.

---

