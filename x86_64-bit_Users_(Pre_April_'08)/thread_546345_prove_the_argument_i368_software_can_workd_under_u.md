---
title: "prove the argument: i368 software can workd under ubuntu64"
date: 2007-09-08
forum: x86 64-bit Users (Pre April '08)
---

### Post by tetrafuran on 2007-09-08
nothing any more. I searched but didn't find what was already in a sticky. I just realized that a little too late. Sorry for terrorizing the forum like this.

---

### Post by Kilz on 2007-09-08
> **tetrafuran said:**
> Some people say 386 software can be used under 64bit ubuntu. I've come across tons of malfunctioning software and ended up simply abandoning them when they had the wrong architecture. Such software are: aMSN, wine, xnee and so on. I can live without most of them, but gettin xnee working would be really cool.

Xnee is a program for recording and replaying mouse and keyboard actions. This means that if I record myself opening a browser and checking my various e-mail accounts, I could later on perform all these various steps with just a click of a button. Of course this is just an example for illustrating the point. I would probably be using xnee for multi step image manipulation operations in gimp and other interesting experiments.

The problem is that the repositories contain an ancient (but functioning) version of xnee. The latest version is available on [http://www.sandklef.com/xnee/?q=node/17]("http://www.sandklef.com/xnee/?q=node/17")

It just happens to be i386 architecture and therefore uninstallable as far as my skills go. Now smarter people have an opportunity to prove their arguments about 368 software working under a 64 bit OS. I haven't seen it done. In fact I've faced this problem so many times that I'm beginning to consider... well, no, not really. I can still bare it. But it's still farely disturbing to read "wrong architecture" on error messages every week.

My suggestion is to [search the package site ]("http://packages.ubuntu.com/")before posting another of these posts saying something doesnt exist.
You might want to take a look at the [Xnee page]("http://packages.ubuntu.com/feisty/x11/xnee") on the package site and look at the bottom of the page. You will notice there is a AMD64 package. Since that package has a page nd download, you can use Synaptic to install it.
Wine is avilable from the Winehq. A search , or a look at the stickies would give you a link in seconds. aMSN also has [a page on the package site]("http://packages.ubuntu.com/feisty/x11/amsn"), and a 64bit package. A search in Synaptic brings it up.

---

### Post by tetrafuran on 2007-09-08
Thanks anyway.
Unfortunately I'll have to tell you some bad news.
1) The 64 xnee is the old one I mentioned. It is so ancient that it's barely usable. The new shiny and very usable one just happens to be unusable.
2) I forced the new xnee with dpkg -i --force-architecture and it didn't work. Obviously it just wasn't designed to. It installed but running the program was impossible.
3) The 64 bit wine is not for edgy. It is available on feisty.
4) aMSN. Some months ago I found out that the latest version cannot be installed in 64 bit, however the old useless one can. Unfortunately it doesn't have the "speaking" feature so I might as well use gaim.

4b) Now it's installed. Still the same problems as usual. I is the old version. Therefore it constantly complains about updates that are uninstallable and it lacks the key feature I'm looking for.

---

### Post by tomdkat on 2007-09-08
Does Opera 9.23 for Linux count?  If you download the standard Deb from the Opera site and try to install it directly it won't install due to it being an i386 architecture package.  Installing using the "dpkg -i --force-architecture" command works and Opera does run.  Do you need a screenshot as evidence?    :)

Also, check out the "Simple64" thread in this forum to learn about the script used to install many i386 packages in a 64-bit Ubuntu system.

EDIT:  As for your aMsn issue, can you use [Pidgin](http://pidgin.im/)?  I use Pidgin to chat via MSN, AIM, and Yahoo! Messenger all the time and at the same time.

Peace...

---

### Post by Kilz on 2007-09-08
> **tetrafuran said:**
> Thanks anyway.
Unfortunately I'll have to tell you some bad news.
1) The 64 xnee is the old one I mentioned. It is so ancient that it's barely usable. The new shiny and very usable one just happens to be unusable.
2) I forced the new xnee with dpkg -i --force-architecture and it didn't work. Obviously it just wasn't designed to. It installed but running the program was impossible.
3) The 64 bit wine is not for edgy. It is available on feisty.
4) aMSN. Some months ago I found out that the latest version cannot be installed in 64 bit, however the old useless one can. Unfortunately it doesn't have the "speaking" feature so I might as well use gaim.

4b) Now it's installed. Still the same problems as usual. I is the old version. Therefore it constantly complains about updates that are uninstallable and it lacks the key feature I'm looking for.

