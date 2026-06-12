---
title: "Winetricks and the perpetual sha1sum errors"
date: 2013-02-27
forum: Wine
---

### Post by sienile on 2013-02-27
I've been trying to install Flash (among other things) with Wintricks. Every single time I do it, whether from GUI or terminal, it gives a sha1sum error. (also noted that *sh winetricks* no longer works, must use just *winetricks*)

I've tried giving _all users full control_ of **~\.cache\winetricks** and have deleted the files each time the error occurs, but it still happens **every** time.

What gives? Winetricks used to be useful, now it just seems broken.

---

### Post by sienile on 2013-02-27
Was able to get Flash 11 installed using the SVN release at: [http://winetricks.googlecode.com/svn/trunk/src/winetricks]("http://winetricks.googlecode.com/svn/trunk/src/winetricks").

Flash 10 did not install. It gave the same sha1sum error.

Is all that's wrong with Winetricks just a few outdated URLs and sums?

---

