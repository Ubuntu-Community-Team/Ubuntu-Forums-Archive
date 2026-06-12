---
title: "Oblivion / Wine crash+freeze"
date: 2007-11-30
forum: Wine
---

### Post by ZugZugTheOrc on 2007-11-30
Okay, here's the issue. I installed Oblivion before.. but it was all sorts of crappy. So I uninstalled it and reinstalled it again. This time is much better.

If you've played the game you'll understand this... I can make it out of the sewers. Once I'm outside I can look around and the graphics are okay. I can interact with the world and I can fight a mud crab. But when I start to walk away from the sewer entrance in any direction the game freezes and the console has these errors in it. I think it is happening when the game tries to load the next cell.. but I have no idea.

```
fixme:d3d:state_vertexblend Vertex blending enabled, but not supported by hardware
fixme:d3d:state_vertexblend Vertex blending enabled, but not supported by hardware

fixme:d3d:FindContext The PBuffr context is only supported for one thread for now!

err:seh:setup_exception stack overflow 40 bytes in thread 0015 eip 7c6f15ae esp 7c449fd8 stack 0x7c44a000-0x7c55a000

err:ntdll:RtlpWaitForCriticalSection section 0x14932a0 "?" wait timed out in thread 0010, blocked by 0015, retrying (60 sec)
err:ntdll:RtlpWaitForCriticalSection section 0x14932a0 "?" wait timed out in thread 0010, blocked by 0015, retrying (60 sec)
```

Does this make any sense to anyone? If so, what's going on with it (and hopefully a fix).

I think my specs would help too..

```
Dell XPS M1710
1GB Ram
256MB Video (NVIDIA) - on this note.. not sure if there are specific dell linux drives for my laptop.. I didnt check yet..
Dual Core 2GHz
```

---

### Post by cogadh on 2007-12-01
There are a couple of known bugs with Oblivion in Wine. One of them causes the game to crash if you haven't renamed the Videos folder (Wine can't play the videos). The other causes the Oblivion.ini file to be created incorrectly, leading to a game crash. I would check and (if necessary) correct those two items first.

---

### Post by ZugZugTheOrc on 2007-12-02
> **cogadh said:**
> There are a couple of known bugs with Oblivion in Wine. One of them causes the game to crash if you haven't renamed the Videos folder (Wine can't play the videos). The other causes the Oblivion.ini file to be created incorrectly, leading to a game crash. I would check and (if necessary) correct those two items first.

Hey thanks for the reply. I had originally thought that about the INI file, but I had ran oblivion (through the sewers) and then modified the INI afterwards. I removed all references to the movies too. Where it crashes there are no movies that should play at that point in the game, so not sure it's an issue with that. 

I read somewhere that Wine sometimes has issues with something called a pbuffer. I also heard there was an alternate setting instead of pbuffer. 

Any other ideas?:confused:

---

### Post by cogadh on 2007-12-02
There is an alternate setting you can use, fbo (framebuffer objects). You need to create some registry entires in Wine to change that. See the Wine [Useful Registry Keys](http://wiki.winehq.org/UsefulRegistryKeys) page for details. the "fbo" setting is under the "Direct3D" section.

---

### Post by ZugZugTheOrc on 2007-12-02
> **cogadh said:**
> There is an alternate setting you can use, fbo (framebuffer objects). You need to create some registry entires in Wine to change that. See the Wine [Useful Registry Keys](http://wiki.winehq.org/UsefulRegistryKeys) page for details. the "fbo" setting is under the "Direct3D" section.

I'm assuming they are the same registry keys that were used in the Wiki for the install procedures right? I'll give those a try and let you know how it goes.

Long live Ubuntu!!!

---

### Post by ZugZugTheOrc on 2007-12-03
Hey just wanted to let you know that I changed the value from pbuffer to fbo and it works great. I set the settings on "Ultra High" and kept Bloom/HDR turned off. The game runs smooth. So far I can bring up menus, interact with people, and all sorts of things without glitch or hang-ups. :KS:KS

If you know of how to solve the pbuffer issue (I have the latest wine I believe... ) that would be good to know why it does that and how to fix it. Thought the Wine FAQ said it was fixed.. strange.

Anyways, I am going to see if the drivers I've got can do the bloom/Hdr thing.. no idea if it will work. But that's the fun of trying eh?:)

---

