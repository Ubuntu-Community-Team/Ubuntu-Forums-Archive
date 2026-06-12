---
title: "Pulseaudio problems"
date: 2008-07-21
forum: Wine
---

### Post by Nexusx6 on 2008-07-21
Hi,

I'm having troubles with stea/team fortress 2 and pulseaudio. The problem specifically is that when I run steam with the padsp wrapper like so:
> padsp wine steam.exe
I can get sound in TF2 but its causes the game to lag horribly. No matter what I do the graphics, or what level I start dxlevel at its very choppy.

/sigh. Can I have sound and enjoyable game play? I'm starting to seriously debate if I should even keep pulseaudio installed as all it does is cause problems, but not offer any really useful features >.> I would greatly appreciate any help

---

### Post by Nexusx6 on 2008-07-23
I solved my problem by renicing hl2.exe after I started TF2 up

```
sudo renice -12 -p [pid]
```

Open up system monitor and look for "hl2.exe" The pid of that process is what goes in the [pid] part (no brackets). You can only find the process *after* you have started up TF2 (or whatever steam game)

---

