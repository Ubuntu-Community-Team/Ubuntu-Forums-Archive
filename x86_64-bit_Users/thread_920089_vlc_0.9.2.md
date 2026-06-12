---
title: "vlc 0.9.2"
date: 2008-09-14
forum: x86 64-bit Users
---

### Post by KuriKai on 2008-09-14
hey all.
Vlc 0.9.2 has been released but I am having problems compiling it, does anyone else have these problems?
```
/Downloads/vlc-0.9.2$ make
make  all-recursive
make[1]: Entering directory `/home/dave/Downloads/vlc-0.9.2'
Making all in po
make[2]: Entering directory `/home/dave/Downloads/vlc-0.9.2/po'
make[2]: Leaving directory `/home/dave/Downloads/vlc-0.9.2/po'
Making all in src
make[2]: Entering directory `/home/dave/Downloads/vlc-0.9.2/src'
make  all-recursive
make[3]: Entering directory `/home/dave/Downloads/vlc-0.9.2/src'
Making all in .
make[4]: Entering directory `/home/dave/Downloads/vlc-0.9.2/src'
make[4]: Nothing to be done for `all-am'.
make[4]: Leaving directory `/home/dave/Downloads/vlc-0.9.2/src'
Making all in test
make[4]: Entering directory `/home/dave/Downloads/vlc-0.9.2/src/test'
make[4]: Nothing to be done for `all'.
make[4]: Leaving directory `/home/dave/Downloads/vlc-0.9.2/src/test'
make[3]: Leaving directory `/home/dave/Downloads/vlc-0.9.2/src'
make[2]: Leaving directory `/home/dave/Downloads/vlc-0.9.2/src'
Making all in libs/srtp
make[2]: Entering directory `/home/dave/Downloads/vlc-0.9.2/libs/srtp'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/dave/Downloads/vlc-0.9.2/libs/srtp'
Making all in bin
make[2]: Entering directory `/home/dave/Downloads/vlc-0.9.2/bin'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/dave/Downloads/vlc-0.9.2/bin'
Making all in modules
make[2]: Entering directory `/home/dave/Downloads/vlc-0.9.2/modules'
Making all in access
make[3]: Entering directory `/home/dave/Downloads/vlc-0.9.2/modules/access'
make  all-recursive
make[4]: Entering directory `/home/dave/Downloads/vlc-0.9.2/modules/access'
Making all in dvb
make[5]: Entering directory `/home/dave/Downloads/vlc-0.9.2/modules/access/dvb'
make  all-am
make[6]: Entering directory `/home/dave/Downloads/vlc-0.9.2/modules/access/dvb'
make[6]: Nothing to be done for `all-am'.
make[6]: Leaving directory `/home/dave/Downloads/vlc-0.9.2/modules/access/dvb'
make[5]: Leaving directory `/home/dave/Downloads/vlc-0.9.2/modules/access/dvb'
Making all in mms
make[5]: Entering directory `/home/dave/Downloads/vlc-0.9.2/modules/access/mms'
make  all-am
make[6]: Entering directory `/home/dave/Downloads/vlc-0.9.2/modules/access/mms'
make[6]: Nothing to be done for `all-am'.
make[6]: Leaving directory `/home/dave/Downloads/vlc-0.9.2/modules/access/mms'
make[5]: Leaving directory `/home/dave/Downloads/vlc-0.9.2/modules/access/mms'
Making all in cdda
make[5]: Entering directory `/home/dave/Downloads/vlc-0.9.2/modules/access/cdda'
make  all-am
make[6]: Entering directory `/home/dave/Downloads/vlc-0.9.2/modules/access/cdda'
make[6]: Nothing to be done for `all-am'.
make[6]: Leaving directory `/home/dave/Downloads/vlc-0.9.2/modules/access/cdda'
make[5]: Leaving directory `/home/dave/Downloads/vlc-0.9.2/modules/access/cdda'
Making all in rtsp
make[5]: Entering directory `/home/dave/Downloads/vlc-0.9.2/modules/access/rtsp'
make  all-am
make[6]: Entering directory `/home/dave/Downloads/vlc-0.9.2/modules/access/rtsp'
make[6]: Nothing to be done for `all-am'.
make[6]: Leaving directory `/home/dave/Downloads/vlc-0.9.2/modules/access/rtsp'
make[5]: Leaving directory `/home/dave/Downloads/vlc-0.9.2/modules/access/rtsp'
Making all in rtmp
make[5]: Entering directory `/home/dave/Downloads/vlc-0.9.2/modules/access/rtmp'
make  all-am
make[6]: Entering directory `/home/dave/Downloads/vlc-0.9.2/modules/access/rtmp'
make[6]: Nothing to be done for `all-am'.
make[6]: Leaving directory `/home/dave/Downloads/vlc-0.9.2/modules/access/rtmp'
make[5]: Leaving directory `/home/dave/Downloads/vlc-0.9.2/modules/access/rtmp'
Making all in v4l2
make[5]: Entering directory `/home/dave/Downloads/vlc-0.9.2/modules/access/v4l2'
make  all-am
make[6]: Entering directory `/home/dave/Downloads/vlc-0.9.2/modules/access/v4l2'
make[6]: Nothing to be done for `all-am'.
make[6]: Leaving directory `/home/dave/Downloads/vlc-0.9.2/modules/access/v4l2'
make[5]: Leaving directory `/home/dave/Downloads/vlc-0.9.2/modules/access/v4l2'
Making all in vcd
make[5]: Entering directory `/home/dave/Downloads/vlc-0.9.2/modules/access/vcd'
make  all-am
make[6]: Entering directory `/home/dave/Downloads/vlc-0.9.2/modules/access/vcd'
make[6]: Nothing to be done for `all-am'.
make[6]: Leaving directory `/home/dave/Downloads/vlc-0.9.2/modules/access/vcd'
make[5]: Leaving directory `/home/dave/Downloads/vlc-0.9.2/modules/access/vcd'
Making all in vcdx
make[5]: Entering directory `/home/dave/Downloads/vlc-0.9.2/modules/access/vcdx'
make  all-am
make[6]: Entering directory `/home/dave/Downloads/vlc-0.9.2/modules/access/vcdx'
make[6]: Nothing to be done for `all-am'.
make[6]: Leaving directory `/home/dave/Downloads/vlc-0.9.2/modules/access/vcdx'
make[5]: Leaving directory `/home/dave/Downloads/vlc-0.9.2/modules/access/vcdx'
Making all in screen
make[5]: Entering directory `/home/dave/Downloads/vlc-0.9.2/modules/access/screen'
make  all-am
make[6]: Entering directory `/home/dave/Downloads/vlc-0.9.2/modules/access/screen'
make[6]: Nothing to be done for `all-am'.
make[6]: Leaving directory `/home/dave/Downloads/vlc-0.9.2/modules/access/screen'
make[5]: Leaving directory `/home/dave/Downloads/vlc-0.9.2/modules/access/screen'
make[5]: Entering directory `/home/dave/Downloads/vlc-0.9.2/modules/access'
make[5]: Nothing to be done for `all-am'.
make[5]: Leaving directory `/home/dave/Downloads/vlc-0.9.2/modules/access'
make[4]: Leaving directory `/home/dave/Downloads/vlc-0.9.2/modules/access'
make[3]: Leaving directory `/home/dave/Downloads/vlc-0.9.2/modules/access'
Making all in access_filter
make[3]: Entering directory `/home/dave/Downloads/vlc-0.9.2/modules/access_filter'
make  all-am
make[4]: Entering directory `/home/dave/Downloads/vlc-0.9.2/modules/access_filter'
make[4]: Nothing to be done for `all-am'.
make[4]: Leaving directory `/home/dave/Downloads/vlc-0.9.2/modules/access_filter'
make[3]: Leaving directory `/home/dave/Downloads/vlc-0.9.2/modules/access_filter'
Making all in audio_filter
make[3]: Entering directory `/home/dave/Downloads/vlc-0.9.2/modules/audio_filter'
make  all-recursive
make[4]: Entering directory `/home/dave/Downloads/vlc-0.9.2/modules/audio_filter'
Making all in channel_mixer
make[5]: Entering directory `/home/dave/Downloads/vlc-0.9.2/modules/audio_filter/channel_mixer'
make  all-am
make[6]: Entering directory `/home/dave/Downloads/vlc-0.9.2/modules/audio_filter/channel_mixer'
make[6]: Nothing to be done for `all-am'.
make[6]: Leaving directory `/home/dave/Downloads/vlc-0.9.2/modules/audio_filter/channel_mixer'
make[5]: Leaving directory `/home/dave/Downloads/vlc-0.9.2/modules/audio_filter/channel_mixer'
Making all in converter
make[5]: Entering directory `/home/dave/Downloads/vlc-0.9.2/modules/audio_filter/converter'
make  all-am
make[6]: Entering directory `/home/dave/Downloads/vlc-0.9.2/modules/audio_filter/converter'
make[6]: Nothing to be done for `all-am'.
make[6]: Leaving directory `/home/dave/Downloads/vlc-0.9.2/modules/audio_filter/converter'
make[5]: Leaving directory `/home/dave/Downloads/vlc-0.9.2/modules/audio_filter/converter'
Making all in resampler
make[5]: Entering directory `/home/dave/Downloads/vlc-0.9.2/modules/audio_filter/resampler'
make  all-am
make[6]: Entering directory `/home/dave/Downloads/vlc-0.9.2/modules/audio_filter/resampler'
make[6]: Nothing to be done for `all-am'.
make[6]: Leaving directory `/home/dave/Downloads/vlc-0.9.2/modules/audio_filter/resampler'
make[5]: Leaving directory `/home/dave/Downloads/vlc-0.9.2/modules/audio_filter/resampler'
Making all in spatializer
make[5]: Entering directory `/home/dave/Downloads/vlc-0.9.2/modules/audio_filter/spatializer'
make  all-am
make[6]: Entering directory `/home/dave/Downloads/vlc-0.9.2/modules/audio_filter/spatializer'
make[6]: Nothing to be done for `all-am'.
make[6]: Leaving directory `/home/dave/Downloads/vlc-0.9.2/modules/audio_filter/spatializer'
make[5]: Leaving directory `/home/dave/Downloads/vlc-0.9.2/modules/audio_filter/spatializer'
make[5]: Entering directory `/home/dave/Downloads/vlc-0.9.2/modules/audio_filter'
make[5]: Nothing to be done for `all-am'.
make[5]: Leaving directory `/home/dave/Downloads/vlc-0.9.2/modules/audio_filter'
make[4]: Leaving directory `/home/dave/Downloads/vlc-0.9.2/modules/audio_filter'
make[3]: Leaving directory `/home/dave/Downloads/vlc-0.9.2/modules/audio_filter'
Making all in audio_mixer
make[3]: Entering directory `/home/dave/Downloads/vlc-0.9.2/modules/audio_mixer'
make  all-am
make[4]: Entering directory `/home/dave/Downloads/vlc-0.9.2/modules/audio_mixer'
make[4]: Nothing to be done for `all-am'.
make[4]: Leaving directory `/home/dave/Downloads/vlc-0.9.2/modules/audio_mixer'
make[3]: Leaving directory `/home/dave/Downloads/vlc-0.9.2/modules/audio_mixer'
Making all in audio_output
make[3]: Entering directory `/home/dave/Downloads/vlc-0.9.2/modules/audio_output'
make  all-am
make[4]: Entering directory `/home/dave/Downloads/vlc-0.9.2/modules/audio_output'
make[4]: Nothing to be done for `all-am'.
make[4]: Leaving directory `/home/dave/Downloads/vlc-0.9.2/modules/audio_output'
make[3]: Leaving directory `/home/dave/Downloads/vlc-0.9.2/modules/audio_output'
Making all in codec
make[3]: Entering directory `/home/dave/Downloads/vlc-0.9.2/modules/codec'
make  all-recursive
make[4]: Entering directory `/home/dave/Downloads/vlc-0.9.2/modules/codec'
Making all in cmml
make[5]: Entering directory `/home/dave/Downloads/vlc-0.9.2/modules/codec/cmml'
make  all-am
make[6]: Entering directory `/home/dave/Downloads/vlc-0.9.2/modules/codec/cmml'
make[6]: Nothing to be done for `all-am'.
make[6]: Leaving directory `/home/dave/Downloads/vlc-0.9.2/modules/codec/cmml'
make[5]: Leaving directory `/home/dave/Downloads/vlc-0.9.2/modules/codec/cmml'
Making all in dmo
make[5]: Entering directory `/home/dave/Downloads/vlc-0.9.2/modules/codec/dmo'
make  all-am
make[6]: Entering directory `/home/dave/Downloads/vlc-0.9.2/modules/codec/dmo'
make[6]: Nothing to be done for `all-am'.
make[6]: Leaving directory `/home/dave/Downloads/vlc-0.9.2/modules/codec/dmo'
make[5]: Leaving directory `/home/dave/Downloads/vlc-0.9.2/modules/codec/dmo'
Making all in avcodec
make[5]: Entering directory `/home/dave/Downloads/vlc-0.9.2/modules/codec/avcodec'
make  all-am
make[6]: Entering directory `/home/dave/Downloads/vlc-0.9.2/modules/codec/avcodec'
/bin/bash ../../../libtool --tag=CC   --mode=link gcc -std=gnu99 `top_builddir="../../.." ../../../vlc-config --cflags plugin libavcodec_plugin.la` -Wall -Wextra -Wsign-compare -Wundef -Wpointer-arith -Wbad-function-cast -Wcast-align -Wwrite-strings -Wmissing-prototypes -Wvolatile-register-var -rpath '/usr/local/lib/vlc/codec' -avoid-version -module -no-undefined -export-symbol-regex ^vlc_entry -shrext .so `top_builddir="../../.." ../../../vlc-config --ldflags plugin libavcodec_plugin.la`  -o libavcodec_plugin.la  libavcodec_plugin_la-avcodec.lo libavcodec_plugin_la-video.lo libavcodec_plugin_la-audio.lo libavcodec_plugin_la-deinterlace.lo  libavcodec_plugin_la-encoder.lo  `top_builddir="../../.." ../../../vlc-config -libs plugin libavcodec_plugin.la` ../../../src/libvlccore.la 
gcc -std=gnu99 -shared  .libs/libavcodec_plugin_la-avcodec.o .libs/libavcodec_plugin_la-video.o .libs/libavcodec_plugin_la-audio.o .libs/libavcodec_plugin_la-deinterlace.o .libs/libavcodec_plugin_la-encoder.o  -Wl,--rpath -Wl,/home/dave/Downloads/vlc-0.9.2/src/.libs -lpthread -L/usr/local/lib -lavcodec -lavutil -lm ../../../src/.libs/libvlccore.so  -mtune=athlon64 -Wl,-soname -Wl,libavcodec_plugin.so -o .libs/libavcodec_plugin.so
/usr/bin/ld: /usr/local/lib/libavcodec.a(allcodecs.o): relocation R_X86_64_32 against `aasc_decoder' can not be used when making a shared object; recompile with -fPIC
/usr/local/lib/libavcodec.a: could not read symbols: Bad value
collect2: ld returned 1 exit status
make[6]: *** [libavcodec_plugin.la] Error 1
make[6]: Leaving directory `/home/dave/Downloads/vlc-0.9.2/modules/codec/avcodec'
make[5]: *** [all] Error 2
make[5]: Leaving directory `/home/dave/Downloads/vlc-0.9.2/modules/codec/avcodec'
make[4]: *** [all-recursive] Error 1
make[4]: Leaving directory `/home/dave/Downloads/vlc-0.9.2/modules/codec'
make[3]: *** [all] Error 2
make[3]: Leaving directory `/home/dave/Downloads/vlc-0.9.2/modules/codec'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/dave/Downloads/vlc-0.9.2/modules'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/dave/Downloads/vlc-0.9.2'
make: *** [all] Error 2

