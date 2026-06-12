---
title: "Diablo 3 Stuttering"
date: 2012-08-09
forum: Wine
---

### Post by Lodmot on 2012-08-09
Hi.

I've been trying to get Diablo 3 to run on my desktop computer, with some success. The game works alright with sound and everything, but it is very stuttery, and it's irritating, especially hearing the sound stutter like that through a loud 5.1 surround sound system. 

I've looked up this problem on the internet and people say that doing "setarch -i386 -3" fixes it for them, or "taskset -c 0" or similar works too. I've tried many of these things, and none of them worked. It didn't make the game faster or slower. I've also tried running the game in windowed mode, setting CPU affinity, etc, and these options also had no effect whatsoever.

My desktop is my own custom-built computer with an ATI Radeon HD 4300 graphics card with 512 MB of VRAM, I believe the sound card is a Creative Sound Blaster Live. I have the system connected to a 48" Toshiba LCD TV via the HDMI output on the graphics card. In order to make use of all the pixels on the screen, I have the overscan set to its max, otherwise there's a black border around all four sides of the screen, and it bugs me to no end. The computer has a 3.0 GHz dual-core Pentium D processor, with 4GB of RAM, and I'm running on Ubuntu 12.04 64-bit. 

I've also tried playing a bit with the AMD catalyst settings, turning off vblank, and booting into Ubuntu 2D. 

Any suggestions as to what I should do at this point? 

Thanks.

---

### Post by sffvba[e0rt on 2012-08-09
My searching on Google is severly impaired due to being at work and no sites related to gaming will open but my guess is your Graphics card is just not up to the task.


404

---

### Post by Lodmot on 2012-08-09
Very well. In that case I will try a lower graphics setting in Diablo 3's video settings.  I was actually planning on buying a new graphics card eventually anyway. ^^

---

### Post by Lodmot on 2012-08-10
Update:
Just tried setting the overscan amount to its default setting in the AMD catalyst center, and that, along with using lesser video settings, and the "setarch i386 -3" command helped. 

Pretty sure that means I need a new graphics card. Good thing I just got paid. Lol.

---

### Post by sffvba[e0rt on 2012-08-10
> **Lodmot said:**
> Update:
Just tried setting the overscan amount to its default setting in the AMD catalyst center, and that, along with using lesser video settings, and the "setarch i386 -3" command helped. 

Pretty sure that means I need a new graphics card. Good thing I just got paid. Lol.

Sadly this is the fate of hardware, outdated even before it hits the store shelves.


404

---

### Post by Lodmot on 2012-08-11
Update: 

I've made some further observations about this problem. 
After playing the game a while, it almost seems like the graphics are working better than the sound. Still, not great, but like what they should be for the old Radeon card that I have... It seems like there are times when the graphics are actually very smooth even, and the sound still has to catch up with the game because it's stuttering so much. 

I also noticed this effect in *other* Wine applications. Trying an SNES emulator did the same sort of effect-- graphics seemed buttery smooth, but sound stuttered terribly. Another N64 emulator (Project64) on Wine did the same thing as well, again, with well-running graphics, but stuttering sound. However, when I tried the linux-native Mupen64 emulator with the same game, it ran perfectly fine. No sound stuttering, smooth (for the most part) graphics all around. 

So the long and short of it is.... it's a Wine problem that I'm probably having...

It can't be the hardware of my sound card or graphics card being faulty.

So... any ideas?

Thankies. ^^

---

### Post by vexorian on 2012-08-12
Have you verified that this happen *only* with WINE applications? For example, non-totem video players might have this too. (I had a similar issue with VLC due to my pulse audio config having a bad setting).

---

### Post by Lodmot on 2012-08-12
> **vexorian said:**
> Have you verified that this happen *only* with WINE applications? For example, non-totem video players might have this too. (I had a similar issue with VLC due to my pulse audio config having a bad setting).
Yeah, this only seems to be happening with Wine applications.

I just tried something though. I uninstalled the ATI proprietary drivers that I had, and installed the new 12.6 ones. Now the sound in Diablo 3 seems to be working great! But now I have the infamous "click Login and freeze" bug. I think it had something to do with the AMD drivers though, now that I'm seeing this work a bit better. (Hopefully)...

UPDATE:

While I still can't login to Diablo 3 without it doing a hard freeze, the SNES emulator in wine is now working! Like Diablo 3, the sound is working great in that application as well now. Additionally, the N64 emulator in Wine also had a noticable improvement. The sound was still a little choppy, but nothing like before. So, I'm getting closer!

---

