---
title: "How to play mp3 files."
date: 2006-08-26
forum: x86 64-bit Users (Pre April '08)
---

### Post by Ausus on 2006-08-26
Hi All,

What is required to play MP3 files.
What files do I require to down load.

Regards

---

### Post by Greycloak on 2006-08-26
The easiest way is to install Automatix.  It will allow you to download a bunch of goodies for Ubuntu, including MP3 support, DVD playback, etc.

[http://www.ubuntuforums.org/showthread.php?t=177646](http://www.ubuntuforums.org/showthread.php?t=177646)

---

### Post by klytu on 2006-08-26
> **Ausus said:**
> Hi All,

What is required to play MP3 files.
What files do I require to down load.

Regards

The overview on [Restricted Formats]("https://help.ubuntu.com/community/RestrictedFormats") will give you good background to get you up and running with not just MP3s but also just about every other proprietary format.

The [Dapper Getting Started Guide]("http://ubuntuguide.org/wiki/Dapper#How_to_install_Multimedia_Codecs") has good step-by-step instructions. It is a terrific resource for other information as well.

Also see the link in my signature for a ton of general resources that you may find useful.

Hope this helps.

---

### Post by fistfullofroses on 2006-08-26
All you need to do is intall the media codecs

$ sudo -s
# apt-get install mpg123 mp32ogg gstreamer0.10-ffmpeg gstreamer0.10-gl gstreamer0.10-plugins-base gstreamer0.10-plugins-good gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse 

If you want a player that is better than that which comes with Gnome... I would recommend getting beep-media-player or XMMS.

---

### Post by Ausus on 2006-08-26
Hi fistfullofroses,

Tnx I followed your suggestions, it works.
I down-loaded beep-media-player, how do I get it in my menu.
I'm new with Linux.


Regards

---

### Post by cocteau on 2006-08-26
you can use synaptic to get the alacarte menu editor. That makes it pretty straight forward to modify you menues in gnome.

---

