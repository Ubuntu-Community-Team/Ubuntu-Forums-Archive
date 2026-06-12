---
title: "Low Sound Issue"
date: 2009-06-16
forum: x86 64-bit Users
---

### Post by AquaFusion on 2009-06-16
Hello, this is my first time user of Ubuntu going from Window to Mac to Ubuntu, what i can say about it, im very quite impressed with it. anyway get back to the point. I been having problem with low sound in my Ubuntu 8.10. I changed to HDA Intel ALC888 Analog (OSS) since it the only one that working. i tired ALSA one but it didnt work. I test the sound in Sound Preferences and i can hear the sound just fine with my headphone, but when i play music video with Totem Player or VLC, the sound is so so so low, i only can hear the beat of the music. i did crank up the volume and still the same result, this video already tested in my Window Vista laptop and it sound normal. any help with this?

---

### Post by pixel :-) on 2009-06-16
right click on the applet
and Open volume control
probably PCM is too low, if not play with the various options

---

### Post by AquaFusion on 2009-06-16
I am using shuttle box case. So i use the front plug for listening my sound through headphone. i found out it using ALSA, is there a way to change the ALSA to OSS Mixer? OSS Analog seem only works with my sound, not the rest. Is there a way to disable PulseAudio? i read that PulseAudio is the main reason it cause problem with sound.

And i did try few options, the back of the case still have extrememly low sound even PCM is full up. and i want my front of the case plug to work if that is possible

---

### Post by pixel :-) on 2009-06-17
try in this forum

[http://ubuntuforums.org/forumdisplay.php?f=334](http://ubuntuforums.org/forumdisplay.php?f=334)

---

### Post by AquaFusion on 2009-06-17
seem it sloved, i got more sound now. all i need to do is to [php]sudo apt-get install alsa-oss[/php] and it works, i seem to got more sound out of my ubuntu. thanks

---

