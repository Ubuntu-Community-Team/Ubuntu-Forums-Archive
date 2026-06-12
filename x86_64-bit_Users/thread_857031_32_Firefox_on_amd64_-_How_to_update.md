---
title: "32 Firefox on amd64 - How to update?"
date: 2008-07-12
forum: x86 64-bit Users
---

### Post by mdsharp24 on 2008-07-12
First, I want to say that I am TRULY thankful for the workaround listed [[COLOR="Blue"]_Here_[/COLOR]]("https://help.ubuntu.com/community/AMD64/FirefoxAndPlugins#32bit").... as my Firefox, flash, etc... issues on amd64 have been a headache.

I followed the directions and everything is now sane. However, I have one thought and one question as it relates to running Firefox 32 Bit on amd64 and the plugins.

1. Obviously since this entire tutorial relies on manually installing Firefox, Flash Player 9, Realplayer, firefoxmplayer, and firefox-form-widgets not via apt-get/aptitude/synaptics then I am not going to get updates and will have to rely on looking for the updates to Firefox, flash, realplayer, firefoxmplayer and the widgets every few months to make sure I get security patches and updates correct?

2. In the tutorial, it asks you to place the following info in /usr/local/bin/firefox32:

export GTK_PATH=/usr/lib32/gtk-2.0
export PANGO_RC_FILE=/etc/pango32/pangorc
export GDK_PIXBUF_MODULE_FILE=/etc/gtk-2.0/gdk-pixbuf.loaders.32
linux32 /usr/local/firefox32/firefox "$@"

I don't have the file /etc/gtk-2.0/gdk-pixbuf.loaders.32 or gdk-pixbuf.loaders.32 anywhere on my system. Where can I get this file?

Michael

---

### Post by soxs on 2008-07-12
Did you try ```
sudo apt-get install gtk2-engines-pixbufgtk2-engines-pixbuf
```

---

### Post by mdsharp24 on 2008-07-12
It's already installed...

michael@makayla:~$ sudo apt-get install gtk2-engines-pixbuf
Reading package lists... Done
Building dependency tree       
Reading state information... Done
gtk2-engines-pixbuf is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
michael@makayla:~$

---

