---
title: "Ubuntu 9.10 Karmic Koala - Problems with Video Players"
date: 2009-11-01
forum: x86 64-bit Users
---

### Post by ramka001 on 2009-11-01
Hi All,

I have upgraded from my previous installation of ubuntu 9.04 to the current release ubuntu 9.10. The installation of the files went smoothly however I am facing a  glitch in my video players such as the "Totem Movie Player" and VLC Media Player.  Both of the players have the similar problem in the picture display whereby the colour of the image is distorted i.e. it is appears as in black and white. 

I have attached a screen shot of the image. Anyone who has encountered the same problem and has any idea how to solve it?  Some advice on this would be greatly appreciated.

Thanks in advance.

Cheers

Ram Kumar

---

### Post by The Funkbomb on 2009-11-01
I had a problem with videos too after upgrading.  My sound was very choppy in VLC.  The solution I went with was to back up what I wanted to keep and do a fresh install.  Things are MUCH better now.

---

### Post by ~williahayd~ on 2009-11-01
I've been getting weird color's with some videos (skin tones tuning blueish green), I've found logging out and logging back in fixes the problem for a short while, seems .flv files are the worst culprits, but it has also happened with .avi and dvd's.

Not all that sure on what is causing it. Sorry.

---

### Post by Candrian on 2009-11-01
Opening Totem->Preferences->Hue and adjusting it back to a default position should fix the green blueish problem with movies after opening totem, without further reboots needed.

For the black and white screen I would see if any of the other colour balance settings are also off from the default position in totem.  Hope this helps!

---

### Post by abelta on 2009-11-01
Thanks, Candrian, I was having that same problem too. I can't believe that could be misconfigured during an upgrade just like that. How weird.

---

### Post by kozjegyzo on 2009-11-03
Hi,

I have an issue with video playback too. Since the upgrade to Karmic, all my video players display the same problem. The video seems fine at first, but if there is fast movement in the film, the video shows horizontal breakage. This happens with all players. The videos are still watchable, but it's very annoying.
I tried reinstalling the codecs, but that didn't do anything. 

The other accruing problem is that sometimes the whole video playback freezes for a few seconds and the audio keeps going, and then everything is back to normal.

Anyone facing the same problem? Fixes?

THX in advance

---

### Post by timsdeepsky on 2009-11-03
Same for me....I had an odd colored video problem in all players....Changing drivers fixed this....I still have the choppy video problem in all players no matter what i change....

---

### Post by timsdeepsky on 2009-11-03
*UPDATE*
This before mentioned problem of choppy video does not happen in Kino and Cinelerra....

---

### Post by NDotter99 on 2009-11-03
I have same problem but mainly with VLC.  I wont play files I have on second hard drive.  It freezes or comes in black or white.  Can anyone help?

---

### Post by Renzo-M on 2009-11-04
Having choppy video too in Karmic Koala, didn't have this problem in 9.04. It's really annoying, it's got me booting in Windows, hope this gets fixed soon...

---

### Post by timsdeepsky on 2009-11-04
Anybody find a launchpad bug listing for this yet??....

---

### Post by john11smith on 2009-11-05
> **Candrian said:**
> Opening Totem->Preferences->Hue and adjusting it back to a default position should fix the green blueish problem with movies after opening totem, without further reboots needed.

For the black and white screen I would see if any of the other colour balance settings are also off from the default position in totem.  Hope this helps!
Thank you it really help:
Open video with Totem movie player then   Edit->Preferences->Display and press "Reset to Defaults" button. That's it. This procedure must fix colours in VLC also.

---

### Post by Arup on 2009-11-05
I don't use Totem but do use latest VLC 1.03 from C. Korn ppa, it works out fine here with my nvidia 8400GS card using nvidia drivers from repo. I also extensively use smplayer to play back HD movies with VDPAU and even there I face no glitches. This could be a video card driver issue.

---

### Post by myk.dinis on 2009-11-05
Found a solution!! Go into Synaptic Package Manager and mark all upgrades.

Hit apply.

Voila!

Cheers!!

Myk

EDIT: Dang, that only worked for half my video collection. All my HD stuff is still choking. I'm thinking codec incompatibilities.
If anyone else has any better info, please keep us posted!

---

### Post by kozjegyzo on 2009-11-06
Hey,

A friend suggested that I reinstall Karmic so everything is fresh (since I only upgraded with the upgrade manager). So I did a reinstall with a live cd. Nothing changed, still having choppy video and sometimes freeze for a few seconds, no problem with audio though. I never had these problems with 9.04...

