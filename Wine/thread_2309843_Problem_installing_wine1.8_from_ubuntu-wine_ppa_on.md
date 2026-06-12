---
title: "Problem installing wine1.8 from ubuntu-wine ppa on 14.04"
date: 2016-01-13
forum: Wine
---

### Post by dcottingham on 2016-01-13
I just installed wine1.8 from the ubuntu-wine ppa on a 14.04 system, following these instructions:
[http://ubuntuhandbook.org/index.php/2015/12/install-wine-1-8-stable-new-ppa/](http://ubuntuhandbook.org/index.php/2015/12/install-wine-1-8-stable-new-ppa/)

First time I run winecfg, I get two popups complaining about the absence of mono and gecko. I hit "cancel" on each. This complaint seems odd, since the "apt-get install" I did reported that it was installing mono and gecko. But I investigate.

First I deal with gecko. Following the instructions on the popup, I visit here: [http://wiki.winehq.org/Gecko](http://wiki.winehq.org/Gecko)
It explains that wine looks in /usr/share/wine/gecko. I look there, and the files are present. But the wiki says that wine1.8 requires wine-gecko2.40, and what got installed was wine-gecko2.34. I go ahead and "sudo apt-get install wine-gecko2.40 wine-gecko2.40:i386". Now winecfg does not complain about gecko, but still complains about mono.

Next I visit [http://wiki.winehq.org/Mono](http://wiki.winehq.org/Mono)
This says wine looks for mono in /usr/share/wine/mono/mono-1.0 or mono-2.0. On checking I see that the mono msi files (version 4.5.4) got installed in /usr/share/wine/mono (which has no subdirectories, wine-n.0 or otherwise). On a hunch, I just grab the latest version of mono: "sudo apt-get install wine-mono4.5.6". And now winecfg has no more complaints.

So looks to me like the dependencies in the ubuntu-wine ppa need to be fixed: 1.8 needs gecko 2.40 and mono 4.5.6.

---

### Post by yoshii on 2016-01-14
You should submit this info to the Ubuntu devs as a formal bug report.  You did a great job of figuring out what was wrong and fixing it.  Also you should re-set the thread title to [SOLVED].  So that others will utilize this info more easily.

---

