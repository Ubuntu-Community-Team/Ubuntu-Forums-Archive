---
title: "Codecs for Media files."
date: 2009-07-07
forum: x86 64-bit Users
---

### Post by Chase Young on 2009-07-07
**NOTE: MANY OF YOU WILL KNOW THIS IS ALSO CALLED UBUNTU-RESTRICTED-EXTRAS**

Hey there. I've first registered a long time ago when I was using my old computer, but now I bought a new laptop =) It's a 64-bit, which is why I'm in this particular board, but I'm having problems installing the codecs for things like .mp3, .mpeg, etc. This is what happens:

I'll go to my old music folder (Windows, uuck), and open a file. Obviously, it doesn't open. It requests I download the new codecs in order to play the file (this applies with music and movies). It opens up a screen with two codecs available. I'll select them both, and then it asks me to confirm, I click OK. It then attempts to install, but after about  seconds, this happens:
```


E: Could not get lock /var/cache/apt/archives/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the download directory

```

EDIT - FIXED THAT PROBLEM.

I have another, though lol


After I install those, my music still doesn't play. What's going on? :S

P.S. Off topic, but I also can't use conpizconfig becuase I don't have the right drivers for my Nvidia graphics card. I tried the whole System/administrator/hardware thing, but it just searches for a long time and doesn't find anything.

---

### Post by dabl on 2009-07-08
That is what ... THREE problems in one post?    LOL

OK, solution to multimedia issues is, follow this:

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

Solution to downloading and installing the nVidia driver is here:

[http://kubuntuforums.net/forums/index.php?topic=3100807.msg164892#msg164892](http://kubuntuforums.net/forums/index.php?topic=3100807.msg164892#msg164892)

disregard the version number in that thread -- just follow the process.  Current nVidia driver for newish cards is 185.18.14.

---

### Post by freackout on 2009-07-13
> **dabl said:**
> That is what ... THREE problems in one post?    LOL

OK, solution to multimedia issues is, follow this:

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

Solution to downloading and installing the nVidia driver is here:

[http://kubuntuforums.net/forums/index.php?topic=3100807.msg164892#msg164892](http://kubuntuforums.net/forums/index.php?topic=3100807.msg164892#msg164892)

disregard the version number in that thread -- just follow the process.  Current nVidia driver for newish cards is 185.18.14.

here is a more exact hands on approach for mostly all codecs [http://juliensimon.blogspot.com/2008/12/howto-compiling-vlc-with-all-major.html](http://juliensimon.blogspot.com/2008/12/howto-compiling-vlc-with-all-major.html) with a very good explanations. just copy/paste. + you get vlc 1.0

---

### Post by freackout on 2009-07-13
> **freackout said:**
> here is a more exact hands on approach for mostly all codecs [http://juliensimon.blogspot.com/2008/12/howto-compiling-vlc-with-all-major.html](http://juliensimon.blogspot.com/2008/12/howto-compiling-vlc-with-all-major.html) with a very good explanations. just copy/paste. + you get vlc 1.0

try EnvyNG for both nvidia and ati cards its simple click n go, no messing without x while installing ect.

---

