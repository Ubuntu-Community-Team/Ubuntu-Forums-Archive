---
title: "DVD play back."
date: 2008-11-04
forum: x86 64-bit Users
---

### Post by Lex-Man on 2008-11-04
How do I play DVD in ubuntu?

I've installed VLC but they don't seem to want to play.

---

### Post by cariboo on 2008-11-04
You also need libdvdcss2, this is an illegal codec in some parts of the world, so you will have to enable the medibuntu repositories. To do that go here:

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

Use at your own discretion

Jim

---

### Post by Lex-Man on 2008-11-04
> **cariboo907 said:**
> You also need libdvdcss2, this is an illegal codec in some parts of the world, so you will have to enable the medibuntu repositories. To do that go here:

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

Use at your own discretion

Jim

Now I can play the first 10 seconds, with movie player, of a DVD and then it cuts out.  I get an error saying it can't read the stream, and with VLC it just flicks between a large size and small size until I pause.

---

### Post by Lex-Man on 2008-11-04
> **Lex-Man said:**
> Now I can play the first 10 seconds, with movie player, of a DVD and then it cuts out.  I get an error saying it can't read the stream, and with VLC it just flicks between a large size and small size until I pause.

Scratch that its working now.

---

### Post by Lex-Man on 2008-11-06
Ok, I can play full DVD's but the playback it jerky.

I have an ATI card which may be the problem.

I also installed ubuntu-restricted-extras from the Synamptic package manager which I think un installed some other things.

---

### Post by Th3Professor on 2008-11-16
I had the couple-seconds of play then no play, only now with a fresh install (new computer) I get the top/main menu but nothing else when clicking on 'play'.

The "guide" (a sticky in this forum) does not work in its current state, I went through each step within it. No luck getting DVDs to play.



I did get an error message.

---

### Post by John.Michael.Kane on 2008-11-16
> **Th3Professor said:**
> I had the couple-seconds of play then no play, only now with a fresh install (new computer) I get the top/main menu but nothing else when clicking on 'play'.

The "guide" (a sticky in this forum) does not work in its current state, I went through each step within it. No luck getting DVDs to play.



I did get an error message.

What exactly is not working for you?

Using the same guide, I unfortunately am unable to duplicate whatever issues you are having.

I first installed the proper repositories, and codecs on 8.10.

Testing totem, I simply replaced totem-gstreamer with totem-xine using synaptic.

For vlc all that is required is to install it, as for mplayer it might require a some set-up, however it is minor.

I have included screen-shots of vlc, mplayer, and totem-xine.

Now, I am not saying you are not having problems. I just cannot reproduce any errors that you may have encountered.

---

### Post by Th3Professor on 2008-11-16
sudo wget [http://www.medibuntu.org/sources.list.d/intrepid.list](http://www.medibuntu.org/sources.list.d/intrepid.list) -O /etc/apt/sources.list.d/medibuntu.list
wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O - | sudo apt-key add - && sudo apt-get update
sudo aptitude install libavifile-0.7c2 gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-ffmpeg x264 libdvdcss2
sudo aptitude install w64codecs
sudo aptitude install totem-xine libxine1-ffmpeg
When I put in the DVD to play, it auto-plays the initial video (prior to main/top menu) and moves on to the main/top menu. I click on the menu to play, it starts to play though is interrupted with the following:

"An error occurred: Failed to connect stream: OK"

---

### Post by John.Michael.Kane on 2008-11-16
> **Th3Professor said:**
> sudo wget [http://www.medibuntu.org/sources.list.d/intrepid.list](http://www.medibuntu.org/sources.list.d/intrepid.list) -O /etc/apt/sources.list.d/medibuntu.list
wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O - | sudo apt-key add - && sudo apt-get update
sudo aptitude install libavifile-0.7c2 gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-ffmpeg x264 libdvdcss2
sudo aptitude install w64codecs
sudo aptitude install totem-xine libxine1-ffmpeg
When I put in the DVD to play, it auto-plays the initial video (prior to main/top menu) and moves on to the main/top menu. I click on the menu to play, it starts to play though is interrupted with the following:

"An error occurred: Failed to connect stream: OK"

Make sure totem-gstreamer is removed. After which you should be able to play the dvd with totem-xine.

To remove totem-gstreamer.
```
sudo apt-get remove totem-gstreamer
```

---

### Post by hnesk on 2008-12-08
For me it helped to switch from pulseaudio to alsa.
"System" -> "Preferences" -> "Audio"

---

### Post by motoperpetuo on 2008-12-20
switching to alsamixer fixed the problem i was having with the "failed to connect to stream" error.

now the only thing i can't do is use the slider bar labeled "time" in totem to fast-forward. if i try, totem just kicks me back to the point in the movie where i left off. anyone know how to fix this?

---

