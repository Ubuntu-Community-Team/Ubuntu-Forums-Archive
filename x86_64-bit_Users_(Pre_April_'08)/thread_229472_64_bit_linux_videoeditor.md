---
title: "64 bit linux videoeditor"
date: 2006-08-04
forum: x86 64-bit Users (Pre April '08)
---

### Post by Tithis on 2006-08-04
I've wanted to install Ubuntu 64 for awhile now. The main reason was to finaly use the 64bit capabilities of my processor. I also do alot of videoediting and converting and heard that its faster to do when using a 64bit operating system. 

Well I just got a new harddrive(60gb) to slave on my computer and install Ubuntu-64 on. So I was wondering if anyone knew of a good compatible videoediting software.

Also I would like a guess on how much using a 64 bit system could improve my conversion rates. Normaly in windows I do on average 40-50fps.

---

### Post by LinuxConvertJune2006 on 2006-08-04
I've used Kino on 32bit Ubuntu and have installed it but not yet tested on 64bit Dapper. It works great:[URL="https://help.ubuntu.com/ubuntu/desktopguide/C/video.html"]
https://help.ubuntu.com/ubuntu/desktopguide/C/video.html[/URL]

---

### Post by juicemansam on 2006-08-05
You might want to try [Cinelerra](http://www.heroinewarrior.com/). They have a 64-bit version, which is supposed to (at least users have said) be many times better than the 32-bit version. I'm currently experimenting with it, but I can't seem to resize a video. I'm not sure, but there should be a deb'd version in one of the repositories, so you don't break things with installing an alien'd version. Just a warning, your mileage will vary greatly.

---

### Post by darkshadow on 2006-08-05
I use kino for dv footage and avidemux for everything else like quick converting types and linear editing to cut out stuff like commercials.

And for your performance question you should see somewhere around a 30% increase.

---

### Post by aouie on 2007-06-28
I haven't found any significant speed changed using the 64-bit version of cinelerra. It still seems equally slow on an Athlon 64 3000+ with 1GB RAM when applying some blur effects and rendering to mpeg2 by piping to ffmpeg. But, it does work in 64-bit mode too.

Adding some information onto this thread for those who stumble upon it.

As has been pointed out in other places, the AMD64 packages for edgy listed at the [Cinelerra CV site]("http://cvs.cinelerra.org") works in feisty too.
Sincerely,
Aouie

---

