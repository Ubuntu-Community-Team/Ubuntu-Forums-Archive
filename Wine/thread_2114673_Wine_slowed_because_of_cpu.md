---
title: "Wine slowed because of cpu?"
date: 2013-02-10
forum: Wine
---

### Post by taylor179 on 2013-02-10
I have installed multiple games using wine, and all of them run. But none of them run to their potential. I can only run League of Legends at somewhere between 20 and 30 fps, when on windows I was at solid 60. I know wine cuts performance, but I didn't think it was that bad. Same goes for Call of Duty 4: Modern Warfare, it runs, but not well. I don't think this is a graphics issue, as I have the graphics driver installed, and no matter what the graphics settings are, I get the same frames. Is it my CPU that has troubles with these programs? Any help is greatly appreciated. 

My specs are:
AMD Athlon II x4 
Nvidia GTX 650
4 Gigs of ram
500 Gigabyte hard drive
Ubuntu 12.10 32 bit installation

On this rig I wouldn't think I should be getting any problems. 

Thanks for helping, 
Taylor

---

### Post by Mark Phelps on 2013-02-10
Wine does not function as an emulator, that is, you're not really running Windows; instead, it replaces native Windows DLLs with custom DLLs that make Linux System calls instead of Windows system calls.

In theory, this should not cut down on performance -- but when running games, you also have to take into account the DirectX level implemented by the Linux video drivers.  If the Linux drivers provide less acceleration benefit than the Windows drivers, you will see a performance hit in games.

---

### Post by taylor179 on 2013-02-10
I understand that it is not an emulator, but I'm pretty sure it's not a graphics problem. As I said, at any graphics settings I get the same frames.

---

### Post by taylor179 on 2013-02-10
If anyone can help, it would be greatly appreciated. I know it's a lot to ask, but is there anything I can do to get programs to run close to identical in performance as in windows? Like what kind of tweaks should I be making sure to do in Configure Wine and such.

Thanks again for any input. 
Taylor

---

### Post by taylor179 on 2013-02-11
Can no one give me a hand with this?

---

### Post by holastickboy on 2013-02-12
Problem is that WINE uses single core processing (without hacked versions) that will mean despite your cores, you will be running a bit slower than windows.  Have you applied any tweaks to improve your performance in LOL?

Check this link, or google LOL wine performance tweaks
[http://unixblogger.wordpress.com/2011/02/07/improfe-the-performance-of-lol-in-wine/](http://unixblogger.wordpress.com/2011/02/07/improfe-the-performance-of-lol-in-wine/)

---

### Post by taylor179 on 2013-02-12
I got LoL working at a solid 40 frames, now I'm focusing on Call of Duty 4. I can't for the life of me figure out why the performance is so bad. Also, if you know anything about the keyboard not focusing on the fullscreen CoD, that'd be amazing. :P

---

### Post by Mark Phelps on 2013-02-13
> **taylor179 said:**
> I understand that it is not an emulator, but I'm pretty sure it's not a graphics problem. As I said, at any graphics settings I get the same frames.

But ... that conflicts with:

> I can only run League of Legends at somewhere between 20 and 30 fps, when on windows I was at solid 60.

So, which of these is true?

---

### Post by taylor179 on 2013-02-13
I'm saying I'm pretty sure the performance drop is due to something other than my graphics card, as my graphics card isn't too shabby. I can change the LoL graphics settings to high, get solid 40 frames, turn it down to low, no frame change. This was the same when I was at 20 to 30 fps, in game graphics settings didn't effect fps.

---

### Post by Tweak42 on 2013-02-13
> **taylor179 said:**
> I'm saying I'm pretty sure the performance drop is due to something other than my graphics card, as my graphics card isn't too shabby. I can change the LoL graphics settings to high, get solid 40 frames, turn it down to low, no frame change. This was the same when I was at 20 to 30 fps, in game graphics settings didn't effect fps.

I would bet it's the multi-core issue or wine not able to optimally offload direct3d processing to your gpu.  In windows the the graphics drivers are often optimized for popular directX games and they can detect and offload graphics loads to the gpu to boost fps.  In linux there is no direct3d (wine translates direct3d to opengl) and there are no such optimizations unless someone makes a wine hack specifically for the game in question to offload work to the gpu.

For example this bug has been ongoing since 2008.
[http://bugs.winehq.org/show_bug.cgi?id=11674](http://bugs.winehq.org/show_bug.cgi?id=11674)

As a sort of experiment to try and find your bottleneck, you could try diabling cpu cores in your bios to 1 and see what kinda of perforamnce you get in windows and compare it to in ubuntu.

You can also compare gaming gpu utilization in linux vs. windows. At the command line "nvidia-smi -q" generates a report of stats for your video card.  It doesnt't report the utilization on my old chip but may work on your new card.  If it works, try using "watch nvidia-smi" and monitoring usage.  Then compare to gpu utilzation in windows - you'd have to search around to find a program that can do the equivalent.

---

### Post by taylor179 on 2013-02-14
I don't have a windows install at the moment, so won't be able to do any testing. But I know my frames were constantly a lot higher than what is noticable. I think they were at around 100 fps.

---

