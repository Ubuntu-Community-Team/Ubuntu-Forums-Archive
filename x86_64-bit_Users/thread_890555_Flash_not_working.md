---
title: "Flash not working"
date: 2008-08-15
forum: x86 64-bit Users
---

### Post by TwoOranges on 2008-08-15
I just installed a fresh install of Ubuntu 8.04 but I am unable to get Flash working 100%. Some flash files (mostly smaller ones) I can see, but when I go for instance to [http://www.comedycentral.com/colbertreport/index.jhtml](http://www.comedycentral.com/colbertreport/index.jhtml) all flashcontent is turned into a grey rectange. 

When I run firefox from command line I can see the following messages being outputted:

```

(npviewer.bin:11151): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/immodules/im-uim.so: wrong ELF class: ELFCLASS64

(npviewer.bin:11151): Gtk-WARNING **: Loading IM context type 'uim' failed

(npviewer.bin:11151): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/immodules/im-uim.so: wrong ELF class: ELFCLASS64

(npviewer.bin:11151): Gtk-WARNING **: Loading IM context type 'uim' failed

(npviewer.bin:11151): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/immodules/im-uim.so: wrong ELF class: ELFCLASS64

(npviewer.bin:11151): Gtk-WARNING **: Loading IM context type 'uim' failed

(npviewer.bin:11151): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/immodules/im-uim.so: wrong ELF class: ELFCLASS64

(npviewer.bin:11151): Gtk-WARNING **: Loading IM context type 'uim' failed

(npviewer.bin:11151): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/immodules/im-uim.so: wrong ELF class: ELFCLASS64

(npviewer.bin:11151): Gtk-WARNING **: Loading IM context type 'uim' failed
*** NSPlugin Wrapper *** ERROR: NPP_DestroyStream() wait for reply: Connection closed
*** NSPlugin Wrapper *** ERROR: NPP_URLNotify() invoke: Connection closed
*** NSPlugin Wrapper *** ERROR: NPP_GetValue() invoke: Connection closed
*** NSPlugin Wrapper *** WARNING: unhandled variable 11 in NPP_GetValue()
*** NSPlugin Wrapper *** ERROR: NPP_GetValue() invoke: Connection closed
*** NSPlugin Wrapper *** WARNING: unhandled variable 11 in NPP_GetValue()
*** NSPlugin Wrapper *** ERROR: NPP_GetValue() invoke: Connection closed
*** NSPlugin Wrapper *** WARNING: unhandled variable 11 in NPP_GetValue()
*** NSPlugin Wrapper *** ERROR: NPP_GetValue() invoke: Connection closed
*** NSPlugin Wrapper *** WARNING: unhandled variable 11 in NPP_GetValue()
*** NSPlugin Wrapper *** ERROR: NPP_GetValue() invoke: Connection closed
*** NSPlugin Wrapper *** WARNING: unhandled variable 11 in NPP_GetValue()

```

I only got the nonfree flash plugin installed. Does anyone know how to solve this?

---

### Post by Sef on 2008-08-16
Check out [Kilz's Tutorial]("http://ubuntuforums.org/showthread.php?t=772490").

---

### Post by TwoOranges on 2008-08-16
I already followed the instructions in that thread. This solved my problem partially, because now I get video at for instance YouTube, but the Comedy Central websites still aren't working, although they worked fine in my old Ubuntu 7.10 installation :(

---

### Post by IntuitiveNipple on 2008-08-16
The problem with Comedy Central isn't the Flash player it is their web-site.

When the player loads it requests:

```

http://www.comedycentral.com/global/apps/player/flex/Loader.swf
?type=network
&CONFIG_URL=http://www.comedycentral.com/sitewide/video_player/services/config.jhtml
?uri=mgid:cms:item:thedailyshow.com:178463
&ns=thedailyshow.com
&autoplay=true
&ref=esi_unavailable
&geo=esi_unavailable

```

(I've un-escaped the CONFIG_URL to make it readable)

The CONFIG_URL however return a 404 Not Found error:
```

 wget http://www.comedycentral.com/sitewide/video_player/services/config.jhtml
--18:18:41--  http://www.comedycentral.com/sitewide/video_player/services/config.jhtml
           => `config.jhtml'
Resolving www.comedycentral.com... 84.45.224.6, 84.45.224.22
Connecting to www.comedycentral.com|84.45.224.6|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
18:18:41 ERROR 404: Not Found.

```

---

### Post by go_beep_yourself on 2008-12-13
Why are the videos at comedy central playable by some but not others? I'm having the same problem. The strange thing is, it worked earlier today. Now it tells me to install flash player even though I have it. Flash on all other websites that I've tried works just fine. I dual boot 64-bit xp and had a similar problem with it. The videos in Windows played in IE but not Firefox.

---

### Post by go_beep_yourself on 2008-12-13
I forgot to mention that I was using nspluginwrapper with the flashplugin-nonfree package from the ubuntu repositories. I didn't have video in comedy central, so I went to the adobe labs development website, downloaded flash player 64-bit alpha, copied the file over to ~/.mozill/plugins. I then had video at comedy central. I can't understand this part. Later the same day I tried again, and it was no longer working.

---

### Post by Arup on 2008-12-13
> **go_beep_yourself said:**
> I forgot to mention that I was using nspluginwrapper with the flashplugin-nonfree package from the ubuntu repositories. I didn't have video in comedy central, so I went to the adobe labs development website, downloaded flash player 64-bit alpha, copied the file over to ~/.mozill/plugins. I then had video at comedy central. I can't understand this part. Later the same day I tried again, and it was no longer working.

Did you totally remove nspluginwrapper either via a sudo apt-get --purge remove or via Synaptic? If you have remnants of older x32 Flash or nsplugin, you would have big issues.

---

### Post by go_beep_yourself on 2008-12-14
I figured out the problem. Adblock was doing it. I disabled it, and the videos played.

---

