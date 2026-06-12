---
title: "mplayerplug-in problem, sound ok but no image"
date: 2006-04-23
forum: x86 64-bit Users (Pre April '08)
---

### Post by Entity on 2006-04-23
I installed mozilla-mplayer on Dapper, but when I try to view a video within the browser I see the plugin download the video, I get the sound but not the image.

Any idea on how to solve this?

---

### Post by davygravy on 2006-04-23
I have the same problem - I want to watch the New Hour video segments from PBS.org, and I also get sound, but no picture...

...so, I second that call for a solution.

Ideas, anyone?

---

### Post by dimitri6000 on 2007-02-19
Check this file:

/home/user/.mplayer/config

for this line:

really-quiet="1"

and comment it out, like this:

#really-quiet="1"

It was intended to suppress console output, but it was keeping the video from being viewable unless I went into Full Screen mode.  Once I removed that line, the videos were back again.

---

### Post by Kilz on 2007-02-19
> **Entity said:**
> I installed mozilla-mplayer on Dapper, but when I try to view a video within the browser I see the plugin download the video, I get the sound but not the image.

Any idea on how to solve this?

You may want to look in my signature for the 32bit Firefox 2.0 setup with java, Flash, and Mplayer plugins for Dapper.

---

