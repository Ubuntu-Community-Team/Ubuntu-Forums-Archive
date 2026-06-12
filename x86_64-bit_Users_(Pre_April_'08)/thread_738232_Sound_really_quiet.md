---
title: "Sound really quiet?????"
date: 2008-03-28
forum: x86 64-bit Users (Pre April '08)
---

### Post by davedom on 2008-03-28
using a realtek ac97 5.2 channel audio codec

even with speakers and nvidia mixer at 100% is really quiet, would have been deafening in windows!!

---

### Post by John Jason Jordan on 2008-03-28
> **davedom said:**
> using a realtek ac97 5.2 channel audio codec
even with speakers and nvidia mixer at 100% is really quiet, would have been deafening in windows!!
I have the same problem, although I have the same problem in Windows.

Using lspci I find the the audio is:

00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)

This device is on the motherboard, which is an Asus M2NPV-VM. The OS is Gutsy, x86_64.

In troubleshooting I have done the following:

Installed Amarok and Exaile
Tried playing music CDs directly, as well as mp3s 
Booted to the latest beta of Hardy x86_64
Booted to Fedora 8 live x86_64

None of the above solved the problem. In all cases the sound is audible, but to be able to hear it at all I have to crank the volume to the max. This causes a bit of distortion, and it's not loud enough anyway.It's like the audio device is not putting out enough voltage.

---

### Post by hvc123 on 2008-03-28
you guys tried installing alsa-mixer? run it from terminal and use the arrow keys and space to unmute the required outputs (mine are maxed ut in the red)

this worked for me on my abit uguru an7 mobo

---

### Post by John Jason Jordan on 2008-03-28
> **hvc123 said:**
> you guys tried installing alsa-mixer? run it from terminal and use the arrow keys and space to unmute the required outputs (mine are maxed ut in the red)
this worked for me on my abit uguru an7 mobo
Thanks for the suggestion. I installed it and when I launched it everything was already maxed out. 

I'm beginning to think that the problem is the audio device on the motherboard. It just doesn't put out very much juice.

---

