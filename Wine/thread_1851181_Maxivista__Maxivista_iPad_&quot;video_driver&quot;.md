---
title: "Maxivista / Maxivista iPad &quot;video driver&quot;"
date: 2011-09-27
forum: Wine
---

### Post by 1kenthomas on 2011-09-27
Howdy all.  
I'm trying to get Maxivista's products to work under ubuntu-- previous (2-3old) posts indicate is,  or was,  possible.

Maxivista's installer wants to add video drivers,  and the program fails to run because it does not detect them.  Can someone point me in the right direction to get started with such an issues?

Thanks!

---

### Post by Tweak42 on 2011-09-28
> **1kenthomas said:**
> Howdy all.  
I'm trying to get Maxivista's products to work under ubuntu-- previous (2-3old) posts indicate is,  or was,  possible.

Maxivista's installer wants to add video drivers,  and the program fails to run because it does not detect them.  Can someone point me in the right direction to get started with such an issues?

Thanks!

Because the Primary needs to install a proprietary driver to tie into Windows video system, I doubt it will be ever be possible to get it working under wine.

The Secondary is possible to get working since it doesn't need special drivers.  Essentially it's a viewer app, so all it should require is basic 2d video playback and network connection.  Experimenting around with windows components using winetricks might help.

---

### Post by 1kenthomas on 2011-09-30
Well...  It's not all that interesting to use a linux machine as a secondary to a windows machine :P,  though I suspect their *could* be some uses for it.  Archival posts from 2002-2010 seem to indicate that people have gotten Maxivista to work under Wine;  every one of those versions required a driver.

---

