---
title: "Installing Gnash (CVS) for watching youtube on amd64"
date: 2007-06-11
forum: x86 64-bit Users (Pre April '08)
---

### Post by predaeus on 2007-06-11
Since Gnash 0.8.0 is not available in the Feisty nor Gutsy repositories as of writing this I'll explain how to install the cvs version.

DISCLAIMER: Use this tutorial at your own risk. Although these steps worked for me, there is no guarantee that it will work for you. Also it can break your system. I take no responsibilities for any problems that arise. Read all steps first before starting to execute any!



You will need many libraries and the build-essential package for this to work. You can see what dev libraries are missing when you follow the tutorial.

TESTED ON: AMD64, running Xubuntu Feisty Fawn, Kernel Linux 2.6.20-15-generic, with Gnash cvs version from June, 11th 2007.



Gnash 0.8.0 (alpha) was finally released on June 9, 2007 and supports playing some (all?) youtube videos.

[http://www.gnu.org/software/gnash/](http://www.gnu.org/software/gnash/)


To get the current version from cvs run:

```

export CVS_RSH="ssh"
cvs -z3 -d:pserver:anonymous@cvs.sv.gnu.org:/sources/gnash co gnash

```

as stated on the official web page above.

Just hit enter if there is a password prompt (there was none for me). This will download the current cvs sources of gnash to ./gnash/ in the current directory.

Next read the accompanying README, README_CVS and INSTALL files to get an idea of what options you have when configuring. I chose --enable-media=GST first which did not work, or the random youtube video just would not work with gnash. Anyway, I tried ffmpeg next and it worked.

So run:

```

./configure --enable-renderer=opengl --enable-media=ffmpeg

```

which will take quite a while to configure all options.

If any libraries are missing the configure script will tell you at the end of it's execution, so carefully read the output (just the part at the end when it finished) to see what dev packages you might be missing.

The configure script is very nice and will tell you the exact package names needed to install with apt-get. So if anything is missing just install with apt-get (just write "sudo apt-get install" and then add all missing package names by marking with the mouse and pasting with either ctrl-c/v or middle-mouse-click, don't forget to separate package names with a space) and re-run the configure command above. (The last three warnings about missing dev packages was only for debugging output of gnash that you might not need so just ignore them or install the packages if you want). If there is more packages who's names are not explicitly listed then use "apt-cache search NAME" to find out what the package you need might be (typically it starts with "lib" and ends with "-dev", so something like "libblablabla1.2-dev")

Ok, if configure finished successfully you can run:

```

make

```

which will start to compile the sources together with the options you set with ./configure. 

This will take even longer and scroll a lot of messages on your console. Just be patient and wait. This should not bring up any errors, if it does then make will abort and you will have to fix those. Then run make again (it will not rebuild successfully compiled parts of gnash, only the things that it did not compile yet).

If you have problems post them here so someone can help. But normally after you configured successfully there should be no problems.

When everything is done, you can run

```

sudo make install

```

to install gnash into the default location /usr/local/bin/gnash and the gnash firefox plugin into .mozilla/plugins/libgnashplugin.so.

WARNING: If you chose to remove gnash later you need to keep the build directory to do it easily. To uninstall gnash later run

```

sudo make uninstall

```

from the build directory to remove any files installed. If you lose the build directory you will have to remove the installed files by hand. This can lead to problems if not done correctly and when installing packaged versions of gnash later on.

Now if everything worked fine, open firefox and youtube.com and watch some video of a space shuttle lift-off, I just did ;-D

Enjoy!

---

### Post by Cappy on 2007-06-12
Awesome. Do you know if it works in alternate browsers such as Opera (which is 32-bit only)? I guess you would probably need to recompile this for an i386 arch to run it on an i386 browser?

Does it work on other flash players on other sites such as shoutfile.com or break.com?

Thanks for the guide!

---

### Post by jusmurph on 2007-06-12
Sounds promising :grin:

---

### Post by zsouthboy on 2007-06-12
Or you could share a .deb, if you were a nice guy, since you already got compiling to work :D

---

### Post by howlingmadhowie on 2007-07-13
i found i had to 

sudo apt-get install libboost-thread-dev libboost-date-time-dev

as well :)

---

### Post by crush304 on 2007-07-16
there are deb's in the mozilla team preview archive

[https://wiki.ubuntu.com/MozillaTeam/PreviewArchives]("https://wiki.ubuntu.com/MozillaTeam/PreviewArchives")

---

### Post by ubuntubrian on 2007-07-24
I couldn't run the ./configure command. I got "command not found" and in checking the README_CVS I saw that I had to run ".autogen.sh" first, then do the configure.

---

### Post by ubuntubrian on 2007-07-24
the configure went fine-no errors but I get this on make:

```
Making all in utilities
make[2]: Entering directory `/home/brianokeefe/gnash/utilities'
/bin/sh ../libtool --tag=CXX --mode=link g++  -g -O2 -pthread     -W     -Wall     -Wcast-align     -Wcast-qual     -Wpointer-ar ith     -Wreturn-type      -ldl -lltdl  -lxml2 -lz -lm -L/usr/local/lib -lavcodec -lz -la52 -lmp3lame -lm -lxvidcore -lfaac -lfa ad -ldl -ltheora -lavutil -logg   -ldts   -lvorbisenc -lvorbis -lm -logg   -L/usr/local/lib -lavformat -lavcodec -lz -la52 -lmp3 lame -lm -lxvidcore -lfaac -lfaad -ldl -ltheora -lavutil -logg   -L/usr/local/lib -lavutil   -ltheora -logg   -lgsm -ldc1394_con trol -L/usr/lib -lcurl -lboost_date_time -lboost_thread -lpthread  -Wl,--as-needed -o dumpshm  dumpshm.o ../server/libgnashserve r.la ../libbase/libgnashbase.la ../backend/libgnashbackend.la ../libamf/libgnashamf.la -L/usr/local/lib -lavcodec -lz -la52 -lmp 3lame -lm -lxvidcore -lfaac -lfaad -ldl -ltheora -lavutil -logg   -ldts   -lvorbisenc -lvorbis -lm -logg   -L/usr/local/lib -lav format -lavcodec -lz -la52 -lmp3lame -lm -lxvidcore -lfaac -lfaad -ldl -ltheora -lavutil -logg   -L/usr/local/lib -lavutil   -lt heora -logg   -lgsm -ldc1394_control  -lglib-2.0    -lrt -lX11 -lXi -lm
g++ -g -O2 -pthread -W -Wall -Wcast-align -Wcast-qual -Wpointer-arith -Wreturn-type -Wl,--as-needed -o .libs/dumpshm dumpshm.o -L/usr/local/lib -L/usr/lib ../server/.libs/libgnashserver.so ../libbase/.libs/libgnashbase.so ../backend/.libs/libgnashbackend. so /home/brianokeefe/gnash/server/.libs/libgnashserver.so /home/brianokeefe/gnash/libamf/.libs/libgnashamf.so /home/brianokeefe/ gnash/libgeometry/.libs/libgnashgeo.so /usr/lib/libxml2.so /usr/lib/libfreetype.so -lfontconfig /usr/lib/libSDL.so /usr/lib/liba sound.so /usr/lib/libartsc.so -L/usr/share/qt3/lib /usr/lib/libgthread-2.0.so /usr/lib/libesd.so /usr/lib/libaudiofile.so -laudi o -lXt -lXext /usr/lib/libaa.so -lncurses -lslang /usr/lib/libpangox-1.0.so /usr/lib/libpango-1.0.so /usr/lib/libatk-1.0.so /usr /lib/libgobject-2.0.so /usr/lib/libgmodule-2.0.so ../libamf/.libs/libgnashamf.so /home/brianokeefe/gnash/libbase/.libs/libgnashb ase.so /usr/lib/libjpeg.so /usr/lib/libcurl.so -lgssapi_krb5 -lkrb5 -lk5crypto -lkrb5support -lcom_err -lresolv /usr/lib/libidn. so -lssl -lcrypto -lGL -lGLU /usr/lib/libltdl.so -lboost_date_time -lboost_thread -lpthread -ldts /usr/lib/libvorbisenc.so /usr/ lib/libvorbis.so -lavformat -lavcodec -lz /usr/lib/liba52.so /usr/lib/libmp3lame.so -lxvidcore -lfaac -lfaad -ldl -lavutil /usr/ lib/libtheora.so /usr/lib/libogg.so -lgsm -ldc1394_control /usr/lib/libglib-2.0.so -lrt -lX11 -lXi -lm -Wl,--rpath -Wl,/usr/loca l/lib
/home/brianokeefe/gnash/libbase/.libs/libgnashbase-cvs.so: undefined reference to `sws_scale'
/home/brianokeefe/gnash/libbase/.libs/libgnashbase-cvs.so: undefined reference to `sws_getContext'
collect2: ld returned 1 exit status
make[2]: *** [dumpshm] Error 1
make[2]: Leaving directory `/home/brianokeefe/gnash/utilities'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/brianokeefe/gnash'
make: *** [all] Error 2
```


Am I missing some library?

:(

---

### Post by HarshReality on 2007-07-24
Did you look into democracy or is thee a specific reason you sighted Gnash?

[http://www.getmiro.com/download/](http://www.getmiro.com/download/)

---

### Post by jamesford on 2007-07-24
the repo one working quite well...almost. sticking with it!
thanks for the heads up

---

### Post by ubuntubrian on 2007-07-24
OK-it seems that the ffmpeg code has been stripped to make it truly open. see
[http://savannah.gnu.org/bugs/?20500](http://savannah.gnu.org/bugs/?20500)
 and follow the link 
[http://lists.mplayerhq.hu/pipermail/ffmpeg-user/2007-June/009255.html](http://lists.mplayerhq.hu/pipermail/ffmpeg-user/2007-June/009255.html)

I switched to compiling for gstreamer and gnash installed fine.

---

