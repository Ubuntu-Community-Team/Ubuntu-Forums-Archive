---
title: "Flash, Firefox, and 64-Bit Fun!"
date: 2008-09-12
forum: x86 64-bit Users
---

### Post by jdorenbush on 2008-09-12
I am running Flash 3x on my AMD64. I am running into problems with Flash. At least the Flash on the only website I goto that has Flash - Pandora.com

Its extremely slow and sometimes completely unresponsive. I have high speed Internet, so it can't be a slow connection.

I am not sure if the problem lies within Flash, Firefox, or 64bit, or all of them combined.

---

### Post by Sef on 2008-09-13
1) How did you install Flash?

2) Does this problem exists with any other websites? If not, then I suspect the problem lies with the coding for that site.

---

### Post by jdorenbush on 2008-09-13
> **Sef said:**
> 1) How did you install Flash?

I installed it when the plugin notification within Firefox came up. I went to Pandora.com, it said I didn't have the appropriate plugin. So I followed the prompts to install it.

> **Sef said:**
> 2) Does this problem exists with any other websites? If not, then I suspect the problem lies with the coding for that site.

Heck, I don't really know what other sites to test it in. Like I said, Pandora works great on XP and Vista.

---

### Post by jdorenbush on 2008-09-20
Bump

---

### Post by WiFi Ed on 2008-09-21
I haven't used Pandora for awhile but your post triggered my curiosity. Pandora behaves in a similar manner for me too. When I first load the site and log-in it works ok, but trying to load a different "station" just seems to "hang".

I'm running Hardy 64bit, and installed flash using Synaptic. Flash seems to work ok on most other sites.

---

### Post by steveneddy on 2008-09-21
Weird little radio station.

I just run streamtuner and play it with audacious.

---

### Post by jdorenbush on 2008-09-21
> **WiFi Ed said:**
> I haven't used Pandora for awhile but your post triggered my curiosity. Pandora behaves in a similar manner for me too. When I first load the site and log-in it works ok, but trying to load a different "station" just seems to "hang".

I'm running Hardy 64bit, and installed flash using Synaptic. Flash seems to work ok on most other sites.

Hmm. Interesting. I wonder if I should report it to Pandora??

---

### Post by Sef on 2008-09-21
> I haven't used Pandora for awhile but your post triggered my curiosity. Pandora behaves in a similar manner for me too. When I first load the site and log-in it works ok, but trying to load a different "station" just seems to "hang".


I wonder if it uses Live Connect - part of java, but not yet in OpenJDK.   I have one site that it goes to and keeps loading and loading.  There is a bug report for this.  For more information on Java for 64-bit, click [here]("http://ubuntuforums.org/showthread.php?t=774956").

---

### Post by ju2wheels on 2008-09-21
I highly doubt its the website. Flash (10 on my Intrepid 64bit) is extremely unstable. Sometimes I have to reload a flash video two or three times to watch it because it crashes so much. The issue seems to be a return of the Flash/PulseAudio issue, which for some reason seems worse than on my Hardy install on my laptop.

On my laptop I was able to set everything to point to ALSA and it worked fine with multiple concurrent audio streams, but thats not the case for Intrepid A6.

Either way, pandora.com did work fine for me without hanging up so I doubt its a Flash problem or it would have definitely crashed considering the track record already.

---

### Post by tuxxy on 2008-09-21
That pandora site loads fine for me using flashplugin and JDK, Flash and ALSA working fine here on AMD64 Intrepid :)

---

### Post by nss0000 on 2008-09-21
JDB:

Just checked out PANDORA. Worked fine, FLASH & all. I'm running x64HH and AMD5400+ with generic 16-bit soundcard.

---

