---
title: "Stop Suspend Mode When Using Foobar2000 in WINE"
date: 2013-09-17
forum: Wine
---

### Post by stevenjrees on 2013-09-17
I have to use Foobar2000 in WINE to play my MP4 albums because gstreamer still doesn't support MP4 chapters via text:tx3g.

However, my PC still goes into suspend after the set interval. 
Is there anyway to stop the PC from going into suspend when Foobar2000 specifically or WINE in general is running?

cheers

---

### Post by Toz on 2013-09-17
Haven't tried it myself with a wine app, but caffeine might work for you. See [https://launchpad.net/~caffeine-developers/+archive/ppa?field.series_filter=raring]("https://launchpad.net/~caffeine-developers/+archive/ppa?field.series_filter=raring"), [http://www.webupd8.org/2012/05/2-ways-to-temporarily-disable.html]("http://www.webupd8.org/2012/05/2-ways-to-temporarily-disable.html") and [http://askubuntu.com/questions/182400/how-to-prevent-suspention-when-a-program-is-currently-running]("http://askubuntu.com/questions/182400/how-to-prevent-suspention-when-a-program-is-currently-running").

---

### Post by stevenjrees on 2013-09-19
Thanks, unfortunately, caffeine doesn't work. the only app i have found that correctly reads m4a albums is VLC. But this is a documented feature request for gstreamer since 2009 but still hasn't been implemented. Hence the need to use foobar2000

---

