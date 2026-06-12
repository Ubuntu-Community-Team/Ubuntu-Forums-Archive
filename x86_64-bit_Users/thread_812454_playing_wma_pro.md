---
title: "playing wma pro"
date: 2008-05-29
forum: x86 64-bit Users
---

### Post by pixel :-) on 2008-05-29
wma are reversed engineered except wma pro(wma 10).
Anyone had any luck with making it work without a virtual PC.I already have windows in virtual box, but i find it heavy handed.

I tried to force w32codecs,didn't do anything.Are they some packages that i can install?if i force a mplayer32,will it work(i'll try this tomorrow)?

I tried vlc for windows,in wine,apparently it missing a library for wma pro,any ideas what?I copied the dlls from w32codecs in the dll folder of vlc for windows.This will not work?I knead to add something in the registry.

Or at least,is there any wmv(with wma pro) to ogg converter for windows?Working either under wine or simply in virtual box.

---

### Post by soxs on 2008-05-30
in case you have medibuntu repos in your sources list, you could simply install w64codecs

---

### Post by pixel :-) on 2008-05-30
w64codecs are not equivalent to w32codecs (w64=623kB,w32=~30M).I had tried this before,thats why i forced w32codecs

---

### Post by soxs on 2008-05-30
I don't really know mtoo much about that, but I had no problems playing all my DVD/media files so far.

---

### Post by James_mtl on 2008-05-30
I'm on the same boat.  At work I sometime need to listen to streaming event and they use wma ( not sure which version ).  I used to be able to listen to the stream with mplayer and the w32codecs when I was in Gutsy 32 bits.  I upgraded to Heron 64 bits and now only realizing same thing : w64codecs is not w32codecs.  I'm still looking for a way to listen to my streams other then reinstalling everything 32 bits.

---

