---
title: "How to play MP3 with xmms or totem"
date: 2005-04-21
forum: x86 64-bit Users (Pre April '08)
---

### Post by aurelien007 on 2005-04-21
Hi ! 
I've just install my new ubuntu but i can't play mp3 :( (be it with xmms or totem etc...)
My sound is working perfectly (gaim, ubuntu startup etc...)

However I can't do that :

sudo apt-get install gstreamer0.8-plugins
sudo apt-get install w32codecs

And when I try to uncomment those line :

#deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
#deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

i've got an error in synaptic :S  ](*,) 

please help  me !!!! :p

[sorry for my dirty english]

---

### Post by Fab on 2005-04-21
[www.ubuntuguide.org](www.ubuntuguide.org) -> extra repositories

---

### Post by FluffyElmo on 2005-04-21
Note that the w32 codecs are not available under a 64bit system. Many codecs are available for 64bit, but some (WM9) aren't. 

To just play mp3s in RythmBox install *gstreamer0.8-mad*, though that may be included in *gstreamer0.8-plugins*.

---

### Post by buddyankur on 2006-03-01
aurelien007 u r great buddy....THNX ALOT

 i was trying to play and install MP3 for last one weeek.. as iam new kid to UBUNTU:evil: ...so really dont know much about installing stuff...

but after reading wht u have asked ..everything is wrking fine...though i tried  few more steps..let me discuss them in case others might need them...

Before i go ahead... iam using AMD 64 bit processor..not sure about 32 bit processors.

1) Before typing these commands:

   sudo apt-get install gstreamer0.8-plugins
   sudo apt-get install w32codecs

2)try to update the apt-get by using :

  sudo apt-get update
   (for more help on apt-get use: apt-get -f)

 3) once apt-get is updated now try these commands:

   sudo apt-get install gstreamer0.8-plugins
   sudo apt-get install w32codecs

It worked for me... hope it works for you as well..GUD LUCK:D \\:D/ :)

---

