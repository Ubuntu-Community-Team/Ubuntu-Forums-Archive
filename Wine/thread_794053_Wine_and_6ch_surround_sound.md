---
title: "Wine and 6ch surround sound"
date: 2008-05-14
forum: Wine
---

### Post by psychok9 on 2008-05-14
I've a CMI8788 card (X-Meridian, series Oxygen HD).
For work 6ch with speaker-test i've configured .asoundrc:
```
pcm.dmixs51 {
	type dmix
	ipc_key 1024
	ipc_key_add_uid false # let multiple users share
	ipc_perm 0660 # IPC permissions (octal, default 0600)
	slave {
		pcm "hw:0,0" # see below
		rate 48000
		channels 6
		period_time 0
		period_size 1024
		buffer_time 0
		buffer_size 4096
	}
}

pcm.asym51 {
           type asym
           playback.pcm "dmixs51" 
           capture.pcm "hw:0,0" # this might be "dsnoop:0"
}

pcm.dsp0 {
         type plug
         slave.pcm "asym51"
}

```
[U]
But now, how can I use real 6ch surround sound on Wine?[/U]
My dist is Ubuntu 8.04 (fresh install).

Thank You!

---

### Post by cogadh on 2008-05-14
In Wine's sound settings, just tell it to use the PCM device you created (dmix51). I'm not on my Linux box right now so I can't confirm if you can do that through winecfg, but I know you can do it with one of Wine's [Useful Registry Keys](http://wiki.winehq.org/UsefulRegistryKeys)

---

### Post by psychok9 on 2008-05-14
If i set "pcm.dmixs51 { -> pcm.!default {" i don't get any sound.

---

### Post by Yellow Onion on 2008-07-09
try this adding this instead
(plug allows rate covertion)

pcm.!default {
     type plug
     slave.pcm "dmixs51"
}

but wine doesn't allow 5.1 (well last time I checked - right now Counter-strike source refuses to run on anything but 2 channels) anyway so you will only get 2 channels out

---

### Post by psychok9 on 2008-07-22
> **Yellow Onion said:**
> try this adding this instead
(plug allows rate covertion)

pcm.!default {
     type plug
     slave.pcm "dmixs51"
}

but wine doesn't allow 5.1 (well last time I checked - right now Counter-strike source refuses to run on anything but 2 channels) anyway so you will only get 2 channels out

:(
Is there anyone who knows if this feature is in development?
Thanks!

---