1 and 2. That the packages are old is a problem that is shared with 32bit. What errors did you get when you tried running xnee? What steps did you do to solve those problems?
3. I have a solution for wine, Upgrade to Feisty. Its much better than Edgy IMHO. You could also read the sticky posts if you want to run Edgy.
4.Upgrading to Feisty would bring you up to version .96. Its also possible to compile and  run .97rc1 from the downloadable source. You will need to install tcltls, tcl8.4-dev, and tk8.4-dev. Then ./configure then make, then sudo make install.

---

### Post by Yellow Pasque on 2007-09-08
I would suggest upgrading to Feisty as well (or waiting for the October release of Gutsy). But if you can't there's an easy fix to get the 32-bit version of wine running:
[http://wiki.winehq.org/UbuntuAMD64](http://wiki.winehq.org/UbuntuAMD64)

---

### Post by Kilz on 2007-09-08
There are better howto's in the stickies for Wine. Of course that would take the original poster looking there, the main reason I mentioned them instead of just linking to it.

---

### Post by Sayers on 2007-09-08
368 software wont work anywhere. It is 386 and considered X86 now adays. However cant you just compile the software in amd64 to get it to work?

---

### Post by Cappy on 2007-09-08
All 32-bit programs can be run on 64-bit with getlibs:
[http://ubuntuforums.org/showthread.php?t=474790](http://ubuntuforums.org/showthread.php?t=474790)

If you have a problem with a piece of 32-bit software you should just post the errors you get so someone can actually help.

---

### Post by John.Michael.Kane on 2007-09-08
> **Sayers said:**
> 368 software wont work anywhere. It is 386 and considered X86 now adays. However cant you just compile the software in amd64 to get it to work?

On the contrary i386 aka 32bit software can be run in a 64bit environment provided all the dependencies for those programs are met.

One example of i386/32bit program running under 64bit is Kilz guide for installing 32 bit Firefox with Flash w/sound and Java for AMD64.

---

### Post by Kilz on 2007-09-08
> **SD-Plissken said:**
> On the contrary i386 aka 32bit software can be run in a 64bit environment provided all the dependencies for those programs are met.

One example of i386/32bit program running under 64bit is Kilz guide for installing ```
32 bit Firefox with Flash w/sound and Java for AMD64
```.

Which may be on the verge of becoming obsolete.  :D  I am currently testing the Blackdown java in 64bit Swiftweasel and its very stable.

---

### Post by John.Michael.Kane on 2007-09-08
> **Kilz said:**
> Which may be on the verge of becoming obsolete.  :D  I am currently testing the Blackdown java in 64bit Swiftweasel and its very stable.

That would be very cool. I guess an alpha-test script will be coming soon..

---

### Post by tetrafuran on 2007-09-09
> "1 and 2. That the packages are old is a problem that is shared with 32bit. What errors did you get when you tried running xnee? What steps did you do to solve those problems?"

I got a whole pile of errors. Wan't to see? actually what I want to run is gnee. It's usefull little program that gives xnee a GUI. Anyway here's what happened I said gnee and terminal replied:


```
(process:5112): Gdk-WARNING **: locale not supported by C library

(gnee:5112): Gtk-WARNING **: Locale not supported by C library.
        Using the fallback 'C' locale.

** (gnee:5112): WARNING **: Couldn't find pixmap file: xnee128.xpm
*** glibc detected *** gnee: free(): invalid next size (fast): 0x08333fa0 ***
======= Backtrace: =========
/lib32/libc.so.6[0xf77e747d]
/lib32/libc.so.6(__libc_free+0x84)[0xf77e7604]
gnee(vfprintf+0x65c)[0x804cbdc]
/lib32/libc.so.6(__libc_start_main+0xdc)[0xf77958cc]
gnee(vfprintf+0x221)[0x804c7a1]
======= Memory map: ========
08048000-08083000 r-xp 00000000 03:01 7646012                            /usr/bin/gnee
08083000-0808d000 rw-p 0003a000 03:01 7646012                            /usr/bin/gnee
0808d000-0834c000 rw-p 0808d000 00:00 0                                  [heap]
f5a00000-f5a21000 rw-p f5a00000 00:00 0 
f5a21000-f5b00000 ---p f5a21000 00:00 0 
f5b58000-f5b62000 r-xp 00000000 03:01 9241565                            /usr/lib32/libgcc_s.so.1
f5b62000-f5b63000 rw-p 00009000 03:01 9241565                            /usr/lib32/libgcc_s.so.1
f5b73000-f5bdf000 r--p 00000000 03:01 7880837                            /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans-Bold.ttf
f5bdf000-f5e81000 r--p 00000000 03:01 2834450                            /usr/share/icons/hicolor/icon-theme.cache
f5e81000-f6f69000 r--p 00000000 03:01 9158885                            /usr/share/icons/crystalsvg/icon-theme.cache
f6f69000-f75ca000 r--p 00000000 03:01 7979099                            /usr/share/icons/gnome/icon-theme.cache
f75ca000-f763b000 r--p 00000000 03:01 7880841                            /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans.ttf
f763b000-f764c000 r-xp 00000000 03:01 9241899                            /usr/lib32/gtk-2.0/2.10.0/engines/libubuntulooks.so
f764c000-f764d000 rw-p 00011000 03:01 9241899                            /usr/lib32/gtk-2.0/2.10.0/engines/libubuntulooks.so
f764d000-f7656000 r-xp 00000000 03:01 2474013                            /lib32/libnss_files-2.4.so
f7656000-f7658000 rw-p 00008000 03:01 2474013                            /lib32/libnss_files-2.4.so
f7658000-f7660000 r-xp 00000000 03:01 2474015                            /lib32/libnss_nis-2.4.so
f7660000-f7662000 rw-p 00007000 03:01 2474015                            /lib32/libnss_nis-2.4.so
f7662000-f7674000 r-xp 00000000 03:01 2474010                            /lib32/libnsl-2.4.so
f7674000-f7676000 rw-p 00011000 03:01 2474010                            /lib32/libnsl-2.4.so
f7676000-f7678000 rw-p f7676000 00:00 0 
f7678000-f767f000 r-xp 00000000 03:01 2474011                            /lib32/libnss_compat-2.4.so
f767f000-f7681000 rw-p 00006000 03:01 2474011                            /lib32/libnss_compat-2.4.so
f7681000-f7683000 rw-p f7681000 00:00 0 
f7683000-f768a000 r-xp 00000000 03:01 2474020                            /lib32/librt-2.4.so
f768a000-f768c000 rw-p 00006000 03:01 2474020                            /lib32/librt-2.4.so
f768c000-f7690000 r-xp 00000000 03:01 9241634                            /usr/lib32/libXdmcp.so.6.0.0
f7690000-f7691000 rw-p 00003000 03:01 9241634                            /usr/lib32/libXdmcp.so.6.0.0
f7691000-f7692000 rw-p f7691000 00:00 0 
f7692000-f76b4000 r-xp 00000000 03:01 9241611                            /usr/lib32/libpng12.so.0.1.2.8
f76b4000-f76b5000 rw-p 00021000 03:01 9241611                            /usr/lib32/libpng12.so.0.1.2.8
f76b5000-f76b7000 r-xp 00000000 03:01 9241632                            /usr/lib32/libXau.so.6.0.0
f76b7000-f76b8000 rw-p 00001000 03:01 9241632                            /usr/lib32/libXau.so.6.0.0
f76b8000-f76d4000 r-xp 00000000 03:01 9241581                            /usr/lib32/libexpat.so.1.0.0
f76d4000-f76d6000 rw-p 0001c000 03:01 9241581                            /usr/lib32/libexpat.so.1.0.0
f76d6000-f76e9000 r-xp 00000000 03:01 9241568                            /usr/lib32/libz.so.1.2.3
f76e9000-f76ea000 rw-p 00012000 03:01 9241568                            /usr/lib32/libz.so.1.2.3
f76ea000-f7751000 r-xp 00000000 03:01 9241583                            /usr/lib32/libfreetype.so.6.3.10
f7751000-f7754000 rw-p 00067000 03:01 9241583                            /usr/lib32/libfreetype.so.6.3.10
f7754000-f7755000 rw-p f7754000 00:00 0 
f7755000-f777f000 r-xp 00000000 03:01 9241999                            /usr/lib32/libpangoft2-1.0.so.0.1400.5
f777f000-f7780000 rw-p 00029000 03:01 9241999                            /usr/lib32/libpangoft2-1.0.so.0.1400.5
f7780000-f78ad000 r-xp 00000000 03:01 2474004                            /lib32/libc-2.4.so
f78ad000-f78af000 r--p 0012c000 03:01 2474004                            /lib32/libc-2.4.so
f78af000-f78b1000 rw-p 0012e000 03:01 2474004                            /lib32/libc-2.4.so
f78b1000-f78b4000 rw-p f78b1000 00:00 0 
f78b4000-f78c3000 r-xp 00000000 03:01 2474018                            /lib32/libpthread-2.4.so
f78c3000-f78c5000 rw-p 0000f000 03:01 2474018                            /lib32/libpthread-2.4.so
f78c5000-f78c7000 rw-p f78c5000 00:00 0 
f78c7000-f78cb000 r-xp 00000000 03:01 9241647                            /usr/lib32/libXtst.so.6.1.0
f78cb000-f78cc000 rw-p 00003000 03:01 9241647                            /usr/lib32/libXtst.so.6.1.0
f78cc000-f795d000 r-xp 00000000 03:01 9241601                            /usr/lib32/libglib-2.0.so.0.1200.4
f795d000-f795e000 rw-p 00091000 03:01 9241601                            /usr/lib32/libglib-2.0.so.0.1200.4
f795e000-f795f000 rw-p f795e000 00:00 0 
f795f000-f7961000 r-xp 00000000 03:01 2474007                            /lib32/libdl-2.4.so
f7961000-f7963000 rw-p 00001000 03:01 2474007                            /lib32/libdl-2.4.so
f7963000-f7966000 r-xp 00000000 03:01 9241603                            /usr/lib32/libgmodule-2.0.so.0.1200.4
f7966000-f7967000 rw-p 00002000 03:01 9241603                            /usr/lib32/libgmodule-2.0.so.0.1200.4
f7967000-f79a0000 r-xp 00000000 03:01 9241602                            /usr/lib32/libgobject-2.0.so.0.1200.4
f79a0000-f79a1000 rw-p 00038000 03:01 9241602                            /usr/lib32/libgobject-2.0.so.0.1200.4
f79a1000-f7a67000 r-xp 00000000 03:01 9241622                            /usr/lib32/libX11.so.6.2.0
f7a67000-f7a6a000 rw-p 000c5000 03:01 9241622                            /usr/lib32/libX11.so.6.2.0
f7a6a000-f7aca000 r-xp 00000000 03:01 9241578                            /usr/lib32/libcairo.so.2.9.2
f7aca000-f7acc000 rw-p 0005f000 03:01 9241578                            /usr/lib32/libcairo.so.2.9.2
f7acc000-f7b04000 r-xp 00000000 03:01 9241997                            /usr/lib32/libpango-1.0.so.0.1400.5
f7b04000-f7b06000 rw-p 00037000 03:01 9241997                            /usr/lib32/libpango-1.0.so.0.1400.5
f7b06000-f7b07000 rw-p f7b06000 00:00 0 
f7b07000-f7b0b000 r-xp 00000000 03:01 9242003                            /usr/lib32/libXfixes.so.3.1.0
f7b0b000-f7b0c000 rw-p 00003000 03:01 9242003                            /usr/lib32/libXfixes.so.3.1.0
f7b0c000-f7b14000 r-xp 00000000 03:01 9242002                            /usr/lib32/libXcursor.so.1.0.2
f7b14000-f7b15000 rw-p 00007000 03:01 9242002                            /usr/lib32/libXcursor.so.1.0.2
f7b15000-f7b17000 r-xp 00000000 03:01 9241643                            /usr/lib32/libXrandr.so.2.0.0
f7b17000-f7b18000 rw-p 00002000 03:01 9241643                            /usr/lib32/libXrandr.so.2.0.0
f7b18000-f7b1f000 r-xp 00000000 03:01 9241636                            /usr/lib32/libXi.so.6.0.0
f7b1f000-f7b20000 rw-p 00006000 03:01 9241636                            /usr/lib32/libXi.so.6.0.0
f7b20000-f7b22000 r-xp 00000000 03:01 9241637                            /usr/lib32/libXinerama.so.1.0.0
f7b22000-f7b23000 rw-p 00001000 03:01 9241637                            /usr/lib32/libXinerama.so.1.0.0
f7b23000-f7b2a000 r-xp 00000000 03:01 9241644                            /usr/lib32/libXrender.so.1.3.0
f7b2a000-f7b2b000 rw-p 00006000 03:01 9241644                            /usr/lib32/libXrender.so.1.3.0
f7b2b000-f7b2c000 rw-p f7b2b000 00:00 0 
f7b2c000-f7b38000 r-xp 00000000 03:01 9241635                            /usr/lib32/libXext.so.6.4.0
f7b38000-f7b39000 rw-p 0000c000 03:01 9241635                            /usr/lib32/libXext.so.6.4.0
f7b39000-f7b62000 r-xp 00000000 03:01 9241582                            /usr/lib32/libfontconfig.so.1.0.4
f7b62000-f7b67000 rw-p 00028000 03:01 9241582                            /usr/lib32/libfontconfig.so.1.0.4
f7b67000-f7b68000 rw-p f7b67000 00:00 0 
f7b68000-f7b6f000 r-xp 00000000 03:01 9242001                            /usr/lib32/libpangocairo-1.0.so.0.1400.5
f7b6f000-f7b70000 rw-p 00006000 03:01 9242001                            /usr/lib32/libpangocairo-1.0.so.0.1400.5
f7b70000-f7b94000 r-xp 00000000 03:01 2474008                            /lib32/libm-2.4.so
f7b94000-f7b96000 rw-p 00023000 03:01 2474008                            /lib32/libm-2.4.so
f7b96000-f7bab000 r-xp 00000000 03:01 9241976                            /usr/lib32/libgdk_pixbuf-2.0.so.0.1000.6
f7bab000-f7bac000 rw-p 00015000 03:01 9241976                            /usr/lib32/libgdk_pixbuf-2.0.so.0.1000.6
f7bac000-f7bc4000 r-xp 00000000 03:01 9241952                            /usr/lib32/libatk-1.0.so.0.1213.0
f7bc4000-f7bc6000 rw-p 00017000 03:01 9241952                            /usr/lib32/libatk-1.0.so.0.1213.0
f7bc6000-f7bc7000 rw-p f7bc6000 00:00 0 
f7bc7000-f7c48000 r-xp 00000000 03:01 9241977                            /usr/lib32/libgdk-x11-2.0.so.0.1000.6
f7c48000-f7c4b000 rw-p 00081000 03:01 9241977                            /usr/lib32/libgdk-x11-2.0.so.0.1000.6
f7c4b000-f7f94000 r-xp 00000000 03:01 9241978                            /usr/lib32/libgtk-x11-2.0.so.0.1000.6
f7f94000-f7f9a000 rw-p 00349000 03:01 9241978                            /usr/lib32/libgtk-x11-2.0.so.0.1000.6
f7f9a000-f7f9b000 rw-p f7f9a000 00:00 0 
f7fa5000-f7fa7000 r-xp 00000000 03:01 9241989                            /usr/lib32/pango/1.5.0/modules/pango-basic-fc.so
f7fa7000-f7fa8000 rw-p 00001000 03:01 9241989                            /usr/lib32/pango/1.5.0/modules/pango-basic-fc.so
f7fa8000-f7fa9000 r-xp 00000000 03:01 9241503                            /usr/lib32/gconv/ISO8859-1.so
f7fa9000-f7fab000 rw-p 00001000 03:01 9241503                            /usr/lib32/gconv/ISO8859-1.so
f7fab000-f7fad000 rw-p f7fab000 00:00 0 
f7fad000-f7fc8000 r-xp 00000000 03:01 2474001                            /lib32/ld-2.4.so
f7fc8000-f7fca000 rw-p 0001b000 03:01 2474001                            /lib32/ld-2.4.so
ffa3f000-ffa4a000 rw-p ffa3f000 00:00 0                                  [stack]
ffffe000-fffff000 r-xp ffffe000 00:00 0 
Aborted (core dumped)
```

I didn't really understand anything so I didn't do anything about it, (besides giving up).

> 3. I have a solution for wine, Upgrade to Feisty. Its much better than Edgy IMHO. You could also read the sticky posts if you want to run Edgy.

Yes. I've been thinking of feisty... Perhaps I should. 

Perhaps compiling could help a lot of issues. I never really read much about the whole procedure. I'm planning to eventually.

Installing the appropriate 32 libraries was the first thing I did a long time a go.

---

### Post by Kilz on 2007-09-09
> **tetrafuran said:**
> I got a whole pile of errors. Wan't to see? actually what I want to run is gnee. It's usefull little program that gives xnee a GUI. Anyway here's what happened I said gnee and terminal replied:


I didn't really understand anything so I didn't do anything about it, (besides giving up).



Yes. I've been thinking of feisty... Perhaps I should. 

Perhaps compiling could help a lot of issues. I never really read much about the whole procedure. I'm planning to eventually.

Installing the appropriate 32 libraries was the first thing I did a long time a go.

downloading  a source tarball, extracting it, opening a terminal , navigating to the folder, and Typing 
```
./configure
 make
 sudo make install
``` isnt that hard. Compiling an applications is a benefit of Linux in general and can solve a lot of the problems dealing with old applications.

---

### Post by NullHead on 2007-09-09
make shure to search the "INSTALL" file located inside the folder and look for the dependencies first and and just making shure you have them all first.

---

### Post by brharri1 on 2007-09-09
> Which may be on the verge of becoming obsolete.  I am currently testing the Blackdown java in 64bit Swiftweasel and its very stable.

Kilz, be sure and let us hear your opinions after you've had enough time with it; very curious to know!

---

