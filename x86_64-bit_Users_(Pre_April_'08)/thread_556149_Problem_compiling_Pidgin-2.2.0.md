---
title: "Problem compiling Pidgin-2.2.0"
date: 2007-09-20
forum: x86 64-bit Users (Pre April '08)
---

### Post by GumbyX on 2007-09-20
I am running into problems trying to compile pidgin all of a sudden. I haven't been able to get a deb that has spell-check with it,so I decided to compile it myself (have done it before and it was easy). I installed all needed dependencies and uninstalled all .deb installed, then compiled. ./configure went fine, but when I try to make it, this is the error message I get:

```
make[5]: *** [libxmpp.la] Error 1
make[5]: Leaving directory `/home/gumby/Program (Source)/pidgin-2.2.0/libpurple/protocols/jabber'
make[4]: *** [all-recursive] Error 1
make[4]: Leaving directory `/home/gumby/Program (Source)/pidgin-2.2.0/libpurple/protocols'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/home/gumby/Program (Source)/pidgin-2.2.0/libpurple'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/home/gumby/Program (Source)/pidgin-2.2.0/libpurple'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/gumby/Program (Source)/pidgin-2.2.0'
make: *** [all] Error 2

```

I do not know why this keeps happening, but it now happens with ANY version of pidgin I download and try to compile from source. Its late and I can't really think all that well right now and have to leave for work at 6 AM, so can any of you guys help me out? I would appreciate it.

PS After thinking it was me who was screwing it up, I used this [guide]("http://jhcore.com/2007/06/04/install-pidgin-in-ubuntu/") to compile it. Anything I am doing from this guide that I shouldn't be?

---

### Post by ryno519 on 2007-09-21
Well, that guide isn't going to get the spell checker going for you. For that you will need these following packages.

libgtkspell0
aspell
aspell-en

If you get all of those installed the .deb should be able to use the spell check feature.

```
sudo apt-get install libgtkspell0 aspell aspell-en
```

Run that then restart pidgin, make sure the spell checker is enabled in the preferences and see if that works. If you still want to compile it, try the following.

```
sudo apt-get build-dep gaim
sudo apt-get install libnss-dev libgstreamer0.10-dev libgtkspell-dev aspell aspell-en
./configure
make
sudo make install
```

After the ./configure make sure there are no errors and make sure spell checking says yes.

---

### Post by GumbyX on 2007-09-21
> **ryno519 said:**
> Well, that guide isn't going to get the spell checker going for you. For that you will need these following packages.

libgtkspell0
aspell
aspell-en

If you get all of those installed the .deb should be able to use the spell check feature.

```
sudo apt-get install libgtkspell0 aspell aspell-en
```

Run that then restart pidgin, make sure the spell checker is enabled in the preferences and see if that works. If you still want to compile it, try the following.

```
sudo apt-get build-dep gaim
sudo apt-get install libnss-dev libgstreamer0.10-dev libgtkspell-dev aspell aspell-en
./configure
make
sudo make install
```

After the ./configure make sure there are no errors and make sure spell checking says yes.

I don't know why, but I keep getting the same errors as listed above. I seem to be getting warnings when it hits libpurple. Not sure why I am getting the errors now as I had no problems installing and compiling this before.

After getting all the dependencies installed, I tried the deb for 2.2.0 from getdeb and it seems to have worked. It has sound and spellcheck. I am not sure why I cannot compile from source, but as long as I got it working, I guess I can't complain. If anyone thinks they might know what the problem is, I would appreciate it if you could give me a heads up. I have been having problems with this AMD64 install and its tempting me to switch back to x86.

---

### Post by kevdog on 2007-09-24
Hmm Ive compiled pidgin on a few separate machines but all 32 bit.  Do you have the libxml-dev or the libxml2-dev package installed?  Are you running the configure statement with options or simply ./configure??

---

### Post by John.Michael.Kane on 2007-09-24
You can also download pidgin from the link below. Note: not sure if they compiled spellcheck etc into the deb.
[Pidgin Ubuntu Feisty 64 bits -  2.2.0  ]("http://www.getdeb.net/app.php?name=Pidgin")

For compiling.One of these may help.
[HowTo : Install Pidgin 2.0.0 on Ubuntu Feisty (with all plugins)]("http://ubuntuforums.org/showthread.php?t=441363&highlight=pidgin")
[Howto compile Pidgin IM]("http://ubuntuforums.org/showthread.php?t=404508&highlight=pidgin")

---

