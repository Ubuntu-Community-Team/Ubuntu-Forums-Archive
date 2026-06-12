---
title: "Wine/Sketchup on 12.04"
date: 2012-08-16
forum: Wine
---

### Post by eslavko on 2012-08-16
Hello..

I Install GoogleSketchup in wine. In the 1'st I have trouble with GL settings. But searching the net find solution with registry editing and now works. But have problems with display.

1. On start of sketchup the main frame is transparent(or sometime black) until I click into.

2. Then to select the human icon I need to click it twice. 

3. When selected I press Delete key but I need to click on desktop to "redraw" screen without that image. (when pressed delete key they doesn't dissapair.

Probably some GL problem is still there. 
Any help?

Thanks

---

### Post by eslavko on 2012-08-16
Just more observation. 
Seems that sketchup lagging one event. (Mouse or keyboard click)

---

### Post by oldos2er on 2012-08-16
Moved to Wine.

---

### Post by drende on 2012-10-23
There is a way to get rid of the deferred selection misbehavior.

Start Sketchup with the command:

vblank_mode=0 /usr/bin/wine "path to Sketchup.exe"

In my case the command line is (on one line):

vblank_mode=0 /usr/bin/wine "/home/dag/.wine/drive_c/Program Files/Google/Google SketchUp 8/SketchUp.exe"

Try and enjoy!

---

### Post by omniEngr on 2013-02-02
If you don't want to run the command everytime you use sketchup, you can run gedit, and type in the command you use to run sketchup, and save it in "/usr/local/bin" as "sketchup" (no extension). then, still in gedit, open "~/.local/share/applications/wine/Programs/Sketchup 8/SkethchUp.desktop". on the third line, where is says Exec=blah blah blah. erase the stuff after Exec= (only erase stuff on line 3, lines 4-6 stay). after Exec=, type /usr/local/bin/sketchup and save it. now when you click sketchup in the dash, it runs your script, which starts sketchup the right way

---

