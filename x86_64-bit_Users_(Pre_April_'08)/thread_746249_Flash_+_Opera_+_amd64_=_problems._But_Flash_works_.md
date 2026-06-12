---
title: "Flash + Opera + amd64 = problems. But Flash works fine in Firefox"
date: 2008-04-05
forum: x86 64-bit Users (Pre April '08)
---

### Post by kung fu buntu on 2008-04-05
I launch Opera from the command line and when I open a video in youtube this is what I get:> ERROR: ld.so: object '/usr/lib/libartsdsp.so.0' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib/libartsc.so.0' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib/libartsdsp.so.0' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib/libartsc.so.0' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib/libartsdsp.so.0' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib/libartsc.so.0' from LD_PRELOAD cannot be preloaded: ignored.

(npviewer.bin:12040): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/immodules/im-uim.so: wrong ELF class: ELFCLASS64

(npviewer.bin:12040): Gtk-WARNING **: Loading IM context type 'uim' failed

(npviewer.bin:12040): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/immodules/im-uim.so: wrong ELF class: ELFCLASS64
The strange thing is that the audio (from the flash video) works fine... I just can't seem the image... and the page gets all messed up instead.
Another thing I don't understand is why does it complain about arts when I'm using ALSA (at least I would like to).
BTW, UIM is a package that allows me to write in &#26085;&#26412;&#35486;.

When I close the youtube tab this is what I get:> (npviewer.bin:12040): Gtk-WARNING **: Loading IM context type 'uim' failed
The program 'npviewer.bin' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadWindow (invalid Window parameter)'.
  (Details: serial 82639 error_code 3 request_code 2 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

My dmesg:> npviewer.bin[8090]: segfault at 00000000f5d02030 rip 00000000f79a90e0 rsp 00000000ffeedd80 error 4
operapluginwrap[8035]: segfault at 0000000000000000 rip 0000000000410678 rsp 00007fffbf406360 error 4
operapluginwrap[11179]: segfault at 0000000000000000 rip 0000000000410678 rsp 00007fffc24cd420 error 4
operapluginwrap[11266]: segfault at 0000000000000000 rip 0000000000410678 rsp 00007fff174553b0 error 4
operapluginwrap[11346]: segfault at 0000000000000000 rip 0000000000410678 rsp 00007fff4ba819d0 error 4
operapluginwrap[11425]: segfault at 0000000000000000 rip 0000000000410678 rsp 00007fffb4fcef20 error 4

I have installed on my system the latest version of:
ia32-libs ia32-libs-gtk linux32 lib32asound2
nspluginwrapper (0.9.91.5-2) 
flashplayer-mozilla (9.0.115.0-0.4)
opera (9.50 Beta 2 build 1875 - [http://ubuntuforums.org/showthread.php?t=597609&page=2](http://ubuntuforums.org/showthread.php?t=597609&page=2))

Any ideas?
Thank you.

---

### Post by jpkotta on 2008-04-05
Are you using a 64-bit opera with 32-bit flash?  I'm pretty certain that won't work.

---

### Post by kung fu buntu on 2008-04-06
> **jpkotta said:**
> Are you using a 64-bit opera with 32-bit flash?  I'm pretty certain that won't work.That is true for Opera, but not true for Firefox! So there must be a way!

---

### Post by olmari on 2008-04-06
What Opera version? Newer snapshot releases of Opera 9.5 codename Kestrel 64-bit builds does work natively with 32-bit plugins, so everything you need to do is to copy or symlink the libflashplayer.so to /usr/lib/opera/plugins directory...

And also have ia32-libs installed as operapluginwrapper needs it for 32-bit plugins (otherwise Opera behaves like no [32-bit] plugins exists)...

Look for the releases here: [http://my.opera.com/desktopteam/blog/](http://my.opera.com/desktopteam/blog/) Allways newest one available :)

P.S. In case you didn't noticed, Kestrel has native 64-bit builds too...

---

### Post by kung fu buntu on 2008-04-07
I have flash working... but I still have problem.
I opened a thread some days ago at [Opera's forum]("http://my.opera.com/community/forums/topic.dml?id=228511&t=1207417322") and it was with their help that I got flash working.

finance.google.com doesn't work, and youtube doesn't load up properly.
Besides that, I also have problems with Java :(
It seems Sun doesn't support 64bits systems very well :(

I have a 64bit build of Opera and likely a newer version than yours (not necessarily better).
[Opera amd64 18-Mar-2008]("http://snapshot.opera.com/unix/snapshot-1875/x86_64-linux/")

---

### Post by olmari on 2008-04-07
I have 1887... I have allways newest atleast until first 64-bit stable ;) As said allways available from the Desktop team blog, + some flash related fixes again on latest one...

---

### Post by kung fu buntu on 2008-04-07
You are correct :)
I now have that version.

Build 1887 solves the youtube problem (of the "html" not loading properly).
However finance.google.com still doesn't work properly.
In adobe.com the menus still get behind the banner (so you can't do anything) 

And I'm still unable to get java working

---

