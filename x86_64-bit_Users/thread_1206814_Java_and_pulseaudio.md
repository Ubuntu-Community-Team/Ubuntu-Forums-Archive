---
title: "Java and pulseaudio"
date: 2009-07-07
forum: x86 64-bit Users
---

### Post by Thelasko on 2009-07-07
I installed 64-bit Java and the plugin from Sun's website a while ago.  However, it has just come to my attention that the audio output for Java is not going through pulseaudio.  Does anyone have any suggestions on how to fix this?  I'm running Hardy Heron.

Thanks

---

### Post by Thelasko on 2009-07-08
Java appears to be outputing sound with ALSA, but it's not being forwarded to pulseaudio.  I don't know why.

---

### Post by Yellow Pasque on 2009-07-09
Use padsp when opening a Java app?
[http://www.razorsedge.org/~mike/docs/asoundrc.html](http://www.razorsedge.org/~mike/docs/asoundrc.html)

FWIW, the IcedTea Java plugin has pulse output, but of course, it doesn't work with some web pages.

---

### Post by Thelasko on 2009-07-10
I think it was trying to access the device directly with the "Java Sound Audio Engine".  I've just figured out how to change the device in Java through the sound.properties file, but it still isn't being picked up by pulse audio.  My options are "plughw:0,0"; "Java Sound Audio Engine"; and "hw:0".

padsp doesn't do anything because Java isn't using oss.

---

