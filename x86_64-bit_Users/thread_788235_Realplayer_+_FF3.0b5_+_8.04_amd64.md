---
title: "Realplayer + FF3.0b5 + 8.04 amd64?"
date: 2008-05-09
forum: x86 64-bit Users
---

### Post by Zorael on 2008-05-09
I've been trying to get Realplayer running on my Kubuntu 8.04 x64 installation for a while now, with marginal success.

After realizing that I couldn't just grab the RealPlayerGOLD11.bin from the site like everyone else (since it's for x32 browsers), I googled and found the site with nightly builds. I've been trying a whole bunch now and they all segfault on me.

([http://forms.helixcommunity.org/helix/builds/?category=realplay-current](http://forms.helixcommunity.org/helix/builds/?category=realplay-current))
```
zorael@sunspire:~$ realplay http://www.udel.edu/UMS/itv/realplayer/test.rpm
/usr/bin/realplay: line 54: 25425 Segmentation fault      $HELIX_LIBS/realplay.bin "$@"
```

As for the plugin, I know how to symlink the libraries to get them to work in Firefox 3.0b5. The embedded video player shows up (with controls and everything), prints a message about connecting and loading, then the player goes gray and it outputs a segfault message to the terminal. Firefox remains running (thankfully), but the plugin will have disappeared from about:plugins.


Does anyone have any advice as to where I should look for a stable amd64 Realplayer?

---

### Post by dabang on 2008-05-09
There should be nothing wrong with standard RealPlayerGOLD11.bin, but you have to do a little extra work.
First install ia-32libs and nspluginwrapper:
```
sudo apt-get install ia32-libs nspluginwrapper
```
Now install Realplayer by executing the bin file:
```
chmod +x /path/to/RealPlayerGOLD11.bin
sudo /path/to/RealPlayerGOLD11.bin
```
This will install RealPlayer system wide, I'd recommend installing it into /opt. This will also install the 32bit plugin file to Firefox' plugin directory. Of course Firefox being 64bit connot handle those. So, we need to find and delete them:
```
ls -la /usr/lib/*/plugins/nphelix*
```
Delete all the "nphelix.so" files the command above shows up. Now install the plugin again with nspluginwrapper:
```
sudo nspluginwrapper -i /opt/RealPlayer/.../nphelix.so
```
(I don't remember the exact path right now...)
I havn't tried nspluginwrapper with RealPlayer11, so I can't say for sure, if this works! (It did work with AdobeReader 8.12 plugin)

---

### Post by Zorael on 2008-05-09
```
...

Calling realplay
playeripc: Got command Version 1
playeripc: Got command Embed type='audio/x-pn-realaudio-plugin' pluginspage='http://www.udel.edu/ums/itv/realplayer/testfailed.html' src='test.rpm' controls='ImageWindow' console='lecture' autostart='true' height='240' width='600'

(npviewer.bin:30726): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libqtengine.so: wrong ELF class: ELFCLASS64

(npviewer.bin:30726): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libqtengine.so: wrong ELF class: ELFCLASS64
playeripc: Got command Browser 0 'Mozilla/5.0 (X11; U; Linux x86_64; en-US; rv:1.9b5) Gecko/2008050509 Firefox/3.0b5' 0 1
playeripc: Got command SetWindow 0 75497496 0 0 600 240 0 0 240 600 1

(realplay.bin:30746): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libqtengine.so: wrong ELF class: ELFCLASS64

(realplay.bin:30746): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libqtengine.so: wrong ELF class: ELFCLASS64

(realplay.bin:30746): GLib-GObject-WARNING **: /build/buildd/glib2.0-2.16.3/gobject/gsignal.c:1669: signal `button_press_event' is invalid for instance `0x8172148'

(realplay.bin:30746): GLib-GObject-WARNING **: /build/buildd/glib2.0-2.16.3/gobject/gsignal.c:1669: signal `start_seeking' is invalid for instance `0x8172148'

(realplay.bin:30746): GLib-GObject-WARNING **: /build/buildd/glib2.0-2.16.3/gobject/gsignal.c:1669: signal `stop_seeking' is invalid for instance `0x8172148'
Failed to load pixbuf file: /opt/realplayer/share/realplay/logo.png: Unable to load image-loading module: /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: wrong ELF class: ELFCLASS64

(realplay.bin:30746): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
*** NSPlugin Wrapper *** WARNING: unhandled variable 11 in NPP_GetValue()
playeripc: Got command SetWindow 0 75497496 0 0 600 240 0 0 240 600 1
playeripc: Got command Embed type='audio/x-pn-realaudio-plugin' src='empty.rpm' controls='ControlPanel' console='lecture' height='25' width='350'
playeripc: Got command Browser 1 'Mozilla/5.0 (X11; U; Linux x86_64; en-US; rv:1.9b5) Gecko/2008050509 Firefox/3.0b5' 0 1
playeripc: Got command SetWindow 1 75497503 0 240 350 25 0 0 25 350 1
Failed to load pixbuf file: /opt/realplayer/share/default/play.png: Unable to load image-loading module: /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: wrong ELF class: ELFCLASS64
Failed to load pixbuf file: /opt/realplayer/share/default/pause.png: Unable to load image-loading module: /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: wrong ELF class: ELFCLASS64
Failed to load pixbuf file: /opt/realplayer/share/superbuffer/track.png: Unable to load image-loading module: /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: wrong ELF class: ELFCLASS64
Failed to load pixbuf file: /opt/realplayer/share/superbuffer/nonsuperb.png: Unable to load image-loading module: /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: wrong ELF class: ELFCLASS64
Failed to load pixbuf file: /opt/realplayer/share/superbuffer/superbuffer.png: Unable to load image-loading module: /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: wrong ELF class: ELFCLASS64
Failed to load pixbuf file: /opt/realplayer/share/superbuffer/superbufferlive.png: Unable to load image-loading module: /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: wrong ELF class: ELFCLASS64

** (realplay.bin:30746): CRITICAL **: file superbufhscale.cpp: line 493 (void hx_superbuf_hscale_init(HXSuperbufHScale*)): assertion `superbuf_hscale->tile_graphics[HX_SUPERB_MODE_BG].pixbuf' failed
Failed to load pixbuf file: /opt/realplayer/share/default/volume_popup_mute.png: Unable to load image-loading module: /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: wrong ELF class: ELFCLASS64
Failed to load pixbuf file: /opt/realplayer/share/default/volume_popup_off.png: Unable to load image-loading module: /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: wrong ELF class: ELFCLASS64
Failed to load pixbuf file: /opt/realplayer/share/default/volume_popup_low.png: Unable to load image-loading module: /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: wrong ELF class: ELFCLASS64
Failed to load pixbuf file: /opt/realplayer/share/default/volume_popup_mid.png: Unable to load image-loading module: /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: wrong ELF class: ELFCLASS64
Failed to load pixbuf file: /opt/realplayer/share/default/volume_popup_high.png: Unable to load image-loading module: /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: wrong ELF class: ELFCLASS64
Failed to load pixbuf file: /opt/realplayer/share/default/volume_mute.png: Unable to load image-loading module: /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: wrong ELF class: ELFCLASS64
Failed to load pixbuf file: /opt/realplayer/share/default/volume_off.png: Unable to load image-loading module: /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: wrong ELF class: ELFCLASS64
Failed to load pixbuf file: /opt/realplayer/share/default/volume_low.png: Unable to load image-loading module: /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: wrong ELF class: ELFCLASS64
Failed to load pixbuf file: /opt/realplayer/share/default/volume_mid.png: Unable to load image-loading module: /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: wrong ELF class: ELFCLASS64
Failed to load pixbuf file: /opt/realplayer/share/default/volume_high.png: Unable to load image-loading module: /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: wrong ELF class: ELFCLASS64
*** NSPlugin Wrapper *** WARNING: unhandled variable 11 in NPP_GetValue()

(realplay.bin:30746): Pango-CRITICAL **: pango_layout_set_text: assertion `layout != NULL' failed

(realplay.bin:30746): Pango-CRITICAL **: pango_layout_get_pixel_extents: assertion `PANGO_IS_LAYOUT (layout)' failed
playeripc: Got command SetWindow 1 75497503 0 240 350 25 0 0 25 350 1

(realplay.bin:30746): Pango-CRITICAL **: pango_layout_set_text: assertion `layout != NULL' failed

(realplay.bin:30746): Pango-CRITICAL **: pango_layout_get_pixel_extents: assertion `PANGO_IS_LAYOUT (layout)' failed
playeripc: Got command Embed type='audio/x-pn-realaudio-plugin' src='empty.rpm' controls='StatusField' console='lecture' height='25' width='130'
playeripc: Got command Browser 2 'Mozilla/5.0 (X11; U; Linux x86_64; en-US; rv:1.9b5) Gecko/2008050509 Firefox/3.0b5' 0 1
playeripc: Got command SetWindow 2 75497509 350 240 130 25 0 0 25 130 1
*** NSPlugin Wrapper *** WARNING: unhandled variable 11 in NPP_GetValue()
playeripc: Got command SetWindow 2 75497509 350 240 130 25 0 0 25 130 1
playeripc: Got command Embed type='audio/x-pn-realaudio-plugin' src='empty.rpm' controls='PositionField' console='lecture' height='25' width='120'
playeripc: Got command Browser 3 'Mozilla/5.0 (X11; U; Linux x86_64; en-US; rv:1.9b5) Gecko/2008050509 Firefox/3.0b5' 0 1
playeripc: Got command SetWindow 3 75497513 480 240 120 25 0 0 25 120 1
*** NSPlugin Wrapper *** WARNING: unhandled variable 11 in NPP_GetValue()
playeripc: Got command SetWindow 3 75497513 480 240 120 25 0 0 25 120 1
playeripc: Got command NewStream 0 0 http://www.udel.edu/UMS/itv/realplayer/test.rpm audio/x-pn-realaudio-plugin 49



(realplay.bin:30746): Pango-CRITICAL **: pango_layout_set_text: assertion `layout != NULL' failed
*<removing about 20 of these lines>*


Opening ALSA PCM device pulse
/usr/bin/realplay: line 54: 30746 Floating point exception$HELIX_LIBS/realplay.bin "$@"
```
Well! At least it didn't segfault this time, but close enough.

The plugin is properly placed as **/usr/lib/firefox-addons/plugins/npwrapper.helix.so**, and obviously the browser finds it and tries to use it.

Any other ideas?

---

### Post by Zorael on 2008-05-09
I tried another test page (randomly googling) to see if the crashes were caused by that specific video. And it actually played. But the audio sounded like the unoiled hinges of the gates of hell grinding in symphony with a choir of undead rodents, lamenting their lost lives and all the cheese that went with it.

The sound would only stop if I stopped alsa itself, resuming if I restarted it, so I had to do a system reboot to be rid of it. Needless to say, I removed that Realplayer version.

Any other ideas?

---

### Post by Yellow Pasque on 2008-05-09
I believe this will get RealPlayer for you:
```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by Zorael on 2008-05-09
> **Temüjin said:**
> I believe this will get RealPlayer for you:
```
sudo apt-get install ubuntu-restricted-extras
```
The restricted extras packages actually don't contain Realplayer; it doesn't seem to be in the repositories at all.

[http://packages.ubuntu.com/hardy/ubuntu-restricted-extras](http://packages.ubuntu.com/hardy/ubuntu-restricted-extras)

---

### Post by Yellow Pasque on 2008-05-09
Zorael, I think Gutsy used to have RealPlayer in that package, but I just double-checked and you're right. No RP in the repo :( Sorry.

---

### Post by oozie on 2009-02-08
> **Zorael said:**
> [...]
```
zorael@sunspire:~$ realplay http://www.udel.edu/UMS/itv/realplayer/test.rpm
/usr/bin/realplay: line 54: 25425 Segmentation fault      $HELIX_LIBS/realplay.bin "$@"
```

As for the plugin, I know how to symlink the libraries to get them to work in Firefox 3.0b5. The embedded video player shows up (with controls and everything), prints a message about connecting and loading, then the player goes gray and it outputs a segfault message to the terminal. Firefox remains running (thankfully), but the plugin will have disappeared from about:plugins.

Does anyone have any advice as to where I should look for a stable amd64 Realplayer?
Not exactly this but I had a similar problem on an x86_64 Gentoo with Firefox3, except that RealPlayer worked fine from the commandan line (not from FF3). I tried messing with the command line options and found that -n does the trick for me. I edited /usr/bin/realplay to add -n to realplay.bin as described [HERE]("http://troubleshoot.ooz.ie/2009/02/program-realplaybin-received-x-window.html") and had no problems since.

---

