---
title: "64-bit transcoder?"
date: 2008-05-29
forum: x86 64-bit Users
---

### Post by Skeorx13 on 2008-05-29
Are there any good transcoders/encoders for ubuntu that utilize multicore processors? I've got a monster quadcore and need to transcode a massive amount of flac files to 320kbs mp3s to use with my ipod. I normally use CDex in XP but it is only 32-bit. (I realize by the time I get a response here I probably could have been finished transcoding in windows but I'd like to at least know for future reference) I need the program to be 64-bit, utilize multiple cores (preferably 4), copy all metadata from the flac to the mp3s, and keep the file names the same (except for the extension of course). I'd prefer it use a GUI but command line would be fine too.

---

### Post by Artemis3 on 2008-05-29
Heh, you are getting picky... I would use 4 terminals and use [a script like this](http://www.sklav.com/?q=node/4).

That script is already set for 320kbps. If you want to experiment lower bitrates, [read here](http://wiki.hydrogenaudio.org/index.php?title=LAME) and always stick to the recommendations.

You are of course using the lame package from the repositories, which is already 64bits. But lame is not multi-threaded, thats why i would use 4 of them in your quad core case ;)

Maybe there is a fancier gui to do the same.


If this for your **portable**, my personal recommendation is to use **-V5 --vbr-new** unless you plan to listen into a totally silent place with very high quality headphones. Any background noise or cheap earplugs and all that extra bitrate becomes waste.

If you do listen in totally **silent areas** with high quality headphones, then something like **-V2 --vbr-new** is pretty much indistinguishable from 320kbps. Do your own [abx tests](http://wiki.hydrogenaudio.org/index.php?title=ABX) tho.

---

### Post by Skeorx13 on 2008-05-30
I prefer to keep the bitrate as high as possible. I have good headphones for my ipod and on some songs I can actually tell a difference between the 256kbs VBR and full 320kbs. I started on lower bitrates when I was just getting into mp3s in highschool (many many moons ago). My computer only had one speaker so they were fine. My computer is now connected to a 7.1 stereo system, so yeah lower bitrates don't cut it. (I just use flac now for that. Well, for the albums I have store bought hard copies of, at least.)

I know lame isn't multicore yet. I read that the 64-bit version causes a few errors here and there though and I don't want any artifacts in my music. The slightest difference in sound from the original and my brain tend to go wonky. (think nails on chalkboard)

---

