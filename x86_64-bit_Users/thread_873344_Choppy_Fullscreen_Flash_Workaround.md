---
title: "Choppy Fullscreen Flash Workaround"
date: 2008-07-28
forum: x86 64-bit Users
---

### Post by Neo Adventist on 2008-07-28
Hello folks.  I haven't posted in a while, but I thought I'd share my $0.02 with you.

Many of us use Adobe's proprietary Flash plugin.  I am one of them.  And I think we can all agree that it sucks when playing in fullscreen mode.  In a native 64-bit environment, Adobe's proprietary Flash plugin is utter crap.  No matter how powerful your CPU or GPU may be, fullscreen Flash is choppy and pixilated.

Fortunately, I have recently discovered a fairly painless workaround for viewing fullscreen Youtube (Flash) videos.  If you are using the Firefox web browser, install the Video Download Helper extension.  If you find a Flash video you like, rip it from the webpage with Download Helper.  You can find it again in /home/<yourusername>/dwhelper

If opened with Totem Movie Player, your downloaded Flash video should play in fullscreen mode without screen tearing or pixilation.  VLC Media Player, MPlayer, and other movie players should also work fine.  Mind, a 4 MB Youtube video will still be in all its fuzzy Youtube glory :D

Forgive me if someone has already discovered this and posted it, or if this is otherwise "old news", for I obviously did not find it elsewhere in the forums.

My System:

Gateway 614GE
AMD Athlon64 3400+  @2.40GHZ
Via/S3 Graphics Unicrome Pro IGP
512 MB RAM (448 MB after IGP reservation)

Ubuntu64 8.04.1
Firefox 3.0.1
Download Helper 3.2

---

### Post by homerhomer on 2008-07-29
Damn!

Your Laptop sounds nice and flash is still slow?

Try the new flash 10 beta plugin.

