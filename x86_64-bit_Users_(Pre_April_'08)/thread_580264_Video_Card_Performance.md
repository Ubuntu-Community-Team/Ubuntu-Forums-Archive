---
title: "Video Card Performance"
date: 2007-10-18
forum: x86 64-bit Users (Pre April '08)
---

### Post by ishkabob on 2007-10-18
I recently built myself a new machine with the following specs hoping to play some games:

MSI mobo w/ nvidia MCP61 chipset
AMD Athlon 64 X2 4800+ (dual 2.5 ghz cores)
500GB SATA drive
2 GB RAM
Geforce 8400 GS w/ latest drivers from NVIDIA's website.

I've run a couple older games with satisfying results but when I run glxgears, I only get an FPS around 3000.  I know glxgears isn't a reliable benchmarking tool, but I feel like my FPS should be quite a bit higher than that (according to posts i've seen here).  Can anyone affirm/contradict/comment on this conclusion?  Do I need to change some video card setting?

---

### Post by belgarth on 2007-10-18
Hi all, just wanted to add in my experience with my AN-M2HD and ubuntu.

I just bought a new system to set up as an HTPC here are the specs:

motherboard: AN-M2HD 
Processor: AMD 64 X2 4600+
RAM: 2GB
Hard drive: 750 GB WD Cavier SATA
Tuners: HdHomerun and PVR-150

This system is to be connected to my Sharp Aquos 46 inch 46d92u lcd tv.

I have tried Fiesty, Gusty Alpha Tribe 5, Gusty Beta, and Gusty RC1 and in each case, the install works except for 2 problems. 1) no audio over hdmi. I accept now that it isn't yet supported in linux and I'm ok with using another connection until it is
2) I cannot output at 1080i or 1080p. I am able to get 720p to work with no problem, but 1080p isn't listed as an option. I've inspected the log and it shows the resolution as not supported. I've tried tweaking the config file according to every guide I can find with no luck.

I'm installing Gusty release now, I'm hoping it works better, but since the installer said it couldn't detect my screen or card correctly, I don't have high hopes.

I have tried with both hdmi to hdmi and hdmi to dvi with no luck. I'm going to try connecting to different hdmi ports on the tv and see if that makes a difference.

If people seem to be having trouble with 64-bit, maybe it is 64-bit specific. I may try 32-bit and see if it works any better.

If anyone has any other ideas let me know.

Also to note, I had a old pc with ATI 9800 Pro I was using as a htpc temporarily and it displayed 1080p without a problem. I'm not sure if that means the problem is just with my the integrated vido or an incompatibility of the tv and video.

---

### Post by saru411 on 2007-10-19
> **belgarth said:**
> Hi all, just wanted to add in my experience with my AN-M2HD and ubuntu.

I just bought a new system to set up as an HTPC here are the specs:

motherboard: AN-M2HD 
Processor: AMD 64 X2 4600+
RAM: 2GB
Hard drive: 750 GB WD Cavier SATA
Tuners: HdHomerun and PVR-150

This system is to be connected to my Sharp Aquos 46 inch 46d92u lcd tv.

I have tried Fiesty, Gusty Alpha Tribe 5, Gusty Beta, and Gusty RC1 and in each case, the install works except for 2 problems. 1) no audio over hdmi. I accept now that it isn't yet supported in linux and I'm ok with using another connection until it is
2) I cannot output at 1080i or 1080p. I am able to get 720p to work with no problem, but 1080p isn't listed as an option. I've inspected the log and it shows the resolution as not supported. I've tried tweaking the config file according to every guide I can find with no luck.

I'm installing Gusty release now, I'm hoping it works better, but since the installer said it couldn't detect my screen or card correctly, I don't have high hopes.

I have tried with both hdmi to hdmi and hdmi to dvi with no luck. I'm going to try connecting to different hdmi ports on the tv and see if that makes a difference.

If people seem to be having trouble with 64-bit, maybe it is 64-bit specific. I may try 32-bit and see if it works any better.

If anyone has any other ideas let me know.

Also to note, I had a old pc with ATI 9800 Pro I was using as a htpc temporarily and it displayed 1080p without a problem. I'm not sure if that means the problem is just with my the integrated vido or an incompatibility of the tv and video.

do NOT hijack others threads. MAKE YOUR OWN!

---

### Post by saru411 on 2007-10-19
> **ishkabob said:**
> I recently built myself a new machine with the following specs hoping to play some games:

MSI mobo w/ nvidia MCP61 chipset
AMD Athlon 64 X2 4800+ (dual 2.5 ghz cores)
500GB SATA drive
2 GB RAM
Geforce 8400 GS w/ latest drivers from NVIDIA's website.

I've run a couple older games with satisfying results but when I run glxgears, I only get an FPS around 3000.  I know glxgears isn't a reliable benchmarking tool, but I feel like my FPS should be quite a bit higher than that (according to posts i've seen here).  Can anyone affirm/contradict/comment on this conclusion?  Do I need to change some video card setting?

the 8400 is not a gaming card. it only has a 64 bit interface.

---

