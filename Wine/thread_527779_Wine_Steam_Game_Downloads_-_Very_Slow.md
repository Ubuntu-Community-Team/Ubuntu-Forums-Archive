---
title: "Wine: Steam Game Downloads - Very Slow"
date: 2007-08-17
forum: Wine
---

### Post by sjschu on 2007-08-17
Okay, I'm new to Ubuntu... I was quick to get Wine to try playing some hl2.  I got Wine installed fine, as well as Steam but one problem I've had is with game download speeds.  When downloading HL2 in Steam the download speed will go up to 380 Kb/s, and get down to less than 1 Kb/s, then eventually move back up.  I have searched around on these forums, google, and linux-gamers.net without success.  
Any ideas?

---

### Post by sjschu on 2007-08-17
Ugh, now the max I'm getting in Steam is 1KB/s, downloads through firefox and with wget in the terminal go quickly though.

---

### Post by GFree678 on 2007-08-17
I suspect it's less to do with Linux and more to do with Steam choosing a crap content server. It can happen, even in Windows.

Normally to fix this you'd delete the ClientRegistry.blob file in your Steam folder (when Steam's not running of course), then you'd run Steam again to recreate the file and hopefully it would choose a faster server. This technique sometimes screws up with WINE though.

---

### Post by sjschu on 2007-08-17
I was able to do that, but no change.

---

### Post by Sindwiller on 2007-08-17
It also depends on where you live and what kind of internet connection you have...

---

### Post by harkon on 2009-02-21
I also use Steam to play on some Left For Dead servers but I have no problems with the speed of the connection. If you have speed problems you can just consult your ISP and perhaps buy a faster internet package from him...

Steve, [http://www.grandmatrix.com](http://www.grandmatrix.com)

---

