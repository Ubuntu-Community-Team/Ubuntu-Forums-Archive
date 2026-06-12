---
title: "quicktime?  please tell me this is possible..."
date: 2005-12-15
forum: x86 64-bit Users (Pre April '08)
---

### Post by kerinin on 2005-12-15
i've tried installing mplayer for firefox, and the multimedia codecs (using automatix), and searched the forums, and as far as i can tell, there's no way to watch quicktime movies in-browser.

this seems like very basic functionality to me - i can't really use ubuntu for surfing the internet if i can't watch quicktime movies.

please please tell me there's some way around this so i don't have to completely reinstall my system using 32-bit ubuntu (and wasting my 64-bit processor)  

:(

---

### Post by Suger on 2005-12-15
Isn't there a vlc plugin for firefox ?

---

### Post by RAOF on 2005-12-15
This isn't what you want to hear, but I've never got any in-browser video plugins to work.  But I haven't tried that hard, either, so it might be possible after sufficient messing around.

---

### Post by Suger on 2005-12-15
Sorry about the first answer, I forgot we were talking 64bits here.

Without wasting your install, you can always try going throught the chroot path

[http://ubuntuforums.org/showthread.php?t=24575](http://ubuntuforums.org/showthread.php?t=24575)

---

### Post by kerinin on 2005-12-15
OK, so i've installed chroot, installed gnome and all that stuff, and installed firefox.  I then added xine, vlc, and the mplayer-mozilla plugin, along with the w32codecs.

still nothing.  when i go to look at apple trailers (for example), it tries to open then in xine, but xine can't even open them.  In cany case that's not really relevant - i want to view them in the browser like a normal person.  

what am i missing here?

---

### Post by kerinin on 2005-12-15
OK, well i solved part of the problem - i had installed totem-xine, which is what was sending the files to xine.  after removing xine mplayer starts playing the clips in browser (good) however the playback is choppy and slow (bad).

have other people had similar problems with mplayer and quicktime fiels?  is it possibto use VLC in firefox instead of mplayer?

thanks

---

### Post by kerinin on 2005-12-16
OK, it seems to be fixed now...

1) install chroot.  the catch here is to make sure that breezy is installed instead of hoary.  i just changed the repos and dist-upgraded

2) install mplayer and codecs.  just to be sure, i downloaded the most recent rpm's from the mplayer site, converted them to debs, and installed them.  firefox was crashing earlier, i'm hopnig this will solve that little glitch.  make sure the totem plugins have been deleted from /chroot/usr/lib/mozilla-firefox/plugins

---

### Post by Suger on 2005-12-16
Good.

Nevertheless, I have to contradict myself once again : there is a 64 bit mozilla-vlc plugin, available through synaptic. Sadly, anyhow, there are many other issues which make it necessary to be running a 32bit browser.

---

