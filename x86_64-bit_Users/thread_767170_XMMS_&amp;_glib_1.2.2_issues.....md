---
title: "XMMS &amp; glib 1.2.2 issues...."
date: 2008-04-25
forum: x86 64-bit Users
---

### Post by Tsukino Kyuuketsuki on 2008-04-25
I woke up this morning with Hardy and found out XMMS wasn't in the repos no more. I've been trying all morning to install it manually but I keep getting this error:



```
checking for glib-config... no
checking for GLIB - version >= 1.2.2... no
*** The glib-config script installed by GLIB could not be found
*** If GLIB was installed in PREFIX, make sure PREFIX/bin is in
*** your path, or set the GLIB_CONFIG environment variable to the
*** full path to glib-config.
configure: error: *** GLIB >= 1.2.2 not installed - please install first ***
```



Then I got Glib 2.14 (do I REALLY have to get 1.2.2?)... same error... so I don't know, any suggestions on how to fix this :confused:?

---

### Post by smartboyathome on 2008-04-25
install libglib-dev.

---

### Post by mali2297 on 2008-04-25
Have you installed the development package **libglib2.0-dev**?

---

### Post by Tsukino Kyuuketsuki on 2008-04-25
Yup, got both, libglib-dev and libglib2.0-dev... still get the same error :confused:

---

### Post by Half-Left on 2008-04-25
Sorry to keep going on but Audacious is a better replacement and alot more up to date.

---

### Post by Tsukino Kyuuketsuki on 2008-04-25
> **Half-Left said:**
> Sorry to keep going on but Audacious is a better replacement and alot more up to date.

Don't like Audacious :( and no Amarok either... I like my mp3 player to be light and simple xD
XMMS was perfect for me, gotta be a way to fix the problem :confused:

---

### Post by Half-Left on 2008-04-25
Why dont you like Audacious?, it's the same as Xmms, you can even use winamp skins.

---

### Post by Tsukino Kyuuketsuki on 2008-04-25
> **Half-Left said:**
> Why dont you like Audacious?, it's the same as Xmms, you can even use winamp skins.

I don't know, I think it runs a little bit slower than xmms, might be using more ram... not sure :S But it's what I'm using right now, not quite happy though.

---

### Post by johnraff on 2008-04-26
> **Tsukino Kyuuketsuki said:**
> I woke up this morning with Hardy and found out XMMS wasn't in the repos no more. I've been trying all morning to install it manually but I keep getting this error:



```
checking for glib-config... no
checking for GLIB - version >= 1.2.2... no
*** The glib-config script installed by GLIB could not be found
*** If GLIB was installed in PREFIX, make sure PREFIX/bin is in
*** your path, or set the GLIB_CONFIG environment variable to the
*** full path to glib-config.
configure: error: *** GLIB >= 1.2.2 not installed - please install first ***
```



Then I got Glib 2.14 (do I REALLY have to get 1.2.2?)... same error... so I don't know, any suggestions on how to fix this :confused:?Have you installed libglib1.2-dev ? It looks as if xmms might want that version.

---

### Post by Evil Dax on 2008-04-28
xmms and Audacious are not the same,
I used xmms before, just because it is one of the few players (except BMP and VLC) that can send audio to my SPDIF (hardware 0,2), while the rest of them cannot...
And BMP is just to buggy....

---

### Post by je_suce on 2008-04-29
Passing by,


I had the same problem, try to install :

libgtkmm-dev and
libguilegtk-1.2-dev

my "./configure" works, but the "make" fails.

Good luck

---

### Post by je_suce on 2008-04-29
Last step :

copy the libs  ("*.so*") from ~/xmms-1.2.1/1ibxmms/.lib to /usr/lib

after what it works.

---

### Post by DirtDawg on 2008-04-29
Second post of this thread has links to [COLOR="DarkRed"]XMMS Hardy Deb packages[/COLOR]:[http://ubuntuforums.org/showthread.php?t=765609](http://ubuntuforums.org/showthread.php?t=765609)

They reportedly are in working order.

---

### Post by plazo on 2008-04-30
Hi,

audacious is a fork of xmms
xmms is no more maintained and will be replaced with xmms2

I'm using audacious and I can't see any difference with xmms exept the default skin

xmms should be considered as a deprecated package reason why it will be hard to install...

---

### Post by gattanegra on 2008-06-17
> **plazo said:**
> Hi,

audacious is a fork of xmms
xmms is no more maintained and will be replaced with xmms2

I'm using audacious and I can't see any difference with xmms exept the default skin

xmms should be considered as a deprecated package reason why it will be hard to install...

No, it is not truth!!!
XMMS is XMMS , XMMS2 is UGLY and A-B-S-O-L-U-T-E-L-Y non-functional. 
As for the Damned Audacious - it EATS my ram. It just GULPS it.
I can not understand WHY do they ruin stg. that was working SOOO NICE before?!!??!?!?!

---

### Post by Vishal Agarwal on 2008-06-17
did u get installed GTK+1.2.
is that problem over ?

---

### Post by ///MVinny on 2008-12-09
> **je_suce said:**
> Passing by,


I had the same problem, try to install :

libgtkmm-dev and
libguilegtk-1.2-dev

my "./configure" works, but the "make" fails.

Good luck

Money maker... that worked.... Thanks!

---

### Post by efalk on 2009-01-18
OK, here's what I think the story is:

The GTK graphics library has two versions, 1 (aka GTK+) and 2.  These two versions are *not* backwards compatible, meaning that a program written to use 1.2 will not compile or link to version 2.  In practice, any Linux system will need to have both versions installed.

Gtk contains three components:  gtk, the toolkit; gdk, the drawing package; and glib, the utilities library.

For some reason, the Hardy distribution deleted glib from the GTK distribution.  Until I found this thread, I was unable to find out where it went.

ETA:  It looks like glib was always in its own package, but the package was renamed from libglib1.2 to libglib1.2ldbl, breaking dependencies.

---

