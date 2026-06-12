---
title: "OK trying to copy a DVD"
date: 2007-07-27
forum: x86 64-bit Users (Pre April '08)
---

### Post by DaGGer on 2007-07-27
I'm trying to copy a dvd to my computer so I can burn it. I have the messanger and when I use acidrip, dvdrip, or thoggen dvd rip It doesn't work. Now when I use thoggen it says that I don't have some codes installed. libdvdcss2, it says I don't have this installed but I did but I couldn't get the win32 codec installed. I need some help. I want to copy a few dvds but I can't do it.

---

### Post by caryb on 2007-07-27
Try K9copy it works great for me!


Cary

PS it is in the repo's

---

### Post by DaGGer on 2007-07-28
ok now all my video is messed up. this really sucks, someone please help me out.

---

### Post by stmiller on 2007-07-28
[http://medibuntu.sos-sts.com/](http://medibuntu.sos-sts.com/)

This has win32codecs, libdvdcss2, etc. Add medibuntu to your system following their instructions.

dvdrip, k9copy, or handbrake are all good programs. K3B also has some ripping functionality I believe.

---

### Post by DaGGer on 2007-07-28
OMG thank you, I couldn't find anythingo n this stuff. I found how to do add but it wouldn't work for me and now it does. thank you so very much.

---

### Post by DaGGer on 2007-07-29
sorry thats a lie, it isn't working. When I try topen videos on firefox it just comes up with a bunch of letters, numbers, and symbols. Also when i try to open these files under totem (when I save the file to my computer) it won't start up. If I play is in VLC it works but the sound is very choppy.

---

### Post by stmiller on 2007-07-29
Read the sticky at the top of this forum for multimedia hints.

---

### Post by DaGGer on 2007-07-29
Ok well i've narrowed the problem down. Ok well now the video works fine if i DON'T start Firefox, but as soon as I start it and try to open a video it won't let me. I can have the video running and open firefox and its fine but if I close the video and try to reopen it won't work. Even if I ctl+alt+delete and log back in it won't work. I deleted all the things I added to the source.list file and checked to see if that was it. and it wasn't so I added the one package I need to it from that link above and its still the same. I'm thinking I'm having a problem with my sound because if I have Rhythmbox when I open firefox it makes it crash. So maybe I have some conflict in my sound or video.

---

### Post by DaGGer on 2007-07-29
ok update just minutes after. Well I had entered this code into the .asoundrc file

```
pcm.!default {
	type plug
	slave.pcm "surround51"
	slave.channels 6
	route_policy duplicate
}
```

and well now it works fine. Its weird because it didn't mess up my videos before this.

---

