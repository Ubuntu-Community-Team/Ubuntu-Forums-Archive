---
title: "ALSA sound issue with Wine and Kubuntu"
date: 2008-09-04
forum: Wine
---

### Post by rocky5051 on 2008-09-04
Hello everyone! I am currently running a machine with Kubuntu 8.04.1 (KDE4 Remix) x86, and Wine-1.1.3, and my motherboard is recent (1 year old from NewEgg, but an older model, Socket A) with the SiS 7012 wave 6.1 channels (embedded in mobo).

Anyway, I installed Kubuntu (wiped my old Kubuntu setup and replaced it entirely) about 2 weeks ago, and I later installed an official wine deb for wine 1.1.3 shortly after. Wine works very well for everything I run, except for with ALSA...

I know that Kubuntu 8.04.1 uses ALSA still, and whenever I set the sound option for Wine to use ALSA, my games (all were w/o this issue on Kubuntu 7.10 on older wine releases) will work with sound for about a minute, and then randomly the sound will cut out, and won't work again until I restart the game.

I should also add that this isn't a problem if I set sound to OSS in winecfg, but I get better sound quality from ALSA. I also compiled the same version of wine from source, but the same issue occurred.

Now the only reason I ask here rather than on the wine forum is because I'm not sure whether or not this is a wine issue or a Kubuntu issue. I know that wine-1.1.3 got some tweaks for PulseAudio, but I'm not sure if that'd have any effect on ALSA performance.

So, has anyone else experienced this issue? If so, could anyone give me a few pointers in how I could fix it? I haven't tried an older wine release on this new version of Kubuntu yet, but I can if someone asks.

Thanks :) (and sorry for the wordyness :( )

---

### Post by whitevamp on 2008-09-05
I have this same issue, playing wow. the sound will just stop at randome times. I haven't tried using OSS sound yet, to see if it still dose it, or not.
on a side note: I also have freebsd install and no issues with sound useing wine, and sound.

---

### Post by rocky5051 on 2008-09-05
It seems to occur quicker when a greater variety of sounds gets tossed in. I also checked the terminal to see if anything came up when this occurs but, nothing does. I'm about to try compile wine-1.1.4 right now so I'll tell if that changes any then.

Oh, and the games that this has occurred for me so far:

-Call of Duty 1
-Age of Mythology v1.0 (and updated versions)
-American McGee's Alice

---

