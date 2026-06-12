---
title: "[SOLVED] video DVD's no longer work"
date: 2008-07-29
forum: x86 64-bit Users
---

### Post by dystorteddream on 2008-07-29
Well I've got everything up and running with my new system. I've got codec's downloaded and everything. DVD's used to work... and now VLC, Mplayer and Totem do not play any DVD's. It'll prompt and even auto start... but now it won't play with any player, saying "Could not read from resource." I have two DVD drives and they both work in Vista, but it's not reading from my 64 bit machine. any ideas?


D~D

---

### Post by ModelM on 2008-07-29
If these are commercial DVD movies, you'll need libdvdcss in order to decode the encryption so you can play them.

Here's a link to a DEB package for it. Just download it to your desktop, then double-click it to install...

[http://download.videolan.org/pub/libdvdcss/1.2.9/deb/libdvdcss2_1.2.9-1_i386.deb](http://download.videolan.org/pub/libdvdcss/1.2.9/deb/libdvdcss2_1.2.9-1_i386.deb)

---

### Post by dystorteddream on 2008-07-29
> **ModelM said:**
> If these are commercial DVD movies, you'll need libdvdcss in order to decode the encryption so you can play them.

Here's a link to a DEB package for it. Just download it to your desktop, then double-click it to install...

[http://download.videolan.org/pub/libdvdcss/1.2.9/deb/libdvdcss2_1.2.9-1_i386.deb](http://download.videolan.org/pub/libdvdcss/1.2.9/deb/libdvdcss2_1.2.9-1_i386.deb)
I'm getting an error message, since I'm using the x86-64 bit kernel. "Error: Wrong architecture 'i386'

---

### Post by ModelM on 2008-07-29
Here's the project homepage. I don't know if they have any pre-compiled pkgs for 64 bit. You may have to build it yourself...

[http://freshmeat.net/projects/libdvdcss/](http://freshmeat.net/projects/libdvdcss/)

---

### Post by ajgreeny on 2008-07-29
Not sure about the 64bit version but 32bit is available in medibuntu repos.  See [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu) for more info.

---

### Post by xen-uno on 2008-07-29
libdvdcss2 x64 is available from Synaptic Package Manager from the Medibuntu repository ... but you have to add the site to System>Administration>Software Sources. I also have libdvdnav4 & libdvdread3 installed. "Could not read from resource" is definitely a copywrited DVD error, fixable with css2. Why it died on you I have no clue.

---

### Post by stchman on 2008-07-30
> **dystorteddream said:**
> Well I've got everything up and running with my new system. I've got codec's downloaded and everything. DVD's used to work... and now VLC, Mplayer and Totem do not play any DVD's. It'll prompt and even auto start... but now it won't play with any player, saying "Could not read from resource." I have two DVD drives and they both work in Vista, but it's not reading from my 64 bit machine. any ideas?


D~D

Follow my tutorials.

Install CODECs
[http://www.stchman.com/codecs.html](http://www.stchman.com/codecs.html)

Install Medibuntu for libdvdcss2
[http://www.stchman.com/dvd_rip.html](http://www.stchman.com/dvd_rip.html)

---

### Post by dystorteddream on 2008-08-01
> **stchman said:**
> Follow my tutorials.

Install CODECs
[http://www.stchman.com/codecs.html](http://www.stchman.com/codecs.html)

Install Medibuntu for libdvdcss2
[http://www.stchman.com/dvd_rip.html](http://www.stchman.com/dvd_rip.html)
Again, sir, you do rock, even if you are a blues/cardinals fan. That worked perfectly!

---

### Post by Funk Phenomena on 2008-08-04
For me, this has been a rather frustrating endeavor with Ubuntu 64.  I tried both flavors on the Ubuntu Guide and with the first, the movie goes directly to playing and trying to fast forward makes it hang.  Trying the alternate method for menus had the dvd start fine, allowed selection of scenes and such, but when it went to play it claimed it needed libdvdcss.  Ultimately I just said eff it with the desktop as I have an upconverting dvd player for the tv, and chose the simple 'play only' option for the laptop.  

I suppose I'll flail along some other time until I get it right, so just consider this whining (or solace if you're in the same boat).

---

### Post by soxs on 2008-08-04
> **ajgreeny said:**
> Not sure about the 64bit version but 32bit is available in medibuntu repos.  See [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu) for more info.

there are 64 bit debs

---

### Post by smCw6GNakQn300£ on 2008-09-23
> **stchman said:**
> Follow my tutorials.

Install CODECs
[http://www.stchman.com/codecs.html](http://www.stchman.com/codecs.html)

Install Medibuntu for libdvdcss2
[http://www.stchman.com/dvd_rip.html](http://www.stchman.com/dvd_rip.html)

Outstanding - it all works for me now!

Thanks!

---

