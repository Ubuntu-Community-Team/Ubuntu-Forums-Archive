---
title: "Wine and Pulseaudio issues"
date: 2014-12-26
forum: Wine
---

### Post by darksidedude on 2014-12-26
I thought I would post under the wine subforum. although I am using kubuntu 15.04 alpha. if mods feel it is in the wrong place I apologize. 

I was trying to play wow on my laptop and I noticed the sound would lag for a few seconds. come back for a few then get hopelessly distorted in any wine program (steam windows and WOW) I thought I would post and see if I can get some thoughts and or fixes from the community =) 

as a side note I am using git compiled Pulseaudio and wine 1.7.33. the issue was present in standard distro packages so I compiled these versions in hopes of a upstream fix. to no avail. thanks again for everything! 

```
pulseaudio 5.99.2-1-g6e4e8
```

```
 wine-1.7.33-74-g0db8da7
```

---

### Post by Mark Phelps on 2014-12-26
> using kubuntu 15.04 alpha

Sorry, but anyone using an Alpha should expect frequent breakage and stuff generally not working.

You should really post your 15.04 questions in the Development forum section.

---

### Post by darksidedude on 2014-12-27
In a way I can accept your response. but I am using compiled versions of wine an pulse. meaning its not tied directly to the release schedule. 

anyway I made progress.. as long as the OS is not using the sound card ie beep music etc. wine will play fine. but if the os and wine try to access the card at the same time. ie (play music in amarok and use vent) all sound stops

```

err:ole:CoInitializeEx Attempt to change threading model of this apartment from multi-threaded to apartment threaded
ALSA lib pcm.c:7843:(snd_pcm_recover) underrun occurred
 
```

---

