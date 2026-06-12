---
title: "Counter-Strike 1.6 / Steam / Wine sound problem"
date: 2007-03-18
forum: Wine
---

### Post by peterhaagerup on 2007-03-18
For days I have been trying to play Counter-Strike on my linux box, experiencing lot of different problems:

1. I managed to get the non-steam versions of Half-Life, Counter-Strike, Opposing Force etc. to work with CrossOver - running in window-mode. I can't run the game in fullscreen -- if I try to do it, it changes the resolution, no game screen appears on the screen and the system completely freezes. I also have this problem with Steam, when I try to launch any game - it doesn't make any difference if I use regular wine or CrossOver. So far, I can only run in window mode / desktop emulating. Any ideas to solve this problem?

2. I have several audio problems. Everything works fine with the non-steam versions, if I play in a window, except that the sound is played 1 second or so after the actual action. I managed to fix this in a dirty way, setting the console parameter _snd_mixahead to -0.4 or around that. Sometimes I need to set it to another value to get it work. This is wierd, i think - any solutions?

3. I only get this problem with Steam: When I start Steam, it takes quite a time to startup - this is maybe normal. When I launch Half-Life (old Half-Life, not Half-Life 2) it works fine, except that i also have to fix the sound using the _snd_mixahead parameter. When I launch Counter-Strike or Deathmatch Classic (properly more games) the game screen comes up with no menu and nothing happens except that the CPU load is going up to insane levels. Then, it is completely frozen. It is telling me in the terminal from which i started Steam

```

err:dscapture:widDsCreate DirectSoundCapture flag not set
This sound card's driver does not support direct access
The (slower) DirectSound HEL mode will be used instead.
```

Please note that I get those messages for all games, but not all games are freezing. I started getting this after i went to winecfg and setting the hardware acceleration to emulation, because wine told me I should do so. Whatever I am trying, it won't stop freezing.

Yesterday, I managed to start everything with no freezing at all, but with the cost of no sound. I can't remember how I did - after i restarted, everything was back to normal again.

I've googled a lot and found no solutions. Somebody found solutions to the direct access problem, but it didn't work for me. To me, it really looks like the freezing is a sound problem. I get this problem with both wine and CrossOver. I also tried the newest wine from cvs - with that, i never got far because it was missing opengl32.dll, but it was located in the system32 folder.

I really need help on this - I'm so tired of troubleshooting - I just want to play a game :(

My hardware is an Intel MacBook, 1.83 GHz Core Duo, 1 GB RAM, Intel GMA 950 graphics, HDA Intel audio etc. I am using Ubuntu Edgy (6.10) kernel 2.6.15-27-686, wine 0.9.32, crossover 6.0.0. I have no problems playing native linux games such as quake3.

---

### Post by buttons on 2007-03-18
You should use OSS for your sound in winecfg.  I am using Full hardware acceleration; I'm not sure what the implications for hardware acceleration are with your soundcard so I won't speculate.  I DO know, however, that if you're using anything other than the OSS driver, steam shouldn't work.  If that doesn't work by itself, try using that and Full.  Uncheck Driver Emulation.

You shouldn't be running esd or aRts.  Be certain of this.

Why are you running such an old kernel?  Isn't edgy at 2.6.17 at least by now?  I have the feeling quite a few problems could be helped right there.

That error happens to everyone.  It's not an issue here.

The reason wine couldn't find opengl32.dll when you compiled it is because you forgot to compile opengl support into wine.  I believe the command is ./configure --enable-opengl.  In this case the newer version of wine very likely won't help you.

If none of the above helps you, you can try the suggestions listed by Con Kolivas [here]("http://ck.kolivas.org/faqs/audio_hints").  These are written mainly for his excellent ck kernel patches, but there are plenty of suggestions (hdparm, the filesystem tweaks) that may bring your drive latency down, and thus help diminish the need for the evil _snd_mixahead tweaks.