---

### Post by Arup on 2009-11-06
> **kozjegyzo said:**
> Hey,

A friend suggested that I reinstall Karmic so everything is fresh (since I only upgraded with the upgrade manager). So I did a reinstall with a live cd. Nothing changed, still having choppy video and sometimes freeze for a few seconds, no problem with audio though. I never had these problems with 9.04...

What video card are you using?

---

### Post by timsdeepsky on 2009-11-08
Video players seem to have trouble with .MOV....I can turn my .MOV's into DV and they are fine in Totem,,Vlc,,etc....I did not have this problem in 9.04....

---

### Post by a2z on 2009-11-09
> **timsdeepsky said:**
> *UPDATE*
This before mentioned problem of choppy video does not happen in Kino and Cinelerra....

I first became aware of this problem while trying cinelerra. 
I can not play any vid in cinelerra. 

I hardly think it's a matter of adjusting color scheme in any player. Something internal going on. Perhaps with the kernel.

Ironically this morning my video in cinelerra made some amazing progress. I can actually click play and watch the slider advance across the screen. However, the screen is still black. And all videos in all players still have colors inverted!

Keep up the great work Ubuntu. I know this is being looked at and will be repaird asap.

---

### Post by waba on 2009-11-09
I have the same problem of horizontal tearing in Movie Player when playiong a .avi file, after a fresh install of karmic koala. i have a ati 4770, and have installed the propriety driver for it from the repository. :(

---

### Post by confy on 2009-11-11
> **john11smith said:**
> Thank you it really help:
Open video with Totem movie player then   Edit->Preferences->Display and press "Reset to Defaults" button. That's it. This procedure must fix colours in VLC also.

I can confirm this!!! It worked :)
It seems totem confused codecs prefences until next restart :)

---

### Post by fugazi41 on 2009-11-13
I have the 8400GS with 9.10. No tearing IF compiz is OFF. But I like compiz running!
With 9.04 didn't had the tearing with compiz ON or OFF. I use Totem, VLC and smplayer.

I did a fresh install of 9.10, didn't upgrade. The biggest flaw is pulseaudio when using AC3/SPDIF. Crapy sound. Have to switch to ALSA to listen to AC3 movies, VLC smplayer can do the trick but Totem or Totem-xine doesn't. Hope it'll be fixed in 10.04. 9.04 didn't had that sound problem. 

Regards,

Jean

---

### Post by waba on 2009-11-13
i do have compiz running, didnt realise that was what was causing the problem. i use totem, and like compiz too, so dont want to turn it off - any way round the tearing whilst having compiz on? any updates?

---

### Post by deltron30 on 2009-11-14
Turn "sync to Vblank" on for everything in x server. Then make sure it's checked in compiz. It fixes this tearing for the most part. Streaming flash videos still tear full screen but it's probably a flash bug. If I want to watch a flash movie full screen I just zoom in on the video and it looks great. I hope this helps.

---

### Post by waba on 2009-11-14
whats x server?

---

### Post by deltron30 on 2009-11-16
I use an nvidia card. I have an "nvidia x server settings" GUI. There are options to set the "XVideo" texture settings and the "OpenGL" texture settings. There is an option for "Sync to VBlank" in both. Once I check those boxes and the box under "General" in compiz config manager this problem went away in VLC and mplayer. However, I still have this problem in most flash videos when I'm using my browser. I think it's a flash bug. I'm not quite sure though. BTW this is all while Emerald, and Compiz are running.

---

### Post by RyuTesla on 2009-11-17
I'm not experiencing the "tearing" of the video on playback, nor stuttering, but I am experiencing hue shift in all my video players. The hue shift makes skin color look a slightly greenish blue, close to cyan. That which should be dark red becomes dark green.

I primarily use VLC, but the same problem is in Movie Player and MPlayer. In VLC, I adjusted the hue to correct the issue, but the issue in inconsistent. When I start a video, the issue may or may not be active. If I fullscreen the video, if the issue is inactive, it then may activate, or if it is active, it may stop, or there will be no change. I also get the same result when I skip ahead in the video, forcing me to be constantly turning off and on the hue adjustment.

I was thinking of doing a clean install of v9.10, but from the comments on this thread, doing so won't fix the problem.

Don't know if this is a contributing factor, but I am using the NVIDIA graphics driver v185.

Is there a bug report on this? I would like to add my symptoms to the report.

---

