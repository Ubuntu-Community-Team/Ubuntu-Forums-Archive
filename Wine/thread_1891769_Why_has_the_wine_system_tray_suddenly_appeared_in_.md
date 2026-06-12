---
title: "Why has the wine system tray suddenly appeared in the top left corner ?"
date: 2011-12-06
forum: Wine
---

### Post by PM47 on 2011-12-06
I installed Ubuntu 11.10 a week or so ago and installed all my apps, including several Windoze apps running in Wine 1.2.3. One Windoze app places an icon in the desktop notification area, or at least it did until a couple of hours ago ! I've not installed any new apps or done any updates for a couple of days, re-booted earlier today and the icon that was in the desktop notification area has suddenly moved to a grey bar in the top left corner that forces the panel off the left of the screen. It seems the grey bar is the wine system tray. Why has this suddenly appeared and how do I get the Windoze system tray icon back onto the desktop notification area ? So far I've drawn a blank on this one :-(

---

### Post by kostkon on 2011-12-06
A screenshot would be helpful.

Are you using 11.10 with Unity?

---

### Post by PM47 on 2011-12-06
Thanks for your reply, yes I'm using Unity.

I've attached a screen-shot of the Wine system tray, the little red post box is the Windoze app system tray icon (Vpop3 mail server status app, Vpop3 itself is running on another PC). I've solved one problem however, the grey bar I referred to WAS the Wine system tray, with the title bar hidden under the top bar on the desktop. I've managed to grab it and move it out onto the desktop, hence the screen-shot.

What puzzles me is why, since I installed 11.10, has the icon for the Windoze app remained in the desktop notification area, then suddenly today I have a Wine system tray on the desktop with the Windoze app icon in it ?? More to the point how do I get the Wine system tray icon back into the desktop notification area and lose the Wine system tray as this was a lot more convenient ??

---

### Post by PM47 on 2011-12-07
Aaaaargh - this is so frustrating !!

The wine system tray window is now behaving itself and remaining where I put it on the desktop, not ideal, but workable. I'm still looking for how to move the icons back into the notification area.

Now one of my other Windoze programs is exhibiting similar behaviour, when I run it the window is fixed at the top left, this time OVER the top bar of the desktop with the title bar off the top of the screen. The left of the window is also off the screen. It appears to be exhibiting 'always on top' behaviour as everything, including the launcher, remains underneath it. In fact I've just noticed ALL the Windoze apps are now exhibiting 'always on top' behaviour !! Pressing the ALT key and clicking the window doesn't move it either so I'm now stuck and can no longer use the Windoze app, which is a problem as it's my preferred email program:-(

Any further suggestions would be most appreciated.

---

### Post by PM47 on 2011-12-20
I've still not found any way to determine how the wine system tray behaves apart from the following ; If I include the Windoze app as a startup app, so it runs automatically when I log on, I end up with a movable Wine system tray on the desktop. If I manually run the Windoze app from an icon on the desktop after I've logged on the Windoze system tray icon appears in the desktop notification area. I guess it must be something to do with exactly when Wine is started with respect to whatever process manages the notification area ?

---

