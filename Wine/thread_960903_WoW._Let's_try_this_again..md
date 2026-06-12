---
title: "WoW. Let's try this again."
date: 2008-10-27
forum: Wine
---

### Post by Milkium on 2008-10-27
Hey guys.
I recently got a new monitor. It is a Vision V193WDB Widescreen. You've probably never heard of it. I know I haven't.

Anyway, before I had this monitor, I had an HP mx705 CRT, which **displayed WoW just fine without any problems. ** Now it seems that that is not the case with my new monitor. All I did was plug it in, and use it. As far as I'm concerned, monitors don't need drivers. But that is the only thing that I would imagine that could be wrong here. 

I made no changes to anything else on my system, except that I got a new monitor. After starting up WoW, as soon as I get to the login screen, my screen does something weird. I have a picture  attached. What's going on?

P.S. I know I posted this before but I felt that I didn't elaborate enough, so I posted this one. Delete this thread *if you must*.

---

### Post by Milkium on 2008-10-28
Bump.

---

### Post by JakeWatkins on 2008-10-28
Widescreens, as I've found out, use more power (CPU/GPU, not energy.. maybe..)

If you have it set to 1440x900 or higher, it's going to have to work harder then 1028x768.

Try setting it to that setting, or get a better graphics card.

= D

Hope this helped!

---

### Post by Milkium on 2008-10-28
That didn't directly help me, but it gave me the idea to open winecfg and try running the game on a virtual desktop. (Don't ask how I connected your post with this idea. I dont' even know, but I did.) I was able to run WoW, and set the game to run in Windowed mode. Because going to the wtf.cfg file and adding SET "gxWindow 1" <--or something like that, didn't work out for me. But now WoW runs fine in GNOME.

But I do have a new problem. My fps at it's highest is 8. This was never a problem before. Anyone have any ideas on how to fix this?

---

### Post by ratmandall on 2008-10-28
> **Milkium said:**
> 

But I do have a new problem. My fps at it's highest is 8. This was never a problem before. Anyone have any ideas on how to fix this?

Again it might be because your graphics card has to work harder because of the bigger resolution.

---

### Post by Milkium on 2008-10-28
Well, with the old CRT, my resolution was 1024x768, and it ran just fine at around 20-28 fps. 

I tried putting the game on 800x600 with this new monitor, but I still get an fps of around 8.

---

### Post by shredswithpiks on 2008-10-29
Normally when I've seen monitors freak out like yours in the OP it's either an issue with the refresh rate or bad memory on the video card. There's a setting in the wow video stuff to match wow to the refresh rate of your monitor. Most CRTs can do 75-85hz, possibly higher. LCDs are normally bound to 50-60hz, and when you try to run higher refresh rates you get all that blocky nonsense.

Your low FPS could be due to other video settings changes while you were working through the other issue. Maybe something got bumped to high? Have you played wow on wine with decent framerates since 3.0.2 (they added a fair bit of graphical goodness that drags FPS down on older hardware)?

Also, most of the WoW + wine tutorials on the net tell you to disable GL_ARB_vertex_buffer_object in wine's regedit. With WoW 3.0.2 blizzard seems to have fixed the problem with that extension and re-enabling it (deleting the registry key the tutorials tell you to add in) jumped my framerate up considerably (30-40% depending on the area in game). Try doing that and see how it goes?

---

### Post by hotballz87 on 2008-10-29
is this with the new 3.o patch with the bad framerates?

because if it is, its not just you, blizzard updated ALL the spell detail grapix, and that has decreased the performance on even my computer, (3 gigs of ram, 5800+ dual core, geforce 8800gtx)

i will be going dual card once i get some money....

---

### Post by shredswithpiks on 2008-10-29
> **hotballz87 said:**
> is this with the new 3.o patch with the bad framerates?

because if it is, its not just you, blizzard updated ALL the spell detail grapix, and that has decreased the performance on even my computer, (3 gigs of ram, 5800+ dual core, geforce 8800gtx)

i will be going dual card once i get some money....

my setup is rocking a solid 60fps (vsynch woohoo!)... 3gb ram, E6600 core2duo, geforce 8800gts 320mb. At 1680x1050. There's more going on than the increased graphics from the patch.

---

### Post by lH)4~mK0e on 2008-10-31
> **Milkium said:**
> Well, with the old CRT, my resolution was 1024x768, and it ran just fine at around 20-28 fps. 

I tried putting the game on 800x600 with this new monitor, but I still get an fps of around 8.

If you were getting fps in that range at 1024x768, then your video card will definitely need to be upgraded post 3.0.2.  As was mentioned, there is a lot of graphical changes that have been made.  To give you an idea, I have a geforce 7600 gs 512mb that gets between 30-40 fps outside cities at 1280x1024 resolution post patch.  Before I would get between 40-50 fps.  If you upgrade, get an nvidia 7xxx (if you can find an agp).

---

