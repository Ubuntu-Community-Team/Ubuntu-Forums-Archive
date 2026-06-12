---
title: "Mp3 play"
date: 2007-08-26
forum: x86 64-bit Users (Pre April '08)
---

### Post by masoodkamal on 2007-08-26
hi

i tried to play a MP3 file and it prompted me to download codec. when i clicked it, it told me about Cstreamer codec, but a msg below sayng tht it cannot be installed on AMD64 machine.
Now wht i do :confused:

Plz help !

---

### Post by John.Michael.Kane on 2007-08-26
> **masoodkamal said:**
> hi

i tried to play a MP3 file and it prompted me to download codec. when i clicked it, it told me about Cstreamer codec, but a msg below sayng tht it cannot be installed on AMD64 machine.
Now wht i do :confused:

Plz help !

As far as Gstreamer based codecs are concerned they install fine under 64bit ubuntu. 

To install them run the following command.
```
gksudo aptitude install  gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse 

```
To install other codecs such as flash/java/dvd play back. Read the bottom of this sticky thread [Please Read First Advantages and Disadvantages of 64bit. (Plus install Guides)]("http://ubuntuforums.org/showthread.php?t=368607")

Also make sure you have all the repositories enabled.if you don't know how read the post below.
[ Enabling Extra Repositories]("http://www.psychocats.net/ubuntu/sources")

---

### Post by funrider on 2007-08-27
FYI, if you are looking for an winamp alternative, try xmms, it works well in FF 64 and it is in the repository. 

you can use winamp skin too!

---

