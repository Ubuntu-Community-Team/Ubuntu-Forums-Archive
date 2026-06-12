---
title: "Flash on 64bit Firefox (nspluginwrapper) not working"
date: 2006-10-01
forum: x86 64-bit Users (Pre April '08)
---

### Post by tOz666 on 2006-10-01
Hi, I'm trying to use flash with firefox 64bits using nspluginwrapper, I followed some howto's I have found here using the search, installed the wrapped plugin, and it shows in the about: plugins

But whenever I try to load a page that has any flash, and youtube and google videos too, firefox freezes completely and I have to kill it and kill npviewer.bin to return the system's stability. Only a grey box shows instead of the flash content.

However, I tried the same using Mozilla Suite, and it works flawlessly.

I tried many different combinations of flash/nspluginwrapper versions with no luck, any ideas?

I'm triying to avoid any 32bit-based solutions, as I intend to have the system the more 64-bit pure possible, and heck, I recently upgraded to a athlon64 and want to feel it's power to the maximum :mrgreen:

---

### Post by a-musing amazon on 2006-10-01
I previously posted this a couple fo days ago in another thread ([http://ubuntuforums.org/showthread.php?t=160318](http://ubuntuforums.org/showthread.php?t=160318))

The security upgrade to Firefox 1.5.0.7 has broken nspluginwrapper 0.9.90.1 - the version publically available.

There has been a recent upgrade to 0.9.90.3, released on 19-Aug-06, that is supposed to fix this, however it is currently only available as a Mandrake src deb and a i586 binary deb, not on the nspluginwrapper website as of now.

Unfortunately the src package needs to be compiled on a 32-bit distro or in a chroot. I've had a look at what's involved and it seems to need a complete 32-bit development library set for of X, Gtk, cairo, pango etc. Which, for me, seems a heavy download and learning curve for such a small app (I do do compilations but so far only 64-bit ones).

I've tried to convert the i586 .rpm to a .deb using alien but it seems not to be picking up my i386 shared libraries properly (because its i586?) even though the named libs are there, so I suspect that a hand-install wouldn't work either.

I'm aware that you can avoid this hassle by using a 32-bit Firefox but I run Epiphany and Liferea on top of Firefox, and my other 32-but 'wrapped' nsplugins work OK, so don't really want to go that route. Hopefully the maintainer of nspluginwrapper (Gwenolé Beauchesne) will release a more generally compatible version.

Or is anyone else up for getting nspluginwrapper working on Dapper?

---

### Post by tOz666 on 2006-10-01
Well I managed to find the rpm's of the newer version you mentioned, and as stated in the howto's, I converted them to .deb using alien and installed the wrapped flash plugin. Now flash works without hanging firefox.

The rpm's are located here:

[http://mirror.linux.org.mt/mirror/mandrakelinux/devel/cooker/amd64/media/main/release/nspluginwrapper-0.9.90.3-1mdv2007.0.x86_64.rpm](http://mirror.linux.org.mt/mirror/mandrakelinux/devel/cooker/amd64/media/main/release/nspluginwrapper-0.9.90.3-1mdv2007.0.x86_64.rpm)
[http://mirror.linux.org.mt/mirror/mandrakelinux/devel/cooker/amd64/media/main/release/nspluginwrapper-i386-0.9.90.3-1mdv2007.0.x86_64.rpm](http://mirror.linux.org.mt/mirror/mandrakelinux/devel/cooker/amd64/media/main/release/nspluginwrapper-i386-0.9.90.3-1mdv2007.0.x86_64.rpm)

However before that I was trying to setup opera, it's 32 bit, so with little effort I managed to get every plugin working: flash, mplayerplug-in (the one modified for mplayer32, with win32 codecs), java, and even 32bit Acrobat Reader with mozplugger. Was triying that because opera doesn't break too much my setup and it's not a mess like having 64-bit and 32-bit firefox versions installed at the same time. If anyone wants I can write a little guide, explaining the tricks I made to get all working.

Don't have the time now, but i'll try the rest of plugins, right now in my 64bit firefox i'm using the blackdown java plugin, and for the only applet I tested, it just displays it incorrectly :(

So i'm wondering if anyone has managed to get java (32bit or 64) working in 64bit firefox.

---

### Post by kuja on 2006-10-01
Firefox(64-bit) likely won't be able to use the 32-bit java plugin, though, you could try if you wanted. 

Install the *ia32-sun-java5-bin* package.

Afterwards, copy /usr/lib/jvm/ia32-java-1.5.0-sun/jre/plugin/i386/ns7/libjavaplugin_oji.so to your plugin directory (~/.firefox/plugins)

The plugin works fine for 32-bit browsers though.

---

### Post by sha_man on 2006-10-02
> **tOz666 said:**
> Well I managed to find the rpm's of the newer version you mentioned, and as stated in the howto's, I converted them to .deb using alien and installed the wrapped flash plugin. Now flash works without hanging firefox.

The rpm's are located here:

[http://mirror.linux.org.mt/mirror/mandrakelinux/devel/cooker/amd64/media/main/release/nspluginwrapper-0.9.90.3-1mdv2007.0.x86_64.rpm](http://mirror.linux.org.mt/mirror/mandrakelinux/devel/cooker/amd64/media/main/release/nspluginwrapper-0.9.90.3-1mdv2007.0.x86_64.rpm)
[http://mirror.linux.org.mt/mirror/mandrakelinux/devel/cooker/amd64/media/main/release/nspluginwrapper-i386-0.9.90.3-1mdv2007.0.x86_64.rpm](http://mirror.linux.org.mt/mirror/mandrakelinux/devel/cooker/amd64/media/main/release/nspluginwrapper-i386-0.9.90.3-1mdv2007.0.x86_64.rpm)

wow - thank you for the rpms! 

> However before that I was trying to setup opera, it's 32 bit, so with little effort I managed to get every plugin working: flash, mplayerplug-in (the one modified for mplayer32, with win32 codecs), java, and even 32bit Acrobat Reader with mozplugger. Was triying that because opera doesn't break too much my setup and it's not a mess like having 64-bit and 32-bit firefox versions installed at the same time. If anyone wants I can write a little guide, explaining the tricks I made to get all working.


I would be *very* interested in such a HowTo, since i don't want to mess with to firefox installed!

---

### Post by tOz666 on 2006-10-02
First of all, grab the ubuntu 6.06 shared i386 deb, from opera homepage [http://www.opera.com/download/](http://www.opera.com/download/)
You can use the static deb if you want to, but the shared works too if you install the appropiate ia32 libs.

For the latest .deb it should be installed as follows:

cd to the directory you downloaded opera and issue the following command:

sudo dpkg -i --force-architecture opera_9.02-20060919.6-shared-qt_en_i386.deb

Then you have opera basically set-up, so you can use it right as it is.

But to have the various plugins working is a bit tricky, specially in this particular case where you have to install all 32-bit plugins in a 64bit os.

1) Setting up mplayerplug-in, using 32bit mplayer and win32codecs for maximum compatibility:

You have to read this [howto]("http://www.ubuntuforums.org/showthread.php?t=188974") on setting up 32bit mplayer, and then download the plugins I prepared using the modified mplayerplugin that is available in that thread. It's just the mplayerplug-in that looks for mplayer32 instead of regular mplayer, and compiled for opera in 32bit like stated in the [opera for linux plugin installation guides]("http://www.opera.com/linux/docs/plugins/install/#mplayer")

You can download this plugin [here]("http://telefonica.net/web2/toz/mplayerplug-in_mplayer32_opera.tar.bz2"), untar the files in the /usr/lib/opera/plugins directory. Then test it playing some online radios, or streaming videos, or apple trailers or whatever.

2) Flash player:

Easy one, just download the installer from the adobe flash player for linux page, and then use the installer calling it with linux32 as this:

sudo linux32 ./flashplayer-installer

and point it to install in the /usr/lib/opera/plugins directory.

or, you can just copy libflashplayer.so to /usr/lib/opera/plugins

3) Sun Java:

You should use the 32bit java, install the ia32-sun-java5-bin package.

follow the guide at the [opera website]("http://www.opera.com/support/search/supsearch.dml?index=459") and use this path for java setup: /usr/lib/jvm/ia32-java-1.5.0-sun-1.5.0.06/jre/lib/i386/

4) Acrobat reader and others using mozplugger:

First install acrobat reader 32bit using this [debs]("http://mirror.eepis-its.edu/debian-marillat/pool/main/a/acroread/")

install as usual with dpkg -i --force-architecture debfile

grab the acroread, and acroread-escript ones

I didn't use the acrobat's own plugin because i couldn't get it to work so i used mozplugger that can do the same and display other files too (like openoffice ones)

Download the plugin from my website, it's from the dapper i386 mozplugger deb, copy mozplugger.so to /usr/lib/opera/plugins and mozpluggerrc to /etc/  mozpluggerrc is modified to work with acrobat reader 32 bits, i changed one line to open acroread in a new window with the file requested (the open in same browser window way didn't work).

Grab it [from here.]("http://telefonica.net/web2/toz/mozplugger_opera.tar.bz2")

Well, that's it for the plugins I have tested, i think there will be no more of interest so there's a fairly complete opera+plugins setup ;)

---

### Post by kuja on 2006-10-02
Rather than using the static-qt, if you want to use the shared-qt ones (usually looks a bit better), all you have to do is install the package ia32-libs-kde :D

---

### Post by a-musing amazon on 2006-10-02
[QUOTE=tOz666;1569488]
> Well I managed to find the rpm's of the newer version
> you mentioned, and as stated in the howto's, I 
> converted them to .deb using alien and installed the 
> wrapped flash plugin. Now flash works without hanging
> firefox.

The rpm's are located here:

[http://mirror.linux.org.mt/mirror/mandrakelinux/devel/cooker/amd64/media/main/release/nspluginwrapper-0.9.90.3-1mdv2007.0.x86_64.rpm](http://mirror.linux.org.mt/mirror/mandrakelinux/devel/cooker/amd64/media/main/release/nspluginwrapper-0.9.90.3-1mdv2007.0.x86_64.rpm)
[http://mirror.linux.org.mt/mirror/mandrakelinux/devel/cooker/amd64/media/main/release/nspluginwrapper-i386-0.9.90.3-1mdv2007.0.x86_64.rpm](http://mirror.linux.org.mt/mirror/mandrakelinux/devel/cooker/amd64/media/main/release/nspluginwrapper-i386-0.9.90.3-1mdv2007.0.x86_64.rpm)

Many thanks for the links - I hadn't found those versions . NB for any one else updating alien issues a whole series of warnings - but it still works :).

---

### Post by a-musing amazon on 2006-10-02
> **tOz666 said:**
> 
> Don't have the time now, but i'll try the rest of 
> plugins, right now in my 64bit firefox i'm using the
> blackdown java plugin, and for the only applet I tested,
> it just displays it incorrectly :(
>
> So i'm wondering if anyone has managed to get java 
> (32bit or 64) working in 64bit firefox.
>
My experience is that most java applets do work for me using the 64-bit Blackdown Java package. However it is not 100%.

---

### Post by Murwiz on 2006-10-02
> 2) Flash player:

Easy one, just download the installer from the adobe flash player for linux page, and then use the installer calling it with linux32 as this:

sudo linux32 ./flashplayer-installer

and point it to install in the /usr/lib/opera/plugins directory.

or, you can just copy libflashplayer.so to /usr/lib/opera/plugins

Hmm, I tried that: I now have libflashplayer.so installed in /usr/lib/firefox. And yet, no Flash ... for instance, youtube.com just reports that I have an old version of Flash installed.

---

### Post by a-musing amazon on 2006-10-02
> **Murwiz said:**
> Hmm, I tried that: I now have libflashplayer.so installed in /usr/lib/firefox. And yet, no Flash ... for instance, youtube.com just reports that I have an old version of Flash installed.

You are using a guide to how to install 32-bit (the only sort) of flashplayer in 32-bit Opera.

Are you trying to install your 32-bit plugin in 64-bit Firefox? - the directory ref. you provides suggests you are. To do that succesfully you have to use nspluginwrapper which will provide a 32-bit to 64-bit compatibility layer.

---

### Post by sha_man on 2006-10-06
thanks for your howto tOz666! =D>

---