```

---

### Post by cariboo on 2008-09-14
Looks like you're missing libavcodec-dev. It is available from the reositories. to install it in a terminal:

```
sudo apt-get install libavcodec-dev
```

Jim

---

### Post by KuriKai on 2008-09-15
I already have that installed

---

### Post by r.e.lietz on 2008-09-28
Yeah, I'm having that same problem too.  My husband installed VLC 0.9.3 on his computer, got it working, and copied the files to my computer...EXACTLY as he had them...and I'm still getting the same error.  When I try ./compile, it generates this error:  

source='spatializer.cpp' object='libspatializer_plugin_la-spatializer.lo' libtool=yes \
	DEPDIR=.deps depmode=none /bin/bash ../../../autotools/depcomp \
env: g++: No such file or directory
make: *** [all] Error 2


I've tried everything I can think of and then some...no change!!!:confused:


ANY SUGGESTION ANYONE CAN OFFER WOULD BE VERY WELCOME!!!

---

### Post by tjotser on 2008-09-28
Not being very helpful , but i received it on INTREPID updates today .

---

### Post by r.e.lietz on 2008-09-28
Well, I thought I found a fix...I installed g++!!!  

sudo apt-get install g++

and when I typed ./compile, it went way past the point where it gave me that error....but now it gave me this error:


source='qt4.cpp' object='libqt4_plugin_la-qt4.lo' libtool=yes \
	DEPDIR=.deps depmode=none /bin/bash ../../../autotools/depcomp \
In file included from dialogs/open.hpp:35,
                 from dialogs_provider.hpp:38,
                 from qt4.cpp:38:
ERROR   : ./ui/open.h: 33:  expected constructor, destructor, or type conversion before 'class'
make: *** [all] Error 2


UPDATE:

okay, make install didn't work (permission error), but sudo make install almost did...it generated this error:


In file included from dialogs/open.hpp:35,
                 from dialogs_provider.hpp:38,
                 from qt4.cpp:38:
./ui/open.h:33: error: expected constructor, destructor, or type conversion before &#8216;class&#8217;
make[6]: *** [libqt4_plugin_la-qt4.lo] Error 1
make[6]: Leaving directory `/home/rachelle/Desktop/vlc-0.9.3/modules/gui/qt4'
make[5]: *** [install] Error 2
make[5]: Leaving directory `/home/rachelle/Desktop/vlc-0.9.3/modules/gui/qt4'
make[4]: *** [install-recursive] Error 1
make[4]: Leaving directory `/home/rachelle/Desktop/vlc-0.9.3/modules/gui'
make[3]: *** [install] Error 2
make[3]: Leaving directory `/home/rachelle/Desktop/vlc-0.9.3/modules/gui'
make[2]: *** [install-recursive] Error 1
make[2]: Leaving directory `/home/rachelle/Desktop/vlc-0.9.3/modules'
make[1]: *** [install-recursive] Error 1
make[1]: Leaving directory `/home/rachelle/Desktop/vlc-0.9.3'
make: *** [install] Error 2

---

### Post by r.e.lietz on 2008-09-29
Alrighty,

This isn't really a 'fix', but at least VLC will work...it turns out that while I was trying to make the install and compile work...well, I didn't really need to because VLC already worked.  It won't run if you just type in vlc....and you'll have to add a launcher to the applications yourself, but it opens!!!  To add the launcher correctly, when entering the Command, you will have to browse to the vlc folder and select the file called VLC.  Let me know if it works for you...it's FINALLY working on mine.  

Not quite as nice as if it actually installed or compiled correctly...but it works!  Yay!!!  If anyone finds a way to get past those errors on the ./compile or make install, please let me know!!!!  Thanks, and hope this helps!!


Um, yeah, another update:

Just a note...after all this, my speakers have stopped working.  I'm pretty sure it's not anything I've posted here, just some other dumb thing I did while trying to fix all this, but thought in all fairness I should warn you...please, if you don't mind, let me know if you do or don't have this problem too.  When I find a fix, I'll let you know.

---

### Post by r.e.lietz on 2008-09-29
Well, finally got my speakers and, it seems, everything working right.  Still didn't get the make install or ./configure to work...but, then again, I haven't retried them yet as I don't seem to need to.  

Just in case anyone else has trouble with the speakers (I messed a lot up when I fiddled around, but I'm still pretty sure it wasn't any of the steps I posted - just other junk I shouldn't have played with), I had to go to System->Administration->Software Sources, then Updates and select all of the four options under Ubuntu Updates.  Not sure if that's a good thing, but something in there worked.  My speakers are good again.  My login screen reverted back (wierd!), but my Compiz, theme, and everything else still seem to work.

Except that I can't get Ubuntu to automatically check for updates...hmm...

Lol, I just know that one of these days I'm going to mess things up so bad that I'm going to have to reinstall and start all over!  Fun fun!!!!

Hope things work out for everyone else...who wants to guess that, now that I've just about killed my comp to get the new VLC working, they'll come out with the debugged linux install of it in the next day or two!!  I wouldn't be surprised, that sounds like my life!

---

### Post by Sockerdrickan on 2008-09-29
[http://tombuntu.com/index.php/2008/09/16/install-vlc-media-player-092-in-ubuntu/](http://tombuntu.com/index.php/2008/09/16/install-vlc-media-player-092-in-ubuntu/)

---

### Post by r.e.lietz on 2008-09-29
Wow, I knew there had to be an easier way!  Unfortunately, even though it appeared to install fine, when I try to open VLC it's generating this error:


rachelle@rachelle-laptop:~$ vlc
VLC media player 0.9.3 Grishenko
[00000001] main libvlc debug: VLC media player - version 0.9.3 Grishenko - (c) 1996-2008 the VideoLAN team
[00000001] main libvlc debug: libvlc was configured with ./configure  '--disable-mad' '--disable-avformat' '--disable-glx'
[00000001] main libvlc debug: translation test: code is "C"
[00000001] main libvlc error: no memcpy module matched "any"
[00000530] main demux error: no demux module matched "xspf-open"
[00000527] main input error: no suitable demux module for `file/xspf-open:///home/rachelle/.local/share/vlc/ml.xspf'
[00000533] main interface error: no interface module matched "hotkeys,none"
[00000533] main interface error: no suitable interface module
[00000001] main libvlc error: interface "hotkeys,none" initialization failed
[00000534] main interface error: no interface module matched "inhibit,none"
[00000534] main interface error: no suitable interface module
[00000001] main libvlc error: interface "inhibit,none" initialization failed
[00000535] main interface error: no interface module matched "screensaver,none"
[00000535] main interface error: no suitable interface module
[00000001] main libvlc error: interface "screensaver,none" initialization failed
[00000536] main interface error: no interface module matched "signals"
[00000536] main interface error: no suitable interface module
[00000001] main libvlc error: interface "signals" initialization failed
[00000001] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
[00000537] main interface error: no interface module matched "any"
[00000537] main interface error: no suitable interface module
[00000001] main libvlc error: interface "(null)" initialization failed
*** LibVLC Exception not handled: Interface initialization failed
Set a breakpoint in 'libvlc_exception_not_handled' to debug.



