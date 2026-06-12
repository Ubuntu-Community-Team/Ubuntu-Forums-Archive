---
title: "Trouble playing .RMVB files"
date: 2007-01-08
forum: x86 64-bit Users (Pre April '08)
---

### Post by Metal03 on 2007-01-08
I've installed a few video codecs in the past few days (using Atomatix) and I got all my videos working but one kind of file...

the .RMVB files won't play...  I'll only get the audio playing and not the video.

Anyone knows how to fix that?

---

### Post by pay on 2007-01-08
There are codecs here [http://www.mplayerhq.hu/design7/dload.html](http://www.mplayerhq.hu/design7/dload.html) that can be used to play real video. Also you can use realplayer to play it.

---

### Post by Metal03 on 2007-01-09
.RMVB files are special Real videos

I still haven't been able to play them in Real player...  it seems the sound play good, but the video won't play at all!!  I must be missing something!!

---

### Post by pay on 2007-01-09
Look at this [https://help.ubuntu.com/community/RestrictedFormats/WindowsCodecs](https://help.ubuntu.com/community/RestrictedFormats/WindowsCodecs) and this [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by Vanish00 on 2007-01-20
I'm having the exact problem in trying to get my .rmvb files to run.  I tried visiting [http://www.mplayerhq.hu/design7/dload.html]("http://www.mplayerhq.hu/design7/dload.html") but I have no idea what files I need to download.  Pay, think you could tell which ones I need.  At the moment I have the default mplayer.

---

### Post by janfsd on 2007-01-21
Well the windows codecs will work if you are on i386, but not on amd64. I play them with RealPlayer, but at the beginning I had some video problems, just got fixed by running realplayer with aoss (you will need to install it first, i thinks you just need sudo apt-get install aoss) and after try to run like this:
aoss realplay
Try this.

---

### Post by Vanish00 on 2007-01-21
I ended up going with Totem Player.  Got everything to work perfectly there, thanks for the reply! :)

---

### Post by wh0rd on 2007-01-22
installed w32codecs

Real Play 10 - No audio. Yes Video.
Totem - Yes audio. No Video.
VLC - No audio. No Video.
Mplay - ERROR.

:roll:

installing xfmedia player worked!

---

### Post by zhumingvictor on 2007-02-23
> **wh0rd said:**
> installed w32codecs

Real Play 10 - No audio. Yes Video.
Totem - Yes audio. No Video.
VLC - No audio. No Video.
Mplay - ERROR.

:roll:

installing xfmedia player worked!
Hi, I got exactly same problems. Can anybody help?

---

### Post by uuwatti on 2007-03-01
seems like rmvb files have something against xv. switch your video output to gl and they should work fine.

---

