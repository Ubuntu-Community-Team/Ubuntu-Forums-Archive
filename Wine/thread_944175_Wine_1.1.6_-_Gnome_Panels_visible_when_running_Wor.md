---
title: "Wine 1.1.6 - Gnome Panels visible when running World of Warcraft"
date: 2008-10-11
forum: Wine
---

### Post by Humph on 2008-10-11
I've just updated WINE to 1.1.6, and now when I run World of Warcraft both the top and bottom Gnome Panels are visible, but they weren't before this update.  Is there a way to hide the Gnome Panels when playing WoW or is there a way to roll back WINE to an earlier version?

---

### Post by Perfect Storm on 2008-10-11
Have you tried disable compiz while running WoW?

---

### Post by Humph on 2008-10-11
> **Artificial Intelligence said:**
> Have you tried disable compiz while running WoW?

I have all desktop effects turned off by default.

---

### Post by Perfect Storm on 2008-10-11
Try with
```
metacity --replace
```

instead and see if it helps.

---

### Post by asdfoo on 2008-10-11
> **Humph said:**
> I have all desktop effects turned off by default.

Also reported here [http://forum.winehq.org/viewtopic.php?t=2511](http://forum.winehq.org/viewtopic.php?t=2511)

---

### Post by Humph on 2008-10-11
> **Artificial Intelligence said:**
> Try with
```
metacity --replace
```instead and see if it helps.

I tried that, but without success. :(

---

### Post by hotcarl on 2008-10-11
I'm having the same problem.  Any help would be appreciated :)

---

### Post by yuminig on 2008-10-11
try wine configuration then go to graphics tab then change the "allow the window manager.... "

---

### Post by Humph on 2008-10-11
> **yuminig said:**
> try wine configuration then go to graphics tab then change the &quot;allow the window manager.... &quot;

Nope. Panels still visible. Tried with one or other and both the "allow the window manager..." options. :(

---

### Post by david_kt on 2008-10-12
> **Humph said:**
> I've just updated WINE to 1.1.6, and now when I run World of Warcraft both the top and bottom Gnome Panels are visible, but they weren't before this update.  Is there a way to hide the Gnome Panels when playing WoW or is there a way to roll back WINE to an earlier version?

Open synaptic, click wine, press <ctrl> <E> (force version), and then select the version you want.

After that, click package and lock version to make sure it do not upgrade in the future. If you want to have multiple wine and the reasons why, please see below 2 threads:

[http://ubuntuforums.org/showthread.php?t=944949](http://ubuntuforums.org/showthread.php?t=944949)
[http://ubuntuforums.org/showthread.php?t=942269](http://ubuntuforums.org/showthread.php?t=942269)

DK

---

### Post by oronte on 2008-10-12
There's a much easier way. You need to install the Compbiz settings manager. Go to the general options (enable them), open the game you want to play, click the plus (grab) button on the fullscreen line and click on your game. Now reopen your game and it should be fine. Worked for me on Neverwinter 2. I'm assuming you're running the game in a virtual/emulated desktop.

---

### Post by louisgag on 2008-10-13
thanks oronte!

I installed compiz options (without enabling the visual effects)

And by doing an advanced search in the settings for "fullscreen" I found the "Extra VM actions" options and used it to enable a keybinding for toggling fullscreen.. Then, back to wow I simply pressed the keys I had just bound and my game was back to real fullscreen, no gnome bars

(will only work if I leave the compiz-settings window open while I play)

---

### Post by oronte on 2008-10-13
> **louisgag said:**
> thanks oronte!

I installed compiz options (without enabling the visual effects)

And by doing an advanced search in the settings for "fullscreen" I found the "Extra VM actions" options and used it to enable a keybinding for toggling fullscreen.. Then, back to wow I simply pressed the keys I had just bound and my game was back to real fullscreen, no gnome bars

(will only work if I leave the compiz-settings window open while I play)

My apologies I pointed you to the wrong setting. Go to Window Rules under Window Management and choose the grabber next to the full screen option (don't forget to enable window rules) now it should work perfectly.

---

### Post by Humph on 2008-10-13
> **oronte said:**
> My apologies I pointed you to the wrong setting. Go to Window Rules under Window Management and choose the grabber next to the full screen option (don't forget to enable window rules) now it should work perfectly.

I was unable to get that to work. Probably something I was doing wrong, as I'm not very familiar with Linux.  I did, however, revert to WINE 1.0 following david_kt's suggestion, and I've got rid of those pesky Gnome Panels.

---

### Post by asdfoo on 2008-10-13
fyi - someone has filed a bug report here: [http://bugs.winehq.org/show_bug.cgi?id=15598](http://bugs.winehq.org/show_bug.cgi?id=15598)

---

### Post by SniperSlap on 2008-10-15
With compiz enabled, you will always see the bar no matter what you do.

**If you disable compiz**, do the following:

*Applications -> Wine -> Configure Wine : Graphics - Emulate a Virtual Desktop*

Make sure that is checked off.  Once you've done that, under "Desktop size", put in your full screen resolution.  That value is going to be the highest and exact same resolution that you prefer to run WoW at.  For me, I run at 1920x1200 on one machine (widescreen) and 1280x1024 on another (regular).  Some other common values are 1024x768, 800x600, 1152x864 and 1280x800.

Don't forget that after the update to the latest version (Oct 14th WotLK patch), a new desktop shortcut is created by the updater.  This new shortcut will not run the game in OpenGL mode if you are using the commandline "-opengl" switch.

The bug mentioned by asdfoo is now confirmed and it looks like a fix will be out for the next version of WINE.  So remember what you do so you can undo it after you update next time - I'm sure all the solutions people are trying have been costing them resources and/or functionality they shouldn't be required to sacrifice.

---

### Post by Cuppa-Chino on 2008-11-06
there is a patch published here:

[http://www.winehq.org/pipermail/wine-patches/2008-October/063232.html]("http://www.winehq.org/pipermail/wine-patches/2008-October/063232.html")

but how is it applied and is it safe?

for what its worth I am going back to 1.1.5

---

### Post by YokoZar on 2008-11-06
> **Cuppa-Chino said:**
> there is a patch published here:

[http://www.winehq.org/pipermail/wine-patches/2008-October/063232.html]("http://www.winehq.org/pipermail/wine-patches/2008-October/063232.html")

but how is it applied and is it safe?

for what its worth I am going back to 1.1.5
Or you can go forward to 1.1.7, which already has the patch.

---

### Post by tafbuntu on 2009-11-30
I'm running 9.10 and I can't get the whole screen to populate? Even after configuring wine.cfg to match current x server display settings? 
Help. I've searched everywhere and tried everything the threads say. Want to maximize on the 64bit amd ubuntu with 8gb ram as XP only sees 3gb.

---

