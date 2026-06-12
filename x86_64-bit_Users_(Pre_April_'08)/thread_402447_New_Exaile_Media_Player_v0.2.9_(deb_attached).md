---
title: "New Exaile Media Player v0.2.9 (deb attached)"
date: 2007-04-05
forum: x86 64-bit Users (Pre April '08)
---

### Post by cmost on 2007-04-05
Hey everyone, a brand new release of Exaile, everyone's favorite Gnome knock-off of Amarok is now available.  I've built an amd64 deb (attached) if anyone wants to get in on the goodness.  The requirements are as follows:

    * Python 2.4
    * python-gtk2 (2.8.6)
    * python-glade2
    * gstreamer0.10, gstreamer0.10-plugins-good
    * python-gst0.10 or python-gstreamer0.10
    * python-dbus
    * python-pysqlite2
    * python-mutagen
    * python-elementtree 

Optional requirements...
    * python-cddb (for audio CD support)
    * python-gpod (for iPod support) — you may need to install python-eyed3 as well
    * gstreamer0.10-plugins-ugly (for MP3 support)
    * gstreamer0.10-gnomevfs (for SHOUTcast support)
    * python-gamin (for directory watching)
    * sexy-python (to add a clear button to filters)
    * python-gnome2-extras or some similarly-named package (for lyrics, better tray icon, etc.)

Enjoy!

---

### Post by drs305 on 2007-04-05
Can you tell me if it's capable of playing MMS files from internet streams. An example is a live NHL broadcast at [http://www.nhl.com/scores/index.html](http://www.nhl.com/scores/index.html) .  (Any live game with a 'Listen' link).

Thanks.

---

### Post by John Jason Jordan on 2007-04-06
> **cmost said:**
> Hey everyone, a brand new release of Exaile, everyone's favorite Gnome knock-off of Amarok is now available.  I've built an amd64 deb (attached) if anyone wants to get in on the goodness.  
Thanks. I installed it on my Edgy amd64 computer without any problems. But now that it's installed, I can't figure out what it does. I was happy to see a tab for "Radio," but when I opened the tab and went to my favorite (Classical > Symphonic) I found a bunch of shoutcasts. They work, but how do I connect to a radio station?

I have a couple dozen internet radio stations in RealPlayer's Favorites folder. I was hoping that Exaile might be an open source alternative to RealPlayer. But I can't figure out how to add the URL for an internet radio station. I clicked on Help, but I guess it hasn't occurred to anyone to write a Help file yet.

Oh well. I've uninstalled it. I'll stick to RealPlayer for now.

---

### Post by matog on 2007-04-07
When I tried to install it, I've got the following errors:
```

Traceback (most recent call last):
  File "/usr/bin/exaile", line 2399, in ?
    main()
  File "/usr/bin/exaile", line 2388, in main
    exaile = ExaileWindow(options, fr)
  File "/usr/bin/exaile", line 108, in __init__
    self.settings = config.Config("%s%ssettings.ini" % (SETTINGS_DIR, os.sep))
  File "/usr/share/exaile/xl/config.py", line 250, in __init__
    self.config = XlConfigParser(loc)
  File "/usr/share/exaile/xl/config.py", line 50, in __init__
    converter = ConvertIniToConf(self, self.loc)
  File "/usr/share/exaile/xl/config_convert.py", line 97, in __init__
    v[1](setting, v[0])
  File "/usr/share/exaile/xl/config_convert.py", line 104, in conv_int
    self.settings.set_int(new_key, int(self.osettings[old_key]))
ValueError: invalid literal for int(): Top
```

---

### Post by joeinnes on 2007-04-24
I installed it on 64-bit Feisty, thus far, working great. Much thanks :o)

Joe

---

### Post by Kobalt on 2007-06-10
Thanks a bunch cmost, Exaile! is just awsome.

---

### Post by John Jason Jordan on 2007-06-10
> **joeinnes said:**
> I installed it on 64-bit Feisty, thus far, working great.
I installed it via Synaptic, and it appears to work fine. But I have no idea how to get it to work. For example, I have the following URLs for Bartok Radio (Budapest), Swiss Classic (Bern), and ABC (Sydney) that works fine in RealPlayer:

[http://real1.radio.hu/bartok.ram](http://real1.radio.hu/bartok.ram)
[http://real.xobix.ch/live/ssatclass.ram](http://real.xobix.ch/live/ssatclass.ram)
[http://www.abc.net.au/streaming/classic/classicfm.ram](http://www.abc.net.au/streaming/classic/classicfm.ram)

But I can't figure out how to make any of them work in Exaile. In fact, I can't get anything to work in Exaile. There is no help file and I can't find instructions anywhere on the net. Can someone tell me step by step how to add an internet radio station and make it play? Or if it's not possible, tell me that too, so I can stop trying.

---

