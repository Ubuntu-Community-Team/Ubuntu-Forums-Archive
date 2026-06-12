---
title: "amd64-general kernel versus amd64-k8 kernel"
date: 2006-06-01
forum: x86 64-bit Users (Pre April '08)
---

### Post by miggl on 2006-06-01
What are the differences? I have installed the k8 kernel now and am 'imagining' that things are slightly quicker :). But the general kernel has been quick all along, too, so I'm not sure. I'm using an Athlon64 3500+ CPU with 2GB RAM and dual NVidia 6800 Ultras (SLI).

---

### Post by captive on 2006-06-01
Not really sure about it, but i think there are some differences in settings of things like preemption and timing.. The result should be a more "responsive" system.

---

### Post by henriquemaia on 2006-06-01
[quote=miggl]What are the differences? I have installed the k8 kernel now and am 'imagining' that things are slightly quicker :). But the general kernel has been quick all along, too, so I'm not sure. I'm using an Athlon64 3500+ CPU with 2GB RAM and dual NVidia 6800 Ultras (SLI).[/quote] 
With your specs, it is very difficult to notice any difference. I use the k8 kernel and everything wors, so it fine for me. If you have everything working on the k8 kernel, stay with it, since its optimized for your hardware (even thought you can't notice).

---

### Post by miggl on 2006-06-01
Thanks for the encouragement guys! I was doubting my actions, but it sounds like I did the right thing. :) I'll stick with it.

---

### Post by Bokonon on 2006-06-01
Plop in a AMD64-X2 processor and it will speed things up a lot.  Maybe not gaming so much, but my java applications sure work faster after I went from a AMD64 3500+ to a 4400+ X2.  If I remember, the 3500+ only has 512MB of cache.

I did a k7 to k8 kernel upgrade and things are a bit snappier, but the processor upgrade was definately noticeable.

The new chips are not that expensive and will certainly drop in price when AM2 hits the market strong.  Be sure to check your mobo for X2 support.  I had to download a BIOS patch.

---

### Post by miggl on 2006-06-02
[QUOTE=Bokonon]Plop in a AMD64-X2 processor and it will speed things up a lot.  Maybe not gaming so much, but my java applications sure work faster after I went from a AMD64 3500+ to a 4400+ X2.  If I remember, the 3500+ only has 512MB of cache.[/QUOTE]
I will try that in a few months... right now I'm on upgrade freeze (I spent about 2k on my machine and swore I wouldn't upgrade for another 2 years [yeah right!]) :).

---

### Post by cyrus7580 on 2006-06-02
Currently using an AMD 64 X2 3800+ and my kernel is the "amd64-generic" version. I think it's pretty fast, but I'm not sure it's registering both cores. 

My question is, how can you tell? Shouldn't "top" show two processors? Maybe /proc/cpuinfo? Should I switch to the K8 kernel from "generic"? 

Cyrus

---

### Post by miggl on 2006-06-02
[QUOTE=cyrus7580]Shouldn't "top" show two processors?[/QUOTE]

Yes, but you have to hit the "1" key to toggle between CPU summary and individual CPU load.

---

