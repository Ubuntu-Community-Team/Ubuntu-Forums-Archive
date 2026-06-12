---
title: "Launching any media causes xserver to crash/reboot"
date: 2007-02-02
forum: x86 64-bit Users (Pre April '08)
---

### Post by WalmartSniperLX on 2007-02-02
Im running Ubuntu 6.06.1 LTS and have all needed codecs for the media I keep trying to run. However, when I click to view a video in any movie player (mplayer, totem, xine, doesnt matter) my screen will freeze, flash black, and take me to the login screen. It also does this when I click on music (.mp3, .ogg, etc). However, listening to music thru amarok seems to have no problems. 

The only problems Im seeing is when I click on the media from a file browser (nautilus) and try and open it/run it/watch it/listen to it. 

Any ideas?

---

### Post by incubus on 2007-02-02
I have very small experience with Gnome, but what I would do is since this is happening in Nautilus, I would open a terminal, run nautilus and see if you get any error messages when you click a media file.

Since it's gonna crash, you could do something like this:
```

$ nautilus > nautilus.log

```

And read it after the crash.

Now, I don't know if that's the way you launch nautilus the file browser.  It may automatically save the log file somewhere else as well.

It does sound like there's something wrong with the media engine and maybe gtk, since Amarok works fine.

incubus

---

### Post by jonas80 on 2007-02-12
> **WalmartSniperLX said:**
> Im running Ubuntu 6.06.1 LTS and have all needed codecs for the media I keep trying to run. However, when I click to view a video in any movie player (mplayer, totem, xine, doesnt matter) my screen will freeze, flash black, and take me to the login screen. It also does this when I click on music (.mp3, .ogg, etc). However, listening to music thru amarok seems to have no problems. 

The only problems Im seeing is when I click on the media from a file browser (nautilus) and try and open it/run it/watch it/listen to it. 

Any ideas?

Are you using the fglrx drivers? 

If so, try playing video from mplayer using x11 output driver, for example *mplayer -vo x11 movie.avi*

If that works, add *Option "no_dri" "on"* to your device section in /etc/X11/xorg.conf

Section "Device"
    [INDENT]Identifier "aticonfig-Device[0]"
    Driver "fglrx"
    Option "VideoOverlay" "on"
    Option "OpenGLOverlay" "off"
    Option "no_dri" "on"[/INDENT]
EndSection

// Jonas

---