Not sure what to do now...going to try a few things, probably going to mess up my comp again :p  but oh well.  Any suggestions?

---

### Post by r.e.lietz on 2008-09-29
Never mind this message...fixed this, back to the last problem - I'm sure it must be related to old configurations ...I know they are carrying over.  In the old VLC, I had the sound set to default at 200%...and in the new VLC, it's defaulting to 200% even though I didn't specify that anywhere since the old one.  And, if you notice, the code says VLC was configured with a bunch of things disabled...well, that's from when I was trying to install it from source...that one will run, but the interface from the actual install won't.  I don't know how to remove these old configure settings, I already tried aptitude purge vlc, and I thought it definately did something.  aptitude install vlc installed the old VLC...

sudo apt-get remove vlc

then redid the steps from the webpage, an voila, the new VLC is back...but still won't launch.!!!!

So, I'm stuck using this uninstalled one unless someone has any more ideas...I'm fresh out at the moment :S

__________________________________________

Um, okay, I've REALLY messed things up now, and I'm not entirely sure how!  Does anyone know how to remove VLC and ALL it's components and associated apps, etc...As if it had never, ever been installed to begin with...

Help, please!!!!!  I'm at my wit's end, not a clue what to do!!:confused:

---

### Post by Artemis3 on 2008-09-29
Have you ever seen ~/.vlc/vlcrc ? Use a text editor :)

