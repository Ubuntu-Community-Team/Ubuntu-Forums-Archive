---
title: "Can't play all streaming videos"
date: 2007-11-13
forum: x86 64-bit Users (Pre April '08)
---

### Post by sxjast on 2007-11-13
I have been using movie player to play internet videos(streaming). It works in most of the cases 
except when I watch videos from this site (for example, this video [http://www.zings-fm.com/1.Starplus/KGGK/13THNovKahaani.html](http://www.zings-fm.com/1.Starplus/KGGK/13THNovKahaani.html)). 

I tried both xine and gstreamer and didn't help.

Can someone please help me on this or any ideas?

Thanks
sxjast

---

### Post by John.Michael.Kane on 2007-11-13
That link played fine for me using.

```
sudo aptitude install mozilla-mplayer
```

and
```
sudo aptitude install mozilla-plugin-vlc
```

---

### Post by sxjast on 2007-11-15
Thanks for the help. Now I'm able to watch the videos fine.

---

### Post by Revfisk on 2007-11-15
I've been going nuts trying to watch videos at 
[http://www.nba.com/video/](http://www.nba.com/video/)

i've tried all the plugins and can't seem to configure them.  It was working two days ago, then poof.

Is there a way to choose which plugins are used in Mozilla, or does Mozilla just pick the most suitable if you have them all in?

thanks!

---

### Post by John.Michael.Kane on 2007-11-15
> **Revfisk said:**
> I've been going nuts trying to watch videos at 
[http://www.nba.com/video/](http://www.nba.com/video/)

i've tried all the plugins and can't seem to configure them.  It was working two days ago, then poof.

Is there a way to choose which plugins are used in Mozilla, or does Mozilla just pick the most suitable if you have them all in?

thanks!
Take your pick of the ones above, and remove the ones you don't want using synaptic. which in most cases would be totem-mozilla. clear your browsers cache, and re try the site you want to view.

---

### Post by Revfisk on 2007-11-16
I'm pretty sure I've removed everything except for mplayer.  It now manages to play the file, but ONLY as audio.  There is  no picture.  As I'm trying to watch sports highlights, this is a bit less than acceptable.  [-X

So any more advice would be much appreciated1  \\:D/

---

### Post by John.Michael.Kane on 2007-11-16
> **Revfisk said:**
> I'm pretty sure I've removed everything except for mplayer.  It now manages to play the file, but ONLY as audio.  There is  no picture.  As I'm trying to watch sports highlights, this is a bit less than acceptable.  [-X

So any more advice would be much appreciated1  \\:D/

Well I managed to get the videos at the site you linked to work testing was done using mplayer browser plugin, and the steps below.

Heres what I did. 

1) Try playing the video.
2) As the video is attempting to play right click on the box that will have the video.
3) Select configure.
4) Where it say video output change to x11.
5) Adjust the cache if you need to. During testing I made mine 2092.
6) Change percent of media to cache to 50.

Sorry the long steps,however. this should allow you playback files in your browser now.

---

### Post by Revfisk on 2007-11-16
Rock on.  You kick.... :-\"

Thanks!:):biggrin:

---

### Post by Revfisk on 2007-11-16
While I got your attenion (and way off topic) how do I put a neat little pic by my name like you've got?

---

### Post by John.Michael.Kane on 2007-11-16
> **Revfisk said:**
> While I got your attenion (and way off topic) how do I put a neat little pic by my name like you've got?

Click on UserCP then click edit profile.

Listed under settings & options is Edit Avatar click on it, and upload the file you want to use.

---

### Post by John.Michael.Kane on 2007-11-16
> **Revfisk said:**
> Rock on.  You kick.... :-\"

Thanks!:):biggrin:

Glad it is working.

---

### Post by Revfisk on 2007-11-16
Rock on.

---

### Post by devilscemo on 2007-11-18
hello all.. yes i have had the same problems as revfisk... i do have the mozilla mplayer plug-in also but i can't seem to play some streaming videos (for example the ones at nba.com) ... when i clicked on the video window no "configure" option showed up ... am i that stupid??? is there another way?? thanks for you help and time

---

