---
title: "0% Volume does not mean muted?"
date: 2009-06-04
forum: x86 64-bit Users
---

### Post by ddales on 2009-06-04
I just did a fresh install of Kubuntu 9.04 due to a hard drive failure.  I'm now having a strange problem with the sound that I didn't have before.  The only thing in my system that has changed was the hard drive and that can't be the cause.

I have a Logitech keyboard with volume controls.  With my previous installation of 9.04 I could turn down the sound and it was actually silent.  Now however, 0% volume does not mean silent.  I still get very low volume even though I turn the master channel down to 0.  Muting definitely means silent, but not 0% volume.

Forumed/Googled this and didn't find anything useful.  Most people have the problem in the other direction, no sound, whereas I can't make it be quiet.

Thanks in advance!

Details:
Asus M2N-VM HDMI Mainboard
AMD X2 6000+ processor
on-board Nvidia HD Sound
Kubuntu 9.04 fully patched
KDE 4.2.4 latest
Multimedia device preferences all set to Pulse Audio
Alsamixer all volumes max
Channel control in Kmix set to Master

---

### Post by ddales on 2009-06-12
Never done this before but,

BUMP!

No one has seen this, ever?

---

### Post by PatrickVogeli on 2009-06-12
try to set the keys to control the PCM track instead of the Master one.

---

### Post by ddales on 2009-06-12
Thanks for the tip.  I've already tried that.  I turn the master all the way up and use the PCM as the master channel.  Same result but now I've struck a balance between the two that I can live with.

Thanks

---

### Post by Ocxic on 2009-06-16
0% does not disconnect the audio channel. what you are hearing is the back ground hum of the hardware/audio channel, activating mute will disconnect the audio channel and your hardware will stop sending the audio signal to your speakers.

---

### Post by ddales on 2009-06-16
The sound that I hear is the music, not background hum or crackling.  It's the actual music playing just at a very low volume.

---

