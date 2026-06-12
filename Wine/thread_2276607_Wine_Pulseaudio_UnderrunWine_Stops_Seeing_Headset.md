---
title: "Wine Pulseaudio Underrun/Wine Stops Seeing Headset"
date: 2015-05-03
forum: Wine
---

### Post by Uruz on 2015-05-03
I'm running Wine (and PlayOnLinux) on a fresh install of 15.04 and I'm having that darn audio underrun error.

I know what causes it/how to fix it (specify Wine's output device rather than using "System Default") but the fix doesn't stick.

What happens: I start up my computer and open Winecfg. Under the audio tab, my output will either be "(System Default)" or my USB headset. If it's using my headset, I can hit the test button and hear the nice little beep. If it's "(System Default)," I can change it to use my headset and the sound test works.

If I start up League of Legends (the only thing I'm really trying to run) and press the "Launch" button, it will *usually* sound fine. By the time the login screen loads, Wine defaults to using "(System Default)," causing the underrun (once or twice it's lasted longer, but there's no consistency). At this point (or at any point where it begins to underrun), Wine no longer sees my USB headset and I can't make it see it again without rebooting my computer.

I've tried everything from editing Wine's registries (which never look like the tutorials say they should), to forcing Pulseaudio to only load my headset (by disabling auto-scan and manually directing it to the device). No matter what I do, Wine loses the headset and I get the underrun.

Thanks for your help,

Uruz

---

### Post by Uruz on 2015-05-05
Update: I've tried disabling Pulseaudio and running the audio only through Alsa. The launcher audio works fine, but when it gets into the client, there's absolutely no sound. That makes me think that for some reason, the client won't run through ALSA at all, just Pulseaudio.

---

