---
title: "Black TF2 Objects"
date: 2008-04-20
forum: Wine
---

### Post by Sinja on 2008-04-20
So, I've successfully installed Steam, installed team fortress 2 (or brought it up to 100% in Steam "my games" tab), and got it running.  However, now, there are several "black" objects that appear when TF2 runs.  For example, in the main menu, the backround is black.  When i bring up the server list, the server names, latency, players, and all that good stuff is black.  When I get into a game, The score is black, my ammo is black, my special ammo is black, my portrait is black.  The only thing that isnt black is the game itself.  ALL the ui ingame is black.

My video card is an e-geforce 8800 GT (its pretty good, id recommend if you want to upgrade).  So what is the problem here?  I think that something went wrong during installation.  Because, it could just be that the game is not loading the right images for the "black" objects.

What do you guys think?

---

### Post by lingnoi on 2008-04-21
Sounds like a problem with Textures or Shaders. Try playing around with either:

1) Texture Settings
2) Any Texture memory settings
3) Shader Settings

---

### Post by Sinja on 2008-04-23
Uh.... how exactly do i do that?

---

### Post by aoanla on 2008-04-24
This problem is known - it's the "problem with DirectX 9" that people (including me) keep putting in their write-ups for TF2 on the Wine AppDB. There is nothing wrong with the install, or your graphics card.

The simplest way to avoid the problem is to get TF2 to run in DirectX 8.1 mode, thus not trying to do the fancy DirectX 9 shader stuff that Wine /can't quite/ do properly for it (yet).

To do this, in Steam, select TF2 in your games list, click on the Properties button on the bottom-right, and then choose "Set Launch Options". Add the string

-dxlevel 81

That should solve your problem - personally, I'd keep checking on the AppDB entry when a new Wine version comes out, just to see if this is fixed yet.

---

