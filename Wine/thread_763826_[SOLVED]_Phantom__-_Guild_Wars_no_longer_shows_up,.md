---
title: "[SOLVED] Phantom  - Guild Wars no longer shows up, but is running."
date: 2008-04-23
forum: Wine
---

### Post by lifestream on 2008-04-23
Hey all,
So here's the deal: I've been running Guild Wars in Wine for a long time now... months and months. It runs even nicer than on Windows :-) Good job Wine team :P
But anyway, I get this occasional problem, where if I tell the window to move itself to "desktop 4" or any for that matter, and only in some occasions, the game disappears, (no its not on that desktop) and the icon disappears from the gnome bar.
The game still shows as "sleeping" in the gnome system monitor and I can hear the game music.

Great. So I have no option but to kill the task, and I do so. Now, next time I launch Guild Wars, the usual Connecting to ArenaNet message comes up, but as soon as the game itself is going to launch.... you guessed it: it just disappears somewhere, and no icon is shown on the taskbar anymore.

I can give it the --windowed prefix which is valid for guild wars. Does not help with the problem.

I use compiz + emerald + awn but I have tried without them. In fact, I have completely wiped my Ubuntu install, reinstalled fresh, and then tried running without compiz... I can then replicate the error even without composite.

Now if you've read this far, please read the additional information I have provided if you think you might be able to help :) 

Thanks for any input you might provide!


 Wine version - Doesn't matter, happens with whichever version I've tried. But if you really want to know it's 0.9.59 at the moment.

Terminal output - 
```

Lots of fixme's which I have been told are ok.
err:d3d:getColorBits Unsupported format: WINED3DFMT_R32F

```

Wine configuration - It's the default settings. (I run wineprefixcreate after installing wine)
Hardware specs/drivers - G72M [Quadro NVS 110M/GeForce Go 7300] restricted drivers 
Intel core duo

 Other Wine applications - Ummm just notepad that comes w/ Wine.



   1. Check AppDB -  Yes, I have. Game runs fine. Game runs great for me too.
   2. Search for an existing how-to - Been searching for ages (months). None necessary since GW runs fine.
   3. Update Wine - Done
   4. Use the Wine virtual desktop - Done - the game goes away (but still running) just the same as it would on the gnome desktop. Only the virtual desktop background shows up. (The "connecting to arenanet" message from guild wars shows up fine, notepad works fine, its just when the game goes launch that it becomes hidden"
   5. Search the forums - I've tried, maybe I was searching with the wrong words, but Ive been trying for a couple of months.
   6. Try different OS versions - I've exhausted wine's options.
   7. Check the terminal output - It's pasted above. Let me know if you spot something fishy :)

---

### Post by lifestream on 2008-04-27
Bump :( let me know if there's any info I need to include.

---

### Post by Ignotser on 2008-06-23
Yeah, I would like to know if anyone has any sort of explanation or solution to this... I've been frequently experience the same problem that you mentioned in your post earlier.

---

### Post by DestroyMicroshaft on 2008-08-27
I had this same issue in Slackware 12.1, using Xfce. I solved it by reinstalling the game. I've since made a backup of the fully downloaded game on a external hdd.

GL.

---