---

### Post by r.e.lietz on 2008-09-29
The file that came up when I typed in 

gedit ~/.vlc/vlcrc

was for VLC 0.8.6e...

I might want to mention at this point that I am a real newbie to all this...I'm winging it, and so far it's not going so great :S  Not sure what I'm supposed to do with this file, or if the fact that it's pointing to the wrong one is an indication of something (I'm guessing so) and how to fix it.  Please bear with me, I really appreciate all advice.  Thanks!

---

### Post by Yellow Pasque on 2008-09-30
You might be missing prerequisite libraries or -dev packages. Try this and then configuring/making again:
```
sudo apt-get build-dep vlc
```
(BTW, the above command should work for any software you're trying to build with a corresponding package available in Synaptic, unless the newer version has added dependencies.)

---

### Post by r.e.lietz on 2008-09-30
Alrighty, it works!  Exactly like it's supposed to!  

Nothing was fixing the problem, no matter how many times I removed, purged, or otherwise got rid of/changed/reinstalled VLC.

So, I purged VLC, and then decided I had nothing to lose...So I did something I considered very stupid at the time, and deleted ALL files that said VLC (except for the four fonts that had 'vlc' in their name :)).  Then I removed the repository I had added under 'Third-Parties', and restarted.

And then I followed the very simple steps on the webpage (thanks for posting that, it was a life-saver!!), and voila!!  VLC is working perfect!!!

Thanks for all the help everyone!

---

### Post by Yellow Pasque on 2008-09-30
For those who don't wish to, or are having trouble building, VLC 0.9.3 looks like it will make it in intrepid (due out on Oct. 30)
[https://launchpad.net/ubuntu/+source/vlc](https://launchpad.net/ubuntu/+source/vlc)

---

### Post by r.e.lietz on 2008-10-13
> **Tux0r said:**
> [http://tombuntu.com/index.php/2008/09/16/install-vlc-media-player-092-in-ubuntu/](http://tombuntu.com/index.php/2008/09/16/install-vlc-media-player-092-in-ubuntu/)



Okay, new problem.  My VLC 0.9.3 was working fine...and then update manager ran, and VLC 0.9.4 installed...and doesn't work properly.  It will no longer display video while Compiz is running.  (This is solely a problem with VLC, I got games and other videos to work, VLC is the only thing now not working with Compiz.)  This was not a problem in 0.9.3.  And despite the fact that all these settings are ON in VLC, the interface is not integrated with video, it doesn't display an interface when in fullscreen, and the window is not by default on top of other windows.  All of these worked in VLC 0.9.3, and I did not have to turn off Compiz as there was no conflict.  Now there is, and this happened RIGHT after the update installed 0.9.4.  Is anyone else having this problem, or have any suggestions?  Is there more information I can give that might help?

I should have removed the repository once I had VLC running properly, so that it didn't update and mess things up...I meant to, too...but I didn't!  What now?  I've tried just about everything, I have discovered that VLC 0.8 runs fine when that is installed...but 0.9.4 doesn't, and I can't figure out how to get 0.9.3 without trying to install from source again.  Help...........

---

### Post by Yellow Pasque on 2008-10-13
Open Synaptic and click on the vlc package. Under the Package menu, there is an option to "Force Version.." See if 0.9.3 is available there. Once you have 0.9.3 installed, then choose "Lock version" (also under the Package menu) to prevent upgrading.

---

### Post by istblacken on 2008-10-13
i updated to vlc 0.9.4 without any problem. i used this PPA [https://launchpad.net/~c-korn/+archive](https://launchpad.net/~c-korn/+archive)
it is not a signed repository...

---

### Post by Yellow Pasque on 2008-10-13
I believe that is the package she is using. The guide she followed had her add the repo to Software Sources
> deb [http://ppa.launchpad.net/c-korn/ubuntu](http://ppa.launchpad.net/c-korn/ubuntu) hardy main

---

### Post by tyk on 2008-10-13
@ Kurikai
what's this?
/usr/bin/ld: /usr/local/lib/libavcodec.a(allcodecs.o): relocation R_X86_64_32 against `aasc_decoder' can not be used when making a shared object; recompile with -fPIC

---

### Post by r.e.lietz on 2008-10-13
Hey, thanks for all the help everyone.  I got the video to show by going into preferences, video output, and selecting X11.  Unfortunately, my research has shown that integrated video was disabled for this version :( due to bugs...And, also unfortunate, synaptic cannot roll back to 0.9.3...it only has 0.8.6 and 0.9.4.  Does anyone know any other way to revert to an earlier version or installation?

Thanks so much guys!

---

### Post by Yellow Pasque on 2008-10-13
At this point you'll need to uninstall your existing vlc and either build vlc 0.9.3 from source or search the web for a vlc 0.9.3 .deb

---

### Post by ds3 on 2008-10-14
So, I upgraded from VLC 0.8.6e to 0.9.4 using the c-korn repository and noticed the problem with not being able to get the integrated controls as well. I'm surprised it was disabled as mentioned by r.e.lietz, seeing as it works in the Windows version, but that's not my most confusing problem.

When I try to open a .mpg file directly I get a message that the system cannot find "wxvlc" and it won't open. Other file types open fine and I can open the .mpg files from VLC fine. I tried installing wxvlc from Synaptic but it didn't help. Does anyone have any suggestions on this problem?

As far as the controller issue, I don't know about 0.9.3, but you can still get VLC 0.9.2 for AMD64 systems off the Debian experimental repository:
[http://packages.debian.org/experimental/vlc](http://packages.debian.org/experimental/vlc)
I don't know how much longer it will be there though since they've already updated the 32bit version to 0.9.4.

---

### Post by r.e.lietz on 2008-10-17
Alright, update:  In Intrepid (I upgraded and had numerous problems, but just a note:  since new updates came out, my ATI video card works better than ever!), the repositories have VLC 0.9.4, and recent updates have fixed the video integration and fullscreen controller problems.  Yay!

Just wondering if someone can tell me, does the c-korn repository have the fixed version?

---

