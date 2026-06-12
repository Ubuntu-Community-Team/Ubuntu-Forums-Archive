---
title: "Software for ubuntu x86-64"
date: 2004-12-04
forum: x86 64-bit Users (Pre April '08)
---

### Post by frankps on 2004-12-04
Hi all,

this is my first post.

To the ubuntu developers, thank you for making a great linux distro for average joe. Before choosing my linux distro, I tested out suse, fedora and ubuntu. 

I went to Guadec in Kristiansand, Norway this summer, and was quite impressed of Dashboard. Recently I read about Beagle on OSNEWS, clicked on the links and saw that there was a wiki for a linux distro that I had seen in the news frequently the last months. 

A new computer was just ordered (AMD64), and at work I downloaded Fedora and Ubuntu. Tried Ubuntu first, deleted it, cause I had always used Redhat and Fedora as my 3rd OS before. Installed Fedora Core 3. It felt like walking on glue on a brand new computer. Where was the speed? Bought Suse 9.2, and for the first time I managed to loose the whole content of my harddisk. That has never happened before, and had to figure out a way to fix the MBR. I had my backups, but I can't say more then that I was quite so disappointed.

To make it short, the Ubuntu installation is back on my system. I am staying with this distro. It turned out to be a great one!

Could somebody help me with getting Beagle installed on my system? The wiki seems to be wrong or not applying for x86-64 systems. I have read this small article: [http://www.ubuntulinux.org/wiki/BeagleInstallHowto/view?searchterm=beagle](http://www.ubuntulinux.org/wiki/BeagleInstallHowto/view?searchterm=beagle)

I am playing with Linux at home, and fast found out that I was missing some software and codecs. I don't like the music players in the distro and I truely miss the mpeg3 codec. All my CDs are ripped to mp3 under windows. 

What music players can I download and install for ubuntu without having to compile them and end up in the "dependency hell"?

Could someone list me all the apt servers where I can download software for my system?

Thank you all in advance...

---

### Post by Suzan on 2004-12-04
If you want install software very easy, try synaptic!To find a lot of software, you have to [enable the universe-sources](http://www.ubuntulinux.org/support/documentation/howto/helpcenterhowto.2004-09-30.5359349801).

For MP3-Files i recommend "XMMS", for nearly every kind of videos "MPlayer". Use the K6-version for your AMD. For that K6-Mplayer you have to add that to your sources.lst:

deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) testing main 

If you have an error with MPlayer concerning ALSA, simply change the audio preferences to "OSS".

Have a lot of fun!

---

### Post by frankps on 2004-12-04
Hi Suzan,

Thank you for your answer.

I just started using the Synaptic Package Manager 5 minutes before checking for answers on my questions.

Regarding XMMS, I was more looking for something like Jamboree - [http://imendio.com/projects/jamboree/](http://imendio.com/projects/jamboree/)

I also liked the screenshots from Blam - 
[http://imendio.com/projects/blam/](http://imendio.com/projects/blam/)

I am using a similar applications on my Mac.

---

### Post by Suzan on 2004-12-04
Have you tried "Rythmbox"?

---

### Post by frankps on 2004-12-04
Yes, I have.

It has crashed every single time.


Frank

---

### Post by leech on 2004-12-10
I only had it crash after doing a re-install, and then not having all the plugins installed.

So try doing a 'apt-get install gstreamer0.8-plugins' and hopefully it'll fix the crashing.  It fixed mine.

Leech

---

### Post by frankps on 2004-12-16
Will try as soon as I get home.


Frank

---

### Post by Gnobody on 2004-12-18
You can't use the [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) mirror on AMD64, it only has i386 packages.  I wish they had AMD64 packages.

---

### Post by Ribs on 2004-12-19
[QUOTE=Gnobody]You can't use the [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) mirror on AMD64, it only has i386 packages.  I wish they had AMD64 packages.[/QUOTE]
i386 packages can be installed if you force them. see the dpkg output for help in doing so, I can't remember the exact command off the top of my head.

i386 packages should work in most cases. They just won't be optimised.

-Ribs.

---

### Post by frankps on 2004-12-20
I have gotten most of the Mono applications working on my laptop: F-spot, Muine and Tomboy. I love them, and I am looking forward to see what future versions will bring.

I have decided to run the x86-64 as stable and I install as little as possible on it for now, and at least not x86-32 software on it.

---

