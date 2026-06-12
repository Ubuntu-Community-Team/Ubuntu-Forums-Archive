---
title: "compiling wine with pulseaudio support"
date: 2016-01-01
forum: Wine
---

### Post by harvodan on 2016-01-01
I'm trying to build wine (1.9.0) with pulseaudio support. I have libpulse0 (plus the i386 package) libpulse-dev (plus i386 again) installed. Despite this, when compiling wine, I get "configure: libpulse 32-bit development files not found or too old, Pulse won't be supported". I can't seem to install anything that will please wine at this point, as nothing seems to satisfy this dependancy.

Any suggestions? Do I need to set up some symbolic links somewhere? Any hints? Anything at all? Google hasn't provided anything helpful and I've been looking for answers for some time.

I'm running ubuntu 15.10 64 bit and wine 1.9.0 from source with wine-staging patches. I've tried without staging, no difference.

Thanks people.

---

### Post by harvodan on 2016-01-02
Bump. Anyone out there?

---

### Post by kostkon on 2016-01-04
You could use the [wine-staging ppa]("https://launchpad.net/~ehoover/+archive/ubuntu/compholio").

---

### Post by kc1di on 2016-01-04
Or you could use playonlinux which allows you to use newer versions of wine.  without having to build them.
good luck.

---

### Post by harvodan on 2016-01-04
I actually have a few patches that I use with wine, so that rules out using wine-staging's ppa. Unless playonlinux allows the removal and adding of various patches to the source code?

---

### Post by kc1di on 2016-01-09
not sure if Playonlinux allows that never tried.

---