As suggested in the his audio hints, renicing the wineserver thread UP may fix quite a few problems.  Not down (low latency), UP.  As he explains, many sound issues can be corrected in this manner.

---

### Post by peterhaagerup on 2007-03-19
Thank you very much for your reply :) I'm now using kernel 2.6.17-10-386 - the ubuntu startup screen now look newer - i think something in my upgrade to edgy from dapper went wrong. Everything works perfect - except steam :/ I have tried to set the hardware acceleration to full in winecfg. Driver emulation is not set, so I leave it this way. This didn't make any difference at all. Then, I tried to set the hardware acceleration to emulation, because wine is telling me to do so. No difference. Then i tried to use ALSA, just to see what happened. This time it looks like i can play the games, but with no sound. I switched back to OSS - now, i'm also able to play games but still without sound. It feels like it hasn't realized that I switched back to OSS. What is happening now is very much like before, when i managed to get the games to work without sound. It doesn't look like the kernel did any difference to wine. :( 

Please note, that I killed esd and gnome's mixer applet to be sure that anything wasn't using the sound driver.

I have looked at some of the suggestions by Con Kolivas - i can see that my nice-number is fine, DMA is enabled and so on. It doesn't look like something is wrong there.

I am getting tired of this - it shouldn't be that hard to play some games now and then. I've also tried to play through vmware because it have experiential 3d acceleration. I didn't got far with that - it won't start the 3d acceleration and in the logs i can see, that it is complaining about my graphics card is missing some opengl-extensions. It works fine in any native opengl-game such as quake3 or when running glxgears.

Since I can't use wine, crossover, vmware - i think it will be the same with cedega. I've looked in the transgaming forum for problems with steam and it seems to be the same problems that regular wine-users is having.

There must be a solution - it would be perfect to see if another person with a  1.83 GHz Core Duo MacBook would try plaing CS 1.6 in Steam trough wine. By the way, I can tell that I tried to run steam on my little brothers computer (A new Dell Latitude Laptop) - about the same problems is going on there. I think both computers is using Intel GMA 950 Graphics - maybe the same sound card too. I am still open for any considerations or solutions to this Steam-problem.

---

### Post by peterhaagerup on 2007-03-19
Anyone having those problems? I still haven't solved it yet. I tried to install Steam using CrossOver on Mac OS X and it worked just fine. No problems at all. Then, in Linux, I tried to compile wine 0.9.33 to see if it was better, but I get the same problems. I think it might be my sound driver - anyone having weird problems with the HDA Intel using wine/oss?

For the problem that I can only play in a window (else X freezes) - maybe it has something to do with the 915resolution-package or something else?

I can live with playing in a window but right now, I can't play because of the sound freezing problem.

The fact that I can play in Mac OS X is not solving my problems - I want to play in Linux - there's a reason I'm using Ubuntu - to do everything - not just what is possible in Windows and in Mac OS X :) I still think it's weird that i works perfect in Mac OS X but not in Linux...

---

### Post by .kkursor on 2009-01-16
I have a similar problem in Ubuntu Intrepid 8.10. Patched no-steam version of Counter-Strike 1.6 is working perfectly but a licensed one which uses Steam hangs in random moments. It may work for several hours perfectly or crash in 10 minutes since startup. When this occurs, the sound begins to loop and the screen stops moving. It seems that operating system continues working - the HDD activity LED blinks. But the computer stops responding to keypresses - none of the hotkeys work. I tried Ctrl+Alt+BkSp, Ctrl+Alt+F1, Ctrl+Alt+Del and many-many-many other hotkeys - they do not work. Reset is the only solution to bring computer back to life. Sometimes sound in the game disappears, and it's required to restart it to bring it back. But I haven't noticed a crash when the game is running without sound. The Wine sound system is ALSA, OSS is disabled. When I enable OSS, sound disappears.

It's interesting that Half-Life (1) running under the same Steam is running perfectly - no problems.

---

