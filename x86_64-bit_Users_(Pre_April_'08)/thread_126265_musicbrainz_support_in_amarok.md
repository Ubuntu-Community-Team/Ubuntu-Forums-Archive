---
title: "musicbrainz support in amarok"
date: 2006-02-06
forum: x86 64-bit Users (Pre April '08)
---

### Post by Josef K. on 2006-02-06
I've installed amarok from repository (and libtunepimp* and libmusicbrainz*...) but musicbrainz support seems not to work :(

so (after manually compiling taglib 1.4) I've tried to compile amarok from source but I got an error (says recursive error without any specification :confused: )

did anybody get musicbrainz support working or I'm doomed find something else?

---

### Post by Gowator on 2006-02-22
Im still stuck, I heard you can use certain repo's from Debian for the libpimp but it seems one of those 'secrets' noone is willing to post due to it not being official Ubuntu policy??  I dunno in other words but its damned frustrating so I now use my GF's Pure Debian install to fill in all the tags.  

I'm starting to wonder about switching back to pure deb because of similar problems as this.  Its a balance of a bit more hassle setting things up to start off but then a lot less 'secrecy' concerning stuff like DVD playback and libpimp and 'alternate repositories'  ...  lots of stuff works well in Ubuntu first time  that requires a bit more work in Debian but the problem for me is the whole secrecy thing whereby getting Ubuntu to do something that isn't policy is a lot harder.

---

### Post by Josef K. on 2006-02-22
[QUOTE=Gowator]Im still stuck, I heard you can use certain repo's from Debian for the libpimp but it seems one of those 'secrets' noone is willing to post due to it not being official Ubuntu policy??  I dunno in other words but its damned frustrating so I now use my GF's Pure Debian install to fill in all the tags.  
[/QUOTE]

didn't use any debian repos (not to break my breezy install)
I just recompiled by hand _all_ libraries amarok would need, then I recompiled amarok too... and still didn't work :-k
since at the moment there's no logic reason why musicbrainz support is still broken on some systems (and sounds to work with others) I simply gave up wasting my time with that ram-eater! 8)

> 
I'm starting to wonder about switching back to pure deb because of similar problems as this.  Its a balance of a bit more hassle setting things up to start off but then a lot less 'secrecy' concerning stuff like DVD playback and libpimp and 'alternate repositories'  ...  lots of stuff works well in Ubuntu first time  that requires a bit more work in Debian but the problem for me is the whole secrecy thing whereby getting Ubuntu to do something that isn't policy is a lot harder.

I don't understand
ubuntu is almost a testing debian with a greater community ;)
the only problem with ubuntu is in codecs\java\flash: in 32bit automatix works great, in 64bit there's no support at all, no matter which distro you use

---

