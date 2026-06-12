---
title: "Firefox Ubuntu embedded mp3 playback"
date: 2009-10-01
forum: x86 64-bit Users
---

### Post by rupert160 on 2009-10-01
Howdy all.

I'm running a vanilla install of Firefox on Ubuntu x64 with the following specs:
Ubuntu x64 9.04
Firefox 3.0.14
sound application preferences (from preferences>applications tab)
mp3 audio mplayerplug-in 3.55 (in firefox)
mp3 audio (streamed) mplayerplug-in 3.55 (in firefox)

javascript is turned on but the following code snippet in the page can't be successfully played:

page: 
[http://www.wordreference.com/es/en/translation.asp?spen=ver](http://www.wordreference.com/es/en/translation.asp?spen=ver)

html:
<a 
   title='Spain pronunciation' 
   href='' 
   onClick='DHTMLSound(
    "http://www.wordreference.com/audio/es/es/es038945-11.mp3"
   ); return false'>

javascript code to be run:
function DHTMLSound(surl) {
   if ((navigator.userAgent.indexOf('iPhone') != -1) ||
   (navigator.userAgent.indexOf('iPod') != -1)){
      window.location = surl;
   } 
   else 
   {
      document.getElementById("dummyspan").innerHTML=
         "<embed src='"+surl+"' hidden=true 
         autostart=true loop=false type='audio/mpeg'>";
   }
}

hence it tries to play the following html:
<embed src='http://www.wordreference.com/audio/es/es/es038945-11.mp3'
hidden=true autostart=true loop=false type='audio/mpeg'>

it plays successfully in ff3.0 in windows XP

further notes: I can't see any references to sound in "about:config"

Thanks in advance.

---

### Post by rupert160 on 2009-10-11
Maybe that was too wordy. I'm running Ubuntu x64 9.04 and firefox won't play/run embedded mp3 files on web pages (as described above). Ideas?

---

### Post by rupert160 on 2009-11-04
Bump.

---

### Post by polki@mac.com on 2009-11-04
I couldn't play it either. I tried with this:

[http://sorkar.se/sounds/07-hon_kommer_hit.mp3](http://sorkar.se/sounds/07-hon_kommer_hit.mp3)

and that worked in FF on Karmic 64-bit.

Sorry I couldn't be of more help.

---

### Post by P.KO on 2009-11-04
Hi,

It works ok for me. I can play your link.

Installed FF 3.5.4
Plugins: mplayerplug-in 3.55, mplayerplug-in-wmp.so, mplayerplug-in-dvx.so,

---

### Post by rupert160 on 2009-11-07
well I've looked at my plugins:

flashplugin-alternative.so	       mplayerplug-in-qt.so
libflashplayer.so		       mplayerplug-in-qt.xpt
librhythmbox-itms-detection-plugin.so  mplayerplug-in-rm.so
libtotem-cone-plugin.so		       mplayerplug-in-rm.xpt
libtotem-gmp-plugin.so		       mplayerplug-in.so
libtotem-mully-plugin.so	       mplayerplug-in-wmp.so
libtotem-narrowspace-plugin.so	       mplayerplug-in-wmp.xpt
mplayerplug-in-dvx.so		       mplayerplug-in.xpt
mplayerplug-in-dvx.xpt

after installing
sudo apt-get install mozilla-mplayer
sudo apt-get install flashplugin-nonfree

still no joy.I assume you're refering to the sound link on the page:
[http://www.wordreference.com/es/en/translation.asp?spen=ver](http://www.wordreference.com/es/en/translation.asp?spen=ver)

---

### Post by polki@mac.com on 2009-11-07
Tried the link on OS X 10.5 and it worked...

---

### Post by rupert160 on 2009-11-07
Are you using vanilla install of x64 Karmic P.KO?

---

### Post by HappyFeet on 2009-11-08
> **rupert160 said:**
> Are you using vanilla install of x64 Karmic P.KO?

Try the Mplayer or VLC plugin.

---

### Post by rupert160 on 2009-11-08
the VLC and MPlayer plugins were originally vanilla, I have now in addition installed those above. 

Please note I can hear sound on most sites. I'm _specifically_ referring to the _embedded_ tags that exist on the page url above.

---

