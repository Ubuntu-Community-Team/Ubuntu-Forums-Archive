---
title: "Codecs"
date: 2005-03-24
forum: x86 64-bit Users (Pre April '08)
---

### Post by idn on 2005-03-24
will the windows 32bit codecs work under hoary? currently I don't have support for all the main multimedia formats such as mpeg, although I can play .wav :)

Thanks

---

### Post by s_p_a_r_k_y on 2005-03-25
They will work in  hoary, but not 64bit. You can try 32bit hoary, or create a CHROOT environment. [http://www.debian.org/releases/stable/i386/ch-preparing#s-linux-upgrade](http://www.debian.org/releases/stable/i386/ch-preparing#s-linux-upgrade)

Read that for a howto on getting a chroot going. I have it working with mplayer and xine, but its not ideal, but it works and lets me use 64bit applications with 32bit ones in the chroot.

---

### Post by Jad on 2005-03-25
[http://ubuntuguide.org/#codecs](http://ubuntuguide.org/#codecs)
sudo apt-get install gstreamer0.8-plugins
sudo apt-get install w32codecs

---

### Post by macavity on 2005-03-25
[QUOTE=idn]will the windows 32bit codecs work under hoary? currently I don't have support for all the main multimedia formats such as mpeg, although I can play .wav :)

Thanks[/QUOTE]

$ sudo apt-get install vlc (and all nessesery vlc-plugins such as alsa, esd and etc.)

---

### Post by macavity on 2005-03-25
[QUOTE=Jad][http://ubuntuguide.org/#codecs](http://ubuntuguide.org/#codecs)
sudo apt-get install gstreamer0.8-plugins
sudo apt-get install w32codecs[/QUOTE]

Jad, it doesn't work for hoary... I'm using vlc.

---

### Post by idn on 2005-03-25
Yeah i installed VLC, posted a thread praising it:) it pretty much does everything excpet wmv, crappy wind00bs.

---

### Post by songochain on 2005-03-27
I downloaded win32codecs from mplayer web and i installed it in the correct directory

---

### Post by bored2k on 2005-03-27
[QUOTE=macavity]Jad, it doesn't work for hoary... I'm using vlc.[/QUOTE]
 apt-get w32codecs worked for me under Hoary . VLC still owns MPlayer ^_^ , but w32codecs are great on hoary .

---

### Post by songochain on 2005-03-28
[QUOTE=bored2k]apt-get w32codecs worked for me under Hoary . VLC still owns MPlayer ^_^ , but w32codecs are great on hoary .[/QUOTE]
 hoary amd64 or i386?? i didnt find win32codecs doing apt-cache search either synaptic

---

