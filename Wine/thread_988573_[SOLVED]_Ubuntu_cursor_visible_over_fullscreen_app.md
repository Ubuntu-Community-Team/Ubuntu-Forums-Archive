---
title: "[SOLVED] Ubuntu cursor visible over fullscreen apps"
date: 2008-11-20
forum: Wine
---

### Post by Capt. Mac on 2008-11-20
When I use full screen applications like Fallout or Starcraft, my main cursor (not the one actually used by the application) shows up in the middle of the screen. If I slide my mouse to the side really quickly while the program is booting I can hide it on the right side of the screen, but I was curious if there was an actual fix for this. I also encounter this when running native Quake 3 fullscreen or dosbox. While searching Google it indicated that it might be an OpenGL problem.

I read one creative solution that was simply to make the Ubuntu cursor transparent, but I'd rather not resort to that. Anyone know of a true fix?

---

### Post by AndrewRiedi on 2008-11-21
1) Does the game function (as far as the cursor goes) in windows XP?

2) Have you tried Wine 1.1.9?  (I got a couple cursor patches accepted - although I don't think any of them will fix this particular issue, it might be worth a try.)

3) Have you made a bug report with the [Wine Bugzilla]("http://bugs.winehq.org") yet?  (So the bug doesn't get lost.)  A bug report doesn't in any way guarantee that the bug will be fixed, but it does at least let the interested developers know that the bug is there.

If you decide you want to file a bug report, please include these things:
3a) Description of exactly how to reproduce the error.
3b) Graphics card/driver versions.
3c) Set the version to the output of 'wine --version'.
3d) In the initial bug, leave everything you are unsure of as the defaults.
3e) Any logs developers may ask for.

4) If you don't want to file a bug report for various reasons, I would still appreciate it if you could test with Wine 1.1.9 and post here letting me know if the problem still exists.

---

### Post by quanumphaze on 2008-11-22
This is not a Wine problem! It's probably a problem with the Intel graphics driver. I'm using an Intel 945GM.

I have this exact same behaviour in native Linux games (try Frozen Bubble, Starfighter and Gens for example).

Workarounds: (2nd works well for Fallout)[LIST]
[*]Quickly move the mouse to the lower right during the screen resizing
[*]Set a global key combo for fullscreen in "System->Preferences->Keyboard Shortcuts" (to Crtl+F11 for example, very handy WM function try it out on the file browser) Use virtual desktop in Winecfg, use xrandr to adjust the desktop size to fit the game
[/LIST]
If anyone here is good at writing bug reports you are quite welcome to.

---

### Post by quanumphaze on 2008-11-23
There is another thread in the General Help section about this I plan to hijack :D [[link]]("http://ubuntuforums.org/showthread.php?t=925046") where I hope we can shed some light on the fundamental problem. Feel free to post information about it and get enough info for a bug report (if there isn't one already).

---

