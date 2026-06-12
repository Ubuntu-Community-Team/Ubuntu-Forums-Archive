---
title: "Rythymbox and other audio apps dont work"
date: 2005-11-24
forum: x86 64-bit Users (Pre April '08)
---

### Post by shubox357 on 2005-11-24
every time i put in a cd and try to play a song off of it the cd player or rythym box doesnt work it says somehting about "gst register" and asks if I have run it or not. what can I do so I can listen to music?

---

### Post by shubox357 on 2005-11-25
anyone?

---

### Post by mortram on 2005-11-25
in the terminal, try running gst-register-0.8, if you have installed any new codecs recently.

as far as i know, rhythmbox doesn't play audio-cds -- that's done by the Gnome cd-player

Applications > Sound & Video > CD Player

---

### Post by shubox357 on 2005-11-25
well i loaded songs fromt eh cd onto my desktop and tried to play them in rythym box and that didnt work. noen of my audio apps worked. i just installed from a shipit cd i got a few days ago. its my first try at linux and i want to be able to listen to music. what could be wrong? how can i "run" soemthing in terminal, do i type this "sudo gst-register-0.8" or what?

---

### Post by shubox357 on 2005-11-25
actually i have it figured out now...

linux.....eh its free, the least i can do is THINK

---

### Post by shubox357 on 2005-11-25
i can play audio cds on my mac now, but i sitll cant play any MP3s because i haevnt installed any decoders??? what the hell? what am i supposed to do now?

---

### Post by Brian McConnell on 2005-11-25
[QUOTE=shubox357]i can play audio cds on my mac now, but i sitll cant play any MP3s because i haevnt installed any decoders??? what the hell? what am i supposed to do now?[/QUOTE]
[http://userlinux.net/pub/stuff/ubuntu/](http://userlinux.net/pub/stuff/ubuntu/)
that's for the last version of Ubuntu (Hoary), I assume you have the current version of Ubuntu, which is called Breezy. Most of the info in that link is still relevant, however I do not know of one updated for Breezy.
Read a lot, don't be afraid to try and have fun doing it. Play around with your new system a bit and I'm sure you'll find loads more of questions :D

quick hint, change the occurence of the word "hoary" to "breezy" when copying the apt-get sources.list information from that page to your own file. you'll see what I mean after you read. You'll get your mp3, flac, ogg or whatever groove on quick enough!

---

### Post by ssam on 2005-11-26
also have a look at
[https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)

or in future use the open/free [ogg]("http://www.vorbis.com/") format for music.

---

### Post by xslf on 2005-12-03
So the buttom line is- no MP3 on Ubuntu ppc? Or am I missing something?

---

### Post by ssam on 2005-12-03
[https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats) might help you with installing codecs

---

### Post by xslf on 2005-12-03
[QUOTE=ssam][https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats) might help you with installing codecs[/QUOTE]

I asked my question after reading that page, since it says that many of these codecs (like w32codecs) won't work for PPC.
So my question still stands- are there codecs available for **Ubuntu PPC** that allow playing of mp3 files?

---

### Post by ssam on 2005-12-03
have a search for gstreamer in synaptic.
gstreamer0.8-ffmpeg or gstreamer0.8-mad look like they have mp3 codecs.

or have a look at [https://wiki.ubuntu.com/RestrictedFormats#head-3be93401c382d54ab39c29d84538612d874817c0](https://wiki.ubuntu.com/RestrictedFormats#head-3be93401c382d54ab39c29d84538612d874817c0)

---

### Post by xslf on 2005-12-04
That worked- thanks!

---

### Post by shubox357 on 2005-12-14
im not online though, and cant be with my mac, how can i get the repositories i need then?

---

### Post by shubox357 on 2005-12-16
anyone?

---

