---
title: "breve compiling issues"
date: 2006-04-28
forum: x86 64-bit Users (Pre April '08)
---

### Post by Rxke on 2006-04-28
I'm a long-time fan of [breve]("http://www.spiderland.org/breve/"), hence my Avatar...

However there is no binary for it for LinuxPPC, and I'm stumped how to build one myself...

./configure exits, complaining missing zlib library, but I checked and zlib is installed, at least zlib1g is...:confused: 

I'm probably doin something obviously completely wrong, but what?

---

### Post by 3rdalbum on 2006-04-29
Just to check: Do you have zlib1g-dev, or just zlib1g? You should have the former as well as the latter.

---

### Post by Rxke on 2006-04-29
Yes, I did, but my noobness re: compiling had me barking up the wrong tree, despite it complainging about the zlib it turns out to be GLUT that was missing...

And a boatload of other stuff, too, grin...
I'm learning, ahem. Like *how* to read a config.log file to get the info I need :blush:

Slowly getting there, largelly thanks to Jon Klein's help and patience with me @ the breveforums...

The problem I had is that Ubuntu doesn't come with a lot -or any?- of .dev libs installed as standard, so I'm installing them bit by bit.

Thank you for the feedback.

---

