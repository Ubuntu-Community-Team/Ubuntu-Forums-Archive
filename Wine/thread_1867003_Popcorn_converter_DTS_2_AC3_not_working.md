---
title: "Popcorn converter DTS 2 AC3 not working"
date: 2011-10-22
forum: Wine
---

### Post by kinggo on 2011-10-22
After upgrading to 11.10 I can't convert any movie with DTS to AC3. I've been successfully using this program under wine for quite long without any problems but in 11.10 it doesn't work.
Program starts normally, all audio tools are there but I always end up with this

[http://i56.tinypic.com/339ub8z.jpg](http://i56.tinypic.com/339ub8z.jpg)

Choosing different DTS decoder library doesn't help. Also tried different versions of audio tools but the error is always the same.

Ubuntu is 11.10 64 and wine version is 1.3.28

Any help or idea is more than welcome because I tried everything that came to my mind and the result is always this error. :(

---

### Post by kinggo on 2011-10-24
nobody?

---

### Post by long2know on 2012-01-08
I have the exact same problem.

I did spend a lot of time resolving it, though.  I found an alternate solution:

[https://github.com/JakeWharton/mkvdts2ac3/](https://github.com/JakeWharton/mkvdts2ac3/)

So far, it works great.  The only change I made to the script was on the line where aften is run, I added '-b 640' to increase the AC3 bitrate.

Hope that helps!

---

