---
title: "Troubleshooting CVS Banshee from the RAOF repository..."
date: 2006-07-18
forum: x86 64-bit Users (Pre April '08)
---

### Post by RAOF on 2006-07-18
Ok.  Rather than cluttering up the "unofficial repository" thread with trying to get CVS Banshee running, let's do this in a separate thread.

First of all, I'll say that the version in my repository is working for me - I've just imported my 2.8K library consisting of ogg, flac, mp3 & m4a, and successfully synced my iPod.  So it should be possible to get it working for **you** :).  Banshee can be a bit unstable with all the banshee-official-plugins enabled (I'm yet to narrow it down to a particular plugin), but with just the **audioscrobbler**, **metadata searcher** and **notification area icon** plugins enabled, it seems rock solid here.

To get it to work, I needed the latest mono packages - I backported these from the Edgy repositories, and they're in the "mono" section of my repository.  The new mono fixed importing files for me - previously banshee would just segfault whenever it tried to import a file into my library.

Still, the packages don't seem to be working for everybody.  Let's see if we can fix that :)

First, and error I know how to deal with:

If you start Banshee from a terminal, and get this error:
```

** (/usr/lib/banshee/banshee.exe:27433): WARNING **: The following assembly referenced from /usr/lib/banshee/Banshee.Base.dll could not be loaded:
Assembly: Mono.Data.SqliteClient (assemblyref_index=16)
Version: 2.0.0.0
Public Key: 0738eb9f132ed756
The assembly was not found in the Global Assembly Cache, a path listed in the MONO_PATH environment variable, or in the location of the executing assembly (/usr/lib/banshee).


** (/usr/lib/banshee/banshee.exe:27433): WARNING **: The class Mono.Data.SqliteClient.SqliteCommand could not be loaded, used in Mono.Data.SqliteClient, Version=2.0.0.0, Culture=neutral, PublicKeyToken=0738eb9f132ed756

** ERROR **: file class.c: line 2505 (mono_class_setup_parent): should not be reached
aborting...
Aborted

```
you just need to install the **libmono-sqlite2.0-cil** package.  I'll fix the Banshee package in my repository to include this as a dependency, but untill then you can install the package manually.

That's the only problem I currently know how to fix.  If you have other problems, could you please run Banshee from a terminal, and paste in the error messages here - I'd like to help you, and fix my packages :)

---

### Post by RAOF on 2006-07-19
So has that fixed Banshee for everyone, or am I the only one who wants a CVS banshee? :)

---

### Post by jkwarras on 2006-08-01
I get another error on startup:
```

An unhandled exception was thrown: libdbus-glib-1

  at (wrapper managed-to-native) Banshee.BansheeEntry:dbus_g_thread_init ()
  at Banshee.BansheeEntry.Startup (System.String[] args) [0x00000] 
  at Banshee.BansheeEntry.Main (System.String[] args) [0x00000] 
.NET Version: 2.0.50727.42

Assembly Version Information:

Mono.Posix (2.0.0.0)
Banshee.Widgets (0.0.0.0)
glade-sharp (2.8.0.0)
gnome-sharp (2.8.0.0)
dbus-sharp (0.60.0.0)
gconf-sharp (2.8.0.0)
Banshee.Base (0.0.0.0)
gdk-sharp (2.8.0.0)
System (2.0.0.0)
atk-sharp (2.8.0.0)
glib-sharp (2.8.0.0)
gtk-sharp (2.8.0.0)
banshee (0.11.0.8263)
mscorlib (2.0.0.0)

Platform Information: Linux 2.6.15-26-amd64-generic x86_64 unknown GNU/Linux

Disribution Information:

[/etc/debian_version]
testing/unstable

[/etc/lsb-release]
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=6.06
DISTRIB_CODENAME=dapper
DISTRIB_DESCRIPTION="Ubuntu 6.06 LTS"
```

---

### Post by RAOF on 2006-08-02
Ok.  You've caught me at a bad time :).  I don't have access to the box that I do the banshee packaging on, and won't for a couple more days :(.

But the simple things first:  what does 
```
aptitude show libdbus-glib-1
```
give you?

---

