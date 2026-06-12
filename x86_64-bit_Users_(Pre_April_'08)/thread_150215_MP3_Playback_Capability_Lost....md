---
title: "MP3 Playback Capability Lost..."
date: 2006-03-25
forum: x86 64-bit Users (Pre April '08)
---

### Post by TDave on 2006-03-25
All,

After an unsuccesful forray into a direct upgrade to testing Dapper recently I was left with no easier option than to do a full reinstall of Breezy on my Powerbook G4 (I would have just done a Dapper install, except I'm in no position to maintain solid updates until the final release).

I backed up my selections and sources.list beforehand so I doubted I'd have had much trouble.
However, after reinstalling what certainly appears to be everything succesfully (apt-get dist-upgrade and reselecting and installing the selections went off without a hitch) I for some reason can still not playback MP3s or .m3us and the like through any of the players (XMMS, Quod Libet, Rhythmbox). And I'm at a loss as to why.

*.oggs play perfectly but unfortunately whilst I was back I made sure all my music was *.mp3 so that I could move it to the old iPod. I didn't have time to write as ogg as well. That was a later plan...

So, anybody have any ideas as to what could cause this? Or more importantly any ideas as to what could rectify it? Its annoying me as it worked seamlessly before but now I'm forced to be logged into OS X in order to keep myself entertained aurally whilst on the laptop :-)

Many thanks

Dave

---

### Post by jpkotta on 2006-03-25
Did you try the procedure outlined in [https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)?

---

### Post by TDave on 2006-03-26
Followed it to the letter after the selections import failed.

Completely baffled by it.

Like I say, oggs play perfectly, but if I try to open MP3s it struggles. Well actually, XMMS just sort of hangs.

---

### Post by ssam on 2006-03-26
did you install gstreamer0.8-mad

you could try running

```
gst-register-0.8
```

that makes sure that gstreamer knows about what plugins are installed

---

### Post by TDave on 2006-03-29
Thanks for the help guys.

Could have sworn I ran gst-register numerous times in the process of installing the various codecs, as well as when the MP3s didn't work the first time but I must have missed something. After a reboot all seemed to work fine again.

Strange, but thanks!

Dave

---

