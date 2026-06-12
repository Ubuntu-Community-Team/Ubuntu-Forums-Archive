---
title: "Runescape"
date: 2008-03-01
forum: x86 64-bit Users (Pre April '08)
---

### Post by bloodhound23 on 2008-03-01
I am bored and want to play runescape. But I am unable to play it, I just get a grey box. What do I need to do to play it?

---

### Post by Omnios on 2008-03-01
Runescape uses Java.

 I used automatix to install it.

---

### Post by kaginken on 2008-03-01
Hogwash.  Automatix is a bad idea which is why ubuntu doesn't support it.

I play runescape all the time (check me out, cajunken lvl 98 )

Just:

[HTML]sudo apt-get install sun-java6-plugin[/HTML]

Hope that works for you!

Rock on!  :guitar:

---

### Post by kaginken on 2008-03-01
While we're at it, take a look at a snippet of a shell script I've created to run first thing after installing ubuntu.  It adds all the stuff a body needs:

```
sudo apt-get install vlc
sudo aptitude install gstreamer0.10-ffmpeg gstreamer0.10-gl gstreamer0.10-plugins-base gstreamer0.10-plugins-good gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse libxine-extracodecs w32codecs
sudo apt-get install -y msttcorefonts
sudo apt-get install mozilla-mplayer
sudo apt-get -y install unrar
sudo apt-get install smbfs smbclient
sudo aptitude install libdvdcss2
sudo apt-get install brasero
sudo apt-get install sun-java6-plugin
sudo apt-get install checkgmail
sudo apt-get update
sudo aptitude install mplayer
sudo apt-get install -y flashplugin-nonfree
sudo apt-get install gftp
sudo apt-get install vim
```

---

### Post by bloodhound23 on 2008-03-02
THere is no sun-java6-plugin for i386.

---

### Post by bloodhound23 on 2008-03-02
edit for x86-64, there is only a sun-java6-plugin for i386

---

### Post by bloodhound23 on 2008-03-02
bump

---

### Post by Superkoop on 2008-03-02
Install the 32bit Firefox, follow this[ howto]("http://ubuntuforums.org/showthread.php?p=1174435")

---

