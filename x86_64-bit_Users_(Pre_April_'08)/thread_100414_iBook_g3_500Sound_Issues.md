---
title: "iBook g3 500Sound Issues"
date: 2005-12-07
forum: x86 64-bit Users (Pre April '08)
---

### Post by bhilton on 2005-12-07
I've got a couple of strange things going on.  

1.  System sounds are working fine through the laptop speakers.
2.  XMMS works through the laptop speakers.
3.  Nothing works through the headphone output.
4.  Rythmbox crashes on every attempt to play anything.
5.  Totem gives me the following error message...
     "falied to play:  Could not get/set settings from/on resource."

Ideally, I'd like to use Rythmbox so that I can listen to my iPod and internet radio.

I realize that there may be several things at play here, but I don't know where to start.

Anybody have any ideas?

Thanks,

Brad

---

### Post by ssam on 2005-12-07
first thing is to open up the volume control panel (rightclick (f12) on the volume applet.)

go to its preferences and tick on everything.

have a play with all the sliders and switches. this may get you're headphones working.

then next thing to have a play with is systym -> preferences -> multimedia system selector. and have a play with different outputs. that chooses the gstreamer output (gstreamer is the audio system that rhythmbox uses) that may get rhythmbox working.

note: some of the sound servers can only play sound from application at a time.

---

