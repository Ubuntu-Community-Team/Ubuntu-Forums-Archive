---
title: "Flash 10 x64, Firefox 3.5.2: No Sound"
date: 2009-08-12
forum: x86 64-bit Users
---

### Post by dannymichel on 2009-08-12
I installed firefox 3.5.2 using ubuntuzilla and flash using [this method]("http://blog.lckymn.com/2009/06/07/installing-64bit-flash-player-in-ubuntu-linux/").
My sound is fine for other applications.
Im getting no sound when playing anything from firefox.
any ideas?

---

### Post by Yellow Pasque on 2009-08-12
> I installed firefox 3.5.2 using ubuntuzilla
That's a 32-bit browser. Why install that?

Anyway, if you want to diagnose the problem, start firefox from the terminal, try to play sound in some Flash site, and see if you get any helpful output.

---

### Post by darco on 2009-08-12
Did you substitute the new available x64 flashplayer file with what the how-to shows?

darco

*edit* heh, didnt notice that he was on x32...

---

### Post by dannymichel on 2009-08-12
this is what i got ```
danny@danny-desktop:~$ sudo /usr/bin/mozilla-firefox
/usr/lib/gio/modules/libgvfsdbus.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgvfsdbus.so
/usr/lib/gio/modules/libgioremote-volume-monitor.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgioremote-volume-monitor.so
/usr/lib/gio/modules/libgiogconf.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgiogconf.so
LoadPlugin: failed to initialize shared library /usr/lib/xulrunner-addons/plugins/libnullplugin.so [/usr/lib/xulrunner-addons/plugins/libnullplugin.so: wrong ELF class: ELFCLASS64]
LoadPlugin: failed to initialize shared library /usr/lib/xulrunner-addons/plugins/libunixprintplugin.so [/usr/lib/xulrunner-addons/plugins/libunixprintplugin.so: wrong ELF class: ELFCLASS64]
LoadPlugin: failed to initialize shared library /usr/lib/totem/gstreamer/libtotem-cone-plugin.so [/usr/lib/totem/gstreamer/libtotem-cone-plugin.so: wrong ELF class: ELFCLASS64]
LoadPlugin: failed to initialize shared library /usr/lib/totem/gstreamer/libtotem-gmp-plugin.so [/usr/lib/totem/gstreamer/libtotem-gmp-plugin.so: wrong ELF class: ELFCLASS64]
LoadPlugin: failed to initialize shared library /usr/lib/totem/gstreamer/libtotem-mully-plugin.so [/usr/lib/totem/gstreamer/libtotem-mully-plugin.so: wrong ELF class: ELFCLASS64]
LoadPlugin: failed to initialize shared library /usr/lib/totem/gstreamer/libtotem-narrowspace-plugin.so [/usr/lib/totem/gstreamer/libtotem-narrowspace-plugin.so: wrong ELF class: ELFCLASS64]
LoadPlugin: failed to initialize shared library /usr/lib/xulrunner-addons/plugins/librhythmbox-itms-detection-plugin.so [/usr/lib/xulrunner-addons/plugins/librhythmbox-itms-detection-plugin.so: wrong ELF class: ELFCLASS64]
LoadPlugin: failed to initialize shared library /usr/lib/totem/gstreamer/libtotem-cone-plugin.so [/usr/lib/totem/gstreamer/libtotem-cone-plugin.so: wrong ELF class: ELFCLASS64]
LoadPlugin: failed to initialize shared library /usr/lib/totem/gstreamer/libtotem-gmp-plugin.so [/usr/lib/totem/gstreamer/libtotem-gmp-plugin.so: wrong ELF class: ELFCLASS64]
LoadPlugin: failed to initialize shared library /usr/lib/totem/gstreamer/libtotem-mully-plugin.so [/usr/lib/totem/gstreamer/libtotem-mully-plugin.so: wrong ELF class: ELFCLASS64]
LoadPlugin: failed to initialize shared library /usr/lib/totem/gstreamer/libtotem-narrowspace-plugin.so [/usr/lib/totem/gstreamer/libtotem-narrowspace-plugin.so: wrong ELF class: ELFCLASS64]
danny@danny-desktop:~$ 

```

---

### Post by Yellow Pasque on 2009-08-12
Yeah, you would need 32-bit versions of all of that stuff in /usr/lib32.

Again, just run a 64-bit browser. There's no reason not to.

---

### Post by darco on 2009-08-12
Download and install the x32 flashplayer for this x32 FF...or do as Temujin says....

darco

---

### Post by ufuser1 on 2009-08-12
I wouldn't recommend upgrading your Firefox version right now, just sit still and wait for a propietary Firefox 3.5 package, I tried this myself and got me into a lot of trouble.
to undo changes you can do this.
```
ubuntuzilla.py -a remove -p firefox

```However, if you are that desperate to use an x64 bit Firefox with flash capabilities then just download Shiretoko's web browser off Ubuntu's Add or Remove Package. It's basically the same thing, works GREAT for me at least.

---

### Post by nanotube on 2009-08-12
> **dannymichel said:**
> I installed firefox 3.5.2 using ubuntuzilla and flash using [this method]("http://blog.lckymn.com/2009/06/07/installing-64bit-flash-player-in-ubuntu-linux/").
My sound is fine for other applications.
Im getting no sound when playing anything from firefox.
any ideas?

instead of using the method you linked to, try using the method described on the ubuntuzilla faq for 64bit users. here's a linky:

[http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Ubuntuzilla_FAQ#.5BFirefox.5D_What_happened_with_Flash_and_all_my_other_plugins.3F](http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Ubuntuzilla_FAQ#.5BFirefox.5D_What_happened_with_Flash_and_all_my_other_plugins.3F)

---

### Post by ronaldprettyman on 2009-08-13
> **dannymichel said:**
> I installed firefox 3.5.2 using ubuntuzilla and flash using [this method]("http://blog.lckymn.com/2009/06/07/installing-64bit-flash-player-in-ubuntu-linux/").
My sound is fine for other applications.
Im getting no sound when playing anything from firefox.
any ideas?

Are you running Ubuntu or Kubuntu, Theirs a bug with flash+firefox+kubuntu. Make sure pulse and gstreamer are working.

---

### Post by adempewolff on 2009-08-13
from my experience the 64bit version of firefox for ubuntu (Mozilla/5.0 (X11; U; Linux x86_64; en-US; rv:1.9.0.13) Gecko/2009080315 Ubuntu/9.04 (jaunty) Firefox/3.0.13 (.NET CLR 3.5.30729) along with the 64 bit beta flash plugin from adobe (10.0 d21) is the fastest and most stable way to use flash controls that I have seen.  It is certainly much faster, leaner, and less buggy than the non alpa/beta plugins for 32 bit linux (and faster than the windows plugins).

In conclusion: use the 64 bit browser and the beta flashplugin if you want a great flash experience.

---

### Post by motang on 2009-09-06
> **dannymichel said:**
> I installed firefox 3.5.2 using ubuntuzilla and flash using [this method]("http://blog.lckymn.com/2009/06/07/installing-64bit-flash-player-in-ubuntu-linux/").
My sound is fine for other applications.
Im getting no sound when playing anything from firefox.
any ideas?
I was having the same problem, so I deleted the flash plugin that I put in the plugins folder and just installed the flash plugin from **Add and Remove** and it worked find afterwards.

---

### Post by foxmajik on 2009-09-22
Hello,

It seems that Alsa gets in an invalid state if the system is suspended and resumed on x64.

I made a launcher that reloads Alsa.  It fixes the problem so I can get audio in Firefox and other applications at the same time:

gksudo /sbin/alsa force-reload

---

