---
title: "New Amd64 repository (unofficial)"
date: 2006-06-13
forum: x86 64-bit Users (Pre April '08)
---

### Post by Corbelius on 2006-06-13
uPure64 (ubuntu pure x86_64) is a repository for the Ubuntu Linux AMD64 (64bit) distribution, it's update to last stable release, at this moment Feisy Fawn AMD64, the packages of the previous versions of Ubuntu will remain online until the Canonical expire their support. The repository exist to make more complete and compatible the 64bit like to i386, between the packages included in it there are NsPluginWrapper, Gnash, Beagle, Banshee, Rhythmbox, Pidgin, K3B, Kdenlive and many others. All the packages are complete of their sources and released under the original software license, GPL or whichever other Open Source.

To add the repository:

```
gpg --keyserver hkp://keyserver.ubuntu.com:11371/ --recv-keys 2C4C84CC && gpg --export --armor 2C4C84CC | sudo apt-key add -
```

Otherwise::

```
wget http://download.tuxfamily.org/upure64/2C4C84CC.gpg -O- | sudo apt-key add -
```

Dapper Drake:
```
## uPure64 Repository
deb http://download.tuxfamily.org/upure64/ dapper-upure64 main-amd64
```

Edgy Eft:
```
## uPure64 Repository
deb http://download.tuxfamily.org/upure64/ edgy-upure64 main-amd64
```

Feisty Fawn:
```
## uPure64 Repository
deb http://download.tuxfamily.org/upure64/ feisty-upure64 main-amd64
deb-src http://download.tuxfamily.org/upure64/ feisty-upure64 main-amd64

## uPure64 Repository (Experimental)
deb http://download.tuxfamily.org/upure64/ feisty-upure64 experimental-amd64
deb-src http://download.tuxfamily.org/upure64/ feisty-upure64 experimental-amd64
```

Gutsy Gibbon:
```
## uPure64 Repository
deb http://download.tuxfamily.org/upure64/ gutsy-upure64 main
deb-src http://download.tuxfamily.org/upure64/ gutsy-upure64 main

## uPure64 Repository (Experimental)
deb http://download.tuxfamily.org/upure64/ gutsy-upure64 experimental
deb-src http://download.tuxfamily.org/upure64/ gutsy-upure64 experimental
```

Homepage: [http://www.janvitus.netsons.org/repository/](http://www.janvitus.netsons.org/repository/)

Feed rss: [http://www.janvitus.netsons.org/feed/](http://www.janvitus.netsons.org/feed/)

Tell me any problems and suggestions ;)



p.s.: sorry for my english

---

### Post by henriquemaia on 2006-06-13
Wow, thanks a lot. I was willing to try the Listen player for quite some time now and you gave me the oportunity to do it. 

Thanks again. Listen installs ok and runs ok. 

You ask for suggestions. You mean programs to add to your repository?

---

### Post by John Jason Jordan on 2006-06-13
[QUOTE=Corbelius]
```
## Janvitus Amd64 Repository
deb http://janvitus.interfree.it/ ./
```[/QUOTE]
Thanks!

But I have a problem with gxine. After adding your repository it shows in Synaptic as having an upgrade available. But when I tell Synaptic to install the upgrade Synaptic tells me that it cannot do so because of a lot of unresolved dependencies, that cannot be installed. :(

Meantime I'm going to install Listen and see what I think of it.

---

### Post by John Jason Jordan on 2006-06-13
[QUOTE=John Jason Jordan]Meantime I'm going to install Listen and see what I think of it.[/QUOTE]
Oops, posted that too soon. Same problem with Listen. Won't install because of unresolved dependencies, which Synaptic says cannot be installed. :(

---

### Post by henriquemaia on 2006-06-14
[quote=John Jason Jordan]Oops, posted that too soon. Same problem with Listen. Won't install because of unresolved dependencies, which Synaptic says cannot be installed. :([/quote]

Have you enabled the multiverse repositories? On mine Listen just installed, without any flaws.

---

### Post by Corbelius on 2006-06-14
[QUOTE=John Jason Jordan]Oops, posted that too soon. Same problem with Listen. Won't install because of unresolved dependencies, which Synaptic says cannot be installed. :([/QUOTE]

Sorry, my repository required dapper libraries :)

[QUOTE=henriquemaia]

You ask for suggestions. You mean programs to add to your repository?[/QUOTE]

Or some newest version of the most popular software (example rhythmbox, amule, etc.), or newest software are not include in the officials dapper repositories (example Listen, bonfire, etc.) :)

---

### Post by Hendrik van den Boogaard on 2006-06-14
At my place the 'listen' packages do not work and give me the same error as the i386 packages I tried before:

```

hendrik@hendrik:~$ listen
LISTEN : CREATE DATABASE
Traceback (most recent call last):
  File "/usr/bin/listen", line 409, in ?
    Listen()
  File "/usr/bin/listen", line 136, in __init__
    self.run()
  File "/usr/bin/listen", line 255, in run
    from player import Player
  File "/usr/lib/listen/player.py", line 35, in ?
    from misc_widget import VolumeSlider
  File "/usr/lib/listen/misc_widget.py", line 319, in ?
    from podcast_manager import PodcastManager
  File "/usr/lib/listen/podcast_manager.py", line 31, in ?
    from db_manager import DBManager
  File "/usr/lib/listen/db_manager.py", line 681, in ?
    DBManager = ListenDBManager(True)
  File "/usr/lib/listen/db_manager.py", line 39, in __init__
    self.db = ListenDB(check_exist)
  File "/usr/lib/listen/db_manager.py", line 384, in __init__
    self.cur.execute( requete_media )
pysqlite2.dbapi2.OperationalError: database is locked

```

Removing the .listen settings dir did not solve the problem. Does it have to do with the fact that some packages from other AMD64 repositories (for Compiz for example) might interfere? Any suggestions?

---

### Post by henriquemaia on 2006-06-14
[quote=Hendrik van den Boogaard][...]
Removing the .listen settings dir did not solve the problem. Does it have to do with the fact that some packages from other AMD64 repositories (for Compiz for example) might interfere? Any suggestions?[/quote]

Probably that, since I don't have compiz installed and listen works great.

My output on the terminal:

```
Traceback (most recent call last):
  File "/usr/lib/listen/view_podcast.py", line 295, in on_row_selected
    self.song_view.fill(songs)
  File "/usr/lib/listen/view_song.py", line 142, in fill
    self.set_songs(songs)
  File "/usr/lib/listen/view_song.py", line 211, in set_songs
    self.get_toplevel().window.set_cursor(gtk.gdk.Cursor(gtk.gdk.WATCH))
AttributeError: 'NoneType' object has no attribute 'set_cursor'
Traceback (most recent call last):
  File "/usr/bin/listen", line 349, in source_run
    source.run()
  File "/usr/lib/listen/media_source.py", line 496, in run
    self.view.populate()
  File "/usr/lib/listen/view_iradio.py", line 43, in populate
    self.fill(self.songs_cache)
  File "/usr/lib/listen/view_song.py", line 142, in fill
    self.set_songs(songs)
  File "/usr/lib/listen/view_song.py", line 211, in set_songs
    self.get_toplevel().window.set_cursor(gtk.gdk.Cursor(gtk.gdk.WATCH))
AttributeError: 'NoneType' object has no attribute 'set_cursor'
Traceback (most recent call last):
  File "/usr/lib/listen/view_browser.py", line 411, in on_search_changed_cb
    self.fill(self.get_list_type()[0],song_to_add)
  File "/usr/lib/listen/view_browser.py", line 283, in fill
    self.get_toplevel().window.set_cursor(gtk.gdk.Cursor(gtk.gdk.WATCH))
AttributeError: 'NoneType' object has no attribute 'set_cursor'

```

---

### Post by JoWilly on 2006-06-14
Thanks, this just gave me the opportunity to try bonfire and listen :)

---

### Post by Corbelius on 2006-06-15
[QUOTE=Hendrik van den Boogaard]At my place the 'listen' packages do not work and give me the same error as the i386 packages I tried before:

Removing the .listen settings dir did not solve the problem. Does it have to do with the fact that some packages from other AMD64 repositories (for Compiz for example) might interfere? Any suggestions?[/QUOTE]

Maybe it's the same bug: [http://sourceforge.net/tracker/index.php?func=detail&aid=1502778&group_id=161415&atid=819743](http://sourceforge.net/tracker/index.php?func=detail&aid=1502778&group_id=161415&atid=819743)

---

### Post by Corbelius on 2006-06-17
New package:

Bonfire 0.3.90 (update package "libgnomevfs2-0" from the repsoitory "dapper-updates")

Music-applet 0.9.2

U can check packages news here: [http://www.janvitus.netsons.org/index.php?catid=2&blogid=1](http://www.janvitus.netsons.org/index.php?catid=2&blogid=1)

Or on feed-rss: [http://www.janvitus.netsons.org/xml-rss2.php](http://www.janvitus.netsons.org/xml-rss2.php)

---

### Post by jairo.serrano on 2006-06-17
ZSnes?
more emulators?
kqemu?

hum...

---

### Post by Nicks Spleen on 2006-06-17
Thank you for this. I have been wanting to get bonfire but relutant to build it myself. Its stuff like this that is going to help make amd64 a lot better.

---

### Post by RAOF on 2006-06-18
I have some suggestions:
1) Could you post source packages?  They're really useful - some of these packages might not have been built for architectures other than IA32 (like PPC), and if you post the source packages, they won't have to duplicate the effort of packaging.

2) Perhaps you could change your version scheme?  If you replace "*x*ubuntu*y*" with "*x*janvitus*y*", it's more obvious where the updates are coming from, and (importantly) it will be obvious when there is an **official** Ubuntu update/package.

3) If you want an easy way to add the GPG key to your repository, might I suggest you use *falcon* to manage the repository.  It's in the Ubuntu repository, and works really well.

Finally, [my repository]("http://raof.dyndns.org/falcon") also has some AMD64 packages.  Specifically, mythtv 0.19 + some SVN fixes, Rhythmbox 0.9.4.1, and the XGL/Compiz stuff.  Oh, and gnash.  It's also an example of a default falcon setup :)

---

### Post by Stormbringer on 2006-06-18
@RAOF:

First off - thanks for providing the repository; I was really looking forward an up-to-date version of ffmpeg for my AMD64 box.

However, there seems to be a small glitch:
Your ffmpeg package is missing a required dependency: libx264-dev
Installation wents fine, but upon lauch ffmpeg complains about the missing library.

BTW: Since you are providing other newer packages (libcairo, libdrm, ...): is it safe to install them without having the XGL eyecandy stuff installed or will this break things?

Cheers,
Storm.

---

### Post by RAOF on 2006-06-18
[QUOTE=Stormbringer]...
However, there seems to be a small glitch:
Your ffmpeg package is missing a required dependency: libx264-dev
Installation wents fine, but upon lauch ffmpeg complains about the missing library.

BTW: Since you are providing other newer packages (libcairo, libdrm, ...): is it safe to install them without having the XGL eyecandy stuff installed or will this break things?
...[/QUOTE]
Thanks.  That's what you get for not using a clean-build environment to build your packages :(.  I'll update my packages.

The libcairo/libdrm stuff **should** be safe to install without XGL, but if you don't want it, you can include only the sections of my repository you want, like:
```
deb http://raof.dyndns.org/falcon/ dapper multimedia gnash
```

---

### Post by RAOF on 2006-06-19
Oh, and for those people wanting iPod support in Listen, my repository has libgpod packages, with the python bindings (python2.4-gpod) built.  Read and write to your iPods through Listen!

---

### Post by jkwarras on 2006-06-21
Hi,

Thanks for these grat repositories, it's really useful :)

I just wanted to suggest two packages for your consideration to include:

- Exaile! (ala banshee, amarok, quodlibet...)
- Muine 0.8.5 (in the official respository there's version 0.8.4 that depends on gstreamer 0.8)

Thanks!

---

### Post by Corbelius on 2006-06-21
> **RAOF]I have some suggestions:

2) Perhaps you could change your version scheme?  If you replace "*x*ubuntu*y*" with "*x*janvitus*y*", it's more obvious where the updates are coming from, and (importantly) it will be obvious when there is an **official** Ubuntu update/package.[/quote]

New suffix is "xubuntuy~janvitus"  said:**
> 3) If you want an easy way to add the GPG key to your repository, might I suggest you use *falcon* to manage the repository.  It's in the Ubuntu repository, and works really well.

Tnx for the suggest :)

[QUOTE=jkwarras]

