---
title: "No WMV Support?"
date: 2005-06-11
forum: x86 64-bit Users (Pre April '08)
---

### Post by movery on 2005-06-11
Is there a way I can play WMV files in VLC?  Can play avi's and mpeg's ok...

Thanks,

---

### Post by rsw on 2005-06-12
i think we're waiting on x86_64 codecs from the recent MS WinXP 64 release. Dunno what the status is, but it would be nice to be able to play wmv's & realplayer movies/streams. Anyone got an update on this? Where we at?

---

### Post by FluffyElmo on 2005-06-12
I can play quite a few wmv files (pretty much any that aren't wmv9/10 encoded), and most real player files (not streams though). Sadly, I'm really not sure how I accomplished this.

I have a fairly recent ffmpeg version installed (plus AVIDemux and Transcode) and my bet is that ffmpeg provides many of the extra codecs. Though I've also installed  MPlayer/Totem-Xine/VLC and pretty much every other package in Synaptic with 'codec' in the name or description:) So it could be anything...

Still you might want to try building ffmpeg-cvs from source...couldn't hurt. I have a repository (*deb [http://cyberspace.ucla.edu/marillat/](http://cyberspace.ucla.edu/marillat/) unstable main*) that I installed most of my a/v software from but many packages have since moved on from the Hoary dependencies...you'd need to grab packages from Breezy for them to work.

---

