---
title: "MMOD streaming"
date: 2008-03-20
forum: x86 64-bit Users (Pre April '08)
---

### Post by stringkarma on 2008-03-20
I am having problems watching the March Madness on Demand (MMOD) and I hope someone can help.

I seem to only get video with vlc plugin but no audio. I get sporadic audio with totem xine but no video.

anyone have any suggestions?

Thanks

---

### Post by davebridges on 2008-03-20
have you tried making sure you have the wmv codecs installed:

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

apparently you might have to manually uninstall some conflicting codecs too:

[http://ubuntuforums.org/showthread.php?t=146096&highlight=march+madness](http://ubuntuforums.org/showthread.php?t=146096&highlight=march+madness)

by the way I am having the same problem, i just dont have the time to fiddle around with it and figure it out

---

### Post by stringkarma on 2008-03-20
yeah, I have seen these already. Thanks though. I am stilll working on it, glad to hear I am not the only one!

---

### Post by kernel tom on 2008-03-20
> **stringkarma said:**
> yeah, I have seen these already. Thanks though. I am stilll working on it, glad to hear I am not the only one!

I would love to see a fix to this, not sure why mine isn't opening using mplayer plugin for firefox, what kind of stream is this?

tom

---

### Post by stringkarma on 2008-03-20
I think I have a fix, let me test it a bit, but it hinges on vlc and the vlc-plugin-esd.
BRB

---

### Post by stringkarma on 2008-03-20
OK I've got it I believe. I am not totally sure on the order, but here goes.

1) in synaptic remove totem-mozilla
2) in synaptic install vlc mozilla-plugin-vlc vlc-plugin-esd
3) I am not sure if it matters but I do have the ubuntu-restricted-extras as well as w64codecs installed

at this point MMOD should work.

I was also able to install totem-mozilla again here, but the video, but when watching, vlc is obviously still the player.

hope this works for you guys.

As a note it appears that my problem was that I did not have vlc-plugin-esd installed.

Also while you test, it is annoying to have to wait in the waiting room for the MMOD to let you in. This link (from the ncaa website) has a video that seems to accurately test. If you can see and hear, you should be fine.  [http://plugindoc.mozdev.org/testpages/wmp9.html](http://plugindoc.mozdev.org/testpages/wmp9.html)

Cheers!

---

### Post by pestilence4hr on 2008-03-20
The name of the plugin is mozilla-plugin-vlc.  But if you use this plugin, the video (with audio) works.  I had to disable adblock to get it to work.  I also had to disable MediaPlayerConnectivity (another plugin that worked in previous years).  Thanks!

---

### Post by thelounge on 2008-03-20
I'm new to Ubuntu and this problem is really getting the best of me.

I removed Totem, installed mozilla-plugin-vlc and vlc-plugin-esd... but MMOD video player just gives me "(no video)" on a black backround.

Is anyone else having this problem?

Note: the test link that stringkarma works for me with video + audio.

---

### Post by stringkarma on 2008-03-21
I like that vlc seems to play most kinds of video sources, but it is not very user friendly. One if its most annoying features (besides not having the ability to advance/rewind in pre-recorded streams) is that upon loading a stream it displays a message that there is no video. For a larger video, and thus a longer buffer, that message may last some time. Load up the MMOD page and wait a full minute, on a game you know is in progress (not a halftime either, I'm not sure if they kill the stream) and lets hope that your software is in fact working, as the test would indicate.

Also thanks pestilence4hr for correcting the package name. I also had to remove MediaPlayerConnectivity, but I guess it wasn't needed.

---

### Post by oddworld on 2008-03-21
Its not working for me.
I am stuck on "no video" after following the instructions above.
Also, the test page works fine.

---

### Post by stringkarma on 2008-03-27
Have you installed all your codecs?

In synaptic install w32codecs or w64codecs depending on if you have a 32 or 64 bit system. Also the ubuntu restricted package couldn't hurt in this endeavor (unless you are opposed to proprietary stuff)

Sorry if this doesn't help, it will be harder for me to help (though I can try) I was really just posting what worked for me.

---

