---
title: "cpu overused during playback of flash videos on Mozilla, why?"
date: 2009-01-10
forum: x86 64-bit Users
---

### Post by clean60r on 2009-01-10
is there a way to utilize playback of flash videos more efficiently in Mozilla without overusing my CPU resources?

---

### Post by mikewhatever on 2009-01-11
Not really. Flash is a CPU intensive plugin, and as far as I know, there isn't much you can do other then upgrading the CPU. What's your CPU speed?

---

### Post by clean60r on 2009-01-18
thanks 4 da reply mikewhatever, am running on intel core 2 duo, 1.8 centrino. upgrading the cpu will mean replacing my lovely hp pavillion laptop :(

---

### Post by Yellow Pasque on 2009-01-19
Are you using the 32-bit Flash w/nspluginwrapper from the Ubuntu repo, or are you using the 64-bit Flash Alpha? (Use about:plugins in the URL bar or look in Synaptic to see if flashplugin-nonfree is installed if you're unsure).

---

### Post by cariboo on 2009-01-19
I'm using the 64bit Beta flash plugin, and watching a video on youtube, according to [top]("http://unixhelp.ed.ac.uk/CGI/man-cgi?top"), my cpu is running at about 13% usage. I run a AMD X2 3800 cpu.

You can get the 64bit beta [here]("http://labs.adobe.com/downloads/flashplayer10.html").

Jim

---

### Post by clean60r on 2009-01-20
yes i have the non-free flash plugin installed, am using 64-bit 8.10 ubuntu intrepid ibex.

---

### Post by clean60r on 2009-01-20
just try to load two separate youtube videos then watch your cpu meter, coz mine would shoot to 70-80% sometimes it would hit 100% and just stay there while the cpu fan goes full thrust.

---

### Post by cariboo on 2009-01-20
You should uninstall the Flashplugin-nonfree and use the 64bit version. Just download it, extract it. Create a plugins directory in ~/.mozilla and copy libflashplayer.so to ~/.mozilla/plugins. Playing 3 flash videos at the same time according to top I am using about 40% cpu and my fan speed is 2376 RPM.

Jim

---

### Post by waspbr on 2009-01-21
is there a way to install the beta plugins for other browsers like, say, opera for instance? I wanted to see if there was any performance improvements with another browser

---

### Post by clean60r on 2009-01-23
thanx cariboo907, i will try ur method then will post the results, i also tried it on opera it seems to handle flv's much better than mozilla and cpu clocks 30-50% even if i play 3 or more vids, unfortunately opera tends to freez when playing many clips at once.

---

