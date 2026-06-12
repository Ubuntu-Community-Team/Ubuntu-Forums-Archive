---
title: "Does MPlayer work on AMD64?"
date: 2006-01-01
forum: x86 64-bit Users (Pre April '08)
---

### Post by handy on 2006-01-01
Has anyone managed to make mplayer do it's thing in 64bit?

Thanks,

handy

---

### Post by Bghmsh on 2006-01-01
Yes I managed to get it working about 1 hour ago load form synaptic I have even managed to get it streaming across the network

---

### Post by handy on 2006-01-01
Thanks for the reply.

I just refreshed & checked synaptic & found an AMD64 version of mplayer, I installed everything except where there was duplication 32/64bit.

Mplayer crashes badly, unfortunately for me.  I will try again in another month & see how it is going.  Having gXine, Totem & VLC will keep me going.  When Mplayer is working I can make an informed decision & dump the ones that I don't need.

Thanks again for your reply, I wouldn't have noticed the 64bit version without it.  :p 

Cheers,

handy

---

### Post by lunatech on 2006-01-01
mplayer works, but some of the codecs that it needs to play the closed formats are available in 32 bit version only.  Hence, some of the formats will not work.

---

### Post by nothreat33 on 2006-01-01
So you will be unable to play some media formats?

---

### Post by handy on 2006-01-02
I can play commercial DVD's with Totem, gXine & VLC.

Mplayer can't get near playing the same DVD's.

"Fatal Error:  MPlayer interupted by signal 11 in module:  decode_audio"

I don't think this is a codec problem.

Like all the others, this problem will become history soon enough, as the bugs are squashed underfoot.

handy

---

### Post by lunatech on 2006-01-02
[QUOTE=nothreat33]So you will be unable to play some media formats?[/QUOTE]
Yes.  However there are workarounds to make mplayer play all the formats.  You will have to check on their official website how they do it, since I don't ahve a 64 bit machine

---

### Post by gil-galad on 2006-01-02
[QUOTE=handy]I can play commercial DVD's with Totem, gXine & VLC.

Mplayer can't get near playing the same DVD's.

"Fatal Error:  MPlayer interupted by signal 11 in module:  decode_audio"
[/QUOTE]

That is actually a bug with the mplayer-amd64 package when it trys to decode dolby digital audio.  You can either recompile it yourself or use the mplayer-nogui package, which works but doesn't include the gui interface.

---

