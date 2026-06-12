---
title: "no sound ibook 600 g3 breezy"
date: 2005-10-20
forum: x86 64-bit Users (Pre April '08)
---

### Post by zenlunatic on 2005-10-20
I have no sound on breezy on an ibook 600mhz g3 with 8meg video, but the sound worked in hoary and warty.  Any ideas?

---

### Post by crayon on 2005-10-24
Hi Zen,


    I too have that problem. But I found the solution on a mailing list (I forgot where). However, here's the simple solution:

1.) Open your **/etc/modules** file with your favorite text editor like Vi or Gedit with superuser/root access

2.) Look for the line containing *snd-powermac* and insert the following above it:

*dmasound-pmac*
*-r dmasound-pmac*

That's it, just insert those two lines. Restart your iBook and you should hear the wonders of music again. :)

Cheers!
Les

---

### Post by bhilton on 2005-12-05
I have an iBook 500 and the same problem.  Adding these lines didn't seem to make any difference.  Does anybody have any other ideas?

---

### Post by muchmusic on 2005-12-05
Check the default sink and try different outputs - are any available? do any work?

I expect at least ALSA to work in Breezy

to test, go to System menu, Preferences, Multimedia Systems

---

### Post by ssam on 2005-12-05
try this: [https://wiki.ubuntu.com/CommonProblemsMultimedia](https://wiki.ubuntu.com/CommonProblemsMultimedia)

---

### Post by bhilton on 2005-12-05
In the Multimedia Systems Selector, the default sink was set to ESD.  I tried changing it to ALSA and OSS, but none of them were able to play a test sound.

I've also messed around with the sliders in the Mixer to no avail.

---

### Post by bhilton on 2005-12-05
I had commented out the entries above and rebooted before making the change to the default sink.  I reinstated the entries in /etc/modules and changed to ALSA, rebooted again and now it works fine.

Thanks for your help!

---

