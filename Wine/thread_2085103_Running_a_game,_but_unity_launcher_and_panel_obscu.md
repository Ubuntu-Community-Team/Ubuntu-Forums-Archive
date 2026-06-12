---
title: "Running a game, but unity launcher and panel obscures view..."
date: 2012-11-17
forum: Wine
---

### Post by orange2k on 2012-11-17
I'm running Max Payne 2, but the problem is that I can't get rid of the annoying unity launcher and the top panel when running the game fullscreen...

Is there a way to turn them off somehow, because I can normally run the game only within gnome-shell environment, but want to run it inside stock Ubuntu?

---

### Post by anarchticgrimm on 2012-11-17
Are launcher and top panel covers the game window or game window seems like an ordinary maximized application like firefox, nautilus etc.? - Also, are you sure your wine configuration has no enabled virtual desktop option?

If none of them above and/or launcher and top panel covers the game window, then it may be a compiz problem. If you're using 12.04, can you play your game fullscreen under Unity 2D?

One more: Any other game does show the same behavior?

---

### Post by orange2k on 2012-11-17
I haven't tried any other games yet (I'm not a passionate gamer) so I don't know. And no, I haven't enabled virtual desktop option in wine. Well then, I'll just have to resort to Unity 2d or gnome-shell, I guess...

---

### Post by anarchticgrimm on 2012-11-17
Additionally, when your game is running, can you reach the top panel? If you can, is there any options for maximizing, minimizing or closing? (if, of course, top panel and launcher are not covering the game)

Or, it's just a compiz bug. =/

---

### Post by orange2k on 2012-11-17
> **anarchticgrimm said:**
> Additionally, when your game is running, can you reach the top panel? If you can, is there any options for maximizing, minimizing or closing? (if, of course, top panel and launcher are not covering the game)

Or, it's just a compiz bug. =/

No, I can't reach the top panel, I can normally play the game, but the launcher and the panel are bugging me...

I agree, its a compiz issue...

---

### Post by anarchticgrimm on 2012-11-17
Sorry to hear that =/ - But I'm optimistic; Compiz is a FPS killer anyways. =)

---

### Post by Dlambert on 2012-11-18
Try opening the Unity launcher by hitting the windows key, then double click in your game window. Also, it helps for me to 1) Emulate a desktop 2) Un tick "allow window manager to decorate/ control" windows in winecfg's display tab.


To get there, open terminal:

```
winecfg
```

Or if in PlayOnLinux, Right click on the app in the POL GUI and hit configure, then Configure wine.

---

### Post by orange2k on 2012-11-19
> **Dlambert said:**
> 2) Un tick "allow window manager to decorate/ control" windows in winecfg's display tab.


I tried to do that, but then I can't control the game... :(

---

