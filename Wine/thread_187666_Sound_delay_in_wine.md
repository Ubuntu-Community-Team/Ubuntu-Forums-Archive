---
title: "Sound delay in wine"
date: 2006-06-03
forum: Wine
---

### Post by KubuntuKilledMe on 2006-06-03
I can play Warcraft 3 fine with wine in kubuntu dapper but the sound i hear has nearly 1 second delay from what it should be. I've tried different settings in winecfg audio tab but it makes no difference. I'm using alsa output in wine.

Is there a way to fix this delay?

---

### Post by blacktorch on 2006-06-30
Don't know how to fix it, but I have the same problem. It's the same with Max Payne as well. I hope someone knows how to fix this...

---

### Post by Megatog615 on 2006-09-15
*BUMP*

I have this problem too.

---

### Post by XVampireX on 2006-09-16
Here comes your savior:

The problem is well known with wine. If you use ALSA, that most likely is the problem, as the wine alsa drivers are not good. I'm having the same problem trying to run D2:LoD with ALSA (Alot of lag between action and sound).

Solution: Disable (untick) ALSA and Enable (tick) OSS.

Hope that works.

WC3 worked for me last time I checked (No sound lag).

But if you really need alsa, you can *try* and run it (while in oss) via alsa-oss wrapper:

```

sudo apt-get install alsa-oss

```

and then

```

aoss wine /path/to/file

```

---

### Post by louman on 2006-09-18
i have an audio delay of about 50-100 milliseconds with pretty much everything i run with wine. i changed the settings to use OSS instead of ALSA but had no luck. I also tried using JACK with no luck. Anyone else have this problem?

---

### Post by ph0nph0n on 2007-09-06
After some testing, it turned out that setting the driver emulation to on on the audio tab of the wine config (run winecfg in a terminal, or click on the link in your applications menu) greatly decreased the sound delay. Well, at least that worked for me.

You probably don't give a **** about what i'm saying because your post was one year ago, but nevermind... others may have this problem now!

Hope this helps, hf and gl.

---

### Post by hyperair on 2007-12-05
Thanks man that really helped. I was suffering in a CS game earlier.

Just for additional info, I'm using pulseaudio, and I just stick padsp in front of everything.

---

### Post by oilgame on 2009-10-19
> **ph0nph0n said:**
> After some testing, it turned out that setting the driver emulation to on on the audio tab of the wine config (run winecfg in a terminal, or click on the link in your applications menu) greatly decreased the sound delay. Well, at least that worked for me.

You probably don't give a **** about what i'm saying because your post was one year ago, but nevermind... others may have this problem now!

Hope this helps, hf and gl.

Works great :) Thanks!

---

