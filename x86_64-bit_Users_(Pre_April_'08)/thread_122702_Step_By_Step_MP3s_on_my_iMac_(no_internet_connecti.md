---
title: "Step By Step MP3s on my iMac? (no internet connection)"
date: 2006-01-28
forum: x86 64-bit Users (Pre April '08)
---

### Post by shubox357 on 2006-01-28
I installed ubuntu 5.10 and want to play mp3s but the iMac is not set up to use the internet. what can i do so that i can play MP3s? thanks!

---

### Post by navilon on 2006-01-28
you will have to download the lame codec package elsewhere and install it using dpkg

---

### Post by shubox357 on 2006-01-28
where do i get the codecs and how do i use dpkg? thanks


BTW has anyone actually done it? I always get links and stuff but has anyone done it with no internet connection?

---

### Post by tufkakf on 2006-01-29
I think it depends on what program you want to use to play mp3s.
If you want to use rhythmbox (the default music player for ubuntu) you need gstreamer0.8-mad I think.

The best way to install it would probably be to download it and it's dependencies from packages.ubuntu.com:
[http://packages.ubuntu.com/breezy/libs/gstreamer0.8-mad](http://packages.ubuntu.com/breezy/libs/gstreamer0.8-mad)

Then you can install it from a terminal with sudo dpkg -i packageyouwanttoinstall.deb

Hope this helps.

---

### Post by hentaidan on 2006-01-29
[QUOTE=shubox357]BTW has anyone actually done it? I always get links and stuff but has anyone done it with no internet connection?[/QUOTE]

Yes, I do it all the time with my laptop. As long as you download all the dependencies as well, you should have no problems.

---

### Post by shubox357 on 2006-01-29
**hentaidan:** what are all the dependencies and where can i find them? do you htink you could explain exactly what you did? thanks

**tufkakf:** thanks, im trying it now...

---

### Post by shubox357 on 2006-01-29
nevermind i got it..

---

### Post by shubox357 on 2006-01-29
ok i burned it to a cd (gstreamer-mad) then copied it to my desktop and did the sudo dpkg -i on it and a bunch of errors came up. what am i doing wrong? its a fresh install so i haevnt enabled anyhting else yet. what do i do? please give me simple steps, im not a linux guru that knows everything. step by step would be best; ie: go to the site, download this program. type this in, oyu get the idea

---

### Post by tufkakf on 2006-01-29
[QUOTE=shubox357]ok i burned it to a cd (gstreamer-mad) then copied it to my desktop and did the sudo dpkg -i on it and a bunch of errors came up. what am i doing wrong? its a fresh install so i haevnt enabled anyhting else yet. what do i do? please give me simple steps, im not a linux guru that knows everything. step by step would be best; ie: go to the site, download this program. type this in, oyu get the idea[/QUOTE]
You probably need some dependencies.

Look at the page I linked to, the dependencies for gstreamer0.8-mad are listed there. Download them and install them with dpkg -i (I'm just guessing, but you probably need at least libmad0 and libid3tag0). If all installs fine, run sudo apt-get -f install, this should make sure everything is installed correctly.

---

### Post by Leang on 2006-02-04
I'm very new to Ubuntu and Linux in general, but I did get mp3 playback to work. My suggestion would be to just setup internet connection with Ubuntu and download all the features you want, and disconnect it after. If you want just mp3 playback, it shouldn't take more then 10 minutes or so depending on your internet connection. I think mine took a little over 5 minutes. Here's what I did.
 
1. Open Ubuntu help.
2. Click Ubuntu 5.10 Starter Guide.
3. On the left side panel, click the little arrow next to Applications to expand it.
4. Click Music and Movies.
5. Step one will show you how to update your Synaptic to show Universe and Multiverse.
6. Step two lists the packages that will come in handy. Since you only want mp3 playback, I assume you don't need the Graphics packages. I don't even know if you need the Libraries packages but it wouldn't hurt to install them.
7. Follow step three to finish up. When you double click an mp3 it should playback fine now.

---

### Post by Laxflip on 2006-02-08
thansk for the help now rhythm box is bumping my tunes.. now soon as someone codes the new creative x-fi platinum card i can start getting AWESOME sound:KS \\:D/ :mrgreen:

---

