---
title: "[SOLVED] Flash 10 64bit alpha"
date: 2008-11-27
forum: x86 64-bit Users
---

### Post by WiFi Ed on 2008-11-27
I decided to try the 64bit Flash alpha release today. I've been using the 32bit version installed from Synaptic with pretty good success but I haven't broken my Ibex installation in a while so I thought I'd take a chance.

First, I uninstalled the flashplugin-nonfree package (complete removal option), then downloaded the 64bit package from Adobe here:
[http://labs.adobe.com/downloads/flashplayer10.html]("http://labs.adobe.com/downloads/flashplayer10.html")

I extracted it to the Desktop and copied the libflashplayer.so file to:
/usr/lib/firefox-3.0.4/plugins/

I restarted Firefox and tried some websites with Flash content (CNN, Speedtest.net, etc.) and it works (so far).:)

---

### Post by damvcoool on 2008-11-27
I have used the same since it came out a few days ago, and so far there is nothing to complain about. in the contrary it actually seems more stable, and fast. i am now able to open multiple Youtube, Dailymotion, and Veoh videos, plus Flash games at the same time, i could not do that before. it would crash npviewer, and no flash until i killed the process and restart FF.

now we should only way for Sun Java Plugin in 64 bit, Iced Tea is good but not good enough.

---

### Post by Cracauer on 2008-11-27
Do they have flexible audio interfaces by now?

Or still ALSA only?

---

### Post by felker2 on 2008-11-27
> **wifi ed said:**
> i haven't broken my ibex installation in a while so i thought i'd take a chance.



lol!

---

### Post by philinux on 2008-11-27
I copied mine to

~/.mozilla/plugins

Had to create the plugins folder first.

Seems to be working fine on Jaunty 64 bit. Java next eh.

---

### Post by WiFi Ed on 2008-11-27
> **philinux said:**
> I copied mine to

~/.mozilla/plugins

Had to create the plugins folder first.

Seems to be working fine on Jaunty 64 bit. Java next eh.

I "thought" I tried that location first, but it didn't work. After reading your post, I revisited it and it seems I made a folder called "plugin", not "plugins". I just now renamed it, removed flash from the other location and all is well..:)

---

### Post by WiFi Ed on 2008-11-27
> **Cracauer said:**
> Do they have flexible audio interfaces by now?

Or still ALSA only?

I don't know. How would I check that?

---

