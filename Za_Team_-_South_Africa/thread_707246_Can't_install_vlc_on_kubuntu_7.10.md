---
title: "Can't install vlc on kubuntu 7.10"
date: 2008-02-25
forum: Za Team - South Africa
---

### Post by LDrenzo on 2008-02-25
Hi guyz am totaly new to linux and i installed kubuntu days ago so am having trouble installing vlc on it. The software is a .tar.gz archieve and .deb. The gzipped vlc give an error message when i try to configure it and the .deb vlc say some libray dependency is not  satistiyable. Ive tried to explain as best as could.
Any help will be appriciated guyz, thankz.

---

### Post by deepclutch on 2008-02-25
heard vlcplayer is now on available with qt .y dont ya try source? ;)

---

### Post by erginemr on 2008-02-25
> **LDrenzo said:**
> Hi guyz am totaly new to linux and i installed kubuntu days ago so am having trouble installing vlc on it. The software is a .tar.gz archieve and .deb. The gzipped vlc give an error message when i try to configure it and the .deb vlc say some libray dependency is not  satistiyable. Ive tried to explain as best as could.
Any help will be appriciated guyz, thankz.

Probably the Debian installer you have downloaded does not comply with your system libraries, or your version of Ubuntu. I suggest you to install "vlc" directly from the repositories:
```
sudo aptitude install vlc
```
which will handle dependencies, too.

---

### Post by Circus-Killer on 2008-02-26
> **LDrenzo said:**
> Hi guyz am totaly new to linux and i installed kubuntu days ago so am having trouble installing vlc on it. The software is a .tar.gz archieve and .deb. The gzipped vlc give an error message when i try to configure it and the .deb vlc say some libray dependency is not  satistiyable. Ive tried to explain as best as could.
Any help will be appriciated guyz, thankz.

okay, just to try clear things up. when you install through the repositories, any other programs that vlc may depend on and require will be automagically installed. however, when you install from a .deb directly, it is unable to automatically get the dependencies. so you would have to install each of the depencies on your own.

having said that, i would suggest you take erginemr's advice. and in future, always check to see if the program you want is in the repos.

---

### Post by LDrenzo on 2008-03-03
hi guyz

Thankz so much your help. I was a little busy with my studies so couldn't give u feed back. I don't have internet connection on my pc so I get an error saying "can't create executable". So i think the best solution is to download the 1 by 1 nad see how that works. If there is any alternative way of doing this please let me know, I will be very happy if there is. Again thanks in advance

---

### Post by erginemr on 2008-03-03
When I issue:
```
sudo aptitude install vlc
```
I get the feedback that the following packages are also to be installed as a dependency:
```
The following NEW packages will be installed:
  libdvbpsi4 libdvdnav4 libebml0 libiso9660-4 libmatroska0 libtar 
  libvcdinfo0 libvlc0 libxosd2 vlc vlc-nox 
```

But I am using Gnome and you are using KDE, so you may need a few more packages to satisfy the dependencies. Nevertheless, this list will be a good start.

You can visit this site:
[http://packages.ubuntu.com/gutsy/vlc](http://packages.ubuntu.com/gutsy/vlc)

and download the above packages, and of course "vlc" itself, elsewhere to a pen drive, take them to your pc and install them all with:
```
cd <the folder where those debian packages are stored>
sudo dpkg -i *.deb
```

---

### Post by LDrenzo on 2008-03-05
Hi again guy.
Thankz for that advice Erginemr am gonna try it out and see what it brings out. I wonder thou if u or any one of knows of another link that I can down download vlc dependencies in .deb format because the packages that saw at [http://packages.ubuntu.com/gutsy/vlc](http://packages.ubuntu.com/gutsy/vlc) are .gz. Every time I try to configure samething I get the Error: compiler can't craete executables. 

Thanks again guyz:):)

---

### Post by erginemr on 2008-03-05
Are you sure? When I click on one of the packages and proceed, I reach a debian package...

---

### Post by LDrenzo on 2008-03-06
Hi guyz

Thanks a million tyms 4 those snapshots Erginemr your a life saver. Am done downloading them and am gona put them on a disc and go try them out. U will defintely here from me tommorrow to give you feed back ayt.:):):):):)

---

### Post by LDrenzo on 2008-03-07
Hi guyz 

:):):)

I successful installed vlc on my pc last nyt with no probs. Now i can play music and movies. Just 1 tiny problem thou, the movies don't show any pics its just music, sounds and voices. I don't know if its codes problem or if absense of drivers for my graphic card  or something. If any one knows a way arround this one can he please what me what to do so I can be able to see pics when am watching a movie. Any suggestion will be greatly appreciated.

Thanks in advance agin guyz

---

### Post by erginemr on 2008-03-07
Kudos for having successfully installed VLC. :D Now, the following will be kind of blind shots as I do not use vlc myself, but these sure will enable to view movies of many formats in Totem (and possibly in vlc). Here we go:

1) The Medibuntu repository holds a few valuable packages, "w32codecs" for Windows media codecs and "libdvdcss2" for playing DVD movies. For a general review:
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

1a. You can download w32codecs Debian package from:
[http://packages.medibuntu.org/pool/non-free/w/w32codecs/](http://packages.medibuntu.org/pool/non-free/w/w32codecs/)

1b. And libdvdcss2 from:
[http://packages.medibuntu.org/pool/free/libd/libdvdcss/](http://packages.medibuntu.org/pool/free/libd/libdvdcss/)

In both directories, you should look for the i386 (i.e. for 32 bit PC) Debian package with the latest version.

2) Also download the following packages from the Ubuntu repository:

2a. Package name: libdvdread3 (for DVD playback again)
[http://packages.ubuntu.com/gutsy/libdvdread3](http://packages.ubuntu.com/gutsy/libdvdread3)

2b. Package name: libdvdnav4 (for DVD movie navigation menu)
[http://packages.ubuntu.com/gutsy/libdvdnav4](http://packages.ubuntu.com/gutsy/libdvdnav4)

2c. Package name: gstreamer0.10-plugins-ugly (a few other codecs)
[http://packages.ubuntu.com/gutsy/gstreamer0.10-plugins-ugly](http://packages.ubuntu.com/gutsy/gstreamer0.10-plugins-ugly)

2d. Package name: ffmpeg (for DivX support)
[http://packages.ubuntu.com/gutsy/ffmpeg](http://packages.ubuntu.com/gutsy/ffmpeg)
(You should download other files on the same page too, to be used in case ffmpeg needs some of them and they are not installed in your system.)

2e. Package name: gstreamer0.10-ffmpeg (companion to ffmpeg)
[http://packages.ubuntu.com/gutsy/gstreamer0.10-ffmpeg](http://packages.ubuntu.com/gutsy/gstreamer0.10-ffmpeg)

There may be a few redundant packages, yet this pretty much should do it. ;)

---

