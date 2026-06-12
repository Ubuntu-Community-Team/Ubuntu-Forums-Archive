---
title: "mplayer codecs for ppc!"
date: 2005-12-06
forum: x86 64-bit Users (Pre April '08)
---

### Post by Axios on 2005-12-06
Hi

I found this, perhaps its just me that didn't knew of them, but better to look stupid, than help fellow guys.

[http://www.mplayerhq.hu/homepage/design7/dload.html#codecs](http://www.mplayerhq.hu/homepage/design7/dload.html#codecs)

There is the all-ppc. I have to try this out.

---

### Post by Axios on 2005-12-07
[QUOTE=Axios]Hi

I found this, perhaps its just me that didn't knew of them, but better to look stupid, than help fellow guys.

[http://www.mplayerhq.hu/homepage/design7/dload.html#codecs](http://www.mplayerhq.hu/homepage/design7/dload.html#codecs)

There is the all-ppc. I have to try this out.[/QUOTE]

[http://www1.mplayerhq.hu/MPlayer/releases/codecs/all-ppc-20051120.tar.bz2](http://www1.mplayerhq.hu/MPlayer/releases/codecs/all-ppc-20051120.tar.bz2)

mplayer can't find the codecs, when I put the in /usr/lib/codecs or /usr/local/lib/codecs

What to do??

---

### Post by jdusc2002 on 2005-12-08
the codecs need to be placed in /usr/lib/win32 for mplayer to work.  i just installed it on my mac mini and it "works," albeit the video playback is rather choppy --- still working on that.  hope that helps.

JD

---

### Post by Axios on 2005-12-09
[QUOTE=jdusc2002]the codecs need to be placed in /usr/lib/win32 for mplayer to work.  i just installed it on my mac mini and it "works," albeit the video playback is rather choppy --- still working on that.  hope that helps.

JD[/QUOTE]


axios@maccie:/usr/local/lib/codecs$ mplayer
MPlayer dev-CVS--4.0.2 (C) 2000-2005 MPlayer Team
CPU: PowerPC


86 audio & 200 video codecs


I have the same number of  codecs no matter where I put the codecs. Even if I erase them.

---

