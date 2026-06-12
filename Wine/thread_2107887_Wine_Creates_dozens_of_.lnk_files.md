---
title: "Wine Creates dozens of .lnk files"
date: 2013-01-23
forum: Wine
---

### Post by bookcrazy on 2013-01-23
Dear All,

So I finally convinced my wife to try Ubuntu 12.04 on her Samsung netbook and she is loving it! 

However, every time she save a WORD file (installed office 2010 through Play on Linux) it creates about 1 to 3 DOZEN .lnk files. ???? Any ideas on what I can do to keep this from happening?

---

### Post by Tweak42 on 2013-01-24
Did a little searching and found this [http://bugs.winehq.org/show_bug.cgi?id=15480](http://bugs.winehq.org/show_bug.cgi?id=15480)

Try the workaround in [comment #17]("http://bugs.winehq.org/show_bug.cgi?id=15480#c17").

> **bookcrazy said:**
> Dear All,

So I finally convinced my wife to try Ubuntu 12.04 on her Samsung netbook and she is loving it! 

However, every time she save a WORD file (installed office 2010 through Play on Linux) it creates about 1 to 3 DOZEN .lnk files. ???? Any ideas on what I can do to keep this from happening?

---

### Post by bookcrazy on 2013-01-28
Tweak 42, 

Thank you for your reply! 
Unfortuantely, I forgot to mention that I'm using Play on Linux and not WINE. Sorry about that! However, I went through and added a recent folder to every hidden wine folder I could find. Let's hope it works!

---

### Post by Tweak42 on 2013-01-29
POL is essentially normal wine with a graphical installer frontend and management tools for mutiple wine versions and "bottle" prefixes.  Thus all you should need to do is find the prefix directory where POL put the Office 2010 install and add the correct directories.       


> **bookcrazy said:**
> Tweak 42, 

Thank you for your reply! 
Unfortuantely, I forgot to mention that I'm using Play on Linux and not WINE. Sorry about that! However, I went through and added a recent folder to every hidden wine folder I could find. Let's hope it works!

---

