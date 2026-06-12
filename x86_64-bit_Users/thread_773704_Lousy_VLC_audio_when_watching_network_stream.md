---
title: "Lousy VLC audio when watching network stream"
date: 2008-04-29
forum: x86 64-bit Users
---

### Post by restamp on 2008-04-29
I'm throwing this out mainly to see if anyone else is experiencing this, too, or might have some suggestions:

I just upgraded from 64-bit Feisty to 64-bit Hardy.  I have an [HDHomeRun]("http://www.silicondust.com/wiki/products/hdhomerun") box on my local LAN which I like to occasionally use with this PC.  I do this using [VLC]("http://www.videolan.org/vlc/") and its Network Stream interface.  (In both instances, I've used the Ubuntu-provided VLC package.) Under Feisty, VLC performs this task reasonably well, with only occasional dropped packets.  (At least, it does so until I do a suspend/restore, after which the number of dropped packets becomes unacceptable, necessitating a reboot if I wanted to seriously watch my HDHomeRun box.)  Under Hardy, the video reproduction is nearly perfect with very few dropped packets, but the audio borders on the unacceptable, with almost exactly 10% of the audio packets being dropped.  (I get this info from VLC's *Stream and Media Info* window.)  The audio starts out sounding acceptable, but within a few seconds (10?) it degrades to the point where every 10th packet is lost.

This is really my only major problem with Hardy I am still grappling with at this point -- I've resolved or worked around all the other glitches.  And, frankly, I'm not even sure it is a Ubuntu problem, but the same version of VLC works under Feisty.

Any ideas?

---

### Post by Knatchwa on 2009-04-28
Not sure if it this in line with the question, and this may of been a time back as today Jaunty is what I am using, but I use VLC to watch, streams, there seems to be more issues when trying to stream where it breaks apart on occasion, or has other issues.

---

