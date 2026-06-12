---
title: "Firefox crashes at Gmail"
date: 2009-08-10
forum: x86 64-bit Users
---

### Post by ThotDjehuty on 2009-08-10
I can't use Gmail whit Firefox because it crashes every time I go the. It let's me log in and after few seconds FF crashes. No idea whats going on, but because Ubuntu developor are doing something to Firefox before putting it to repos, so this must be case to report here at Ubuntu.

Mozilla/5.0 (X11; U; Linux x86_64; en-US; rv:1.9.0.13) Gecko/2009080315 Ubuntu/9.04 (jaunty) Firefox/3.0.13

---

### Post by sanderj on 2009-08-10
Does it also crash after de-activating / uninstalling all plugins?

If you download and install a plain Firefox 3.0 ([http://www.mozilla.com/en-US/firefox/all-older.html](http://www.mozilla.com/en-US/firefox/all-older.html)) into a seperate directory, can you run that without problems?

If YES and YES, it could be a bug, which you can report on Launchpad (not here on Ubuntu Forums). It helps for the report when you start Firefox from the command line, and post the output you see there in your bug report.

---

### Post by ThotDjehuty on 2009-08-10
> **sanderj said:**
> Does it also crash after de-activating / uninstalling all plugins?

If you download and install a plain Firefox 3.0 ([http://www.mozilla.com/en-US/firefox/all-older.html](http://www.mozilla.com/en-US/firefox/all-older.html)) into a seperate directory, can you run that without problems?

If YES and YES, it could be a bug, which you can report on Launchpad (not here on Ubuntu Forums). It helps for the report when you start Firefox from the command line, and post the output you see there in your bug report.

Thanks for the advice - I will make a test like you said!

---

### Post by emmiesix on 2009-09-03
Did you create a bug report?  I have the same issue (I suspect the alpha flash plugin from adobe), but I'm not experienced enough to debug well.

---

### Post by Anusiya on 2009-09-11
The reason is flashplugin! Go to [HTML]http://ubuntuforums.org/showthread.php?t=1263905[/HTML]

The fix worked perfectly for me.

Thanks,

Anusiya

---

