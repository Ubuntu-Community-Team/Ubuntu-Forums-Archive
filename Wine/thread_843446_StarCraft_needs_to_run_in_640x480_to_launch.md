---
title: "StarCraft needs to run in 640x480 to launch"
date: 2008-06-28
forum: Wine
---

### Post by gamelord12 on 2008-06-28
I have a LAN party at a friend's house in a few days, and we'll all be playing StarCraft.  I've got a desktop that runs Windows, but for the sake of carrying a computer, my only option is my laptop that runs Ubuntu.  I installed StarCraft, the expansion, and all patches, including the no-CD feature from the newest patch.  The game is ready to go.  However, I need to run the game in 640x480 or I get a Direct3D error.  I go into Wine Config and it gives me the option to run all Wine programs in a virtual desktop of whatever resolution I desire, but I can't full-screen that window.  How do I get StarCraft to run the way I want it?  I did it before I re-installed 7.10 (8.04 gives Dell laptops some issues like no sound) but don't remember how.  I'd like to be able to:

1. Get the game running full-screen.
2. Preferably have it maintain the same aspect ratio.  I have a 16:10 screen, and it stretches everything.  This isn't quite as important as number 1.

---

### Post by gamelord12 on 2008-06-28
Also, I tried turning up my DPI to artificially make StarCraft draw larger on the screen.  Turns out all it did was make the text in the WINE configuration screen completely unusable.  How do I reset that to defaults?

---

### Post by mriedel on 2008-07-09
I got it to run by adding a modeline to /etc/X11/xorg.conf that turned off my second monitor and set my primary monitors resolution to 640x480. That's with wine's virtual desktop setting disabled. I set the modeline through nvidia-settings which also allowed me to disable stretching for resolutions that don't fit my (16:10) monitor. The modeline should be no problem if you have a non-nvidia card (just edit xorg.conf directly), but about the stretching I don't know.

Still I don't feel the above is the perfect solution. I'd love to have starcraft run in a maximized window on my primary screen with my secondary screen still turned on and wine's "allow directx to keep the mouse from leaving the window" (or similar) setting actually working (it does nothing for me).

---

### Post by Felson on 2008-07-09
Try running it with [this]("http://ubuntuforums.org/showthread.php?t=854354")
Just posted this, and it may be an answer to your problem.

---

