---
title: "TV Video Play"
date: 2007-12-10
forum: x86 64-bit Users (Pre April '08)
---

### Post by fjgaude on 2007-12-10
Can anyone tell me what they did to get this site to play videos:

[http://www.foodnetwork.com/food/video_guide/](http://www.foodnetwork.com/food/video_guide/)

I installed 64-bit Gutsy fresh, and did let it auto do everything as needed, but this site is not working for video playback. The site loads, flash works, but the playing of the video doesn't. Could I need other than Totem, Movie Player?

Thanks.

---

### Post by coskierken on 2007-12-10
Here is link for you.  My buddy developed it and it is a LIFESAVER.  It is called uBackup! but it has utilities in the menu to get all the codecs you need to fix the video problem.  :lolflag:

[http://ubuntuforums.org/showthread.php?t=613462](http://ubuntuforums.org/showthread.php?t=613462)

---

### Post by fjgaude on 2007-12-10
Thanks, but the question, can you play the videos in the link I posted?

---

### Post by vinmar on 2007-12-10
The videos play for me on Gutsy 64-bit. If I right-click on the video and select About it says it is playing through:

-----
totem-plugin-viewer 2.20.0
Browser Plugin using xine-lib version 1.1.8
-----

But I don't get any sound...

edit: Actually not quite true, I get sound on some of the videos.

---

### Post by fjgaude on 2007-12-10
> **vinmar said:**
> The videos play for me on Gutsy 64-bit. If I right-click on the video and select About it says it is playing through:

-----
totem-plugin-viewer 2.20.0
Browser Plugin using xine-lib version 1.1.8
-----

But I don't get any sound...

edit: Actually not quite true, I get sound on some of the videos.

Thanks... I see, mine says I'm using GStreamer 0.10.14, of totem-plugin-viewer 2.20.0. So Gutsy doesn't auto install the right Browser Plugin, in this case gstreamer for me, xine-lib for you.

Thanks again for pointing to an issue. So many varied ways to get to what we want, eh?

---

### Post by fjgaude on 2007-12-11
Well, I installed xine, gxine and still cannot play those videos, nor play simple DVD movies and the like.

How did you install the various codecs for your system? The uBackup script produces an error in my terminal.

---

### Post by fjgaude on 2007-12-11
Okay, folks, I took out gstreamer, leaving totem, but added all the xine plugins in Synatic. And all work now. Maybe gstreamer would have worked if I had done the same thing with it.

(As far as I know, can tell, 64-bit Gutsy works perfectly in all functions on my main box. Hooray!)

Is gxine between than gstreamer in Totem, have more features? Who knows?

---

