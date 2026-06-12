---
title: "Wine 1.3.30+ and sound issues"
date: 2012-01-09
forum: Wine
---

### Post by Atroxus on 2012-01-09
Hi,

So when 1.3.25 came out it busted sound quite a bit. There was a thread ([http://forum.winehq.org/viewtopic.php?t=13182&postdays=0&postorder=asc&start=50]("http://forum.winehq.org/viewtopic.php?t=13182&postdays=0&postorder=asc&start=50")) on the wine forums discussing using .asoundrc to resolve some of it (dardack's guide near the end).  I tried it out and it worked fantastically.  Both wine and pulseaudio talk to dmixed devices from asoundrc and most of my sound issues were gone. wine, pulseaudio, flash etc all worked.

Fast forward to 1.3.30.  Wine switches the setup for sound again.  The new setup works very well however wine seems to completely ignore any asoundrc setup and accesses alsa devices directly and exclusively. This causes immediate issues with pulseaudio (asoundrc or no) and any other application trying to use alsa at the same time.

I have tried getting this working with and without pulseaudio, with and without my asoundrc changes all without success. So it is probably a wine or alsa issue.  Right now I just keep bouncing back and forth between 1.3.29 and 1.3.35 depending what I'm playing.

Anyone else having similar issues or suggestions on how to fix this?

ubuntu 10.04
Pulseaudio: 0.9.22~0.9.21+stable-queue-32-g8478-0ubuntu14
libasound2: 1.0.24.1-0ubuntu6~lucid1

Thanks.

---

### Post by Atroxus on 2012-01-11
So I did make some progress with this yesterday.

Back to using the pulseaudio alsa plugin.  This is the default in ubuntu where apps using alsa are routed thru pulseaudio then thru alsa to the sound card.

.asoundrc:```

pcm.!default { type pulse } 
ctl.!default { type pulse } 
pcm.pulse { type pulse } 
ctl.pulse { type pulse } 
```

As usual this routinely drops sound within wine but it's usable.  This is originally why I had changed my configuration because wine was dropping sound all the time with the alsa plugin.  Anyone been able to get around this?

I can remove this pulse asoundrc setup which defaults wine back to using alsa directly (for things like Skyrim).  The rest of the time I guess I'll have to live with unstable audio from the pulseaudio alsa plugin.

---

