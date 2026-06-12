---
title: "CPU frequency adjust problems"
date: 2009-03-07
forum: x86 64-bit Users
---

### Post by TomB19 on 2009-03-07
I'm running Kubuntu 8.10 - 2.6.27-11-generic.  CPU is a Phenom 9850b.  Motherboard is 790GX/SB750 based.

I installed lm_sensors and noticed in ksensors that the CPU frequency generally sits at 1250 MHz on this 2500 MHz CPU.  Fair enough.

I've seen it shift to 2500 MHz plenty of times but only for a moment or two.

Right now, I'm running two copies of DeVeDe which is transcoding a ton of video.  The Frequency is sitting at 1250.

I suppose part of the issue is that DeVeDe does not take advantage of multiple cores.  Each copy runs on a core.  Right now, I've got two cores nailed up to 100% usage and two cores more or less idling.

How can I tune the energy saving features to provide a little more muscle for times like right now?

---

### Post by dcstar on 2009-03-07
> **TomB19 said:**
> I'm running Kubuntu 8.10 - 2.6.27-11-generic.  CPU is a Phenom 9850b.  Motherboard is 790GX/SB750 based.

I installed lm_sensors and noticed in ksensors that the CPU frequency generally sits at 1250 MHz on this 2500 MHz CPU.  Fair enough.

I've seen it shift to 2500 MHz plenty of times but only for a moment or two.

Right now, I'm running two copies of DeVeDe which is transcoding a ton of video.  The Frequency is sitting at 1250.

I suppose part of the issue is that DeVeDe does not take advantage of multiple cores.  Each copy runs on a core.  Right now, I've got two cores nailed up to 100% usage and two cores more or less idling.

How can I tune the energy saving features to provide a little more muscle for times like right now?

You can change the threshold settings where it switches from one state to the other, but I'm not sure how much real benefit you would get.

You have to remember that things already change when the CPU demand requires it, and you will only be fiddling about with a setup that already does the job pretty well.

---

### Post by Chibone on 2009-03-08
Maybe you could change your power-saving preferences to performance so that the core always runs at 100% frequency.  Not sure how to do it in Kubuntu but the app I installed in Gnome is the CPU frequency applet.

---

### Post by Yellow Pasque on 2009-03-09
About the 1250MHz with two transcodings - that doesn't sound right. Hopefully, Ubuntu 9.04 (kernel 2.6.28.x) will have a better scaling algorithm.

> Maybe you could change your power-saving preferences to performance
Running the CPU at 100% all the time is a waste of electricity for most users. However, the user can temporarily switch with cpufrequtils, e.g.:
```
sudo cpufreq-set -g performance
sudo cpufreq-set -g ondemand
```

---

### Post by Arup on 2009-03-09
Easiest way to get 100% CPU is to turn off Power Now or Speed Step in case of Intel in the BIOS. However I don't advice it as it would run the fan at 100% putting more wear and tear. The scaling works out very good. I have done work with 100% CPU and scaling enabled. I have seen no performance difference whatsoever.

---

