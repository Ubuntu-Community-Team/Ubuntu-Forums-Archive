---
title: "Flash Player on Firefox &amp; AMD64"
date: 2007-06-24
forum: x86 64-bit Users (Pre April '08)
---

### Post by Luke771 on 2007-06-24
I'm running Ubuntu7.04 AMD64 and it works pretty well, except for one small detail: I can't get the Flash Player to work on Firefox.
When I run ./flashplayer-installer I get a output telling me that I can't do that on a 64bit OS, I googled it and I found out that I could get the installer to  run by commenting out line 46, I did that and the installer actually runs, yet flash animations are not displayed and the browser complains about missing plugins.
I did run the imodified installer both as user and as root, and installed in all the possible directories where it would install: still nothing.

So far, the only solution I could find was to install the Windows version of Firefox under Wine, and run that one when I wanted to see flash stuff. Kind of annoying having to start another browser each time I want to see flash stuff, the alternative would be to always run the Windows version, which would be annoying fior different reasosn, for instance being stuck to the Wine "looks" (themes don't work) so I decided to keep running the Linux version and only using the Win version when I "need" to see some flash animation, game, or whatever.

Has anyone sorted out how to make Flash work in Firefox under Ubuntu 64bit?

---

### Post by jamesford on 2007-06-24
[http://ubuntuforums.org/showpost.php?p=2549700&postcount=1](http://ubuntuforums.org/showpost.php?p=2549700&postcount=1)

---

### Post by Luke771 on 2007-06-24
That worked perfectly, thanks.

---

