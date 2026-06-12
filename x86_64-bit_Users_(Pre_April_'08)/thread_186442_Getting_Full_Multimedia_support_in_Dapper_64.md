---
title: "Getting Full Multimedia support in Dapper 64"
date: 2006-06-01
forum: x86 64-bit Users (Pre April '08)
---

### Post by Third Thoughts on 2006-06-01
Hey all,
I've got a friend who I've convinced to try out Dapper Drake on her laptop that I helped her buy. The computer hasn't arrived yet, but I'm trying to prepare for when it does so I can help her have a smooth install. Its a AMD Turion 64, so obviously I'd like to be able to install the 64 bit version of Dapper, but I'm pretty sure this girl is going to need full multimedia support including WMV3/Windows Video 9/VC-1 stuff. From what I understand its pretty easy to get everything but that. I'm pretty tech savy so I'm willing to jump for some hoops for this, but since its not my computer and I'll be doing it on her time I don't want to take my  usual approach of tweaking around until I figure something out. Is there anyone who can point me towards a relatively clear guide of how to get what I want so I don't have to spend alot of time messing around on her computer?

---

### Post by miggl on 2006-06-02
**dito**
Looking for the same thing. :)

---

### Post by RAOF on 2006-06-02
Short answer: you **can't** get WMV3/Windows Video9/VC-1 working in Ubuntu64.  Use the 32bit version.

Long answer: Ok, you **really** want to mess around :).  You've got a couple of options:
1) make a 32bit chroot, and install your media stuff (mplayer, etc) in there.  Simplest.
2) The sourcecode for a VC-1 decoder was released about a year ago;  There's a brief howto on [Jon's blog]("http://nanocrew.net/2005/09/01/compiling-vlc/") about building VLC with VC-1/etc support.  Harder.
3) You could hook up this decoder into FFmpeg (from memory of ffmpeg-devel, someone had done this in the past), and build a GStreamer-ffmpeg with these ffmpeg sources, thus giving you seamless WMV3 support in all gstreamer apps.  Hardest ;)

---

### Post by nalmeth on 2006-06-02
There is a howto somewhere in the forums (for hoary I believe! long time ago) for creating a 32-bit chroot environment, including showing how to symlink the commands so that it run's seamlessly along the regular 64-bit install.

I haven't tested it for dapper, but for breezy it worked great. I just had to replace every instance of 'hoary' with 'breezy'. *Every instance*. I missed a couple of them and screwed somethings up, so if you try this, just keep a keen eye.

I have a 64-bit processor, but still run the 32-bit version on my PC, and I'm happy with the performance. Is it hyperthreading / dual-core? If so you can grab the right kernel to increase performance. Personally, to save time and effort I would go with the generic 386 version. She may end up crying for XP after all the effort.

Also, make sure that installing another OS doesn't void the warranty, some manufacturer's use this loop-hole to kindly screw-over their customer's.

---

### Post by Caseyjp on 2006-06-02
Just a quick thought here.  I'm running a dual core amd 64 (3800) system, and originally slapped 64bit dapper on.  So many issues with application support (still really wet behind the ears imho) that I moved back to 32bit version.

Tell ya what, no more application issues whatsoever, AND from a purely 'eyeball' performance perspective, I canna' tell the difference.  

Until the 64bit side is more mature on the application/general purpose side, that's purely a testing environment for me.  32bit is still screaming fast and best, compatible.

Also, a friend of mine is running the 32bit version on a similar laptop to the OP's query, and its screams.  He's now a new linux convert after years of waffling.

Personally to get the multimedia stuff going I'd recommend bumps, as that script is quick and installs the codecs needed as well as the dvd stuff.

---

### Post by Enderend on 2006-06-02
Do you have a link to bumps script?

---

### Post by Kilz on 2006-06-02
[QUOTE=Enderend]Do you have a link to bumps script?[/QUOTE]

[http://www.ubuntuforums.org/showthread.php?t=181248](http://www.ubuntuforums.org/showthread.php?t=181248) is the link to the Bumps thread. But like all automatic multimedia scripts it will not work on 64 bit ubuntu. The reason is that the codecs are 32 bit, your media players are 64 bit and cant use the 32 bit codecs.

---

