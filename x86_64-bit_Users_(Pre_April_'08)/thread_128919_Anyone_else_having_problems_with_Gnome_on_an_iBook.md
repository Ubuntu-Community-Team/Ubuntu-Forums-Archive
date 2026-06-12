---
title: "Anyone else having problems with Gnome on an iBook?"
date: 2006-02-12
forum: x86 64-bit Users (Pre April '08)
---

### Post by spaceballl on 2006-02-12
My screen gets all jumbled with GNOME. At first I thought it was an XORG issue, so I installed KDE. KDE works just fine so it must be gnome. Then I though that maybe it was an issue specific to Ubuntu so last night I installed the most recent Fedora. I will try and get a screenshot of what i'm talking about and post it, but anyone have an idea?

-Kevin

---

### Post by ssam on 2006-02-12
is this with 5.10 breezy or with a dapper flight cd? i have seen this in dapper.

---

### Post by spaceballl on 2006-02-12
It's with Dapper's most recent flight, dapper's most recent build, as well as with Fedora Core 5 test 2.

Are you sure this is a dapper problem though? I felt it was until I went to FC...

-Kevin

---

### Post by ssam on 2006-02-12
it not pressent in breezy. it must be upstream in Xorg.

i have heard the devs talk about this so i assume its in malone somewhere.

turning of the desktop background image is a work around.

update: found it [https://launchpad.net/distros/ubuntu/+source/xorg/+bug/5175](https://launchpad.net/distros/ubuntu/+source/xorg/+bug/5175)

---

### Post by spaceballl on 2006-02-12
Well, thanks so much for actually identifying the problem! So it's just a background re-draw issue eh? Looks like i'll get rid of FC5 and go back to dapper...

Although I must say, I have really enjoyed the brief time i've spent with FC5. Many aspects of the distro seem a bit more polished than Ubuntu's. However, after living on a distro w/ apt-get and debian package management, i really don't think i can go back to FC's crappy yum.

Time to re-download and burn that iso...

-Kevin

---

### Post by spaceballl on 2006-02-12
i guess my last question would be that if this is an xorg problem, why does it only manifest itself in gnome?

-kevin

---

### Post by spaceballl on 2006-02-15
Looks like the issue has been fixed in XORG, pending an upload. So it should only be a short matter of time before this issue is squashed.
Kevin

---

### Post by T31 on 2006-02-20
I got the same problem, and posted it in the dapper forum, today morning update still no solution at all, b/w I went back to icewm with rox and the -pinboard option, wow man how fast my machine runs now :D

---

### Post by T31 on 2006-02-20
[QUOTE=T31]I got the same problem, and posted it in the dapper forum, today morning update still no solution at all, b/w I went back to icewm with rox and the -pinboard option, wow man how fast my machine runs now :D[/QUOTE]


one last thing, I upgraded from breezy to dapper via sources.list changes and aptitude

sorry guys someone knows how to delete this post, I made it twice by mistake I only wanted to edit it :(

---

### Post by spaceballl on 2006-02-20
[QUOTE=T31]I got the same problem, and posted it in the dapper forum, today morning update still no solution at all, b/w I went back to icewm with rox and the -pinboard option, wow man how fast my machine runs now :D[/QUOTE]
oh dude click the link above. All you have to do is add a nopixmaps option in one config file, and it totally fixes the problem.

-Kevin

---

### Post by T31 on 2006-02-20
Spaceball I have to try this tomorrow, now Im not at home now, but the way around to eliminate the background I already tried without success :/

update: but change xorg file worked fine :S I dont know why I didnt check the link before to post :P sorry

Anyway my mac is working so fast with the combo icewm+rox with the double sized taskbar and the command line embedded that I think I will go back to icewm-experimental (mostly becouse of the antialiasing and such things) after try out a while the new Gnome features :)

---

