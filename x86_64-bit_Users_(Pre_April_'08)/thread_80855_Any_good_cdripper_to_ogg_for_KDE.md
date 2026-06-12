---
title: "Any good cdripper to ogg for KDE?"
date: 2005-10-23
forum: x86 64-bit Users (Pre April '08)
---

### Post by JuanC on 2005-10-23
Kubuntu / Ubuntu drop support to mp3 to increase popularity of the free ogg vorbis.

Why don't include a cdripper to ogg?

I would like to encode my cds in this format to listen in kubuntu.

Any good cdripper to ogg for KDE that has 64bits support?

---

### Post by JensKue on 2005-10-23
Grip - [http://nostatic.org/grip/](http://nostatic.org/grip/)
KAudioCreator - [http://www.icefox.net/programs/?program=KAudioCreator](http://www.icefox.net/programs/?program=KAudioCreator)

---

### Post by JuanC on 2005-10-24
[QUOTE=JensKue]KAudioCreator - [http://www.icefox.net/programs/?program=KAudioCreator](http://www.icefox.net/programs/?program=KAudioCreator)[/QUOTE]

I try it and i think is a good cd ripper , but i have a problem , How to choose the quality of the output ogg file?

The output ogg file is 112 kbps and i like at least 128 kbps.

---

### Post by Terracotta on 2005-10-24
I've been wondering 'bout that for a while, I don't think you can change it :s. I wonder about the ripper that's built in Konqueror, how can you change the bitrate there?

---

### Post by idn on 2005-10-24
Try goobox, its awesome, I use it all the time. It is in the repositories, it will be added as CD Player in the menu after you install it BTW, threw it off. 

It has cover art amoun other things. You can encode to various qualities, I always have mine on high.

Edit: 320 Kps for ogg - jsut checked :)

---

### Post by bbking on 2005-10-25
you can change the bitrate for ogg mp3 in Kaudicreator by adding 
the term

-b *bitrate*

to the command line options in settings > encoders >

-b 160 -m 128 -M 192 results in variable bit rate (vbr) within the given    specifications

---

### Post by getaceres on 2005-10-25
[QUOTE=JuanC]Kubuntu / Ubuntu drop support to mp3 to increase popularity of the free ogg vorbis.

Why don't include a cdripper to ogg?

I would like to encode my cds in this format to listen in kubuntu.

Any good cdripper to ogg for KDE that has 64bits support?[/QUOTE]
Kubuntu includes one. It's called audiocd:/.
Insert an Audio CD and type audiocd:/ in konqueror or select Audio-CD Browser from the sidebar.
You must see now some folders. Each one is named as the way it will be ripped. Just copy the desired folder to your hard disk and you have it ripped.
To configure the output quality, go to the audio CD subsection in the sound section of the KDE control center.

---

### Post by JuanC on 2005-10-25
[QUOTE=getaceres]Kubuntu includes one. It's called audiocd:/.
Insert an Audio CD and type audiocd:/ in konqueror or select Audio-CD Browser from the sidebar.
You must see now some folders. Each one is named as the way it will be ripped. Just copy the desired folder to your hard disk and you have it ripped.
To configure the output quality, go to the audio CD subsection in the sound section of the KDE control center.[/QUOTE]

That's easy !!! Thanks for your info.

[QUOTE=bbking]
you can change the bitrate for ogg mp3 in Kaudicreator by adding
the term

-b bitrate

to the command line options in settings > encoders >

-b 160 -m 128 -M 192 results in variable bit rate (vbr) within the given specifications[/QUOTE]

I will try it , thanks.

---

### Post by fistfullofroses on 2005-10-26
KAudioCreator can rip from CD to OGG, and it works fairly well too.
If that doesn't work, DL the Gnome libs and use soundjuicer

---

