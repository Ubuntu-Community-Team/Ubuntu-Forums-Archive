---
title: "Multimedia keys and gnome settings daemon"
date: 2008-05-08
forum: x86 64-bit Users
---

### Post by Sherlock Holmboy on 2008-05-08
I'm having trouble getting my multimedia keys working with gmusicbrowser. I have all the dependant perl packages installed, but when I go to enable the plugin it tells me:
```

no signal with name 'MediaPlayerKeyPressed' is exported in object '/org/gnome/SettingsDaemon'

```
I tried restarting the the gnome settings daemon and get this:
```

joe@joe-desktop:~$ killall gnome-settings-daemon
joe@joe-desktop:~$ gnome-settings-daemon
** (gnome-settings-daemon:8713): WARNING **: Failed to acquire org.gnome.SettingsDaemon

** (gnome-settings-daemon:8713): WARNING **: Could not acquire name

```
 Keys can control other programs such as totem and volume. Where do I go from here?

---

### Post by Sherlock Holmboy on 2008-05-24
*bump*

---

### Post by prshah on 2008-05-25
> **Sherlock Holmboy said:**
> I'm having trouble getting my multimedia keys working with gmusicbrowser.
```

no signal with name 'MediaPlayerKeyPressed' is exported in object '/org/gnome/SettingsDaemon'

```


Try System-Preferences-Keyboard Shortcuts; there, click on "Launch Media Player" and press the shortcut key you want.

You can also assign other actions/shortcut keys from here.

---

### Post by Sherlock Holmboy on 2008-05-25
My multimedia keys work in other applications just fine, but not in gmusicbrowser.

---

### Post by Ghost_Danser on 2008-05-28
I have the same problem. I got to this support request after searching the error on Google!

The multimedia keys are working in other players. I am on Hardy Heron.

Any luck solving the problem?

GD

---

### Post by Sherlock Holmboy on 2008-05-29
Not yet, but I just started a thread on gmusicbrowser's sourceforge forum here:

[http://sourceforge.net/forum/forum.php?thread_id=2057646&forum_id=493125](http://sourceforge.net/forum/forum.php?thread_id=2057646&forum_id=493125)

---

### Post by Sherlock Holmboy on 2008-06-04
I added the repository from gmusicbrowsers web sit and upgraded from version 0.963 to 0.964 and now everything works:guitar:

---