### Post by TripleE on 2006-08-03
> **RAOF said:**
> So has that fixed Banshee for everyone, or am I the only one who wants a CVS banshee? :)
I tried it.  Banshee would work one update, but not another.  The plugins never worked for me.  It messed up beagle and f-spot to the point that I could not start them up.  Maybe it was a mono thing.  It took about an hour to get everything working again with the dapper universe and multiverse repositories.:mad:  I shall try it again though.  I love banshee and want the podcasting plugin bad.:p

---

### Post by RAOF on 2006-08-03
> **TripleE said:**
> I tried it.  Banshee would work one update, but not another.  The plugins never worked for me.  It messed up beagle and f-spot to the point that I could not start them up.  Maybe it was a mono thing.  It took about an hour to get everything working again with the dapper universe and multiverse repositories.:mad:  I shall try it again though.  I love banshee and want the podcasting plugin bad.:p

When I get back to making packages, I should be able to build the new banshee-official-plugins.  Last time I tried, the podcasting plugin had fallen behind Banshee's API.

I was afraid that the new Mono would break existing apps, but it didn't for me :).  Many of the packages got split out/renamed, so it's entirely possible that your problems running F-Spot and Beagle are due to missing packages.  Maybe I should rebuild them, too, depending on the new mono :).

---

### Post by gurgle on 2006-08-03
evan@evan-desktop:~$ banshee
Warning: [8/3/2006 10:33:51 AM] (Cannot connect to NetworkManager) - An available, working network connection will be assumed
Debug: [8/3/2006 10:33:51 AM] (Default player engine) - GStreamer 0.10
Debug: [8/3/2006 10:33:51 AM] (Audio CD Core Initialized) -

** (/usr/lib/banshee/banshee.exe:14041): WARNING **: The class IPod.TrackDatabase could not be loaded, used in ipod-sharp, Version=0.0.1.0, Culture=neutral, PublicKeyToken=536f152cecbf758a

Unhandled Exception: System.TypeInitializationException: An exception was thrown by the type initializer for Banshee.Dap.DapCore ---> System.Reflection.ReflectionTypeLoadException: The classes in the module cannot be loaded.
  at <0x00000> <unknown method>
  at (wrapper managed-to-native) System.Reflection.Assembly:GetTypes (bool)
  at System.Reflection.Assembly.GetTypes () [0x00000]
  at Banshee.Dap.DapCore..cctor () [0x00000] --- End of inner exception stack trace ---

  at <0x00000> <unknown method>
  at Banshee.Base.Globals.Initialize () [0x00000]
  at Banshee.BansheeEntry.Startup (System.String[] args) [0x00000]
  at Banshee.BansheeEntry.Main (System.String[] args) [0x00000]

---

### Post by jkwarras on 2006-08-03
> **RAOF said:**
> Ok.  You've caught me at a bad time :).  I don't have access to the box that I do the banshee packaging on, and won't for a couple more days :(.

But the simple things first:  what does 
```
aptitude show libdbus-glib-1
```
give you?
It give a message that it can't find it.
I'll try to reinstall libdbus-glib-1-2 wich seems to be the closest packages to "libdbus-glib-1". I'll see if that helps.

---

### Post by TripleE on 2006-08-03
I reenabled the repository and tried to run:
```
sudo aptitude update

``` But I am getting:
```
Err http://raof.dyndns.org dapper Release.gpg
  Could not connect to raof.dyndns.org:80 (202.63.35.99), connection timed out

``` Am I missing something?

