---
title: "3gp videos on Ubuntu PPC?"
date: 2006-04-22
forum: x86 64-bit Users (Pre April '08)
---

### Post by Entity on 2006-04-22
Hi I'm able to watch 3gp videos on my Powerbook but I don't get any sound using totem-xine, mplayer, vlc or ffplay. Some has been able to get audio and video with these 3gp files? (Ubuntu Dapper Drake PPC)

---

### Post by aimislame15 on 2006-04-22
Install the correct gstreamer drivers and try it with that, they're in the repo.

---

### Post by Entity on 2006-04-22
[QUOTE=aimislame15]Install the correct gstreamer drivers and try it with that, they're in the repo.[/QUOTE]
What is the package name? I have mostly every gstreamer0.10-* installed except for the dbg and dev packages. totem-gstreamer gives me no sound just like the others.

---

### Post by amubu on 2006-04-29
did you find solution i have the same prblem

---

### Post by Entity on 2006-04-29
Nope.

---

### Post by glennric on 2006-05-03
I have the same problem with Dapper Beta.  No sound with these files.  I am on an Athlon XP 2700.  I have sound and video with RealPlayer, but do not have sound with MPlayer or Totem.

---

### Post by glennric on 2006-06-09
I finally got 3gp files to play with sound in mplayer, but I had to recompile mplayer with --enable-wmr_nb to get it to work.

---

### Post by laxmanbalu on 2008-05-12
> **aimislame15 said:**
> Install the correct gstreamer drivers and try it with that, they're in the repo.

I want to run a 3gp file in gstreamer with rtsp . 

I typed like this
gst-launch rtspsrc location=rtspt://172.17.5.197/sample_50kbit.3gp . But it is giving some error . My email id [email]laxmnabalu@gmail.com[/email] . At here I am using Darwin server. It follows like



Setting pipeline to PAUSED ...
Pipeline is live and does not need PREROLL ...
Setting pipeline to PLAYING ...
New clock: GstSystemClock
ERROR: from element /pipeline0/rtpamrdepay0: The stream is in the wrong format.
Additional debug info:
gstbasertpdepayload.c(270): gst_base_rtp_depayload_chain (): /pipeline0/rtpamrdepay0:
no clock rate was specified, likely incomplete input caps
Execution ended after 599000 ns.
Setting pipeline to PAUSED ...
Setting pipeline to READY ...
Setting pipeline to NULL ...
FREEING pipeline ...

so please give the exact gst-launch plugins to me

---

### Post by radopenev on 2008-05-14
Hi, everybody!
This is NOT fix the problem,but is quick solution!
[OnlineConverterToFlash]("http://www.bg-estate.org/TheWorldOf3D.php?convertor=on")
(Left panel)
1.browse
2.choice width x height(not necessary)
3.press button
After a while ,like YouTube, can watch the video...
Conversion with 3gp is OK.
But You  CAN DOWNLOAD zip with everything you need.
(blue link below player after conversion)
Unzip ,open html-file with  browser and ...voilà!:)

Sorry for my English!
Best regards!
p.s.I'm 3D artist and made that to upload my projects to the my site.I hope this is helpfully...English version is coming soon!
Your video is only for you and your friends!The link is active 1 hour!
Sorry but 30MB limit for video!

---

