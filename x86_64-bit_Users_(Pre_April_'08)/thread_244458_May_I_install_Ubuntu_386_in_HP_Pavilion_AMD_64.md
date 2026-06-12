---
title: "May I install Ubuntu 386 in HP Pavilion AMD 64"
date: 2006-08-26
forum: x86 64-bit Users (Pre April '08)
---

### Post by dmery on 2006-08-26
Hi,
I have one notebook HP Pavilion zv6015us AMD 64 - 3500. I want to know if I can install on this notebook a Ubuntu PCx386 :confused: . Because a lot  applications do not work properly with 64 bit-PC system.
Thanks for answering =D> 
regards,
dmery

---

### Post by jamesford on 2006-08-26
theres no prob running 32 bit linux on an amd64

u might want to install the k7 kernel once u got ubuntu installed

---

### Post by Kilz on 2006-08-26
> **dmery said:**
> Hi,
I have one notebook HP Pavilion zv6015us AMD 64 - 3500. I want to know if I can install on this notebook a Ubuntu PCx386 :confused: . Because a lot  applications do not work properly with 64 bit-PC system.
Thanks for answering =D> 
regards,
dmery

What programs do you think dont work properly?

---

### Post by dmery on 2006-08-26
I have some problems with "xine", I can not watch movies, I have problem to watch videos with RealPlayer10, problems to use wine, etc :frown: . I know that the solution is loading chroot, but I like that all my system works out the box, like my desktop AMD-Athlon =D> . I think was not good idea to buy one 64 bits laptop. 
Thank for answering
Regards,
dmery

---

### Post by Kilz on 2006-08-26
> **dmery said:**
> I have some problems with "xine", I can not watch movies, I have problem to watch videos with RealPlayer10, problems to use wine, etc :frown: . I know that the solution is loading chroot, but I like that all my system works out the box, like my desktop AMD-Athlon =D> . I think was not good idea to buy one 64 bits laptop. 
Thank for answering
Regards,
dmery

What type movies cant you watch with xine? what type of video's in real payer 10? You do unsderstand regardeless of the linux version proprietary formats require setup. Wine is avaiable to 64bit, a lot of people have used my howto to install it.
Looking at your posts history, this is your first thread in the 64bit section. why havent you asked questions here before?

---

### Post by dmery on 2006-08-26
Hi,
Thank for answering me,
Do you know where can I get libdvdcss2.deb for 64 bits, because this is reason that I can not use my xine to watch DVD movies. With RealPlay10 I can not watch videos from internet because the sound and the movie is "out of sync". I have the same problem in two laptops (HP Pavilion zv6015us) with different distro (Dapper and Gentoo, both 64 bits). Both programs -in my desktop AMD Athlon XP 32 bits- are working fine (with Dapper -my favourite- and Gentoo). I would appreciate if you know some information about this problem ;) . I am planning to move Gentoo 64 bits to Ubuntu (64 or 32) because I prefer Ubuntu than Gentoo for a lot of reasons. Gentoo spend a lot of time to compile programs when you update the system. I love Debian based Distros like Ubuntu.
thanks in advance
Regards,
dmery  :)

---

### Post by cocteau on 2006-08-26
libdvd is not a xine problem but a codec problem. You need to start synaptic, enable universe and multiverse repositories and install the libxine-extracodecs package. While you're at it, get the various gstreamer codec packages, then you'll be able to play most things (wma - wmv excluded).

There's a very good help page on ubuntu for doing these things here: [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

Good luck. And btw, I've got xine running beautifully, playing dvds and all :)

---

### Post by Kilz on 2006-08-26
> **dmery said:**
> Hi,
Thank for answering me,
Do you know where can I get libdvdcss2.deb for 64 bits, because this is reason that I can not use my xine to watch DVD movies. With RealPlay10 I can not watch videos from internet because the sound and the movie is "out of sync". I have the same problem in two laptops (HP Pavilion zv6015us) with different distro (Dapper and Gentoo, both 64 bits). Both programs -in my desktop AMD Athlon XP 32 bits- are working fine (with Dapper -my favourite- and Gentoo). I would appreciate if you know some information about this problem ;) . I am planning to move Gentoo 64 bits to Ubuntu (64 or 32) because I prefer Ubuntu than Gentoo for a lot of reasons. Gentoo spend a lot of time to compile programs when you update the system. I love Debian based Distros like Ubuntu.
thanks in advance
Regards,
dmery  :)

Video's from what site?

---

### Post by Lonthong on 2006-08-26
> **dmery said:**
> Hi,
Thank for answering me,
Do you know where can I get libdvdcss2.deb for 64 bits, because this is reason that I can not use my xine to watch DVD movies. With RealPlay10 I can not watch videos from internet because the sound and the movie is "out of sync". I have the same problem in two laptops (HP Pavilion zv6015us) with different distro (Dapper and Gentoo, both 64 bits). Both programs -in my desktop AMD Athlon XP 32 bits- are working fine (with Dapper -my favourite- and Gentoo). I would appreciate if you know some information about this problem ;) . I am planning to move Gentoo 64 bits to Ubuntu (64 or 32) because I prefer Ubuntu than Gentoo for a lot of reasons. Gentoo spend a lot of time to compile programs when you update the system. I love Debian based Distros like Ubuntu.
thanks in advance
Regards,
dmery  :)

apt-get install liba52-0.7.4-dev libdvdread3-dev libdvdnav-dev
That will solve the problem of libdvdcss2 complaint
sudo /usr/share/doc/libdvdread3/examples/install-css.sh (For DVD menu).
I think you must have these installed as well
debhelper, build-essential and fakeroot packages

---

### Post by Lonthong on 2006-08-27
> **Kilz said:**
> Video's from what site?

Kilz,
I followed yr how-to & managed to get everything working. 
But I can not get the video in [www.laptoplogic.com](www.laptoplogic.com) working

---

### Post by Kilz on 2006-08-27
> **Lonthong said:**
> Kilz,
I followed yr how-to & managed to get everything working. 
But I can not get the video in [www.laptoplogic.com](www.laptoplogic.com) working

Its flash. I have flash working on a number of sites but cant see the video on that one. This leads me to believe it may be flash 8 format. Flash 8 isnt avalable on linux.

---

### Post by dmery on 2006-08-29
> **Lonthong said:**
> apt-get install liba52-0.7.4-dev libdvdread3-dev libdvdnav-dev
That will solve the problem of libdvdcss2 complaint
sudo /usr/share/doc/libdvdread3/examples/install-css.sh (For DVD menu).
I think you must have these installed as well
debhelper, build-essential and fakeroot packages

Thanks all you guys,

I can see movies now with totem, (I moved two days ago one of two laptop from Gentoo to Ubuntu Dapper, :)). In the other laptop I have problem with sound when I am trying to watch a movie (but I think is another problem, I will try to fix it). When I try to see videos from internet [http://www.faithevansonline.com/video.asp](http://www.faithevansonline.com/video.asp) with Real Play (32 bits) I have problem with the sound (is muted). I will tomorrow install wine in both.
Thanks for your support, now I am seeing that I wasted my time try to configure Gentoo-laptop (Ubuntu forum is more supportive)  
Regards,
dmery:D

---

