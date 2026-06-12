---
title: "Sound issues (vent &amp; wow)"
date: 2008-11-12
forum: Wine
---

### Post by aquaspeeder on 2008-11-12
Hi, I just upgraded to 8.10 yesterday. I've been running wow + vent in wine for about a year without this problem until now. The sound is very, i'm not even sure how to describe it, scratchy/staticy? sounds somewhat dragged out and just plain terrible. Elsewhere I don't seem to be having any sound issues so I don't know if this is a wine problem or an alsa problem. I'm using version 1.1.8 of wine right now and these are my settings:

Box checked to use alsa driver
Direct Sound: Emulation
Default Sample rate: 48000
default bits per sample: 16
Driver emulation checked 

Any ideas?


edit: nevermind. fixed by uninstalling wine and going back to version 1.0.1

edit again: now I'm having a different problem where vent sound just dies entirely after a few minutes. Earlier it was working without problem for awhile but now it just keeps cutting out and going silent even though i know people are talking.

---

### Post by Tea4all on 2008-11-12
Try changing Emulation to Full. Set sample rate to 44100. Uncheck driver emulation. Press apply.

---

