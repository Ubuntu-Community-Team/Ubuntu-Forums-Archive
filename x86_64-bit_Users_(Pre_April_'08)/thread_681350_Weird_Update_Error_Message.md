---
title: "Weird Update Error Message"
date: 2008-01-28
forum: x86 64-bit Users (Pre April '08)
---

### Post by ohmycar on 2008-01-28
So after following this guide that was supposed to resolve my driver issues with my soundcard, I gave up and went back to the default kernel and now when I try to update, I get this:

[IMG]http://img91.imageshack.us/img91/4082/55340949od9.jpg[/IMG]

this is the guide I followed:
[http://ubuntuforums.org/showthread.php?t=571656](http://ubuntuforums.org/showthread.php?t=571656)


Anyone have any ideas on how to resolve this?

---

### Post by prince_niceguy on 2008-01-29
can you run in the terminal

> $ sudo apt-get update

that should give some more details. seems like a pacakage .deb is missing from the /var/cache/apt/archives directory.

find the package missing and copy it into this directory.

---

### Post by Kilz on 2008-01-29
> **ohmycar said:**
> So after following this guide that was supposed to resolve my driver issues with my soundcard, I gave up and went back to the default kernel and now when I try to update, I get this:

[IMG]http://img91.imageshack.us/img91/4082/55340949od9.jpg[/IMG]

this is the guide I followed:
[http://ubuntuforums.org/showthread.php?t=571656](http://ubuntuforums.org/showthread.php?t=571656)


Anyone have any ideas on how to resolve this?

Did you perhaps compile a custom kernel?

---

