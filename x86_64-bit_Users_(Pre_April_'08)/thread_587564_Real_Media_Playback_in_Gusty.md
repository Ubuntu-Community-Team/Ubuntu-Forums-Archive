---
title: "Real Media Playback in Gusty"
date: 2007-10-22
forum: x86 64-bit Users (Pre April '08)
---

### Post by Modius on 2007-10-22
After upgrading to Gusty, I realized that my mplayer won't play rm video, but the sound is working fine.

So I tried reinstalling w32codec/w64codecs in every reasonable location (usr/lib/codecs, usr/local/lib/codecs, usr/lib/win32, usr/local/lib/win32....) 

But mplayer dosen't seems to be able to file the codecs in those locations.:confused:

And I've also tried all the video settings recommended in all the guides that I can find in google. (eg, X11/Xv driver w/ FFmpeg's libavcodec codec family or w/ RealVideo decoder..)

So the question is, did mplayer in Gusty's respo. changed the location where it stores/finds codecs, or am I missing something?:-k

And for those who can successfully play rm files in 64bit Ubuntu, can you please kindly post your video settings for your mplayer for my reference.

Thanks in advance.

---

### Post by tarekeldeeb on 2007-11-02
same problem here ..:confused:

---

### Post by LavianoTS386 on 2007-11-02
I have the same issue on both totem and VLC, but I was able to use Mplayer following [this]("http://www.simplehelp.net/2007/07/27/how-to-play-rmvb-files-in-ubuntu/") method.

Still can't go full screen with them, but I'll take what I can get.

---

### Post by Modius on 2007-11-04
:lolflag:

That is exactly the same tutorial I found, and it didn't work for me.

Anyways, my problem was solved after adding repos from mediubuntu, and install w32/w64 codecs from there.....heck, I really donno how that differs from manually installing it myself.
But it works anyhow, and that's all I care about.

---

### Post by dingorunner on 2007-11-21
Well, if you read the REAME file inside essential-20071007, it says there's a new codec directory; follow these steps  [http://www.simplehelp.net/2007/07/27/how-to-play-rmvb-files-in-ubuntu/](http://www.simplehelp.net/2007/07/27/how-to-play-rmvb-files-in-ubuntu/)
but change 
cd Desktop
cd essential-date
sudo mkdir /usr/lib/win32
sudo cp * /usr/lib/win32
to
cd Desktop
cd essential-date
sudo mkdir /usr/lib/codecs
sudo cp * /usr/lib/codecs

 Worked for me!

---

### Post by dezany1 on 2007-11-25
thanks so much~!
i missed out the part where the codecs directory was changed.

---

### Post by dingorunner on 2007-11-25
So, It worked?
You should consider copying your codecs in this directory too: 
There's been a series of updates that have been causing problems with Mplayer. First It was the codecs directory thing, then I changed it and fixed it; then another uptade, this time xine-codecs (or something like that) and it caused problems again, I couldn't open ANY file from Mplayer but I could reproduce videos from TOTEM. I open a video file by a command in the console and it was asking for some codecs here: /usr/local/lib/codecs, so I copied esscential20071007 in that directory and fixed it again. I hope there will be no more updates like those.

---

### Post by ronron261 on 2007-12-23
> **LavianoTS386 said:**
> I have the same issue on both totem and VLC, but I was able to use Mplayer following [this]("http://www.simplehelp.net/2007/07/27/how-to-play-rmvb-files-in-ubuntu/") method.

Still can't go full screen with them, but I'll take what I can get.

I changed it first to  the video driver on X11 (XImage/Shm) and like you no full screen.
So I set it back to X11/Xv and got full screen back

greetings,
Ronald

---

### Post by wingnux on 2008-01-24
It used to work here but now it won't show the video, only audio on any player =/ To make matters worse, RealPlayer crashes when I try to open a rmvb file...

And yes, I've tried EVERYTHING above.

---