just go to this website 
[https://launchpad.net/~thielmann/+archive](https://launchpad.net/~thielmann/+archive)

Add this guy's repo and you should then be able to remove the old flash and add the new beta, I hope it works.

apt-get update
apt-get remove flashplugin-nonfree
apt-get install flashplugin-nonfreebeta

---

### Post by Neo Adventist on 2008-07-29
Hmmm, maybe I'll give it a shot.  Adobe Flash 9 is a disaster when I try to watch full screen Youtube videos.  Which is why I use my workaround.

Oh, and btw, my system is a *desk*top, not a *lap*top  (hehe, no biggie). It's still 5-6 years old, though.  Was only $800 when I got it.

---

### Post by Neo Adventist on 2008-08-05
OK, so I've been trying out this Flash 10 beta plugin...... and fullscreen Flash videos still suck.  Still lagging, chopping, tearing, and pixilating.

Fortunately, using the "Download Helper" firefox extension and playing the videos through Totem still works wonderfully.

Oh well, it was worth a shot.

---

### Post by vscantu on 2008-11-25
> **Neo Adventist said:**
> Hello folks.  I haven't posted in a while, but I thought I'd share my $0.02 with you.

Many of us use Adobe's proprietary Flash plugin.  I am one of them.  And I think we can all agree that it sucks when playing in fullscreen mode.  In a native 64-bit environment, Adobe's proprietary Flash plugin is utter crap.  No matter how powerful your CPU or GPU may be, fullscreen Flash is choppy and pixilated.

Fortunately, I have recently discovered a fairly painless workaround for viewing fullscreen Youtube (Flash) videos.  If you are using the Firefox web browser, install the Video Download Helper extension.  If you find a Flash video you like, rip it from the webpage with Download Helper.  You can find it again in /home/<yourusername>/dwhelper

If opened with Totem Movie Player, your downloaded Flash video should play in fullscreen mode without screen tearing or pixilation.  VLC Media Player, MPlayer, and other movie players should also work fine.  Mind, a 4 MB Youtube video will still be in all its fuzzy Youtube glory :D

Forgive me if someone has already discovered this and posted it, or if this is otherwise "old news", for I obviously did not find it elsewhere in the forums.

My System:

Gateway 614GE
AMD Athlon64 3400+  @2.40GHZ
Via/S3 Graphics Unicrome Pro IGP
512 MB RAM (448 MB after IGP reservation)

Ubuntu64 8.04.1
Firefox 3.0.1
Download Helper 3.2

I have the same problem. I'd like to use the fixit you describe, but I don't use Firefox. I use Internet Explorer. Any thoughts on how I can fix this problem?

Victor

---

### Post by Kilz on 2008-11-25
> **vscantu said:**
> I have the same problem. I'd like to use the fixit you describe, but I don't use Firefox. I use Internet Explorer. Any thoughts on how I can fix this problem?

Victor

Are you a windows user using Explorer under windows?

---

### Post by meldroc on 2008-11-25
I've had pretty good luck using the new 64-bit Flash 10 alpha on my system, running AMD64 Hardy Huron.  It does use some GPU acceleration for playing video, which results in a big improvement in video quality and frame-rate.  Granted, there's only so much you can do with Youtube quality video, but this smooths out a lot of the pixellation and compression artifacts.  It also resolved 90+% of the crashes and grey boxes I've been experiencing with 32-bit Flash 9.

---

### Post by LibertyShadow on 2008-11-26
I have had success with the alpha 64-bit flash plugin as well.  In fact I just gave a presentation with 2 full screen youtube videos without a hitch!

So I wrote up a script and sent it via email to two colleagues running 64-bit, and it worked for them.  ( I took the purge lines from the flash 10 script by Kilz )

```

#!/bin/sh
#Remove old installs
sudo apt-get -y purge nspluginwrapper
sudo apt-get -y purge mozilla-plugin-gnash
sudo apt-get -y purge swfdec-mozilla
sudo apt-get -y purge flashplugin-nonfree
sudo rm -rfd /usr/lib/nspluginwrapper
sudo rm -f /usr/lib/firefox-addons/plugins/libflashplayer.so
sudo rm -f /usr/lib/mozilla/plugins/flashplugin-alternative.so
#start the install
sudo mkdir /usr/local/flash-64
cd /usr/local/flash-64
sudo wget http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.d20.7.linux-x86_64.so.tar.gz
sudo tar xvzf ./libflashplayer-10.0.d20.7.linux-x86_64.so.tar.gz
sudo ln -sf  /usr/local/flash-64/libflashplayer.so /usr/lib/firefox-addons/plugins

```

If you use epiphany you can install the flashplayer.  (I am using gecko in Hardy, haven't tested in webkit Intrepid yet)
```

sudo ln -sf /usr/local/flash-64/libflashplayer.so /usr/lib/epiphany-gecko/2.22/plugins/

```

---

### Post by steveneddy on 2008-11-26
> **vscantu said:**
> I have the same problem. I'd like to use the fixit you describe, but I don't use Firefox. I use Internet Explorer. Any thoughts on how I can fix this problem?

Victor

My answer is to install Ubuntu with Firefox or just start using Firefox.

I assume that you are on Windows.

Why would anyone still use IE in this day and age of secure browsing from Firefox or Opera?

---

### Post by saftaplan on 2008-11-26
I think that using the [Greasemonkey]("https://addons.mozilla.org/nl/firefox/addon/748") extension (also available in the Ubuntu repositories) along with [HQTube]("http://userscripts.org/scripts/show/24999") is a much better solution than the one you suggest. The script will replace the crappy Flash player with whatever plug-in that is capable of playing the video format, be it Totem, mplayer, Xine, VLC or something else. So you can choose your own player to stream the video and have no problems at all with fullscreen playback. Furthermore, you can always watch the HQ version of a movie, and it also adds a download link. And you can resize the embedded video and change the aspect ratio.

Ain't that nice :)

---

### Post by LibertyShadow on 2008-11-27
> **saftaplan said:**
> I think that using the [Greasemonkey]("https://addons.mozilla.org/nl/firefox/addon/748") extension (also available in the Ubuntu repositories) along with [HQTube]("http://userscripts.org/scripts/show/24999") is a much better solution than the one you suggest. The script will replace the crappy Flash player with whatever plug-in that is capable of playing the video format, be it Totem, mplayer, Xine, VLC or something else. So you can choose your own player to stream the video and have no problems at all with fullscreen playback. Furthermore, you can always watch the HQ version of a movie, and it also adds a download link. And you can resize the embedded video and change the aspect ratio.

Ain't that nice :)

Right, but does that work for flash-based websites, or just videos?

---

### Post by zim2dive on 2009-01-08
> **LibertyShadow said:**
> Right, but does that work for flash-based websites, or just videos?

You can also improve Flash performance in Intrepid by setting the Desktop Appearance effects to None.

---

### Post by zim2dive on 2009-01-08
I didn;t try 180.22 yet, but I can confirm that 180.18 does nothing to help full-screen flash on the 8200.. still chokes and dies on The Daily show and hulu HD (reverting to 173 fixes performance)

---

### Post by arimakun on 2009-01-25
that's it.. just got flash 10 in its deb version for hardy (directly from adobe), unistalled flash-nonfree and instaled the new one and the videos wont eat my cpu anymore when fullscreen, ocasionally get de CPU problem but restarting fixes it again (vieweing the same video in youtube gets sometimes 80-90% cpu and keeps like that for all flash videos, before restarting gets back to 30-40%). And still vsync problems (tearing) but I suspect that has little to do with flash since I've never been able to get vsync in any linux ñ_n (only in overlay and flash doesn't use it) so I guess we should get the new flash 10 and post if the high cpu usage is fixed in all systems or only in some (I have C2d and intel450gma with effects enabled).
By the way  I have all updates until now.

---

### Post by zim2dive on 2009-02-10
I haven't had a chance (and wont for a few days) to try it, but the new nvidia driver 180.29 appears to fix the Flash problems for the 8200/8300 (and maybe also 9300/9400).

---

### Post by wry on 2009-05-09
This fixed it for me
[http://spoilt.blogsite.org/wordpress/index.php/2008/07/04/flash-player-for-linux](http://spoilt.blogsite.org/wordpress/index.php/2008/07/04/flash-player-for-linux)
only seems to fix youtube videos though. abciview (australia) is still choppy

---

