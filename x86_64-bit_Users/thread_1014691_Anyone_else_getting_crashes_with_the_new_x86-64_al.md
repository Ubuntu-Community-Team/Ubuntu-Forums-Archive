---
title: "Anyone else getting crashes with the new x86-64 alpha Flash &amp; Firefox?"
date: 2008-12-18
forum: x86 64-bit Users
---

### Post by meldroc on 2008-12-18
This one's frustrating.  I'm currently running two systems.  One, my laptop, is running Hardy, and has the new x86-64 alpha Flash player, and it works great - no crashes at all, I can watch Youtube, lots of other videos, play Flash games, surf all over the place and it Just Works.

The other's an older Athlon 64-based desktop, and that one, when I install the 64-bit flash player, does not work so well - when I go to certain sites, [http://episteme.arstechnica.com/](http://episteme.arstechnica.com/) in particular (which has a certain NVidia flash ad that has 3D graphics and little tiny full-motion videos) BOOM - Firefox dies, presumably with a segfault.

I made damned sure there were no traces of older Flash plugins and nspluginwrapper, so that's not the problem.

Does anyone else have this problem?  And does anyone know how to fix it?

Better yet, has Adobe EVER released a version of Flash for Linux that actually works?

---

### Post by Arup on 2008-12-18
It works best when you don't have any remnants of your previous x32 flash and its very important to remove the nsplugin. If you do that, it works out really well, in my case neither Opera nor FF ever give me any issues.

---

### Post by meldroc on 2008-12-18
I did that - I purged nspluginwrapper and all traces of any 32-bit Flash.

---

### Post by Kilz on 2008-12-18
Its an [COLOR="Red"]**ALPHA**[/COLOR]. If you have problems file a bug report with adobe. Posting here will do little good if any.

---

### Post by meldroc on 2008-12-18
What's odd is that on my laptop, that alpha's worked far better than any of the "stable" versions of Flash that Adobe's released for Linux.

---

### Post by Yellow Pasque on 2008-12-18
There was an update to the native 64-bit Flash today (12/16). Perhaps that will fix things.

---

### Post by WiFi Ed on 2008-12-18
It's working fine for me. The arstechnica link you provided loads with no problems and I can spin the nvidia flash ad thingy.

---

### Post by Yellow Pasque on 2008-12-18
If you're having Flash ads crash your browser after installing the latest Flash, then you should probably install Flashblock and/or AdBlock Plus (either from the FF site or from Ubuntu's repo packages). At least you can access sites without ads crashing them.

Also, try starting FF from the terminal so you can see exactly why the browser crashes.

---

### Post by Arup on 2008-12-18
The arstechnica works fine here as well with Opera 9.63 or FF 3.05

---

### Post by caeroe on 2008-12-18
Hulu is no longer crashing me since the 12/16 release, so that's a major plus.

Flash video performance is still worse than in Windows though, especially when full screen.  The video chops up when I scroll at the bottom and the video controls pop up.

I obviously have the hardware and connection speed for hi-rez video playback, as mentioned, I dual-boot still.

---

