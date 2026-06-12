---
title: "adobe flash 10 alpha on intrepid amd64"
date: 2008-12-28
forum: x86 64-bit Users
---

### Post by graysky on 2008-12-28
I read the sticky above, but I can't believe all that is necessary to get flash 10 working under intrepid.  I have a Debian/Lenny install and all I did to get it working with firefox (iceweasel) there was:

[http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.d20.7.linux-x86_64.so.tar.gz](http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.d20.7.linux-x86_64.so.tar.gz)

```
# mkdir /usr/local/lib/flashplugin
# mv libflashplayer.so /usr/local/lib/flashplugin
# cd /etc/alternatives
# mv flash-mozilla.so flash-mozilla.so-old
# ln -s /usr/local/lib/flashplugin/libflashplayer.so flash-mozilla.so
```

This didn't work under intrepid, but surely there's something similar without all the steps/32-bit libs, etc.?

---

### Post by Skripka on 2008-12-28
libflashplayer.so should live in /usr/lib/mozilla/plugins. At least on Intrepid anyway--put the 64bit flashplayer there (and uninstall whatever flash you may have installed via Synaptic) and it should work beautifully.  You'll need sudo permissions to put it there, of course.

---

### Post by graysky on 2008-12-28
> **Skripka said:**
> libflashplayer.so should live in /usr/lib/mozilla/plugins. At least on Intrepid anyway--put the 64bit flashplayer there (and uninstall whatever flash you may have installed via Synaptic) and it should work beautifully.  You'll need sudo permissions to put it there, of course.

I just did this and it worked :)

```
$ mkdir ~/.mozilla/plugins
$ mv libflashplayer.so ~/.mozilla/plugins
```

Why all the fuss with that sticky?

Anyway, I didn't see that I have any flash player installed in synaptic... do you know what the out-of-the-box one for intrepid might be?

---

### Post by Skripka on 2008-12-28
> **graysky said:**
> I just did this and it worked :)

```
$ mkdir ~/.mozilla/plugins
$ mv libflashplayer.so ~/.mozilla/plugins
```

Why all the fuss with that sticky?

Anyway, I didn't see that I have any flash player installed in synaptic... do you know what the out-of-the-box one for intrepid might be?

If the mozilla/plugins folder was empty before your started playing around with things, then you don't have anything to worry about.

Last I knew the Ubuntu repos only had 32-bit Flash 10.0.15 with the plugin wrapper--not the native 64bit Alpha "refresh", last I knew....flashplugin-nonfree hitches a ride for install if the Ubuntu Restricted Extras metapackage gets installed IIRC.

---

### Post by graysky on 2008-12-28
Yeah, all I had in there was the totem stuff:
```
/-rwxr-xr-x 1 root root 9.1M 2008-12-28 21:44 libflashplayer.so
lrwxrwxrwx 1 root root   44 2008-12-28 11:23 libtotem-basic-plugin.so -> ../../totem/default/libtotem-basic-plugin.so
lrwxrwxrwx 1 root root   42 2008-12-28 11:23 libtotem-gmp-plugin.so -> ../../totem/default/libtotem-gmp-plugin.so
lrwxrwxrwx 1 root root   44 2008-12-28 11:23 libtotem-mully-plugin.so -> ../../totem/default/libtotem-mully-plugin.so
lrwxrwxrwx 1 root root   50 2008-12-28 11:23 libtotem-narrowspace-plugin.so -> ../../totem/default/libtotem-narrowspace-plugin.so
```

BTW, do you know how to go about installing the 64-bit java runtimes?

---

### Post by Skripka on 2008-12-28
> **graysky said:**
> Yeah, all I had in there was the totem stuff:
[code]/-rwxr-xr-x 1 root root 9.1M 2008-12-28 21:44 libflashplayer.so
lrwxrwxrwx 1 root root   44 2008-12-28 11:23 libtotem-basic-plugin.so -> ../../totem/default/libtotem-basic-plugin.so
lrwxrwxrwx 1 root root   42 2008-12-28 11:23 libtotem-gmp-plugin.so -> ../../totem/default/libtotem-gmp-plugin.so
lrwxrwxrwx 1 root root   44 2008-12-28 11:23 libtotem-mully-plugin.so -> ../../totem/default/libtotem-mully-plugin.so
lrwxrwxrwx 1 root root   50 2008-12-28 11:23 libtotem-narrowspace-plugin.so -> ../../totem/default/libtotem-narrowspace-plugin.so[code]

BTW, do you know how to go about installing the 64-bit java runtimes?

I've honestly have yet to worry about any other Java than what is in the repos-I don't know off hand.

Although this might be helpful :D (Yes, I'm in a smart @$$ type mood tonight)

http://lmgtfy.com/?q=64bit+Java+ubuntu+linux

---

### Post by stchman on 2008-12-29
According to the Intrepid repos the flashplugin-nonfree works with AMD64.

[http://packages.ubuntu.com/intrepid/flashplugin-nonfree](http://packages.ubuntu.com/intrepid/flashplugin-nonfree)

If that does not work then use the following:

Download the Flash 10 for 64 bit Linux.
[http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)

Then unpack the archive into the ~/.mozilla/plugins folder.

This worked for me.

---

