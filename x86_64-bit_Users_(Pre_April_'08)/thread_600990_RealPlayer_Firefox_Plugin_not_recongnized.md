---
title: "RealPlayer Firefox Plugin not recongnized"
date: 2007-11-02
forum: x86 64-bit Users (Pre April '08)
---

### Post by hobbes_ba on 2007-11-02
Hi, I am using Firefox 64 bits on Guitsy, Flash and IcedTea all from the repo. But after i installed Realplayer i noticed the plugin isn't showing on about:plugins.

My question is there a way to make it work under on FF 64bits? I know it works on 64 bits Feisty using Firefox 32 bits.

The nphelix.so and nphelix.xpt are listed on this directories:

 /usr/lib/mozilla/plugins/ 
/usr/lib/firefox/plugins/
/home/user/.mozilla/plugins/

Anyone?

---

### Post by Kilz on 2007-11-02
> **hobbes_ba said:**
> Hi, I am using Firefox 64 bits on Guitsy, Flash and IcedTea all from the repo. But after i installed Realplayer i noticed the plugin isn't showing on about:plugins.

My question is there a way to make it work under on FF 64bits? I know it works on 64 bits Feisty using Firefox 32 bits.

The nphelix.so and nphelix.xpt are listed on this directories:

 /usr/lib/mozilla/plugins/ 
/usr/lib/firefox/plugins/
/home/user/.mozilla/plugins/

Anyone?

The problem is that those plugins are probably 32bit so the 64bit browser cant see or use them.

---

### Post by cjazz on 2007-11-02
You know, you're right. I hadn't noticed this before because I have the mplayer-plugin installed, and it shows up as handling realplayer mime types in about: plugins. Personally, I prefer to let Real Player handle those file types, so I use the MediaPlayerConnectivity extension for Firefox to let Real Player handle streaming files as a stand-alone player. But the plug-in as such seems DOA.

---

### Post by hobbes_ba on 2007-11-02
> **Kilz said:**
> The problem is that those plugins are probably 32bit so the 64bit browser cant see or use them.

Is there a way to make it work with nspluginwrapper like the flash plugin? On the [COLOR="Sienna"][NSpluginwrapper]("http://gwenole.beauchesne.info/projects/nspluginwrapper/#downloads")[/COLOR] website says it works, but the version listed its an old one, mine its 10.0.9.809 GOLD. 

Thanks for reading.

---

### Post by Kilz on 2007-11-02
> **hobbes_ba said:**
> Is there a way to make it work with nspluginwrapper like the flash plugin? On the [COLOR="Sienna"][NSpluginwrapper]("http://gwenole.beauchesne.info/projects/nspluginwrapper/#downloads")[/COLOR] website says it works, but the version listed its an old one, mine its 10.0.9.809 GOLD. 

Thanks for reading.

You need the realplayer and the 32bit plugin installed, as well as nspluginwrapper. Then open a terminal and type ```
sudo nspluginwrapper -i /usr/lib/mozilla/plugins/nphelix.so
``` then restart the browser.
If you want the player buttons to look good, type

```
gksudo gedit /usr/bin/realplay
```

paste in the following under #!/bin/sh

```
export GTK_PATH=/usr/lib32/gtk-2.0
export LD_PRELOAD=/usr/lib32/libpangohack.so.0
export GDK_PIXBUF_MODULE_FILE=/etc/gtk-2.0/gdk-pixbuf.loaders.32
```

[You might also need this file]("http://home.comcast.net/~ubuntu64user/ia32-lib-firefox-amd64.deb") I made it for my 32bit firefox script, but it has the libs needed.

---

### Post by hobbes_ba on 2007-11-03
> **Kilz said:**
> You need the realplayer and the 32bit plugin installed, as well as nspluginwrapper. Then open a terminal and type ```
sudo nspluginwrapper -i /usr/lib/mozilla/plugins/nphelix.so
``` then restart the browser.
If you want the player buttons to look good, type

```
gksudo gedit /usr/bin/realplay
```

paste in the following under #!/bin/sh

```
export GTK_PATH=/usr/lib32/gtk-2.0
export LD_PRELOAD=/usr/lib32/libpangohack.so.0
export GDK_PIXBUF_MODULE_FILE=/etc/gtk-2.0/gdk-pixbuf.loaders.32
```

[You might also need this file]("http://home.comcast.net/~ubuntu64user/ia32-lib-firefox-amd64.deb") I made it for my 32bit firefox script, but it has the libs needed.


Thanks, again! I got halfway that. :)

I was missing this part to make work.

```
export GTK_PATH=/usr/lib32/gtk-2.0
export LD_PRELOAD=/usr/lib32/libpangohack.so.0
export GDK_PIXBUF_MODULE_FILE=/etc/gtk-2.0/gdk-pixbuf.loaders.32
```

Well, now i can see a future to my Firefox 64, besides some future - let's hope not - stability problems my daily basic needs for web browsing is complete.

You should add this to a sticky post about Firefox 64 on gutsy! It will help a lot of people  to have all that information together.

If you already did that, just forget my lack of attention.

Thanks again.

---

