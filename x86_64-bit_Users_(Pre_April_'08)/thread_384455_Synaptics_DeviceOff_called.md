---
title: "Synaptics DeviceOff called"
date: 2007-03-14
forum: x86 64-bit Users (Pre April '08)
---

### Post by Luna.jp on 2007-03-14
*hmm...looking more into it, I find that that might not be the problem but something to do with (**) RADEON(0): RADEONCloseScreen coming up in the BAD log...hmm..any ideas?*


**Short Version**
In my Xorg.0.log I see this, "Synaptics DeviceOff called"
This is the only thing stopping me and total world domination, sound and no blank screens.
Help me, how do I disable this from starting up during the normal boot process?


**Long Version**
Good evening.
I have a question about Xorg.conf that I hope you can help me with.
I have been trying to get Ubuntu 6.10 64bit to work properly on my Gateway 7510GX while sister to a WinXP partition and using the windows boot loader.
I have come near the end of my coffee pot, Starbucks is closed and I have one problem remaining.

Aside from sometimes the whole Ubuntu won't boot up and I get a blank screen RANDOMLY, I got a fix for this.
I simply go into the recovery setting, and type startx and everything works great. No hal.dll error, sound is on, and it is fast using my radeon driver, vice ati like it use to say in Xorg.conf.

I didn't understand. Why would startx work but the normal boot would hang? So onto the logs, two of them. One for when it boots without me, and the other when it boots by me going to recovery mode, and typing startx.

The only difference is this.

Synaptics DeviceOff called

Then some mumbo jumbo that I don't understand. But perhaps you do.
I'm thinking, if I can disable this *Synaptics DeviceOff called* monster, I can boot normally into Ubuntu and everything will work. So...how do I stop this?

PS:
I cut the log files so I can upload them here...Just look towards the end to see the difference.

---

### Post by Luna.jp on 2007-03-14
What is the significance of this *ProcXCloseDevice*?

---

