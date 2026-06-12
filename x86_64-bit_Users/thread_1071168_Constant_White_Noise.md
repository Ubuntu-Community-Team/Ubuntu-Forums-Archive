---
title: "Constant White Noise"
date: 2009-02-15
forum: x86 64-bit Users
---

### Post by mateocicoria on 2009-02-15
I am completely new at this. I installed Ubuntu 8.10 (64 bit) to see what Linux was all about. The only thing that I have installed other than the OS is flash player I believe. I must have gotten lucky, because from some of the things I have seen flash player does not install on 64 bit Ubuntu, but I seem to have downloaded a file straight from adobe that worked. No matter.

Since installed the OS originally, I turned off the onboard audio on my motherboard, and installed a Sound blaster Live! 5.1 (model no. sb0100) soundcard. Now when booting into Ubuntu, I get an extreme amount of white noise (static) when no sound is playing.

The sound works through the card, but when I am not playing anything the speakers just his, and when I do play stuff, they still hiss just much more quietly. How do I fix this?

---

### Post by mateocicoria on 2009-02-19
bump.

Where can I find info on clearing the drivers Ubuntu WAS using when I had my onboard sound enabled, and then info on installing the drivers for the Live! card that I use now?

---

### Post by Clancy_s on 2009-02-19
I'm no gun so I can't advise you directly.  I found this how to on Pulse Audio cleaned up the sound in my 8.10 64bit install very nicely:

[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

---

### Post by Yellow Pasque on 2009-02-19
If you disabled the onboard audio in the BIOS, then Linux won't load a driver for it.
My guess is that your issue is caused by input/mic levels being too high. Run alsamixer and make sure your inputs are at moderate level (or muted if you don't intend to use them).

---

### Post by mateocicoria on 2009-02-22
The problem has been found. I ran ALSA, and found that by default the drivers for the Live! card in Ubuntu enable the digital out port, which doubles as a subwoofer/center channel port. So I was getting hiss because I do not have any digital equipment, but had my sub and center channel plugged into the enabled digital out.

---

