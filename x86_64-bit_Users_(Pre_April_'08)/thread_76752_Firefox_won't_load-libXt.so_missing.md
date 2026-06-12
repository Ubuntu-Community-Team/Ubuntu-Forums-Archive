---
title: "Firefox won't load-libXt.so missing?"
date: 2005-10-15
forum: x86 64-bit Users (Pre April '08)
---

### Post by grsing on 2005-10-15
I tried to install Real player, and seem to have messed it up, and Firefox with it.  Neither Real nor Firefox will load from the GUI; when I try to load Firefox from Terminal, I get this error:

LoadPlugin: failed to initialize shared library libXt.so [libXt.so: cannot open shared object file: No such file or directory]

and the same error replacing libXt with libXext.  Everything else seems to be working as normal.  I've tried reinstalling libXt from Synaptic, but it hasn't helped.  I'm pretty new with linux, so I appreciate any help you can give me.  Thanks!

---

### Post by grsing on 2005-10-16
Well, reinstalling Ubuntu fixed it, and was probably a good idea anyway, given all the stuff I'm sure I've slightly screwed up as I learn linux the past week or so.

---

### Post by renderedbrian on 2005-10-16
I get the same error trying to run galeon on a fresh 5.10 amd64 install. Firefox does work for me though, but not Galeon due to this libXt.so  :confused: 

Edit - gnome-app-install also fails due to not finding libXt.so

Edit - made a symlink to libXt.so from libXt.so.6, galeon now finds libXt.so
-- 
Brian

---

### Post by youngster1 on 2005-10-18
> **grsing]I tried to install Real player, and seem to have messed it up, and Firefox with it.  Neither Real nor Firefox will load from the GUI said:**
> 

and the same error replacing libXt with libXext.  Everything else seems to be working as normal.  I've tried reinstalling libXt from Synaptic, but it hasn't helped.  I'm pretty new with linux, so I appreciate any help you can give me.  Thanks!


This problem is kicking my butt. I have tried installing RealPlayer twice now and each time it borks up the ability to run Firefox. I tried other browsers too - no luck. The only way to resolve the problem is reloading Ubuntu...what a pain.

Has anyone been successful in installing RealPlayer 10 on Ubuntu 64-bit yet?

---

### Post by Hallavej on 2005-10-25
Realplayer installs plugins in /usr/lib/mozilla-firefox/plugins/. As I remenber it is two files called *helix*.so and .xpt I don't remenber the exact names. They are links to nonexisting files. Remove them and everything is working again.
And no, realplayer doesnt work in 64-bit.

---

### Post by Robocoastie on 2005-11-21
[QUOTE=Hallavej]Realplayer installs plugins in /usr/lib/mozilla-firefox/plugins/. As I remenber it is two files called *helix*.so and .xpt I don't remenber the exact names. They are links to nonexisting files. Remove them and everything is working again.
And no, realplayer doesnt work in 64-bit.[/QUOTE]

You ROCK dude! As does the search feature for this forum!!! libXt.so in "search" led me BAM! right to this thread and your advice here fixed that problem for me.

Question though. Why does RealPlayer worker in Suse64 though? Do they have it actually custom running as 32 bit somehow? I tried their eval version a few days ago and noticed it installed with it as the mp3 default. However it was very unstable with my ATI card and I turned to Ubuntu....and not looking back :razz: 

Rob

---

### Post by Hallavej on 2005-11-22
[QUOTE=Robocoastie]
Question though. Why does RealPlayer worker in Suse64 though? Do they have it actually custom running as 32 bit somehow? I tried their eval version a few days ago and noticed it installed with it as the mp3 default. However it was very unstable with my ATI card and I turned to Ubuntu....and not looking back :razz: 

Rob[/QUOTE]

Dont know how suse does it, but it can be done in Ubuntu as well. You can either make a 32-bit chroot: [http://ubuntuforums.org/showthread.php?t=24575](http://ubuntuforums.org/showthread.php?t=24575)
or use this trick: [http://ubuntuforums.org/showthread.php?t=90106&highlight=firefox+32+bit](http://ubuntuforums.org/showthread.php?t=90106&highlight=firefox+32+bit)
made for firefox 32-bit but it also works with realplayer.

---

### Post by Robocoastie on 2005-11-30
[QUOTE=Hallavej]Dont know how suse does it, but it can be done in Ubuntu as well. You can either make a 32-bit chroot: [http://ubuntuforums.org/showthread.php?t=24575](http://ubuntuforums.org/showthread.php?t=24575)
or use this trick: [http://ubuntuforums.org/showthread.php?t=90106&highlight=firefox+32+bit](http://ubuntuforums.org/showthread.php?t=90106&highlight=firefox+32+bit)
made for firefox 32-bit but it also works with realplayer.[/QUOTE]

Thanks I'll check that out. In the meantime the problem is back suddenly :( and this time I didn't try to install Real at all. The plugins directory only has these in it:
```

libflash-mozplugin.so  libtotem_mozilla.so
libjavaplugin_oji.so   libtotem_mozilla.xpt

```

Yet I'm getting that libXt.so error all over again oddly.

Rob

edit/update: solved. in another thread with this similar issue a person suggested to install libxt-dev and that solved the problem for me.

---

