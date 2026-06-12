---
title: "Kubuntu 64 movies"
date: 2005-05-09
forum: x86 64-bit Users (Pre April '08)
---

### Post by Terracotta on 2005-05-09
I have an amd64 and kubuntu 64 running on it, but every time I close kaffeine, it crashes, sometimes it crashes when opening a file. I think it has something to do with missing codecs, I know there are no win64 codecs available, but are their native linux codecs for all media filetypes, and are their other players to play them with.
I'm looking for a complete player, wich can play music and videos/dvd's ..., At the moment all media things are to be done with different programs, and the strange thing is, only kaffeine (when it doesn't crash) gives sound.

---

### Post by FluffyElmo on 2005-05-09
I don't use Kubuntu, so some of what I suggest might not apply. A few thoughts...

After installing Kaffeine I lost sound in other apps. I think changing the audio output to 'esd' fixed that problem. While you're messing with settings try changing the 'video driver' setting as well. Some options cause crashes for me while others work. Trial and error worked for me. 

In Kaffeine these settings are under Settings->xine Engine Parameters. Global settings are in System->Preferences->Multimedia System Selector.

Codec wise, I have Totem-xine, MPlayer64 and Kaffeine installed along with every codec i could find in synaptic (search for 'codec' in Name/Description). I can play pretty much everything I've tried except WMV10 files. 

Finally, I don't know if there is a unified player that's decent, I use Totem-xine for video and Rythmbox for music and it works pretty well though.

---

### Post by Wowbagger on 2005-05-14
Hoary comes with the 1.0.0. Version of the xinelibs. So Download xinelib 1.0.1 from [xinehq](http://xine.sourceforge.net/), compile and install it - voilà (worked for me). The changelog of the xine-libs mentions changes in 64bit compliance of some decoder between 1.0.0 and 1.0.1. Probably there will soon be an update of the xine-libs.

---

### Post by Terracotta on 2005-05-15
Thanks for the help but they are already 1.0-1 in the repositories. And they didn't solve the problem. Kaffeine crashes upon closing if it started to play a file, and when it doesn't start one, it crashes trying to open it.

---

### Post by devil28 on 2005-05-15
there is a version 0.6.1 of kaffeine on the net(its a deb-file). cant tell you where right now. that did the trick for me.

---

### Post by AndreAPL on 2005-05-21
[QUOTE=devil28]there is a version 0.6.1 of kaffeine on the net(its a deb-file). cant tell you where right now. that did the trick for me.[/QUOTE]
 have same problem :( can't play any movie with kaffeine, either with win32 codecs and totem/vlc...

---

### Post by Octane on 2005-06-18
[QUOTE=AndreAPL]have same problem :( can't play any movie with kaffeine, either with win32 codecs and totem/vlc...[/QUOTE]
 Just wanted to say, I'm having the same exact problem. I don't its a codec problem (since i have tried playing many different files).

[QUOTE=devil28]there is a version 0.6.1 of kaffeine on the net(its a deb-file). cant tell you where right now. that did the trick for me.[/QUOTE]
[http://mirror.hamakor.org.il/pub/mirrors/debian-amd64/pool/main/k/kaffeine/kaffeine_0.6-1_amd64.deb](http://mirror.hamakor.org.il/pub/mirrors/debian-amd64/pool/main/k/kaffeine/kaffeine_0.6-1_amd64.deb)

That doesn't do the trick though

---

### Post by Optimal Aurora on 2005-06-18
Yes I noticed that when I **use to use** Kubuntu... But running Ubuntu, totem-xine I don't have that problem... So you will probably have better luck with totem-xine...

---

### Post by ::DoGG:: on 2005-06-21
HEY!
I`m not using kubuntu, but i got a big problems with movies too. tries with kaffeine, totem, xine etc..
Then i finally found a deb package from amd64 debian distro with mplayer, installed it by hand and worked great for me!
But i still had some audio desync problems, so i followed the howto on this forum for solving that (on motherboards with nForce chipset - generally it`s disabling the sound server, proper asound config file and settind default diver to alsa , not ESD- which btw for me is a royal piece of crap).
Hope that helps.

---

### Post by NickB on 2005-06-21
For most everything except mpeg4 encoded videos, I find xine works best for me.  For mpeg4 (like divx, xvid, etc), only mplayer/gmplayer doesn't segfault when trying to play the video.  However, I have yet to have mplayer successfully play a majority of my DVDs.

Nick

---

