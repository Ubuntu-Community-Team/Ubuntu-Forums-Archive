---
title: "GrabIt window dissapearing on desktop switch"
date: 2007-12-06
forum: Wine
---

### Post by jorwex on 2007-12-06
Hey all. I'm using wine 0.9.40 with aksel's patch so I could use SketchUp (works great now!).

The only thing i needed was GrabIt, which works from what I can see. Except for one thing. If I change desktops (rotate compiz cube), and rotate back to the original one with GrabIt running, it'll be gone. No sign of it on the taskbar, and I can't switch to it with alt-tab. Here's a terminal log:

$ wine GrabIt
fixme:win:SetLayeredWindowAttributes (0x1002a,0x00000000,240,2): stub!
err:systray:delete_icon invalid tray icon ID specified: 10186528
fixme:systray:handle_incoming unhandled tray message: 4
err:systray:delete_icon invalid tray icon ID specified: 10186528
err:systray:delete_icon invalid tray icon ID specified: 10186528

and it stays running there and doesn't exit. I don't know too much about Ubuntu yet (recent windows deserter) so I don't really know if there's a "Bring process to front" equivalent that I might be able to try.

It also crashed once when I added things to the batch. Doesn't seem like its easily reproducable tho. I'm mostly concerned with the desktop switching bug.


Any advice?

---

### Post by cogadh on 2007-12-06
Generally speaking, Wine and Compiz don't work well together and Compiz should be disabled before running applications with Wine. However, have you tried simply using ALT-TAB to see if the application will come back up?

---

### Post by jorwex on 2007-12-06
ya i tried that.

however, after reading a bit, I disabled the window manager and let it set up a virtual desktop window, and now its working great. 

for some reason though, if i launch a second program in the virtual desktop (sketchup) it wont display correctly. the left half of the sketchup window will be on screen, but the right half will be chopped off, and i cant resize it or move it to see the missing portion.

weird eh?

---

