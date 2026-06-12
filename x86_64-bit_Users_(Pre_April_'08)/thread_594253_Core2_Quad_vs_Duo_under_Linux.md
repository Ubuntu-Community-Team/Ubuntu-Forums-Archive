---
title: "Core2 Quad vs Duo under Linux"
date: 2007-10-27
forum: x86 64-bit Users (Pre April '08)
---

### Post by pony-tail on 2007-10-27
I am about to build a new machine . Most likely based on Core2 architecture but if Phenom turns out better I will go that way.
My question is pretty simple ! Is there any real world advantages to running a Quad core CPU under Linux over running a dual core ? Most likely to be setup with Kubuntu 64 7.10 .

---

### Post by Cryptic1911 on 2007-10-27
yes, 4 > 2

do it

---

### Post by Tlon on 2007-10-28
> **pony-tail said:**
> I am about to build a new machine . Most likely based on Core2 architecture but if Phenom turns out better I will go that way.
My question is pretty simple ! Is there any real world advantages to running a Quad core CPU under Linux over running a dual core ? Most likely to be setup with Kubuntu 64 7.10 .

Define 'real world'.  The benchmarks are out there.  In SOME applications, the quad core processors perform at just a shade under double what the dual core procs were able to pull off (which is pretty amazing if you think about it).  For other applications, the difference is negligible, and in very, very few the dual core procs show an advantage.  One wildcard I've yet to see in these benchmarks is the use of irqbalance, which should improve performance on multi-proc machines considerably.

---

### Post by pony-tail on 2007-10-28
The machine will only have Linux so what I was talking about was actual real world use with Linux running compiz-fusion playing and ripping video  playing and ripping mp3s some web surfing etc . So I would guess pretty much average use the only games I currently play (in Linux ) are Quake 2 & 3 and Unreal 2003 - nothing overly hardware intensive . An Athlon K7 does all of this - but it choked on the latest (7.10) version of Ubuntu . It runs but it is struggling . The machine to be replaced is an Athlon 3000+ with 512meg ram and an nForce2 chipset with a GF6800XT 128mb video card - So basically any current machine will out perform it .But I was looking to build something that  I would get the longest possible life out of .

---

### Post by blakeg on 2007-10-28
Pony-Tail,

wait another month or so till Intel puts out the Penryn 45nm processors. They should cost the same amount, but give better performance than the current conroe based Core2duo/quads.

I don't think you will notice anything amazing with a quad compared to running a duo chip. But you never know :)

BlakeG

---

### Post by nss0000 on 2007-10-28
Humm:

If you're writing/compiling your OWN  'C' for local use, GCC will NOT automagically distribute the execution tasks among multiple cpus. I imagine you can FORCE this in the code, but I haven't (mybad) got there yet.  

 Anyrate, if anything else is  running it seems the system will farm-that-out to cpus 2-3 ...etc.

---

### Post by eyelessfade on 2007-10-28
make -j 4 :)

---

### Post by keforex on 2007-10-28
My machine is Core 2 Extreme on an Asus P5K3 DeLuxe with 4Gb (soon to be 8Gb) and both Vista Ultimate x64 and Linux Ubuntu 7.10 / Gnome 2.20 x64 are running fine.

My graphics card is nVidea 8800 GTX.

This machine is FAST. I am not sure if all the apps under Linux use all 4 cores, but since I am running the processor at 3.34GHz and front bus at 1500 everything is so fast that I can't tell if one or four cores are in use.

The ONLY issue I am having so far is with the interface shell called mac4lin - some of the features aren't stable yet. The fact that I am also using a 30" monitor at 2560x1600 and a 19" at 1280x1024 probably doesn't help matters for mac4lin + Compiz but oh well.

I can throw anything at these CPUs and they won't even break a sweat...

---

### Post by syxbit on 2007-10-28
you have to be realistic though
the kernel dose a great job with multiple cores, even if apps don't.
so you could have 16 apps loaded up, and be smooth :)

---

