---
title: "So funny sound problem with Wine"
date: 2008-05-27
forum: Wine
---

### Post by Ioky on 2008-05-27
I just start to use Wine for a few days. and I discover some weird problem. I can't really get wine's sound work if my sound is not active. What I mean by that is. Wine's sound work, if I have some Music or whatever sound playing. And It fail while No sound is playing. 

additional information: This sound problem actually will only occur when any sound player are played once before wine run. in order, if I just boot up my system, and didn't do anything, wine will run OK. I am running wine 0.9.59

Don't know is that a bug. or just something that I need to config

Thanks

---

### Post by cogadh on 2008-05-27
What Ubuntu version are you using? What do you have configured for a sound driver in Wine?

---

### Post by Ioky on 2008-05-28
I am using ubuntu 8.04 and ALSA

---

### Post by cogadh on 2008-05-28
8.04 uses PulseAudio for its sound system, which has known problems with Wine. From the Wine FAQ:
> **2.24. Why isn't PulseAudio available?**

The Wine project has decided not to pursue a Pulse driver for Wine, at this time. We feel it is best to keep working on the more mature Wine Alsa driver. We are aware that some distributions use Pulse as the default, and this is unfortunate. PulseAudio is also known to be buggy when emulating Alsa/OSS and should be disabled for Wine.

There is an unofficial PulseAudio driver for Wine, but it is unsupported and do not submit bug reports while usuing it

---

### Post by javafiend on 2008-05-28
So should we be using PulseAudio primarily?  Can  PulseAudio be used for the system and ALSA used for Wine simultaneously?

---

### Post by cogadh on 2008-05-28
Whether or not you should be using Pulse is a matter of choice. I personally believe that Pulse is not really ready for general usage and that Ubuntu should have stuck with ALSA for the time being. I don't know if you can run ALSA and Pulse simultaneously, but you should be able to remove Pulse completely and replace it with ALSA, as ALSA is still available in the repositories. Don't ask me what steps might be required to do that, I use Kubuntu just because it still uses ALSA by default, so I've never had to deal with removing Pulse and replacing it with ALSA.

---

### Post by MemoryDump on 2008-05-28
pulse has a ton of potential, but I agree with cogadh.. it's not ready for prime time.. especially for a LTS release. Way too much manual configuring required.

---

