---
title: "An patch for wmv native support on PPC, amd64 or any PC run linux."
date: 2006-03-06
forum: x86 64-bit Users (Pre April '08)
---

### Post by Tsai Dung-Bang on 2006-03-06
As far as everyone know, wmv is a very evil codec, and in the present, people use binary codecs from x86 windows, and use Win32 DLL loader to load the codcs from x86 PC. Hence we could not use the codcs on PPC or AMD64.

Now, a patch for VLC could be find on [Instructions for compiling VLC with VC-1 (WMV9) support under Ubuntu Breezy]("http://www.nanocrew.net/2005/09/01/compiling-vlc/")

and a patch for mplayer have been down by jserv.
[An native wmv patch for mplayer]("http://blog.linux.org.tw/~jserv/archives/001545.html")

The following are step by step.

```
apt-get build-dep mplayer
```

```
apt-get source mplayer
```

Download the attachment patch file or the following link.
(I will remove it in one day.)
```
wget http://www.phys.ncku.edu.tw/~c2491665/mplayer-wmv3.diff.gz
```

Due to the path in the patch, we need to change the dir of source, this depond
on which ubuntu you use. In the last dapper, you may like to follow me.

```
mv mplayer-0.99+1.0pre7try2+cvs20060117 mplayer

```

```
zcat mplayer-wmv3.diff.gz | patch -p0
```

```
cd mplayer
dpkg-buildpackage

```

After a long time, you will get deb file, just type 
```

cd ..
dpkg -i *.deb

```

And everthing is down, enjoy your wmv moves and forget the evil windows dll codecs.

By Dung-Bang Tsai

---

### Post by killerfish on 2006-03-25
Has anyone tried this?  Does it work?  I'm about to do a fresh Dapper Flight 5 install and am debating between 64 and 32 bit installs.  I'm cool with the Flash/Java issues of 64 bit, but am interested in having WMV 9 working.  

Until I saw this, I thought it impossible!

---

### Post by derloc on 2006-05-01
Uhm.. dosent seem to work on here (Dapper, AMD64).
My first try was just do "mplayer wmv9-file.wmv", then mplayer told me
"...  Cannot find codec matching selected -vo and video format 0x33564D57. ..." with sound but without video.
Then I figured out the name of added wmv codec: "mplayer -vc help | grep wmv" .. this gave me " ffwmv3      ffmpeg    crashing  FFmpeg M$ WMV3/WMV9  [wmv3]" and I tried:
"mplayer -vc ffwmv3 wmv9-file.wmv" with result:

Forced video codec: ffwmv3
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Cannot find codec 'wmv3' in libavcodec...
VDecoder init failed :(

Any idea?

edit:
Forget in, I just installed the wrong .deb (the mplayer-amd64 .deb didnt have any content, the pure mplayer .deb worked).
Wohoo, WMV9 on amd64!

---

### Post by Tsai Dung-Bang on 2006-05-01
It should work very perfect. 

In my system, amd64, powerpc and arm system all work.

But I do not know why few people are interested in it.

After I postd the patch, I waitd a long time until someone reply this.

---

### Post by derloc on 2006-05-02
[QUOTE=Tsai Dung-BangBut] I do not know why few people are interested in it.[/QUOTE]
Yes, strange. Well, I was just lucky to find this.

Another question. What about the license? I took a look at the libvc1 files but I didnt get really clear about it. Is it a "use, but not change"-kind license?

---

### Post by pvz on 2006-05-03
This worked nicely, thanks. Finally we can watch those danged wmv-files on our PPC's :-) Most files I tried worked well, but some had choppy sound. I can put a .deb up if there is any need/interest for it, but the build instructions work well, all you need is some time to compile it depending on your CPU-power..

---

### Post by samoht on 2006-06-01
Great, this works! Thank you!

Binaries for Dapper (amd64): 
[http://karmann-paf.de/ubuntu/mplayer_amd64/](http://karmann-paf.de/ubuntu/mplayer_amd64/)

---

### Post by Lempa on 2006-06-03
Hey thanks it worked great, except i don't have a gui for mplayer now, atleast i don't know how to start it. how can i fix this?

---

### Post by samoht on 2006-06-03
@Lempa: You can start mplayer-gui with "gmplayer".
There should be a shortcut in the menu though...

---

### Post by Soup4Brains on 2006-06-07
This guide seems to be helping everyone, but I'm not quite sure I understand what to do. This is probably due in part to the new Dapper release since this thread was written.

It seems most webpages are using WMV9 and I can't view it. Help!

---

### Post by michux on 2006-06-20
[QUOTE=Soup4Brains]This guide seems to be helping everyone, but I'm not quite sure I understand what to do. This is probably due in part to the new Dapper release since this thread was written.

It seems most webpages are using WMV9 and I can't view it. Help![/QUOTE]

In order to watch it on a webpage you probably need mplayerplug-in for Firefox as well.

---

### Post by janfsd on 2006-06-21
thanks for this, it worked great, even in the latest svn... now no need to chroot mplayer

---

### Post by jkwarras on 2006-07-01
wow, that works. Thanks! :)

---

### Post by bastupungen on 2006-07-07
This worked for me too! YAY!!! Im using an Ibook G4 with Kubuntu 6.06 dapper drake

It did not work at first because, i too, installed the wrong package. when i did "sudo dpkg -i *.deb" it fails to install mplayer (mplayer_0.99+1.0pre7try2+cvs20060117-0ubuntu8_powerpc.deb)

first i got really irritated (i had not eaten properly =D) that nothing worked. but I did everything once again and tried to install mplayer_0.99+1.0pre7try2+cvs20060117-0ubuntu8_powerpc.deb after i did dpkg -i *.deb and that worked!

It might be good to say that in the guide that if you get an error that mplayer did not install you have to do that manually. (with "sudo dpkg -i mplayer_0.99+1.0pre7try2+cvs20060117-0ubuntu8_powerpc.deb" depending on cvs version of source of course)

Anyways! Thanks

---

### Post by bastupungen on 2006-07-07
hmm... i cant really get internet streaming to work. If i try to open a stream through firefox i get the mplayer-plugin screen up and i get sound but to video. I can get it to work, video and sound but no gui, if i start the stream through the console (mplayer [http://whatever.wmv](http://whatever.wmv))

So there is no real problem with the codecs, as far as i can understand.

Anyone know why this is?

---

### Post by bluppfisk on 2006-07-10
I get these errors in the very beginning already. What's wrong?
> 
sandr@loki:~/videolan/vlc-trunk$ sudo apt-get build-dep mplayer
Reading package lists... Done
Building dependency tree... Done
E: Unable to find a source package for mplayer

sandr@loki:~/videolan/vlc-trunk$ apt-get source mplayer
Reading package lists... Done
Building dependency tree... Done
E: Unable to find a source package for mplayer


---

### Post by bastupungen on 2006-07-12
You propobly dont have your lists from where you download the packages from right.

There is an really nice webpage that does this automaticly, i use that one and it works for me. Right now i can't find the webpage but if you check around in the forums it should be there. Or you can update the /etc/apt/sources.list yourself. Though you probobly already know all this =)

---

### Post by maleficent on 2006-07-16
And here's one for xine (make sure you've already got build-essential, dpkg-dev and fakeroot installed):

sudo apt-get build-dep libxine-extracodecs
apt-get source libxine-extracodecs
cd xine-extracodecs-1.1.1+ubuntu1
zcat ../libxine-extracodecs-1.1.1-wmv9.patch.gz | patch -p1
dpkg-buildpackage -rfakeroot
cd ..
sudo dpkg -i libxine-extracodecs_1.1.1+ubuntu1-2+_amd64.deb

(don't be stupid, if filenames don't match, use what you've got)

---

### Post by soulsource on 2006-07-30
Wow, that was one of the two things I really missed on AMD64 (the second is a compiling native OpenOffice 2.X). Many thanks to jserve (and to Tsai Dung-Bang, of course, for posting here in english, so I was able to find it - pity me can't read jserve's blog). It's also working flawlessly with the new Mplayer Release (pre8).

---

### Post by skylark on 2006-07-31
I wouldn't have guessed an open-source WMV9 solution was possible.

Does anybody know if jserv's work is being officially integrated into codecs that VLC/MPlayer/Xine use? What about gstreamer..?

EDIT: I did some googling and found WMV9 is being worked on as part of the [VC-1 standard]("http://en.wikipedia.org/wiki/VC-1") implementation in [FFmpeg]("http://ffmpeg.mplayerhq.hu/"). This should make WMV9 natively available in other programs (eg via [the gstreamer ffmpeg plugin]("http://gstreamer.freedesktop.org/modules/gst-ffmpeg.html")).

FFmpeg also has a [google summer of code project for VC-1]("http://code.google.com/soc/ffmpeg/appinfo.html?csaid=5AA777DB19E2BB24").

---

### Post by refdoc on 2006-08-01
Thanks for the above.

---

### Post by Rondom on 2006-08-05
> **maleficent said:**
> And here's one for xine (make sure you've already got build-essential, dpkg-dev and fakeroot installed):Could anyone please modify this patch to work with xine-extracodecs 1.1.2?

---

### Post by citizenkeith on 2006-08-09
> **Tsai Dung-Bang said:**
> Download the attachment patch file or the following link.
(I will remove it in one day.)
```
wget http://www.phys.ncku.edu.tw/~c2491665/mplayer-wmv3.diff.gz
```



> Resolving [www.phys.ncku.edu.tw](www.phys.ncku.edu.tw)... 140.116.91.1
Connecting to www.phys.ncku.edu.tw|140.116.91.1|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
07:35:09 ERROR 404: Not Found.


Anybody else hosting this file?

---

### Post by daFoos on 2006-08-15
> **citizenkeith said:**
> Anybody else hosting this file?

yeah that would be great please!

---

### Post by jsvidyad on 2006-09-23
[http://jserv.sayya.org/mplayer/wmv3-support-via-vc1.diff.gz](http://jserv.sayya.org/mplayer/wmv3-support-via-vc1.diff.gz)

---

### Post by Raj1991 on 2006-10-24
> **Tsai Dung-Bang said:**
> 

Due to the path in the patch, we need to change the dir of source, this depond
on which ubuntu you use. In the last dapper, you may like to follow me.

```
mv mplayer-0.99+1.0pre7try2+cvs20060117 mplayer

```

```
zcat mplayer-wmv3.diff.gz | patch -p0
```

```
cd mplayer
dpkg-buildpackage

```

After a long time, you will get deb file, just type 
```

cd ..
dpkg -i *.deb

```

And everthing is down, enjoy your wmv moves and forget the evil windows dll codecs.

By Dung-Bang Tsai

Hi guys this is my first post on the forums and I'm a new Ubuntu user. So far its going good for me and I've managed to get most of the codecs down except this one. What I want to know Is how I get past this bit. I don't really know what to do now. Ive gotten through the first bits.

---

### Post by radiobuzzer on 2006-10-24
It worked for me... all, except the mplayer-nogui deb package which returned some strange errors. But installed just the rest 3 of them and WORK PERFECTLY. Thanks pals!

---

### Post by jkwarras on 2006-10-30
Could someone post some instructions on how-to patch ffmpeg to support wmv9, so gstreamer (and totem) support it?

Sorry, I don't know how to do it myself :rolleyes: 

Thanks a lot.

---

### Post by xstaticxgpx on 2006-10-30
or you could just build the mplayer svn with instructions from [this thread]("http://ubuntuforums.org/showthread.php?t=270066&highlight=wmv9")

and jkwarras, build the ffmpeg from svn and totem should be able to support wmv9

---

### Post by RAOF on 2006-10-30
> **jkwarras said:**
> Could someone post some instructions on how-to patch ffmpeg to support wmv9, so gstreamer (and totem) support it?

...

You can't; gstreamer-ffmpeg uses their own internal copy of the ffmpeg source.  You need to wait for them to update their internal ffmpeg source before gstreamer will have native wmv9 support.

---

### Post by jkwarras on 2006-10-31
> **RAOF said:**
> You can't; gstreamer-ffmpeg uses their own internal copy of the ffmpeg source.  You need to wait for them to update their internal ffmpeg source before gstreamer will have native wmv9 support.

So even if I rebuild from source ffmpeg like xstaticxgpx propose, totem will not use it?

---

### Post by RAOF on 2006-10-31
> **jkwarras said:**
> So even if I rebuild from source ffmpeg like xstaticxgpx propose, totem will not use it?

Short answer:  That's right.  

Long answer: gst-ffmpeg is built from it's **own** copy of the ffmpeg source (as is recommended by FFmpeg developers).  You'd need to get the gst-ffmpeg source, copy the new ffmpeg source code into it's build directory, fix up any of the things the changed FFmpeg API will break, and then rebuild gst-ffmpeg.  That's not going to be easy.

---

### Post by jkwarras on 2006-11-02
> **RAOF said:**
> You'd need to get the gst-ffmpeg source, copy the new ffmpeg source code into it's build directory, fix up any of the things the changed FFmpeg API will break, and then rebuild gst-ffmpeg.  That's not going to be easy.

Too much for me ;) Thanks for the answer.

---

### Post by RAOF on 2006-11-02
> **jkwarras said:**
> Too much for me ;) Thanks for the answer.

Actually, it seems that gst-ffmpeg in CVS has wmv3 support.  I'd be much easier to build that :).

---

### Post by darkshadow on 2006-11-03
How do I change the version number so that update-manager does not constantly complain about it. I don't want to lock the version in synaptic since for some reason every time I try synaptic segfaults

---

### Post by jkwarras on 2006-11-05
> **RAOF said:**
> Actually, it seems that gst-ffmpeg in CVS has wmv3 support.  I'd be much easier to build that :).

Sorry, I'm too noob but is there some Howto to compile gst-ffmpeg from CVS? :rolleyes: Thanks.

---

### Post by Azakus on 2006-11-05
You know, VLC has native support for WMV9 in its 0.8.6 release that is in Edgy's repos. Just do sudo apt-get install vlc vlc-plugin-esd and you're good to go.

---

### Post by camilluk on 2006-11-30
Do I have to use mplayer to watch wmv's or can I follow these instructions and then use kaffeine? I don't want to let all these players proliferate on my machine and I'm quite happy with Amarok and Kaffeine...

If that wouldn't do, do you have any suggestions to watch wmv's with Kaffeine or that's simply not possible?

Thank you[FONT=monospace][/FONT]!
Cam

---

### Post by berlakovich on 2007-01-11
tried in Edgy on AMD64 - WORKS GREAT !!! thanks !

---

### Post by janfsd on 2007-01-11
I don't know if the patch is needed anymore, because the latest build of ffmpeg already have built in support for wmv.

---

### Post by spatterlight on 2007-05-11
This is a great solution -- I just put Ubuntu 6.10 on my parents' geriatric iMac, and streaming wmv (.asf) files were the final thing they wanted it to do. Huge thanks.

But I can't get the files to stream from Firefox -- I've got the same problem as a previous poster. I can get it to stream perfectly when I make the terminal do it ($ mplayer [http://199.xxx.xxx.164/movie.asf](http://199.xxx.xxx.164/movie.asf)) but in Firefox, all I get is sound and no video, just like before the patch. (And a brief pink flash across the entire screen, though, which never showed up before the patch.)

I've got the mplayer plugin for Firefox installed, do I need to reconfigure it somehow? Thanks for helping me out.

---

### Post by caryb on 2007-06-28
After stuffing around for a couple of hours & getting nowhere i found this post back a page
> You know, VLC has native support for WMV9 in its 0.8.6 release that is in Edgy's repos. Just do sudo apt-get install vlc vlc-plugin-esd and you're good to go.

It just works no more effort thanks mate!

Cary
Gutsy Kubuntu 64

---

