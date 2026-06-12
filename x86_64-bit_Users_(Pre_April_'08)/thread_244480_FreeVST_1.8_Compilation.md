---
title: "FreeVST 1.8 Compilation"
date: 2006-08-26
forum: x86 64-bit Users (Pre April '08)
---

### Post by coder_ on 2006-08-26
Well, I've been trying all day to get FreeVST 1.8 to compile, and I've run into a brick wall of what to do next.  :/

I've been going at it all day getting the right dependencies (a lot!!) and compiling programs not available by apt-get or Synaptic by source (namely lash, which was also a pain).  I've been fixing all the errors, but last time I tried I got "No package 'gtk+-2.0' found" so I ran "sudo apt-get install libgtk2.0-dev" and now all of a sudden, I don't get any package errors, just this. I don't know what I need to do next to make it work... Any ideas?

```

$ make
cp -a `find . | grep 'vstsdk[^/]*\$'`/source/common ./vst
sed -i '/struct VstFileType\|struct VstFileSelect/,/};/d' vst/aeffectx.h
winegcc -c  `pkg-config --cflags gtk+-2.0` `pkg-config --cflags jack` `pkg-config --cflags jack` `pkg-config --cflags lash-1.0` -DHAVE_LASH -I.   -o audiomaster.o audiomaster.c
winegcc: i486-linux-gnu-gcc failed.
make: *** [audiomaster.o] Error 2

```

That's my whole entire make output now :S

Just in case it matters, I'm running Ubuntu Dapper Drake 64 bit Edition.


EDIT: Now that I look at it later, maybe I should have posted this somewhere else?

---

### Post by coder_ on 2006-08-27
*Bump*

Anyone?  :'(   Still no luck.

---

### Post by RAOF on 2006-08-27
What is FreeVST, and why is it using winegcc?  Is it a Windows program?

---

### Post by coder_ on 2006-08-27
FreeVST is a way to use VST plugins (developed by Steinberg) under Linux with WINE and the JACK audio server.  (Maybe a mod could move this to the Ubuntu Studio Forum category?)  So it's like, half a Windows program, half Linux ;)

Some VST links to people who may be interested/want more info:
[http://en.wikipedia.org/wiki/Virtual_Studio_Technology](http://en.wikipedia.org/wiki/Virtual_Studio_Technology) - VST
[http://quicktoots.linuxaudio.org/toots/vst-plugins/](http://quicktoots.linuxaudio.org/toots/vst-plugins/) - VST under Linux
[http://joebutton.co.uk/fst/](http://joebutton.co.uk/fst/) - FreeVST Project

---

### Post by RAOF on 2006-08-27
> **coder_ said:**
> FreeVST is a way to use VST plugins (developed by Steinberg) under Linux with WINE and the JACK audio server.  (Maybe a mod could move this to the Ubuntu Studio Forum category?)  So it's like, half a Windows program, half Linux ;)
...
Eeep!  That means that you'll be trying to link wine code with native gtk code?  Ugh.  Probably the problem you're having is that you'll need to build 32bit code (so that it links with wine, which is 32bit).  This means that all the things you want to link with have to be 32bit - you'll need 32bit gtk libraries, etc.

But looking at it, it seems that the current problem is that it can't find i486-linux-gnu-gcc.  You could **possibly** fix that one problem by creating a shell script:
```

#!/bin/sh
/usr/bin/gcc -m32 $@

```
and saving it as **/usr/bin/i486-linux-gnu-gcc**.  That might work long enough for other problems to come along :-|

---

### Post by coder_ on 2006-08-28
Thanks a ton for replying and trying to help, but that didn't seem to do the trick.. :/

I'll just do my VST stuff on my Winblowze laptop...

---

