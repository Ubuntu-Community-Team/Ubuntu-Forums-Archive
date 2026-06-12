---
title: "DVD playback problems..."
date: 2005-05-08
forum: x86 64-bit Users (Pre April '08)
---

### Post by Joey French on 2005-05-08
My system configuration is as follows:
ABIT NF8 Mobo
2* 512 Memory
Athlon 64 2800+
Sony DVD-r/w drive
Maxtor 20 G HD
KDE 3.4.0
Ubuntu 2.6.10.5-amd64-k8
Generic video card, 

I have enabled DMA.
I have tried to install all plugins necessary for multimedia; Gstreamer, xine,etc...
I have the restricted formats "howto" taken care of.
I have the extra repositories.
I have been unable to add some codecs, such as the windows64, etc. I guess that there are not for the linux peeps to retrofit.

When I open a DVD, i have the best luck with Kaffeine player. I guess I should say, it doesn't crash instantly. I have tried xine, mplayer, totem, anything I could find. Upon openig the disc, I can get it to play audio, smoothly. Also, I can actually select areas on the black screen to move to other areas on the dvd, where the menu should be. I can even take a screenshot, and the scene from the dvd that is playing at the time will appear! What I cannot do, however, is get the video to play on screen. I have a black screen with great sound. Then, when I exit Kaffeine, I get a crash notice, with no "debugging output".

Help!

Anyone got a clue? Is it my crap video card? It is the last item I am going to upgrade. I have used the "pgpgears" thing to test it, and it is pretty slow. Just as an example, it looks kinda bad running Supertux!

Thanks a bunch!
Joey

---

### Post by Joey French on 2005-05-08
Anyone?

---

### Post by bigbangbigbigbang on 2005-05-08
Try instaling mplayer from Marillat (the version in ubuntu is broken) along with win32codecs, libdvdcss2, ffmpeg etc.
If you choose the version from Marillat you will need some packages from debian unstable also, in order to satisfy dependencies.

Otherwise you can get mplayer from ubuntu backports also, I think this should work fine, I have not tried it though.

You can also try vlc, it is a decent dvdplayer too.

---

### Post by Joey French on 2005-05-08
So, then it is probably not my Oh-So-Crappy video card, then?

---

### Post by Professor X on 2005-05-08
Have you tried playing video files (.wmv,.mov,.mpeg) using kaffeine?  Try playing different DVDs and see if there are any changes.  It's probably not your video card.  I'm using a $15 nvidia card and have had no problems with DVD playback.

Good luck.

---

### Post by gazzie on 2005-05-09
I'm also using AMD64 platform and having DVD issues, though they seem to be a little different.

[http://www.ubuntuforums.org/showthread.php?t=32565](http://www.ubuntuforums.org/showthread.php?t=32565)

---

### Post by Joey French on 2005-05-09
No, I cannot playback most of these files, simply because I have been unable to acquire or install the necessary codecs. Is this due to the 65 bit architecture? Has anyone else been able to use the codecs necessary -on a 64 bit system- without the chroot/ debootstrap fix?

---

### Post by gazzie on 2005-05-09
I am able to playback xvid/divx etc without problems in VLC. I haven't tried it in mplayer.

---

### Post by floogy on 2005-05-09
[QUOTE=Joey French]windows64[/QUOTE]
What's that? Is that the 64bit replacement for the win32codecs at marillat? Where can I find these window64 codecs?

regards

floogy

---

### Post by c_dog on 2005-05-09
[QUOTE=floogy]What's that? Is that the 64bit replacement for the win32codecs at marillat? Where can I find these window64 codecs?

regards

floogy[/QUOTE]
They don't exist yet. XP 64 uses a 32-bit version of Windows MediaPlayer w/ the old 32 -bit codecs.

---

### Post by FluffyElmo on 2005-05-09
Joey, try changing the Video Driver setting in your media player. It's likely set to auto, try trial and error to see if any of the available options will work. In my case xv works best while some options cause instant player crashes and some work but won't scale the video to full screen.

In Kaffeine you can change the driver under Settings->xine Engine Parameters->Video

Codec wise, on my 64bit machine I have Totem-xine and MPlayer installed and can play pretty much anything except WMV10. I also installed ffmpeg and various other encoding tools which may have something to do with it...but the codec situation isn't as bad as it was a few months ago.

---

### Post by rsw on 2005-05-09
Kaffeine is the only thing which will play DVD's for me on amd64. At least it plays them :) Thanks for mentioning it, I had never heard of it having not been much of a kde user...

to get it working I did (as root, though I suppose you could use 'sudo' for each of these):

apt-get install fakeroot

/usr/share/doc/libdvdread3/examples/install-css.sh     
 * (make sure you have the packages it says it needs, use: dpkg -l | grep nameofpackageitwants   ..to see if you have it)

apt-get install ffmpeg kaffeine


I have universe & multiverse in my sources.list, but no other 'weird' repos. hopefully this points someone else in the right direction, but it probably won't :)




UPDATE.... for totem to play dvd's:

1. apt-get install fakeroot
2. /usr/share/doc/libdvdread3/examples/install-css.sh
3. apt-get install libxine1 totem-xine

should work.

---

### Post by Joey French on 2005-05-09
Cool, guys. Thanks! I will have to give these a try, and I will report back in a bit!

---

### Post by Joey French on 2005-05-09
I have been able to use my DVD player for the first time, and I fixed it by changing the driver in Kaffeine player. I tried to install ffmpeg, but it sent back errors having to do with my repositories. No matter. I can watch movies now, hehe...

Thanks, guys!

---

