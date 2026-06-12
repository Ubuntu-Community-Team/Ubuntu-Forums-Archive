---
title: "Unable to install Flashplayer 64 on Firefox 3.1 b2"
date: 2009-01-22
forum: x86 64-bit Users
---

### Post by herve34fr on 2009-01-22
Hi,
I'm running Intrepid 64 and I have allready installed without any problem FlashPlayer 10 64 bits.
I copied the file as indicated in the forum : 
**/usr/lib/mozilla/plugins/libflashplayer.so**

Now, I'm trying to install Firefox 3.1 beta 2. 
I downloaded the file from mozilla,decompressed and installed in my home by creating a "firefox" directory.
Firefox 3.1 beta2 works fine and re-use all the data from the 3.05 installation (bookmark, preferences, ...).
***The only thing that goes wrong is Flash***.
I've tried to copy the libflashplayer.so into the directory plugins inside firefox.
Nothing more.
If somebody has any idea, i'd be very interested because FF 3.1 seems a lot of faster than FF 3.05.

Merci d'avance

Hervé

---

### Post by zika on 2009-01-22
I'm also using FF3.2a1pre(mozilla-central Minefield)(if You find 3.1 fast try this ...;)) and I have that plugin in following places and it works:```
/home/whatever/.mozilla/plugins/libflashplayer.so
/usr/lib/mozilla/plugins/libflashplayer.so
```

---

### Post by herve34fr on 2009-01-22
I've installed FF3.2a1 pre(mozilla-central Minefield). And flash works without any other operation. . . Plugins all ready installed are all functional.
I don't understand why it is not the same thing with FF3.1 b1 or b2.

FF3.2 seems fast, but there is only english version, and so I prefer the french one.

Thanks for your help.

---

### Post by zika on 2009-01-22
> **herve34fr said:**
> I've installed FF3.2a1 pre(mozilla-central Minefield). And flash works without any other operation. . . Plugins all ready installed are all functional.
I don't understand why it is not the same thing with FF3.1 b1 or b2.

FF3.2 seems fast, but there is only english version, and so I prefer the french one.

Thanks for your help.
on the same computer(s) of mine (with file locations listed in my previous post) **both** 3.1b{1,2,3} and 3.2a1 (nightly's updated daily) share (and use) plug-ins with 3.0.5 ...
(just a thought): did You edit **~/firefox/firefox** so the line *moz_libdir=/home/whatever/firefox* points to the right directory?

---

### Post by herve34fr on 2009-01-22
I don't see what you mean.
Where is that " ~/firefox/firefox" file ? I don't see any . . .

---

### Post by zika on 2009-01-23
**herve34fr: **I downloaded the file from mozilla,decompressed and installed in my home by creating a "firefox" directory.

in that **""firefox" directory"** You have a file **firefox** and in it You have a line with **moz_libdir=**. did You edit that line to point to Your **""firefox" directory"**?

(~/firefox/firefox is actually /home/whatever/firefox/firefox)

---

### Post by herve34fr on 2009-01-23
In my firefox/firefox I have this value :
moz_libdir=/usr/local/lib/firefox-3.1b2
Should I give an other value to that, and which one ?
I have noticed that for FF3.2al the value was :
moz_libdir=/usr/local/lib/firefox-3.2a1pre, and all plugins were working fine.
I really don't understand why it's working with 3.2 and not with 3.1.

I've seen that you're from Belgrad. Weather must be very cold, snow may be ?

---

### Post by zika on 2009-01-23
> **herve34fr said:**
> In my firefox/firefox I have this value :
moz_libdir=/usr/local/lib/firefox-3.1b2
Should I give an other value to that, and which one ?
I have noticed that for FF3.2al the value was :
moz_libdir=/usr/local/lib/firefox-3.2a1pre, and all plugins were working fine.
I really don't understand why it's working with 3.2 and not with 3.1.

I've seen that you're from Belgrad. Weather must be very cold, snow may be ?
You should put the path to Your firefox file. so if You have /1/2/3/4/5/firefox/firefox You should put moz_libdir=/1/2/3/4/5/firefox and I'm pretty sure that Your problems will be gone. the reason I could come up with is that these are different branches of the development for FF so 3.1 already mimics "official" FF while 3.2 is totally "independent" ... I'm not sure if I am making clear what I mean but, just try and I'll leave my lame theory for some other time ... ;)

no, the weather is pretty warm now, yesterday and the day before yesterday around 10C and now it's 4C. raining with fog though.

---

