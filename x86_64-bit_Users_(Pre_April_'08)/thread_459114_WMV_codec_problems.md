---
title: "WMV codec problems"
date: 2007-05-30
forum: x86 64-bit Users (Pre April '08)
---

### Post by blazini on 2007-05-30
I couldn't get much help in the multimedia forum, so I'm reposting this here

I'm having problems with some wmv files. Some play fine, some play choppy as if they are partially corrupted (which they are not, they still play fine on a windows machine), and some don't play video at all. I have the codec pack from Automatix installed, I tried installing other codecs or packs but can't seem to get any of them working. The last tutorial I came across on this forum for wmv9 worked until the last step, but I got an error that said the package wasn't for AMD64. Does anyone know of a surefire way of getting all WMV files working on AMD 64?

---

### Post by ronocdh on 2007-05-30
> **blazini said:**
> I couldn't get much help in the multimedia forum, so I'm reposting this here

I'm having problems with some wmv files. Some play fine, some play choppy as if they are partially corrupted (which they are not, they still play fine on a windows machine), and some don't play video at all. I have the codec pack from Automatix installed, I tried installing other codecs or packs but can't seem to get any of them working. The last tutorial I came across on this forum for wmv9 worked until the last step, but I got an error that said the package wasn't for AMD64. Does anyone know of a surefire way of getting all WMV files working on AMD 64?
How are you trying to play them? I use VLC and it's a beast, I love it. I don't use Automatix personally, but if you search in Synaptic, you'll find other codecs. I had to get the MPlayer one and its Mozilla plugin in order to stream WMVs online. Hope this helps.

---

### Post by blazini on 2007-05-30
the problem isn't the player, I'm missing a wmv codec. I have VLC, Mplayer, Totem and Kaffeine installed, none of them play certain WMV files. I can't even convert them to something else cuz I don't have the original codec. I seem to remember trying to open the file with Avidemux and getting a WMV3 error.

---

### Post by Tanker Bob on 2007-05-30
Add the codecs in medibuntu.  You can find the appropriate instruction [here](http://ubuntuforums.org/showthread.php?t=457263&highlight=medibuntu+repositories).  You'll find the 64-bit codecs in that repository.

---

### Post by blazini on 2007-05-30
> **Tanker Bob said:**
> Add the codecs in medibuntu.  You can find the appropriate instruction [here](http://ubuntuforums.org/showthread.php?t=457263&highlight=medibuntu+repositories).  You'll find the 64-bit codecs in that repository.

What package am I looking for exactly in synaptic? I added the Medibuntu source as you pointed out. The best thing I could find is a package called "w64" which didn't do the trick

---

### Post by Cappy on 2007-05-31
Right click on a video and change to the "Audio/Video" tab.
Post back the information from the "Codec" section of **Video** and **Audio** for videos that work, videos that skip, and videos that don't work.
Hopefully, there is a clue in there.

Also, try this:
Open one of your skipping videos in Mplayer. Goto the Mplayer settings and click on the "driver" tab. Try using the X11 driver and if that doesn't make the video smoother try the "gl" driver. You might want to try them all. That fixed my own skipping video problems.

---

### Post by Tanker Bob on 2007-05-31
w64codecs is the package you want.  Player engine should be set to xine or mplayer.

---

### Post by cisforcojo on 2007-06-01
Here's a script I got from someone on the forums to automatically update a fresh feisty install with codecs.

Just pick and choose what you want. This should definitely solve your wmv problems.

---

### Post by blazini on 2007-06-01
Ok, here's where I am so far.......

I used that script that was posted, seemed to go OK but I got this error after the "refresh repositories" step......
W: GPG error: [http://ubuntu.geole.info](http://ubuntu.geole.info) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY BC40ED2499419355
I've got this error before, not sure if it affected the script or not. I'm a noob so I have no Idea what this means. The script didn't help the 2 videos that don't play.

The default kaffiene engine is set to kaffiene-xine

Most WMV9 files play perfect other than a few. Most of the choppy ones are WMV8. The 2 files that don't  play at all are a a sequence of the same clip, when I tried right clicking the file to get the audio/video tab and the browser  window stops responding. These files play fine on my modded xbox, not sure what type of codecs that uses. I think those files are WMP3 cuz of the error I get when I try to open them with AVIdemux, any idea where to get that codec?

---

