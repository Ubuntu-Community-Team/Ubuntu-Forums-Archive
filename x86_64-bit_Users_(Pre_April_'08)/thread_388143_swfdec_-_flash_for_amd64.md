---
title: "swfdec - flash for amd64"
date: 2007-03-19
forum: x86 64-bit Users (Pre April '08)
---

### Post by saneone on 2007-03-19
Hello,
I always read the recent news about Linux software and yesterday i've read about Swfdec
([http://swfdec.freedesktop.org/wiki/](http://swfdec.freedesktop.org/wiki/)). The developer claims his plugin is even able to play (since last month) YouTube movies (Gnash can't do that). Moreover it should work like a charm with amd64. Has anyone tried this solution?

---

### Post by Rinnan on 2007-03-19
I have downloaded the source for the latest version of swfdec (from git), compiled it and run it on my system, it does play youtube videos just fine (except seeking).  So, there's some verification.  Except, I don't run amd64.  But at least you know an ubuntu-head managed to get it to work.  I don't suppose that it is any harder to get to work on amd64, but who knows.  Give it a shot! :)

---

### Post by nicoladimaria on 2007-03-20
> **saneone said:**
> [...]
Has anyone tried this solution?
same question here

---

### Post by saneone on 2007-03-20
I wanted to compile swfdec 0.4.2, but i face some compilation problems that i'm unable to cope with.

"#./configure" runs ok, then "#make" outputs several warnings and stops after theses lines:

gcc -DHAVE_CONFIG_H -I. -I. -I../.. -Wall -Wextra -Wno-missing-field-initializers -Wno-unused-parameter -I../.. -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I. -DXP_UNIX -DDEBUG -fno-strict-aliasing -g -O2 -MT libjs_la-jsinterp.lo -MD -MP -MF .deps/libjs_la-jsinterp.Tpo -c jsinterp.c  -fPIC -DPIC -o .libs/libjs_la-jsinterp.o
jsinterp.c: In function 'js_Interpret':
jsinterp.c:1533: warning: format '%d' expects type 'int', but argument 3 has type 'long int'
jsinterp.c:4258: warning: format '%d' expects type 'int', but argument 3 has type 'long int'
gcc: Internal error: Segmentation fault (program cc1)
Please submit a full bug report.
See <URL:http://gcc.gnu.org/bugs.html> for instructions.
For Debian GNU/Linux specific bug reporting instructions, see
<URL:file:///usr/share/doc/gcc-4.1/README.Bugs>.

make[4]: *** [libjs_la-jsinterp.lo] Error 1
make[4]: Leaving directory `/home/saneone/swfdec-0.4.2/libswfdec/js'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/home/saneone/swfdec-0.4.2/libswfdec'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/home/saneone/swfdec-0.4.2/libswfdec'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/saneone/swfdec-0.4.2'
make: *** [all] Error 2

---

### Post by aanderse on 2007-03-22
hey,

i installed feisty fawn herd 5 (64bit) the other day, people had been having such great success i decided to run it as my primary os and i don't have a single complaint - not one :)

so the news about the swfdec release was today, i've been waiting for this because i like to just use the free software (with the only exception being nvidia graphics driver).

i downloaded the swfdec and swfdec-mozilla and went into the swfdec directory after i extracted it then typed ./configure (i already had build-essential installed), it told me a bunch of things weren't installed (like gtk, pango, mozilla, etc...) so i used synaptic to find them all (libgtk2.0-dev, etc...) and install them.
so after i found all the dependencies i tried ./configure again and had a success.  so i typed make and everything worked, finally sudo make install ... success again!

so i extract swfdec-mozilla and go into that directory and run my ./configure again, but it tells me no mozilla.  i was a bit confused because i've never compiled any browser stuff before, but i assumed firefox-dev was what it was looking for ... and it was, so bingo i install that, successfully run ./configure, followed by make and sudo make install and everything is fine.

it tells me that the plugins are located in /usr/local/lib/mozilla-firefox/plugins so i go there and see 3 files: libswfdecmozilla.a, libswfdecmozilla.la, and libswfdecmozilla.so
now i have no clue which of the three of these plugins i need (again, no prior experience at this) so i just copy and paste all three of them into /home/aaron/.mozilla/plugins then open up my epiphany browser and go to youtube ... and it works!

let me clarify "works".  i can press the play button, i can pause, i can resume from pause, the progress bar tells me how far along the video is (but no scroll, as the author said), i can replay the video after its over, the audio is in sync with the video, and it doesn't crash.  i'm incredibly pleased with this.  for the first time ever i can watch youtube on 64bit gnu/linux!

i really recommend this program to everyone!

---

### Post by saneone on 2007-03-22
could you please make packages with checkinstall?

---

### Post by aanderse on 2007-03-22
sorry ... i've uninstalled all the development libraries and deleted the code, so i can't help you out :-\

just a personal opinion though ... people should probably stop asking for binaries on forums and whatnot.  linux is only virus proof if you don't go installing viruses, this isn't an issue right now because gnu/linux has such a small userbase (relative to microsoft) but don' think that for one second when gnu/linux gains a bit more popularity it won't become a target for malicious coders.  either compile stuff by yourself or use "official" binaries because you never quite know whats in a binary of someone you don't trust. </opinion+rant>

---

### Post by chrisinator_Shuttle_XPC on 2007-03-23
well there's no real reason for it! just install normal flash w/ a linux 32 command, and have firefox32 installed through linux32 synaptic. Then you just move the .so (at least I believe thats what it is named) into the same folder in firefox normal and it runs fast and good on my Shuttle XPC

---

### Post by saneone on 2007-03-23
> **chrisinator_Shuttle_XPC said:**
> well there's no real reason for it! just install normal flash w/ a linux 32 command, and have firefox32 installed through linux32 synaptic. Then you just move the .so (at least I believe thats what it is named) into the same folder in firefox normal and it runs fast and good on my Shuttle XPC

I use firefox32 with flash9... but i wanna use FREE flash plugin, and i want to use 64 bit browser... that's why i need swfdec...

---

### Post by Trevice on 2007-03-23
version 0.4.3 has been released...

...it compiles....

and it is working!!!!


ohhh yessss, I am waching you tube videos only with FREE software!

not works perfect....but its impressive that someone archieve this with only a few months of works.....

CONGRATULATIONS!!!!!!


and sorry for my but english...

---

### Post by xopher on 2007-03-24
Nice, have to try this one out - since Adobe doesn't seem to care much of us 64-bit users. Currently Im using the latest flash (9.something) with nspluginwrapper, which actually exceeded my expectations in both usability and stability.

Earlier Ive tried Gnash and gplflash (or something like that, can't remember exactly what they were called) but neither of them worked, well they might have opened something, but there was no antialiasing etc and then suddenly fx just crashed.

---

### Post by Aldrik on 2007-03-24
Sounds great, has anyone tried it in konqueror?

Doesn't want to compile here... :(
```
../libswfdec/.libs/libswfdec-0.4.so: undefined reference to `img_convert'
collect2: ld returned 1 exit status
make[3]: *** [swfplay] Error 1
make[3]: Leaving directory `/home/me/Desktop/swfdec-0.4.3/player'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/home/me/Desktop/swfdec-0.4.3/player'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/me/Desktop/swfdec-0.4.3'
make: *** [all] Error 2
```

---

### Post by Company on 2007-03-28
The Ubuntu forums should have an option to cc me on all things swfdec... ;)
Thanks for trying and being happy with swfdec. It's very pleasing to read all the positive comments. Just to be sure, you have probably all found the properties dialog of the mozilla plugin by now?

As for the compile error: That sounds like you did something weird with your ffmpeg installation. Reinstalling libavcodec-dev (or whatever it's called exactly) should solve that - assuming you're on Feisty.
I have no idea if Swfdec works on Edgy or even older stuff. But then, noone complained to me yet, and that normally means it does work.

I'm pretty sure that swfdec will hit the unstable repos just days after Feisty is released, so if you want to try it but can't seem to make it work, you don't have to wait *that* long.

And of course I have to add the request I put everywhere: Swfdec is not supposed to crash. Ever. Because if Swfdec crashes, it brings down your browser, and that should never ever happen. So if swfdec does manage to bring down your browser, please file a bug at [https://bugs.freedesktop.org](https://bugs.freedesktop.org) including the website that made it crash. This is important in particular in the AMD64 case, because I don't have an AMD64 and might miss problems while testing.

---

### Post by Rui Pais on 2007-03-28
hi,
just out of curiosity, can this work, on a 64 bit env, simultaneosly as close flash? i mean can i have both firefox and firefox32, the fist with swfdec and the 32 version with close flash plugin?

---

### Post by saneone on 2007-03-28
> **Rui Pais said:**
> hi,
just out of curiosity, can this work, on a 64 bit env, simultaneosly as close flash? i mean can i have both firefox and firefox32, the fist with swfdec and the 32 version with close flash plugin?
unless u use nspluginwrapper for firefox64, u can have both of them - adobe flash for 32 and swfdec for 64

---

### Post by Rui Pais on 2007-03-28
hi, thanks for your answer.

Regrettably i couldn't manage to compile on edgy 64bits. 
It stops at ./configure with:
> checking for FFMPEG... no
configure: error: Couldn't find ffmpeg. You might need to install the libavcodec-dev package.

although i have libavcodec-dev and ffmped installed ...

---

### Post by johnficca on 2007-03-31
I can't get it to play youtube video no matter what I do, I finally got one video to play but the video and the sound was very choppy and bad. I booted up the live feisty beta cd and tried to compile and make on but make fails with an error 2  I don't know what that means. any help would be great.

---

### Post by kefir on 2007-04-16
```
../libswfdec/swfdec_types.h:6:19: error: cairo.h: No such file or directory
In file included from swfdec_out.h:24,
                 from swfdec_out.c:26:
../libswfdec/swfdec_color.h:68: error: expected ')' before '*' token
../libswfdec/swfdec_color.h:79: error: expected ')' before '*' token
../libswfdec/swfdec_color.h:80: warning: type defaults to 'int' in declaration of 'cairo_matrix_t'
../libswfdec/swfdec_color.h:80: error: expected ';', ',' or ')' before '*' token
../libswfdec/swfdec_color.h:81: warning: type defaults to 'int' in declaration of 'cairo_matrix_t'
../libswfdec/swfdec_color.h:81: error: expected ';', ',' or ')' before '*' token
../libswfdec/swfdec_color.h:82: warning: type defaults to 'int' in declaration of 'cairo_matrix_t'
../libswfdec/swfdec_color.h:82: error: expected ';', ',' or ')' before '*' token
In file included from swfdec_out.h:25,
                 from swfdec_out.c:26:
../libswfdec/swfdec_rect.h:26: warning: type defaults to 'int' in declaration of 'cairo_matrix_t'
../libswfdec/swfdec_rect.h:26: error: expected ';', ',' or ')' before '*' token
In file included from swfdec_out.c:26:
swfdec_out.h:81: warning: type defaults to 'int' in declaration of 'cairo_matrix_t'
swfdec_out.h:81: error: expected ';', ',' or ')' before '*' token
swfdec_out.c:272: warning: type defaults to 'int' in declaration of 'cairo_matrix_t'
swfdec_out.c:272: error: expected ';', ',' or ')' before '*' token
make[3]: *** [libswfedit_la-swfdec_out.lo] Error 1
make[3]: Leaving directory `/home/kefir/program/swfdec-0.4.3/test'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/kefir/program/swfdec-0.4.3/test'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/kefir/program/swfdec-0.4.3'
make: *** [all] Error 2
```

This is what i get when trying to compile swfdec on my 64 edgy system.
Anyone has an idea of what might be missing/wrong?

Kinda sucks to not have a working flashplayer, tried gnosh but it would only play some swf files and locked up firefox frequently.

Any help is appreciated =)

EDIT : The output indicates it would be something funny with cairo, but i have installed every single cairo-dev lib i can find and no difference =(

EDIT2 : Disregard this post i got it working by installing some more random cairo stuff with synaptic =)

---

### Post by RealityMaster on 2007-04-17
Not working for me on F F 7.04 x64..

#./configure
....

checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking for ANSI C header files... (cached) yes
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for GLIB... no
configure: error: cannot find GLIB-2.0, which is required for build
#

:confused: 

Is this in any repo's yet?

---

### Post by Company on 2007-04-18
I guess there's a reason for it, but I haven't figured it out yet: People don't read the README.

Anyway, you'll need the following development packages installed to build swfdec:
libglib2.0-dev
libgtk2.0-dev
libcairo2-dev
zlib1g-dev
libmad0-dev
liboil0.3-dev
libasound2-dev
libavcodec-dev
For swfdec-mozilla, you also need:
firefox-dev

---

### Post by RealityMaster on 2007-04-18
> **Company said:**
> I guess there's a reason for it, but I haven't figured it out yet: People don't read the README.

Anyway, you'll need the following development packages installed to build swfdec:
libglib2.0-Dev
libgtk2.0-Dev
libcairo2-Dev
zlib1g-Dev
libmad0-Dev
liboil0.3-Dev
libasound2-Dev
libavcodec-Dev
For swfdec-Mozilla, you also need:
FireFox-Dev

OK deserved, RTFM should have been my first action.  ;-) but that still wasn't enough, I also needed

libfaad2-Dev
libx264-Dev
libxvidcore-Dev
liblame-dev

Got it working after those were met, then copied the plugin files to ~/.Mozilla/plugins , restarted FF and W00T it's working!  Got You Tube!

I'm using Beryl, which makes this unusable, all white with occasional flashes of video.  When I switch back to metacity, it looks great, video with occasional flashes of white.  

Great work, and thank you for filling the gap as this was really needed.  Thanks for your assistance as well!!!

AHHH YouTube!

---

### Post by Corbelius on 2007-04-27
Feisty Fawn:

[http://janvitus.interfree.it/ubuntu/pool/feisty-janvitus/main-amd64/libswfdec0.4_0.4.3-2ubuntu1~janvitus_amd64.deb](http://janvitus.interfree.it/ubuntu/pool/feisty-janvitus/main-amd64/libswfdec0.4_0.4.3-2ubuntu1~janvitus_amd64.deb)

[http://janvitus.interfree.it/ubuntu/pool/feisty-janvitus/main-amd64/swfdec-mozilla_0.4.3-2ubuntu1~janvitus_amd64.deb](http://janvitus.interfree.it/ubuntu/pool/feisty-janvitus/main-amd64/swfdec-mozilla_0.4.3-2ubuntu1~janvitus_amd64.deb)

---

### Post by Garyu on 2007-04-27
> **Corbelius said:**
> Feisty Fawn:

[http://janvitus.interfree.it/ubuntu/pool/feisty-janvitus/main-amd64/libswfdec0.4_0.4.3-2ubuntu1~janvitus_amd64.deb](http://janvitus.interfree.it/ubuntu/pool/feisty-janvitus/main-amd64/libswfdec0.4_0.4.3-2ubuntu1~janvitus_amd64.deb)

[http://janvitus.interfree.it/ubuntu/pool/feisty-janvitus/main-amd64/swfdec-mozilla_0.4.3-2ubuntu1~janvitus_amd64.deb](http://janvitus.interfree.it/ubuntu/pool/feisty-janvitus/main-amd64/swfdec-mozilla_0.4.3-2ubuntu1~janvitus_amd64.deb)

Hey... I tried this in feisty x64... but all I get when I go to youtube is "loading"... and I am still told at flash sites that "you need to install a plugin". so, do I need to do anything else besides installing the .deb's?

EDIT: oh, I restarted Firefox, so now youtube works. BUT other sites will suddenly stop working. Like for example [www.nordnet.se](www.nordnet.se) has a list of stocks that displayed fine before, but now the list will pop up in a new window with only text, which is really annoying. So I uninstalled the mozilla .deb but then I'm back at no flash. Sigh.

---

### Post by hamil on 2007-04-28
Compiling from a fresh installed Feisty, I had to do this to get through the configure script;
```
sudo apt-get install libglib2.0-dev libgtk2.0-dev libcairo2-dev zlib1g-dev libmad0-dev liboil0.3-dev libasound2-dev libavcodec-dev firefox-dev libfaad2-dev libx264-dev libxvidcore-dev liblame-dev libgstreamer0.10-dev libgnomevfs2-dev
```

After make, I am not able to get any further. Make stops at this:
```
c -lz /usr/lib/liba52.so -ldts -lgsm /usr/lib/libmp3lame.so -lxvidcore -lx264_pic -ldc1394_control -lfaac -lfaad /usr/lib/libvorbisenc.so /usr/lib/libraw1394.so -lavutil /usr/lib/libvorbis.so /usr/lib/libogg.so /usr/lib/libgstreamer-0.10.so /usr/lib/libgobject-2.0.so /usr/lib/libgmodule-2.0.so -ldl /usr/lib/libgthread-2.0.so -lrt /usr/lib/libxml2.so /usr/lib/libglib-2.0.so -lm  -pthread -Wl,-soname -Wl,libswfdec-0.4.so.3 -Wl,-version-script -Wl,.libs/libswfdec-0.4.ver -o .libs/libswfdec-0.4.so.3.0.0
/usr/bin/ld: cannot find -lfaac
collect2: ld returned 1 exit status
make[4]: *** [libswfdec-0.4.la] Error 1
make[4]: Leaving directory `/home/lars/src/swfdec-0.4.4/libswfdec'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/home/lars/src/swfdec-0.4.4/libswfdec'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/home/lars/src/swfdec-0.4.4/libswfdec'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/lars/src/swfdec-0.4.4'
make: *** [all] Error 2
```

The author released a 0.4.4 version the other day, but have the wrong links posted at the dl site. It should be like this:
[swfdec-mozilla 0.4.4](http://swfdec.freedesktop.org/download/swfdec-mozilla/0.4/swfdec-mozilla-0.4.4.tar.gz)

---

### Post by hamil on 2007-04-29
Well, I managed to get past the compile error by adding libfaac-dev also. And the swfdec intsalled fine. But again, I had some troubles installing the mozilla plugin. I am using checkinstall for installing my applications, so that I always have a working deb file for the apps/libraries. But when I did a sudo checkinstall with the mozilla plugin. I got this error:
```
Making install in src
make[1]: Entering directory `/home/lars/src/swfdec-mozilla-0.4.4/src'
make[2]: Entering directory `/home/lars/src/swfdec-mozilla-0.4.4/src'
make[2]: Nothing to be done for `install-exec-am'.
test -z "/usr/local/lib/mozilla-firefox/plugins" || mkdir -p -- "/usr/local/lib/mozilla-firefox/plugins"
 /bin/bash ../libtool --mode=install /usr/bin/install -c  'libswfdecmozilla.la' '/usr/local/lib/mozilla-firefox/plugins/libswfdecmozilla.la'
/usr/bin/install -c .libs/libswfdecmozilla.so /usr/local/lib/mozilla-firefox/plugins/libswfdecmozilla.so
/usr/bin/install: setting permissions for `/usr/local/lib/mozilla-firefox/plugins/libswfdecmozilla.so': No such file or directory
/usr/bin/install -c .libs/libswfdecmozilla.lai /usr/local/lib/mozilla-firefox/plugins/libswfdecmozilla.la
/usr/bin/install: setting permissions for `/usr/local/lib/mozilla-firefox/plugins/libswfdecmozilla.la': No such file or directory
/usr/bin/install -c .libs/libswfdecmozilla.a /usr/local/lib/mozilla-firefox/plugins/libswfdecmozilla.a
/usr/bin/install: setting permissions for `/usr/local/lib/mozilla-firefox/plugins/libswfdecmozilla.a': No such file or directory
chmod 644 /usr/local/lib/mozilla-firefox/plugins/libswfdecmozilla.a
ranlib /usr/local/lib/mozilla-firefox/plugins/libswfdecmozilla.a
ranlib: could not create temporary file whilst writing archive: No more archived files
make[2]: *** [install-pluginLTLIBRARIES] Error 1
make[2]: Leaving directory `/home/lars/src/swfdec-mozilla-0.4.4/src'
make[1]: *** [install-am] Error 2
make[1]: Leaving directory `/home/lars/src/swfdec-mozilla-0.4.4/src'
make: *** [install-recursive] Error 1
```

I did a normal sudo make install, and it did not present me with any errors, but why I was not able to use checkinstall, I do not understand... Anyone know why?

---

### Post by samwyse on 2008-03-06
Is there a trick to get the version from the repos working? Firefox doesn't see the plugin.

---

### Post by mobiryder on 2008-04-27
thx for this thread, i just installed swfdec, via Synaptics and it works great.. 
the only issue i'm experiencing is when i load a page with flash on it, the flash is preceded by a** > Play button i have to click** to get the flash working, does anyone know how to enable all flash by default?

thx :)

---

### Post by WebChat006 on 2008-04-28
> **mobiryder said:**
> thx for this thread, i just installed swfdec, via Synaptics and it works great.. 
the only issue i'm experiencing is when i load a page with flash on it, the flash is preceded by a** > Play button i have to click** to get the flash working, does anyone know how to enable all flash by default?

thx :)


I had the same problem. I solved it by uninstalling swfdec-mozilla and then installing the Adobe flash plugin instead (when prompted by Firefox). It plays flash without any interaction. You can control this behaviour with the Flashblock extension.

---

### Post by mobiryder on 2008-04-28
> **WebChat006 said:**
> I had the same problem. I solved it by uninstalling swfdec-mozilla and then installing the Adobe flash plugin instead (when prompted by Firefox). It plays flash without any interaction. You can control this behaviour with the Flashblock extension.

i've tried a few means to get adobe installed and it just doesnt want to work for me... that script a user made doesnt work for Hardy yet either.. so i'll be using swfdec until there's another way... im happy i can at least use flash now, albeit an inconvenience to have to click every flash area on every page i go to :)

:guitar:

---

### Post by ribbon on 2008-05-02
> **mobiryder said:**
> i've tried a few means to get adobe installed and it just doesnt want to work for me... that script a user made doesnt work for Hardy yet either.. so i'll be using swfdec until there's another way... im happy i can at least use flash now, albeit an inconvenience to have to click every flash area on every page i go to :)

:guitar:

I have the same problem, adobe flash won't install for me: I deleted swfdec, went to youtube, tried to install the adobe player and I get "Package flashplugin-nonfree already" installed, even though youtube still says I don't have it and I can't watch anything of course. Then when I try to download the flash installer from the adobe website and run it, I get

```
xxx@xxxxx:/media/Files/Files/Drivers/Linux/install_flash_player_9_linux$ sudo ./flashplayer-installer 

ERROR: Your architecture, \'x86_64\', is not supported by the
       Adobe Flash Player installer.
```

/sigh

Sucks having to hit 'play' at sites like nba.com which is basically entirely in flash. Also I can't play facebook poker but swfdec and not sure how to fix it, so I blame swfdec :X

---

