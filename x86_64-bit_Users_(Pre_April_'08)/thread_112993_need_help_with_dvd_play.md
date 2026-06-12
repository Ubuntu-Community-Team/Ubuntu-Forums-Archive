---
title: "need help with dvd play"
date: 2006-01-05
forum: x86 64-bit Users (Pre April '08)
---

### Post by seatea on 2006-01-05
I attempted to play a dvd(s) and none of them will play properly. I can get sound from xine, but no video and the screen will turn yellow and blue and remain that way even after quitting the program. I then have to log out and log in again to straighten out the display. I ran xine-check and everything shows up as good with  the exception that "duplicate  multiple xine executables found in your PATH
         I have found more than one occurance of 'xine' in your PATH:
         /usr/bin/X11/xine
         /usr/bin/xine
         You have probably installed xine-ui more than once, or the directory
         where you have installed xine occurs more than once in your PATH.
         Technically, this is not really a problem, but it's probably
         somewhat confusing, as it's not obvious, which xine you're using.
         You should probably uninstall the copies that you don't use...
         Further tests assume, you're using /usr/bin/X11/xine"
and
" several instances of xine-config found in your PATH
         xine-config executables have been found in these places:
         /usr/bin/X11/xine-config
         /usr/bin/xine-config
         This probably means you have several versions of xine-lib installed.
         It's probably best to uninstall all unused xine-libs.
         Further tests will use /usr/bin/X11/xine-config."

I have not removed anything though.

I believe my regionset is ok and I have followed the  instructions in  the wiki for dvd playback, but no video and my display messes up each time. All repositories in my sources list have been added that are available. Totem and other players just freeze or quit and do nothing except change the display to yellow and blue.  Any advice?

Thanks

Addendum: I forgot to include in the original post: PM G4 400 Gigabit with standard ATI Rage 128.

---

### Post by tmeier on 2006-01-05
My first idea would be to use Synaptic and completely remove totem and xine and then re-install which ever is your preference and see if that helps any.  A place to start anyway.

---

### Post by dombleu on 2006-01-05
Have a look at:

[http://download.videolan.org/pub/libdvdcss/](http://download.videolan.org/pub/libdvdcss/)

download and compile and install.

In other words:

get to the directory were you downloaded libdvdcss-1.2.9.tar.gz

```
$ tar zxvf libdvdcss-1.2.9.tar.gz
$ cd libdvdcss-1.2.9
$ ./configure
$ make
$ sudo make install
```

That being done I was able to play dvds, even encrypted ones on my powerbook G4 12". But my success was limited to xine. I guess some configuration tweaks with vlc or mplayer should do the trick but anyway... If that can help, you can install xine by doing;

```
sudo apt-get install gxine
```

Hope this help!
dom

Edit: And by the way, my xine-check complains on my side too about multiple executables. Who cares! It works fine like it is....

---

### Post by seatea on 2006-01-06
Thanks for taking the time to offer your suggestions.

I removed every DVD player I had installed. I downloaded and installed libdvdcss-1.2.9.tar.gzm installed gxine and, after it did not work, xine, then tried to play a DVD again. I had no luck. The sound played in xine, not in gxine which quit unexpectedly, with no picture and left my  display colored yellow and blue again, but usable. What can I do now?

---

