---
title: "Full screen flicker - missing plugin?"
date: 2009-11-08
forum: x86 64-bit Users
---

### Post by munitor on 2009-11-08
After doing a clean install of 64 bit 9.10, I'm having problems with playback of DVD video. Mplayer works fine in a window, but full screen, the image jumps and flickers. VLC won't play DVD video at all. Both of these worked fine under 64 bit 9.04.

I did have to move from "Extra" visual effects to "Normal" because it was randomly making my screen darken and windows jump. With "Normal" at least my desktop is behaving acceptably. Strangely, when I had "Extra" on, if I clicked the mouse in the lower right corner, it snapped things back to normal.

I'm running dual nVidia GeForce 7500, SLI on auto, single monitor.

I tried to figure out what this might be, but am a noob, and usually just search online until I find a solution. I haven't found a solution for this. I did note that when I ran gstreamer-properties, I get the message:

 Failed to load plugin '/usr/lib/gstreamer-0.10/libgstflatstm.so': /usr/lib/gstreamer-0.10/libgstflatstm.so: wrong ELF class: ELFCLASS32

so I am suspecting this *might* have something to do with it, and appears to be related to 64/32 libraries, but as these display problems are often complicated, I figured I'd ask for help before hosing things up too badly. Besides, I got "Prey", cairo dock, Citrix, Handbrake and all my other apps working, so am hoping this is just a little tweak that won't break the rest.

---

### Post by blueridgedog on 2009-11-10
Do you get the flicker if you switch to "none" for effects?

---

### Post by munitor on 2009-11-10
No, if its None, Mplayer works without a flicker in fullscreen. But then cairo dock gets a black background. Does this mean its an nVidia driver problem?

---

### Post by blueridgedog on 2009-11-10
That is my read on it.  I had the same issue with ATI cards, and switched to an nvidia.  I use the latest nvidia driver and have no issues.  Are you using the latest restricted driver?  There are posts of others downgrading, but that is beyond what I can walk you through.

---

### Post by munitor on 2009-11-10
Yes, I'm using latest restricted driver. I guess I'll have to wait for a solution. Don't watch much full screen video on my system, anyway.

---