- Exaile! (ala banshee, amarok, quodlibet...)
- Muine 0.8.5 (in the official respository there's version 0.8.4 that depends on gstreamer 0.8)
[/QUOTE]

Mmm... ok, i can try to both :D

---

### Post by jkwarras on 2006-06-22
[QUOTE=Corbelius]
Mmm... ok, i can try to both :D[/QUOTE]
Thanks!

---

### Post by Corbelius on 2006-07-02
[http://www.janvitus.netsons.org/?itemid=6](http://www.janvitus.netsons.org/?itemid=6)


[QUOTE=jkwarras]

- Exaile! (ala banshee, amarok, quodlibet...)
- Muine 0.8.5 (in the official respository there's version 0.8.4 that depends on gstreamer 0.8)
[/QUOTE]

Mmm... i have problem to compile this, muine don't want create a .deb, but i get try in the next days.

---

### Post by XioNoX on 2006-07-02
Gaim 2.0.3 64bits is aviable here :
 deb [http://people.ubuntu.com/~seb128/deb](http://people.ubuntu.com/~seb128/deb) ./
 deb-src [http://people.ubuntu.com/~seb128/deb](http://people.ubuntu.com/~seb128/deb) ./
But there are no 64bits guifications plugin.
(only this 32bits : [http://debuntu.free.fr/divers/gaim-guifications-2.13+beta3.tar.bz2](http://debuntu.free.fr/divers/gaim-guifications-2.13+beta3.tar.bz2))

Can you make the lastest tcl/tk deb for 64bits ? and the aMSN non-aliased ?
Thanks

---

### Post by jkwarras on 2006-07-06
[QUOTE=Corbelius][http://www.janvitus.netsons.org/?itemid=6](http://www.janvitus.netsons.org/?itemid=6)




Mmm... i have problem to compile this, muine don't want create a .deb, but i get try in the next days.[/QUOTE]
Thanks, I'll wait for these two :)

---

### Post by derek_harding on 2006-07-07
Thanks for the repository - how about a port of scribus-ng to dapper-64? I'm having a lot of dependency problems with the amd64 deb and with compiling the source.

-- 
Best wishes,
Derek

---

### Post by Corbelius on 2006-07-07
Update package: gxine 0.5.7, sensors-applet 1.7.2

[http://www.janvitus.netsons.org/xml-rss2.php](http://www.janvitus.netsons.org/xml-rss2.php)

---

### Post by gurgle on 2006-07-11
i cant get into RAOF's repo - is it down?

---

### Post by JoWilly on 2006-07-11
> **gurgle said:**
> i cant get into RAOF's repo - is it down?

Use the mirror : [http://ubuntu.moshen.de/](http://ubuntu.moshen.de/)

---

### Post by RAOF on 2006-07-11
> **gurgle said:**
> i cant get into RAOF's repo - is it down?
My repo is down quite frequently - It's my home computer, so I need to turn it off when I want to sleep :)

Plus, I occasionally go crazy and install -mm kernels :).  Moshen is much more reliable (and with better bandwidth).

---

### Post by charlier653 on 2006-07-12
found this at sun website, doin't know how to get it to install  (yes, i'm a newbie) jre-1_5_0_07-linux-amd64.bin

also, nvidia has a linux driver for the gforce line that is supposed to work better than the nv that comes with Ubuntu

[http://www.nvidia.com/object/linux_display_amd64_1.0-7182.html](http://www.nvidia.com/object/linux_display_amd64_1.0-7182.html)


i have the geforce 5500 on my machine........thought maybe i could enable some of the features available on this card.....again, being a total noob to linux, can't seem to get it to install.

i have the AMD sempron64 3400+ cpu, 1.5 gb ddr ram on a gigabyte GA K8U ULi M 1689 MB

---

### Post by Corbelius on 2006-07-12
> **charlier653 said:**
> found this at sun website, doin't know how to get it to install  (yes, i'm a newbie) jre-1_5_0_07-linux-amd64.bin

also, nvidia has a linux driver for the gforce line that is supposed to work better than the nv that comes with Ubuntu

[http://www.nvidia.com/object/linux_display_amd64_1.0-7182.html](http://www.nvidia.com/object/linux_display_amd64_1.0-7182.html)


i have the geforce 5500 on my machine........thought maybe i could enable some of the features available on this card.....again, being a total noob to linux, can't seem to get it to install.

i have the AMD sempron64 3400+ cpu, 1.5 gb ddr ram on a gigabyte GA K8U ULi M 1689 MB

[https://help.ubuntu.com/community/Java?highlight=%28java%29](https://help.ubuntu.com/community/Java?highlight=%28java%29)

[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia?highlight=%28nvidia%29](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia?highlight=%28nvidia%29)

---

### Post by charlier653 on 2006-07-13
thanks, i needed that!

---

### Post by RAOF on 2006-07-13
New in my repository: tracker 0.0.4 & a tracker-enabled build of nautilus.  Virtual-search-folders comeing soon to a Gnome desktop near you!

---

### Post by gurgle on 2006-07-15
for xgl/compiz sexiness, what should i install?

---

### Post by Corbelius on 2006-07-16
> **gurgle said:**
> for xgl/compiz sexiness, what should i install?

This is the guide: [http://www.compiz.net/viewtopic.php?id=389](http://www.compiz.net/viewtopic.php?id=389)

This is the reopositories: [http://xgl.compiz.info/](http://xgl.compiz.info/)




I have inserted in my repository istanbul 0.2 (screen recorder based on gstreamer0.10), and the latest versione of Bonfire (0.4.1).

---

### Post by JoWilly on 2006-07-16
> **Corbelius said:**
> This is the guide: [http://www.compiz.net/viewtopic.php?id=389](http://www.compiz.net/viewtopic.php?id=389)



Be warned this is again one more shitty howto. There is no need to edit gdm.conf and there is no need for a script. Some people have fiddled in trying to do their own cooking and came up with complicated ways to do it, this is one of the results.

Installing xgl is as easy as 1-2-3. It has been posted on these forums countless times.

Install the packages, edit gdm.conf-custom (put 0 for the server number for nvidia, 1 for ati), and add [FONT=Verdana][SIZE=2]"gnome-window-decorator" and "compiz --replace gconf" to "menu/system/prefs/sessions/startup apps".
[/SIZE][/FONT]

---

### Post by RAOF on 2006-07-16
[SIZE="4"]New in my repository: mono 1.1.13.8[/SIZE]
Backported from Edgy.  If you're cautious about replacing a fairly important system library with (practically) untested code, now's the time to change "all" to "eyecandy flash multimedia mythtv" in your sources.list :)

This seems to fix the "Banshee segfaults on import" problem that I've been as yet unable to track down.  Once again, amaze your friends as you run CVS banshee (thus far the most complete iPod solution I've found.  CVS now supports cover art, too :)) with the banshee-official plugins.

Now that that's fixed, I can start thinking about packaging the unofficial banshee plugins :)

---

### Post by jonah1980 on 2006-07-16
yes someone please do a scribus-ng 64bit as i can't open anything i made in scribus on old computer on 1.3.3.2 cos it's only 1.2.4 or whatever on 64bit dapper!!

---

### Post by gurgle on 2006-07-16
W: Failed to fetch [http://ubuntu.moshen.de/pool/mono/libmono-system-web1.0-cil_1.1.13.8-1ubuntu2_all.deb](http://ubuntu.moshen.de/pool/mono/libmono-system-web1.0-cil_1.1.13.8-1ubuntu2_all.deb)
  404 Not Found


W: Failed to fetch [http://ubuntu.moshen.de/pool/mono/libmono1.0-cil_1.1.13.8-1ubuntu2_all.deb](http://ubuntu.moshen.de/pool/mono/libmono1.0-cil_1.1.13.8-1ubuntu2_all.deb)
  404 Not Found


W: Failed to fetch [http://ubuntu.moshen.de/pool/mono/mono-classlib-1.0_1.1.13.8-1ubuntu2_all.deb](http://ubuntu.moshen.de/pool/mono/mono-classlib-1.0_1.1.13.8-1ubuntu2_all.deb)
  404 Not Found


W: Failed to fetch [http://ubuntu.moshen.de/pool/multimedia/banshee_0.11.0-cvs-0raof5_amd64.deb](http://ubuntu.moshen.de/pool/multimedia/banshee_0.11.0-cvs-0raof5_amd64.deb)
  404 Not Found


W: Failed to fetch [http://ubuntu.moshen.de/pool/misc/libnautilus-extension1_2.14.1-0ubuntu9tracker1_amd64.deb](http://ubuntu.moshen.de/pool/misc/libnautilus-extension1_2.14.1-0ubuntu9tracker1_amd64.deb)
  404 Not Found


W: Failed to fetch [http://ubuntu.moshen.de/pool/misc/tracker_0.0.4-0raof1_amd64.deb](http://ubuntu.moshen.de/pool/misc/tracker_0.0.4-0raof1_amd64.deb)
  404 Not Found


W: Failed to fetch [http://ubuntu.moshen.de/pool/misc/nautilus-data_2.14.1-0ubuntu9tracker1_all.deb](http://ubuntu.moshen.de/pool/misc/nautilus-data_2.14.1-0ubuntu9tracker1_all.deb)
  404 Not Found


W: Failed to fetch [http://ubuntu.moshen.de/pool/misc/nautilus_2.14.1-0ubuntu9tracker1_amd64.deb](http://ubuntu.moshen.de/pool/misc/nautilus_2.14.1-0ubuntu9tracker1_amd64.deb)
  404 Not Found



:(

---

### Post by RAOF on 2006-07-17
> **gurgle said:**
> ...
W: Failed to fetch [http://ubuntu.moshen.de/pool/misc/nautilus_2.14.1-0ubuntu9tracker1_amd64.deb](http://ubuntu.moshen.de/pool/misc/nautilus_2.14.1-0ubuntu9tracker1_amd64.deb)
  404 Not Found



:(
Oops.  Looks like I need to better sync the mirror, then!

---

### Post by gurgle on 2006-07-17
Raof, sorry im being noobish, but can you link to a longer description of each package? im wondering what this mono is.......

---

### Post by jonah1980 on 2006-07-17
W: Failed to fetch [http://ubuntu.moshen.de/pool/misc/libnautilus-extension1_2.14.1-0ubuntu9tracker1_amd64.deb](http://ubuntu.moshen.de/pool/misc/libnautilus-extension1_2.14.1-0ubuntu9tracker1_amd64.deb)
  404 Not Found


W: Failed to fetch [http://ubuntu.moshen.de/pool/misc/tracker_0.0.4-0raof1_amd64.deb](http://ubuntu.moshen.de/pool/misc/tracker_0.0.4-0raof1_amd64.deb)
  404 Not Found


W: Failed to fetch [http://ubuntu.moshen.de/pool/misc/nautilus-data_2.14.1-0ubuntu9tracker1_all.deb](http://ubuntu.moshen.de/pool/misc/nautilus-data_2.14.1-0ubuntu9tracker1_all.deb)
  404 Not Found


W: Failed to fetch [http://ubuntu.moshen.de/pool/misc/nautilus_2.14.1-0ubuntu9tracker1_amd64.deb](http://ubuntu.moshen.de/pool/misc/nautilus_2.14.1-0ubuntu9tracker1_amd64.deb)
  404 Not Found

---

### Post by RAOF on 2006-07-17
> **gurgle said:**
> Raof, sorry im being noobish, but can you link to a longer description of each package? im wondering what this mono is.......
In general, if you browse [raof.dyndns.org/falcon](raof.dyndns.org/falcon) (or the moshen mirror, once I've got everything sorted out so I can sync to it) there are links to the package descriptions.  Here's the one for mono:

> 
Mono is a platform for running and developing applications based on the ECMA/ISO Standards. Mono is an open source effort led by Novell. Mono provides a complete CLR (Common Language Runtime) including compiler and runtime, which can produce and execute CIL (Common Intermediate Language) bytecode (aka assemblies), and a class library.


Basically, it's the runtime for such programs as Banshee, F-Spot, Tomboy, Beagle, etc.  It's in my repository because the new version fixes Banshee (for me).

---

### Post by joakim2 on 2006-07-17
jryden@blade:/etc/apt$ banshee
Warning: [7/17/2006 7:10:34 PM] (Cannot connect to NetworkManager) - An available, working network connection will be assumed

** (/usr/lib/banshee/banshee.exe:27433): WARNING **: The following assembly referenced from /usr/lib/banshee/Banshee.Base.dll could not be loaded:
     Assembly:   Mono.Data.SqliteClient    (assemblyref_index=16)
     Version:    2.0.0.0
     Public Key: 0738eb9f132ed756
The assembly was not found in the Global Assembly Cache, a path listed in the MONO_PATH environment variable, or in the location of the executing assembly (/usr/lib/banshee).


** (/usr/lib/banshee/banshee.exe:27433): WARNING **: The class Mono.Data.SqliteClient.SqliteCommand could not be loaded, used in Mono.Data.SqliteClient, Version=2.0.0.0, Culture=neutral, PublicKeyToken=0738eb9f132ed756

** ERROR **: file class.c: line 2505 (mono_class_setup_parent): should not be reached
aborting...
Aborted

---

### Post by RAOF on 2006-07-17
Yup, that's one of the things I'm working on.  The Banshee pakcage is currently missing a dependency on libmono-sqlite2.0-cil.  If you install that package manually, Banshee should work.

Currently my repo is a bit broken with things like that.  I'll post back when I've managed to iron everything out.

---

### Post by joakim2 on 2006-07-17
> **RAOF said:**
> Yup, that's one of the things I'm working on.  The Banshee pakcage is currently missing a dependency on libmono-sqlite2.0-cil.  If you install that package manually, Banshee should work.

Currently my repo is a bit broken with things like that.  I'll post back when I've managed to iron everything out.

I forgive you ;)

No seriously dude, thanks for providing the packages. If you want them hosted on a faster (much faster) connection, let me know.

---

### Post by gurgle on 2006-07-17
more mirrors would be very welcome. thanks again raof, your repo is awesome. 

hmmmm banshee is still not launching for me. any ideas? i open up the app and its thinks for a bit, then it just doesnt open :(

---

### Post by RAOF on 2006-07-18
> **joakim2 said:**
> I forgive you ;)

No seriously dude, thanks for providing the packages. If you want them hosted on a faster (much faster) connection, let me know.
My repository is already mirrored by Doc.Horn (that's the ubuntu.moshen.de mirror), but more mirrors are always welcome :).  All I need is rsync & an ssh account.

But I tend not to sync with moshen while my repository is a bit broken.  I'll fix it, **then** I'll sync.  It takes a little while, too - the repository has grown somewhat - it's now 600mb or so.  Maybe it's time to clean out some of the older packages ;)

Rather than try and fix everyone's Banshee in here, I've created a [new thread]("http://www.ubuntuforums.org/showthread.php?t=218037").  If you want help fixing your Banshee, post in there :)

---

### Post by jonah1980 on 2006-07-20
still desperate for scribus-ng (3.2 or whatever) as can't open old files from previous computer and also can you add latest version of tellico as i also can't open files on new system as it's not new enough tellico in 64bit dapper

please... please...

---

### Post by RAOF on 2006-07-20
> **jonah1980 said:**
> still desperate for scribus-ng (3.2 or whatever) as can't open old files from previous computer and also can you add latest version of tellico as i also can't open files on new system as it's not new enough tellico in 64bit dapper

please... please...
Ok.  I'll build scribus-ng & tellico from Debian unstable & add it to my repository.  My ADSL router is somewhat stuffed at the moment (anyone have suggestions for a new one? :)), though, so it might be some time before it makes it out to the mirrors.  It'll probably take until the weekend until things are sorted out.

---

### Post by jonah1980 on 2006-07-20
wow your the nicest person i've ever met!! thanks so much - i know loads of people are after scribus-ng anyway, there's lots of requests on launchpad but not for 64bit.

thanks so so much, it'll mean a lot to me to be able to reopen the files i can't get into!

you're a king among humans!

---

### Post by jonah1980 on 2006-07-20
oh and this is my adsl router i've always been real happy with but i don't really know much about different ones!

[http://svp.co.uk/products-solo.php?pid=512](http://svp.co.uk/products-solo.php?pid=512)

---

### Post by RAOF on 2006-07-21
Ok...
[size=4]New in my repository: Scribus-ng (3.3.2) and Tellico (1.1.6)[/size]
Both taken from Debian unstable, and totally untested :).  Currently in the "misc" section.

Get 'em from the generously donated mirrors: [ubuntu.moshen.de](ubuntu.moshen.de) (German) and [ubuntu.systemadministrator.org](ubuntu.systemadministrator.org) (US).  Remember: killing the bandwidth of poor little raof.dyndns.org makes it more difficult for me to build packages ;)

---

### Post by s_spiff on 2006-07-21
cool one, only that more apps should be added [ latest releases ]. I go nuts trying to search programs for 64 bit arch. BTW any of the repo's have dc++ or dcpp..anything?

---

### Post by jonah1980 on 2006-07-21
you just made my year!! i can open all the old files from my old system now! wow thanks so much.

---

### Post by rogeriovinhal on 2006-07-21
I have made amd64 packages for tcl8.5, tk8.5, amsn 0.97b, gaim 2.0beta3.
All these packages were made with my distribution version (roger1). If you are interested to include them in your repository, just contact me.

But I haven't tested it in another computers, here it worked fine, but the debs may have some flaws, as they are my firsts.

---

### Post by s_spiff on 2006-07-21
RAOF , getting a error from the new repo :
> Failed to fetch [http://ubuntu.moshen.de/dists/dapper/Release](http://ubuntu.moshen.de/dists/dapper/Release)  Unable to find exp ected entry  {All/binary-amd64/Packages in Meta-index file (malformed Release fi le?)
Failed to fetch [http://ubuntu.systemadministrator.org/dists/dapper/Release](http://ubuntu.systemadministrator.org/dists/dapper/Release)  Unab le to find expected entry  {All/binary-amd64/Packages in Meta-index file (malfor med Release file?)
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used  instead.

I got the keys using the commands you have given on the frontpage. What am I doing wrong? [ btw i'm a newb ]

---

### Post by RAOF on 2006-07-22
> **s_spiff said:**
> RAOF , getting a error from the new repo :

I got the keys using the commands you have given on the frontpage. What am I doing wrong? [ btw i'm a newb ]
It's **possible** that you got them at a time when I was syncing those mirrors.  I'll have a look.

Anyone else having problems with the moshen or systemadministrator mirrors?

---

### Post by jonah1980 on 2006-07-22
ooh i've got another suggestion which might go down well, a newer version of inkscape, again the one shipped with 64bit is way old and it's also got a lot less features and different interface layout to new version. thanks.

---

### Post by Corbelius on 2006-08-03
Add Alltray and Glipper in the repository, check the homepage.

---

### Post by jamesford on 2006-08-03
wow alltray and glipper. they are such useful tools! thanks

may i request audacious?

---

### Post by Corbelius on 2006-08-03
> **jamesford said:**
> wow alltray and glipper. they are such useful tools! thanks

may i request audacious?

I can try :)


Add last-exit 2.0 and gaim-libnotify to repository, check my homepage.

Gaim-libnotify, and Dapper users, required this version of Gaim: [http://ubuntuforums.org/showpost.php?p=894777&postcount=56](http://ubuntuforums.org/showpost.php?p=894777&postcount=56)

---

### Post by jonah1980 on 2006-08-03
hi just tried to install last-exit the lastfm player thing, it installed and added to my apps menu but won't launch. says it's starting minimised in window bar and then dissapears and doesn't start up.

also i installed the gaim plugin for notifications but it's not in my plugins list in gaim, i can't see it at least anyway. thanks for any help.

also could we have a newest version of inkscape if poss!! hehe thanks.

---

### Post by jamesford on 2006-08-03
this last fm player is it like a media player? does it only play stream or mp3s too ? what about other audio streams? screenshot ?

---

### Post by Corbelius on 2006-08-03
> **jonah1980 said:**
> hi just tried to install last-exit the lastfm player thing, it installed and added to my apps menu but won't launch. says it's starting minimised in window bar and then dissapears and doesn't start up.

Someone has had the same problem? however start last-exit from the command line and report the error.

> also i installed the gaim plugin for notifications but it's not in my plugins list in gaim, i can't see it at least anyway. thanks for any help.

also could we have a newest version of inkscape if poss!! hehe thanks.

Have you restarted gaim?

> **jamesford said:**
> this last fm player is it like a media player? does it only play stream or mp3s too ? what about other audio streams? screenshot ?

[http://www.last.fm/listen/](http://www.last.fm/listen/) :)

[http://ubuntuforums.org/showthread.php?t=213185&highlight=last-exit](http://ubuntuforums.org/showthread.php?t=213185&highlight=last-exit)

[http://ubuntuforums.org/showthread.php?t=212828&highlight=last-exit](http://ubuntuforums.org/showthread.php?t=212828&highlight=last-exit)

---

### Post by jonah1980 on 2006-08-03
thanks, seems mono isn't installed that's why last-exit isn't working, so just installing mono now.

i have restarted gaim and it's still not in the list though, unless it appears under a diff name?

> **Corbelius said:**
> Someone has had the same problem? however start last-exit from the command line and report the error.



Have you restarted gaim?



[http://www.last.fm/listen/](http://www.last.fm/listen/) :)

[http://ubuntuforums.org/showthread.php?t=213185&highlight=last-exit](http://ubuntuforums.org/showthread.php?t=213185&highlight=last-exit)

[http://ubuntuforums.org/showthread.php?t=212828&highlight=last-exit](http://ubuntuforums.org/showthread.php?t=212828&highlight=last-exit)

---

### Post by jonah1980 on 2006-08-03
ah wasn't as simple as installing mono - got this error now:

> jonah@jonah-desktop:~$ last-exit

** (/usr/lib/last-exit/last-exit.exe:17546): WARNING **: The following assembly referenced from /usr/lib/last-exit/last-exit.exe could not be loaded:
     Assembly:   gnome-sharp    (assemblyref_index=6)
     Version:    2.8.0.0
     Public Key: 35e10195dab3c99f
The assembly was not found in the Global Assembly Cache, a path listed in the MONO_PATH environment variable, or in the location of the executing assembly (/usr/lib/last-exit).


** (/usr/lib/last-exit/last-exit.exe:17546): WARNING **: The class Gnome.Program could not be loaded, used in gnome-sharp, Version=2.8.0.0, Culture=neutral, PublicKeyToken=35e10195dab3c99f

** ERROR **: file class.c: line 2505 (mono_class_setup_parent): should not be reached
aborting...
Aborted


---

### Post by jamesford on 2006-08-03
thanks for hte info. its not for me i think.i was hoping it would be something like [screamer radio]("http://www.screamer-radio.com/") for windows. it was neat and could record any stream u threw at it

---

### Post by jonah1980 on 2006-08-03
streamtuner is awesome for streams/radio etc

---

### Post by Corbelius on 2006-08-04
> **jonah1980 said:**
> 

i have restarted gaim and it's still not in the list though, unless it appears under a diff name?

Libnotify-popups in the menu-plugins of Gaim.

> **jonah1980 said:**
> ah wasn't as simple as installing mono - got this error now:

Fix Last-Exit package, tnx for the report.

---

### Post by jamesford on 2006-08-07
the latest gnome sensors applet version seems to have some fixes  i need. *hopes it will magically appear in some repository* ;)

---

### Post by jonah1980 on 2006-08-07
> **Corbelius said:**
> Libnotify-popups in the menu-plugins of Gaim.



Fix Last-Exit package, tnx for the report.

Hi thanks for fixing that up, something still isn't right though. Last-exit plays and works but buffering seems bad, songs just stop and start and sometimes it'll play one song and then just stop and not play the next one.

---

### Post by jonah1980 on 2006-08-07
> **jonah1980 said:**
> Hi thanks for fixing that up, something still isn't right though. Last-exit plays and works but buffering seems bad, songs just stop and start and sometimes it'll play one song and then just stop and not play the next one.

It maybe just when the lastfm server was busy or something. the other thing i also noticed was that there's no icon in the menu shortcut it adds.

---

### Post by Corbelius on 2006-08-08
> **jonah1980 said:**
> the other thing i also noticed was that there's no icon in the menu shortcut it adds.

Strange... restart GNOME.

> **jamesford said:**
> the latest gnome sensors applet version seems to have some fixes  i need. *hopes it will magically appear in some repository* ;)

Done :shock: 

Update Last-Exit package, add savesong patch.

---

### Post by jonah1980 on 2006-08-09
Hi just wondered if RAOF or someone else wouldn't mind updating Scribus-ng/Scribus to version 1.3.3.3.

The program isn't updated that often but i read on their website today that this newer version was out with a load of bugfixes and it'd be cool if someone could update it in the repository for me and others. I use it a lot for work so fingers crossed. thanks guys if you can.

---

### Post by jamesford on 2006-08-09
Corbelius, thanks for the gnome-sensors but your latest package seems to be a bit broken on this system, the sensor icons are all replaced with little red crosses (like those we love so much in ie when an image cant be displayed)

---

### Post by RAOF on 2006-08-09
> **jonah1980 said:**
> Hi just wondered if RAOF or someone else wouldn't mind updating Scribus-ng/Scribus to version 1.3.3.3.

The program isn't updated that often but i read on their website today that this newer version was out with a load of bugfixes and it'd be cool if someone could update it in the repository for me and others. I use it a lot for work so fingers crossed. thanks guys if you can.

They're being pushed to my mirrors as I type this.  Bear in mind that I'm not sure whether the dependency info is entirely correct; the source package is written to use a **debhelper** version found only in Edgy, and Dapper's **debhelper** doesn't quite support all the things it's trying to do.

That said, it **should** work just fine.

---

### Post by jonah1980 on 2006-08-10
thanks your a top dude

---

### Post by Corbelius on 2006-08-10
> **jamesford said:**
> Corbelius, thanks for the gnome-sensors but your latest package seems to be a bit broken on this system, the sensor icons are all replaced with little red crosses (like those we love so much in ie when an image cant be displayed)

Try: sudo update-mime

---

### Post by jamesford on 2006-08-10
Corbelius, that didnt work :(
does it require me using a particular icon theme?
where are the icons located ?

---

### Post by jonah1980 on 2006-08-17
hi would anyone mind adding the latest blender to the repositories? the debs have already been made so maybe you could build from them easily? thanks if you can.

[http://www.ubuntuforums.org/showthread.php?t=238405](http://www.ubuntuforums.org/showthread.php?t=238405)

---

### Post by jonah1980 on 2006-08-17
also if poss can we get xara xtreme too:

[http://www.xaraxtreme.org/](http://www.xaraxtreme.org/)

the .package won't install for some reason.

as professionally i do design and graphics all these programs are a great alternative to having to use windows. scribus, inkscape, xara, blender etc.

will one day they accommodate all the packages you guys have made into the official repos, rather than doing ones in launchpad, can't they take yours?

---

### Post by RAOF on 2006-08-18
I perhaps should apply to become a Master Of The Universe, but that would mean my packages would need to get a bit cleaner :).

---

### Post by jonah1980 on 2006-08-18
that'd be awesome, you'd add so much more to ubuntu.

---

### Post by Corbelius on 2006-08-20
> **jamesford said:**
> Corbelius, that didnt work :(
does it require me using a particular icon theme?
where are the icons located ?

Sorry, i was in vacation ;)

Try this: [http://www.gnomefiles.org/comment.php?soft_id=715#5700](http://www.gnomefiles.org/comment.php?soft_id=715#5700)

---

### Post by jamesford on 2006-08-20
thanks Corbelius, gonna try a bit later :)
hope u had a nice vacation

btw u and RAOF are really making 64 bit a lot better, so thanks to you both !

there should be a sticky btw with all the good amd64 repos

---

### Post by fabertawe on 2006-08-21
> **jamesford said:**
> thanks Corbelius, gonna try a bit later :)
hope u had a nice vacation

btw u and RAOF are really making 64 bit a lot better, so thanks to you both !

there should be a sticky btw with all the good amd64 repos

I second this :) 

It would be great if someone could write a how-to on compiling for 64bit and creating debs. I can compile some things but I'm really doing the absolute basics and flying in the dark. Plus (I may have mentioned this before) we could all then contribute our debs to a single repo for the good of the 64bit community (at least have them posted in one thread).

Paul

---

### Post by jonah1980 on 2006-08-21
yeah i think this too.

i think like ubuntu themselves or a grouping of devs should set up a 64bit repo as a central location for everyone to post debs or use as a repository somehow. if everyone was using the same servers and mirrors then everyones hardwork would be available to all and it'd be easier for you guys.

you've made 64bit loads better, coupled with automatix it's not really far behind 32bit for most people.

---

### Post by Corbelius on 2006-08-31
I have update my repository, inserted Audacity-1.3.0beta (GTK2), and i have changed address and added GPG-key:

[http://www.janvitus.netsons.org/index.php?catid=3&blogid=1](http://www.janvitus.netsons.org/index.php?catid=3&blogid=1)

Feed: [http://www.janvitus.netsons.org/xml-rss2.php](http://www.janvitus.netsons.org/xml-rss2.php)

---

### Post by gurgle on 2006-09-04
can get to your repo, is it down?

---

### Post by Corbelius on 2006-09-05
> **gurgle said:**
> can get to your repo, is it down?

Provider problem, now it's all ok :)

I have inserted quod libet 0.22.1, tomorrow i insert the quodlibet-plugins.

---

### Post by Corbelius on 2006-09-07
> **Corbelius said:**
>  tomorrow i insert the quodlibet-plugins.

Done, and also i have inserted exaile and listen beta1.

---

### Post by jamesford on 2006-09-07
great job Corbelius, looking forward to trying these tonight

---

### Post by jonah1980 on 2006-09-07
hi i don't suppose anyone could maintain a 64bit optimized blender build, i can't seem to get it working and some folk having been struggling here:

[http://www.ubuntuforums.org/showthread.php?t=238405](http://www.ubuntuforums.org/showthread.php?t=238405)

---

### Post by jamesford on 2006-09-13
was wondering if one of you 64 bit gurus could make packages of one or more of the following torrent clients, as im rather fed up with azureus' resource usage and most of the other torrent clients such as transmission are a bit too simple for my taste with not very many options

[qbittorrent]("http://www.qbittorrent.org/") qt but nice features

[tribler]("http://www.tribler.org/") looks really interesting
[torrent swapper]("http://bit-torrent.sourceforge.net/") also looks like it could be useable

---

### Post by prince_niceguy on 2006-09-13
you are doing a great job!!! Kudos to you... 
Is it possible for you to put ntfs-3g and nautilus scripts to mount usb drives using ntfs-3g.

thanks in advance if you are able ;-)...

Any way thanks for maintaining the repos...

---

### Post by Corbelius on 2006-09-15
> **jamesford said:**
> 
[qbittorrent]("http://www.qbittorrent.org/") qt but nice features

[tribler]("http://www.tribler.org/") looks really interesting


mmm... other guys want them?

i prefer Transmission :)

> **prince_niceguy said:**
> you are doing a great job!!! Kudos to you... 
Is it possible for you to put ntfs-3g and nautilus scripts to mount usb drives using ntfs-3g.

thanks in advance if you are able ;-)...

Any way thanks for maintaining the repos...

I think is better to wait Edgy Eft stable...

---

### Post by Das Goat on 2006-09-20
dasgoat@Ubuntu-laptop:~$ wget [http://janvitus.netsons.org/ubuntu/E64649C6.gpg](http://janvitus.netsons.org/ubuntu/E64649C6.gpg) -O- | sudo apt-key add -
Password:--21:34:01--  [http://janvitus.netsons.org/ubuntu/E64649C6.gpg](http://janvitus.netsons.org/ubuntu/E64649C6.gpg)
           => `-'
Resolving janvitus.netsons.org... 213.202.245.196, 2001:470:1f00:363::3
Connecting to janvitus.netsons.org|213.202.245.196|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 3,804 (3.7K) [text/plain]

100%[====================================>] 3,804          4.31K/s

21:34:03 (4.31 KB/s) - `-' saved [3804/3804]


dasgoat@Ubuntu-laptop:~$ ## Janvitus Amd64 Repository
dasgoat@Ubuntu-laptop:~$ deb [http://janvitus.netsons.org/ubuntu/](http://janvitus.netsons.org/ubuntu/) dapper-janvitus all
bash: deb: command not found
dasgoat@Ubuntu-laptop:~$


No dice. What am I doing wrong?

---

### Post by kleeman on 2006-09-21
You really want to read up on the basics of repositories dasgoat!.:D :D 


That deb line you put in at the prompt goes in the file /etc/apt/sources.list
and you update your system at the prompt with
sudo apt-get update
sudo apt-get dist-upgrade

---

### Post by Das Goat on 2006-09-21
thanks Kleeman. I am so new I still have *that new car smell*

at least I am learing something, like how you edit that file :-) I'll get there eventually.

So I edited it and ran your commands:

Reading package lists... Done
W: GPG error: [http://janvitus.netsons.org](http://janvitus.netsons.org) dapper-janvitus Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 45B63ECEE64649C6
W: You may want to run apt-get update to correct these problems

is this a problem? sudo apt-get dist-upgrade
 seemed to work with out errors

I also re-ran wget [http://janvitus.netsons.org/ubuntu/E64649C6.gpg](http://janvitus.netsons.org/ubuntu/E64649C6.gpg) -O- | sudo apt-key add -

this is the output:

Length: 3,804 (3.7K) [text/plain]

100%[====================================>] 3,804         --.--K/s

19:55:21 (1.99 MB/s) - `-' saved [3804/3804]

gpg: no ultimately trusted keys found
OK

so, did I do it correctly? and, in a nut shell, what have I done? I undertand that I added this place as a repository to get files from, but what does that do for me?

---

### Post by aceracer24 on 2006-09-21
you missed the deb part in source.list, cut and paste from deb all the way to all at the end.  

deb [http://janvitus.netsons.org/ubuntu/](http://janvitus.netsons.org/ubuntu/) dapper-janvitus all

and possible that his repo was down at the time. As for 

```
gpg: no ultimately trusted keys found
OK
``` don't worry about that.

---

### Post by kleeman on 2006-09-21
Looks good to me. Here's what happens:
sudo apt-get update  THIS REVISES THE LIST OF PACKAGES YOU HAVE AVAILABLE TO INSTALL
sudo apt-get dist-upgrade THIS COMPLETELY UPDATES YOUR PACKAGES FROM YOUR LIST. YOU NEED TO RUN THE PREVIOUS COMMAND TO MAKE CORBELIUS STUFF AVAILABLE.

Use synaptic to browse through the possible new packages you have in your newly added repository once you do the first command above. You could instead just use synaptic for everything. The reload button does the first command while the "mark upgrades" does the second.

---

### Post by Corbelius on 2006-09-25
I have inserted new Gnomebaker 0.6 (new great version) and DC# (direct connect client write in mono [http://mono.dcsharp.com/](http://mono.dcsharp.com/) ).

---

### Post by gurgle on 2006-09-25
Can someone write a XGL/compiz that works with RAOF's repo? I would prefer a session method so I can easily switch between the 2.

---

### Post by RAOF on 2006-09-26
New in my dapper repository: mythtv 0.20, built from the new edgy sources!  Also mythplugins 0.20.

---

### Post by gurgle on 2006-09-26
thanks raof. will the mirrors be updated soon?

---

### Post by fabertawe on 2006-09-27
> **RAOF said:**
> New in my dapper repository: mythtv 0.20, built from the new edgy sources!  Also mythplugins 0.20.

Hi RAOF,

I've just tried updating but I'm getting this error
```
E:/var/cache/apt/archives/mythtv-frontend_0.20-0.0ubuntu1_amd64.deb: trying to overwrite `/usr/bin/mythlcdserver', which is also in package mythtv-lcdserver
```
which then leaves me in a cycle (see attached image) with a broken software index
```
It is impossible to install or remove any software. Please use the package manager "Synaptic" or run "sudo apt-get install -f" in a terminal to fix this issue at first.
```

Any ideas?

Cheers ... Paul

EDIT: by fiddling in Synaptic I've got it working (0.20) but the plugins are still 0.19.

---

### Post by Das Goat on 2006-09-28
Does anyone know if there is a 64 bit audio player that will mimic RealPlayer10 for live streaming Audio? I usually listen to NPR while I work, but that doesn't seem possible with all of the players I have tried so far, even the XMMS player that came with my 6.06 ubuntu.](*,)

---

### Post by jamesford on 2006-09-28
u can easily install real player 32 bit with  --force-architecture

---

### Post by jamesford on 2006-09-28
Corbelius  hpow about the brand new exaile 0.2.4 ?
the new features sound exciting

---

### Post by Corbelius on 2006-09-29
> **jamesford said:**
> Corbelius  hpow about the brand new exaile 0.2.4 ?
the new features sound exciting

Done, and inserted new last-exit 3.0.

---

### Post by jamesford on 2006-09-29
thanks a lot!

---

### Post by sha_man on 2006-09-29
hello, thanks for your repos!

Could you also add the latest VLC releases? :D

---

### Post by Das Goat on 2006-09-29
Automatix, loading it is the answer! I figured it out and installed. during the updated i grabbed everything 64 bit. i don't recommend this, as it took more than two hours to get it all and install everything. Now i have more apps than you can shake a stick at. But the best part is it loaded all of the missing Mplayer plug ins for FireFox. And now my NPR audio works, at least if you pick the Windows Media format. I haven't tried other formats yet. unfortunately, there are no controls, so I can't skip to the next story if I want, but at least it is something.

---

### Post by Das Goat on 2006-10-02
Has anyone gotten WINE to install on 64-bit? I followed the directions on the  WINE page, but it crashed:

Failed to fetch [http://wine.budgetdedicated.com/apt/dists/dapper/main/binary-amd64/Packages.gz](http://wine.budgetdedicated.com/apt/dists/dapper/main/binary-amd64/Packages.gz)  404 Not Found
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.
dasgoat@dasgoat-laptop:~$ sudo apt-get install wine
Reading package lists... Done
Building dependency tree... Done
Package wine is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package wine has no installation candidate
dasgoat@dasgoat-laptop:~$

:-k

---

### Post by Das Goat on 2006-10-02
Ah, some poking and I find that I should be pointing to [http://wine.budgetdedicated.com/apt/dists/dapper/main/binary-all/Packages.gz](http://wine.budgetdedicated.com/apt/dists/dapper/main/binary-all/Packages.gz)

But i don't know how to make the script that runs do that.....

---

### Post by jonah1980 on 2006-10-03
hi, RAOF i wondered if you could kindly updated scribus in your repository from 1.3.3.3 as they've just release 1.3.3.4.

much appreciated if you can, it's great to be able to keep upto date on 64bit with scribus as they're updates always show really useful improvements. thanks

---

### Post by Corbelius on 2006-10-03
> **Das Goat said:**
> Ah, some poking and I find that I should be pointing to [http://wine.budgetdedicated.com/apt/dists/dapper/main/binary-all/Packages.gz](http://wine.budgetdedicated.com/apt/dists/dapper/main/binary-all/Packages.gz)

But i don't know how to make the script that runs do that.....

Wine does not have a deb package for amd64, you must force the installation of i386 package.

---

### Post by s_spiff on 2006-10-12
was looking for dc++, but yu gave a good substitute. Thanks for the repo man. Downloading the stuff right now.

---

### Post by Corbelius on 2006-10-12
Update to Edgy Eft:

```
deb http://janvitus.netsons.org/ubuntu/ edgy-janvitus all
```

---

### Post by RAOF on 2006-10-12
> **jonah1980 said:**
> hi, RAOF i wondered if you could kindly updated scribus in your repository from 1.3.3.3 as they've just release 1.3.3.4.

much appreciated if you can, it's great to be able to keep upto date on 64bit with scribus as they're updates always show really useful improvements. thanks

Hey, they've actually got the latest Scribus-ng in Edgy's Universe repository.  Cool.

As you probably want to stay on Dapper, I'll build that package with Dapper dependencies :).

---

### Post by jonah1980 on 2006-10-13
THANKS RAOF... I'm gonna move on to edgy on one of my machines but keep the other nice and stable on dapper for now.

---

### Post by s_spiff on 2006-10-19
is there a problem with the repos or something? i cant get the list of your repo. it gets stuck here :
```


Err http://janvitus.netsons.org dapper-janvitus Release.gpg
  Cannot initiate the connection to janvitus.netsons.org:80 (2001:470:1f00:363::3). - connect (101  Network is unreachable) [IP: 2001:470:1f00:363::3 80]

99% [Connecting to janvitus.netsons.org (213.202.245.196)]


```i followed the exact procedures. it worked untill day before yesterday too.  am i doing something wrong here?

---

### Post by kopilo on 2006-10-19
I'm getting something similar...```
Err http://janvitus.netsons.org dapper-janvitus Release.gpg
  Cannot initiate the connection to janvitus.netsons.org:80 (2001:470:1f00:363::3). - connect (101 Network is unreachable) [IP: 2001:470:1f00:363::3 80]

``` I'm thinking the repository is down or something...

---

### Post by Corbelius on 2006-10-19
Strange... i don't have problems:

```
	
Ign http://archive.ubuntu.com edgy-backports/multiverse Translation-it
**Get:6 http://janvitus.netsons.org dapper-janvitus Release.gpg [189B]**
Hit http://archive.ubuntu.com edgy Release               
Hit http://archive.ubuntu.com edgy-updates Release                        
Hit http://archive.ubuntu.com edgy-backports Release                      
Ign http://janvitus.netsons.org dapper-janvitus/all Translation-it        
**Get:7 http://janvitus.netsons.org edgy-janvitus Release.gpg [189B]**
Hit http://archive.ubuntu.com edgy/main Packages         
Ign http://janvitus.netsons.org edgy-janvitus/all Translation-it
Hit http://janvitus.netsons.org dapper-janvitus Release
Hit http://janvitus.netsons.org edgy-janvitus Release    
```

---

### Post by kopilo on 2006-10-19
Something wrong with the connection from my end.. Maybe firewall?
```
ping janvitus.netsons.org
PING server.netsons.org (213.202.245.196) 56(84) bytes of data.

--- server.netsons.org ping statistics ---
32 packets transmitted, 0 received, 100% packet loss, time 31037ms

```
I'll turn the router's firewall off, test and make an edit here.

Nope no difference...
```
ping -c 5 janvitus.netsons.org
PING server.netsons.org (213.202.245.196) 56(84) bytes of data.

--- server.netsons.org ping statistics ---
5 packets transmitted, 0 received, 100% packet loss, time 4001ms
```

---

### Post by Corbelius on 2006-10-22
Mmm... you can download any files form web? [http://www.janvitus.netsons.org/ubuntu/dists/edgy-janvitus/gnome/](http://www.janvitus.netsons.org/ubuntu/dists/edgy-janvitus/gnome/)

---

### Post by Corbelius on 2006-11-14
I have changed the address of the repository for edgy, the new is:

[http://janvitus.cabspace.com/](http://janvitus.cabspace.com/)

To add to your sources.list:

```
deb http://janvitus.cabspace.com/ edgy-janvitus all
```

For dapper remain the old link, see first message in this topic.

I have uploaded some packages, new glipper, xvidcap, gwget and others.

---

### Post by kopilo on 2006-11-14
> **Corbelius said:**
> Mmm... you can download any files form web? [http://www.janvitus.netsons.org/ubuntu/dists/edgy-janvitus/gnome/](http://www.janvitus.netsons.org/ubuntu/dists/edgy-janvitus/gnome/)

No. >_<
"Firefox can't establish a connection to the server at www.janvitus.netsons.org."

---

### Post by Corbelius on 2006-11-14
> **kopilo said:**
> No. >_<
"Firefox can't establish a connection to the server at www.janvitus.netsons.org."

Try this:

```
wget http://janvitus.cabspace.com/E64649C6.gpg -O- | sudo apt-key add -
```

Add this to ur sources.list:

```
## Janvitus Amd64 Repository
deb http://janvitus.cabspace.com/ edgy-janvitus all
```

---

### Post by RFScheer on 2006-11-14
Confirming - works for me on Edgy 64.

---

### Post by kopilo on 2006-11-15
> **Corbelius said:**
> Try this:

```
wget http://janvitus.cabspace.com/E64649C6.gpg -O- | sudo apt-key add -
```

Seems to hang on "sudo apt-key add-"

```
kopilo@integra:~$ wget http://janvitus.cabspace.com/E64649C6.gpg -O- | sudo apt-key add - Password:--15:51:13--  http://janvitus.cabspace.com/E64649C6.gpg
           => `-'
Resolving janvitus.cabspace.com... 65.175.85.100
Connecting to janvitus.cabspace.com|65.175.85.100|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 4,594 (4.5K) [text/plain]

100%[=================================================================================================================>] 4,594         16.02K/s

15:51:14 (16.01 KB/s) - `-' saved [4594/4594]
```


[quote=Corbelius]
Add this to ur sources.list:

```
## Janvitus Amd64 Repository
deb http://janvitus.cabspace.com/ edgy-janvitus all
```[/QUOTE]
Sorry, I'm running drapper due to video card difficulties. >_<

Ok found a way around it
```

wget http://janvitus.cabspace.com/E64649C6.gpg
sudo apt-key add E64649C6.gpg
sudo rm E64649C6.gpg

```

EDIT: However it still doesn't connnect on aptitude update
or [http://www.janvitus.netsons.org/](http://www.janvitus.netsons.org/)

---

### Post by flapane on 2006-11-15
even xvidcap... ^^
sei grande

---

### Post by Corbelius on 2006-11-15
> **kopilo said:**
> 

EDIT: However it still doesn't connnect on aptitude update
or [http://www.janvitus.netsons.org/](http://www.janvitus.netsons.org/)

Sorry, Netsons hosting has many problems in these days.

I have inserted brasero 0.5.1 in the repository, i have enable libburn: [http://www.janvitus.netsons.org/index.php?itemid=52](http://www.janvitus.netsons.org/index.php?itemid=52)

Install schema file and check gconf-editor for enable it (raccomend to install cdrkin).

Download schema file: [http://www.janvitus.netsons.org/varie/brasero_schemas.tar.bz2](http://www.janvitus.netsons.org/varie/brasero_schemas.tar.bz2)

Install: gconftool --install-schema-file=/path/to/brasero.schemas

Example:

[IMG]http://img220.imageshack.us/img220/4701/schermatazc0.png[/IMG]

---

### Post by kopilo on 2006-11-15
Ok I've installed branso into gconf-editor.. now what?

---

### Post by Corbelius on 2006-11-17
See the image and check the box with libburn options.

---

### Post by Corbelius on 2006-11-21
I don't have lucky with the hosting providers, cabspace has closed, i'm returned on Netsons, see the first message:

[http://ubuntuforums.org/showpost.php?p=1134877&postcount=1](http://ubuntuforums.org/showpost.php?p=1134877&postcount=1)

New quod libet 0.24 is up.

---

### Post by xopher on 2006-11-21
Hi! I have a suggestion for the gnome-sensors-applet package; could you use the alternative icons epicbard offers? With the green temperature as normal temp. I dont like looking at orange when things are supposed to be normal ;)

normal: [IMG]http://www.kolumbus.fi/jacce/normal-temp-icon.png[/IMG]
high: [IMG]http://www.kolumbus.fi/jacce/high-temp-icon.png[/IMG]

---

### Post by Corbelius on 2006-11-22
> **xopher said:**
> Hi! I have a suggestion for the gnome-sensors-applet package; could you use the alternative icons epicbard offers? With the green temperature as normal temp. I dont like looking at orange when things are supposed to be normal ;)

normal: [IMG]http://www.kolumbus.fi/jacce/normal-temp-icon.png[/IMG]
high: [IMG]http://www.kolumbus.fi/jacce/high-temp-icon.png[/IMG]

Good icons, inserted in the new sensors-applet package: [http://www.janvitus.netsons.org/index.php?itemid=54](http://www.janvitus.netsons.org/index.php?itemid=54)

Tnx :)

---

### Post by jamesford on 2006-11-22
thanks for the updates corbelius

---

### Post by flapane on 2006-11-24
Impossibile ottenere [http://www.janvitus.netsons.org/ubuntu/dists/edgy-janvitus/Release.gpg](http://www.janvitus.netsons.org/ubuntu/dists/edgy-janvitus/Release.gpg)  Impossibile iniziare la connessione a [www.janvitus.netsons.org:80](www.janvitus.netsons.org:80) (2001:470:1f00:363::4). - connect (101 La rete è irraggiungibile) [IP: 2001:470:1f00:363::4 80]

---

### Post by rhomp2002 on 2006-11-25
Did this and got this response:

dick@breezydapper:~$ wget [http://janvitus.cabspace.com/E64649C6.gpg](http://janvitus.cabspace.com/E64649C6.gpg) -O- | sudo apt-key add -
--15:38:55--  [http://janvitus.cabspace.com/E64649C6.gpg](http://janvitus.cabspace.com/E64649C6.gpg)
           => `-'
Resolving janvitus.cabspace.com... 209.86.66.92, 209.86.66.93, 209.86.66.94, ...
Connecting to janvitus.cabspace.com|209.86.66.92|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://earthlink-help.net/?d=error_earthlink-bf&q=janvitus.cabspace.com](http://earthlink-help.net/?d=error_earthlink-bf&q=janvitus.cabspace.com) [following]
--15:38:55--  [http://earthlink-help.net/?d=error_earthlink-bf&q=janvitus.cabspace.com](http://earthlink-help.net/?d=error_earthlink-bf&q=janvitus.cabspace.com)
           => `-'
Resolving earthlink-help.net... 72.30.33.102
Connecting to earthlink-help.net|72.30.33.102|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/html]

    [  <=>                                ] 13,850        67.61K/s             

15:38:56 (67.44 KB/s) - `-' saved [13850]

gpg: no valid OpenPGP data found.


Any ideas as to how to get a valid OpenPGP?

---

### Post by Corbelius on 2006-11-26
> **flapane said:**
> Impossibile ottenere [http://www.janvitus.netsons.org/ubuntu/dists/edgy-janvitus/Release.gpg](http://www.janvitus.netsons.org/ubuntu/dists/edgy-janvitus/Release.gpg)  Impossibile iniziare la connessione a [www.janvitus.netsons.org:80](www.janvitus.netsons.org:80) (2001:470:1f00:363::4). - connect (101 La rete è irraggiungibile) [IP: 2001:470:1f00:363::4 80]

E' netsons che ogni tanto va in timeout o è irrangiungibile, non posso farci nulla, sto cercando da tempo un buon host gratuito :)

> **rhomp2002 said:**
> Did this and got this response:


Any ideas as to how to get a valid OpenPGP?


See the first message in this topic: [http://ubuntuforums.org/showpost.php?p=1134877&postcount=1](http://ubuntuforums.org/showpost.php?p=1134877&postcount=1)

```
wget http://www.janvitus.netsons.org/ubuntu/E64649C6.gpg -O- | sudo apt-key add -
```

;)

---

### Post by flapane on 2006-11-27
altervista.org ;)

---

### Post by Corbelius on 2006-11-28
I hope this wold be the last time I change the address of my repository. This wolud be the definitive one, maybe this time i'll be lucky. You can find the new address here:

[http://ubuntuforums.org/showpost.php?p=1134877&postcount=1](http://ubuntuforums.org/showpost.php?p=1134877&postcount=1)

[http://www.janvitus.netsons.org/index.php?itemid=56](http://www.janvitus.netsons.org/index.php?itemid=56)

To surf my repository add "index.html" at the end of the URL, Interfree doesn't support PHP.

---

### Post by rhomp2002 on 2006-11-28
If you look at what I copied in, that is what I entered in the Terminal and I got the message that:

gpg: no valid OpenPGP data found.

I still can't get a valid Open PGP using the entry you mentioned.   That was the whole question.

---

### Post by rhomp2002 on 2006-11-29
Finally got it to work.   All set now.  Thanks for the help.:mrgreen: :mrgreen:

---

### Post by Corbelius on 2006-11-30
> **rhomp2002 said:**
> Finally got it to work.   All set now.  Thanks for the help.:mrgreen: :mrgreen:

Fine :)

I add muine 0.8.6, dcsharp 0.9 and tomboy 0.5.1 to the repsoitory.

---

### Post by jonah1980 on 2006-12-05
hi guys - i just got 1.3.3.6 version at work on windows office machine of scribus which is out today, i was hoping if i asked nice raof or someone would update to this version in the 64 repositories so i can use it at home (i don't have windows). i use it professionally instead of quark or indesign (which i used to use) and every small update is worth so much in usability and bug fixes with this app. thanks guys...

---

### Post by kleeman on 2006-12-05
If you check the scribus webpage you will see they have extensive support for Debian/Ubuntu but the latest version there is only 1.3.3.5. I will build 1.3.3.6 for amd64 when it is updated. I use it all the time as well.

---

### Post by jonah1980 on 2006-12-05
thanks that's awesome... should be there very soon with the windows version already there

---

### Post by flapane on 2006-12-06
maybe you want to add my valknut packages [http://www.ubuntuforums.org/showthread.php?t=312403](http://www.ubuntuforums.org/showthread.php?t=312403) which are better thant old official repo ones. (maybe ask also to the mate who compiled wine amd64 [http://www.ubuntuforums.org/showthread.php?t=297280](http://www.ubuntuforums.org/showthread.php?t=297280))

---

### Post by Corbelius on 2006-12-10
> **flapane said:**
> maybe you want to add my valknut packages [http://www.ubuntuforums.org/showthread.php?t=312403](http://www.ubuntuforums.org/showthread.php?t=312403) which are better thant old official repo ones. (maybe ask also to the mate who compiled wine amd64 [http://www.ubuntuforums.org/showthread.php?t=297280](http://www.ubuntuforums.org/showthread.php?t=297280))

Have you .dsc e .diff.gz files?


Update: inserted Beagle 0.2.13 in the repository.

---

### Post by flapane on 2006-12-10
no, now I only have the debs file you can download from that link, maybe diff files can be found on the developer web site

---

### Post by jonah1980 on 2006-12-11
hey guys, will any of you be adding feisty repos anytime soon for any of us itching to check it out?

---

### Post by jamesford on 2006-12-11
any 64 bit debs for vlc 0.8.6 yet anywhere?

---

### Post by RAOF on 2006-12-12
> **jonah1980 said:**
> hey guys, will any of you be adding feisty repos anytime soon for any of us itching to check it out?

Already done so :p.  I've been on feisty for a couple of weeks now :).

---

### Post by jonah1980 on 2006-12-12
hey RAOF, i still daren't update but good work. it'll be nice knowing that as soon as feisty is stable everyone will have 64bit packages and not be at a disadvantage like we have been in the past...

i was gonna try feisty just on my laptop but loads of folk warned me it would certainly break it and would get more and more unstable and messy after christmas until they broke away from debian...?

---

### Post by RAOF on 2006-12-12
> **jonah1980 said:**
> hey RAOF, i still daren't update but good work. it'll be nice knowing that as soon as feisty is stable everyone will have 64bit packages and not be at a disadvantage like we have been in the past...

i was gonna try feisty just on my laptop but loads of folk warned me it would certainly break it and would get more and more unstable and messy after christmas until they broke away from debian...?

Works for me (tm).  At least, once it became bootable :).

---

### Post by jonah1980 on 2006-12-14
hey guys could anyone please add new f-spot to the repos, 0.3 or whatever version. this would be cool, was using picasa but wanted to try fspot for a bit instead... thanks.

---

### Post by Corbelius on 2006-12-14
> **jonah1980 said:**
> hey guys could anyone please add new f-spot to the repos, 0.3 or whatever version. this would be cool, was using picasa but wanted to try fspot for a bit instead... thanks.

[http://www.janvitus.netsons.org/index.php?itemid=62](http://www.janvitus.netsons.org/index.php?itemid=62) :rolleyes:

---

### Post by jkroto on 2006-12-15
> **Corbelius said:**
> Hi, from this idea - [http://ubuntuforums.org/showthread.php?t=48905&highlight=corbelius](http://ubuntuforums.org/showthread.php?t=48905&highlight=corbelius) - i have created this repository online for amd64 

Problem with Listen?
Thanks for the repository.  I have added several programs from it which all appear to work fine except the new .5 Listen.  The new version will not allow me to add songs to playlists.  Also, it does not recognize all the playlists on my i-pod as the old version did.
Any suggestions?  I have reverted back to the old version for now.
5G I-pod
Edgy AMD 64

---

### Post by Corbelius on 2006-12-16
> **jkroto said:**
> Problem with Listen?
Thanks for the repository.  I have added several programs from it which all appear to work fine except the new .5 Listen.  The new version will not allow me to add songs to playlists.  Also, it does not recognize all the playlists on my i-pod as the old version did.
Any suggestions?  I have reverted back to the old version for now.
5G I-pod
Edgy AMD 64

My package or listen version 0.5beta1?

---

### Post by flapane on 2006-12-16
so what about my valknut packages?

---

### Post by jkroto on 2006-12-16
> **Corbelius said:**
> My package or listen version 0.5beta1?

Honestly I don't know.  I am using several of your other packages and having no problems.  I am using your Listen package but I'm not suggesting it has anything to do with the package, only that there may be a problem with the program.
I was wondering if you had heard any other comments similar?
Thanks.

---

### Post by Corbelius on 2006-12-18
> **flapane said:**
> so what about my valknut packages?

I can't download it, have u dsc and diff files? however for DC net, I prefer dcsharp: [http://www.janvitus.netsons.org/index.php?itemid=40](http://www.janvitus.netsons.org/index.php?itemid=40)

> **jkroto said:**
> Honestly I don't know.  I am using several of your other packages and having no problems.  I am using your Listen package but I'm not suggesting it has anything to do with the package, only that there may be a problem with the program.
I was wondering if you had heard any other comments similar?
Thanks.

[http://ubuntuforums.org/showthread.php?p=1541738&highlight=ipod#post1541738](http://ubuntuforums.org/showthread.php?p=1541738&highlight=ipod#post1541738)

---

### Post by jkroto on 2006-12-18
> **Corbelius said:**
> 
[http://ubuntuforums.org/showthread.php?p=1541738&highlight=ipod#post1541738](http://ubuntuforums.org/showthread.php?p=1541738&highlight=ipod#post1541738)

Thanks for the idea.  I actually do have the latest version of python-gpod installed.  I guess I must have a problem isolated to me.  I think I'll wait until we are out of the beta version.

Thanks again for the repo's, makes working with64-bit that much easier.

---

### Post by flapane on 2006-12-18
> **flapane said:**
> so what about my valknut packages?

fixed the links [http://www.kde-apps.org/content/show.php?content=49574](http://www.kde-apps.org/content/show.php?content=49574)

---

### Post by gurgle on 2006-12-19
is the new Banshee going to be available from anyone repo soon? :)

---

### Post by Corbelius on 2006-12-27
> **gurgle said:**
> is the new Banshee going to be available from anyone repo soon? :)

I have problem to compile banshee-official-plugins.

However I have added rhythmbox 0.9.7 (with libgpod 0.4.0 support) in the edgy repository.

Added also Compiz from Feisty.

---

### Post by jonah1980 on 2006-12-31
hi i wondered if anyone would be kind enough to add the kiba-dock. i installed it from an amd64 deb somewhere on these forums but there's no themes, i can't get it to look right and i can't remove the black borders, even when i 've got it set on rounded corners mode...

---

### Post by jonah1980 on 2006-12-31
here's my screenshot. i figure with a proper package in the repos we could have it looking sweet from the off and all working right with beryl/xgl/compiz whatever. and there could be profiles/themes or icons in already or something. all i know is these docks look pretty cool and it'd be nice to be able to just install one of them from synaptic...

any suggestions or anyone up for doing it?

---

### Post by jonah1980 on 2007-01-03
[http://www.gnome-dock.org/trac](http://www.gnome-dock.org/trac)

or this might be even better - at least it's a gnome build dock so would fit nice with ubuntu!

---

### Post by Corbelius on 2007-01-03
Both are much unstable, waitin' for a stable version.

---

### Post by rajeev1204 on 2007-01-03
Hi

do u have gyachi for amd 64?



regards

rajeev

---

### Post by janfsd on 2007-01-03
Could you add a zsnes package to your repositories?

---

### Post by flapane on 2007-01-04
> **janfsd said:**
> Could you add a zsnes package to your repositories?

+1

---

### Post by Corbelius on 2007-01-05
> **janfsd said:**
> Could you add a zsnes package to your repositories?

This work only on the i386 platform :/

---

### Post by janfsd on 2007-01-05
> **Corbelius said:**
> This work only on the i386 platform :/

Well, actually not, there are some binaries at the zsnes forum for amd64:
[http://board.zsnes.com/phpBB2/viewtopic.php?t=9179](http://board.zsnes.com/phpBB2/viewtopic.php?t=9179)

And it's possible to compile zsnes on AMD64, with the -m32 flag.

---

### Post by fabertawe on 2007-01-08
> **rajeev1204 said:**
> Hi

do u have gyachi for amd 64?


Get Gyachi and kiba-dock [**here**]("http://www.ubuntuforums.org/showthread.php?t=295197").

Paul

---

### Post by Corbelius on 2007-01-09
> **janfsd said:**
> Well, actually not, there are some binaries at the zsnes forum for amd64:
[http://board.zsnes.com/phpBB2/viewtopic.php?t=9179](http://board.zsnes.com/phpBB2/viewtopic.php?t=9179)

And it's possible to compile zsnes on AMD64, with the -m32 flag.

Install ia32-libs-sdl package, download [http://nsrt.edgeemu.com/zsnes-1.5-athlon64.tar.gz](http://nsrt.edgeemu.com/zsnes-1.5-athlon64.tar.gz) , extract and move in /usr/bin directory, start zsnes from console, or make a shortcourt :)

---

### Post by jamesford on 2007-01-09
corbelius, thanks for the great packages u keep making available. just wondering if you could add deluge? i dunno whats up with their repos but i cant get any of then to work, and the packages in them arent up2date either, and im having problems compiling them myself

---

### Post by Corbelius on 2007-01-10
> **jamesford said:**
> corbelius, thanks for the great packages u keep making available. just wondering if you could add deluge? i dunno whats up with their repos but i cant get any of then to work, and the packages in them arent up2date either, and im having problems compiling them myself

You can download it from debian unstable repo: [http://packages.debian.org/unstable/net/deluge-torrent](http://packages.debian.org/unstable/net/deluge-torrent)

Work on Edgy Eft, however is up in my repo.

[http://www.janvitus.netsons.org/2007/01/09/new-gpg-key-and-repository-nuova-chiave-gpg-e-repository/](http://www.janvitus.netsons.org/2007/01/09/new-gpg-key-and-repository-nuova-chiave-gpg-e-repository/)

---

### Post by Azakus on 2007-01-14
Is it just me, or does it look like the repo is down. I keep getting 302 errors when trying to install something from the repo
```
$ sudo aptitude install xvidcap
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
The following NEW packages will be installed:
  xvidcap 
0 packages upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 2999kB of archives. After unpacking 7259kB will be used.
WARNING: untrusted versions of the following packages will be installed!

Untrusted packages could compromise your system's security.
You should only proceed with the installation if you are certain that
this is what you want to do.

  xvidcap 

Do you want to ignore this warning and proceed anyway?
To continue, enter "Yes"; to abort, enter "No": yes
Writing extended state information... Done
Err http://janvitus.interfree.it edgy-janvitus/main-amd64 xvidcap 1.1.4-0ubuntu1~janvitus
  302 Found
```

---

### Post by Corbelius on 2007-01-15
> **Azakus said:**
> Is it just me, or does it look like the repo is down. I keep getting 302 errors when trying to install something from the repo


[http://www.janvitus.netsons.org/2007/01/09/new-gpg-key-and-repository-nuova-chiave-gpg-e-repository/](http://www.janvitus.netsons.org/2007/01/09/new-gpg-key-and-repository-nuova-chiave-gpg-e-repository/)

[http://ubuntuforums.org/showpost.php?p=1134877&postcount=1](http://ubuntuforums.org/showpost.php?p=1134877&postcount=1)

 ;)

---

### Post by flapane on 2007-01-15
why not altervista as I suggested you? rules issues or what?

---

### Post by Azakus on 2007-01-15
> **Corbelius said:**
> [http://www.janvitus.netsons.org/2007/01/09/new-gpg-key-and-repository-nuova-chiave-gpg-e-repository/](http://www.janvitus.netsons.org/2007/01/09/new-gpg-key-and-repository-nuova-chiave-gpg-e-repository/)

[http://ubuntuforums.org/showpost.php?p=1134877&postcount=1](http://ubuntuforums.org/showpost.php?p=1134877&postcount=1)

 ;)

Thanks!

---

### Post by Corbelius on 2007-01-17
> **flapane said:**
> why not altervista as I suggested you? rules issues or what?

Rules: 

> 3.4 Non e' consentito utilizzare un account come semplice spazio per depositare files da scaricare, elementi dinamici o altro materiale utilizzato da siti esterni, e' inoltre vietato aprire piu' accounts per un singolo sito (mirroring) o per ospitare parti di esso.

;)

---

### Post by Corbelius on 2007-01-29
**@ Nspluginwrapper on Edgy Eft**

Before installing my packages of nspluginwrapper for the flash player, eliminated all the files you have installed and created previously, and then read the howto: [http://www.janvitus.netsons.org/2007/01/15/nspluginwrapper-adobe-flash-player/](http://www.janvitus.netsons.org/2007/01/15/nspluginwrapper-adobe-flash-player/)

---

### Post by flapane on 2007-01-29
when I will have spare time I'll finally use nspluginwrapper and not firefox32

---

### Post by Corbelius on 2007-02-22
Anyone can test this package and report errors? :)

[Rhythmbox 0.9.8](www.janvitus.netsons.org/varie/rhythmbox_0.9.8-0ubuntu1~janvitus_amd64.deb) > md5: 390cb2c54fa6b4cebd260915920ee1e8

[libgpod1 0.4.2](www.janvitus.netsons.org/varie/libgpod1_0.4.2-0ubuntu1~janvitus_amd64.deb) > md5: ed48bb3a705e26de07f4397029196867

---

### Post by gavintlgold on 2007-02-22
> **Corbelius said:**
> Anyone can test this package and report errors? :)

[Rhythmbox 0.9.8](www.janvitus.netsons.org/varie/rhythmbox_0.9.8-0ubuntu1~janvitus_amd64.deb) > md5: 390cb2c54fa6b4cebd260915920ee1e8

[libgpod1 0.4.2](www.janvitus.netsons.org/varie/libgpod1_0.4.2-0ubuntu1~janvitus_amd64.deb) > md5: ed48bb3a705e26de07f4397029196867
It installs fine, but when I open rhythmbox and go to Help>About, it says it's 0.9.7 still... Restarted, still no difference. And the new features aren't there.

EDIT: I had a compiled version, so when I was launching with command 'rhythmbox' it was using that version. When I did the command "/usr/bin/rhythmbox" the new version launched. My fault.. the packages should be working fine for normal users!

---

### Post by flapane on 2007-02-27
hi
if you want you can add [http://www.kde-apps.org/content/show.php?content=49574](http://www.kde-apps.org/content/show.php?content=49574)
the new valknut come out yesterday

---

### Post by Corbelius on 2007-02-28
Cabspace is down, for new repositories see [www.janvitus.netsons.org/repository/](www.janvitus.netsons.org/repository/)
Sorry for the inconvenience.

[http://www.janvitus.netsons.org/2007/02/28/ritorno-alle-origini/](http://www.janvitus.netsons.org/2007/02/28/ritorno-alle-origini/)

> **flapane said:**
> hi
if you want you can add [http://www.kde-apps.org/content/show.php?content=49574](http://www.kde-apps.org/content/show.php?content=49574)
the new valknut come out yesterday

Se mi mandi tutti i file, .diff, .dsc, .orig, controllo e metto sul repository.

gianvito AT ubuntu-it DOT org

---

### Post by flapane on 2007-02-28
ho solo compilato il sorgente e dato checkinstall, come si può risalire a quegli altri files?

---

### Post by jonah1980 on 2007-02-28
hey dudes, scribus 1.3.3.8 is out if anyone fancies giving it the old amd64 treatment?

---

### Post by Azakus on 2007-03-12
New SVN of Hardinfo out that doesn't crash on SHA1SUM benchmark or on search for USB devices. SVN_124.

---

### Post by cborga1985 on 2007-03-15
I have just made my own repository also for the same purpose with different things i've built. See my sig, just go to the help page for the actual repository.

---

### Post by flapane on 2007-03-16
I suggest you [http://www.kde-apps.org/content/show.php/kooldock?content=50910](http://www.kde-apps.org/content/show.php/kooldock?content=50910)
there aren't any 64bit versions, at this time

---

### Post by cborga1985 on 2007-03-16
> **flapane said:**
> I suggest you [http://www.kde-apps.org/content/show.php/kooldock?content=50910](http://www.kde-apps.org/content/show.php/kooldock?content=50910)
there aren't any 64bit versions, at this time

As you requested I just made it for you. Just download the attachment and untar. I will add it to my repository once cabspace comes back up.

to install

```
sudo dpkg -i kooldock_0.4.5-1_amd64.deb
```

---

### Post by flapane on 2007-03-16
i was referring to gianvitus, but anyway thanks, I get it!

---

### Post by cborga1985 on 2007-03-16
> **flapane said:**
> i was referring to gianvitus, but anyway thanks, I get it!
Yeah I figured that but I figured that I would check it out. Kill 2 birds with one stone type deal. Also, now it is in my repository. My repository is now here.

```
#Cborga's Repository
deb http://www.filespacer.com/users/cborga/ubuntu ./
```

---

### Post by chrisinator_Shuttle_XPC on 2007-03-23
awesome! Great Respitories

---

### Post by Corbelius on 2007-04-15
[http://www.janvitus.netsons.org/2007/04/15/janvitus-amd64-repository-v704/](http://www.janvitus.netsons.org/2007/04/15/janvitus-amd64-repository-v704/)

I have opened the Feisty Fawn repositories, to add them:

```
deb http://janvitus.interfree.it/ubuntu feisty-janvitus main-amd64
deb-src http://janvitus.interfree.it/ubuntu feisty-janvitus main-amd64
```

More info: [http://www.janvitus.netsons.org/repository/](http://www.janvitus.netsons.org/repository/)
Good update! :)

---

### Post by flapane on 2007-04-15
great Gianvito ;)

---

### Post by xopher on 2007-04-16
Just keeps getting better. Thanks (again).

Let's just hope there won't be any dns-problems anymore.

---

### Post by jamesford on 2007-04-26
hmmm could someone make updated sensors applet debs with tango icons or something. didnt that exist before? i hate the default icons anyway

---

### Post by Corbelius on 2007-04-27
> **jamesford said:**
> hmmm could someone make updated sensors applet debs with tango icons or something. didnt that exist before? i hate the default icons anyway

[http://janvitus.interfree.it/ubuntu/pool/edgy-janvitus/main-amd64/sensors-applet_1.7.11-0ubuntu1~janvitus_amd64.deb](http://janvitus.interfree.it/ubuntu/pool/edgy-janvitus/main-amd64/sensors-applet_1.7.11-0ubuntu1~janvitus_amd64.deb)

---

### Post by jamesford on 2007-04-27
thanks corb but its still using the old ugly icons :(
wasnt there a script some place some time that would replace the old icons with tango ones ?

---

### Post by Corbelius on 2007-05-04
> **jamesford said:**
> thanks corb but its still using the old ugly icons :(
wasnt there a script some place some time that would replace the old icons with tango ones ?

In the deb are tango icons :)

I have add a box on my site with latest packages in the repository.

---

### Post by jamesford on 2007-05-04
thanks man, i got it working eventually :)

now we need pidgin 2.0 final
and  the extendedprefs, guifications and encryption for pidgin ;)
edit:wow the new sensors applet detects my nvidia temp!

edit2: can u tell me where the icons in the sensors applet are stored? i modded a few and put them in /usr/share/icons/hicolor/22x22/devices/ but it still displays the old ones, i even rebooted

---

### Post by Corbelius on 2007-05-05
> **jamesford said:**
> thanks man, i got it working eventually :)

now we need pidgin 2.0 final
and  the extendedprefs, guifications and encryption for pidgin ;)

Next week maybe, i'll wait to upload to gutsy repositories.

> edit:wow the new sensors applet detects my nvidia temp!

Eheh :)

What nvdia card you have?

> edit2: can u tell me where the icons in the sensors applet are stored? i modded a few and put them in /usr/share/icons/hicolor/22x22/devices/ but it still displays the old ones, i even rebooted

Open synaptic and  in the properties of the deb package > file installed

---

### Post by jamesford on 2007-05-05
weird, in files installed it says for example "/usr/share/icons/hicolor/22x22/devices/sensors-applet-cpu.png" - this is one of the files i modded, if i do gthumb /usr/share/icons/hicolor/22x22/devices/sensors-applet-cpu.png my modded file shows up, however the icon used in the panel is the old one i overwrote
are the icons cached somewhere ?

ive got a GeForce 7600 GT, this one [http://www.asus.com.tw/products4.aspx?l1=2&l2=6&l3=271&model=1097&modelmenu=1](http://www.asus.com.tw/products4.aspx?l1=2&l2=6&l3=271&model=1097&modelmenu=1)

---

### Post by Corbelius on 2007-05-05
> **jamesford said:**
> weird, in files installed it says for example "/usr/share/icons/hicolor/22x22/devices/sensors-applet-cpu.png" - this is one of the files i modded, if i do gthumb /usr/share/icons/hicolor/22x22/devices/sensors-applet-cpu.png my modded file shows up, however the icon used in the panel is the old one i overwrote
are the icons cached somewhere ?

Maybe you use an icon set that change sensors-applet icons.
You can find other sensors-applet icons in /usr/share/pixmaps/sensors-applet

> ive got a GeForce 7600 GT, this one [http://www.asus.com.tw/products4.aspx?l1=2&l2=6&l3=271&model=1097&modelmenu=1](http://www.asus.com.tw/products4.aspx?l1=2&l2=6&l3=271&model=1097&modelmenu=1)

You can post me the output of lsmod command?

---

### Post by jamesford on 2007-05-05
the icons seem independent of any theme..

```
Module                  Size  Used by
isofs                  38628  1 
loop                   20368  2 
nfnetlink_queue        15104  1 
binfmt_misc            14604  1 
xt_tcpudp               4992  2 
nf_conntrack_ipv4      22160  3 
iptable_filter          4480  1 
ip_tables              23080  1 iptable_filter
xt_NFQUEUE              3328  3 
vmnet                  44832  13 
xt_state                3968  3 
nf_conntrack           73180  2 nf_conntrack_ipv4,xt_state
nfnetlink               9160  4 nfnetlink_queue,nf_conntrack_ipv4,nf_conntrack
x_tables               23688  4 xt_tcpudp,ip_tables,xt_NFQUEUE,xt_state
vmmon                 149644  0 
ppdev                  11272  0 
af_packet              27020  2 
dev_acpi               17028  0 
tc1100_wmi              9224  0 
pcc_acpi               15616  0 
sony_acpi               7064  0 
dock                   11992  0 
container               6144  0 
asus_acpi              19756  0 
video                  19080  0 
button                 10016  0 
ac                      6920  0 
sbs                    17856  0 
i2c_ec                  6784  1 sbs
powernow_k8            16480  1 
backlight               8448  1 asus_acpi
cpufreq_userspace       6176  0 
battery                12040  0 
cpufreq_powersave       3072  0 
cpufreq_stats           8416  0 
cpufreq_conservative     9736  0 
cpufreq_ondemand       10640  1 
freq_table              6336  3 powernow_k8,cpufreq_stats,cpufreq_ondemand
it87                   24336  0 
hwmon_vid               4864  1 it87
i2c_isa                 7680  1 it87
eeprom                  9744  0 
sbp2                   26628  0 
parport_pc             40104  0 
lp                     15048  0 
parport                43404  3 ppdev,parport_pc,lp
snd_emu10k1_synth       9216  0 
snd_emux_synth         39936  1 snd_emu10k1_synth
snd_seq_virmidi         9216  1 snd_emux_synth
snd_seq_midi_emul       8960  1 snd_emux_synth
snd_emu10k1           133024  3 snd_emu10k1_synth
snd_ac97_codec        117720  1 snd_emu10k1
ac97_bus                3968  1 snd_ac97_codec
snd_util_mem            6656  2 snd_emux_synth,snd_emu10k1
snd_hwdep              12168  2 snd_emux_synth,snd_emu10k1
snd_pcm_oss            49536  0 
snd_pcm                92808  4 snd_emu10k1,snd_ac97_codec,snd_pcm_oss
snd_page_alloc         11792  2 snd_emu10k1,snd_pcm
snd_mixer_oss          19840  1 snd_pcm_oss
snd_seq_dummy           5380  0 
snd_seq_oss            36608  0 
snd_seq_midi           11008  0 
snd_rawmidi            29696  3 snd_seq_virmidi,snd_emu10k1,snd_seq_midi
snd_seq_midi_event      9856  3 snd_seq_virmidi,snd_seq_oss,snd_seq_midi
snd_seq                61856  9 snd_emux_synth,snd_seq_virmidi,snd_seq_midi_emul,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
quickcam               76328  0 
ide_cd                 35104  0 
cdrom                  40744  1 ide_cd
snd_timer              26632  3 snd_emu10k1,snd_pcm,snd_seq
snd_seq_device         10260  8 snd_emu10k1_synth,snd_emux_synth,snd_emu10k1,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
irtty_sir              10752  0 
nvidia               7761464  32 
sir_dev                19336  1 irtty_sir
irda                  217708  2 irtty_sir,sir_dev
videodev               29824  1 quickcam
usb_storage            80448  0 
usblp                  16768  0 
snd                    68904  16 snd_emux_synth,snd_seq_virmidi,snd_emu10k1,snd_ac97_codec,snd_hwdep,snd_pcm_oss,snd_pcm,snd_mixer_oss,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
v4l2_common            28800  1 videodev
v4l1_compat            14980  1 videodev
emu10k1_gp              5632  0 
gameport               18704  2 emu10k1_gp
k8temp                  7552  0 
i2c_nforce2             7680  0 
i2c_core               26624  6 i2c_ec,it87,i2c_isa,eeprom,nvidia,i2c_nforce2
pcspkr                  4736  0 
soundcore              10272  1 snd
libusual               22184  1 usb_storage
crc_ccitt               3456  1 irda
psmouse                43536  0 
serio_raw               9092  0 
shpchp                 37404  0 
pci_hotplug            36228  1 shpchp
tsdev                  10112  0 
evdev                  13056  4 
ext3                  143760  4 
jbd                    68208  1 ext3
mbcache                11400  1 ext3
sg                     40616  0 
sd_mod                 25092  9 
amd74xx                16944  0 [permanent]
generic                 6532  0 [permanent]
floppy                 67944  0 
sata_sil               15112  0 
ohci1394               38088  0 
ieee1394              369784  2 sbp2,ohci1394
forcedeth              48776  0 
ehci_hcd               37004  0 
ohci_hcd               24196  0 
usbcore               154416  7 quickcam,usb_storage,usblp,libusual,ehci_hcd,ohci_hcd
sata_nv                24196  5 
ata_generic            10628  0 
libata                137000  3 sata_sil,sata_nv,ata_generic
scsi_mod              166968  5 sbp2,usb_storage,sg,sd_mod,libata
thermal                16912  0 
processor              34952  2 powernow_k8,thermal
fan                     6536  0 
fbcon                  44416  0 
tileblit                4096  1 fbcon
font                    9856  1 fbcon
bitblit                 7296  1 fbcon
softcursor              3712  1 bitblit
vesafb                 10376  0 
cfbcopyarea             5120  1 vesafb
cfbimgblt               4096  1 vesafb
cfbfillrect             5632  1 vesafb
capability              7048  0 
commoncap               9472  1 capability
```
[http://img82.imageshack.us/img82/7438/gpueo8.png](http://img82.imageshack.us/img82/7438/gpueo8.png)

---

### Post by Corbelius on 2007-05-06
> **jamesford said:**
> the icons seem independent of any theme..


Have you restarted the session or the applet?

Anyway Compiz stable 0.4 is in the feisty repository =)

---

### Post by Corbelius on 2007-05-08
Now in the feisty repository:

> pidgin_2.0.0-0ubuntu1~janvitus_amd64.deb
pidgin-data_2.0.0-0ubuntu1~janvitus_all.deb
pidgin-dbg_2.0.0-0ubuntu1~janvitus_amd64.deb
pidgin-dev_2.0.0-0ubuntu1~janvitus_amd64.deb
pidgin-guifications_2.14-0ubuntu1~janvitus_amd64.deb
pidgin-libnotify_0.12-1ubuntu1~janvitus_amd64.deb
pidgin-rhythmbox_2.0-0ubuntu1~janvitus_amd64.deb


;)

---

### Post by jamesford on 2007-05-08
you rule corb :)
how about the encryption plugin? its available here as a tarball [http://gaim-encryption.sourceforge.net/](http://gaim-encryption.sourceforge.net/)

btw i solved the sensors applet icon problem with sudo gtk-update-icon-cache -f -t /usr/share/icons/hicolor

---

### Post by Corbelius on 2007-05-09
> **jamesford said:**
> you rule corb :)
how about the encryption plugin? its available here as a tarball [http://gaim-encryption.sourceforge.net/](http://gaim-encryption.sourceforge.net/)


Done =)

---

### Post by jamesford on 2007-05-09
corb, u rule!
thanks a lot

edit: oops, found another gaim plugin that i need in pidgin, its called extended prefs [http://sourceforge.net/projects/gaim-extprefs/](http://sourceforge.net/projects/gaim-extprefs/)
wont ask you to deb it cos uve already done so much ;)

---

### Post by reets on 2007-05-09
I seem to have this problem where Synaptic wants to remove gaim and ubuntu-desktop when I try to install your Pidgin. If I do that, then try to put in ubuntu-desktop again then it complains about gaim not installed :P Any ideas?

---

### Post by rai4shu2 on 2007-05-09
I don't think you'll need ubuntu-desktop any time soon (unless you plan to dist-upgrade).

---

### Post by reets on 2007-05-09
So ubuntu-desktop is not my ACTUAL desktop gui files? Sorry, I've been using this less than 2 weeks and don't know too much yet :P

---

### Post by rai4shu2 on 2007-05-09
No. You only need ubuntu-desktop to ensure "proper upgrades" (for example, dist-upgrade).

---

### Post by reets on 2007-05-09
Thanx for the info! :)

Finally have sound again in Pidgin. My first upgrade attempt didn't seem to have sound enabled when compiled or something :S and Guification is working! w00t

---

### Post by Corbelius on 2007-05-13
I have changed name to the repository, now is "uPure64", see here for the change (or first messagge in this topic): [http://www.janvitus.netsons.org/repository/](http://www.janvitus.netsons.org/repository/) :)

---

### Post by gavintlgold on 2007-05-13
Great. Once again, thanks for maintaining this repository! I'm installing pidgin right now :)

PS: You might want to visit my blog (in my signature) and add the debs I have there (or compile your own). That might make it easier, since my method isn't so good.

---

### Post by flapane on 2007-05-15
the new kooldock 0.4.6 is out from some time...
[http://www.kde-apps.org/content/show.php/kooldock?content=50910](http://www.kde-apps.org/content/show.php/kooldock?content=50910)

it would be a good dock on a 64bit distro, if compiled :P
I use the 0.4.5 version, but in 0.4.6 there are some bugfixes.

---

### Post by Corbelius on 2007-05-16
> **flapane said:**
> the new kooldock 0.4.6 is out from some time...
[http://www.kde-apps.org/content/show.php/kooldock?content=50910](http://www.kde-apps.org/content/show.php/kooldock?content=50910)

it would be a good dock on a 64bit distro, if compiled :P
I use the 0.4.5 version, but in 0.4.6 there are some bugfixes.

I'm going to see :mrgreen:

---

### Post by Corbelius on 2007-05-19
> **flapane said:**
> the new kooldock 0.4.6 is out from some time...
[http://www.kde-apps.org/content/show.php/kooldock?content=50910](http://www.kde-apps.org/content/show.php/kooldock?content=50910)

it would be a good dock on a 64bit distro, if compiled :P
I use the 0.4.5 version, but in 0.4.6 there are some bugfixes.

Done.

---

### Post by flapane on 2007-05-20
Simply great, Gianvito

---

### Post by flapane on 2007-05-21
(I'll reply to your mail tonight, when I'm back at home;) )

Meanwhile, another cute thing could it be the sysinfo kioslave, written originally for suse:
[http://www.kubuntu-art.org/content/show.php/KIO+Slave+sysinfo%3A%2B+-+Kubuntu+7.04+packa?content=58704](http://www.kubuntu-art.org/content/show.php/KIO+Slave+sysinfo%3A%2B+-+Kubuntu+7.04+packa?content=58704)

Useless, but cute

---

### Post by jusmurph on 2007-06-25
To say i add this repository,

How do i access the packages etc? How do i see whats in it? (Have not got my head fully around 3rd part repos yet).

---

### Post by Corbelius on 2007-06-25
> **jusmurph said:**
> To say i add this repository,

How do i access the packages etc? How do i see whats in it? (Have not got my head fully around 3rd part repos yet).

[http://www.janvitus.netsons.org/repository/](http://www.janvitus.netsons.org/repository/)

[http://janvitus.interfree.it/ubuntu/index.html](http://janvitus.interfree.it/ubuntu/index.html)

Anyway you can see the latest packages on my website, in a box to right menu: [http://www.janvitus.netsons.org/](http://www.janvitus.netsons.org/)

---

### Post by Corbelius on 2007-06-27
> From today will be available another repository’s subsection uPure64 called “experimental”, freely inspired to Debian. In this repository will be put not fully tested extra packages on, or we’ll have ever two available versions of the same program: for example in the main version you will find Compiz 4.0 and in the experimental one you will find 0.5.1+git20070626 with dependencies, in order to leave always a fully working version of the program. To add a new subsection more to basic version:

```

deb http://janvitus.interfree.it/ubuntu/ feisty-upure64 experimental-amd64
deb-src http://janvitus.interfree.it/ubuntu/ feisty-upure64 experimental-amd64
```

Install to your own risk, i’m very conscious and meticulous, but I cannot foresee how things would turn out sometimes. Advices are welcome :) 

[http://www.janvitus.netsons.org/2007/06/27/experimental/](http://www.janvitus.netsons.org/2007/06/27/experimental/)

[http://janvitus.interfree.it/ubuntu/dists/feisty-upure64/experimental-amd64/](http://janvitus.interfree.it/ubuntu/dists/feisty-upure64/experimental-amd64/)

;)

---

### Post by jamesford on 2007-06-27
is this compiz-fusion ?
i get confused with all the variants

---

### Post by Major_Kong on 2007-06-27
Sugestion for packages to be added:

Audacious 1.3.2
Lame 3.97 and liblame0-3.97
oggenc-aoTuv
libfreetype6 libcairo2 libxft2 (the patched libraries for improved sub-pixel font rendering)

(packages i had to compile the .deb to install. There's bound to be someone else interested in them, lol)

EDIT: Why do i have to install pidgin to update unrelated packages ?

---

### Post by Corbelius on 2007-06-28
> **jamesford said:**
> is this compiz-fusion ?
i get confused with all the variants

It's compiz-fusion, they are backports from gutsy gibbon :)

[http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=compiz&searchon=names&subword=1&version=gutsy&release=all](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=compiz&searchon=names&subword=1&version=gutsy&release=all)

> **Major_Kong said:**
> Sugestion for packages to be added:

EDIT: Why do i have to install pidgin to update unrelated packages ?

What do you mean?

---

### Post by Major_Kong on 2007-06-28
If i add both repos, and then run the update manager it tells that i have to do a parcial update first (no problem here). But then in the last confirmation window if i check wich packages are going to be installed i find pidgin, evolution, ekiga and a few other unrelated packages. The only packages that are to be updated are compiz-core, compiz-plugins, compiz, compiz-gnome and tomboy.

EDIT: If i only add the "main" this doesn't happen.

---

### Post by jamesford on 2007-06-28
thanks corb. looking forward to trying it out when i feel adventurous. shouldnt take long

---

### Post by oscrp on 2007-06-29
Please, when you have time, backport emerald from the gutsy repos, thank you :D

---

### Post by Tanker Bob on 2007-06-29
Any chance of getting the latest Thunderbird 2.x version backported?  Thanks. :D

---

### Post by shafin on 2007-07-02
Thanks,at last I've found a way to install compiz fusion.Thanks a lot.

---

### Post by Corbelius on 2007-07-02
> **Major_Kong said:**
> If i add both repos, and then run the update manager it tells that i have to do a parcial update first (no problem here). But then in the last confirmation window if i check wich packages are going to be installed i find pidgin, evolution, ekiga and a few other unrelated packages. The only packages that are to be updated are compiz-core, compiz-plugins, compiz, compiz-gnome and tomboy.

EDIT: If i only add the "main" this doesn't happen.

Mmm... ok, use "experimental" only when necessary :)

> **oscrp said:**
> Please, when you have time, backport emerald from the gutsy repos, thank you :D

Emerald for beryl?

> **Tanker Bob said:**
> Any chance of getting the latest Thunderbird 2.x version backported?  Thanks. :D

It's too big, my webhost is only 400mb, but let me think :)

---

### Post by jamesford on 2007-07-02
whats amule-adunanza ?

---

### Post by Corbelius on 2007-07-03
> **jamesford said:**
> whats amule-adunanza ?

Read the package description ;)

> Contains AdunanzA 3.2 mod ( Fastweb )

Amule-adunanza contain a patch for italian user to have fastweb provider.

---

### Post by Didjit on 2007-07-06
How about kdenlive (needs mlt and mlt++)? [http://kdenlive.org/](http://kdenlive.org/)  Trevino has a 32 bit, but not a 64. 

Didjit

---

### Post by Corbelius on 2007-07-07
> **Major_Kong said:**
> Sugestion for packages to be added:

Audacious 1.3.2



> **Didjit said:**
> How about kdenlive (needs mlt and mlt++)? [http://kdenlive.org/](http://kdenlive.org/)  Trevino has a 32 bit, but not a 64. 

Didjit

Done both ;)

---

### Post by Didjit on 2007-07-07
> **Corbelius said:**
> Done both ;)

Sweet!!! Thanks a ton.

Didjit

---

### Post by Major_Kong on 2007-07-07
> **Corbelius said:**
> Done both ;)

:)

---

### Post by jkwarras on 2007-07-11
I just installed kdenlive, but when adding clips to my project (DV avi files) it crashes. Anyone is having the same problem?

This is what (when running in a terminal) returns:

```
kdecore (KAction): WARNING: KAction::insertKAccel( kaccel = 0x8d15c0 ): KAccel object already contains an action name "edit_paste"
QFile::open: No file name specified
QFile::open: No file name specified
kdenlive: Mlt inited
kdenlive: +++++++++++  Generating scenelist start...  ++++++++++++++++++
kdenlive: Creating new document
kdenlive: deleting contents...
kdenlive: ****************  INIT DOCUMENT VIEW ***************
kdenlive:  +  ++ + ++ ++ PREPARE VID THUMB
kdenlive:  +  ++ + ++ ++ PREPARE AUDIO THUMB
kio (KMimeType): WARNING: KServiceType::offers : servicetype ThumbCreator not found
kio (KMimeType): WARNING: KServiceType::offers : servicetype ThumbCreator not found
kdenlive: ++ FOUND CLIP
KCrash: Application 'kdenlive' crashing...
KCrash cannot reach kdeinit, launching directly.
```

---

### Post by flapane on 2007-07-12
The dock could be interesting;)

[http://www.hwupgrade.it/forum/showthread.php?t=1493699](http://www.hwupgrade.it/forum/showthread.php?t=1493699)

---

### Post by IanW on 2007-07-12
That's Simdock. I'm using it right now. Look for it on Gnomefiles.org.

---

### Post by jamesford on 2007-07-13
i would like to request mesk. its a very nice music player, but ive never beena ble to compile it on ubuntu
[http://www.gnomefiles.org/app.php/Mesk](http://www.gnomefiles.org/app.php/Mesk)

---

### Post by Major_Kong on 2007-07-14
I request the gstreamer0.10-plugins-bad version v0.10.5 with the proposed patch to fix the xingmux problem - [http://bugzilla.gnome.org/show_bug.cgi?id=397759](http://bugzilla.gnome.org/show_bug.cgi?id=397759) , [http://bugzilla.gnome.org/attachment.cgi?id=91184&action=view](http://bugzilla.gnome.org/attachment.cgi?id=91184&action=view)

I already tried it and it seems to work. And it would make life a whole lot easier for people trying to encode to mp3-vbr using gstreamer.

---

### Post by Corbelius on 2007-07-17
> **jkwarras said:**
> I just installed kdenlive, but when adding clips to my project (DV avi files) it crashes. Anyone is having the same problem?

This is what (when running in a terminal) returns:

```
kdecore (KAction): WARNING: KAction::insertKAccel( kaccel = 0x8d15c0 ): KAccel object already contains an action name "edit_paste"
QFile::open: No file name specified
QFile::open: No file name specified
kdenlive: Mlt inited
kdenlive: +++++++++++  Generating scenelist start...  ++++++++++++++++++
kdenlive: Creating new document
kdenlive: deleting contents...
kdenlive: ****************  INIT DOCUMENT VIEW ***************
kdenlive:  +  ++ + ++ ++ PREPARE VID THUMB
kdenlive:  +  ++ + ++ ++ PREPARE AUDIO THUMB
kio (KMimeType): WARNING: KServiceType::offers : servicetype ThumbCreator not found
kio (KMimeType): WARNING: KServiceType::offers : servicetype ThumbCreator not found
kdenlive: ++ FOUND CLIP
KCrash: Application 'kdenlive' crashing...
KCrash cannot reach kdeinit, launching directly.
```

Sorry, i don't have a cam for test it =)

> **jamesford said:**
> i would like to request mesk. its a very nice music player, but ive never beena ble to compile it on ubuntu
[http://www.gnomefiles.org/app.php/Mesk](http://www.gnomefiles.org/app.php/Mesk)

> **Major_Kong said:**
> I request the gstreamer0.10-plugins-bad version v0.10.5 with the proposed patch to fix the xingmux problem - [http://bugzilla.gnome.org/show_bug.cgi?id=397759](http://bugzilla.gnome.org/show_bug.cgi?id=397759) , [http://bugzilla.gnome.org/attachment.cgi?id=91184&action=view](http://bugzilla.gnome.org/attachment.cgi?id=91184&action=view)

I already tried it and it seems to work. And it would make life a whole lot easier for people trying to encode to mp3-vbr using gstreamer.


Mmm... ok, i can see that.

---

### Post by Corbelius on 2007-07-22
I've add opensync packages - [http://www.in.fh-merseburg.de/~jahn/opensync-0.21/](http://www.in.fh-merseburg.de/~jahn/opensync-0.21/) - to experimental section of the uPure64 repository.

```
deb http://janvitus.interfree.it/ubuntu feisty-upure64 experimental-amd64
deb-src http://janvitus.interfree.it/ubuntu feisty-upure64 experimental-amd64
```

Cheers ;)

---

### Post by Major_Kong on 2007-07-27
Request: 
The audacious-mac plugin (for playing .ape audio files)

---

### Post by jamesford on 2007-08-04
winff?

---

### Post by Corbelius on 2007-08-06
> **jamesford said:**
> winff?

You can try movic ;)

[http://www.gnomefiles.org/app.php/movic](http://www.gnomefiles.org/app.php/movic)

Find a .deb into upure64.

---

### Post by jamesford on 2007-08-06
that thing only converts to ipod formats doesent it? 
*wants to convert to anything from anything*

---

### Post by Corbelius on 2007-08-08
> **jamesford said:**
> that thing only converts to ipod formats doesent it? 
*wants to convert to anything from anything*

No, also to creative, cowon, .3gp...

---

### Post by jamesford on 2007-08-08
but id like to convert say from ogg to xvid

---

### Post by Corbelius on 2007-08-09
> **jamesford said:**
> but id like to convert say from ogg to xvid

```
man ffmpeg
```

;)

---

### Post by jamesford on 2007-08-09
hehe :P
sometimes a gui is more convenient

---

### Post by jusmurph on 2007-08-12
What packages do i need to install to get compiz fusion running... i tried and ended up with broken packages.

---

### Post by Corbelius on 2007-08-14
> **jusmurph said:**
> What packages do i need to install to get compiz fusion running... i tried and ended up with broken packages.

compiz, compizconfig-settings-manager

;)

---

### Post by Corbelius on 2007-08-15
Kdenlive 0.5 is in the repository :)

---

### Post by jusmurph on 2007-08-29
Ok i will give it a whirl

---

### Post by jusmurph on 2007-08-29
> **Corbelius said:**
> compizconfig-settings-manager

;)

It can't find that package?

Are we ment to use that tux repo i see running around for compiz... because im not a fan of non keyed repos...

---

### Post by Tanker Bob on 2007-08-29
Any chance of getting BibleTime included from [http://www.bibletime.info/](http://www.bibletime.info/) ? The standard repository is rarely updated. Thank you.

---

### Post by jusmurph on 2007-08-30
> **jusmurph said:**
> It can't find that package?

Are we ment to use that tux repo i see running around for compiz... because im not a fan of non keyed repos...

Found it... its in the expiremental repo.

Thanks again for hosting this repo man :)

---

### Post by Corbelius on 2007-09-04
@ **NSPluginWrapper**

I want to remember to each program upgrade, example firefox, nspluginwrapper or the flash player, you must re-lauch the command &#8220;nspluginwrapper -v -a -i&#8221; to update the wrapper links.

---

### Post by gimmy_bond on 2007-09-04
Thanks for the link. I added the link to my "software sources". However when I reload my Synaptics I get the following message.

W: GPG error: [http://janvitus.interfree.it](http://janvitus.interfree.it) feisty-upure64 Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 5CEBE24C2C4C84CC.

How to resolve it.

---

### Post by Corbelius on 2007-09-06
> **gimmy_bond said:**
> Thanks for the link. I added the link to my "software sources". However when I reload my Synaptics I get the following message.

W: GPG error: [http://janvitus.interfree.it](http://janvitus.interfree.it) feisty-upure64 Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 5CEBE24C2C4C84CC.

How to resolve it.

[http://ubuntuforums.org/showpost.php?p=1134877&postcount=1](http://ubuntuforums.org/showpost.php?p=1134877&postcount=1)

```
gpg --keyserver hkp://keyserver.ubuntu.com:11371/ --recv-keys 2C4C84CC && gpg --export --armor 2C4C84CC | sudo apt-key add -
```

---

### Post by Didjit on 2007-09-08
How about adding the best photo management application (IMHO), Digikam.

This is the last .debs for AMD64 that I have found.

[http://ubuntuforums.org/showthread.php?t=322165&page=3&highlight=digikam](http://ubuntuforums.org/showthread.php?t=322165&page=3&highlight=digikam)

Didjit

---

### Post by Didjit on 2007-09-08
Spelling, my bad.

---

### Post by masters09 on 2007-09-08
Hi 
Thanx alot guys
Masters09:guitar:
:guitar:

---

### Post by flapane on 2007-09-10
new filezilla 3 :)
[http://filezilla-project.org/download.php?type=client](http://filezilla-project.org/download.php?type=client)

---

### Post by glupee on 2007-09-11
thnx for the repo hook-up!

---

### Post by Gujume3333 on 2007-09-11
Hi,

Firstly I wanted to thank all of the help I have found not only from this particular forum but also to Ubuntu.  

Second I was hoping....if someone could make a AMD64 architecture version of the following .deb files:
[http://leighm.dgtlmoon.com/misc/binaries/z600cups_1.0-2_i386.deb](http://leighm.dgtlmoon.com/misc/binaries/z600cups_1.0-2_i386.deb)
[http://leighm.dgtlmoon.com/misc/binaries/z600llpddk_2.0-2_i386.deb](http://leighm.dgtlmoon.com/misc/binaries/z600llpddk_2.0-2_i386.deb)
I am new to linux and I wanted to connect my Dell 720. I am using Kubuntu 7.04 AMD64.  I know the Lexmark Z600 and Z615 drivers work for the i386 architecture but I cant install because the 64 bit architecture is not supported.  If I knew how I would conver it but I lack the knowledge. If someone could convert the driver I would really appreciate it. Also any help with pointing in the right direction will also help greatly. Thanks for all your time and effort...to the community.

Gujume

---

### Post by Corbelius on 2007-09-12
> **Gujume3333 said:**
> Hi,

Firstly I wanted to thank all of the help I have found not only from this particular forum but also to Ubuntu.  

Second I was hoping....if someone could make a AMD64 architecture version of the following .deb files:
[http://leighm.dgtlmoon.com/misc/binaries/z600cups_1.0-2_i386.deb](http://leighm.dgtlmoon.com/misc/binaries/z600cups_1.0-2_i386.deb)
[http://leighm.dgtlmoon.com/misc/binaries/z600llpddk_2.0-2_i386.deb](http://leighm.dgtlmoon.com/misc/binaries/z600llpddk_2.0-2_i386.deb)
I am new to linux and I wanted to connect my Dell 720. I am using Kubuntu 7.04 AMD64.  I know the Lexmark Z600 and Z615 drivers work for the i386 architecture but I cant install because the 64 bit architecture is not supported.  If I knew how I would conver it but I lack the knowledge. If someone could convert the driver I would really appreciate it. Also any help with pointing in the right direction will also help greatly. Thanks for all your time and effort...to the community.

Gujume

[http://openprinting.org/show_printer.cgi?recnum=Lexmark-Z600_series_z601_z602](http://openprinting.org/show_printer.cgi?recnum=Lexmark-Z600_series_z601_z602)
Download the source and compile it.

---

### Post by Corbelius on 2007-09-12
@ **[SIZE="3"]NSPluginWrapper: how to resolve the "white page" and the "flash not working buttons" bugs.[/SIZE]**

> Add my repository to your sources.list and install nspluginwrapper:

```
    sudo apt-get install nspluginwrapper
```

Download Flash Player plugin, extract and move the content of the package in the folder **&#8220;/usr/lib/nspluginwrapper/plugins&#8221;**.
Now from command line execute:

```
    nspluginwrapper -i /usr/lib/nspluginwrapper/plugins/libflashplayer.so
```

Nspluginwrapper will create the necessary files to work in the folder "**/home/user/.mozilla/plugins/**", now check if plugin work correctly, visit [http://www.youtube.com/](http://www.youtube.com/).
This method works with all Gecko browser family&#8217;s (Epiphany, Firefox, Galeon, etc etc.), with Konqueror setting in the preference to watch in &#8220;/home/utente/.mozilla/plugins/&#8221; directory.
**To each program upgrade**, you must lauch the command &#8220;**nspluginwrapper -v -a -u**&#8221; to update the symbolic links.

[http://www.janvitus.netsons.org/2007/01/15/nspluginwrapper-adobe-flash-player/](http://www.janvitus.netsons.org/2007/01/15/nspluginwrapper-adobe-flash-player/)

@ **FFmpeg**

Now into experimental section of the uPure64 repository is present a new version of FFmpeg (0.cvs20072308 ), in this version working x264, AMR (.3gp), xvid and other codec and encoders.

---

### Post by revchris on 2007-09-15
trying to install updates for gaim and pidgin from the update manager and it gives me the following error: 

W: Failed to fetch [http://janvitus.interfree.it/ubuntu/pool/feisty-upure64/main-amd64/libpurple0_2.2.0-0ubuntu1~upure64_amd64.deb](http://janvitus.interfree.it/ubuntu/pool/feisty-upure64/main-amd64/libpurple0_2.2.0-0ubuntu1~upure64_amd64.deb)
  302 Found


W: Failed to fetch [http://janvitus.interfree.it/ubuntu/pool/feisty-upure64/main-amd64/gaim_2.2.0-0ubuntu1~upure64_all.deb](http://janvitus.interfree.it/ubuntu/pool/feisty-upure64/main-amd64/gaim_2.2.0-0ubuntu1~upure64_all.deb)
  302 Found


is the site down?

---

### Post by Corbelius on 2007-09-16
> **revchris said:**
> trying to install updates for gaim and pidgin from the update manager and it gives me the following error: 

W: Failed to fetch [http://janvitus.interfree.it/ubuntu/pool/feisty-upure64/main-amd64/libpurple0_2.2.0-0ubuntu1~upure64_amd64.deb](http://janvitus.interfree.it/ubuntu/pool/feisty-upure64/main-amd64/libpurple0_2.2.0-0ubuntu1~upure64_amd64.deb)
  302 Found


W: Failed to fetch [http://janvitus.interfree.it/ubuntu/pool/feisty-upure64/main-amd64/gaim_2.2.0-0ubuntu1~upure64_all.deb](http://janvitus.interfree.it/ubuntu/pool/feisty-upure64/main-amd64/gaim_2.2.0-0ubuntu1~upure64_all.deb)
  302 Found


is the site down?

Resolved yesterday, i forgot to upload the debs lol

Tnx for the report ;)

---

### Post by revchris on 2007-09-16
Not a problem, just watched some movies all day anyway :popcorn: :lolflag:

---

### Post by Jouke74 on 2007-09-17
I have two debs for your AMD64 repsository Conky 1.47 and Awn 2.43. 
Can I upload them somewhere or mail them to you?

---

### Post by Corbelius on 2007-09-17
> **Jouke74 said:**
> I have two debs for your AMD64 repsository Conky 1.47 and Awn 2.43. 
Can I upload them somewhere or mail them to you?

Show them to me, send a mail to janvitus AT ubuntu-it DOT org

Important: they don't have to created with checkinstall.

---

### Post by Jouke74 on 2007-09-18
I am afraid they were made with checkinstall.... What is wrong with that :confused:

---

### Post by Corbelius on 2007-09-18
> **Jouke74 said:**
> I am afraid they were made with checkinstall.... What is wrong with that :confused:

Checinstall it's no good to make a deb for redistiubution, it's good only to a personal use.

[https://help.ubuntu.com/6.10/ubuntu/packagingguide/C/index.html](https://help.ubuntu.com/6.10/ubuntu/packagingguide/C/index.html)

[http://www.debian.org/doc/maint-guide/](http://www.debian.org/doc/maint-guide/)

;)

---

### Post by tikal26 on 2007-09-22
I don;t know if this was covered somewhere else, but it is no on the front page.
Do you have a gutsy repo?
Are you planning on realising onefor gutsy?

thanks for your help

---

### Post by Corbelius on 2007-09-24
> **tikal26 said:**
> I don;t know if this was covered somewhere else, but it is no on the front page.
Do you have a gutsy repo?
Are you planning on realising onefor gutsy?

thanks for your help

At the momento no, i'll open when released gutsy stable.

---

### Post by HilliBilly on 2007-09-26
sudo gedit **/etc/apt/sources.list**
## uPure64 Repository
deb [http://janvitus.interfree.it/ubuntu/](http://janvitus.interfree.it/ubuntu/) feisty-upure64 main-amd64
deb-src [http://janvitus.interfree.it/ubuntu/](http://janvitus.interfree.it/ubuntu/) feisty-upure64 main-amd64

[B]
$sudo apt-get update[/B]
Err [http://janvitus.interfree.it](http://janvitus.interfree.it) feisty-upure64/main-amd64 Packages
  302 Found
Err [http://janvitus.interfree.it](http://janvitus.interfree.it) feisty-upure64/main-amd64 Sources
  302 Found
Fetched 4B in 0s (6B/s)
Failed to fetch [http://janvitus.interfree.it/ubuntu/dists/feisty-upure64/main-amd64/binary-amd64/Packages.gz](http://janvitus.interfree.it/ubuntu/dists/feisty-upure64/main-amd64/binary-amd64/Packages.gz)  302 Found
Failed to fetch [http://janvitus.interfree.it/ubuntu/dists/feisty-upure64/main-amd64/source/Sources.gz](http://janvitus.interfree.it/ubuntu/dists/feisty-upure64/main-amd64/source/Sources.gz)  302 Found
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.


is the site down again or did i make a mistake?

---

### Post by NullHead on 2007-09-26
I got the same output. :(

---

### Post by Bryn Mawr on 2007-09-26
> **RAOF said:**
> It's **possible** that you got them at a time when I was syncing those mirrors.  I'll have a look.

Anyone else having problems with the moshen or systemadministrator mirrors?

Any news on this?

I'm still getting error 404 on all of the files in the FF Misc section of the German mirror.

---

### Post by colo505 on 2007-09-27
me too!

---

### Post by jamesford on 2007-09-27
i hope corb gets it up and running again as soon as possible. i had to do a reinstall and now i cant get the upgraded packages such as rhythmbox. my god the feisty rhythmbox is fugly compared to the upure version

---

### Post by Corbelius on 2007-09-27
My site is down, only my site, i hope Interfree.it (host) resolve this trouble soon.

Thanks to you guys for the reports, especially from mail ;)

---

### Post by flapane on 2007-09-28
hi
new kooldock version (0.4.7) [http://www.kde-look.org/content/show.php/kooldock?content=50910](http://www.kde-look.org/content/show.php/kooldock?content=50910)
would you amd64-debianize it for us? :)
t.i.a

p.s a friend of mine wrote a gui for bit torrent, in gtk.
The source is at [http://sourceforge.net/projects/gbtpd](http://sourceforge.net/projects/gbtpd) and another friend already compiled it for 32bit architecture, he would appreciate.

---

### Post by Corbelius on 2007-09-29
> **Corbelius said:**
> My site is down, only my site, i hope Interfree.it (host) resolve this trouble soon.

Thanks to you guys for the reports, especially from mail ;)

Well... Interfree host has cancelled my account and site completely, include the repository, i think it use too much bandwith and not permit file hosting, these bast***s remember it after 5 years and without no warning.

I'm trying an other host, maybe tuxfamily.org or PPA-launchapd, wait for some day.

Suggests are welcome =)

---

### Post by flapane on 2007-09-29
have you tried netsons?

---

### Post by jamesford on 2007-09-29
both tuxfamily and launchpad sound like good ideas. at least the compiz-fusion repos hosted there seem to be stable and reliable

---

### Post by Corbelius on 2007-10-02
**Warning:**

The repository is reopened and has changed link, see [here]("http://www.janvitus.netsons.org/repository/") or first messagge in this topic ;)

---

### Post by jamesford on 2007-10-02
wahey, wonderful. thanks a lot for getting it up again :D

---

### Post by colo505 on 2007-10-02
Thanks!

---

### Post by s_spiff on 2007-10-02
> **Corbelius said:**
> **Warning:**

The repository is reopened and has changed link, see [here]("http://www.janvitus.netsons.org/repository/") or first messagge in this topic ;)
Probably this is only with me, but somehow the link you've provided doesn't open up on my pc. also i get an error everytime i do the update in synaptic although, i've added the key's. :
```

W: GPG error: http://download.tuxfamily.org feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2D6CFB44DD800CD9

```

---

### Post by Corbelius on 2007-10-02
> **s_spiff said:**
> Probably this is only with me, but somehow the link you've provided doesn't open up on my pc. also i get an error everytime i do the update in synaptic although, i've added the key's. :
```

W: GPG error: http://download.tuxfamily.org feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2D6CFB44DD800CD9

```

First message...

```
gpg --keyserver hkp://keyserver.ubuntu.com:11371/ --recv-keys 2C4C84CC && gpg --export --armor 2C4C84CC | sudo apt-key add -
```

---

### Post by glupee on 2007-10-02
> **Corbelius said:**
> **Warning:**

The repository is reopened and has changed link, see [here]("http://www.janvitus.netsons.org/repository/") or first messagge in this topic ;)
Thanx!:KS

---

### Post by Coyote21 on 2007-10-02
Tks, I will readd it to my repository list...

---

### Post by jusmurph on 2007-10-03
Cheers. Thanks again for all the work.

---

### Post by Corbelius on 2007-10-11
**Gutsy-upure64 are open!**
```

## uPure 64 Repository
deb http://download.tuxfamily.org/upure64/ gutsy-upure64 main-amd64
deb-src http://download.tuxfamily.org/upure64/ gutsy-upure64 main-amd64
deb http://download.tuxfamily.org/upure64/ gutsy-upure64 experimental-amd64
deb-src http://download.tuxfamily.org/upure64/ gutsy-upure64 experimental-amd64

```

Enjoy =)

---

### Post by NullHead on 2007-10-11
> **Corbelius said:**
> **Gutsy-upure64 are open!**
```

## uPure 64 Repository
deb http://download.tuxfamily.org/upure64/ gutsy-upure64 main-amd64
deb-src http://download.tuxfamily.org/upure64/ gutsy-upure64 main-amd64
deb http://download.tuxfamily.org/upure64/ gutsy-upure64 experimental-amd64
deb-src http://download.tuxfamily.org/upure64/ gutsy-upure64 experimental-amd64

```

Enjoy =)

Thanks Corbelius! I really appreciate all of the work you've put into this project!

---

### Post by seanX on 2007-10-11
I've been waiting for a pure 64-bit version of the KDEnlive non-linear
video editor.  So, I thought I'd give this a try.

I got the repository to register properly with the apt program,
but I am getting the following error when I type 
'sudo apt-get install kdenlive':

  Some packages could not be installed. This may mean that you have
  requested an impossible situation or if you are using the unstable
  distribution that some required packages have not yet been created
  or been moved out of Incoming.

  Since you only requested a single operation it is extremely likely that
  the package is simply not installable and a bug report against
  that package should be filed.

  The following packages have unmet dependencies:
  kdenlive: Depends: libmlt++0.2.3 (>= 0.2.2) but it is not going to be installed
                 Depends: libmlt0.2.4 (>= 0.2.4) but it is not going to be installed
  E: Broken packages

Did anyone get get kdenlive to work properly on a 64-bit Ubuntu system?

I had tried earlier to install kdenlive from source, but I was getting the same 
MLT and MLT++ unresolved dependency errors.  When trying to install
MLT and MLT++ manually from source on my 64-bit system, I was getting
a string of extremely hard-to-resolve dependencies, and Ithought I would
wait until someone automated the installation process.

Thanks in advance for anyone that helps.

---

### Post by Corbelius on 2007-10-15
> **seanX said:**
> I've been waiting for a pure 64-bit version of the KDEnlive non-linear
video editor.  So, I thought I'd give this a try.

I got the repository to register properly with the apt program,
but I am getting the following error when I type 
'sudo apt-get install kdenlive':

  Some packages could not be installed. This may mean that you have
  requested an impossible situation or if you are using the unstable
  distribution that some required packages have not yet been created
  or been moved out of Incoming.

  Since you only requested a single operation it is extremely likely that
  the package is simply not installable and a bug report against
  that package should be filed.

  The following packages have unmet dependencies:
  kdenlive: Depends: libmlt++0.2.3 (>= 0.2.2) but it is not going to be installed
                 Depends: libmlt0.2.4 (>= 0.2.4) but it is not going to be installed
  E: Broken packages

Did anyone get get kdenlive to work properly on a 64-bit Ubuntu system?

I had tried earlier to install kdenlive from source, but I was getting the same 
MLT and MLT++ unresolved dependency errors.  When trying to install
MLT and MLT++ manually from source on my 64-bit system, I was getting
a string of extremely hard-to-resolve dependencies, and Ithought I would
wait until someone automated the installation process.

Thanks in advance for anyone that helps.

Kdenlive now is available in gutsy official repositories.

---

### Post by cotcot on 2007-10-15
None of the 3 methods of [[COLOR="Red"]this tutorial[/COLOR]]("http://doc.ubuntu-fr.org/kdenlive")  worked. I finally added these gutsy repositories :

> # deb [http://be.archive.ubuntu.com/ubuntu/](http://be.archive.ubuntu.com/ubuntu/) gutsy main restricted

# deb-src [http://be.archive.ubuntu.com/ubuntu/](http://be.archive.ubuntu.com/ubuntu/) gutsy main restricted

```
sudo apt-get -i kdenlive
``` installed kdenlive.

After installation I have put a hash in front of the gutsy repos.

---

### Post by emilk on 2007-10-16
Hej there!

Is there something like gstreamer flac and gstreamer musepack support for x86_64 availible? I can't play my music in amarok anymore.
I could imagine that these could be put in the unofficial repos too? Or am I blinded by gutsy and just don't stumble over the packages?
And thank you for the repo work done so far. :-)

Best regards, emilk ):P

edit: okay got it working, I installed some more multimedia apps and now amarok plays my flac and muspepack fine. _64 ffs. nevertheless, thx bye

---

### Post by FredB on 2007-10-17
Thanks for your work. But it seems there is no software right now I'm interested in.

Anyway, I will get back looking from time to time.

---

### Post by jamesford on 2007-10-18
any chance of fusion-icon? it seems to not be in the gutsy repos

---

### Post by jusmurph on 2007-10-18
> **jamesford said:**
> any chance of fusion-icon? it seems to not be in the gutsy repos

I'm sure i saw it in there? I'm not on my ubibox so i can't confirm...

---

### Post by Corbelius on 2007-10-19
> **jamesford said:**
> any chance of fusion-icon? it seems to not be in the gutsy repos

Fusion-icon?

---

### Post by jamesford on 2007-10-19
fusion-icon is like the old beryl tray icon if u remember it. its pretty handy and gives u access to all compiz-fusion settings, also lets u temporarely disable c-f when playing a game for example. 

also i wonder about another thing, i really miss those square notifications/balloon tips or what its called that your libnotify (or wahtever pacakge it was) had in feisty. i cant stand the gutsy rounded ones

---

### Post by jusmurph on 2007-10-19
> **jamesford said:**
> any chance of fusion-icon? it seems to not be in the gutsy repos

Try:

```
gnome-compiz-preferences
```

---

### Post by Tecumseh-nl on 2007-10-22
> **Corbelius said:**
> I've add opensync packages - [http://www.in.fh-merseburg.de/~jahn/opensync-0.21/](http://www.in.fh-merseburg.de/~jahn/opensync-0.21/) - to experimental section of the uPure64 repository.

```
deb http://janvitus.interfree.it/ubuntu feisty-upure64 experimental-amd64
deb-src http://janvitus.interfree.it/ubuntu feisty-upure64 experimental-amd64
```

Cheers ;)

I'm looking for those packages but then for gutsy because the opensync packages in the standard repository are not complete, a couple of plugins are missing like the gnokii plugin.

Can I use the feisty repo line or do I need to wait before these packages are introduced into the gutsy repo?

---

### Post by Major_Kong on 2007-10-22
Could you add the new rc of mplayer (1.0RC2) ?

---

### Post by seanX on 2007-10-22
> **cotcot said:**
> None of the 3 methods of [[COLOR="Red"]this tutorial[/COLOR]]("http://doc.ubuntu-fr.org/kdenlive")  worked. I finally added these gutsy repositories :



```
sudo apt-get -i kdenlive
``` installed kdenlive.

After installation I have put a hash in front of the gutsy repos.

I don't know, but this isn;t working for me.  I'm getting the error:

 Package kdenlive is not available, but is referred to by another package.
 This may mean that the package is missing, has been obsoleted, or
 is only available from another source
 E: Package kdenlive has no installation candidate


I have a full 64-bit v7.04 Ubuntu setup.  I guess maybe you need Gutsy to install
kdenlive from the said repository.

Thanks.

Sean.

---

### Post by s_spiff on 2007-10-22
Well I've seen the i386 debs, bu no x64.hopefully someone will compile them. 
Till then the fusion icon can be installed easily using GIt... I've written a howto on my website, follow the last part of it, works fine. already using it :
[http://alokshenoy.blogrunn.com/computer-programming/compiz-on-ubuntu-x64-using-git/](http://alokshenoy.blogrunn.com/computer-programming/compiz-on-ubuntu-x64-using-git/)

Just follow the last part.

---

### Post by jamesford on 2007-10-27
im trying to install the gutsy sensors-applet from the upure64 repos, but i get this error
sensors-applet:
  Depends: libpango1.0-0 (>=1.18.3) but 1.18.2-0ubuntu1 is to be installed

---

### Post by Corbelius on 2007-10-27
> **jamesford said:**
> im trying to install the gutsy sensors-applet from the upure64 repos, but i get this error
sensors-applet:
  Depends: libpango1.0-0 (>=1.18.3) but 1.18.2-0ubuntu1 is to be installed

Enable gutsy-proposed repository.

---

### Post by jenhsun on 2007-10-27
> **Corbelius said:**
> uPure64 (ubuntu pure x86_64) is a repository for the Ubuntu Linux AMD64 (64bit) distribution, it's update to last stable release, at this moment Feisy Fawn AMD64, the packages of the previous versions of Ubuntu will remain online until the Canonical expire their support. The repository exist to make more complete and compatible the 64bit like to i386, between the packages included in it there are NsPluginWrapper, Gnash, Beagle, Banshee, Rhythmbox, Pidgin, K3B, Kdenlive and many others. All the packages are complete of their sources and released under the original software license, GPL or whichever other Open Source.

To add the repository:

```
gpg --keyserver hkp://keyserver.ubuntu.com:11371/ --recv-keys 2C4C84CC && gpg --export --armor 2C4C84CC | sudo apt-key add -
```

Otherwise::

```
wget http://download.tuxfamily.org/upure64/2C4C84CC.gpg -O- | sudo apt-key add -
```

Dapper Drake:
```
## uPure64 Repository
deb http://download.tuxfamily.org/upure64/ dapper-upure64 main-amd64
```

Edgy Eft:
```
## uPure64 Repository
deb http://download.tuxfamily.org/upure64/ edgy-upure64 main-amd64
```

Feisty Fawn:
```
## uPure64 Repository
deb http://download.tuxfamily.org/upure64/ feisty-upure64 main-amd64
deb-src http://download.tuxfamily.org/upure64/ feisty-upure64 main-amd64

## uPure64 Repository (Experimental)
deb http://download.tuxfamily.org/upure64/ feisty-upure64 experimental-amd64
deb-src http://download.tuxfamily.org/upure64/ feisty-upure64 experimental-amd64
```

Gutsy Gibbon:
```
## uPure64 Repository
deb http://download.tuxfamily.org/upure64/ gutsy-upure64 main-amd64
deb-src http://download.tuxfamily.org/upure64/ gutsy-upure64 main-amd64

## uPure64 Repository (Experimental)
deb http://download.tuxfamily.org/upure64/ gutsy-upure64 experimental-amd64
deb-src http://download.tuxfamily.org/upure64/ gutsy-upure64 experimental-amd64
```

Homepage: [http://www.janvitus.netsons.org/repository/](http://www.janvitus.netsons.org/repository/)

Feed rss: [http://www.janvitus.netsons.org/feed/](http://www.janvitus.netsons.org/feed/)

Tell me any problems and suggestions ;)



p.s.: sorry for my english

Wonderful resource, thanks dude.

---

### Post by Ehtetur on 2007-11-24
> **Corbelius said:**
> Enable gutsy-proposed repository.

You've made a great repo for us x64 folks...

I have one request: Could you add an ipod-sharp deb?
It's needed for Banshee to support ipods... (libipod-cil doesn't work for me).
I got ipod support on Banshee by compiling my own ipod-sharp deb from source. But it would be great if the repos had a precompiled version that could be downloaded along with Banshee.

As for your English... Parlo il Italiano mal! :twisted:

---

### Post by Corbelius on 2007-11-28
> **Ehtetur said:**
> You've made a great repo for us x64 folks...

I have one request: Could you add an ipod-sharp deb?


Next stable release of banshee ;)

---

### Post by ST.x on 2007-11-29
I just added these repos for Gutsy. Is it safe to upgrade to all the latest compiz stuff from the default ones in Gutsy and will emerald from default repos work with the newer compiz version from this repo?

thanks

---

### Post by LaneLester on 2007-11-30
I sure wish there were a 64-bit package of kooldock. I'm running Kubuntu, and I'm reluctant to add all of the gnome packages just to get the gnome-panel. Anyway, I think kooldock is kooler.

Lane

---

### Post by ST.x on 2007-12-04
> **ST.x said:**
> I just added these repos for Gutsy. Is it safe to upgrade to all the latest compiz stuff from the default ones in Gutsy and will emerald from default repos work with the newer compiz version from this repo?

thanks

Anyone? :)

---

### Post by uaeB on 2007-12-04
> **ST.x said:**
> Anyone? :)

I haven't had any problems with the packages in the experimental section myself. I'm not using emerald myself so I can't attest to it's level of stability. One thing you might want to consider is the fact that the repository packager is currently on hiatus as he's moving so newer versions with bug fixes for your computer setup may not be available for some time if there are any. If you want a bleeding edge version of compiz, you may want to compile it from GIT.

---

### Post by Tecumseh-nl on 2007-12-07
> **Tecumseh-nl said:**
> I'm looking for those packages but then for gutsy because the opensync packages in the standard repository are not complete, a couple of plugins are missing like the gnokii plugin.

Can I use the feisty repo line or do I need to wait before these packages are introduced into the gutsy repo?

Any update on this?

---

### Post by Major_Kong on 2007-12-08
Any chance of Audacious 1.4.4 being added to the repo ?

EDIT: And the monkey's audio plugin as well ?

---

### Post by Corbelius on 2007-12-27
> **Tecumseh-nl said:**
> Any update on this?

Yeah, i use my feisty packages on gutsy ;)

> **Major_Kong said:**
> Any chance of Audacious 1.4.4 being added to the repo ?

EDIT: And the monkey's audio plugin as well ?

From my website:

"Upure64 suspended.
The repositories are suspended, I have to move to another city. See you soon."

At the moment i dont have a fast connection (edge with the cellphone) =)

---

### Post by Major_Kong on 2007-12-27
Oops, didn't see that at the time...

Got around to build them myself... But i can re-build them for the repo if you want me to.

---

### Post by Corbelius on 2008-02-08
uPure64 live again :)

Now the repository include also a couple of 32bit packages, like Banshee 0.13.2 (with the new dependencies), Conduit, Gwget...

To allow this, the string of APT has changed:

```
## uPure64 Repository
deb http://download.tuxfamily.org/upure64/ gutsy-upure64 main
# deb-src http://download.tuxfamily.org/upure64/ gutsy-upure64 main

## uPure64 Repository (Experimental)
deb http://download.tuxfamily.org/upure64/ gutsy-upure64 experimental
# deb-src http://download.tuxfamily.org/upure64/ gutsy-upure64 experimental
```

Enjoy =)

---

### Post by Major_Kong on 2008-02-09
New requests :) 
(not quite for me, but i think a lot of people would find them usefull)

Cdemu - It's a real virtual drive suite. It supports .B6T, .CCD, .CDI, .CUE, .ISO, .MDS, .NRG and .TOC image files.

Rubyripper - A secure audio ripper program that uses cdparanoia. Much better than soundjuicer at obtaining an exact rip. (think EAC)

---

### Post by a-town on 2008-02-09
So, I am running 32-bit Ubuntu Gutsy but I've been looking everywhere for a repository that includes the Banshee 0.13.2 update and this is the closest I've come.  But when I run "sudo apt-get upgrade" it holds back the Banshee package (and pidgin) with the following message:

[FONT="Courier New"]The following packages have been kept back:
  banshee pidgin-data
[/FONT]

I can load up Synaptic and force it to upgrade easily enough, but before I do this I wanted to know two things:

1) Why does apt-get hold them back?
2) Will installing them from this 64-bit repository (even though they it is a 32-bit package) cause me grief?

Or better yet, if anyone knows of a 32-bit repository that has Banshee packages, that be great too.  I just like to avoid building from source where possible.  I haven't done it in a long time, but in the past it seems that they just break when you upgrade the distro a few months down the road...


> **Corbelius said:**
> uPure64 live again :)

Now the repository include also a couple of 32bit packages, like Banshee 0.13.2 (with the new dependencies), Conduit, Gwget...

To allow this, the string of APT has changed:

```
## uPure64 Repository
deb http://download.tuxfamily.org/upure64/ gutsy-upure64 main
# deb-src http://download.tuxfamily.org/upure64/ gutsy-upure64 main

## uPure64 Repository (Experimental)
deb http://download.tuxfamily.org/upure64/ gutsy-upure64 experimental
# deb-src http://download.tuxfamily.org/upure64/ gutsy-upure64 experimental
```

Enjoy =)

---

### Post by Corbelius on 2008-02-11
> **a-town said:**
> So, I am running 32-bit Ubuntu Gutsy but I've been looking everywhere for a repository that includes the Banshee 0.13.2 update and this is the closest I've come.  But when I run "sudo apt-get upgrade" it holds back the Banshee package (and pidgin) with the following message:

[FONT="Courier New"]The following packages have been kept back:
  banshee pidgin-data
[/FONT]

I can load up Synaptic and force it to upgrade easily enough, but before I do this I wanted to know two things:

1) Why does apt-get hold them back?
2) Will installing them from this 64-bit repository (even though they it is a 32-bit package) cause me grief?

Or better yet, if anyone knows of a 32-bit repository that has Banshee packages, that be great too.  I just like to avoid building from source where possible.  I haven't done it in a long time, but in the past it seems that they just break when you upgrade the distro a few months down the road...

Block pidgin package upgrade from synaptic or apt-get, in upure64 it's only for 64bit.

---

### Post by ubuntu27 on 2008-02-11
> **a-town said:**
> So, I am running 32-bit Ubuntu Gutsy but I've been looking everywhere for a repository that includes the Banshee 0.13.2 update and this is the closest I've come.  But when I run "sudo apt-get upgrade" it holds back the Banshee package (and pidgin) with the following message:

2) Will installing them from this 64-bit repository (even though they it is a 32-bit package) cause me grief?


The repository presented in this thread is only for (K/X)Ubuntu **64bit**. It will give you lots of headaches if you install it to your 32bit Operating System.

Maybe you will be able to find your desired application at [GetDeb.net]("http://getdeb.net")

---

### Post by Corbelius on 2008-02-11
> **ubuntu27 said:**
> The repository presented in this thread is only for (K/X)Ubuntu **64bit**. It will give you lots of headaches if you install it to your 32bit Operating System.

Maybe you will be able to find your desired application at [GetDeb.net]("http://getdeb.net")

Ehm...

> **Corbelius said:**
> uPure64 live again :)

Now the repository include also a couple of 32bit packages, like Banshee 0.13.2 (with the new dependencies), Conduit, Gwget...



;)

---

### Post by ubuntu27 on 2008-02-11
> **Corbelius said:**
> Ehm...



;)

ooOooohhhhhhhhhhhhhh :popcorn:

---

### Post by kwaanens on 2008-02-17
[http://download.tuxfamily.org/upure64/dists/gutsy-upure64/Release:](http://download.tuxfamily.org/upure64/dists/gutsy-upure64/Release:) Unable to find expected entry  main-amd64/binary-amd64/Packages in Meta-index file (malformed Release file?)

Has been that way for a week now.

---

### Post by kwaanens on 2008-02-17
> **kwaanens said:**
> [http://download.tuxfamily.org/upure64/dists/gutsy-upure64/Release:](http://download.tuxfamily.org/upure64/dists/gutsy-upure64/Release:) Unable to find expected entry  main-amd64/binary-amd64/Packages in Meta-index file (malformed Release file?)

Has been that way for a week now.

Nevermind. I found what was wrong. I have used "main-amd64 experimental-amd64" before. Has there been a change?

---

### Post by Corbelius on 2008-02-19
> **kwaanens said:**
> Nevermind. I found what was wrong. I have used "main-amd64 experimental-amd64" before. Has there been a change?

](*,)

[http://ubuntuforums.org/showpost.php?p=4293171&postcount=339](http://ubuntuforums.org/showpost.php?p=4293171&postcount=339)
[http://ubuntuforums.org/showpost.php?p=1134877&postcount=1](http://ubuntuforums.org/showpost.php?p=1134877&postcount=1)

---

### Post by kwaanens on 2008-02-19
Thanks for the info!

---

### Post by kwaanens on 2008-04-14
Are you planning to provide a hardy repo as well?

---

### Post by Corbelius on 2008-04-15
Sure :)

---

### Post by kwaanens on 2008-07-19
Currently, using flashplugin-nonfree with nspluginwrapper from Upure messes up Flash. Locking nspluginwrapper at the Ubuntu version makes flash work again.

---

### Post by Corbelius on 2008-07-20
> **kwaanens said:**
> Currently, using flashplugin-nonfree with nspluginwrapper from Upure messes up Flash. Locking nspluginwrapper at the Ubuntu version makes flash work again.

Use manual installation of the flash player, working at 100%: [http://www.janvitus.netsons.org/2007/01/15/nspluginwrapper-adobe-flash-player/](http://www.janvitus.netsons.org/2007/01/15/nspluginwrapper-adobe-flash-player/)

---

