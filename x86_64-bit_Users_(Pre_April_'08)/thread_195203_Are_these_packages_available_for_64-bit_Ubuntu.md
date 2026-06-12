---
title: "Are these packages available for 64-bit Ubuntu?"
date: 2006-06-12
forum: x86 64-bit Users (Pre April '08)
---

### Post by Mirrorball on 2006-06-12
At work I have installed Gentoo. If the packages below can be easily installed on Ubuntu, I might delete Gentoo and install Ubuntu in its place.
[LIST=1]
[*]32-bit firefox.
[*]Flash plugin.
[*]Acrobat Reader.
[*]64-bit boost library (for C++ development).[/LIST]These are basically the only programs I need to use at work.

---

### Post by JoWilly on 2006-06-12
Yes, yes, yes, yes :) :


1. Yes, the easiest was is to download firefox32 from getfirefox.com and start it from its extracted dir (u can i.ex put it in your home dir and change/add the launcher in the menu). This way it will automatically install flash when you click on a link, and auto update will also work (as well as realplayer32 plugin etc...). There is also a wiki in the ubuntu wikis on how to best get firefox32 to work with all the plugins.

2. Yes, see above

3. Yes, install the 32bit deb package with "dpkg -i --force-architecture" (latest deb version in the marillat repo -> search apt-get.org for acroread)

4. Yes, its in the repos.

---

### Post by Mirrorball on 2006-06-12
Thanks for the answer!

---

### Post by dyrer on 2006-06-15
How can install acroread in 64bit ?

---

