---
title: "Floola - Has any ones manage to install it on 64?"
date: 2008-06-14
forum: x86 64-bit Users
---

### Post by sweetthdevil on 2008-06-14
Hello, 

As many of us I guess, I have an Ipod and where looking for the best solution to synchronize it, and I found Floola, but unsupported for 64 bits versions, a real shame. 

Anyway, if you manage to get it working with your 64 version please let us know...

Thanks

---

### Post by Floola on 2008-06-18
Check this post: [http://www.floola.com/modules/newbb/viewtopic.php?topic_id=660&start=10](http://www.floola.com/modules/newbb/viewtopic.php?topic_id=660&start=10)

Installing ia32libs, lib32gcc1, libc6i386 via synaptic should be enough.

HTH,
Tomas

---

### Post by firecat53 on 2008-08-15
Hey. I've installed all the 32 bit libraries per the instructions on the Floola website and these forums, and I've got both libgstreamer and libxine installed. Floola will launch without an ipod attached, but as soon as the ipod is attached, I get the following:
libgstreamer not found
libxine not found
Segmentation fault

I tried using getlibs on libgstreamer, and it apparently installed correctly the 32 bit version, but all that does is change the error to:
incompatible version of libgstreamer
libxine not found
Segmentation fault

Any ideas??

Thanks!
Scott

---

### Post by Yellow Pasque on 2008-08-16
The program started fine for me, though I don't have an ipod to test it out.

What commands did you use with getlibs?

---

### Post by firecat53 on 2008-08-16
Well, I got it working, except I can't hear any sound when trying to play music from within Floola. Haven't tested movie clip playback yet.

Floola started up initially just fine, it's just that it would close whenever an ipod was attached.

I used the following to get it working. I tried getlibs -p with the various package names at first, but it didn't seem to solve anything. So I started using getlibs -l with the names of everything Floola said was missing when I ran it from the command line. Still some errors that show up, but .....

```
 sudo getlibs -l libmad.so.0 libmpeg2.so.0 libdvdread.so.3 liboil-0.3.so.0 libsidplay.so.1 libgstmad.so liba52-0.7.4.so libgstgsm.so libgsm.so.1 libgsttrm.so libmusicbrainz.so.4 libgsttaglib.so libtag.so.1 libgstcdaudio.so  libcdaudio.so.1 libgstmms.so  libmms.so.0 libgstmetadata.so libexempi.so.3 libgstmusepack.so libmpcdec.so.3 libgstwildmidi.so libWildMidi.so.0 libgstcacasink.so libcaca.so.0 libgstaasink.so  libaa.so.1 libgstsouphttpsrc.so  libsoup-2.4.so.1 libgstspc.so libopenspc.so.0 libgst1394.so libavc1394.so.0 libgstwavpack.so libwavpack.so.1 libgstdv.so  libdv.so.4 libgstcdio.so libcdio.so.7 libgstmad.so  libid3tag.so.0 libgstshout2.so libshout.so.3 libgstspeex.so libspeex.so.1 libgstsoundtouch.so  libSoundTouch.so.1 libgstmythtvsrc.so libgmyth.so.0 libgstfaad.so  libfaad.so.0 libgstneonhttpsrc.so libneon.so.27

```

Any ideas on fixing sound? Could this be because Hardy uses Pulse Audio now instead of Alsa? Or something completely different?

Scott

---

