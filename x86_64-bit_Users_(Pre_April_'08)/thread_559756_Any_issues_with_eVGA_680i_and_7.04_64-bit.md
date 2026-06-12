---
title: "Any issues with eVGA 680i and 7.04 64-bit?"
date: 2007-09-25
forum: x86 64-bit Users (Pre April '08)
---

### Post by Urinemachine on 2007-09-25
Hey guys I am probably going to be installing 64 bit ubuntu on my new PC but I wanted to see if anyone has it working on an eVGA 680i (NF68-A1) motherboard yet.  I am using 4GB of RAM (for now), a Quad Core Q6600, and an eVGA 680i NF68-A1.  I also have an Nvidia 8800 GTX (evga) that I'd like to have working full-fledge!

Any issues or warnings please let me know!

---

### Post by rada on 2007-09-26
All in all been happy with a similar setup (8800GTS not GTX). I've not gotten great results out of the onboard sound, but also haven't put the time into troubleshooting it. I'm not sure how much of that is motherboard related.

It's also very picky with memory. Sounds like you've already bought your memory, but if not, I would avoid 4 1GB modules, go with two 2 GB sticks, and research very carefully on eVGA forums before buying high end memory, make sure you really would benefit. Basically you want to stress the NF680 memory controller as little as possible and avoid memory voltages over 2.2 if at all possible. Depending on whether you're gaming, developing, rendering, file-serving, lame-ing, folding... whatever YMMV.

I have not used the onboard RAID, so if that's important to you I would post on [[COLOR="Blue"]phoronix[/COLOR]]("http://www.phoronix.com/scan.php?page=home") and eVGA forums and tech support to see if you can get some info there. One of the eVGA RAID tech support guys is a Gentoo user, so he knows what he's talking about.

eVGA support and community are great. Lifetime warranty on board is great. It would be wonderful to have more linux users active on the eVGA forums, so I'm tempted to selfishly say "yeah yeah, go for it!", but really to be honest I would say hold off for a month or so if at all possible. With new gnome, X out and Gutsy nearly released, P35 boards out, SLI not so great under linux yet, 8800GTX pretty bleeding edge, etc. You might make a very different decision if you keep researching for another couple of weeks.

For sensors support you would want to use Gutsy kernel and newer lm-sensors, and (as far as I can tell so far) you will only get coretemp, Vdimm, Vcore, +3, 5, 12 V. It seems that the chip sensing the NB|SB stuff and some of the onboard fans doesn't have a driver yet. Feisty with Gutsy kernel is easy to set up and works fine for me. 

Envy has worked smoothly for me for 1x 8800GTS. nvidia-settings and coolbits fine for me with the 8800GTS. Again, worth using Gutsy kernel so you can use newer proprietary nvidia driver. I would monitor [[COLOR="Blue"]phoronix[/COLOR]]("http://www.phoronix.com/scan.php?page=home") reviews and forums. Lots of great linux|Solaris based testing and reviews of all things hardware.. linux SLI review soon, I have read. **<Edit:> not soon, now:** [[COLOR="Blue"]NVIDIA SLI: Linux vs. Windows[/COLOR]]("http://www.phoronix.com/scan.php?page=article&item=860&num=1") Looks like latest nvidia driver gives SLI performance up to 75% of Windows in their tests. 

As far as GTX working "full fledge" -- what will you be doing with this rig? I'm not super wine literate, but I would bet you won't have anything like DX10 for a long time, and SLI  TBD

Unless you're dual booting into windows and making lots of use of SLI, really will make use of 3 full speed PCIe slots, or you have other specific reasons for wanting this mobo, I'd strongly consider other choices.

---

