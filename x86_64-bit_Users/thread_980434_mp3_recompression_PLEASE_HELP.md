---
title: "mp3 recompression PLEASE HELP"
date: 2008-11-12
forum: x86 64-bit Users
---

### Post by ssk2006s on 2008-11-12
My 8gb nano video iPod used to be able to store 3k+ songs with xp/itunes, with ubuntu/rhythmbox(or amarok) I can only fit around 1k-1.5k songs.  I am assuming this is because of the compression methods used (or not used) on transferred mp3s.  I am hoping there is some way to reduce the file size of my mp3s to compensate for this.  What program/command could I use for this?

Thanks in advance

---

### Post by logos34 on 2008-11-12
yeah, it must be the bitrate difference (what else could it be?)

or do you mean you're merely trying to copy the same tracks you ripped in windows/itunes to the ipod using ubuntu/rhythmbox/amarok app?

---

### Post by ssk2006s on 2008-11-12
You understood it the first time.  Anyway, is there a program I could use to reduce the mp3's size?

---

### Post by Rhubarb on 2008-11-12
Try a nice program called **soundconverter**
```
sudo aptitude install soundconverter
```
Then you'll find it in Applications --> Sound & Video --> Sound Converter
Once opened you'll need to go into Edit --> Preferences
Then you'll need to tell it to use a low(er) bitrate mp3 by default.

It's a nice easy app to use once it's set up.

---

### Post by wallord_j on 2008-11-12
Sometimes I wonder if it is worth having a huge index of mp3's if they all are in a low bit rate format. For most songs 192k is as low as I can go and still enjoy the music.

---

### Post by BunTai on 2008-11-12
thanks..finally i found it!

---

### Post by logos34 on 2008-11-12
> **wallord_j said:**
> Sometimes I wonder if it is worth having a huge index of mp3's if they all are in a low bit rate format. For most songs 192k is as low as I can go and still enjoy the music.

+1

size (# tracks) isn't everything.  Quality is.  You have to read the small print of mp3 player ads to see they base capacity on 128K bitrate.  But most people know this by now and are encoding at the Hydrogenaudio recommended standard of (lame) v2 vbr

---

### Post by Npl on 2008-11-13
If you are using an ipod you could aswell use the .mp4 format which a bit more efficient than mp3 (on average). Means you could have smaller filesize while keeping the same quality.

In any case, dont recompress from mp3 to anything else, quality will suffer alot. If possible, encode fresh from CD or other lossless source

---

### Post by xen-uno on 2008-11-13
^^^ ... I disagree. A high quality (alt pre std minimum) mp3 or ~ 192 avg bitrate ogg or mpc will transcode very well to other lossy formats. You could even ABX between the source lossy and the transcode and be hard pressed to hear a difference. I would always x-code off the CD/wav/flac first but if you don't have the lossless, lossy to lossy produces good results.

---