edit:  With a little more searching,  I found [http://ubuntu.moshen.de/](http://ubuntu.moshen.de/) and [http://ubuntu.systemadministrator.org/](http://ubuntu.systemadministrator.org/) as mirrors.  I am downloading now.:)
edit:  Now I have got it installed by doing
```
sudo aptitude update
sudo aptitude upgrade

``` Banshee now starts.  Now to install the plugins and the rest:
```
sudo aptitude install banshee-albumlist banshee-albumlist-daap banshee-daap banshee-official-plugins
``` I am now getting the same error as gurgle_.:(_

---

### Post by RAOF on 2006-08-03
Ok.  Banshee-albumlist shouldn't be in the repository anymore, sorry.  It's a version of Banshee-0.10 with a little patch of mine to enable an "album info" column, similar to many of Foobar2K's columnsUI themes.  It never quite went upstream (it **was** a bit evil), and I no longer use it.  It should **replace** your current Banshee.  And it **definitely** won't work with all the banshee-official-plugins.

Furthermore, I think the API for the latest Banshee in the repository is newer than that for banshee-official-plugins; they may not work at all.  I should be able to fix these problems either tomorrow or the next day, when I'll actually have access to my build box :)

---

### Post by TripleE on 2006-08-04
> **RAOF said:**
> Ok.  Banshee-albumlist shouldn't be in the repository anymore, sorry.  It's a version of Banshee-0.10 with a little patch of mine to enable an "album info" column, similar to many of Foobar2K's columnsUI themes.  It never quite went upstream (it **was** a bit evil), and I no longer use it.  It should **replace** your current Banshee.  And it **definitely** won't work with all the banshee-official-plugins.

Furthermore, I think the API for the latest Banshee in the repository is newer than that for banshee-official-plugins; they may not work at all.  I should be able to fix these problems either tomorrow or the next day, when I'll actually have access to my build box :)
I uninstalled all of the extra banshee packages:
```
sudo apt-get remove --purge banshee-albumlist banshee-albumlist-daap banshee-daap banshee-official-plugins

``` Now banshee will not open.  /usr/bin/banshee was deleted with the above uninstall. So I did a:
```
sudo apt-get install --reinstall banshee

``` With my fingers crossed, I installed the plugins for banshee:
```
sudo aptitude install banshee-official-plugins

``` I brought up banshee, and it came up beautifully.  Sweet:p  When I started adding podcast feeds, it only downloaded mp3 and ogg podcasts, but it will not download any other format that I am aware of (divx/xvid, avi, mp4, m4a).  I guess I will be keeping iPodder.:(  The control that I have of my podcast is much better than iPodder (sort and download settings per podcast to name a few).  The audio was randomly choppy while it was downloading new podcast though.  Thanks for the help.

edit: For the choppy audio, it appears to be choppy when a podcast is transitioning from downloading to finished.
edit: When I closed banshee after adding 20+ podcast and downloading the default (lastest) podcast I closed banshee in the middle of playing a podcast and got:
```

An unhandled exception was thrown: Index is less than 0 or more than or equal to the list count.
Parameter name: index
0

  at System.Collections.ArrayList.get_Item (Int32 index) [0x00000] 
  at Banshee.Widgets.ActiveUserEventsManager.CancelAll () [0x00000] 
  at Banshee.PlayerUI.Quit () [0x00000] 
  at Banshee.PlayerUI.OnWindowPlayerDeleteEvent (System.Object o, Gtk.DeleteEventArgs args) [0x00000] 
  at (wrapper delegate-invoke) System.MulticastDelegate:invoke_void_object_DeleteEventArgs (object,Gtk.DeleteEventArgs)
  at Gtk.Widget.DeleteEventSignalCallback (IntPtr arg0, IntPtr arg1, IntPtr gch) [0x00000] 
  at (wrapper native-to-managed) Gtk.Widget:DeleteEventSignalCallback (intptr,intptr,intptr)
  at <0x00000> <unknown method>
  at (wrapper managed-to-native) Gtk.Application:gtk_main ()
  at Gtk.Application.Run () [0x00000] 
  at Banshee.BansheeEntry.Startup (System.String[] args) [0x00000] 
  at Banshee.BansheeEntry.Main (System.String[] args) [0x00000] 
.NET Version: 2.0.50727.42

Assembly Version Information:

System.Web (2.0.0.0)
System.Configuration (2.0.0.0)
Mono.CompilerServices.SymbolWriter (2.0.0.0)
DBusProxy (0.0.0.0)
SmartPlaylists (0.11.0.0)
Recommendation (0.11.0.0)
Radio (0.11.0.0)
System.Xml (2.0.0.0)
Podcast (0.11.0.0)
NotificationAreaIcon (0.0.0.0)
MiniMode (0.11.0.0)
MusicBrainz (0.0.0.0)
MetadataSearch (0.0.0.0)
MMKeys (0.0.0.0)
Audioscrobbler (0.0.0.0)
burn-sharp (0.0.0.0)
ipod-sharp-ui (0.0.1.0)
njb-sharp (0.3.0.32600)
Banshee.Dap.Njb (0.0.0.0)
libgphoto2-sharp (3.1.2391.25023)
Banshee.Dap.Mtp (0.0.0.0)
gnome-vfs-sharp (2.8.0.0)
Banshee.Dap.MassStorage (0.0.0.0)
ipod-sharp (0.0.1.0)
Banshee.Dap.Ipod (0.0.0.0)
hal-sharp (0.0.0.0)
gst-player (0.0.0.0)
System.Data (2.0.0.0)
Mono.Data.SqliteClient (2.0.0.0)
pango-sharp (2.8.0.0)
Mono.Posix (2.0.0.0)
Banshee.Widgets (0.0.0.0)
glade-sharp (2.8.0.0)
gnome-sharp (2.8.0.0)
dbus-sharp (0.60.0.0)
gconf-sharp (2.8.0.0)
Banshee.Base (0.0.0.0)
gdk-sharp (2.8.0.0)
System (2.0.0.0)
atk-sharp (2.8.0.0)
glib-sharp (2.8.0.0)
gtk-sharp (2.8.0.0)
banshee (0.11.0.8263)
mscorlib (2.0.0.0)

Platform Information: Linux 2.6.15-26-amd64-k8 x86_64 unknown GNU/Linux

Disribution Information:

[/etc/debian_version]
testing/unstable

[/etc/lsb-release]
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=6.06
DISTRIB_CODENAME=dapper
DISTRIB_DESCRIPTION="Ubuntu 6.06.1 LTS"

```
It appears to be a one time thing because I tried closing banshee playing the same podcast again with no problems.  Strange:-k

---

### Post by jkwarras on 2006-08-13
With banshee version 0.11.0-cvs-0raof11 it gives me a different error:
```

Unhandled Exception: System.NullReferenceException: Object reference not set to an instance of an object
  at Banshee.Base.Branding.get_ApplicationIconName () [0x00000]
  at Banshee.Base.IconThemeUtils.SetWindowIcon (Gtk.Window window) [0x00000]
  at Banshee.Gui.Dialogs.ExceptionDialog..ctor (System.Exception e) [0x00000]
  at Banshee.Gui.CleanRoomStartup.Startup (Banshee.Gui.StartupInvocationHandler startup, System.String[] args) [0x00000]
  at Banshee.BansheeEntry.Main (System.String[] args) [0x00000]

```
Any ideas? :)

---

### Post by TripleE on 2006-08-14
I just installed banshee version 0.11.0-cvs-0raof13, and it works fine for me.  I would try to upgrade first.

The only 2 banshee packages that I have installed are banshee and banshee-official-plugins.  You can do a 
```
dpkg -l | grep banshee

```
and look for "ii" in from of the package to see what is installed.

---

### Post by jkwarras on 2006-08-15
I also have only those two packages installed (ii) but I do have the startup error :(

---

### Post by TripleE on 2006-08-17
When I was having problems with banshee I would clear the config folder:
```
rm -rf ~/.gnome2/banshee/

```
If that does not work, then I would uninstall and reinstall:
```

sudo apt-get remove --purge banshee banshee-official-plugins
sudo apt-get install --reinstall banshee banshee-official-plugins

```

---

### Post by yext on 2006-09-22
> **jkwarras said:**
> With banshee version 0.11.0-cvs-0raof11 it gives me a different error:
```

Unhandled Exception: System.NullReferenceException: Object reference not set to an instance of an object
  at Banshee.Base.Branding.get_ApplicationIconName () [0x00000]
  at Banshee.Base.IconThemeUtils.SetWindowIcon (Gtk.Window window) [0x00000]
  at Banshee.Gui.Dialogs.ExceptionDialog..ctor (System.Exception e) [0x00000]
  at Banshee.Gui.CleanRoomStartup.Startup (Banshee.Gui.StartupInvocationHandler startup, System.String[] args) [0x00000]
  at Banshee.BansheeEntry.Main (System.String[] args) [0x00000]

```
Any ideas? :)

Hi jkwarras,

Try this and launch banshee again.
```
sudo apt-get build-dep banshee
```

I had same error on 0.11.0-cvs-0raof13, but after build-dep, it worked fine:D

---

### Post by jkwarras on 2006-09-25
> **yext said:**
> 
Try this and launch banshee again.
```
sudo apt-get build-dep banshee
```

Thanks. I'll try this and report :)

---

### Post by jkwarras on 2006-09-26
> **yext said:**
> Hi jkwarras,

Try this and launch banshee again.
```
sudo apt-get build-dep banshee
```

I had same error on 0.11.0-cvs-0raof13, but after build-dep, it worked fine:D
It works :) However, it's a pity that you have to install so much extra stuff (and MB) to run banshee...

---

