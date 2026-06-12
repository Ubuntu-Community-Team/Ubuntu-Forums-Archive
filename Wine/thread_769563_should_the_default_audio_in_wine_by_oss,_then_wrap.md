---
title: "should the default audio in wine by oss, then wrapped with padsp?"
date: 2008-04-26
forum: Wine
---

### Post by joshsmith on 2008-04-26
is there any reason why we wouldnt want this as the default?

You could then have the wine executable be changed so it actually loads padsp wine automatically.

Can anyone get alsa output to work properly through pulseaudio, ie appearing as a stream in pavucontrol, or making sound when another pulseaudio app is running? I can't.

am i missing something? oss and padsp seem to be the only way to get wine to play nice

---

### Post by schtufbox on 2008-04-26
I have wine set to use Alsa, so it can use wineasio as I run reaper in wine. Sound works  fine.
In games too sound also works fine even with other apps using sound. I've been running LOTRO and Counterstrike Source in wine, while listening to mp3's in Audacious

---

### Post by joshsmith on 2008-04-26
but is your audacious using pulseaudio? by default it doesnt (a bug), it uses alsa

i'm pretty sure that (unless you have a fancy soundcard that can do hardware mixing) you cant run wine using alsa, and any pulseaudio using application, and get sound from both. If you are running all non pulse using apps (or no apps) then sound will work, but not otherwise. Can anyone confirm this? or am i just dead wrong

I see lots of advice in this section of the forums telling people to use oss, and reroute it... so I kind of think it should be default

---

### Post by schtufbox on 2008-04-26
> **joshsmith said:**
> but is your audacious using pulseaudio? by default it doesnt (a bug), it uses alsa

i'm pretty sure that (unless you have a fancy soundcard that can do hardware mixing) you cant run wine using alsa, and any pulseaudio using application, and get sound from both. If you are running all non pulse using apps (or no apps) then sound will work, but not otherwise. Can anyone confirm this? or am i just dead wrong

I see lots of advice in this section of the forums telling people to use oss, and reroute it... so I kind of think it should be default
nope I set my audacious to use pulse. I don't have a fancy soundcard either, just onboard sound.

Just loaded audacious to confirm, yep def using pulseaudio, ran counterstrike source in wine using alsa just to check. Also worked fine both playing sounds together.
Must be something different between our setups if it's working for me and not for you, damned if I can think of it though.

---

