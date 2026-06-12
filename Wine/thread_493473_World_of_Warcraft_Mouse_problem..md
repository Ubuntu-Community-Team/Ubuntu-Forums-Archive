---
title: "World of Warcraft Mouse problem."
date: 2007-07-05
forum: Wine
---

### Post by Faust942 on 2007-07-05
I recently reinstalled Ubuntu, gotten everything I need setup and configured correctly, except World of Warcraft.

I have installed it and I can login, but the cursor while I am in the window is the Ubuntu Human cursor overlaping the Warcraft cursor.

I have followed the instructions in WoWwiki's Wine guide, and I am still having this problem.
This has worked before I formatted my system. My config.wtf file was not using either OpenGL or d3d, so its not a problem with that. Now I know that WoW uses DirectX, so should I install a version of DirectX?

How do I fix this?

---

### Post by hikaricore on 2007-07-05
If you followed the guide you would know to use OpenGL under linux to run WoW.
[I]Also with the latest version of WINE the cursor issue does not exist in d3d mode,
but this is not really useful unless OpenGL mode which y(ou should be using) does not
work for some reason.[/I]

And lastly you can't install DirectX under linux, there is no need to do so, if you manage to install it anyway you will not accomplish anything as WINE uses it's own d3d libraries.

---

### Post by Faust942 on 2007-07-05
Sorry, I made a major mistake. When I installed Wine, I installed it right after I installed Ubuntu. So I was an older version. I just added another source for wine to my repositories and it works perfectly.

As for OpenGL on my WoW, it freezes while I load. I added d3d but unfortunately, the graphics suck. 

But anyway, I got the game working on whatever its running on right now :S (Its not on OpenGL or d3d).

Thanks anyways for the talking too.

---

### Post by hikaricore on 2007-07-05
Sorry if I was blunt, lack of sleep.  >.< 

Glad it works, but I have to say it's one or the other, WoW defaults to d3d.  It can't be neither mode, it's not possible.  But it works is the important thing.

---

### Post by Faust942 on 2007-07-05
Agreed.

---

### Post by Ripfox on 2007-07-06
D3D  is all that will work with my intel graphics chip so no open gl for me, as ideal as it is i guess...

---

### Post by Sammi on 2007-07-06
In my experience d3d is a little better at running when there are issues, while opengl either works or it doesn't.

---

### Post by Faust942 on 2007-07-14
I recently installed a new version of wine and now my Warcraft is crashing.
I'll be able to login and be able to enter the world, but when my character model is loading it crashes.
Attached is the output from start to finish.
I don't know how to fix this. Please help.

---

### Post by Sammi on 2007-07-14
It's called a regression. As some things in development get better some other things break. It happens because the Wine packages aren't tested before they are released. They are simply snapshots of the current development, that are made at a fixed two weeks interval. 

Go here for the older packages: [http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html)

---

### Post by Venoseth on 2007-12-24
To anyone else who's having the same trouble, I fixed this problem by changing my "Enable hardware cursor" setting (I also changed the "Smooth Cursor" setting, but I don't think that was the issue. 

I don't know if this is something that would have helped you, or just that I ran into a different problem with the same symptom, I'm quite new. Hopefully that helps someone tho'. ^^

---

