---
title: "Definitive Guide to compile latest ffmpeg+lame(+3gp) - Can somebody help?"
date: 2007-09-18
forum: x86 64-bit Users (Pre April '08)
---

### Post by isync on 2007-09-18
Hi there,

I found these posts:
[http://po-ru.com/diary/fixing-ffmpeg-on-ubuntu/](http://po-ru.com/diary/fixing-ffmpeg-on-ubuntu/)
[http://www.howtoforge.com/video_streaming_lighttpd_flowplayer](http://www.howtoforge.com/video_streaming_lighttpd_flowplayer)

but still (not knowing enough about compiling) I am not able to pull everything together and compile a fresh and *complete* version of ffmpeg with lame (and optional 3gp, divx, x264 support) under Dapper 6.06 on AMD64.

Which repositories should I have enabled. Is it possible to compile the 32 bit version as ffmpeg32 to get a really up-to-date binary running. (like here: [http://ubuntuforums.org/showthread.php?t=191205](http://ubuntuforums.org/showthread.php?t=191205))

So far:
> apt-get install build-essential
cd /tmp
wget [http://mesh.dl.sourceforge.net/sourceforge/lame/lame-3.97.tar.gz](http://mesh.dl.sourceforge.net/sourceforge/lame/lame-3.97.tar.gz)
tar xvfz lame-3.97.tar.gz
cd lame-3.97
./configure --enable-shared --prefix=/usr
make
make install
apt-get install ffmpeg libavcodec0d libavformat0d libavifile-0.7c2 libpostproc0d libasound2-plugins avifile-player avifile-utils avifile-mad-plugin avifile-mjpeg-plugin avifile-vorbis-plugin 
ended with "libavcodec0d could not be found". What dos that mean?

> sudo apt-get build-dep ffmpeg
ended with "Could not open /var/lib/apt/lists/packages.freecontrib.org_ubuntu_plf_dists_dapper_free_source_Sources - open (2 No such file or directory)"

---

### Post by stmiller on 2007-09-18
Hey make sure you have medibuntu added:

[http://medibuntu.sos-sts.com/repository.php](http://medibuntu.sos-sts.com/repository.php)

---

